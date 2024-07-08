# my_iptables_cheat_sheet
it is a cheat sheet for me to review my iptables learning
# the old name of iptables was ipchain 
# iptables has 4 table 
each table defines a feature for iptables service
![image](https://github.com/ehsanDadashi/my_iptables_cheat_sheet/assets/29996315/18bcda8a-6364-44e1-b5fe-18f56639a178)
the default table for iptables service is filter.

filter : you can act like firewall service

mangle : you can limit QOS (quality Of Service)

NAT :

RAW :
# each rule in iptables named as chain
your chain can create rule on input , forward or output
![image](https://github.com/ehsanDadashi/my_iptables_cheat_sheet/assets/29996315/05244ebc-0f8b-4a06-971e-79887897fb7d)

# Iptables -t [table] CMD [chain] [rule-spec | num] -j [action]
CMD :

  -A : append command to chain ( دستور در انتهای زنجیر قرار می گیرد )
  
  -I : Insert rules in chain (دستور در ابتدای زنجیر قرار می گیرد)
  
  -D : delete a rule from chain (حذف دستور)
  
  -R : Replace a rule from chain (جایگزین کردن دستور)
  
chain :

 ( INPUT | FORWARD | OUTPUT )

(rule-spec|num):

  -p : protocol-type

  -s : source ip address

  -d : destination ip address

  -i : input interface name

  -o : output interface name

  -sport : source port number

  -dport : destination port number

Action :

  ( REJECT | DROP | ACCEPT )

# sapmle command 
    block a source ip : 
		iptables -A INPUT -s 192.168.1.100 -j DROP

    allow 80 port :
    		iptables -A INPUT -p tcp --dport 80 -j ACCEPT

    block all traffics except SSH:
    		iptables -P INPUT DROP    —---- ابتدا تمام ترافیک ورودی مسدود می گردد
    		 در واقع نو رویکرد (رفتار پیش فرض) را DROP می کند . این رفتار برای chain ها 
     		 در نظر گرفته می شود . در واقع تمام ورودی ها drop شود مگر پایینی	
    		iptables -A INPUT -p tcp --dport 22 -j ACCEPT    —--- حال پورت 22 مجاز می گردد .

