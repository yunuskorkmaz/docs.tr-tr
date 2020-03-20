---
title: WAS Etkinleştirme Mimarisi
ms.date: 03/30/2017
ms.assetid: 58aeffb0-8f3f-4b40-80c8-15f3f1652fd3
ms.openlocfilehash: 67ddcd97ac75ddeb0765c38bb9ce7b5e8f039272
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184246"
---
# <a name="was-activation-architecture"></a><span data-ttu-id="51f51-102">WAS Etkinleştirme Mimarisi</span><span class="sxs-lookup"><span data-stu-id="51f51-102">WAS Activation Architecture</span></span>
<span data-ttu-id="51f51-103">Bu konu, Windows Process Etkinleştirme Hizmeti'nin (WAS olarak da bilinir) bileşenlerini ayrıntılı olarak bildirir ve tartışır.</span><span class="sxs-lookup"><span data-stu-id="51f51-103">This topic itemizes and discusses the components of the Windows Process Activation Service (also known as WAS).</span></span>  
  
## <a name="activation-components"></a><span data-ttu-id="51f51-104">Etkinleştirme Bileşenleri</span><span class="sxs-lookup"><span data-stu-id="51f51-104">Activation Components</span></span>  
 <span data-ttu-id="51f51-105">WAS çeşitli mimari bileşenlerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="51f51-105">WAS consists of several architectural components:</span></span>  
  
- <span data-ttu-id="51f51-106">Dinleyici adaptörleri.</span><span class="sxs-lookup"><span data-stu-id="51f51-106">Listener adapters.</span></span> <span data-ttu-id="51f51-107">Belirli ağ protokollerinde ileti alan ve gelen iletileri doğru alt işleme yönlendirmek için WAS ile iletişim sağlayan Windows hizmetleri.</span><span class="sxs-lookup"><span data-stu-id="51f51-107">Windows services that receive messages on specific network protocols and communicate with WAS to route incoming messages to the correct worker process.</span></span>  
  
- <span data-ttu-id="51f51-108">ÖYLEYDI.</span><span class="sxs-lookup"><span data-stu-id="51f51-108">WAS.</span></span> <span data-ttu-id="51f51-109">Alt işlemlerin oluşturulmasını ve kullanım ömrünü yöneten Windows hizmeti.</span><span class="sxs-lookup"><span data-stu-id="51f51-109">The Windows service that manages the creation and lifetime of worker processes.</span></span>  
  
- <span data-ttu-id="51f51-110">Genel alt işlem çalıştırılabilir (w3wp.exe).</span><span class="sxs-lookup"><span data-stu-id="51f51-110">The generic worker process executable (w3wp.exe).</span></span>  
  
- <span data-ttu-id="51f51-111">Başvuru yöneticisi.</span><span class="sxs-lookup"><span data-stu-id="51f51-111">Application manager.</span></span> <span data-ttu-id="51f51-112">Alt işlem içinde uygulamaları barındıran uygulama etki alanlarının oluşturulmasını ve kullanım ömrünü yönetir.</span><span class="sxs-lookup"><span data-stu-id="51f51-112">Manages the creation and lifetime of application domains that host applications within the worker process.</span></span>  
  
- <span data-ttu-id="51f51-113">Protokol işleyicileri.</span><span class="sxs-lookup"><span data-stu-id="51f51-113">Protocol handlers.</span></span> <span data-ttu-id="51f51-114">Alt işlemde çalışan ve alt işlem ile tek tek dinleyici bağdaştırıcıları arasındaki iletişimi yöneten protokole özgü bileşenler.</span><span class="sxs-lookup"><span data-stu-id="51f51-114">Protocol-specific components that run in the worker process and manage communication between the worker process and the individual listener adapters.</span></span> <span data-ttu-id="51f51-115">İki tür iletişim kuralı işleyicisi vardır: işlem protokolü işleyicileri ve AppDomain iletişim kuralı işleyicileri.</span><span class="sxs-lookup"><span data-stu-id="51f51-115">Two types of protocol handlers exist: process protocol handlers and AppDomain protocol handlers.</span></span>  
  
 <span data-ttu-id="51f51-116">WAS bir alt işlem örneğini etkinleştirdiğinde, gerekli işlem protokolü işleyicilerini alt işleme yükler ve uygulamayı barındıracak bir uygulama etki alanı oluşturmak için uygulama yöneticisini kullanır.</span><span class="sxs-lookup"><span data-stu-id="51f51-116">When WAS activates a worker process instance, it loads the process protocol handlers required into the worker process and uses the application manager to create an application domain to host the application.</span></span> <span data-ttu-id="51f51-117">Uygulama etki alanı, uygulamanın kodunu ve uygulama tarafından kullanılan ağ protokollerinin gerektirdiği AppDomain protokol işleyicilerini yükler.</span><span class="sxs-lookup"><span data-stu-id="51f51-117">The application domain loads the application’s code as well as the AppDomain protocol handlers that the network protocols used by the application require.</span></span>  
  
 ![WAS mimarisini gösteren ekran görüntüsü.](./media/was-activation-architecture/windows-process-application-service-architecture.gif)  
  
### <a name="listener-adapters"></a><span data-ttu-id="51f51-119">Dinleyici Adaptörleri</span><span class="sxs-lookup"><span data-stu-id="51f51-119">Listener Adapters</span></span>  
 <span data-ttu-id="51f51-120">Dinleyici bağdaştırıcıları, dinledikleri ağ iletişimini kullanarak ileti leri almak için kullanılan ağ iletişimi mantığını uygulayan tek tek Windows hizmetleridir.</span><span class="sxs-lookup"><span data-stu-id="51f51-120">Listener adapters are individual Windows services that implement the network communication logic used to receive messages using the network protocol on which they listen.</span></span> <span data-ttu-id="51f51-121">Aşağıdaki tabloda Windows Communication Foundation (WCF) protokolleri için dinleyici bağdaştırıcıları listelenir.</span><span class="sxs-lookup"><span data-stu-id="51f51-121">The following table lists the listener adapters for Windows Communication Foundation (WCF) protocols.</span></span>  
  
|<span data-ttu-id="51f51-122">Dinleyici bağdaştırıcı hizmet adı</span><span class="sxs-lookup"><span data-stu-id="51f51-122">Listener adapter service name</span></span>|<span data-ttu-id="51f51-123">Protokol</span><span class="sxs-lookup"><span data-stu-id="51f51-123">Protocol</span></span>|<span data-ttu-id="51f51-124">Notlar</span><span class="sxs-lookup"><span data-stu-id="51f51-124">Notes</span></span>|  
|-----------------------------------|--------------|-----------|  
|<span data-ttu-id="51f51-125">W3svc</span><span class="sxs-lookup"><span data-stu-id="51f51-125">W3SVC</span></span>|<span data-ttu-id="51f51-126">http</span><span class="sxs-lookup"><span data-stu-id="51f51-126">http</span></span>|<span data-ttu-id="51f51-127">Hem IIS 7.0 hem de WCF için HTTP etkinleştirme sağlayan ortak bileşen.</span><span class="sxs-lookup"><span data-stu-id="51f51-127">Common component that provides HTTP activation for both IIS 7.0 and WCF.</span></span>|  
|<span data-ttu-id="51f51-128">NetTcpActivator</span><span class="sxs-lookup"><span data-stu-id="51f51-128">NetTcpActivator</span></span>|<span data-ttu-id="51f51-129">net.tcp</span><span class="sxs-lookup"><span data-stu-id="51f51-129">net.tcp</span></span>|<span data-ttu-id="51f51-130">NetTcpPortSharing hizmetine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="51f51-130">Depends on the NetTcpPortSharing service.</span></span>|  
|<span data-ttu-id="51f51-131">NetPipeActivator</span><span class="sxs-lookup"><span data-stu-id="51f51-131">NetPipeActivator</span></span>|<span data-ttu-id="51f51-132">net.pipe</span><span class="sxs-lookup"><span data-stu-id="51f51-132">net.pipe</span></span>||  
|<span data-ttu-id="51f51-133">NetMsmqActivator</span><span class="sxs-lookup"><span data-stu-id="51f51-133">NetMsmqActivator</span></span>|<span data-ttu-id="51f51-134">net.msmq</span><span class="sxs-lookup"><span data-stu-id="51f51-134">net.msmq</span></span>|<span data-ttu-id="51f51-135">WCF tabanlı İleti Sıraya uygulamaları ile kullanım için.</span><span class="sxs-lookup"><span data-stu-id="51f51-135">For use with WCF-based Message Queuing applications.</span></span>|  
|<span data-ttu-id="51f51-136">NetMsmqActivator</span><span class="sxs-lookup"><span data-stu-id="51f51-136">NetMsmqActivator</span></span>|<span data-ttu-id="51f51-137">msmq.formatname</span><span class="sxs-lookup"><span data-stu-id="51f51-137">msmq.formatname</span></span>|<span data-ttu-id="51f51-138">Varolan İleti Sıralaması uygulamalarıyla geriye dönük uyumluluk sağlar.</span><span class="sxs-lookup"><span data-stu-id="51f51-138">Provides backwards compatibility with existing Message Queuing applications.</span></span>|  
  
 <span data-ttu-id="51f51-139">Belirli protokoller için dinleyici bağdaştırıcıları aşağıdaki XML örneğinde gösterildiği gibi applicationHost.config dosyasında yükleme sırasında kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="51f51-139">Listener adapters for specific protocols are registered during installation in the applicationHost.config file, as shown in the following XML example.</span></span>  
  
```xml  
<system.applicationHost>  
    <listenerAdapters>  
        <add name="http" />  
        <add name="net.tcp"
          identity="S-1-5-80-3579033775-2824656752-1522793541-1960352512-462907086" />  
         <add name="net.pipe"
           identity="S-1-5-80-2943419899-937267781-4189664001-1229628381-3982115073" />  
          <add name="net.msmq"
            identity="S-1-5-80-89244771-1762554971-1007993102-348796144-2203111529" />  
           <add name="msmq.formatname"
             identity="S-1-5-80-89244771-1762554971-1007993102-348796144-2203111529" />  
    </listenerAdapters>  
</system.applicationHost>  
```  
  
### <a name="protocol-handlers"></a><span data-ttu-id="51f51-140">Protokol Handleyicileri</span><span class="sxs-lookup"><span data-stu-id="51f51-140">Protocol Handlers</span></span>  
 <span data-ttu-id="51f51-141">Belirli protokoller için Işlem ve AppDomain protokol işleyicileri makine düzeyinde Web.config dosyasında kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="51f51-141">Process and AppDomain protocol handlers for specific protocols are registered in the machine-level Web.config file.</span></span>  
  
```xml  
<system.web>  
   <protocols>  
      <add name="net.tcp"
        processHandlerType=  
         "System.ServiceModel.WasHosting.TcpProcessProtocolHandler"  
        appDomainHandlerType=  
         "System.ServiceModel.WasHosting.TcpAppDomainProtocolHandler"  
        validate="false" />  
      <add name="net.pipe"
        processHandlerType=  
         "System.ServiceModel.WasHosting.NamedPipeProcessProtocolHandler"  
          appDomainHandlerType=  
           "System.ServiceModel.WasHosting.NamedPipeAppDomainProtocolHandler"/>  
      <add name="net.msmq"  
        processHandlerType=  
         "System.ServiceModel.WasHosting.MsmqProcessProtocolHandler"  
        appDomainHandlerType=  
         "System.ServiceModel.WasHosting.MsmqAppDomainProtocolHandler"  
        validate="false" />  
   </protocols>  
</system.web>  
```  
  
## <a name="see-also"></a><span data-ttu-id="51f51-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51f51-142">See also</span></span>

- [<span data-ttu-id="51f51-143">WAS'ı WCF ile Kullanmak için Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="51f51-143">Configuring WAS for Use with WCF</span></span>](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)
- <span data-ttu-id="51f51-144">[Windows Server App Kumaş Barındırma Özellikleri](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="51f51-144">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
