# GITLAB
### Omnibus GitLab restart
There may be times in the documentation where you will be asked to  _restart_  GitLab. In that case, you need to run the following command:

```
sudo gitlab-ctl restart

```

The output should be similar to this:

```
ok: run: gitlab-workhorse: (pid 11291) 1s
ok: run: logrotate: (pid 11299) 0s
ok: run: mailroom: (pid 11306) 0s
ok: run: nginx: (pid 11309) 0s
ok: run: postgresql: (pid 11316) 1s
ok: run: redis: (pid 11325) 0s
ok: run: sidekiq: (pid 11331) 1s
ok: run: unicorn: (pid 11338) 0s

```

To restart a component separately, you can append its service name to the  `restart`  command. For example, to restart  **only**  NGINX you would run:

```
sudo gitlab-ctl restart nginx

```

To check the status of GitLab services, run:

```
sudo gitlab-ctl status

```

Notice that all services say  `ok: run`.

Sometimes, components time out (look for  `timeout`  in the logs) during the restart and sometimes they get stuck. In that case, you can use  `gitlab-ctl kill <service>`  to send the  `SIGKILL`  signal to the service, for example  `sidekiq`. After that, a restart should perform fine.

As a last resort, you can try to  [reconfigure GitLab](https://docs.gitlab.com/ee/administration/restart_gitlab.html#omnibus-gitlab-reconfigure)  instead.

### Omnibus GitLab reconfigure[](https://docs.gitlab.com/ee/administration/restart_gitlab.html#omnibus-gitlab-reconfigure "Permalink")

There may be times in the documentation where you will be asked to  _reconfigure_  GitLab. Remember that this method applies only for the Omnibus packages.

Reconfigure Omnibus GitLab with:

```
sudo gitlab-ctl reconfigure

```

Reconfiguring GitLab should occur in the event that something in its configuration (`/etc/gitlab/gitlab.rb`) has changed.
