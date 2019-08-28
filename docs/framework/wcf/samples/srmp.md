---
title: SRMP
ms.date: 03/30/2017
ms.assetid: cf37078c-dcb4-45e0-acaf-2f196521b226
ms.openlocfilehash: e3015e7185fd52a1161b91c74dee57f694fbeebd
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044709"
---
# <a name="srmp"></a><span data-ttu-id="96ba3-102">SRMP</span><span class="sxs-lookup"><span data-stu-id="96ba3-102">SRMP</span></span>
<span data-ttu-id="96ba3-103">Bu örnek, HTTP üzerinden Message Queuing (MSMQ) kullanılarak işlenen sıraya alınmış iletişimin nasıl gerçekleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="96ba3-103">This sample demonstrates how to perform transacted queued communication by using Message Queuing (MSMQ) over HTTP.</span></span>  
  
 <span data-ttu-id="96ba3-104">Sıraya alınmış iletişimde istemci, hizmet ile bir kuyruk kullanarak iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="96ba3-104">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="96ba3-105">Daha kesin olarak, istemci iletileri bir kuyruğa gönderir.</span><span class="sxs-lookup"><span data-stu-id="96ba3-105">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="96ba3-106">Hizmet kuyruktaki iletileri alır.</span><span class="sxs-lookup"><span data-stu-id="96ba3-106">The service receives messages from the queue.</span></span> <span data-ttu-id="96ba3-107">Bu nedenle, hizmet ve istemci, bir kuyruk kullanarak iletişim kurmak için aynı anda çalışıyor olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="96ba3-107">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="96ba3-108">MSMQ, bir kuyruğa ileti göndermek için HTTP kullanımını (HTTPS kullanımı dahil) sağlar.</span><span class="sxs-lookup"><span data-stu-id="96ba3-108">MSMQ enables the use of HTTP (including the use of HTTPS) to send messages to a queue.</span></span> <span data-ttu-id="96ba3-109">Bu örnekte, Windows Communication Foundation (WCF) kuyruğa alınan iletişimin kullanımını ve HTTP üzerinden ileti gönderilmesini gösteririz.</span><span class="sxs-lookup"><span data-stu-id="96ba3-109">In this example, we demonstrate using Windows Communication Foundation (WCF) queued communication and how to send messages over HTTP.</span></span> <span data-ttu-id="96ba3-110">MSMQ, HTTP üzerinden iletişim için SOAP tabanlı bir protokol olan SRMP adlı bir protokol kullanır.</span><span class="sxs-lookup"><span data-stu-id="96ba3-110">MSMQ uses a protocol called SRMP, which is a SOAP-based protocol for communication over HTTP.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="96ba3-111">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="96ba3-111">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="96ba3-112">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="96ba3-112">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="96ba3-113">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="96ba3-113">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="96ba3-114">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="96ba3-114">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
4. <span data-ttu-id="96ba3-115">**Windows Bileşenlerini Ekle/Kaldır**' da örneği çalıştırmadan önce, MSMQ 'nun http desteğiyle yüklü olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="96ba3-115">Before running the sample in **Add/Remove Windows Components**, ensure that MSMQ is installed with HTTP support.</span></span> <span data-ttu-id="96ba3-116">HTTP desteğinin yüklenmesi Internet Information Services (IIS) otomatik olarak yüklenir ve MSMQ için IIS 'de protokol desteğini ekler.</span><span class="sxs-lookup"><span data-stu-id="96ba3-116">Installing HTTP support automatically installs Internet Information Services (IIS) and adds the protocol support in IIS for MSMQ.</span></span>  
  
5. <span data-ttu-id="96ba3-117">İletişim için HTTP 'nin kullanıldığından emin olmak istiyorsanız, MSMQ 'YU güçlendirilmiş modda çalışacak şekilde etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="96ba3-117">If you want to be certain that HTTP is used for communication, you can enable MSMQ to run in hardened mode.</span></span> <span data-ttu-id="96ba3-118">Bu, makinede barındırılan herhangi bir sıraya hiçbir iletinin HTTP olmayan herhangi bir aktarımı kullanarak gelebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="96ba3-118">This ensures that no messages to any queue hosted on the machine can arrive using any non-HTTP transport.</span></span>  
  
6. <span data-ttu-id="96ba3-119">Sağlamlaştırılmış modda çalıştırmak için MSMQ ' yı seçtikten sonra, makine üzerinde [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]yeniden önyükleme gerektirir.</span><span class="sxs-lookup"><span data-stu-id="96ba3-119">After you have selected MSMQ to run in hardened mode, the machine requires a re-boot on [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].</span></span>  
  
7. <span data-ttu-id="96ba3-120">Hizmeti çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="96ba3-120">Run the service.</span></span>  
  
8. <span data-ttu-id="96ba3-121">İstemcisini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="96ba3-121">Run the client.</span></span> <span data-ttu-id="96ba3-122">Uç nokta adresini, localhost yerine makine adına veya IP adresine işaret etmek üzere değiştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="96ba3-122">Ensure that you change the endpoint address to point to the machine name or IP address instead of localhost.</span></span> <span data-ttu-id="96ba3-123">İstemci bir ileti gönderir ve çıkar.</span><span class="sxs-lookup"><span data-stu-id="96ba3-123">The client sends a message and exits.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96ba3-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="96ba3-124">Requirements</span></span>  
 <span data-ttu-id="96ba3-125">Bu örneği çalıştırmak için, MSMQ 'ya ek olarak hem hizmette hem de istemci makinelerde IIS yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="96ba3-125">To run this sample, IIS must be installed on both the service and the client machines in addition to MSMQ.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="96ba3-126">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="96ba3-126">Demonstrates</span></span>  
 <span data-ttu-id="96ba3-127">Örnek, HTTP üzerinden MSMQ kullanarak WCF sıraya alınan iletileri göndermeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="96ba3-127">The sample demonstrates sending WCF queued messages using MSMQ over HTTP.</span></span> <span data-ttu-id="96ba3-128">Bu, SRMP mesajlaşma olarak da adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="96ba3-128">This is also called SRMP messaging.</span></span> <span data-ttu-id="96ba3-129">Sıraya alınan bir ileti gönderildiğinde, Gönderen makinedeki MSMQ iletileri TCP veya HTTP taşıması üzerinden alma kuyruğu Yöneticisi 'ne aktarır.</span><span class="sxs-lookup"><span data-stu-id="96ba3-129">When a queued message is sent, MSMQ on the sending machine transfers the messages to the receiving queue manager over TCP or HTTP transport.</span></span> <span data-ttu-id="96ba3-130">SRMP ' i seçerek Kullanıcı, kuyruk aktarımı için bir taşıma olarak HTTP seçeneğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="96ba3-130">By choosing SRMP, the user indicates the choice of HTTP as a transport for queue transfer.</span></span> <span data-ttu-id="96ba3-131">SRMP Secure, HTTPS kullanımını sunar.</span><span class="sxs-lookup"><span data-stu-id="96ba3-131">SRMP Secure enables the use of HTTPS.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96ba3-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="96ba3-132">Example</span></span>  
 <span data-ttu-id="96ba3-133">Örnek kod, işlem temelli örneğe dayalıdır.</span><span class="sxs-lookup"><span data-stu-id="96ba3-133">The sample code is based on the transacted sample.</span></span> <span data-ttu-id="96ba3-134">Sıradan bir ileti gönderdiğinizde ve SRMP kullanarak kuyruktan ileti aldığınızda, yerel bir protokol kullanarak ileti gönderme ve alma ile aynı olur.</span><span class="sxs-lookup"><span data-stu-id="96ba3-134">How you send a message to the queue and receive a message from the queue using SRMP is the same as sending and receiving messages using a Native protocol.</span></span>  
  
 <span data-ttu-id="96ba3-135">İstemci yapılandırması, sıra Aktarım protokolünün seçimini belirtecek şekilde değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="96ba3-135">The configuration for the client is changed to indicate the choice of the queue transfer protocol.</span></span> <span data-ttu-id="96ba3-136">Sıra Aktarım Protokolü yerel, SRMP veya SrmpSecure değerinden biri olabilir.</span><span class="sxs-lookup"><span data-stu-id="96ba3-136">The queue transfer protocol can be one of Native, SRMP or SrmpSecure.</span></span> <span data-ttu-id="96ba3-137">Varsayılan olarak, Aktarım Protokolü yereldir.</span><span class="sxs-lookup"><span data-stu-id="96ba3-137">By default, the transfer protocol is Native.</span></span> <span data-ttu-id="96ba3-138">İstemci ve hizmet, bu örnekte SRMP 'yi kullanmak için yapılandırmayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="96ba3-138">The client and service specify in the configuration to use SRMP in this example.</span></span>  
  
 <span data-ttu-id="96ba3-139">Aktarım güvenliği ile ilgili olarak SRMP için sınırlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="96ba3-139">There are limitations to SRMP in relation to transport security.</span></span> <span data-ttu-id="96ba3-140">Varsayılan MSMQ taşıma güvenliği, gönderme kuyruğu yöneticisinin ve alma kuyruğu yöneticisinin aynı Windows etki alanında bulunmasını gerektiren Active Directory gerektirir.</span><span class="sxs-lookup"><span data-stu-id="96ba3-140">The default MSMQ transport security requires Active Directory that requires that the sending queue manager and the receiving queue manager reside in the same Windows domain.</span></span> <span data-ttu-id="96ba3-141">HTTP sınırı üzerinden ileti gönderilirken bu mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="96ba3-141">This is not possible when sending messages over HTTP boundary.</span></span> <span data-ttu-id="96ba3-142">Bu nedenle, varsayılan aktarım güvenliği çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="96ba3-142">As such, the default transport security does not work.</span></span> <span data-ttu-id="96ba3-143">Aktarım güvenliği isteniyorsa aktarım güvenliği sertifika olarak ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="96ba3-143">The transport security must be set to Certificate if transport security is desired.</span></span> <span data-ttu-id="96ba3-144">İleti güvenliği, iletinin güvenliğini sağlamak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="96ba3-144">Message security can also be used to secure the message.</span></span> <span data-ttu-id="96ba3-145">Bu örnekte, hem aktarım hem de ileti güvenliği, SRMP iletilerini göstermek için kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="96ba3-145">In this sample, both transport and message security is turned off to illustrate SRMP messaging.</span></span>  
  
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
  
 <span data-ttu-id="96ba3-146">Örnek çalıştırmak aşağıdaki çıktıyı verir.</span><span class="sxs-lookup"><span data-stu-id="96ba3-146">Running the sample yields the following output.</span></span>  
  
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
> <span data-ttu-id="96ba3-147">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="96ba3-147">The samples may already be installed on your machine.</span></span> <span data-ttu-id="96ba3-148">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="96ba3-148">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="96ba3-149">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="96ba3-149">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="96ba3-150">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="96ba3-150">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\SRMP`  
