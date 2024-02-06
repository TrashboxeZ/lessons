# Home Task

1. Доработать роль Ansible  для работы с системами семейства RedHat.
2. Добавить внятный Readme с описание возможностей и примерам использования.
3. Протестировать роль, используя Vagrant. Можно использовать и адаптировать под свой enviroment пример Vagrantfile ниже для тестирования на разных дистибутивах.

```ruby
Vagrant.configure("2") do |config|
    boxes = [
      { :name => "ubuntu-test-box", :box => "generic/ubuntu1804" },
      { :name => "centos-test-box", :box => "generic/centos7" }
    ]
    boxes.each do |opts|
      config.vm.define opts[:name] do |config|
        config.vm.box = opts[:box]
        if opts[:name] == boxes.last[:name]
          config.vm.provision "ansible" do |ansible|
            ansible.playbook = "test.yml"
            ansible.limit = "all"
          end
        end
      end
    end
  end

```

4. Выложить получившуюся роль в публичный репозиторий, например Githib. Прислать ссылку на проверку.

## Links

- <https://developer.hashicorp.com/vagrant/docs/installation>
- <https://medium.com/@yortuc/testing-ansible-playbooks-with-vagrant-722619986013>
- <https://docs.ansible.com/ansible/latest/collections/ansible/builtin/template_module.html>
- <https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_intro.html>
- <https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_loops.html>
- <https://docs.ansible.com/ansible/latest/collections/ansible/builtin/dict_lookup.html>
- <https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_variables.html>
- <https://docs.ansible.com/ansible/latest/reference_appendices/special_variables.html>
- <https://www.codecentric.de/wissens-hub/blog/jinja2-better-ansible-playbooks-templates>
- <https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_templating.html>
- <https://docs.ansible.com/ansible/latest/collections/ansible/builtin/include_tasks_module.html#include-tasks-module>
- <https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_reuse.html#playbooks-reuse>
