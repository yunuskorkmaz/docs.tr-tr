---
title: OperationContextScope
ms.date: 03/30/2017
ms.assetid: 11c11108-8eb4-4d49-95a0-83285a812262
ms.openlocfilehash: 0b2b4d9b22f654fa433c7473160444b41a5adfa4
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575164"
---
# <a name="operationcontextscope"></a><span data-ttu-id="402f9-102">OperationContextScope</span><span class="sxs-lookup"><span data-stu-id="402f9-102">OperationContextScope</span></span>
<span data-ttu-id="402f9-103">OperationContextScope örneği, üst bilgiler kullanılarak Windows Communication Foundation (WCF) çağrısıyla nasıl ek bilgi gönderileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="402f9-103">The OperationContextScope sample demonstrates how to send extra information on a Windows Communication Foundation (WCF) call using headers.</span></span> <span data-ttu-id="402f9-104">Bu örnekte, hem sunucu hem de istemci konsol uygulamalardır.</span><span class="sxs-lookup"><span data-stu-id="402f9-104">In this sample, both the server and client are console applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="402f9-105">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="402f9-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="402f9-106">Örnek, bir istemcinin kullanarak nasıl ek bilgi gönderebileceğinizi gösterir <xref:System.ServiceModel.Channels.MessageHeader> <xref:System.ServiceModel.OperationContextScope> .</span><span class="sxs-lookup"><span data-stu-id="402f9-106">The sample demonstrates how a client can send additional information as a <xref:System.ServiceModel.Channels.MessageHeader> using <xref:System.ServiceModel.OperationContextScope>.</span></span> <span data-ttu-id="402f9-107">Bir <xref:System.ServiceModel.OperationContextScope> nesne, bir kanalda tanımlayarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="402f9-107">An <xref:System.ServiceModel.OperationContextScope> object is created by scoping it to a channel.</span></span> <span data-ttu-id="402f9-108">Uzak hizmete çevrilmesi gereken üstbilgiler <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> koleksiyona eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="402f9-108">Headers that must be translated to the remote service can be added to the <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> collection.</span></span> <span data-ttu-id="402f9-109">Bu koleksiyona eklenen üst bilgiler, hizmetine erişerek hizmetten alınabilir <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A> .</span><span class="sxs-lookup"><span data-stu-id="402f9-109">Headers added to this collection can be retrieved on the service by accessing <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A>.</span></span> <span data-ttu-id="402f9-110">Çağrıları birden çok kanalda yapılır ve ardından istemciye eklenen üstbilgiler yalnızca oluşturmak için kullanılan kanala uygulanır <xref:System.ServiceModel.OperationContextScope> .</span><span class="sxs-lookup"><span data-stu-id="402f9-110">Its calls are made on multiple channels and then the headers added to the client only apply to the channel that was used to create the <xref:System.ServiceModel.OperationContextScope>.</span></span>  
  
## <a name="messageheaderreader"></a><span data-ttu-id="402f9-111">MessageHeaderReader</span><span class="sxs-lookup"><span data-stu-id="402f9-111">MessageHeaderReader</span></span>  
 <span data-ttu-id="402f9-112">Bu, istemciden bir ileti alan ve koleksiyondaki üstbilgiyi aramaya çalışan örnek hizmettir <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A> .</span><span class="sxs-lookup"><span data-stu-id="402f9-112">This is the sample service that receives a message from the client and tries to look up the header in the <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A> collection.</span></span> <span data-ttu-id="402f9-113">İstemci, üst bilgiyle gönderilen GUID 'YI geçirir ve hizmet özel üstbilgiyi alır ve varsa, bunu istemci tarafından bağımsız değişken olarak geçirilen GUID ile karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="402f9-113">The client passes the GUID that it sent in the header and the service retrieves the custom header and, if present, compares it with the GUID passed as the argument by the client.</span></span>  
  
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
  
## <a name="messageheaderclient"></a><span data-ttu-id="402f9-114">MessageHeaderClient</span><span class="sxs-lookup"><span data-stu-id="402f9-114">MessageHeaderClient</span></span>  
 <span data-ttu-id="402f9-115">Bu, uzak hizmetle iletişim kurmak için [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) tarafından oluşturulan proxy 'yi kullanan istemci uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="402f9-115">This is the client implementation that uses the proxy generated by [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to communicate with the remote service.</span></span> <span data-ttu-id="402f9-116">İlk olarak iki proxy nesnesi oluşturur `MessageHeaderReaderClient` .</span><span class="sxs-lookup"><span data-stu-id="402f9-116">It first creates two proxy objects of `MessageHeaderReaderClient`.</span></span>  
  
```csharp
//Create two clients to the remote service.  
MessageHeaderReaderClient client1 = new MessageHeaderReaderClient();  
MessageHeaderReaderClient client2 = new MessageHeaderReaderClient();  
```  
  
 <span data-ttu-id="402f9-117">İstemci daha sonra bir OperationContextScope oluşturur ve bunu ile kapsamlar `client1` .</span><span class="sxs-lookup"><span data-stu-id="402f9-117">Client then creates an OperationContextScope and scopes it to `client1`.</span></span> <span data-ttu-id="402f9-118"><xref:System.ServiceModel.Channels.MessageHeader> <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> Her iki istemcide bir çağrı ekler ve çağırır.</span><span class="sxs-lookup"><span data-stu-id="402f9-118">It adds a <xref:System.ServiceModel.Channels.MessageHeader> to <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> and invokes one call on both clients.</span></span> <span data-ttu-id="402f9-119">`client1` `client2` Çağrının dönüş değeri denetleyerek, üstbilginin yalnızca üzerinde gönderilmesini sağlar `RetrieveHeader` .</span><span class="sxs-lookup"><span data-stu-id="402f9-119">It ensures that the header is sent only on `client1` and not on `client2` by checking the return value from the `RetrieveHeader` call.</span></span>  
  
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
  
 <span data-ttu-id="402f9-120">Bu örnek kendi kendine barındırılır.</span><span class="sxs-lookup"><span data-stu-id="402f9-120">This sample is self-hosted.</span></span> <span data-ttu-id="402f9-121">Örnek çalıştırmanın aşağıdaki örnek çıktısı verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="402f9-121">The following sample output from running the sample is provided:</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="402f9-122">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="402f9-122">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="402f9-123">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="402f9-123">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="402f9-124">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="402f9-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="402f9-125">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="402f9-125">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="402f9-126">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="402f9-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="402f9-127">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="402f9-127">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="402f9-128">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="402f9-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="402f9-129">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="402f9-129">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\OperationContextScope`  
