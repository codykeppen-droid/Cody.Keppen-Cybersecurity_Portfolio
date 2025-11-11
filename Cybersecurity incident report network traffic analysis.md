# Cybersecurity Incident Report: 

# Network Traffic Analysis

| Indicators that led to discovery of incident |
| :---- |
| At 1:24pm today, IT had several reports from customers that they were not able to access the company website, with an error of "destination port unreachable". |

| Investigation of incident |
| :---- |
| When using the UDP protocol from the tcpdump network analyzer tool, port 53 is unreachable. There is also a query identification number of 35084 with a flag of “A?” associated with the DNS protocol. This is based on the results of the network analysis, which show that the ICMP echo reply returned the error message: <br><br> `ICMP 203.0.113.2 udp port 53 unreachable length 254` <br><br> The port noted in the error message is used for the DNS protocol to retrieve the desired IP of the website domain. The most likely issue is an issue with the DNS, port 53.  |  

| Summary of incident and recommendations |
| :---- |
| The network analyzer tool, tcpdump was used to analyze the network for possible issues. The tcpdump returned ICMP packets with the errors of `udp port 53 unreachable` when trying to retrieve the IP address for the client domain from the DNS server. There appears to be an issue with the client DNS that is resulting in the IP address not returning. Thus not allowing a connection to the website domain for the customers. <br><br> The DNS server may need to be reviewed, as there could be an issue, including a DoS attack, that will need to be resolved. |
