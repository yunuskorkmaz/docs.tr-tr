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
# <a name="operationcontextscope"></a><span data-ttu-id="a511f-102">OperationContextScope</span><span class="sxs-lookup"><span data-stu-id="a511f-102">OperationContextScope</span></span>
<span data-ttu-id="a511f-103">OperationContextScope örneği, üstbilgileri kullanarak Windows Communication Foundation (WCF) araması hakkında nasıl ek bilgi gönderilebildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a511f-103">The OperationContextScope sample demonstrates how to send extra information on a Windows Communication Foundation (WCF) call using headers.</span></span> <span data-ttu-id="a511f-104">Bu örnekte, hem sunucu hem de istemci konsol uygulamalarıdır.</span><span class="sxs-lookup"><span data-stu-id="a511f-104">In this sample, both the server and client are console applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a511f-105">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="a511f-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="a511f-106">Örnek, istemcinin <xref:System.ServiceModel.Channels.MessageHeader> kullanarak <xref:System.ServiceModel.OperationContextScope>nasıl ek bilgi gönderebileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a511f-106">The sample demonstrates how a client can send additional information as a <xref:System.ServiceModel.Channels.MessageHeader> using <xref:System.ServiceModel.OperationContextScope>.</span></span> <span data-ttu-id="a511f-107">Bir <xref:System.ServiceModel.OperationContextScope> nesne bir kanala kapsam alabilmek için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a511f-107">An <xref:System.ServiceModel.OperationContextScope> object is created by scoping it to a channel.</span></span> <span data-ttu-id="a511f-108">Uzak hizmete çevrilmesi gereken üstbilgi <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> koleksiyona eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="a511f-108">Headers that must be translated to the remote service can be added to the <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> collection.</span></span> <span data-ttu-id="a511f-109">Bu koleksiyona eklenen başlıklar erişerek hizmetten <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A>alınabilir.</span><span class="sxs-lookup"><span data-stu-id="a511f-109">Headers added to this collection can be retrieved on the service by accessing <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A>.</span></span> <span data-ttu-id="a511f-110">Onun aramaları birden çok kanalda yapılır ve daha sonra istemciye eklenen üstbilgi yalnızca <xref:System.ServiceModel.OperationContextScope>oluşturmak için kullanılan kanal için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a511f-110">Its calls are made on multiple channels and then the headers added to the client only apply to the channel that was used to create the <xref:System.ServiceModel.OperationContextScope>.</span></span>  
  
## <a name="messageheaderreader"></a><span data-ttu-id="a511f-111">MessageHeaderReader</span><span class="sxs-lookup"><span data-stu-id="a511f-111">MessageHeaderReader</span></span>  
 <span data-ttu-id="a511f-112">Bu, istemciden bir ileti alan ve <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A> koleksiyondaki üstbilgiyi aramaya çalışan örnek hizmettir.</span><span class="sxs-lookup"><span data-stu-id="a511f-112">This is the sample service that receives a message from the client and tries to look up the header in the <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A> collection.</span></span> <span data-ttu-id="a511f-113">İstemci üstbilgide gönderdiği GUID'i geçer ve hizmet özel üstbilgi alır ve varsa istemci tarafından bağımsız değişken olarak geçirilen GUID ile karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="a511f-113">The client passes the GUID that it sent in the header and the service retrieves the custom header and, if present, compares it with the GUID passed as the argument by the client.</span></span>  
  
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
  
## <a name="messageheaderclient"></a><span data-ttu-id="a511f-114">MessageHeaderClient</span><span class="sxs-lookup"><span data-stu-id="a511f-114">MessageHeaderClient</span></span>  
 <span data-ttu-id="a511f-115">Bu, uzak hizmetle iletişim kurmak için [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tarafından oluşturulan proxy'yi kullanan istemci uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="a511f-115">This is the client implementation that uses the proxy generated by [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to communicate with the remote service.</span></span> <span data-ttu-id="a511f-116">İlk olarak iki proxy nesnesi `MessageHeaderReaderClient`oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a511f-116">It first creates two proxy objects of `MessageHeaderReaderClient`.</span></span>  
  
```csharp
//Create two clients to the remote service.  
MessageHeaderReaderClient client1 = new MessageHeaderReaderClient();  
MessageHeaderReaderClient client2 = new MessageHeaderReaderClient();  
```  
  
 <span data-ttu-id="a511f-117">İstemci daha sonra bir OperationContextScope `client1`oluşturur ve ''ye göre' yi .</span><span class="sxs-lookup"><span data-stu-id="a511f-117">Client then creates an OperationContextScope and scopes it to `client1`.</span></span> <span data-ttu-id="a511f-118">Her iki <xref:System.ServiceModel.Channels.MessageHeader> <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> istemciye de bir çağrı ekler ve çağırır.</span><span class="sxs-lookup"><span data-stu-id="a511f-118">It adds a <xref:System.ServiceModel.Channels.MessageHeader> to <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> and invokes one call on both clients.</span></span> <span data-ttu-id="a511f-119">Üstbilginin, aramadan gelen iade `client1` değerini `client2` kontrol ederek yalnızca açmave açmama olarak gönderilmesini `RetrieveHeader` sağlar.</span><span class="sxs-lookup"><span data-stu-id="a511f-119">It ensures that the header is sent only on `client1` and not on `client2` by checking the return value from the `RetrieveHeader` call.</span></span>  
  
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
  
 <span data-ttu-id="a511f-120">Bu örnek kendi kendine barındırılır.</span><span class="sxs-lookup"><span data-stu-id="a511f-120">This sample is self-hosted.</span></span> <span data-ttu-id="a511f-121">Numunenin çalıştırılışından elde edilen aşağıdaki örnek çıktı sağlanır:</span><span class="sxs-lookup"><span data-stu-id="a511f-121">The following sample output from running the sample is provided:</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a511f-122">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="a511f-122">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="a511f-123">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="a511f-123">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="a511f-124">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="a511f-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="a511f-125">Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="a511f-125">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a511f-126">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="a511f-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a511f-127">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="a511f-127">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="a511f-128">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="a511f-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a511f-129">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="a511f-129">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\OperationContextScope`  
