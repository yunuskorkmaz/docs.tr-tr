---
title: SRMP
ms.date: 03/30/2017
ms.assetid: cf37078c-dcb4-45e0-acaf-2f196521b226
ms.openlocfilehash: 62075cccfa8ff2c6a181d633756a5f9bc8969932
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44048250"
---
# <a name="srmp"></a><span data-ttu-id="29f38-102">SRMP</span><span class="sxs-lookup"><span data-stu-id="29f38-102">SRMP</span></span>
<span data-ttu-id="29f38-103">Bu örnek HTTP üzerinden Message Queuing (MSMQ) kullanarak hizmetteki kuyruğa alınan iletişim gerçekleştirme gösterir.</span><span class="sxs-lookup"><span data-stu-id="29f38-103">This sample demonstrates how to perform transacted queued communication by using Message Queuing (MSMQ) over HTTP.</span></span>  
  
 <span data-ttu-id="29f38-104">Kuyruğa alınan iletişim kullanarak bir kuyruk hizmetine istemci iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="29f38-104">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="29f38-105">Daha kesin bir istemci bir kuyruğa iletiler gönderir.</span><span class="sxs-lookup"><span data-stu-id="29f38-105">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="29f38-106">Hizmet iletileri kuyruktan alır.</span><span class="sxs-lookup"><span data-stu-id="29f38-106">The service receives messages from the queue.</span></span> <span data-ttu-id="29f38-107">Hizmet ve istemci bu nedenle, bir kuyruk kullanarak iletişim kurmak için aynı anda çalıştırılması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="29f38-107">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="29f38-108">MSMQ bir kuyruğa ileti göndermek için HTTP (HTTPS kullanımı dahil) kullanılmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="29f38-108">MSMQ enables the use of HTTP (including the use of HTTPS) to send messages to a queue.</span></span> <span data-ttu-id="29f38-109">Bu örnekte, Windows Communication Foundation (WCF) kullanarak sıraya iletişim ve HTTP üzerinden ileti göndermek nasıl ekleyebileceğiniz gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="29f38-109">In this example, we demonstrate using Windows Communication Foundation (WCF) queued communication and how to send messages over HTTP.</span></span> <span data-ttu-id="29f38-110">MSMQ HTTP üzerinden iletişim için SOAP tabanlı bir protokol olan SRMP, adlı bir protokolü kullanır.</span><span class="sxs-lookup"><span data-stu-id="29f38-110">MSMQ uses a protocol called SRMP, which is a SOAP-based protocol for communication over HTTP.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="29f38-111">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="29f38-111">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="29f38-112">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="29f38-112">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="29f38-113">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="29f38-113">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="29f38-114">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="29f38-114">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="29f38-115">Örneği çalıştırmadan önce **Windows Bileşenlerini Ekle/Kaldır**, MSMQ yüklü olduğundan emin olun HTTP desteği.</span><span class="sxs-lookup"><span data-stu-id="29f38-115">Before running the sample in **Add/Remove Windows Components**, ensure that MSMQ is installed with HTTP support.</span></span> <span data-ttu-id="29f38-116">HTTP desteği otomatik olarak yükleme, Internet Information Services (IIS) yükler ve protokol desteği için MSMQ IIS'de ekler.</span><span class="sxs-lookup"><span data-stu-id="29f38-116">Installing HTTP support automatically installs Internet Information Services (IIS) and adds the protocol support in IIS for MSMQ.</span></span>  
  
5.  <span data-ttu-id="29f38-117">HTTP iletişimi için kullanılan emin olmak istiyorsanız, sağlamlaştırılmış modda çalıştırmak MSMQ etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29f38-117">If you want to be certain that HTTP is used for communication, you can enable MSMQ to run in hardened mode.</span></span> <span data-ttu-id="29f38-118">Bu makinede barındırılan herhangi bir kuyruğa ileti herhangi bir HTTP olmayan aktarım kullanarak ulaşmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="29f38-118">This ensures that no messages to any queue hosted on the machine can arrive using any non-HTTP transport.</span></span>  
  
6.  <span data-ttu-id="29f38-119">Sağlamlaştırılmış modda çalıştırmak için MSMQ seçtikten sonra makine yeniden önyükleme gerektiği [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].</span><span class="sxs-lookup"><span data-stu-id="29f38-119">After you have selected MSMQ to run in hardened mode, the machine requires a re-boot on [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].</span></span>  
  
7.  <span data-ttu-id="29f38-120">Hizmet çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="29f38-120">Run the service.</span></span>  
  
8.  <span data-ttu-id="29f38-121">İstemciyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="29f38-121">Run the client.</span></span> <span data-ttu-id="29f38-122">Makine adı için işaret edecek şekilde uç nokta adresini veya IP adresi localhost yerine değiştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="29f38-122">Ensure that you change the endpoint address to point to the machine name or IP address instead of localhost.</span></span> <span data-ttu-id="29f38-123">İstemci bir ileti gönderir ve çıkar.</span><span class="sxs-lookup"><span data-stu-id="29f38-123">The client sends a message and exits.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29f38-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="29f38-124">Requirements</span></span>  
 <span data-ttu-id="29f38-125">Bu örneği çalıştırmak için IIS hem hizmet hem de istemci makinelerin MSMQ yanı sıra yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="29f38-125">To run this sample, IIS must be installed on both the service and the client machines in addition to MSMQ.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="29f38-126">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="29f38-126">Demonstrates</span></span>  
 <span data-ttu-id="29f38-127">Örneği, WCF gönderme gösterir. MSMQ kullanarak HTTP üzerinden ileti kuyruğa alındı.</span><span class="sxs-lookup"><span data-stu-id="29f38-127">The sample demonstrates sending WCF queued messages using MSMQ over HTTP.</span></span> <span data-ttu-id="29f38-128">Bu, SRMP Mesajlaşma olarak da adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="29f38-128">This is also called SRMP messaging.</span></span> <span data-ttu-id="29f38-129">Ne zaman bir kuyruğa alınmış ileti gönderilir, MSMQ alıcı Kuyruk Yöneticisi üzerinden TCP veya HTTP aktarım için gönderme makine aktarımlarında iletileri üzerinde.</span><span class="sxs-lookup"><span data-stu-id="29f38-129">When a queued message is sent, MSMQ on the sending machine transfers the messages to the receiving queue manager over TCP or HTTP transport.</span></span> <span data-ttu-id="29f38-130">SRMP seçerek kullanıcı seçimi HTTP kuyruk aktarımı için aktarım olarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="29f38-130">By choosing SRMP, the user indicates the choice of HTTP as a transport for queue transfer.</span></span> <span data-ttu-id="29f38-131">SRMP güvenli HTTPS kullanımını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="29f38-131">SRMP Secure enables the use of HTTPS.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29f38-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="29f38-132">Example</span></span>  
 <span data-ttu-id="29f38-133">Örnek kod, hizmetteki örnek üzerinde temel alır.</span><span class="sxs-lookup"><span data-stu-id="29f38-133">The sample code is based on the transacted sample.</span></span> <span data-ttu-id="29f38-134">Kuyruğa bir ileti göndermek ve SRMP kullanarak kuyruktan bir ileti alırsınız nasıl yerel protokolünü kullanarak ileti gönderme ve alma ile aynı olur.</span><span class="sxs-lookup"><span data-stu-id="29f38-134">How you send a message to the queue and receive a message from the queue using SRMP is the same as sending and receiving messages using a Native protocol.</span></span>  
  
 <span data-ttu-id="29f38-135">İstemci yapılandırması seçeneği sırası Aktarımı Protokolü belirtmek için değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="29f38-135">The configuration for the client is changed to indicate the choice of the queue transfer protocol.</span></span> <span data-ttu-id="29f38-136">Kuyruk Aktarım Protokolü, yerel, SRMP ya da SrmpSecure biri olabilir.</span><span class="sxs-lookup"><span data-stu-id="29f38-136">The queue transfer protocol can be one of Native, SRMP or SrmpSecure.</span></span> <span data-ttu-id="29f38-137">Varsayılan olarak, yerel aktarımı protokolüdür.</span><span class="sxs-lookup"><span data-stu-id="29f38-137">By default, the transfer protocol is Native.</span></span> <span data-ttu-id="29f38-138">Hizmet ve istemci bu örnekte SRMP kullanmak için yapılandırmayı belirtin.</span><span class="sxs-lookup"><span data-stu-id="29f38-138">The client and service specify in the configuration to use SRMP in this example.</span></span>  
  
 <span data-ttu-id="29f38-139">SRMP aktarım güvenliği ile ilgili sınırlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="29f38-139">There are limitations to SRMP in relation to transport security.</span></span> <span data-ttu-id="29f38-140">Gönderme sırası Yöneticisi ve alıcı sırası aynı Windows etki alanında bulunan gerektiren Active Directory varsayılan MSMQ taşıma güvenliği gerektirir.</span><span class="sxs-lookup"><span data-stu-id="29f38-140">The default MSMQ transport security requires Active Directory that requires that the sending queue manager and the receiving queue manager reside in the same Windows domain.</span></span> <span data-ttu-id="29f38-141">Bu HTTP sınır ileti gönderirken mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="29f38-141">This is not possible when sending messages over HTTP boundary.</span></span> <span data-ttu-id="29f38-142">Bu nedenle, varsayılan aktarım güvenliği çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="29f38-142">As such, the default transport security does not work.</span></span> <span data-ttu-id="29f38-143">Aktarım güvenliği isterseniz aktarım güvenliği için sertifika ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="29f38-143">The transport security must be set to Certificate if transport security is desired.</span></span> <span data-ttu-id="29f38-144">İleti güvenliği, ileti güvenliğini sağlamak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="29f38-144">Message security can also be used to secure the message.</span></span> <span data-ttu-id="29f38-145">Bu örnekte, hem aktarım hem de ileti güvenlik SRMP Mesajlaşma göstermek için kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="29f38-145">In this sample, both transport and message security is turned off to illustrate SRMP messaging.</span></span>  
  
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
  
 <span data-ttu-id="29f38-146">Çalışan örnek aşağıdaki çıktıyı üretir.</span><span class="sxs-lookup"><span data-stu-id="29f38-146">Running the sample yields the following output.</span></span>  
  
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
>  <span data-ttu-id="29f38-147">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="29f38-147">The samples may already be installed on your machine.</span></span> <span data-ttu-id="29f38-148">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="29f38-148">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="29f38-149">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="29f38-149">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="29f38-150">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="29f38-150">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\SRMP`  
  
## <a name="see-also"></a><span data-ttu-id="29f38-151">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="29f38-151">See Also</span></span>
