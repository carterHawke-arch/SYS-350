## terraform.tfvars (redacted)

student_name = "carter"
networks     = ["devops", "internal", "web"]
corp_octet   = 11

cloud_image_path      = "/opt/images/ubuntu-cloud-srv"
win_server_image_path = "/opt/images/win2k25.qcow2"
win11_image_path      = "/opt/images/win11.qcow2"

services = {
  mysql = {
    image   = "mysql:8.0"
    network = "web"
    ports   = [{ internal = 3306, external = 3006 }]
    env = {
      MYSQL_ROOT_PASSWORD = "REDACTED"
      MYSQL_DATABASE      = "wordpress"
      MYSQL_USER          = "wpuser"
      MYSQL_PASSWORD      = "REDACTED"
    }
  }
  # ...other services, with passwords and tokens replaced by REDACTED
}

vms = {
  "carter-win-srv"    = { os = "win-server" }
  "carter-win11"      = { os = "win11" }
  "carter-ubuntu-srv" = { os = "ubuntu-server", memory_mb = 2048, vcpu = 1 }
}
