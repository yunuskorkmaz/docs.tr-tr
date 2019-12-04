---
title: SRMP
ms.date: 03/30/2017
ms.assetid: cf37078c-dcb4-45e0-acaf-2f196521b226
ms.openlocfilehash: 0ee11b67dcd9c7251df17dc7523dc20765e157c5
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716699"
---
# <a name="srmp"></a><span data-ttu-id="8d457-102">SRMP</span><span class="sxs-lookup"><span data-stu-id="8d457-102">SRMP</span></span>
<span data-ttu-id="8d457-103">Bu örnek, HTTP üzerinden Message Queuing (MSMQ) kullanılarak işlenen sıraya alınmış iletişimin nasıl gerçekleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8d457-103">This sample demonstrates how to perform transacted queued communication by using Message Queuing (MSMQ) over HTTP.</span></span>  
  
 <span data-ttu-id="8d457-104">Sıraya alınmış iletişimde istemci, hizmet ile bir kuyruk kullanarak iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="8d457-104">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="8d457-105">Daha kesin olarak, istemci iletileri bir kuyruğa gönderir.</span><span class="sxs-lookup"><span data-stu-id="8d457-105">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="8d457-106">Hizmet kuyruktaki iletileri alır.</span><span class="sxs-lookup"><span data-stu-id="8d457-106">The service receives messages from the queue.</span></span> <span data-ttu-id="8d457-107">Bu nedenle, hizmet ve istemci, bir kuyruk kullanarak iletişim kurmak için aynı anda çalışıyor olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="8d457-107">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="8d457-108">MSMQ, bir kuyruğa ileti göndermek için HTTP kullanımını (HTTPS kullanımı dahil) sağlar.</span><span class="sxs-lookup"><span data-stu-id="8d457-108">MSMQ enables the use of HTTP (including the use of HTTPS) to send messages to a queue.</span></span> <span data-ttu-id="8d457-109">Bu örnekte, Windows Communication Foundation (WCF) kuyruğa alınan iletişimin kullanımını ve HTTP üzerinden ileti gönderilmesini gösteririz.</span><span class="sxs-lookup"><span data-stu-id="8d457-109">In this example, we demonstrate using Windows Communication Foundation (WCF) queued communication and how to send messages over HTTP.</span></span> <span data-ttu-id="8d457-110">MSMQ, HTTP üzerinden iletişim için SOAP tabanlı bir protokol olan SRMP adlı bir protokol kullanır.</span><span class="sxs-lookup"><span data-stu-id="8d457-110">MSMQ uses a protocol called SRMP, which is a SOAP-based protocol for communication over HTTP.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8d457-111">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="8d457-111">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="8d457-112">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="8d457-112">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="8d457-113">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="8d457-113">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="8d457-114">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="8d457-114">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
4. <span data-ttu-id="8d457-115">**Windows Bileşenlerini Ekle/Kaldır**' da örneği çalıştırmadan önce, MSMQ 'nun http desteğiyle yüklü olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="8d457-115">Before running the sample in **Add/Remove Windows Components**, ensure that MSMQ is installed with HTTP support.</span></span> <span data-ttu-id="8d457-116">HTTP desteğinin yüklenmesi Internet Information Services (IIS) otomatik olarak yüklenir ve MSMQ için IIS 'de protokol desteğini ekler.</span><span class="sxs-lookup"><span data-stu-id="8d457-116">Installing HTTP support automatically installs Internet Information Services (IIS) and adds the protocol support in IIS for MSMQ.</span></span>  
  
5. <span data-ttu-id="8d457-117">İletişim için HTTP 'nin kullanıldığından emin olmak istiyorsanız, MSMQ 'YU güçlendirilmiş modda çalışacak şekilde etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d457-117">If you want to be certain that HTTP is used for communication, you can enable MSMQ to run in hardened mode.</span></span> <span data-ttu-id="8d457-118">Bu, makinede barındırılan herhangi bir sıraya hiçbir iletinin HTTP olmayan herhangi bir aktarımı kullanarak gelebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="8d457-118">This ensures that no messages to any queue hosted on the machine can arrive using any non-HTTP transport.</span></span>  
  
6. <span data-ttu-id="8d457-119">Sıkı modda çalıştırmak için MSMQ ' yı seçtikten sonra, makinenin [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]yeniden önyüklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="8d457-119">After you have selected MSMQ to run in hardened mode, the machine requires a re-boot on [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].</span></span>  
  
7. <span data-ttu-id="8d457-120">Hizmeti çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="8d457-120">Run the service.</span></span>  
  
8. <span data-ttu-id="8d457-121">İstemcisini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="8d457-121">Run the client.</span></span> <span data-ttu-id="8d457-122">Uç nokta adresini, localhost yerine makine adına veya IP adresine işaret etmek üzere değiştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="8d457-122">Ensure that you change the endpoint address to point to the machine name or IP address instead of localhost.</span></span> <span data-ttu-id="8d457-123">İstemci bir ileti gönderir ve çıkar.</span><span class="sxs-lookup"><span data-stu-id="8d457-123">The client sends a message and exits.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d457-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8d457-124">Requirements</span></span>  
 <span data-ttu-id="8d457-125">Bu örneği çalıştırmak için, MSMQ 'ya ek olarak hem hizmette hem de istemci makinelerde IIS yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8d457-125">To run this sample, IIS must be installed on both the service and the client machines in addition to MSMQ.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="8d457-126">Gösterir</span><span class="sxs-lookup"><span data-stu-id="8d457-126">Demonstrates</span></span>  
 <span data-ttu-id="8d457-127">Örnek, HTTP üzerinden MSMQ kullanarak WCF sıraya alınan iletileri göndermeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="8d457-127">The sample demonstrates sending WCF queued messages using MSMQ over HTTP.</span></span> <span data-ttu-id="8d457-128">Bu, SRMP mesajlaşma olarak da adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="8d457-128">This is also called SRMP messaging.</span></span> <span data-ttu-id="8d457-129">Sıraya alınan bir ileti gönderildiğinde, Gönderen makinedeki MSMQ iletileri TCP veya HTTP taşıması üzerinden alma kuyruğu Yöneticisi 'ne aktarır.</span><span class="sxs-lookup"><span data-stu-id="8d457-129">When a queued message is sent, MSMQ on the sending machine transfers the messages to the receiving queue manager over TCP or HTTP transport.</span></span> <span data-ttu-id="8d457-130">SRMP ' i seçerek Kullanıcı, kuyruk aktarımı için bir taşıma olarak HTTP seçeneğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8d457-130">By choosing SRMP, the user indicates the choice of HTTP as a transport for queue transfer.</span></span> <span data-ttu-id="8d457-131">SRMP Secure, HTTPS kullanımını sunar.</span><span class="sxs-lookup"><span data-stu-id="8d457-131">SRMP Secure enables the use of HTTPS.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d457-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="8d457-132">Example</span></span>  
 <span data-ttu-id="8d457-133">Örnek kod, işlem temelli örneğe dayalıdır.</span><span class="sxs-lookup"><span data-stu-id="8d457-133">The sample code is based on the transacted sample.</span></span> <span data-ttu-id="8d457-134">Sıradan bir ileti gönderdiğinizde ve SRMP kullanarak kuyruktan ileti aldığınızda, yerel bir protokol kullanarak ileti gönderme ve alma ile aynı olur.</span><span class="sxs-lookup"><span data-stu-id="8d457-134">How you send a message to the queue and receive a message from the queue using SRMP is the same as sending and receiving messages using a Native protocol.</span></span>  
  
 <span data-ttu-id="8d457-135">İstemci yapılandırması, sıra Aktarım protokolünün seçimini belirtecek şekilde değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="8d457-135">The configuration for the client is changed to indicate the choice of the queue transfer protocol.</span></span> <span data-ttu-id="8d457-136">Sıra Aktarım Protokolü yerel, SRMP veya SrmpSecure değerinden biri olabilir.</span><span class="sxs-lookup"><span data-stu-id="8d457-136">The queue transfer protocol can be one of Native, SRMP or SrmpSecure.</span></span> <span data-ttu-id="8d457-137">Varsayılan olarak, Aktarım Protokolü yereldir.</span><span class="sxs-lookup"><span data-stu-id="8d457-137">By default, the transfer protocol is Native.</span></span> <span data-ttu-id="8d457-138">İstemci ve hizmet, bu örnekte SRMP 'yi kullanmak için yapılandırmayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="8d457-138">The client and service specify in the configuration to use SRMP in this example.</span></span>  
  
 <span data-ttu-id="8d457-139">Aktarım güvenliği ile ilgili olarak SRMP için sınırlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="8d457-139">There are limitations to SRMP in relation to transport security.</span></span> <span data-ttu-id="8d457-140">Varsayılan MSMQ taşıma güvenliği, gönderme kuyruğu yöneticisinin ve alma kuyruğu yöneticisinin aynı Windows etki alanında bulunmasını gerektiren Active Directory gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8d457-140">The default MSMQ transport security requires Active Directory that requires that the sending queue manager and the receiving queue manager reside in the same Windows domain.</span></span> <span data-ttu-id="8d457-141">HTTP sınırı üzerinden ileti gönderilirken bu mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="8d457-141">This is not possible when sending messages over HTTP boundary.</span></span> <span data-ttu-id="8d457-142">Bu nedenle, varsayılan aktarım güvenliği çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="8d457-142">As such, the default transport security does not work.</span></span> <span data-ttu-id="8d457-143">Aktarım güvenliği isteniyorsa aktarım güvenliği sertifika olarak ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8d457-143">The transport security must be set to Certificate if transport security is desired.</span></span> <span data-ttu-id="8d457-144">İleti güvenliği, iletinin güvenliğini sağlamak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8d457-144">Message security can also be used to secure the message.</span></span> <span data-ttu-id="8d457-145">Bu örnekte, hem aktarım hem de ileti güvenliği, SRMP iletilerini göstermek için kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="8d457-145">In this sample, both transport and message security is turned off to illustrate SRMP messaging.</span></span>  
  
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
          <security mode="None" />  
        </binding>  
      </netMsmqBinding>  
    </bindings>  
  </system.serviceModel>  
  
</configuration>  
```  
  
 <span data-ttu-id="8d457-146">Örnek çalıştırmak aşağıdaki çıktıyı verir.</span><span class="sxs-lookup"><span data-stu-id="8d457-146">Running the sample yields the following output.</span></span>  
  
```console  
Processing Purchase Order: 556b70be-31ee-4a3b-8df4-ed5e538015a4   
Customer: somecustomer.com   
OrderDetails   
    Order LineItem: 54 of Blue Widget @unit price: $29.99   
    Order LineItem: 890 of Red Widget @unit price: $45.89   
    Total cost of this order: $42461.56   
    Order status: Pending  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="8d457-147">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="8d457-147">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8d457-148">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="8d457-148">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="8d457-149">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="8d457-149">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8d457-150">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="8d457-150">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\SRMP`  
