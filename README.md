# Linux System Administration Test Task

Тестовое задание по системному администрированию Linux.

## Environment

- Virtualization: Proxmox VE / KVM
- Guest OS: Ubuntu Server
- Hostname: ubuntu-test
- Main interface: ens18
- Static IPv4: 192.168.243.135/24
- Gateway: 192.168.243.2
- DNS: 192.168.243.2

## Network configuration

На сервере настроен статический IPv4-адрес через Netplan.

Также созданы VLAN-интерфейсы:

- VLAN 10: 192.168.10.1/24
- VLAN 20: 192.168.20.1/24

Файл конфигурации:

`configs/netplan.yaml`

Описание сети:

`docs/network-description.md`

## WireGuard VPN

На сервере установлен и настроен WireGuard.

- Interface: wg0
- Server VPN IP: 10.10.10.1/24
- Listen port: 51820
- Client VPN IP: 10.10.10.2/32

Подключение клиента проверено с Windows. WireGuard handshake и передача данных работают.

В репозитории находится только безопасный пример конфигурации:

`configs/wg0.conf.example`

Приватные ключи в репозиторий не добавляются.

## Remote administration

Удалённое администрирование виртуальной машины выполняется по SSH.

Также настроено подключение к серверу через VPN WireGuard.

## Repository structure

- `configs/` — примеры конфигурационных файлов
- `docs/` — текстовые описания выполненных настроек
- `screenshots/` — скриншоты проверки и результатов
