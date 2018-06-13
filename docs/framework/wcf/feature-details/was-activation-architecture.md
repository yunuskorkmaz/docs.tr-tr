---
title: WAS Etkinleştirme Mimarisi
ms.date: 03/30/2017
ms.assetid: 58aeffb0-8f3f-4b40-80c8-15f3f1652fd3
ms.openlocfilehash: 0c91ebd605fbe503dd11da7167512648afd86449
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498003"
---
# <a name="was-activation-architecture"></a><span data-ttu-id="72bd4-102">WAS Etkinleştirme Mimarisi</span><span class="sxs-lookup"><span data-stu-id="72bd4-102">WAS Activation Architecture</span></span>
<span data-ttu-id="72bd4-103">Bu konuda maddeler halinde listelemektedir ve Windows İşlem Etkinleştirme Hizmeti (WAS olarak da bilinir) bileşenlerinin açıklanır.</span><span class="sxs-lookup"><span data-stu-id="72bd4-103">This topic itemizes and discusses the components of the Windows Process Activation Service (also known as WAS).</span></span>  
  
## <a name="activation-components"></a><span data-ttu-id="72bd4-104">Etkinleştirme bileşenleri</span><span class="sxs-lookup"><span data-stu-id="72bd4-104">Activation Components</span></span>  
 <span data-ttu-id="72bd4-105">OLAN birkaç mimari bileşenden oluşur:</span><span class="sxs-lookup"><span data-stu-id="72bd4-105">WAS consists of several architectural components:</span></span>  
  
-   <span data-ttu-id="72bd4-106">Dinleyici Bağdaştırıcısı yok.</span><span class="sxs-lookup"><span data-stu-id="72bd4-106">Listener adapters.</span></span> <span data-ttu-id="72bd4-107">Belirli ağ protokollerine iletileri almak ve doğru çalışan işlemi için gelen iletileri yönlendirmek için WAS ile iletişim kuran Windows Hizmetleri.</span><span class="sxs-lookup"><span data-stu-id="72bd4-107">Windows services that receive messages on specific network protocols and communicate with WAS to route incoming messages to the correct worker process.</span></span>  
  
-   <span data-ttu-id="72bd4-108">OLUŞTU.</span><span class="sxs-lookup"><span data-stu-id="72bd4-108">WAS.</span></span> <span data-ttu-id="72bd4-109">Oluşturulmasını ve yaşam çalışan işlemleri yöneten Windows hizmeti.</span><span class="sxs-lookup"><span data-stu-id="72bd4-109">The Windows service that manages the creation and lifetime of worker processes.</span></span>  
  
-   <span data-ttu-id="72bd4-110">Genel çalışan işlem yürütülebilir dosyası (w3wp.exe).</span><span class="sxs-lookup"><span data-stu-id="72bd4-110">The generic worker process executable (w3wp.exe).</span></span>  
  
-   <span data-ttu-id="72bd4-111">Uygulama Yöneticisi.</span><span class="sxs-lookup"><span data-stu-id="72bd4-111">Application manager.</span></span> <span data-ttu-id="72bd4-112">Oluşturulmasını ve yaşam süresini konak uygulamaların içinde çalışan işlem uygulama etki alanları yönetir.</span><span class="sxs-lookup"><span data-stu-id="72bd4-112">Manages the creation and lifetime of application domains that host applications within the worker process.</span></span>  
  
-   <span data-ttu-id="72bd4-113">Protokol işleyici.</span><span class="sxs-lookup"><span data-stu-id="72bd4-113">Protocol handlers.</span></span> <span data-ttu-id="72bd4-114">Çalışan işlemde çalıştırın ve çalışan işlemin ve tek tek dinleyici bağdaştırıcısı arasındaki iletişimi yöneten protokole özgü bileşenleri.</span><span class="sxs-lookup"><span data-stu-id="72bd4-114">Protocol-specific components that run in the worker process and manage communication between the worker process and the individual listener adapters.</span></span> <span data-ttu-id="72bd4-115">Protokol işleyici iki tür var: işlem protokol işleyici ve AppDomain protokol işleyici.</span><span class="sxs-lookup"><span data-stu-id="72bd4-115">Two types of protocol handlers exist: process protocol handlers and AppDomain protocol handlers.</span></span>  
  
 <span data-ttu-id="72bd4-116">Olduğunda WAS bir çalışan işlem örneği etkinleştirir çalışan işlemine gerekli işlem protokol işleyici yükler ve uygulama barındırmak için uygulama etki alanı oluşturmak için uygulama Yöneticisi'ni kullanır.</span><span class="sxs-lookup"><span data-stu-id="72bd4-116">When WAS activates a worker process instance, it loads the process protocol handlers required into the worker process and uses the application manager to create an application domain to host the application.</span></span> <span data-ttu-id="72bd4-117">Uygulama etki alanı, uygulama kodunun yanı sıra uygulama iste tarafından kullanılan ağ protokolleri AppDomain protokol işleyici yükler.</span><span class="sxs-lookup"><span data-stu-id="72bd4-117">The application domain loads the application’s code as well as the AppDomain protocol handlers that the network protocols used by the application require.</span></span>  
  
 <span data-ttu-id="72bd4-118">![MİMARİSİDİR](../../../../docs/framework/wcf/feature-details/media/wasarchitecture.gif "WASArchitecture")</span><span class="sxs-lookup"><span data-stu-id="72bd4-118">![WAS Architecture](../../../../docs/framework/wcf/feature-details/media/wasarchitecture.gif "WASArchitecture")</span></span>  
  
### <a name="listener-adapters"></a><span data-ttu-id="72bd4-119">Dinleyici Bağdaştırıcısı</span><span class="sxs-lookup"><span data-stu-id="72bd4-119">Listener Adapters</span></span>  
 <span data-ttu-id="72bd4-120">Dinleyici Bağdaştırıcısı üzerinde dinleme ağ protokolünü kullanarak ileti almak için kullanılan ağ iletişimi mantığını uygulayan ayrı Windows hizmetleridir.</span><span class="sxs-lookup"><span data-stu-id="72bd4-120">Listener adapters are individual Windows services that implement the network communication logic used to receive messages using the network protocol on which they listen.</span></span> <span data-ttu-id="72bd4-121">Aşağıdaki tabloda, Windows Communication Foundation (WCF) protokoller için Dinleyici Bağdaştırıcısı listeler.</span><span class="sxs-lookup"><span data-stu-id="72bd4-121">The following table lists the listener adapters for Windows Communication Foundation (WCF) protocols.</span></span>  
  
|<span data-ttu-id="72bd4-122">Dinleyici Bağdaştırıcısı hizmet adı</span><span class="sxs-lookup"><span data-stu-id="72bd4-122">Listener adapter service name</span></span>|<span data-ttu-id="72bd4-123">Protokol</span><span class="sxs-lookup"><span data-stu-id="72bd4-123">Protocol</span></span>|<span data-ttu-id="72bd4-124">Notlar</span><span class="sxs-lookup"><span data-stu-id="72bd4-124">Notes</span></span>|  
|-----------------------------------|--------------|-----------|  
|<span data-ttu-id="72bd4-125">W3SVC</span><span class="sxs-lookup"><span data-stu-id="72bd4-125">W3SVC</span></span>|<span data-ttu-id="72bd4-126">http</span><span class="sxs-lookup"><span data-stu-id="72bd4-126">http</span></span>|<span data-ttu-id="72bd4-127">IIS 7.0 ve WCF HTTP etkinleştirmesi sağlayan ortak bileşeni.</span><span class="sxs-lookup"><span data-stu-id="72bd4-127">Common component that provides HTTP activation for both IIS 7.0 and WCF.</span></span>|  
|<span data-ttu-id="72bd4-128">NetTcpActivator</span><span class="sxs-lookup"><span data-stu-id="72bd4-128">NetTcpActivator</span></span>|<span data-ttu-id="72bd4-129">net.tcp</span><span class="sxs-lookup"><span data-stu-id="72bd4-129">net.tcp</span></span>|<span data-ttu-id="72bd4-130">NetTcpPortSharing hizmete bağlı.</span><span class="sxs-lookup"><span data-stu-id="72bd4-130">Depends on the NetTcpPortSharing service.</span></span>|  
|<span data-ttu-id="72bd4-131">NetPipeActivator</span><span class="sxs-lookup"><span data-stu-id="72bd4-131">NetPipeActivator</span></span>|<span data-ttu-id="72bd4-132">net.pipe</span><span class="sxs-lookup"><span data-stu-id="72bd4-132">net.pipe</span></span>||  
|<span data-ttu-id="72bd4-133">NetMsmqActivator</span><span class="sxs-lookup"><span data-stu-id="72bd4-133">NetMsmqActivator</span></span>|<span data-ttu-id="72bd4-134">NET.MSMQ</span><span class="sxs-lookup"><span data-stu-id="72bd4-134">net.msmq</span></span>|<span data-ttu-id="72bd4-135">Message Queuing WCF tabanlı uygulamaları ile kullanım için.</span><span class="sxs-lookup"><span data-stu-id="72bd4-135">For use with WCF-based Message Queuing applications.</span></span>|  
|<span data-ttu-id="72bd4-136">NetMsmqActivator</span><span class="sxs-lookup"><span data-stu-id="72bd4-136">NetMsmqActivator</span></span>|<span data-ttu-id="72bd4-137">MSMQ.FormatName</span><span class="sxs-lookup"><span data-stu-id="72bd4-137">msmq.formatname</span></span>|<span data-ttu-id="72bd4-138">Geriye dönük uyumluluk varolan Message Queuing uygulamaları ile sağlar.</span><span class="sxs-lookup"><span data-stu-id="72bd4-138">Provides backwards compatibility with existing Message Queuing applications.</span></span>|  
  
 <span data-ttu-id="72bd4-139">Dinleyici Bağdaştırıcısı belirli protokoller için aşağıdaki XML örnekte gösterildiği gibi applicationHost.config dosyasında, yükleme sırasında kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="72bd4-139">Listener adapters for specific protocols are registered during installation in the applicationHost.config file, as shown in the following XML example.</span></span>  
  
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
  
### <a name="protocol-handlers"></a><span data-ttu-id="72bd4-140">Protokol işleyici</span><span class="sxs-lookup"><span data-stu-id="72bd4-140">Protocol Handlers</span></span>  
 <span data-ttu-id="72bd4-141">İşlem ve AppDomain protokol işleyici belirli protokoller için makine düzeyinde Web.config dosyasına kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="72bd4-141">Process and AppDomain protocol handlers for specific protocols are registered in the machine-level Web.config file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="72bd4-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="72bd4-142">See Also</span></span>  
 [<span data-ttu-id="72bd4-143">WAS'ı WCF ile Kullanmak için Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="72bd4-143">Configuring WAS for Use with WCF</span></span>](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)  
 [<span data-ttu-id="72bd4-144">Windows Server App Fabric barındırma özellikleri</span><span class="sxs-lookup"><span data-stu-id="72bd4-144">Windows Server App Fabric Hosting Features</span></span>](http://go.microsoft.com/fwlink/?LinkId=201276)
