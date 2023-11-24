# iskander-zhienaliev_infra
iskander-zhienaliev Infra repository

Конфигурация ВМ YC:
<br/><br/>
ssh_key_name = yc
1. bastion
   * public_IP = 51.250.13.99
   * internal_IP = 10.128.0.24
   * username = appuser
2. someinternalhost
   * internal_IP = 10.128.0.27
   * username = appuser

### Cпособ подключения к someinternalhost в одну команду из рабочего устройства

```console
ssh -i ~/.ssh/yc -J appuser@51.250.13.99 appuser@10.128.0.27
```
### Alias ssh с именем someinternalhost
1. В консоль используем команду
    ```console
    nano ~/.ssh/config
    ```
2. Вставляем следующий код
    ```
    Host someinternalhost
        HostName 10.128.0.27
        User appuser
        IdentityFile ~/.ssh/yc
        ProxyJump appuser@51.250.13.99
    ```
3. Сохраняем

### Данные для подключения
bastion_IP = 51.250.13.99

someinternalhost_IP = 10.128.0.27

### Приложение ruby
testapp_IP = 130.193.54.53

testapp_port = 9292

## HW7 Принципы организации инфраструктурного кода и работа над инфраструктурой в команде на примере Terraform

### Выполнено:

1. Разделение приложения на две ВМ. Перенастроен Packer

2. Разделение конфигурации тестового приложения на конфигурации двух инстансов (БД и App);

3. Внедрение модулей в Terraform;

4. Настройка remote backend


## HW 8. Знакомство с Ansible.

1. Установка ansible
2. Знакомство с inventory разных форматов
3. Управление сервером через команды ansible
