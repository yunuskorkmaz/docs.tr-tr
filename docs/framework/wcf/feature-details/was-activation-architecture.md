---
title: WAS Etkinleştirme Mimarisi
ms.date: 03/30/2017
ms.assetid: 58aeffb0-8f3f-4b40-80c8-15f3f1652fd3
ms.openlocfilehash: 01c30db1182ece6dd968b69cc4efcaa2d9fabd79
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737506"
---
# <a name="was-activation-architecture"></a><span data-ttu-id="f4a73-102">WAS Etkinleştirme Mimarisi</span><span class="sxs-lookup"><span data-stu-id="f4a73-102">WAS Activation Architecture</span></span>
<span data-ttu-id="f4a73-103">Bu konu başlığı altında, Windows Işlem etkinleştirme hizmeti 'nin (WAS olarak da bilinir) bileşenleri ele alınmaktadır ve açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f4a73-103">This topic itemizes and discusses the components of the Windows Process Activation Service (also known as WAS).</span></span>  
  
## <a name="activation-components"></a><span data-ttu-id="f4a73-104">Etkinleştirme bileşenleri</span><span class="sxs-lookup"><span data-stu-id="f4a73-104">Activation Components</span></span>  
 <span data-ttu-id="f4a73-105">, Birkaç mimari bileşenden oluşur:</span><span class="sxs-lookup"><span data-stu-id="f4a73-105">WAS consists of several architectural components:</span></span>  
  
- <span data-ttu-id="f4a73-106">Dinleyici bağdaştırıcıları.</span><span class="sxs-lookup"><span data-stu-id="f4a73-106">Listener adapters.</span></span> <span data-ttu-id="f4a73-107">Belirli ağ protokollerine ileti alan ve ile iletişim kuran Windows Hizmetleri, gelen iletileri doğru çalışan sürecine yönlendirmelidir.</span><span class="sxs-lookup"><span data-stu-id="f4a73-107">Windows services that receive messages on specific network protocols and communicate with WAS to route incoming messages to the correct worker process.</span></span>  
  
- <span data-ttu-id="f4a73-108">Bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="f4a73-108">WAS.</span></span> <span data-ttu-id="f4a73-109">Çalışan işlemlerinin oluşturulmasını ve yaşam süresini yöneten Windows hizmeti.</span><span class="sxs-lookup"><span data-stu-id="f4a73-109">The Windows service that manages the creation and lifetime of worker processes.</span></span>  
  
- <span data-ttu-id="f4a73-110">Genel çalışan işlemi yürütülebilir dosya (W3wp. exe).</span><span class="sxs-lookup"><span data-stu-id="f4a73-110">The generic worker process executable (w3wp.exe).</span></span>  
  
- <span data-ttu-id="f4a73-111">Uygulama Yöneticisi.</span><span class="sxs-lookup"><span data-stu-id="f4a73-111">Application manager.</span></span> <span data-ttu-id="f4a73-112">Çalışan işlemi içinde uygulamaları barındıran uygulama etki alanlarının oluşturulmasını ve ömrünü yönetir.</span><span class="sxs-lookup"><span data-stu-id="f4a73-112">Manages the creation and lifetime of application domains that host applications within the worker process.</span></span>  
  
- <span data-ttu-id="f4a73-113">Protokol işleyicileri.</span><span class="sxs-lookup"><span data-stu-id="f4a73-113">Protocol handlers.</span></span> <span data-ttu-id="f4a73-114">Çalışan işleminde çalışan ve çalışan işlem ile ayrı dinleyici bağdaştırıcıları arasındaki iletişimi yöneten protokole özgü bileşenler.</span><span class="sxs-lookup"><span data-stu-id="f4a73-114">Protocol-specific components that run in the worker process and manage communication between the worker process and the individual listener adapters.</span></span> <span data-ttu-id="f4a73-115">İki tür protokol işleyicisi vardır: işlem protokol işleyicileri ve AppDomain protokol işleyicileri.</span><span class="sxs-lookup"><span data-stu-id="f4a73-115">Two types of protocol handlers exist: process protocol handlers and AppDomain protocol handlers.</span></span>  
  
 <span data-ttu-id="f4a73-116">, Bir çalışan işlem örneğini etkinleştirdiğinde, çalışan işlemine gereken işlem protokol işleyicilerini yükler ve uygulamayı barındırmak üzere uygulama etki alanı oluşturmak için uygulama yöneticisini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f4a73-116">When WAS activates a worker process instance, it loads the process protocol handlers required into the worker process and uses the application manager to create an application domain to host the application.</span></span> <span data-ttu-id="f4a73-117">Uygulama etki alanı, uygulamanın kodunun yanı sıra uygulama tarafından kullanılan ağ protokollerinin gerektirdiği AppDomain protokol işleyicilerini yükler.</span><span class="sxs-lookup"><span data-stu-id="f4a73-117">The application domain loads the application’s code as well as the AppDomain protocol handlers that the network protocols used by the application require.</span></span>  
  
 ![WAS mimarisini gösteren ekran görüntüsü.](./media/was-activation-architecture/windows-process-application-service-architecture.gif)  
  
### <a name="listener-adapters"></a><span data-ttu-id="f4a73-119">Dinleyici bağdaştırıcıları</span><span class="sxs-lookup"><span data-stu-id="f4a73-119">Listener Adapters</span></span>  
 <span data-ttu-id="f4a73-120">Dinleyici bağdaştırıcıları, dinleyeceği ağ protokolünü kullanarak ileti almak için kullanılan ağ iletişim mantığını uygulayan tek bir Windows hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="f4a73-120">Listener adapters are individual Windows services that implement the network communication logic used to receive messages using the network protocol on which they listen.</span></span> <span data-ttu-id="f4a73-121">Aşağıdaki tabloda Windows Communication Foundation (WCF) protokolleri için dinleyici bağdaştırıcıları listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="f4a73-121">The following table lists the listener adapters for Windows Communication Foundation (WCF) protocols.</span></span>  
  
|<span data-ttu-id="f4a73-122">Dinleyici bağdaştırıcısı hizmet adı</span><span class="sxs-lookup"><span data-stu-id="f4a73-122">Listener adapter service name</span></span>|<span data-ttu-id="f4a73-123">Protokol</span><span class="sxs-lookup"><span data-stu-id="f4a73-123">Protocol</span></span>|<span data-ttu-id="f4a73-124">Notlar</span><span class="sxs-lookup"><span data-stu-id="f4a73-124">Notes</span></span>|  
|-----------------------------------|--------------|-----------|  
|<span data-ttu-id="f4a73-125">ÇALıŞTıRıN</span><span class="sxs-lookup"><span data-stu-id="f4a73-125">W3SVC</span></span>|<span data-ttu-id="f4a73-126">http</span><span class="sxs-lookup"><span data-stu-id="f4a73-126">http</span></span>|<span data-ttu-id="f4a73-127">Hem IIS 7,0 hem de WCF için HTTP etkinleştirmesi sağlayan ortak bileşen.</span><span class="sxs-lookup"><span data-stu-id="f4a73-127">Common component that provides HTTP activation for both IIS 7.0 and WCF.</span></span>|  
|<span data-ttu-id="f4a73-128">Nettcpetkinleştirici</span><span class="sxs-lookup"><span data-stu-id="f4a73-128">NetTcpActivator</span></span>|<span data-ttu-id="f4a73-129">net.tcp</span><span class="sxs-lookup"><span data-stu-id="f4a73-129">net.tcp</span></span>|<span data-ttu-id="f4a73-130">NetTcpPortSharing hizmetine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="f4a73-130">Depends on the NetTcpPortSharing service.</span></span>|  
|<span data-ttu-id="f4a73-131">Netpipeetkinleştirici</span><span class="sxs-lookup"><span data-stu-id="f4a73-131">NetPipeActivator</span></span>|<span data-ttu-id="f4a73-132">net.pipe</span><span class="sxs-lookup"><span data-stu-id="f4a73-132">net.pipe</span></span>||  
|<span data-ttu-id="f4a73-133">Netmsmqetkinleştirici</span><span class="sxs-lookup"><span data-stu-id="f4a73-133">NetMsmqActivator</span></span>|<span data-ttu-id="f4a73-134">net.msmq</span><span class="sxs-lookup"><span data-stu-id="f4a73-134">net.msmq</span></span>|<span data-ttu-id="f4a73-135">WCF tabanlı Message Queuing uygulamalarıyla kullanım için.</span><span class="sxs-lookup"><span data-stu-id="f4a73-135">For use with WCF-based Message Queuing applications.</span></span>|  
|<span data-ttu-id="f4a73-136">Netmsmqetkinleştirici</span><span class="sxs-lookup"><span data-stu-id="f4a73-136">NetMsmqActivator</span></span>|<span data-ttu-id="f4a73-137">MSMQ. formatname</span><span class="sxs-lookup"><span data-stu-id="f4a73-137">msmq.formatname</span></span>|<span data-ttu-id="f4a73-138">Mevcut Message Queuing uygulamalarla geriye dönük uyumluluk sağlar.</span><span class="sxs-lookup"><span data-stu-id="f4a73-138">Provides backwards compatibility with existing Message Queuing applications.</span></span>|  
  
 <span data-ttu-id="f4a73-139">Belirli protokoller için dinleyici bağdaştırıcıları, aşağıdaki XML örneğinde gösterildiği gibi applicationHost. config dosyasına yükleme sırasında kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="f4a73-139">Listener adapters for specific protocols are registered during installation in the applicationHost.config file, as shown in the following XML example.</span></span>  
  
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
  
### <a name="protocol-handlers"></a><span data-ttu-id="f4a73-140">Protokol Işleyicileri</span><span class="sxs-lookup"><span data-stu-id="f4a73-140">Protocol Handlers</span></span>  
 <span data-ttu-id="f4a73-141">Belirli protokoller için işlem ve AppDomain protokol işleyicileri makine düzeyinde Web. config dosyasına kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="f4a73-141">Process and AppDomain protocol handlers for specific protocols are registered in the machine-level Web.config file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f4a73-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4a73-142">See also</span></span>

- [<span data-ttu-id="f4a73-143">WAS'ı WCF ile Kullanmak için Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f4a73-143">Configuring WAS for Use with WCF</span></span>](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)
- <span data-ttu-id="f4a73-144">[Windows Server App Fabric barındırma özellikleri](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="f4a73-144">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
