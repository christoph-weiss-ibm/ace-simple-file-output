# SimpleFileOutput

Einfaches Projekt um das Handling und die Ausgabe von Umlaute zu testen. 

Das Projekt besteht aus einem Flow mit einem Compute und FileOutput Node.  

Im Compute Node wird die Property `dynamicText` als Response gesetzt. Die Reponse wird einerseits als HTTP Reponse, sowie als Datei ausgegeben. 

## Schritte für Verprobung 

**1. Setzen der Werte in der simpleflow.properties Datei** 

``` 
SimpleFileOutput#dynamicText=von der Property äöü
SimpleFileOutput#outputDirectory=/tmp
```

**2. Deploy und Overwrite der Anwendung**
Beispiel: 
```
ibmint deploy --input-bar-file ~/files/SimpleFileOutputproject.TestMode.bar --output-node TestNode --output-server TestServer --overrides-file /home/ace/files/simpleflow.properties --restart-all-applications
```

**3. Aufruf/Test der Anwendung** 
Beispiel (Server ist entsprechend anzupassen):
```
[ace@prunella1 files]$  curl -vv http://prunella1.fyre.ibm.com:7800/Transformation_ESQL
*   Trying 10.11.116.79...
* TCP_NODELAY set
* Connected to prunella1.fyre.ibm.com (10.11.116.79) port 7800 (#0)
> GET /Transformation_ESQL HTTP/1.1
> Host: prunella1.fyre.ibm.com:7800
> User-Agent: curl/7.61.1
> Accept: */*
>
< HTTP/1.1 200 OK
< Content-Type: text/xml;charset=utf-8
< Server: IBM App Connect Enterprise
< Date: Mon, 08 Jan 2024 13:29:59 GMT
< Content-Length: 57
<
* Connection #0 to host prunella1.fyre.ibm.com left intact
<Response><Text>von der Property äöü</Text></Response>
```



