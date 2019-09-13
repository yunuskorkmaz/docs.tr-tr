---
title: CustomChannelsTester
ms.date: 03/30/2017
ms.assetid: ee1fa307-98b1-4647-8860-2e9217ba6082
ms.openlocfilehash: 0d77af319e18868ce7d600269cd9afaa0c4ce2c6
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928639"
---
# <a name="customchannelstester"></a>CustomChannelsTester
, `CustomChannelsTester` Özel kanal uygulamalarınızı önceden tanımlanmış bir hizmet sözleşmeleri kümesine karşı test etmek için kullanabileceğiniz bir araçtır. Hizmet sözleşmeleri kümesini seçebilir ve bir XML dosyası kullanarak araca geçirebilirsiniz. Araç daha sonra ileti değişimi sırasında özel kanal uygulamalarınızı uygulayan hizmeti ve istemciyi oluşturur.  
  
### <a name="to-build-the-tool"></a>Aracı oluşturmak için  
  
1. Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümündeki yönergeleri izleyin.  
  
2. Çözümün oluşturulması üç dosya üretir: CustomChannelsTester. exe, TestSpec. xml ve SampleRun. cmd. SampleRun. cmd dosyası, bu aracın [taşımayı test etmek için nasıl kullanılacağını gösteren örnek bir komut satırına sahiptir: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örneği.  
  
### <a name="to-run-the-tool"></a>Aracı çalıştırmak için  
  
- Komut isteminde aşağıdaki komutu yazın:  
  
    ```console  
    CustomChannelsTester.exe /binding:YourCustomBindngName /dll:TheAssemblyWhereThisTypeisDefined /testspec:XmlFileNameWhichContainsTestOptions  
    ```  
  
     `/binding` Seçeneğinin kullanılması gerekir.  
  
     `/dll`"Binding", Windows Communication Foundation (WCF) tarafından belirtilen sistem tarafından sağlanmış bir bağlama değilse gereklidir.  
  
     `/testspec`isteğe bağlıdır.  
  
     Bu, test belirtimlerine ve bağlamaya göre sunucu ve istemci oluşturur.  
  
     İstemcisini ve sunucuyu yürütür ve sonuçları döndürür.  
  
     Aşağıda, test belirtimleri (TestSpec. xml) açıklaması için örnek XML verilmiştir:  
  
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
