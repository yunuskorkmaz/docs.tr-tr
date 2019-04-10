---
title: OperationContextScope
ms.date: 03/30/2017
ms.assetid: 11c11108-8eb4-4d49-95a0-83285a812262
ms.openlocfilehash: f48a63b1706cad3dfa8b58d84d4a2b5ef818ea92
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59212511"
---
# <a name="operationcontextscope"></a><span data-ttu-id="c44fa-102">OperationContextScope</span><span class="sxs-lookup"><span data-stu-id="c44fa-102">OperationContextScope</span></span>
<span data-ttu-id="c44fa-103">OperationContextScope örnek üst bilgileri kullanarak bir Windows Communication Foundation (WCF) arama hakkında ek bilgi gönderme işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c44fa-103">The OperationContextScope sample demonstrates how to send extra information on a Windows Communication Foundation (WCF) call using headers.</span></span> <span data-ttu-id="c44fa-104">Bu örnekte, hem sunucu hem de istemci konsol uygulamalardır.</span><span class="sxs-lookup"><span data-stu-id="c44fa-104">In this sample, both the server and client are console applications.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c44fa-105">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="c44fa-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="c44fa-106">Örnek, bir istemci ek bilgi olarak göndermek için nasıl gösterir. bir <xref:System.ServiceModel.Channels.MessageHeader> kullanarak <xref:System.ServiceModel.OperationContextScope>.</span><span class="sxs-lookup"><span data-stu-id="c44fa-106">The sample demonstrates how a client can send additional information as a <xref:System.ServiceModel.Channels.MessageHeader> using <xref:System.ServiceModel.OperationContextScope>.</span></span> <span data-ttu-id="c44fa-107">Bir <xref:System.ServiceModel.OperationContextScope> nesnesi bir kanala kapsamı tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c44fa-107">An <xref:System.ServiceModel.OperationContextScope> object is created by scoping it to a channel.</span></span> <span data-ttu-id="c44fa-108">Uzak hizmete çevrilmelidir üstbilgileri eklenebilir <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="c44fa-108">Headers that must be translated to the remote service can be added to the <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> collection.</span></span> <span data-ttu-id="c44fa-109">Bu koleksiyona eklenen üst bilgiler alınabilir hizmette erişerek <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A>.</span><span class="sxs-lookup"><span data-stu-id="c44fa-109">Headers added to this collection can be retrieved on the service by accessing <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A>.</span></span> <span data-ttu-id="c44fa-110">Kendi çağrılar üzerinde birden çok kanalda yapılır ve istemciye eklenen üstbilgileri oluşturmak için kullanılan bir kanala yalnızca geçerli <xref:System.ServiceModel.OperationContextScope>.</span><span class="sxs-lookup"><span data-stu-id="c44fa-110">Its calls are made on multiple channels and then the headers added to the client only apply to the channel that was used to create the <xref:System.ServiceModel.OperationContextScope>.</span></span>  
  
## <a name="messageheaderreader"></a><span data-ttu-id="c44fa-111">MessageHeaderReader</span><span class="sxs-lookup"><span data-stu-id="c44fa-111">MessageHeaderReader</span></span>  
 <span data-ttu-id="c44fa-112">Bu istemciden bir ileti alır ve üst bilgi aramak çalışır, örnek hizmetidir <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="c44fa-112">This is the sample service that receives a message from the client and tries to look up the header in the <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A> collection.</span></span> <span data-ttu-id="c44fa-113">İstemci üst bilgisinde gönderilen hizmet özel üst bilgi alır ve, varsa, istemci tarafından geçirilen bağımsız değişken GUID ile karşılaştırır ve GUID geçirir.</span><span class="sxs-lookup"><span data-stu-id="c44fa-113">The client passes the GUID that it sent in the header and the service retrieves the custom header and, if present, compares it with the GUID passed as the argument by the client.</span></span>  
  
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
  
## <a name="messageheaderclient"></a><span data-ttu-id="c44fa-114">MessageHeaderClient</span><span class="sxs-lookup"><span data-stu-id="c44fa-114">MessageHeaderClient</span></span>  
 <span data-ttu-id="c44fa-115">Bu tarafından oluşturulan proxy kullanan istemci uygulamasıdır [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) Uzak hizmetle iletişim kurmak için.</span><span class="sxs-lookup"><span data-stu-id="c44fa-115">This is the client implementation that uses the proxy generated by [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to communicate with the remote service.</span></span> <span data-ttu-id="c44fa-116">İlk iki proxy nesneleri oluşturur `MessageHeaderReaderClient`.</span><span class="sxs-lookup"><span data-stu-id="c44fa-116">It first creates two proxy objects of `MessageHeaderReaderClient`.</span></span>  
  
```csharp
//Create two clients to the remote service.  
MessageHeaderReaderClient client1 = new MessageHeaderReaderClient();  
MessageHeaderReaderClient client2 = new MessageHeaderReaderClient();  
```  
  
 <span data-ttu-id="c44fa-117">İstemci ardından bir OperationContextScope oluşturur ve ona kapsamlarını `client1`.</span><span class="sxs-lookup"><span data-stu-id="c44fa-117">Client then creates an OperationContextScope and scopes it to `client1`.</span></span> <span data-ttu-id="c44fa-118">Ekler bir <xref:System.ServiceModel.Channels.MessageHeader> için <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> ve her iki istemcinin bir çağrıda çağırır.</span><span class="sxs-lookup"><span data-stu-id="c44fa-118">It adds a <xref:System.ServiceModel.Channels.MessageHeader> to <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> and invokes one call on both clients.</span></span> <span data-ttu-id="c44fa-119">Üst bilgisinin gönderdiğini yalnızca sağlar `client1` değil `client2` dönüş değerini denetleyerek `RetrieveHeader` çağırın.</span><span class="sxs-lookup"><span data-stu-id="c44fa-119">It ensures that the header is sent only on `client1` and not on `client2` by checking the return value from the `RetrieveHeader` call.</span></span>  
  
```csharp
using (new OperationContextScope(client1.InnerChannel))  
{  
    //Create a new GUID that is sent as the header.  
    String guid = Guid.NewGuid().ToString();  
  
    //Create a MessageHeader for the GUID we just created.  
    MessageHeader customHeader = MessageHeader.CreateHeader(CustomHeader.HeaderName, CustomHeader.HeaderNamespace, guid);  
  
    //Add the header to the OutgoingMessageHeader collection.  
    OperationContext.Current.OutgoingMessageHeaders.Add(customHeader);  
  
    //Now call RetreieveHeader on both the proxies. Since the OperationContextScope is tied to   
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
  
 <span data-ttu-id="c44fa-120">Bu örnek kendiliğinden barındırılır.</span><span class="sxs-lookup"><span data-stu-id="c44fa-120">This sample is self-hosted.</span></span> <span data-ttu-id="c44fa-121">Örnek çalışan aşağıdaki örnek çıktıda sağlanır:</span><span class="sxs-lookup"><span data-stu-id="c44fa-121">The following sample output from running the sample is provided:</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c44fa-122">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="c44fa-122">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c44fa-123">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c44fa-123">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="c44fa-124">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c44fa-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="c44fa-125">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c44fa-125">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c44fa-126">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="c44fa-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c44fa-127">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="c44fa-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c44fa-128">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="c44fa-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c44fa-129">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="c44fa-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\OperationContextScope`  
