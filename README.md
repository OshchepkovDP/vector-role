# Vector Role

Ansible-роль для установки и настройки агрегатора логов [Vector](https://vector.dev).

## Требования

- Ansible >= 2.10
- Ubuntu 20.04+ / Debian 11+
- Права sudo (become)

## Переменные роли

### Пользовательские переменные (`defaults/main.yml`)

| Переменная           | Значение по умолчанию       | Описание                              |
|----------------------|-----------------------------|---------------------------------------|
| `vector_version`     | `0.55.0`                    | Версия Vector                         |
| `vector_install_dir` | `/opt/vector`               | Директория установки                  |
| `vector_config_dir`  | `/etc/vector`               | Директория конфигурации               |
| `vector_config_path` | `/etc/vector/vector.yaml`   | Путь к файлу конфигурации             |
| `vector_data_dir`    | `/var/lib/vector`           | Директория данных                     |

### Внутренние переменные (`vars/main.yml`)

| Переменная             | Описание                              |
|------------------------|---------------------------------------|
| `vector_download_url`  | URL для загрузки архива с бинарником  |
| `vector_binary_path`   | Путь к бинарному файлу vector         |

## Зависимости

Нет.

## Пример использования

```yaml
- name: Install Vector
  hosts: vector
  become: true
  roles:
    - role: vector-role
      vars:
        vector_version: "0.55.0"
