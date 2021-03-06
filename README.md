# My tools and configs

Automated installation of tools and dotfiles I use on some/all machines I have access to.

**This is work-in-progress**

Basic ideas:
- use Ansible to distribute and install tools and dotfiles.
  - this gives me the ability to use tailored configuration templates and painlessly install missing tools, all idempotently.
  - it also makes it really easy to update config "everywhere".
- use git to make everything available everywhere, and to be able to edit everything everywhere.
  - code and templates are stored safely and versioned in a publicly hosted repository.
  - wherever Ansible distributes and installs stuff, the repository is available and ready for working on it.
- have a few helper scripts to make common tasks (such as "render me this dotfile template locally on this machine right now") simple and fast.

### Installed and configured things so far

- zsh ([oh-my-zsh](http://ohmyz.sh/) with my customizations)
- tmux

### Next up

- vim with vundle and plugins
- ssh config
- git with config
- other tools: httpie, ipython, pip, virtualenv, ansible, ...


## Installation

*Recursively* clone this repository into `~/lt_tools` on your 'main machine' (or the one you'll use to distribute your configs from for the first time).

```sh
~$ git clone --recursive https://github.com/lars-tiede/lt_tools.git
```

On machines that you want to run ansible playbooks on, you need Ansible. Install it in a local Python 2.7 virtualenv like so:

```sh
$ virtualenv -p python2.7 py-env
$ ./py-env/bin/activate
$ pip install -r requirements.txt
```

If you're not me, you will want to change the inventory or make your own.


## Prerequisites on target machines

Passwordless ssh as lt\_user (see inventory) and root, from the 'control machine' (the one you run playbooks on).

On Macs: [brew](http://brew.sh/).

*(Getting rid of as many prerequisites as possible is on the TODO list)*


## Run

For now, just run playbooks directly. From within lt\_tools:

```bash
ansible-playbook -l ANSIBLE_HOST_PATTERN playbooks/PLAYBOOK
```

Substitute ANSIBLE\_HOST\_PATTERN with a [pattern](http://docs.ansible.com/intro_patterns.html) matching one or many hosts in inventory/default. *Don't forget this*.

Substitute PLAYBOOK with the playbook file you want to run.


## Tricks and often used things

Run playbook on localhost (hostname must be in inventory):
```sh
ansible-playbook -l `hostname` playbooks/PLAYBOOK
```

Update zshrc: edit roles/zsh/templates/zshrc.j2, then
```sh
ansible-playbook -l PATTERN playbooks/zsh.yml
```


## License

[MIT](LICENSE.txt)
