### spfinal solution

***
* Name: Issatay Sultanbekuly
* Email: 180107039@sdu.stu.edu.kz
* Variant: [15](../variants/variant15.md)
* Solution: [./top](./top)
***

First step 
By the task I have to find top 5 unique hosts ,which code starts with 3 ,that were redirected by the server.

I have counted the field of hosts and code by the structure.So host is 1st field (-1$) and code is in 9th field (-9$).

**z=$(awk '{print $1,$9}' $2 | grep '3..$' | cut -d' ' -f1 | sort | uniq -c | sort -n -r | head -$1 | awk '{sum+=$1}END{print sum}')**

I have started with script awk.Printed 1st and 9th field,where second field from this (9th) should be code starting with 3. So to find this from 2nd field I've used [grep '3..$'],which returns me host with only ones that code starts with 3. Sorted by order,counted which ones repeated (uniq -c) , sorted by number by reverse (sort -n -r) for starting with highest numbers.Sum of these repeated numbers i've assigned to the new variable 'z'.

z variable is the total nuber of repeated hosts.

**awk '{print $1,$9}' $2 | grep '3..$' | cut -d' ' -f1 | sort | uniq -c | sort -n -r | head -$1| awk '{print NR". "$2" - "$1" - " sprintf("%.1f" ,$1/'"$z"*100') "%"}' **

First part is same,to sort the information that we need.Second part is to print by list order (NR) separated by dot, second field (host),hyphen (-) ,number of repeated redirections,hyphen,first field divided by total and multiplied to 100 to get percentage.Rounded by sprintf("%.1f") function ,to get needed format of floating numbers.And the percentage sign ("%").


