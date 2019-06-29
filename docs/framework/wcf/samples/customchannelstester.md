---
title: CustomChannelsTester
ms.date: 03/30/2017
ms.assetid: ee1fa307-98b1-4647-8860-2e9217ba6082
ms.openlocfilehash: 1517a2eb73da778c9b84ff857f4b8ad2b4334498
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425000"
---
# <a name="customchannelstester"></a>CustomChannelsTester
`CustomChannelsTester` Bir dizi önceden tanımlanmış hizmet sözleşmeleri, özel kanal uygulamaları test etmek için kullanabileceğiniz bir araçtır. Hizmet sözleşmeleri kümesini seçin ve bir XML dosyası kullanarak aracı geçirin. Araç ardından, özel kanal uygulamaları ileti değişimi sırasında sınayan istemci ve hizmet oluşturur.  
  
### <a name="to-build-the-tool"></a>Aracı yapılandırmak için  
  
1. Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Çözümü üç dosya oluşturur: CustomChannelsTester.exe TestSpec.xml ve SampleRun.cmd. ' % S'dosyası SampleRun.cmd test etmek için bu aracı kullanmayı gösteren bir örnek komut satırı sahip [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örnek.  
  
### <a name="to-run-the-tool"></a>Aracı çalıştırmak için  
  
- Komut isteminde aşağıdaki komutu yazın:  
  
    ```  
    CustomChannelsTester.exe /binding:YourCustomBindngName /dll:TheAssemblyWhereThisTypeisDefined /testspec:XmlFileNameWhichContainsTestOptions  
    ```  
  
     Kullanarak `/binding` seçeneği gereklidir.  
  
     `/dll` "bağlama" Windows Communication Foundation (WCF) tarafından sağlanan sistem tarafından sağlanan bir bağlamayı değilse gereklidir.  
  
     `/testspec` isteğe bağlıdır.  
  
     Bu, sunucu ve istemcileri test belirtimleri ve bağlama dayalı oluşturur.  
  
     İstemci ve sunucu çalıştırır ve sonuçları döndürür.  
  
     Örnek XML açıklaması için test belirtimleri (testspec.xml) aşağıdadır:  
  
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
    <!--URI for the callBack address for the client. The client will receive the messages from the server on this address in case of a CallBack Contract-->  
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
