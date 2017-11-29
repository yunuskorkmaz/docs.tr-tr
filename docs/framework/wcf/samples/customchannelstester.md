---
title: CustomChannelsTester
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ee1fa307-98b1-4647-8860-2e9217ba6082
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2d915d567a5918060ab5e7592d4cd49384249ab9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="customchannelstester"></a>CustomChannelsTester
`CustomChannelsTester` Bir dizi önceden tanımlanmış hizmet sözleşmelerini, özel kanal uygulamaları test etmek için kullanabileceğiniz bir araçtır. Hizmet sözleşmelerini kümeyi seçin ve bir XML dosyası kullanarak aracı geçirin. Araç ardından, özel kanal uygulamaları ileti alışverişi sırasında uygular istemci ve hizmet oluşturur.  
  
### <a name="to-build-the-tool"></a>Aracı yapılandırmak için  
  
1.  Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Çözümü derledikten üç dosyaları oluşturur: CustomChannelsTester.exe, TestSpec.xml ve SampleRun.cmd. Test etmek için bu aracı kullanmak nasıl oluşturulduğunu gösteren örnek komut satırı dosya SampleRun.cmd sahip [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örnek.  
  
### <a name="to-run-the-tool"></a>Aracı çalıştırmak için  
  
-   Komut isteminde aşağıdaki komutu yazın:  
  
    ```  
    CustomChannelsTester.exe /binding:YourCustomBindngName /dll:TheAssemblyWhereThisTypeisDefined /testspec:XmlFileNameWhichContainsTestOptions  
    ```  
  
     Kullanarak `/binding` seçeneği gereklidir.  
  
     `/dll`"bağlama" tarafından sağlanan sistem tarafından sağlanan bir bağlamayı değilse gereklidir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
     `/testspec`isteğe bağlıdır.  
  
     Bu, sunucu ve istemcileri test belirtimleri ve bağlama göre oluşturur.  
  
     İstemci ve sunucu çalıştırır ve sonuçları döndürür.  
  
     Test belirtimleri (testspec.xml) açıklaması için XML örneği verilmiştir:  
  
    ```xml  
    <TestSpec xmlns="http://WCF/TestSpec" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"   
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" >  
    <ServiceContract>  
    <!-- Test a contract which has oneway / twoway operations. If you set ExpandAll = true, both types of contracts are tested -->    <IsOneWay ExpandAll="true">true</IsOneWay>  
    <!-- Test a contract with Asynchronous / Synchronous Operations-->  
        <IsAsync>false</IsAsync>   
    <!-- Test a sessionful / sessionless contract-->      
        <IsSession ExpandAll="true">true</IsSession>  
    <!-- If the Service Contract includes a CallBack Contract-->      
        <IsCallBack ExpandAll="true">true</IsCallBack>  
    </ServiceContract>  
    <TestDetails>  
    <!-- Name of the machine that runs the server - required if you want to run the test crossmachine-->  
        <ServerName>ReplaceThisWithTheServerMachineName</ServerName>  
    <!-- Port Number - Optional-->  
        <Port>8000</Port>  
    <!--URI for the callBack address for the CLient. The client will receive the messages from the server on this address in case of a CallBack Contract-->  
        <ClientCallBackAddress/>      
    <!-- Duration (in sec) after the server has started, it times out - optional(default = 300sec) -->  
        <ServerTimeout>300</ServerTimeout>  
    <!-- Duration (in sec) before the Client initializes -optional(default = 60sec) -->  
        <ClientTimeout>60</ClientTimeout>  
    <!-- Number of clients for each service - optional(default = 1) -->  
        <NumberOfClients>1</NumberOfClients>  
    <!-- Number of messages each client sends to the service - optional(default = 1) -->  
        <MessagesPerClient>1</MessagesPerClient>  
    </TestDetails>  
    </TestSpec>  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.
