---
title: WAS Etkinleştirme Mimarisi
ms.date: 03/30/2017
ms.assetid: 58aeffb0-8f3f-4b40-80c8-15f3f1652fd3
ms.openlocfilehash: 64219649e7b743b7dd3a67673c3f2409aeeba486
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46325870"
---
# <a name="was-activation-architecture"></a><span data-ttu-id="83e6d-102">WAS Etkinleştirme Mimarisi</span><span class="sxs-lookup"><span data-stu-id="83e6d-102">WAS Activation Architecture</span></span>
<span data-ttu-id="83e6d-103">Bu konuda maddeler halinde listeler ve Windows İşlem Etkinleştirme Hizmeti (WAS olarak da bilinir) bileşenlerinin açıklar.</span><span class="sxs-lookup"><span data-stu-id="83e6d-103">This topic itemizes and discusses the components of the Windows Process Activation Service (also known as WAS).</span></span>  
  
## <a name="activation-components"></a><span data-ttu-id="83e6d-104">Etkinleştirme bileşenleri</span><span class="sxs-lookup"><span data-stu-id="83e6d-104">Activation Components</span></span>  
 <span data-ttu-id="83e6d-105">OLAN birkaç mimari bileşenden oluşur:</span><span class="sxs-lookup"><span data-stu-id="83e6d-105">WAS consists of several architectural components:</span></span>  
  
-   <span data-ttu-id="83e6d-106">Dinleyici bağdaştırıcıları.</span><span class="sxs-lookup"><span data-stu-id="83e6d-106">Listener adapters.</span></span> <span data-ttu-id="83e6d-107">Belirli ağ protokollerine iletileri almak ve doğru alt işleme gelen iletileri yönlendirmek için WAS ile iletişim kuran Windows Hizmetleri.</span><span class="sxs-lookup"><span data-stu-id="83e6d-107">Windows services that receive messages on specific network protocols and communicate with WAS to route incoming messages to the correct worker process.</span></span>  
  
-   <span data-ttu-id="83e6d-108">OLUŞTU.</span><span class="sxs-lookup"><span data-stu-id="83e6d-108">WAS.</span></span> <span data-ttu-id="83e6d-109">Oluşturulmasını ve alt işlemlerin yaşam süresini yöneten Windows hizmet.</span><span class="sxs-lookup"><span data-stu-id="83e6d-109">The Windows service that manages the creation and lifetime of worker processes.</span></span>  
  
-   <span data-ttu-id="83e6d-110">Genel çalışan işlemi (w3wp.exe) çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="83e6d-110">The generic worker process executable (w3wp.exe).</span></span>  
  
-   <span data-ttu-id="83e6d-111">Uygulama Yöneticisi.</span><span class="sxs-lookup"><span data-stu-id="83e6d-111">Application manager.</span></span> <span data-ttu-id="83e6d-112">Oluşturulmasını ve ana çalışan uygulamalardan işleyen bir uygulama etki alanları yaşam süresini yönetir.</span><span class="sxs-lookup"><span data-stu-id="83e6d-112">Manages the creation and lifetime of application domains that host applications within the worker process.</span></span>  
  
-   <span data-ttu-id="83e6d-113">Protokol işleyiciler.</span><span class="sxs-lookup"><span data-stu-id="83e6d-113">Protocol handlers.</span></span> <span data-ttu-id="83e6d-114">Çalışan işlem içinde çalıştırın ve bir dinleyici bağdaştırıcıları ile çalışan işlemi arasındaki iletişimi yöneten protokole özgü bileşenler.</span><span class="sxs-lookup"><span data-stu-id="83e6d-114">Protocol-specific components that run in the worker process and manage communication between the worker process and the individual listener adapters.</span></span> <span data-ttu-id="83e6d-115">Protokol işleyiciler iki tür vardır: işlem protokol işleyiciler ve AppDomain protokol işleyiciler.</span><span class="sxs-lookup"><span data-stu-id="83e6d-115">Two types of protocol handlers exist: process protocol handlers and AppDomain protocol handlers.</span></span>  
  
 <span data-ttu-id="83e6d-116">Zaman WAS bir çalışan işlem örneği etkinleştirir, çalışan işlemin gerekli işlem protokol işleyiciler yükler ve uygulama Yöneticisi uygulamasını barındırmak için bir uygulama etki alanı oluşturmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="83e6d-116">When WAS activates a worker process instance, it loads the process protocol handlers required into the worker process and uses the application manager to create an application domain to host the application.</span></span> <span data-ttu-id="83e6d-117">Uygulama etki alanı, uygulama kodunun yanı sıra ağ protokolleri uygulama iste tarafından kullanılan AppDomain protokol işleyiciler yükler.</span><span class="sxs-lookup"><span data-stu-id="83e6d-117">The application domain loads the application’s code as well as the AppDomain protocol handlers that the network protocols used by the application require.</span></span>  
  
 <span data-ttu-id="83e6d-118">![MİMARİSİDİR](../../../../docs/framework/wcf/feature-details/media/wasarchitecture.gif "WASArchitecture")</span><span class="sxs-lookup"><span data-stu-id="83e6d-118">![WAS Architecture](../../../../docs/framework/wcf/feature-details/media/wasarchitecture.gif "WASArchitecture")</span></span>  
  
### <a name="listener-adapters"></a><span data-ttu-id="83e6d-119">Dinleyici bağdaştırıcıları</span><span class="sxs-lookup"><span data-stu-id="83e6d-119">Listener Adapters</span></span>  
 <span data-ttu-id="83e6d-120">Dinleyici, üzerinde dinleme ağ protokolünü kullanarak ileti almak için kullanılan ağ iletişimi mantığını uygulayan Windows Hizmetleri tek tek bağdaştırıcıdır.</span><span class="sxs-lookup"><span data-stu-id="83e6d-120">Listener adapters are individual Windows services that implement the network communication logic used to receive messages using the network protocol on which they listen.</span></span> <span data-ttu-id="83e6d-121">Aşağıdaki tabloda, Windows Communication Foundation (WCF) protokolleri için dinleyici bağdaştırıcıları listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="83e6d-121">The following table lists the listener adapters for Windows Communication Foundation (WCF) protocols.</span></span>  
  
|<span data-ttu-id="83e6d-122">Dinleyici bağdaştırıcı hizmeti adı</span><span class="sxs-lookup"><span data-stu-id="83e6d-122">Listener adapter service name</span></span>|<span data-ttu-id="83e6d-123">Protokol</span><span class="sxs-lookup"><span data-stu-id="83e6d-123">Protocol</span></span>|<span data-ttu-id="83e6d-124">Notlar</span><span class="sxs-lookup"><span data-stu-id="83e6d-124">Notes</span></span>|  
|-----------------------------------|--------------|-----------|  
|<span data-ttu-id="83e6d-125">W3SVC</span><span class="sxs-lookup"><span data-stu-id="83e6d-125">W3SVC</span></span>|<span data-ttu-id="83e6d-126">http</span><span class="sxs-lookup"><span data-stu-id="83e6d-126">http</span></span>|<span data-ttu-id="83e6d-127">IIS 7.0 hem de WCF için HTTP etkinleştirme sağlayan ortak bileşeni.</span><span class="sxs-lookup"><span data-stu-id="83e6d-127">Common component that provides HTTP activation for both IIS 7.0 and WCF.</span></span>|  
|<span data-ttu-id="83e6d-128">NetTcpActivator</span><span class="sxs-lookup"><span data-stu-id="83e6d-128">NetTcpActivator</span></span>|<span data-ttu-id="83e6d-129">net.tcp</span><span class="sxs-lookup"><span data-stu-id="83e6d-129">net.tcp</span></span>|<span data-ttu-id="83e6d-130">NetTcpPortSharing hizmete bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="83e6d-130">Depends on the NetTcpPortSharing service.</span></span>|  
|<span data-ttu-id="83e6d-131">NetPipeActivator</span><span class="sxs-lookup"><span data-stu-id="83e6d-131">NetPipeActivator</span></span>|<span data-ttu-id="83e6d-132">net.pipe</span><span class="sxs-lookup"><span data-stu-id="83e6d-132">net.pipe</span></span>||  
|<span data-ttu-id="83e6d-133">NetMsmqActivator</span><span class="sxs-lookup"><span data-stu-id="83e6d-133">NetMsmqActivator</span></span>|<span data-ttu-id="83e6d-134">NET.MSMQ</span><span class="sxs-lookup"><span data-stu-id="83e6d-134">net.msmq</span></span>|<span data-ttu-id="83e6d-135">Message Queuing WCF tabanlı uygulamaları ile kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="83e6d-135">For use with WCF-based Message Queuing applications.</span></span>|  
|<span data-ttu-id="83e6d-136">NetMsmqActivator</span><span class="sxs-lookup"><span data-stu-id="83e6d-136">NetMsmqActivator</span></span>|<span data-ttu-id="83e6d-137">MSMQ.FormatName</span><span class="sxs-lookup"><span data-stu-id="83e6d-137">msmq.formatname</span></span>|<span data-ttu-id="83e6d-138">Geriye dönük uyumluluk Message Queuing var olan uygulamalarla birlikte sağlar.</span><span class="sxs-lookup"><span data-stu-id="83e6d-138">Provides backwards compatibility with existing Message Queuing applications.</span></span>|  
  
 <span data-ttu-id="83e6d-139">Dinleyici bağdaştırıcıları belirli protokoller için XML aşağıda gösterildiği gibi applicationHost.config dosyasında, yükleme sırasında kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="83e6d-139">Listener adapters for specific protocols are registered during installation in the applicationHost.config file, as shown in the following XML example.</span></span>  
  
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
  
### <a name="protocol-handlers"></a><span data-ttu-id="83e6d-140">Protokol işleyiciler</span><span class="sxs-lookup"><span data-stu-id="83e6d-140">Protocol Handlers</span></span>  
 <span data-ttu-id="83e6d-141">İşlem ve AppDomain protokol işleyiciler belirli protokoller için makine düzeyinde Web.config dosyasına kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="83e6d-141">Process and AppDomain protocol handlers for specific protocols are registered in the machine-level Web.config file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="83e6d-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="83e6d-142">See Also</span></span>  
 [<span data-ttu-id="83e6d-143">WAS'ı WCF ile Kullanmak için Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="83e6d-143">Configuring WAS for Use with WCF</span></span>](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)  
 [<span data-ttu-id="83e6d-144">Windows Server App Fabric barındırma özellikleri</span><span class="sxs-lookup"><span data-stu-id="83e6d-144">Windows Server App Fabric Hosting Features</span></span>](https://go.microsoft.com/fwlink/?LinkId=201276)
