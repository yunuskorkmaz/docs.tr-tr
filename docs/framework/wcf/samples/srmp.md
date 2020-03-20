---
title: SRMP
ms.date: 03/30/2017
ms.assetid: cf37078c-dcb4-45e0-acaf-2f196521b226
ms.openlocfilehash: b1b61c18c801059e95cd0b13a3135132a583882f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183334"
---
# <a name="srmp"></a><span data-ttu-id="6269b-102">SRMP</span><span class="sxs-lookup"><span data-stu-id="6269b-102">SRMP</span></span>
<span data-ttu-id="6269b-103">Bu örnek, http üzerinden Ileti Sırası (MSMQ) kullanarak işlemyapılan sıralı iletişimin nasıl gerçekleştiriltilebildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6269b-103">This sample demonstrates how to perform transacted queued communication by using Message Queuing (MSMQ) over HTTP.</span></span>  
  
 <span data-ttu-id="6269b-104">Sıralı iletişimde, istemci bir sıra kullanarak hizmete iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="6269b-104">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="6269b-105">Daha doğrusu, istemci sıraya ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="6269b-105">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="6269b-106">Hizmet, kuyruktan iletiler alır.</span><span class="sxs-lookup"><span data-stu-id="6269b-106">The service receives messages from the queue.</span></span> <span data-ttu-id="6269b-107">Bu nedenle, hizmet ve istemci, bir sıra kullanarak iletişim kurmak için aynı anda çalışıyor olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="6269b-107">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="6269b-108">MSMQ, kuyruğa ileti göndermek için HTTP (HTTPS kullanımı dahil) kullanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="6269b-108">MSMQ enables the use of HTTP (including the use of HTTPS) to send messages to a queue.</span></span> <span data-ttu-id="6269b-109">Bu örnekte, Windows Communication Foundation (WCF) sıralı iletişimi ve HTTP üzerinden nasıl ileti gönderebileceğimizi gösteriyoruz.</span><span class="sxs-lookup"><span data-stu-id="6269b-109">In this example, we demonstrate using Windows Communication Foundation (WCF) queued communication and how to send messages over HTTP.</span></span> <span data-ttu-id="6269b-110">MSMQ, HTTP üzerinden iletişim için SOAP tabanlı bir protokol olan SRMP adlı bir protokol kullanır.</span><span class="sxs-lookup"><span data-stu-id="6269b-110">MSMQ uses a protocol called SRMP, which is a SOAP-based protocol for communication over HTTP.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6269b-111">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="6269b-111">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="6269b-112">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="6269b-112">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="6269b-113">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="6269b-113">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="6269b-114">Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="6269b-114">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
4. <span data-ttu-id="6269b-115">**Windows Bileşenleri ekle/kaldır'da**örneği çalıştırmadan önce, MSMQ'nun HTTP desteğiyle yüklendiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="6269b-115">Before running the sample in **Add/Remove Windows Components**, ensure that MSMQ is installed with HTTP support.</span></span> <span data-ttu-id="6269b-116">HTTP desteğinin yüklenmesi Internet Information Services 'ı (IIS) otomatik olarak yükler ve MSMQ için IIS'ye protokol desteği ekler.</span><span class="sxs-lookup"><span data-stu-id="6269b-116">Installing HTTP support automatically installs Internet Information Services (IIS) and adds the protocol support in IIS for MSMQ.</span></span>  
  
5. <span data-ttu-id="6269b-117">HTTP'nin iletişim için kullanıldığından emin olmak istiyorsanız, MSMQ'nun sertleştirilmiş modda çalışmasını etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6269b-117">If you want to be certain that HTTP is used for communication, you can enable MSMQ to run in hardened mode.</span></span> <span data-ttu-id="6269b-118">Bu, makinede barındırılan herhangi bir kuyruğa gönderilen hiçbir iletinin HTTP dışı aktarımları kullanarak ulaşmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="6269b-118">This ensures that no messages to any queue hosted on the machine can arrive using any non-HTTP transport.</span></span>  
  
6. <span data-ttu-id="6269b-119">Sertleştirilmiş modda çalışmak üzere MSMQ'yu seçtikten sonra, makine windows server 2003'te yeniden önyükleme gerektirir.</span><span class="sxs-lookup"><span data-stu-id="6269b-119">After you have selected MSMQ to run in hardened mode, the machine requires a re-boot on Windows Server 2003.</span></span>  
  
7. <span data-ttu-id="6269b-120">Servisi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6269b-120">Run the service.</span></span>  
  
8. <span data-ttu-id="6269b-121">İstemciyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6269b-121">Run the client.</span></span> <span data-ttu-id="6269b-122">Uç nokta adresini yerel ana bilgisayar yerine makine adını veya IP adresini işaret edecek şekilde değiştirdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="6269b-122">Ensure that you change the endpoint address to point to the machine name or IP address instead of localhost.</span></span> <span data-ttu-id="6269b-123">İstemci bir ileti gönderir ve çıkar.</span><span class="sxs-lookup"><span data-stu-id="6269b-123">The client sends a message and exits.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6269b-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6269b-124">Requirements</span></span>  
 <span data-ttu-id="6269b-125">Bu örneği çalıştırmak için IIS'nin MSMQ'ya ek olarak hem hizmete hem de istemci makinelere yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="6269b-125">To run this sample, IIS must be installed on both the service and the client machines in addition to MSMQ.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="6269b-126">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="6269b-126">Demonstrates</span></span>  
 <span data-ttu-id="6269b-127">Örnek, HTTP üzerinden MSMQ kullanarak WCF sıralı iletiler göndermeyi göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="6269b-127">The sample demonstrates sending WCF queued messages using MSMQ over HTTP.</span></span> <span data-ttu-id="6269b-128">Buna SRMP iletisi de denir.</span><span class="sxs-lookup"><span data-stu-id="6269b-128">This is also called SRMP messaging.</span></span> <span data-ttu-id="6269b-129">Sıraya alınan bir ileti gönderildiğinde, gönderen makinedeki MSMQ iletileri TCP veya HTTP aktarımı üzerinden alan sıra yöneticisine aktarıyor.</span><span class="sxs-lookup"><span data-stu-id="6269b-129">When a queued message is sent, MSMQ on the sending machine transfers the messages to the receiving queue manager over TCP or HTTP transport.</span></span> <span data-ttu-id="6269b-130">SRMP'yi seçerek, kullanıcı sıra transferi için bir aktarım olarak HTTP seçimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6269b-130">By choosing SRMP, the user indicates the choice of HTTP as a transport for queue transfer.</span></span> <span data-ttu-id="6269b-131">SRMP Secure HTTPS kullanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="6269b-131">SRMP Secure enables the use of HTTPS.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6269b-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="6269b-132">Example</span></span>  
 <span data-ttu-id="6269b-133">Örnek kodu, işlem yapılan örneğe dayanır.</span><span class="sxs-lookup"><span data-stu-id="6269b-133">The sample code is based on the transacted sample.</span></span> <span data-ttu-id="6269b-134">SRMP kullanarak kuyruğa ileti gönderme ve kuyruktan ileti alma şekliniz, Yerel protokol kullanarak ileti gönderip almakla aynıdır.</span><span class="sxs-lookup"><span data-stu-id="6269b-134">How you send a message to the queue and receive a message from the queue using SRMP is the same as sending and receiving messages using a Native protocol.</span></span>  
  
 <span data-ttu-id="6269b-135">İstemcinin yapılandırması, sıra aktarım protokolünün seçimini gösterecek şekilde değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="6269b-135">The configuration for the client is changed to indicate the choice of the queue transfer protocol.</span></span> <span data-ttu-id="6269b-136">Sıra aktarım protokolü Yerel, SRMP veya SrmpSecure'dan biri olabilir.</span><span class="sxs-lookup"><span data-stu-id="6269b-136">The queue transfer protocol can be one of Native, SRMP or SrmpSecure.</span></span> <span data-ttu-id="6269b-137">Varsayılan olarak, aktarım protokolü Yerel'dir.</span><span class="sxs-lookup"><span data-stu-id="6269b-137">By default, the transfer protocol is Native.</span></span> <span data-ttu-id="6269b-138">İstemci ve hizmet yapılandırmada bu örnekte SRMP'yi kullanacağını belirtin.</span><span class="sxs-lookup"><span data-stu-id="6269b-138">The client and service specify in the configuration to use SRMP in this example.</span></span>  
  
 <span data-ttu-id="6269b-139">Aktarım güvenliğiyle ilgili olarak SRMP'de sınırlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="6269b-139">There are limitations to SRMP in relation to transport security.</span></span> <span data-ttu-id="6269b-140">Varsayılan MSMQ aktarım güvenliği, gönderen sıra yöneticisi ve alan sıra yöneticisinin aynı Windows etki alanında ikamet ettiğini gerektiren Etkin Dizin gerektirir.</span><span class="sxs-lookup"><span data-stu-id="6269b-140">The default MSMQ transport security requires Active Directory that requires that the sending queue manager and the receiving queue manager reside in the same Windows domain.</span></span> <span data-ttu-id="6269b-141">Bu, HTTP sınırı üzerinden ileti gönderirken mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="6269b-141">This is not possible when sending messages over HTTP boundary.</span></span> <span data-ttu-id="6269b-142">Bu nedenle, varsayılan aktarım güvenliği çalışmıyor.</span><span class="sxs-lookup"><span data-stu-id="6269b-142">As such, the default transport security does not work.</span></span> <span data-ttu-id="6269b-143">Taşıma güvenliği isteniyorsa, taşıma güvenliği Sertifika olarak ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6269b-143">The transport security must be set to Certificate if transport security is desired.</span></span> <span data-ttu-id="6269b-144">İleti güvenliği, iletiyi güvenli hale getirmek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6269b-144">Message security can also be used to secure the message.</span></span> <span data-ttu-id="6269b-145">Bu örnekte, SRMP iletisini göstermek için hem aktarım hem de ileti güvenliği kapatılır.</span><span class="sxs-lookup"><span data-stu-id="6269b-145">In this sample, both transport and message security is turned off to illustrate SRMP messaging.</span></span>  
  
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
  
 <span data-ttu-id="6269b-146">Numunenin çalıştırılsa, aşağıdaki çıktıyı verir.</span><span class="sxs-lookup"><span data-stu-id="6269b-146">Running the sample yields the following output.</span></span>  
  
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
> <span data-ttu-id="6269b-147">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="6269b-147">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6269b-148">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="6269b-148">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="6269b-149">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="6269b-149">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6269b-150">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="6269b-150">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\SRMP`  
