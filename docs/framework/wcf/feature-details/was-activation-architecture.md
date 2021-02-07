---
description: 'Daha fazla bilgi edinin: WAS etkinleştirme mimarisi'
title: WAS Etkinleştirme Mimarisi
ms.date: 03/30/2017
ms.assetid: 58aeffb0-8f3f-4b40-80c8-15f3f1652fd3
ms.openlocfilehash: 616b3b404258356bcd5600c68b6f70aaf096e978
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756025"
---
# <a name="was-activation-architecture"></a><span data-ttu-id="91145-103">WAS Etkinleştirme Mimarisi</span><span class="sxs-lookup"><span data-stu-id="91145-103">WAS Activation Architecture</span></span>

<span data-ttu-id="91145-104">Bu konu başlığı altında, Windows Işlem etkinleştirme hizmeti 'nin (WAS olarak da bilinir) bileşenleri ele alınmaktadır ve açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="91145-104">This topic itemizes and discusses the components of the Windows Process Activation Service (also known as WAS).</span></span>  
  
## <a name="activation-components"></a><span data-ttu-id="91145-105">Etkinleştirme bileşenleri</span><span class="sxs-lookup"><span data-stu-id="91145-105">Activation Components</span></span>  

 <span data-ttu-id="91145-106">, Birkaç mimari bileşenden oluşur:</span><span class="sxs-lookup"><span data-stu-id="91145-106">WAS consists of several architectural components:</span></span>  
  
- <span data-ttu-id="91145-107">Dinleyici bağdaştırıcıları.</span><span class="sxs-lookup"><span data-stu-id="91145-107">Listener adapters.</span></span> <span data-ttu-id="91145-108">Belirli ağ protokollerine ileti alan ve ile iletişim kuran Windows Hizmetleri, gelen iletileri doğru çalışan sürecine yönlendirmelidir.</span><span class="sxs-lookup"><span data-stu-id="91145-108">Windows services that receive messages on specific network protocols and communicate with WAS to route incoming messages to the correct worker process.</span></span>  
  
- <span data-ttu-id="91145-109">Bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="91145-109">WAS.</span></span> <span data-ttu-id="91145-110">Çalışan işlemlerinin oluşturulmasını ve yaşam süresini yöneten Windows hizmeti.</span><span class="sxs-lookup"><span data-stu-id="91145-110">The Windows service that manages the creation and lifetime of worker processes.</span></span>  
  
- <span data-ttu-id="91145-111">Genel çalışan işlemi yürütülebilir (w3wp.exe).</span><span class="sxs-lookup"><span data-stu-id="91145-111">The generic worker process executable (w3wp.exe).</span></span>  
  
- <span data-ttu-id="91145-112">Uygulama Yöneticisi.</span><span class="sxs-lookup"><span data-stu-id="91145-112">Application manager.</span></span> <span data-ttu-id="91145-113">Çalışan işlemi içinde uygulamaları barındıran uygulama etki alanlarının oluşturulmasını ve ömrünü yönetir.</span><span class="sxs-lookup"><span data-stu-id="91145-113">Manages the creation and lifetime of application domains that host applications within the worker process.</span></span>  
  
- <span data-ttu-id="91145-114">Protokol işleyicileri.</span><span class="sxs-lookup"><span data-stu-id="91145-114">Protocol handlers.</span></span> <span data-ttu-id="91145-115">Çalışan işleminde çalışan ve çalışan işlem ile ayrı dinleyici bağdaştırıcıları arasındaki iletişimi yöneten protokole özgü bileşenler.</span><span class="sxs-lookup"><span data-stu-id="91145-115">Protocol-specific components that run in the worker process and manage communication between the worker process and the individual listener adapters.</span></span> <span data-ttu-id="91145-116">İki tür protokol işleyicisi vardır: işlem protokol işleyicileri ve AppDomain protokol işleyicileri.</span><span class="sxs-lookup"><span data-stu-id="91145-116">Two types of protocol handlers exist: process protocol handlers and AppDomain protocol handlers.</span></span>  
  
 <span data-ttu-id="91145-117">, Bir çalışan işlem örneğini etkinleştirdiğinde, çalışan işlemine gereken işlem protokol işleyicilerini yükler ve uygulamayı barındırmak üzere uygulama etki alanı oluşturmak için uygulama yöneticisini kullanır.</span><span class="sxs-lookup"><span data-stu-id="91145-117">When WAS activates a worker process instance, it loads the process protocol handlers required into the worker process and uses the application manager to create an application domain to host the application.</span></span> <span data-ttu-id="91145-118">Uygulama etki alanı, uygulamanın kodunun yanı sıra uygulama tarafından kullanılan ağ protokollerinin gerektirdiği AppDomain protokol işleyicilerini yükler.</span><span class="sxs-lookup"><span data-stu-id="91145-118">The application domain loads the application’s code as well as the AppDomain protocol handlers that the network protocols used by the application require.</span></span>  
  
 ![WAS mimarisini gösteren ekran görüntüsü.](./media/was-activation-architecture/windows-process-application-service-architecture.gif)  
  
### <a name="listener-adapters"></a><span data-ttu-id="91145-120">Dinleyici bağdaştırıcıları</span><span class="sxs-lookup"><span data-stu-id="91145-120">Listener Adapters</span></span>  

 <span data-ttu-id="91145-121">Dinleyici bağdaştırıcıları, dinleyeceği ağ protokolünü kullanarak ileti almak için kullanılan ağ iletişim mantığını uygulayan tek bir Windows hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="91145-121">Listener adapters are individual Windows services that implement the network communication logic used to receive messages using the network protocol on which they listen.</span></span> <span data-ttu-id="91145-122">Aşağıdaki tabloda Windows Communication Foundation (WCF) protokolleri için dinleyici bağdaştırıcıları listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="91145-122">The following table lists the listener adapters for Windows Communication Foundation (WCF) protocols.</span></span>  
  
|<span data-ttu-id="91145-123">Dinleyici bağdaştırıcısı hizmet adı</span><span class="sxs-lookup"><span data-stu-id="91145-123">Listener adapter service name</span></span>|<span data-ttu-id="91145-124">Protokol</span><span class="sxs-lookup"><span data-stu-id="91145-124">Protocol</span></span>|<span data-ttu-id="91145-125">Notlar</span><span class="sxs-lookup"><span data-stu-id="91145-125">Notes</span></span>|  
|-----------------------------------|--------------|-----------|  
|<span data-ttu-id="91145-126">ÇALıŞTıRıN</span><span class="sxs-lookup"><span data-stu-id="91145-126">W3SVC</span></span>|<span data-ttu-id="91145-127">http</span><span class="sxs-lookup"><span data-stu-id="91145-127">http</span></span>|<span data-ttu-id="91145-128">Hem IIS 7,0 hem de WCF için HTTP etkinleştirmesi sağlayan ortak bileşen.</span><span class="sxs-lookup"><span data-stu-id="91145-128">Common component that provides HTTP activation for both IIS 7.0 and WCF.</span></span>|  
|<span data-ttu-id="91145-129">Nettcpetkinleştirici</span><span class="sxs-lookup"><span data-stu-id="91145-129">NetTcpActivator</span></span>|<span data-ttu-id="91145-130">net.tcp</span><span class="sxs-lookup"><span data-stu-id="91145-130">net.tcp</span></span>|<span data-ttu-id="91145-131">NetTcpPortSharing hizmetine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="91145-131">Depends on the NetTcpPortSharing service.</span></span>|  
|<span data-ttu-id="91145-132">Netpipeetkinleştirici</span><span class="sxs-lookup"><span data-stu-id="91145-132">NetPipeActivator</span></span>|<span data-ttu-id="91145-133">net.pipe</span><span class="sxs-lookup"><span data-stu-id="91145-133">net.pipe</span></span>||  
|<span data-ttu-id="91145-134">Netmsmqetkinleştirici</span><span class="sxs-lookup"><span data-stu-id="91145-134">NetMsmqActivator</span></span>|<span data-ttu-id="91145-135">net. MSMQ</span><span class="sxs-lookup"><span data-stu-id="91145-135">net.msmq</span></span>|<span data-ttu-id="91145-136">WCF tabanlı Message Queuing uygulamalarıyla kullanım için.</span><span class="sxs-lookup"><span data-stu-id="91145-136">For use with WCF-based Message Queuing applications.</span></span>|  
|<span data-ttu-id="91145-137">Netmsmqetkinleştirici</span><span class="sxs-lookup"><span data-stu-id="91145-137">NetMsmqActivator</span></span>|<span data-ttu-id="91145-138">MSMQ. formatname</span><span class="sxs-lookup"><span data-stu-id="91145-138">msmq.formatname</span></span>|<span data-ttu-id="91145-139">Mevcut Message Queuing uygulamalarla geriye dönük uyumluluk sağlar.</span><span class="sxs-lookup"><span data-stu-id="91145-139">Provides backwards compatibility with existing Message Queuing applications.</span></span>|  
  
 <span data-ttu-id="91145-140">Belirli protokoller için dinleyici bağdaştırıcıları, aşağıdaki XML örneğinde gösterildiği gibi applicationHost.config dosyasına yükleme sırasında kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="91145-140">Listener adapters for specific protocols are registered during installation in the applicationHost.config file, as shown in the following XML example.</span></span>  
  
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
  
### <a name="protocol-handlers"></a><span data-ttu-id="91145-141">Protokol Işleyicileri</span><span class="sxs-lookup"><span data-stu-id="91145-141">Protocol Handlers</span></span>  

 <span data-ttu-id="91145-142">Belirli protokoller için işlem ve AppDomain protokol işleyicileri makine düzeyinde Web.config dosyasına kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="91145-142">Process and AppDomain protocol handlers for specific protocols are registered in the machine-level Web.config file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="91145-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91145-143">See also</span></span>

- [<span data-ttu-id="91145-144">WAS'ı WCF ile Kullanmak için Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="91145-144">Configuring WAS for Use with WCF</span></span>](configuring-the-wpa--service-for-use-with-wcf.md)
- <span data-ttu-id="91145-145">[Windows Server App Fabric barındırma özellikleri](/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="91145-145">[Windows Server App Fabric Hosting Features](/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
