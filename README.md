### Создание Kubernetes кластера
#### Создать Kubernetes кластер на базе предварительно созданной инфраструктуры
* Подготовить ansible конфигурации, можно воспользоваться, например Kubespray
* Задеплоить Kubernetes на подготовленные ранее инстансы, в случае нехватки каких-либо ресурсов вы всегда можете создать их при помощи Terraform.

#### Ожидаемые результаты:
* Работоспособный Kubernetes кластер.
* В файле ~/.kube/config находятся данные для доступа к кластеру.
* Команда kubectl get pods --all-namespaces отрабатывает без ошибок.

#### Команды:
ansible-playbook -i ../kubespray-netology-graduation-project/netology-cluster/inventory.ini cluster.yml -b -v -e ansible_user=ubuntu
<br>ssh ubuntu@"{{ tf_master_ip }}"
<br>mkdir -p $HOME/.kube
<br>sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
<br>sudo chown $(id -u):$(id -g) $HOME/.kube/config
<br>kubectl get pods --all-namespaces -o wide
<br>scp file ubuntu@"{{ tf_master_ip }}":~/.kube/config ~/.kube/
<br>Заменяем в конфиге адрес сервера на tf_master_ip
<br>С локального компа проверяем kubectl get pods --all-namespaces -o wide


