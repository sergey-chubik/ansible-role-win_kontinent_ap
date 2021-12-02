Ansible Role: Win-Kontinent-AP
=========

Эта роль установит Континент-АП на ОС Windows.
Континент-АП Ver=3.7.7.651
Установка производится без межсетевого экрана.

Requirements
------------

None.

Role Variables
--------------

Доступные переменные перечислены вместе со значениями по умолчанию (см. `defaults/main.yml`).
Роль добавит статический маршрут на АРМ пользователя через прокси-сервер для доступа к серверам СУФД Казначейства (Default: true):
  - win_kontinent_ap_static_route: true

Dependencies
------------

Выполнение роли может заканчиться ошибкой, например если на хосте настроены виртуальные сетевые карты:
  - "winrm connection error: HTTPSConnectionPool(host='desktop-buh-test.ekaterinburg.fsin.uis', port=5986): Read timed out. (read timeout=30)"

Возникает из-за того что установщик перезапускает сетевые службы и вызывает временную недоступность сети, заставляя Ansible предполагать, что система недоступна, однако сама установка Континент-АП завершается успешно. Как победить эту ошибку пока не придумал!

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - win_kontinent_ap

License
-------

BSD

Author Information
------------------

Chubik Sergey, sergey.chubik@mail.ru.
Chubik Sergey, chubik@ekaterinburg.fsin.uis.
