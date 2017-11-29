---
title: SRMP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf37078c-dcb4-45e0-acaf-2f196521b226
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d42c6f19091703242a730cb40495cfb073631682
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="srmp"></a><span data-ttu-id="de434-102">SRMP</span><span class="sxs-lookup"><span data-stu-id="de434-102">SRMP</span></span>
<span data-ttu-id="de434-103">Bu örnek, HTTP üzerinden Message Queuing (MSMQ) kullanarak hizmetteki kuyruğa alınan iletişim gerçekleştirmek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="de434-103">This sample demonstrates how to perform transacted queued communication by using Message Queuing (MSMQ) over HTTP.</span></span>  
  
 <span data-ttu-id="de434-104">Kuyruğa alınan iletişim, istemci bir sıra kullanarak hizmeti ile iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="de434-104">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="de434-105">Daha hassas bir şekilde istemci kuyruğa ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="de434-105">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="de434-106">Hizmet kuyruktan iletileri alır.</span><span class="sxs-lookup"><span data-stu-id="de434-106">The service receives messages from the queue.</span></span> <span data-ttu-id="de434-107">Hizmet ve istemci bu nedenle, bir sıra kullanarak iletişim kurmak için aynı anda çalışıyor olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="de434-107">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="de434-108">MSMQ HTTP (HTTPS kullanımı dahil) kullanımını kuyruğa ileti göndermek için etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="de434-108">MSMQ enables the use of HTTP (including the use of HTTPS) to send messages to a queue.</span></span> <span data-ttu-id="de434-109">Bu örnekte, biz kullanarak göstermek [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] iletişim ve HTTP üzerinden ileti göndermek nasıl sıraya alındı.</span><span class="sxs-lookup"><span data-stu-id="de434-109">In this example, we demonstrate using [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] queued communication and how to send messages over HTTP.</span></span> <span data-ttu-id="de434-110">MSMQ SRMP, HTTP üzerinden iletişim için SOAP tabanlı bir protokol olan adlı bir protokolünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="de434-110">MSMQ uses a protocol called SRMP, which is a SOAP-based protocol for communication over HTTP.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="de434-111">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="de434-111">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="de434-112">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="de434-112">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="de434-113">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="de434-113">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="de434-114">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="de434-114">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="de434-115">Örneği çalıştırmadan önce **Windows Bileşenlerini Ekle/Kaldır**, MSMQ yüklü olduğundan emin olun HTTP desteği.</span><span class="sxs-lookup"><span data-stu-id="de434-115">Before running the sample in **Add/Remove Windows Components**, ensure that MSMQ is installed with HTTP support.</span></span> <span data-ttu-id="de434-116">HTTP desteği otomatik olarak yükleme Internet Information Services (IIS) yükler ve protokol desteği için MSMQ IIS'de ekler.</span><span class="sxs-lookup"><span data-stu-id="de434-116">Installing HTTP support automatically installs Internet Information Services (IIS) and adds the protocol support in IIS for MSMQ.</span></span>  
  
5.  <span data-ttu-id="de434-117">HTTP iletişimi için kullanılan emin olmak istiyorsanız, sağlamlaştırılmış modda çalıştırmak MSMQ etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="de434-117">If you want to be certain that HTTP is used for communication, you can enable MSMQ to run in hardened mode.</span></span> <span data-ttu-id="de434-118">Bu makinede barındırılan herhangi bir sıra hiçbir iletileri herhangi bir HTTP olmayan aktarım kullanarak gelmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="de434-118">This ensures that no messages to any queue hosted on the machine can arrive using any non-HTTP transport.</span></span>  
  
6.  <span data-ttu-id="de434-119">Sağlamlaştırılmış modda çalıştırmak için MSMQ seçtikten sonra makinenin yeniden önyükleme gerektiriyorsa [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].</span><span class="sxs-lookup"><span data-stu-id="de434-119">After you have selected MSMQ to run in hardened mode, the machine requires a re-boot on [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].</span></span>  
  
7.  <span data-ttu-id="de434-120">Hizmet çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="de434-120">Run the service.</span></span>  
  
8.  <span data-ttu-id="de434-121">İstemciyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="de434-121">Run the client.</span></span> <span data-ttu-id="de434-122">Makine adı işaret edecek şekilde uç noktası adresi veya IP adresi localhost yerine değiştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="de434-122">Ensure that you change the endpoint address to point to the machine name or IP address instead of localhost.</span></span> <span data-ttu-id="de434-123">İstemci bir ileti gönderir ve çıkar.</span><span class="sxs-lookup"><span data-stu-id="de434-123">The client sends a message and exits.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de434-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="de434-124">Requirements</span></span>  
 <span data-ttu-id="de434-125">Bu örneği çalıştırmak için IIS hem hizmet hem de istemci makinelere MSMQ yanı sıra yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="de434-125">To run this sample, IIS must be installed on both the service and the client machines in addition to MSMQ.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="de434-126">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="de434-126">Demonstrates</span></span>  
 <span data-ttu-id="de434-127">Örnek gönderme gösterir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] MSMQ HTTP üzerinden kullanarak sıradaki iletiler.</span><span class="sxs-lookup"><span data-stu-id="de434-127">The sample demonstrates sending [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] queued messages using MSMQ over HTTP.</span></span> <span data-ttu-id="de434-128">Bu, SRMP Mesajlaşma olarak da adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="de434-128">This is also called SRMP messaging.</span></span> <span data-ttu-id="de434-129">Ne zaman bir Sıraya alınan iletinin gönderildiği, MSMQ alıcı sıra yöneticisine TCP veya HTTP taşıması üzerinden gönderme makine aktarımları iletileri üzerinde.</span><span class="sxs-lookup"><span data-stu-id="de434-129">When a queued message is sent, MSMQ on the sending machine transfers the messages to the receiving queue manager over TCP or HTTP transport.</span></span> <span data-ttu-id="de434-130">SRMP seçerek kullanıcı HTTP seçimi sıra aktarımı için bir taşıma olarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="de434-130">By choosing SRMP, the user indicates the choice of HTTP as a transport for queue transfer.</span></span> <span data-ttu-id="de434-131">SRMP güvenli HTTPS kullanımını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="de434-131">SRMP Secure enables the use of HTTPS.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de434-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="de434-132">Example</span></span>  
 <span data-ttu-id="de434-133">Örnek kod hizmetteki örnek üzerinde temel alır.</span><span class="sxs-lookup"><span data-stu-id="de434-133">The sample code is based on the transacted sample.</span></span> <span data-ttu-id="de434-134">Nasıl kuyruğa ileti gönderme ve SRMP kullanarak kuyruktan ileti alma yerel protokolünü kullanarak ileti gönderme ve alma ile aynı olur.</span><span class="sxs-lookup"><span data-stu-id="de434-134">How you send a message to the queue and receive a message from the queue using SRMP is the same as sending and receiving messages using a Native protocol.</span></span>  
  
 <span data-ttu-id="de434-135">Sıra Aktarım Protokolü seçimi belirtmek için istemci yapılandırmasını değiştirdi.</span><span class="sxs-lookup"><span data-stu-id="de434-135">The configuration for the client is changed to indicate the choice of the queue transfer protocol.</span></span> <span data-ttu-id="de434-136">Sıra Aktarım Protokolü yerel, SRMP ya da SrmpSecure biri olabilir.</span><span class="sxs-lookup"><span data-stu-id="de434-136">The queue transfer protocol can be one of Native, SRMP or SrmpSecure.</span></span> <span data-ttu-id="de434-137">Varsayılan olarak, yerel aktarım protokolüdür.</span><span class="sxs-lookup"><span data-stu-id="de434-137">By default, the transfer protocol is Native.</span></span> <span data-ttu-id="de434-138">Bu örnekte SRMP kullanmak üzere yapılandırma istemci ve hizmet belirtin.</span><span class="sxs-lookup"><span data-stu-id="de434-138">The client and service specify in the configuration to use SRMP in this example.</span></span>  
  
 <span data-ttu-id="de434-139">Taşıma güvenliği ile ilgili olarak SRMP sınırlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="de434-139">There are limitations to SRMP in relation to transport security.</span></span> <span data-ttu-id="de434-140">Varsayılan MSMQ taşıma güvenliği gönderme sırası Yöneticisi ve alıcı sırası aynı Windows etki alanında bulunan gerektirir Active Directory gerektirir.</span><span class="sxs-lookup"><span data-stu-id="de434-140">The default MSMQ transport security requires Active Directory that requires that the sending queue manager and the receiving queue manager reside in the same Windows domain.</span></span> <span data-ttu-id="de434-141">Bu iletileri HTTP sınırından gönderirken mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="de434-141">This is not possible when sending messages over HTTP boundary.</span></span> <span data-ttu-id="de434-142">Bu nedenle, varsayılan taşıma güvenliği çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="de434-142">As such, the default transport security does not work.</span></span> <span data-ttu-id="de434-143">Taşıma güvenliği isterseniz taşıma güvenliği için sertifika ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="de434-143">The transport security must be set to Certificate if transport security is desired.</span></span> <span data-ttu-id="de434-144">İleti güvenliği, ileti güvenliğini sağlamak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="de434-144">Message security can also be used to secure the message.</span></span> <span data-ttu-id="de434-145">Bu örnekte, taşıma ve ileti güvenliği SRMP Mesajlaşma göstermeye kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="de434-145">In this sample, both transport and message security is turned off to illustrate SRMP messaging.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  
  <system.serviceModel>  
  
    <client>  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint name="OrderProcessorEndpoint"  
           address=  
          "net.msmq://localhost/private/ServiceModelSamplesSrmp"   
           bindingConfiguration="srmpBinding"   
           binding="netMsmqBinding"   
           contract="IOrderProcessor" />  
    </client>  
    <bindings>  
      <netMsmqBinding>  
        <binding name="srmpBinding"  
                 queueTransferProtocol="Srmp">  
          <security mode="None"></security>  
        </binding>  
      </netMsmqBinding>  
    </bindings>  
  </system.serviceModel>  
  
</configuration>  
```  
  
 <span data-ttu-id="de434-146">Örnek çalıştıran şu çıkışı üretir.</span><span class="sxs-lookup"><span data-stu-id="de434-146">Running the sample yields the following output.</span></span>  
  
```  
Processing Purchase Order: 556b70be-31ee-4a3b-8df4-ed5e538015a4   
Customer: somecustomer.com   
OrderDetails   
    Order LineItem: 54 of Blue Widget @unit price: $29.99   
    Order LineItem: 890 of Red Widget @unit price: $45.89   
    Total cost of this order: $42461.56   
    Order status: Pending  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="de434-147">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="de434-147">The samples may already be installed on your machine.</span></span> <span data-ttu-id="de434-148">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="de434-148">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="de434-149">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="de434-149">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="de434-150">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="de434-150">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\SRMP`  
  
## <a name="see-also"></a><span data-ttu-id="de434-151">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="de434-151">See Also</span></span>
