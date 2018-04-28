---
title: Dayanıklı Çift Yönlü
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4e76d1a1-f3d8-4a0f-8746-4a322cdff6eb
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 50d0ac9efae8e6d795455a63d793b2e84407b987
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="durable-duplex"></a><span data-ttu-id="666f5-102">Dayanıklı Çift Yönlü</span><span class="sxs-lookup"><span data-stu-id="666f5-102">Durable Duplex</span></span>
<span data-ttu-id="666f5-103">Bu örnek, ayarlama ve mesajlaşma etkinlikleri Windows Workflow Foundation (WF) kullanan dayanıklı çift yönlü ileti alışverişi yapılandırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="666f5-103">This sample demonstrates how to set up and configure durable duplex message exchange using the messaging activities in Windows Workflow Foundation (WF).</span></span> <span data-ttu-id="666f5-104">Dayanıklı çift yönlü ileti değişimi gerçekleşir uzun bir süre boyunca bir iki yönlü ileti değişimi ' dir.</span><span class="sxs-lookup"><span data-stu-id="666f5-104">A durable duplex message exchange is a two-way message exchange that takes place over a long period of time.</span></span> <span data-ttu-id="666f5-105">İleti değişimi ömrü iletişim kanalını ömrü ve hizmet örnekleri bellek içi ömrü uzun olabilir.</span><span class="sxs-lookup"><span data-stu-id="666f5-105">The lifetime of the message exchange may be longer than the lifetime of the communication channel and the in-memory lifetime of the service instances.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="666f5-106">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="666f5-106">Sample Details</span></span>  
 <span data-ttu-id="666f5-107">Bu örnekte, iki [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Windows Workflow Foundation kullanılarak uygulanan Hizmetleri dayanıklı çift yönlü ileti değişimi için yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="666f5-107">In this sample, two [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services implemented using Windows Workflow Foundation are configured to have a durable duplex message exchange.</span></span> <span data-ttu-id="666f5-108">Dayanıklı çift yönlü ileti değişimi MSMQ gönderilir ve kullanılarak bağıntılı iki tek yönlü gelen iletileri oluşan [.NET bağlam değişimi](http://go.microsoft.com/fwlink/?LinkID=166059).</span><span class="sxs-lookup"><span data-stu-id="666f5-108">The durable duplex message exchange is composed from two one-way messages sent over MSMQ and correlated using [.NET Context Exchange](http://go.microsoft.com/fwlink/?LinkID=166059).</span></span> <span data-ttu-id="666f5-109">İletileri kullanılarak gönderilen <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.Receive> Mesajlaşma etkinlikleri.</span><span class="sxs-lookup"><span data-stu-id="666f5-109">The messages are sent using the <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.Receive> messaging activities.</span></span> <span data-ttu-id="666f5-110">.NET bağlam değişimi gönderilen iletileri geri çağırma adresini belirtmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="666f5-110">.NET Context Exchange is use to specify the callback address on the sent messages.</span></span> <span data-ttu-id="666f5-111">Her iki hizmet Windows İşlem Etkinleştirme Hizmetleri (WAS) kullanılarak barındırılır ve Hizmetleri örneklerinin Kalıcılık etkinleştirmek için yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="666f5-111">Both services are hosted using Windows Process Activation Services (WAS) and are configured to enable persistence of the services instances.</span></span>  
  
 <span data-ttu-id="666f5-112">İlk hizmet (Service1.xamlx) biraz çalışmanız gönderme hizmete (Service2.xamlx) bir isteği gönderir.</span><span class="sxs-lookup"><span data-stu-id="666f5-112">The first service (Service1.xamlx) sends a request to the send service (Service2.xamlx) to do some work.</span></span> <span data-ttu-id="666f5-113">İş tamamlandığında, Service2.xamlx iş tamamlanıp tamamlanmadığını göstermek için geri için Service1.xamlx bir bildirim gönderir.</span><span class="sxs-lookup"><span data-stu-id="666f5-113">Once the work is completed, Service2.xamlx sends a notification back to Service1.xamlx to indicate that the work has been completed.</span></span> <span data-ttu-id="666f5-114">Bir iş akışı konsol uygulaması hizmetlerin dinlediği sıralarını ayarlar ve Service1.xamlx etkinleştirmek için ilk başlatma iletisi gönderir.</span><span class="sxs-lookup"><span data-stu-id="666f5-114">A workflow console application sets up the queues that the services are listening on and sends the initial Start message to activate Service1.xamlx.</span></span> <span data-ttu-id="666f5-115">İstenen iş tamamlandı Service2.xamlx bildirimden service1.xamlx aldıktan sonra Service1.xamlx sonucu bir XML dosyasına kaydeder.</span><span class="sxs-lookup"><span data-stu-id="666f5-115">Once Service1.xamlx receives the notification from Service2.xamlx that the requested work has been completed, Service1.xamlx saves the result to an XML file.</span></span> <span data-ttu-id="666f5-116">Geri çağırma ileti için beklenirken Service1.xamlx varsayılan kullanılarak örneği durumu devam <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>.</span><span class="sxs-lookup"><span data-stu-id="666f5-116">While waiting for the callback message, Service1.xamlx persists its instance state using the default <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>.</span></span> <span data-ttu-id="666f5-117">Service2.xamlx örneği durumuna Service1.xamlx tarafından istenen çalışmayı tamamladıktan bir parçası olarak devam ettirir.</span><span class="sxs-lookup"><span data-stu-id="666f5-117">Service2.xamlx persists its instance state as part of completing the work requested by Service1.xamlx.</span></span>  
  
 <span data-ttu-id="666f5-118">.NET bağlam değişimi üzerinde MSMQ kullanmak üzere hizmetlerin yapılandırmak için her iki hizmet oluşan özel bağlama kullanmak üzere yapılandırılmış <xref:System.ServiceModel.Channels.ContextBindingElement> ve <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="666f5-118">To configure the services to use .NET Context Exchange over MSMQ, both services are configured to use a custom binding that consists of the <xref:System.ServiceModel.Channels.ContextBindingElement> and the <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>.</span></span> <span data-ttu-id="666f5-119">Bir geri çağırma adresi ile belirtilen <xref:System.ServiceModel.Channels.ContextBindingElement> ve bir geri çağırma içerik üstbilgisinde özel bağlama kullanılarak gönderilen tüm iletiler eklenir.</span><span class="sxs-lookup"><span data-stu-id="666f5-119">A callback address is specified with the <xref:System.ServiceModel.Channels.ContextBindingElement> and is included in a callback context header with all messages sent using a custom binding.</span></span> <span data-ttu-id="666f5-120">Aşağıdaki kod örneğinde özel bağlama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="666f5-120">The following code example defines the custom binding.</span></span>  
  
```xml  
<configuration>  
     <system.serviceModel>  
          …  
          <bindings>  
               <customBinding>  
                    <binding name="netMsmqContextBinding">  
                         <context clientCallbackAddress="net.msmq://localhost/private/DurableDuplex/Service1.xamlx"/>  
                         <msmqTransport exactlyOnce="False">  
                              <msmqTransportSecurity msmqAuthenticationMode="None" msmqProtectionLevel="None"/>  
                         </msmqTransport>  
                    </binding>  
               </customBinding>  
          </bindings>  
          …  
     </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
>  <span data-ttu-id="666f5-121">Bu örnek tarafından kullanılan bağlama güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="666f5-121">The binding used by this sample is not secure.</span></span> <span data-ttu-id="666f5-122">Uygulamanızı dağıtırken, uygulamanızın güvenlik gereksinimlerine bağlı olarak, bağlama yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="666f5-122">When deploying your application you should configure your binding based on the security requirements of your application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="666f5-123">Bu örnekte kullanılan sıraları işlem değildir.</span><span class="sxs-lookup"><span data-stu-id="666f5-123">The queues used in this sample are not transactional.</span></span> <span data-ttu-id="666f5-124">Nasıl ayarlanacağını gösteren bir örnek için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ileti değişimleri işlem kuyrukları kullanma, bkz: [MSMQ etkinleştirme](../../../../docs/framework/wcf/samples/msmq-activation.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="666f5-124">For a sample that shows how to set up [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] message exchanges using transaction queues, see the [MSMQ Activation](../../../../docs/framework/wcf/samples/msmq-activation.md) sample.</span></span>  
  
 <span data-ttu-id="666f5-125">İçin Service2.xamlx service1.xamlx tarafından gönderilen ileti Service2.xamlx ve özel bağlama adresiyle yapılandırılmış bir istemci uç noktası kullanarak, önceden tanımlanmış gönderilir.</span><span class="sxs-lookup"><span data-stu-id="666f5-125">The message sent by Service1.xamlx to Service2.xamlx is sent using a client endpoint configured with the address of Service2.xamlx and the custom binding defined previously.</span></span> <span data-ttu-id="666f5-126">Geri Service2.xamlx aramasından Service1.xamlx için adresi Service1.xamlx tarafından gönderilen geri çağırma içeriğinden alınır için açıkça yapılandırılmış hiçbir adresiyle bir istemci uç noktası kullanılarak gönderilir.</span><span class="sxs-lookup"><span data-stu-id="666f5-126">The callback from Service2.xamlx to Service1.xamlx is sent using a client endpoint with no explicitly configured address because the address is taken from the callback context sent by Service1.xamlx.</span></span> <span data-ttu-id="666f5-127">Aşağıdaki kod örneği, istemci uç noktaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="666f5-127">The following code example defines the client endpoints.</span></span>  
  
```xml  
<?xml version="1.0"?>  
<configuration>  
     <system.serviceModel>  
          …  
          <client>  
               <endpoint address="net.msmq://localhost/private/DurableDuplex/Service2.xamlx" binding="customBinding" bindingConfiguration="netMsmqContextBinding" contract="IDoWork"/>  
               <endpoint binding="customBinding" bindingConfiguration="netMsmqContextBinding" contract="INotify"/>  
          </client>  
          …  
     </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="666f5-128">Aşağıdaki kod örneği, bu özel bağlama kullanmak için net.msmq temel adres için varsayılan protokolü eşleme değiştirerek bu özel bağlama kullanma uç noktaları kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="666f5-128">The following code example exposes endpoints using this custom binding by changing the default protocol mapping for net.msmq base addresses to use this custom binding.</span></span>  
  
```xml  
<configuration>  
     <system.serviceModel>  
          <protocolMapping>  
               <add scheme="net.msmq" binding="customBinding" bindingConfiguration="netMsmqContextBinding"/>  
          </protocolMapping>  
          …  
     </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="666f5-129">Aşağıdaki kod örneğinde ekleyerek her iki hizmet kalıcılığını etkinleştirir <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> davranışı hem Hizmetleri, hem de Kalıcılık veritabanı için bağlantı dizesini belirleme.</span><span class="sxs-lookup"><span data-stu-id="666f5-129">The following code example enables persistence for both services by adding the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior to both services and specifying the connection string for the persistence database.</span></span>  
  
```xml  
<?xml version="1.0"?>  
<configuration>  
    <system.serviceModel>  
          …  
          <behaviors>  
               <serviceBehaviors>  
                    <behavior>  
                         <serviceDebug includeExceptionDetailInFaults="True"/>  
                         <serviceMetadata httpGetEnabled="True"/>  
                         <sqlWorkflowInstanceStore connectionString="Data Source=.\SQLEXPRESS;Initial Catalog=DefaultSampleStore;Integrated Security=True"/>  
                    </behavior>  
               </serviceBehaviors>  
          </behaviors>  
     </system.serviceModel>  
</configuration>  
```  
  
## <a name="system-requirements"></a><span data-ttu-id="666f5-130">Sistem Gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="666f5-130">System Requirements</span></span>  
 <span data-ttu-id="666f5-131">Bu örnek, aşağıdaki bileşenleri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="666f5-131">This sample requires the following components.</span></span>  
  
1.  <span data-ttu-id="666f5-132">Internet Information Services.</span><span class="sxs-lookup"><span data-stu-id="666f5-132">Internet Information Services.</span></span>  
  
2.  <span data-ttu-id="666f5-133">Internet Information Services IIS 6.0 Yönetim uyumluluğu -> IIS metatabanı ve IIS 6.0 yapılandırma uyumluluğu ->.</span><span class="sxs-lookup"><span data-stu-id="666f5-133">Internet Information Services -> IIS 6.0 Management Compatibility -> IIS Metabase and IIS 6.0 configuration compatibility.</span></span>  
  
3.  <span data-ttu-id="666f5-134">World Wide Web Hizmetleri -> uygulama geliştirme özellikleri -> ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="666f5-134">World Wide Web Services -> Application Development Features -> ASP.NET.</span></span>  
  
4.  <span data-ttu-id="666f5-135">Microsoft Message sıraları (MSMQ) sunucusu.</span><span class="sxs-lookup"><span data-stu-id="666f5-135">Microsoft Message Queues (MSMQ) Server.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="666f5-136">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="666f5-136">To use this sample</span></span>  
  
1.  <span data-ttu-id="666f5-137">Kalıcılık veritabanı ve sonuçlar dizini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="666f5-137">Set up the persistence database and the results directory.</span></span>  
  
    1.  <span data-ttu-id="666f5-138">Açık bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut istemi.</span><span class="sxs-lookup"><span data-stu-id="666f5-138">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
    2.  <span data-ttu-id="666f5-139">Bu örnek için klasörüne gidin ve Setup.cmd çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="666f5-139">Navigate to the folder for this sample and run Setup.cmd.</span></span>  
  
2.  <span data-ttu-id="666f5-140">Sanal uygulama ayarlama.</span><span class="sxs-lookup"><span data-stu-id="666f5-140">Set up the virtual application.</span></span>  
  
    1.  <span data-ttu-id="666f5-141">Gelen bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut isteminde, aşağıdaki komutu çalıştırarak ASP.NET kaydolun.</span><span class="sxs-lookup"><span data-stu-id="666f5-141">From a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt, register ASP.NET by running the following command.</span></span>  
  
        ```  
        aspnet_regiis -i  
        ```  
  
    2.  <span data-ttu-id="666f5-142">Çalıştırma [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] sağ tıklanarak yönetici izinlerine sahip [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ve seçerek **yönetici olarak çalıştır**.</span><span class="sxs-lookup"><span data-stu-id="666f5-142">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with administrator permissions by right-clicking [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and selecting **Run as administrator**.</span></span>  
  
    3.  <span data-ttu-id="666f5-143">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], DurableDuplex.sln dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="666f5-143">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the DurableDuplex.sln file.</span></span>  
  
3.  <span data-ttu-id="666f5-144">Hizmet sıralarını ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="666f5-144">Set up the service queues.</span></span>  
  
    1.  <span data-ttu-id="666f5-145">DurableDuplex istemci çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="666f5-145">To run the DurableDuplex client, press F5.</span></span>  
  
    2.  <span data-ttu-id="666f5-146">Açık **Bilgisayar Yönetimi** çalıştırarak konsol `Compmgmt.msc` bir komut isteminden.</span><span class="sxs-lookup"><span data-stu-id="666f5-146">Open the **Computer Management** console by running `Compmgmt.msc` from a command prompt.</span></span>  
  
    3.  <span data-ttu-id="666f5-147">Genişletme **hizmet ve uygulamaları**, **Message Queuing**.</span><span class="sxs-lookup"><span data-stu-id="666f5-147">Expand **Service and Applications**, **Message Queuing**.</span></span> <span data-ttu-id="666f5-148">**Özel sıralar**.</span><span class="sxs-lookup"><span data-stu-id="666f5-148">**Private Queues**.</span></span>  
  
    4.  <span data-ttu-id="666f5-149">Durableduplex/service1.xamlx ve durableduplex/service2.xamlx sıralar sağ tıklatıp **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="666f5-149">Right-click the durableduplex/service1.xamlx and durableduplex/service2.xamlx queues and select **Properties**.</span></span>  
  
    5.  <span data-ttu-id="666f5-150">Seçin **güvenlik** sekmesinde ve izin **herkes ileti Al**, **iletiye** ve **iletisi gönder** izinleri hem sıralar.</span><span class="sxs-lookup"><span data-stu-id="666f5-150">Select the **Security** tab and allow **Everyone Receive Message**, **Peek Message** and **Send Message** permissions for both queues.</span></span>  
  
    6.  <span data-ttu-id="666f5-151">İnternet Bilgi Hizmetleri (IIS) Yöneticisini açın.</span><span class="sxs-lookup"><span data-stu-id="666f5-151">Open Internet Information Services (IIS) Manager.</span></span>  
  
    7.  <span data-ttu-id="666f5-152">Gözat **Server**, **siteleri**, **varsayılan Web sitesi**, **özel**, **dayanıklı çift yönlü** ve seçin **Gelişmiş Seçenekler**.</span><span class="sxs-lookup"><span data-stu-id="666f5-152">Browse to **Server**, **Sites**, **Default Web site**, **private**, **Durable Duplex** and select **Advanced Options**.</span></span>  
  
    8.  <span data-ttu-id="666f5-153">Değişiklik **etkin protokoller** için **http,net.msmq**.</span><span class="sxs-lookup"><span data-stu-id="666f5-153">Change the **Enabled Protocols** to **http,net.msmq**.</span></span>  
  
4.  <span data-ttu-id="666f5-154">Örnek çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="666f5-154">Run the sample.</span></span>  
  
    1.  <span data-ttu-id="666f5-155">Gözat http://localhost/private/durableduplex/service1.xamlx ve http://localhost/private/durableduplex/service2.xamlx hem hizmetlerinin çalıştığından emin olmak için.</span><span class="sxs-lookup"><span data-stu-id="666f5-155">Browse to http://localhost/private/durableduplex/service1.xamlx and http://localhost/private/durableduplex/service2.xamlx to ensure that both services are running.</span></span>  
  
    2.  <span data-ttu-id="666f5-156">DurableDuplexClient çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="666f5-156">Press F5 to run DurableDuplexClient.</span></span>  
  
         <span data-ttu-id="666f5-157">Dayanıklı çift yönlü ileti değişimi tamamlandığında result.xml dosya C:\Inbox klasörüne kaydedilir ve ileti değişimi sonucunu içerir.</span><span class="sxs-lookup"><span data-stu-id="666f5-157">When the durable duplex message exchange completes a result.xml file is saved to the C:\Inbox folder and contains the result of the message exchange.</span></span>  
  
#### <a name="to-cleanup-optional"></a><span data-ttu-id="666f5-158">Temizleme (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="666f5-158">To cleanup (Optional)</span></span>  
  
1.  <span data-ttu-id="666f5-159">CleanUp.cmd çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="666f5-159">Run Cleanup.cmd.</span></span>  
  
    1.  <span data-ttu-id="666f5-160">Açık bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut istemi.</span><span class="sxs-lookup"><span data-stu-id="666f5-160">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
    2.  <span data-ttu-id="666f5-161">Bu örnek için klasörüne gidin ve Cleanup.cmd çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="666f5-161">Navigate to the folder for this sample and run Cleanup.cmd.</span></span>  
  
2.  <span data-ttu-id="666f5-162">Sanal uygulama hizmetleri için kaldırın.</span><span class="sxs-lookup"><span data-stu-id="666f5-162">Remove the virtual application for the services.</span></span>  
  
    1.  <span data-ttu-id="666f5-163">Internet Information Services (IIS) Yöneticisi'ni çalıştırarak açmak `Inetmgr.exe` bir komut isteminden.</span><span class="sxs-lookup"><span data-stu-id="666f5-163">Open the Internet Information Services (IIS) Manager by running `Inetmgr.exe` from a command prompt.</span></span>  
  
    2.  <span data-ttu-id="666f5-164">Varsayılan Web sitesine gidin ve Kaldır **özel** sanal dizin.</span><span class="sxs-lookup"><span data-stu-id="666f5-164">Browse to the default Web site and remove the **private** virtual directory.</span></span>  
  
3.  <span data-ttu-id="666f5-165">Bu örnek için ayarlanan sıraları kaldırın.</span><span class="sxs-lookup"><span data-stu-id="666f5-165">Remove the queues set up for this sample.</span></span>  
  
    1.  <span data-ttu-id="666f5-166">Bilgisayar Yönetimi konsolunu açın `Compmgmt.msc` bir komut isteminden.</span><span class="sxs-lookup"><span data-stu-id="666f5-166">Open the Computer Management console by running `Compmgmt.msc` from a command prompt.</span></span>  
  
    2.  <span data-ttu-id="666f5-167">Genişletme **hizmet ve uygulamaları**, **Message Queuing**, **özel sıralar**.</span><span class="sxs-lookup"><span data-stu-id="666f5-167">Expand **Service and Applications**, **Message Queuing**, **Private Queues**.</span></span>  
  
    3.  <span data-ttu-id="666f5-168">Durableduplex/service1.xamlx ve durableduplex/service2.xamlx sıralar silin.</span><span class="sxs-lookup"><span data-stu-id="666f5-168">Delete the durableduplex/service1.xamlx and durableduplex/service2.xamlx queues.</span></span>  
  
4.  <span data-ttu-id="666f5-169">C:\Inbox dizini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="666f5-169">Remove the C:\Inbox directory.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="666f5-170">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="666f5-170">The samples may already be installed on your machine.</span></span> <span data-ttu-id="666f5-171">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="666f5-171">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="666f5-172">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="666f5-172">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="666f5-173">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="666f5-173">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDuplex`