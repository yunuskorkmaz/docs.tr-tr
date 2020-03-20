---
title: OperationContextScope
ms.date: 03/30/2017
ms.assetid: 11c11108-8eb4-4d49-95a0-83285a812262
ms.openlocfilehash: ce21d9d099d893015ea828bdc3b136ab83f6d8e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183426"
---
# <a name="operationcontextscope"></a>OperationContextScope
OperationContextScope örneği, üstbilgileri kullanarak Windows Communication Foundation (WCF) araması hakkında nasıl ek bilgi gönderilebildiğini gösterir. Bu örnekte, hem sunucu hem de istemci konsol uygulamalarıdır.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 Örnek, istemcinin <xref:System.ServiceModel.Channels.MessageHeader> kullanarak <xref:System.ServiceModel.OperationContextScope>nasıl ek bilgi gönderebileceğini gösterir. Bir <xref:System.ServiceModel.OperationContextScope> nesne bir kanala kapsam alabilmek için oluşturulur. Uzak hizmete çevrilmesi gereken üstbilgi <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> koleksiyona eklenebilir. Bu koleksiyona eklenen başlıklar erişerek hizmetten <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A>alınabilir. Onun aramaları birden çok kanalda yapılır ve daha sonra istemciye eklenen üstbilgi yalnızca <xref:System.ServiceModel.OperationContextScope>oluşturmak için kullanılan kanal için geçerlidir.  
  
## <a name="messageheaderreader"></a>MessageHeaderReader  
 Bu, istemciden bir ileti alan ve <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A> koleksiyondaki üstbilgiyi aramaya çalışan örnek hizmettir. İstemci üstbilgide gönderdiği GUID'i geçer ve hizmet özel üstbilgi alır ve varsa istemci tarafından bağımsız değişken olarak geçirilen GUID ile karşılaştırır.  
  
```csharp
public bool RetrieveHeader(string guid)  
{  
     MessageHeaders messageHeaderCollection =
             OperationContext.Current.IncomingMessageHeaders;  
     String guidHeader = null;  
  
     Console.WriteLine("Trying to check if IncomingMessageHeader " +  
               " collection contains header with value {0}", guid);  
     if (messageHeaderCollection.FindHeader(  
                       CustomHeader.HeaderName,
                       CustomHeader.HeaderNamespace) != -1)  
     {  
          guidHeader = messageHeaderCollection.GetHeader<String>(  
           CustomHeader.HeaderName, CustomHeader.HeaderNamespace);  
     }  
     else  
     {  
          Console.WriteLine("No header was found");  
     }  
     if (guidHeader != null)  
     {  
          Console.WriteLine("Found header with value {0}. "+
         "Does it match with GUID sent as parameter: {1}",
          guidHeader, guidHeader.Equals(guid));  
      }  
  
      Console.WriteLine();  
      //Return true if header is present and equals the guid sent by  
      // client as argument  
      return (guidHeader != null && guidHeader.Equals(guid));  
}  
```  
  
## <a name="messageheaderclient"></a>MessageHeaderClient  
 Bu, uzak hizmetle iletişim kurmak için [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tarafından oluşturulan proxy'yi kullanan istemci uygulamasıdır. İlk olarak iki proxy nesnesi `MessageHeaderReaderClient`oluşturur.  
  
```csharp
//Create two clients to the remote service.  
MessageHeaderReaderClient client1 = new MessageHeaderReaderClient();  
MessageHeaderReaderClient client2 = new MessageHeaderReaderClient();  
```  
  
 İstemci daha sonra bir OperationContextScope `client1`oluşturur ve ''ye göre' yi . Her iki <xref:System.ServiceModel.Channels.MessageHeader> <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> istemciye de bir çağrı ekler ve çağırır. Üstbilginin, aramadan gelen iade `client1` değerini `client2` kontrol ederek yalnızca açmave açmama olarak gönderilmesini `RetrieveHeader` sağlar.  
  
```csharp
using (new OperationContextScope(client1.InnerChannel))  
{  
    //Create a new GUID that is sent as the header.  
    String guid = Guid.NewGuid().ToString();  
  
    //Create a MessageHeader for the GUID we just created.  
    MessageHeader customHeader = MessageHeader.CreateHeader(CustomHeader.HeaderName, CustomHeader.HeaderNamespace, guid);  
  
    //Add the header to the OutgoingMessageHeader collection.  
    OperationContext.Current.OutgoingMessageHeaders.Add(customHeader);  
  
    //Now call RetrieveHeader on both the proxies. Since the OperationContextScope is tied to
    //client1's InnerChannel, the header should only be added to calls made on that client.  
    //Calls made on client2 should not be sending the header across even though the call  
    //is made in the same OperationContextScope.  
    Console.WriteLine("Using client1 to send message");  
    Console.WriteLine("Did server retrieve the header? : Actual: {0}, Expected: True", client1.RetrieveHeader(guid));  
  
    Console.WriteLine();  
    Console.WriteLine("Using client2 to send message");  
    Console.WriteLine("Did server retrieve the header? : Actual: {0}, Expected: False", client2.RetrieveHeader(guid));  
}  
```  
  
 Bu örnek kendi kendine barındırılır. Numunenin çalıştırılışından elde edilen aşağıdaki örnek çıktı sağlanır:  
  
```console  
Prompt> Service.exe  
The service is ready.  
Press <ENTER> to terminate service.  
  
Trying to check if IncomingMessageHeader collection contains header with value 2239da67-546f-42d4-89dc-8eb3c06215d8  
Found header with value 2239da67-546f-42d4-89dc-8eb3c06215d8. Does it match with GUID sent as parameter: True  
  
Trying to check if IncomingMessageHeader collection contains header with value 2239da67-546f-42d4-89dc-8eb3c06215d8  
No header was found  
  
Prompt>Client.exe  
Using client1 to send message  
Did server retrieve the header? : Actual: True, Expected: True  
  
Using client2 to send message  
Did server retrieve the header? : Actual: False, Expected: False  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\OperationContextScope`  
