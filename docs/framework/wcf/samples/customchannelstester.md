---
title: CustomChannelsTester
ms.date: 03/30/2017
ms.assetid: ee1fa307-98b1-4647-8860-2e9217ba6082
ms.openlocfilehash: c23bd3eddd49972b7083347fed88d4e70707ae58
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183806"
---
# <a name="customchannelstester"></a>CustomChannelsTester
Özel `CustomChannelsTester` kanal uygulamalarınızı önceden tanımlanmış hizmet sözleşmeleri kümesine karşı sınamak için kullanabileceğiniz bir araçtır. Hizmet sözleşmeleri kümesini seçebilir ve bir XML dosyasını kullanarak araca aktarabilirsiniz. Araç daha sonra ileti alışverişi sırasında özel kanal uygulamaları egzersizhizmeti ve istemci oluşturur.  
  
### <a name="to-build-the-tool"></a>Aracı oluşturmak için  
  
1. Çözümü oluşturmak için, Windows [Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
2. Çözümü oluşturmak üç dosya oluşturur: CustomChannelsTester.exe, TestSpec.xml ve SampleRun.cmd. SampleRun.cmd [dosyasında, Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örneğini test etmek için bu aracın nasıl kullanılacağını gösteren bir örnek komut satırı vardır.  
  
### <a name="to-run-the-tool"></a>Aracı çalıştırmak için  
  
- Komut istemi'nde aşağıdaki komutu yazın:  
  
    ```console  
    CustomChannelsTester.exe /binding:YourCustomBindngName /dll:TheAssemblyWhereThisTypeisDefined /testspec:XmlFileNameWhichContainsTestOptions  
    ```  
  
     Seçeneğin `/binding` kullanılması gereklidir.  
  
     `/dll`Windows Communication Foundation (WCF) tarafından sağlanan sistem tarafından sağlanan bir bağlama değilse gereklidir.  
  
     `/testspec` isteğe bağlıdır.  
  
     Bu, test belirtimlerine ve bağlamaya dayalı olarak sunucu ve istemciler oluşturur.  
  
     İstemciyi ve sunucuyu yürütür ve sonuçları döndürür.  
  
     Test özelliklerinin (testspec.xml) açıklaması için örnek XML aşağıdavetvelmiyeaşağıdakileri belirteçtir:  
  
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
