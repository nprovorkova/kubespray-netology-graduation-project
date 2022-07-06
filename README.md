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
