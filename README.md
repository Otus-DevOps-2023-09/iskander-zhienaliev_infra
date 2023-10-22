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
bastion_IP = 51.250.13.99 <br/>
someinternalhost_IP = 10.128.0.27
