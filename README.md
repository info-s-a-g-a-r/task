# task
Assignment On AWS DevOps 

1. To Host a simple application on EC2 using SSl/Let's Encrypt
   *opt Ubuntu and select the security group and open port HTTP(80) & HTTPS(443)
   *used Ubuntu OS and refresh the system's package list
   *install nginx server
     -cmd: apt install nginx -y
   *Change the directory to root directory for web server
     -cmd: cd /var/www/html
   *create index.html (write the content to display on webpage), save&exit
   *start the nginx server
     -cmd: systemctl start nginx
   *copy the <instance_ip:port> check in browser, it works
   
2. Let’s Encrypt for SSL/TLS:
   *Certbot (Let's Encrypt tool) is installed on the EC2 instance.
   *A free SSL certificate is obtained using 'Certbot with certbot certonly --nginx'

3.For LoadBalancing (Path Based Routing)
 *Create 2 microservices on ubuntu with nginx server
  -Customer
  -Order
 *Create Security Group for microservices which allows HTTP(80), HTTPS(443)
 *Now Create target group for individual microservices & Register the targets
    -customer-tg
    -order-tg
 *Create Application LoadBalancer 
   -Internet-facing
   select-VPC, Subnets
   -Routing: HTTP-80: Forward to: tg-custommer
   -Routing HTTP-80: Forward to: tg-order 
*now copy the DNS and Check in browser 
ex: <lb_DNS/customer/>
    <lb_DNS/order/>
