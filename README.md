# MikroTik-RouterOS-Update-Ansible
Обновление устройств MikroTik RouterOS с использованием Ansible (как CHR, так и RB)

<h1>Что обновляем?</h1>

- Обновление RouterOS с помощью Ansible

<h1>Где обновляем?</h1>

- Протестировано на Ansible 2.9.17
- Версия RouterOS не ниже 6.45 так как используется sftp для передачи файлов

<h1>Как обновляем?</h1>

- Просто запусти плейбук <b>RouterOS-Update.yml</b>
- Плейбуки <b>BackupRouterOS.yml</b>, <b>UpdateRouterOS-RB.yml</b>, <b>UpdateRouterOS-CHR.yml</b> запускать не нужно, это подзадачи.

<h1>Внимание!</h1>

- Я использую ssh-ключи для аутентификации в примере (и вам рекомендую)
- Перед использованием проверьте последнюю версию RouterOS и введите ее в <b>RouterOS-Update.yml</b> в трех местах (строки № 7, 40, 46)

<h1>Как это работает?</h1>

Этапы работы:
1. Выполнение экспорта и резервного копирования файлов RouterOS
2. Копирование этих файлов в папку "Backup"
3. Проверка и вывод, если это CHR или RB
4. Проверка и вывод версии RouterOS (как CHR, так и RB)
5. Обновление CHR RouterOS, если это необходимо (когда текущая версия RouterOS != {{ version }})
6. Обновление прошивки RB RouterOS + RB Firmware, если это необходимо (при текущей версии RouterOS != {{ version }})
7. Проверка и вывод версии RouterOS после обновления (как CHR, так и RB)
8. Проверка и вывод версии прошивки после обновления (относится только к RB)
9. Необходимая чистка на каждом этапе

Из-за сценариев (задержек и пауз) продолжительность обновления RB и CHR составляет 6 мин 25 сек и 2 мин 15 сек соответственно
