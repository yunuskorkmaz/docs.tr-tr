---
title: OperationContextScope
ms.date: 03/30/2017
ms.assetid: 11c11108-8eb4-4d49-95a0-83285a812262
ms.openlocfilehash: f3dd9c8e83b0840ff68b060889421d60b734d964
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33505150"
---
# <a name="operationcontextscope"></a><span data-ttu-id="eaced-102">OperationContextScope</span><span class="sxs-lookup"><span data-stu-id="eaced-102">OperationContextScope</span></span>
<span data-ttu-id="eaced-103">OperationContextScope örnek nasıl üstbilgileri kullanarak bir Windows Communication Foundation (WCF) çağrısı hakkında ek bilgi göndereceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="eaced-103">The OperationContextScope sample demonstrates how to send extra information on a Windows Communication Foundation (WCF) call using headers.</span></span> <span data-ttu-id="eaced-104">Bu örnekte, sunucu ve istemci, konsol uygulamalardır.</span><span class="sxs-lookup"><span data-stu-id="eaced-104">In this sample, both the server and client are console applications.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eaced-105">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="eaced-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="eaced-106">Bir istemci olarak ek bilgiler nasıl gönderebilir örnek gösterir bir <xref:System.ServiceModel.Channels.MessageHeader> kullanarak <xref:System.ServiceModel.OperationContextScope>.</span><span class="sxs-lookup"><span data-stu-id="eaced-106">The sample demonstrates how a client can send additional information as a <xref:System.ServiceModel.Channels.MessageHeader> using <xref:System.ServiceModel.OperationContextScope>.</span></span> <span data-ttu-id="eaced-107">Bir <xref:System.ServiceModel.OperationContextScope> nesnesi bir kanala kapsamı tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="eaced-107">An <xref:System.ServiceModel.OperationContextScope> object is created by scoping it to a channel.</span></span> <span data-ttu-id="eaced-108">Uzak Hizmet çevrilmelidir üstbilgileri eklenebilir <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="eaced-108">Headers that must be translated to the remote service can be added to the <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> collection.</span></span> <span data-ttu-id="eaced-109">Bu koleksiyona eklenen üstbilgileri alınabilir hizmette erişerek <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A>.</span><span class="sxs-lookup"><span data-stu-id="eaced-109">Headers added to this collection can be retrieved on the service by accessing <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A>.</span></span> <span data-ttu-id="eaced-110">Kendi çağrılar birden çok kanalları yapılır ve istemciye eklenen üstbilgileri oluşturmak için kullanılan kanalı yalnızca geçerli <xref:System.ServiceModel.OperationContextScope>.</span><span class="sxs-lookup"><span data-stu-id="eaced-110">Its calls are made on multiple channels and then the headers added to the client only apply to the channel that was used to create the <xref:System.ServiceModel.OperationContextScope>.</span></span>  
  
## <a name="messageheaderreader"></a><span data-ttu-id="eaced-111">MessageHeaderReader</span><span class="sxs-lookup"><span data-stu-id="eaced-111">MessageHeaderReader</span></span>  
 <span data-ttu-id="eaced-112">Bu, istemciden bir ileti alır ve üst bilgi aramak çalışırsa örnek hizmetidir <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="eaced-112">This is the sample service that receives a message from the client and tries to look up the header in the <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A> collection.</span></span> <span data-ttu-id="eaced-113">İstemci üstbilgisinde gönderilen ve hizmet özel üstbilgi alır ve, varsa, istemci tarafından bağımsız değişken olarak geçirilen GUID ile karşılaştırır GUID geçirir.</span><span class="sxs-lookup"><span data-stu-id="eaced-113">The client passes the GUID that it sent in the header and the service retrieves the custom header and, if present, compares it with the GUID passed as the argument by the client.</span></span>  
  
```  
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
  
## <a name="messageheaderclient"></a><span data-ttu-id="eaced-114">MessageHeaderClient</span><span class="sxs-lookup"><span data-stu-id="eaced-114">MessageHeaderClient</span></span>  
 <span data-ttu-id="eaced-115">Bu tarafından oluşturulan proxy kullanan istemci uygulamasıdır [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) uzak hizmetiyle iletişim kurmak için.</span><span class="sxs-lookup"><span data-stu-id="eaced-115">This is the client implementation that uses the proxy generated by [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to communicate with the remote service.</span></span> <span data-ttu-id="eaced-116">İlk iki proxy nesnelerin oluşturur `MessageHeaderReaderClient`.</span><span class="sxs-lookup"><span data-stu-id="eaced-116">It first creates two proxy objects of `MessageHeaderReaderClient`.</span></span>  
  
```  
//Create two clients to the remote service.  
MessageHeaderReaderClient client1 = new MessageHeaderReaderClient();  
MessageHeaderReaderClient client2 = new MessageHeaderReaderClient();  
```  
  
 <span data-ttu-id="eaced-117">İstemci ardından bir OperationContextScope oluşturur ve ona kapsamları `client1`.</span><span class="sxs-lookup"><span data-stu-id="eaced-117">Client then creates an OperationContextScope and scopes it to `client1`.</span></span> <span data-ttu-id="eaced-118">Ekler bir <xref:System.ServiceModel.Channels.MessageHeader> için <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> ve her iki istemcilerde bir çağrı çağırır.</span><span class="sxs-lookup"><span data-stu-id="eaced-118">It adds a <xref:System.ServiceModel.Channels.MessageHeader> to <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> and invokes one call on both clients.</span></span> <span data-ttu-id="eaced-119">Üstbilgi gönderilen yalnızca sağlar `client1` değil `client2` yönteminden döndürülen değer denetleyerek `RetrieveHeader` çağırın.</span><span class="sxs-lookup"><span data-stu-id="eaced-119">It ensures that the header is sent only on `client1` and not on `client2` by checking the return value from the `RetrieveHeader` call.</span></span>  
  
```  
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
  
 <span data-ttu-id="eaced-120">Bu örnek kendiliğinden barındırılır.</span><span class="sxs-lookup"><span data-stu-id="eaced-120">This sample is self-hosted.</span></span> <span data-ttu-id="eaced-121">Örnek çalışmasını aşağıdaki örnek çıkış sağlanır:</span><span class="sxs-lookup"><span data-stu-id="eaced-121">The following sample output from running the sample is provided:</span></span>  
  
```  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="eaced-122">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="eaced-122">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="eaced-123">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="eaced-123">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="eaced-124">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="eaced-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="eaced-125">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="eaced-125">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="eaced-126">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="eaced-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="eaced-127">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="eaced-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="eaced-128">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="eaced-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="eaced-129">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="eaced-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\OperationContextScope`  
  
## <a name="see-also"></a><span data-ttu-id="eaced-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="eaced-130">See Also</span></span>
