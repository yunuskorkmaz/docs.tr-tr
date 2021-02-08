---
description: 'Daha fazla bilgi edinin: UDP etkinleştirmesi'
title: UDP Etkinleştirme
ms.date: 03/30/2017
ms.assetid: 4b0ccd10-0dfb-4603-93f9-f0857c581cb7
ms.openlocfilehash: 8ee5e6363265ddc74d27884ef40354108da17581
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798231"
---
# <a name="udp-activation"></a><span data-ttu-id="66545-103">UDP Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="66545-103">UDP Activation</span></span>

<span data-ttu-id="66545-104">Bu örnek, [taşıma: UDP](transport-udp.md) örneğine dayalıdır.</span><span class="sxs-lookup"><span data-stu-id="66545-104">This sample is based on the [Transport: UDP](transport-udp.md) sample.</span></span> <span data-ttu-id="66545-105">Bu işlem, Windows Işlem etkinleştirme hizmeti 'ni (WAS) kullanarak işlem etkinleştirmeyi desteklemek için [iletim: UDP](transport-udp.md) örneğini genişletir.</span><span class="sxs-lookup"><span data-stu-id="66545-105">It extends the [Transport: UDP](transport-udp.md) sample to support process activation using the Windows Process Activation Service (WAS).</span></span>  
  
 <span data-ttu-id="66545-106">Örnek üç ana parçadan oluşur:</span><span class="sxs-lookup"><span data-stu-id="66545-106">The sample consists of three major pieces:</span></span>  
  
- <span data-ttu-id="66545-107">Etkinleştirilecek uygulamalar adına UDP iletileri alan tek başına bir işlem olan UDP protokol Etkinleştirici.</span><span class="sxs-lookup"><span data-stu-id="66545-107">A UDP Protocol Activator, a standalone process that receives UDP messages on behalf of applications that are to be activated.</span></span>  
  
- <span data-ttu-id="66545-108">İleti göndermek için UDP özel aktarımını kullanan bir istemci.</span><span class="sxs-lookup"><span data-stu-id="66545-108">A client that uses the UDP custom transport to send messages.</span></span>  
  
- <span data-ttu-id="66545-109">UDP özel aktarımı üzerinden ileti alan bir hizmet (tarafından etkinleştirilen bir çalışan işleminde barındırılan).</span><span class="sxs-lookup"><span data-stu-id="66545-109">A service (hosted in a worker process activated by WAS) that receives messages over the UDP custom transport.</span></span>  
  
## <a name="udp-protocol-activator"></a><span data-ttu-id="66545-110">UDP protokol Etkinleştirici</span><span class="sxs-lookup"><span data-stu-id="66545-110">UDP Protocol Activator</span></span>  

 <span data-ttu-id="66545-111">UDP protokol Etkinleştirici, WCF istemcisi ile WCF hizmeti arasında bir köprüdir.</span><span class="sxs-lookup"><span data-stu-id="66545-111">The UDP Protocol Activator is a bridge between the WCF client and the WCF service.</span></span> <span data-ttu-id="66545-112">Aktarım katmanında UDP protokolü aracılığıyla veri iletişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="66545-112">It provides data communication through the UDP protocol at the transport layer.</span></span> <span data-ttu-id="66545-113">İki ana işleve sahiptir:</span><span class="sxs-lookup"><span data-stu-id="66545-113">It has two major functions:</span></span>  
  
- <span data-ttu-id="66545-114">İle işbirliği yapılan dinleyici bağdaştırıcısı (LA), gelen iletilere yanıt olarak işlemlerin ETKINLEŞTIRILME süreciydi.</span><span class="sxs-lookup"><span data-stu-id="66545-114">WAS Listener Adapter (LA), which collaborates with WAS to activate processes in response to incoming messages.</span></span>  
  
- <span data-ttu-id="66545-115">Etkinleştirilecek uygulamalar adına UDP iletileri kabul eden UDP Protokol dinleyicisi.</span><span class="sxs-lookup"><span data-stu-id="66545-115">UDP Protocol Listener, which accepts UDP messages on behalf of applications that are to be activated.</span></span>  
  
 <span data-ttu-id="66545-116">Etkinleştirici, sunucu makinesinde tek başına bir program olarak çalışıyor olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="66545-116">The activator must be running as a standalone program on the server machine.</span></span> <span data-ttu-id="66545-117">Normal olarak, WAS (Nettcpetkinleştirici ve Netpipeetkinleştirici gibi), uzun süre çalışan Windows hizmetlerinde uygulanan dinleyici bağdaştırıcılarıdır.</span><span class="sxs-lookup"><span data-stu-id="66545-117">Normally, WAS listener adapters (such as the NetTcpActivator and the NetPipeActivator) are implemented in long-running Windows services.</span></span> <span data-ttu-id="66545-118">Ancak kolaylık sağlaması ve açıklık için bu örnek, bağımsız bir uygulama olarak protokol Etkinleştirici uygular.</span><span class="sxs-lookup"><span data-stu-id="66545-118">However, for simplicity and clarity, this sample implements the protocol activator as a standalone application.</span></span>  
  
### <a name="was-listener-adapter"></a><span data-ttu-id="66545-119">WAS dinleyicisi bağdaştırıcısı</span><span class="sxs-lookup"><span data-stu-id="66545-119">WAS Listener Adapter</span></span>  

 <span data-ttu-id="66545-120">UDP için WAS dinleyicisi bağdaştırıcısı `UdpListenerAdapter` sınıfında uygulanır.</span><span class="sxs-lookup"><span data-stu-id="66545-120">The WAS Listener Adapter for UDP is implemented in the `UdpListenerAdapter` class.</span></span> <span data-ttu-id="66545-121">Bu, ile etkileşim kuran modüldür.</span><span class="sxs-lookup"><span data-stu-id="66545-121">It is the module that interacts with WAS to perform application activation for the UDP protocol.</span></span> <span data-ttu-id="66545-122">Bu, aşağıdaki Webhost API 'Leri çağırarak elde edilir:</span><span class="sxs-lookup"><span data-stu-id="66545-122">This is achieved by calling the following Webhost APIs:</span></span>  
  
- `WebhostRegisterProtocol`  
  
- `WebhostUnregisterProtocol`  
  
- `WebhostOpenListenerChannelInstance`  
  
- `WebhostCloseAllListenerChannelInstances`  
  
 <span data-ttu-id="66545-123">İlk kez çağrıldıktan sonra `WebhostRegisterProtocol` , dinleyici bağdaştırıcısı `ApplicationCreated` applicationHost.config ' de kayıtlı tüm uygulamalar için was geri çağırma işlemini alır (%Windir%\System32\inetsrv dizininde bulunur).</span><span class="sxs-lookup"><span data-stu-id="66545-123">After initially calling `WebhostRegisterProtocol`, the listener adapter receives the callback `ApplicationCreated` from WAS for all of the applications registered in applicationHost.config (located in %windir%\system32\inetsrv).</span></span> <span data-ttu-id="66545-124">Bu örnekte, yalnızca UDP protokolüne sahip uygulamaları (Protokol Kimliği "net. UDP") etkin olarak işleyeceğiz.</span><span class="sxs-lookup"><span data-stu-id="66545-124">In this sample, we only handle the applications with the UDP protocol (with the protocol id as "net.udp") enabled.</span></span> <span data-ttu-id="66545-125">Bu tür uygulamalar uygulamaya dinamik yapılandırma değişikliklerine yanıt vermezse (örneğin, devre dışı durumundan etkin 'e geçiş), diğer uygulamalar bunu farklı şekilde işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="66545-125">Other implementations may handle this differently if such implementations respond to dynamic configuration changes to the application (for example, an application transition from disabled to enabled).</span></span>  
  
 <span data-ttu-id="66545-126">Geri arama `ConfigManagerInitializationCompleted` alındığında, bu, protokolünün başlatılmasına yönelik tüm bildirimlerin tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="66545-126">When the callback `ConfigManagerInitializationCompleted` is received, it indicates that WAS has finished all of the notifications for the initialization of the protocol.</span></span> <span data-ttu-id="66545-127">Şu anda, dinleyici bağdaştırıcısı etkinleştirme isteklerini işlemeye hazırlanıyor.</span><span class="sxs-lookup"><span data-stu-id="66545-127">At this time, the listener adapter is ready to process activation requests.</span></span>  
  
 <span data-ttu-id="66545-128">Bir uygulama için yeni bir istek ilk kez geldiğinde, dinleyici bağdaştırıcısı `WebhostOpenListenerChannelInstance` henüz başlatılmadıysa çalışan işlemini başlatan was öğesine çağrılır.</span><span class="sxs-lookup"><span data-stu-id="66545-128">When a new request comes in the first time for an application, the listener adapter calls `WebhostOpenListenerChannelInstance` into WAS, which starts the worker process if it is not started yet.</span></span> <span data-ttu-id="66545-129">Ardından protokol işleyicileri yüklenir ve dinleyici bağdaştırıcısı ile sanal uygulama arasındaki iletişim başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="66545-129">Then the protocol handlers are loaded and the communication between the listener adapter and the virtual application can start.</span></span>  
  
 <span data-ttu-id="66545-130">Dinleyici bağdaştırıcısı, `listenerAdapters` aşağıda gösterildiği gibi <> bölümünde% SystemRoot% \System32\inetsrv\ApplicationHost.config kaydedilir:</span><span class="sxs-lookup"><span data-stu-id="66545-130">The listener adapter is registered in the %SystemRoot%\System32\inetsrv\ApplicationHost.config in the <`listenerAdapters`> section as following:</span></span>  
  
```xml  
<add name="net.udp" identity="S-1-5-21-2127521184-1604012920-1887927527-387045" />  
```  
  
### <a name="protocol-listener"></a><span data-ttu-id="66545-131">Protokol dinleyicisi</span><span class="sxs-lookup"><span data-stu-id="66545-131">Protocol Listener</span></span>  

 <span data-ttu-id="66545-132">UDP Protokol dinleyicisi, sanal uygulama adına bir UDP uç noktasında dinleme yapan protokol Etkinleştirici içindeki bir modüldür.</span><span class="sxs-lookup"><span data-stu-id="66545-132">The UDP protocol listener is a module inside the protocol activator that listens at a UDP endpoint on behalf of the virtual application.</span></span> <span data-ttu-id="66545-133">Sınıfında uygulanır `UdpSocketListener` .</span><span class="sxs-lookup"><span data-stu-id="66545-133">It is implemented in the class `UdpSocketListener`.</span></span> <span data-ttu-id="66545-134">Uç noktası, `IPEndpoint` bağlantı noktası numarasının site için protokolün bağlamalarından ayıklandığı şekilde temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="66545-134">The endpoint is represented as `IPEndpoint` for which the port number is extracted from the binding of the protocol for the site.</span></span>  
  
### <a name="control-service"></a><span data-ttu-id="66545-135">Denetim Hizmeti</span><span class="sxs-lookup"><span data-stu-id="66545-135">Control Service</span></span>  

 <span data-ttu-id="66545-136">Bu örnekte, Etkinleştirici ile WAS çalışan işlemi arasında iletişim kurmak için WCF kullanırız.</span><span class="sxs-lookup"><span data-stu-id="66545-136">In this sample, we use WCF to communicate between the activator and the WAS worker process.</span></span> <span data-ttu-id="66545-137">Etkinleştirici içinde bulunan hizmete denetim hizmeti denir.</span><span class="sxs-lookup"><span data-stu-id="66545-137">The service that resides in the activator is called the Control Service.</span></span>  
  
## <a name="protocol-handlers"></a><span data-ttu-id="66545-138">Protokol Işleyicileri</span><span class="sxs-lookup"><span data-stu-id="66545-138">Protocol Handlers</span></span>  

 <span data-ttu-id="66545-139">Dinleyici bağdaştırıcısı gerçekleştirildikten sonra `WebhostOpenListenerChannelInstance` , was işlem yöneticisi başlatılmamışsa çalışan işlemi başlatır.</span><span class="sxs-lookup"><span data-stu-id="66545-139">After the listener adapter calls `WebhostOpenListenerChannelInstance`, the WAS process manager starts the worker process if it is not started.</span></span> <span data-ttu-id="66545-140">Ardından çalışan işleminin içindeki uygulama Yöneticisi, UDP Işlem Protokolü Işleyicisini (PPH) bunun isteğiyle yükler `ListenerChannelId` .</span><span class="sxs-lookup"><span data-stu-id="66545-140">The application manager inside the worker process then loads the UDP Process Protocol Handler (PPH) with the request for that `ListenerChannelId`.</span></span> <span data-ttu-id="66545-141">İçindeki PPH, çağrıları dönüştürür `IAdphManager` .`StartAppDomainProtocolListenerChannel`</span><span class="sxs-lookup"><span data-stu-id="66545-141">The PPH in turns calls `IAdphManager`.`StartAppDomainProtocolListenerChannel`</span></span> <span data-ttu-id="66545-142">UDP AppDomain protokol Işleyicisini (ADPH) başlatmak için.</span><span class="sxs-lookup"><span data-stu-id="66545-142">to start the UDP AppDomain Protocol Handler (ADPH).</span></span>  
  
## <a name="hostedudptransportconfiguration"></a><span data-ttu-id="66545-143">HostedUDPTransportConfiguration</span><span class="sxs-lookup"><span data-stu-id="66545-143">HostedUDPTransportConfiguration</span></span>  

 <span data-ttu-id="66545-144">Bilgiler Web.config şu şekilde kaydedilir:</span><span class="sxs-lookup"><span data-stu-id="66545-144">The information is registered in the Web.config as follows:</span></span>  
  
```xml  
<serviceHostingEnvironment>  
<add name="net.udp" transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />  
</serviceHostingEnvironment>  
```  
  
## <a name="special-setup-for-this-sample"></a><span data-ttu-id="66545-145">Bu örnek için özel kurulum</span><span class="sxs-lookup"><span data-stu-id="66545-145">Special Setup for This Sample</span></span>  

 <span data-ttu-id="66545-146">Bu örnek yalnızca Windows Vista, Windows Server 2008 veya Windows 7 üzerinde oluşturulup çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="66545-146">This sample can be only built and run on Windows Vista, Windows Server 2008, or Windows 7.</span></span> <span data-ttu-id="66545-147">Örneği çalıştırmak için, önce tüm bileşenlerin doğru şekilde ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="66545-147">To run the sample, you must first get all of the components set up correctly.</span></span> <span data-ttu-id="66545-148">Örneği yüklemek için aşağıdaki adımları kullanın.</span><span class="sxs-lookup"><span data-stu-id="66545-148">Use the following steps to install the sample.</span></span>  
  
#### <a name="to-set-up-this-sample"></a><span data-ttu-id="66545-149">Bu örneği ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="66545-149">To set up this sample</span></span>  
  
1. <span data-ttu-id="66545-150">Aşağıdaki komutu kullanarak ASP.NET 4,0 ' ü yükler.</span><span class="sxs-lookup"><span data-stu-id="66545-150">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="66545-151">Projeyi Windows Vista 'da derleyin.</span><span class="sxs-lookup"><span data-stu-id="66545-151">Build the project on Windows Vista.</span></span> <span data-ttu-id="66545-152">Derlemeden sonra, derleme sonrası aşamasında aşağıdaki işlemleri de gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="66545-152">After compilation, it also performs the following operations in the post-build phase:</span></span>  
  
    - <span data-ttu-id="66545-153">"Default Web site" sitesine UDP bağlamasını kurar.</span><span class="sxs-lookup"><span data-stu-id="66545-153">Installs the UDP binding to the site "Default Web Site".</span></span>  
  
    - <span data-ttu-id="66545-154">"ServiceModelSamples" sanal uygulamasını "%SystemDrive%\inetpub\wwwroot\servicemodelsamples" fiziksel yolunu işaret etmek üzere oluşturur.</span><span class="sxs-lookup"><span data-stu-id="66545-154">Creates the virtual application "ServiceModelSamples" to point to the physical path: "%SystemDrive%\inetpub\wwwroot\servicemodelsamples".</span></span>  
  
    - <span data-ttu-id="66545-155">Ayrıca, bu sanal uygulama için "net. UDP" protokolünü de sunar.</span><span class="sxs-lookup"><span data-stu-id="66545-155">It also enables "net.udp" protocol for this virtual application.</span></span>  
  
3. <span data-ttu-id="66545-156">"WasNetActivator.exe" Kullanıcı arabirimi uygulamasını başlatın.</span><span class="sxs-lookup"><span data-stu-id="66545-156">Start the user interface application "WasNetActivator.exe".</span></span> <span data-ttu-id="66545-157">**Kurulum** sekmesine tıklayın, aşağıdaki onay kutularını işaretleyin ve ardından yüklemek için **yükleme** ' ye tıklayın:</span><span class="sxs-lookup"><span data-stu-id="66545-157">Click the **Setup** tab, check the following check boxes and then click **Install** to install them:</span></span>  
  
    - <span data-ttu-id="66545-158">UDP dinleyicisi bağdaştırıcısı</span><span class="sxs-lookup"><span data-stu-id="66545-158">UDP Listener Adapter</span></span>  
  
    - <span data-ttu-id="66545-159">UDP protokol Işleyicileri</span><span class="sxs-lookup"><span data-stu-id="66545-159">UDP Protocol Handlers</span></span>  
  
4. <span data-ttu-id="66545-160">"WasNetActivator.exe" Kullanıcı arabirimi uygulamasının **etkinleştirme** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="66545-160">Click the **Activation** tab of the user interface application "WasNetActivator.exe".</span></span> <span data-ttu-id="66545-161">Dinleyici bağdaştırıcısını başlatmak için **Başlat** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="66545-161">Click the **Start** button to start the listener adapter.</span></span> <span data-ttu-id="66545-162">Şimdi programı çalıştırmaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="66545-162">Now you are ready to run the program.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="66545-163">Bu örnekle işiniz bittiğinde, "Default Web site" kaynağından net. UDP bağlamasını kaldırmak için Cleanup.bat çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="66545-163">When you are finished with this sample, you must run Cleanup.bat to remove the net.udp binding from the "Default Web Site".</span></span>  
  
## <a name="sample-usage"></a><span data-ttu-id="66545-164">Örnek Kullanım</span><span class="sxs-lookup"><span data-stu-id="66545-164">Sample Usage</span></span>  

 <span data-ttu-id="66545-165">Derlemeden sonra oluşturulan dört farklı ikili dosya vardır:</span><span class="sxs-lookup"><span data-stu-id="66545-165">After compilation, there are four different binaries generated:</span></span>  
  
- <span data-ttu-id="66545-166">Client.exe: istemci kodu.</span><span class="sxs-lookup"><span data-stu-id="66545-166">Client.exe: The client code.</span></span> <span data-ttu-id="66545-167">App.config, Client.exe.config istemci yapılandırma dosyasına derlenir.</span><span class="sxs-lookup"><span data-stu-id="66545-167">The App.config is compiled into the client configuration file Client.exe.config.</span></span>  
  
- <span data-ttu-id="66545-168">UDPActivation.dll: Ana UDP uygulamalarının tümünü içeren kitaplık.</span><span class="sxs-lookup"><span data-stu-id="66545-168">UDPActivation.dll: the library that contains all of the major UDP implementations.</span></span>  
  
- <span data-ttu-id="66545-169">Service.dll: hizmet kodu.</span><span class="sxs-lookup"><span data-stu-id="66545-169">Service.dll: The service code.</span></span> <span data-ttu-id="66545-170">Bu, ServiceModelSamples sanal uygulamasının \bin dizinine kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="66545-170">This is copied to the \bin directory of the virtual application ServiceModelSamples.</span></span> <span data-ttu-id="66545-171">Hizmet dosyası, Service. svc ve yapılandırma dosyası Web.config. Derlemeden sonra, bunlar şu konuma kopyalanır:%SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="66545-171">The service file is Service.svc and the configuration file is Web.config. After compilation, they are copied to the following location: %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.</span></span>  
  
- <span data-ttu-id="66545-172">Lınetactivator: UDP Etkinleştirici programı.</span><span class="sxs-lookup"><span data-stu-id="66545-172">WasNetActivator: The UDP activator program.</span></span>  
  
- <span data-ttu-id="66545-173">Tüm gerekli parçaların düzgün yüklendiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="66545-173">Ensure that all of the required pieces are installed correctly.</span></span> <span data-ttu-id="66545-174">Aşağıdaki adımlar, örneğin nasıl çalıştırılacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="66545-174">The following steps show how to run the sample:</span></span>  
  
1. <span data-ttu-id="66545-175">Aşağıdaki Windows hizmetlerinin başlatıldığından emin olun:</span><span class="sxs-lookup"><span data-stu-id="66545-175">Ensure that the following Windows services have been started:</span></span>  
  
    - <span data-ttu-id="66545-176">Windows Işlem etkinleştirme hizmeti (WAS).</span><span class="sxs-lookup"><span data-stu-id="66545-176">Windows Process Activation Service (WAS).</span></span>  
  
    - <span data-ttu-id="66545-177">Internet Information Services (IIS): W3SVC.</span><span class="sxs-lookup"><span data-stu-id="66545-177">Internet Information Services (IIS): W3SVC.</span></span>  
  
2. <span data-ttu-id="66545-178">Ardından, WasNetActivator.exe Etkinleştirici başlatın.</span><span class="sxs-lookup"><span data-stu-id="66545-178">Then start the activator, WasNetActivator.exe.</span></span> <span data-ttu-id="66545-179">**Etkinleştirme** sekmesi altında, iletişim kutusunda yalnızca **UDP** olan protokol seçilidir.</span><span class="sxs-lookup"><span data-stu-id="66545-179">Under the **Activation** tab, the only protocol, **UDP**, is selected in the drop down list.</span></span> <span data-ttu-id="66545-180">Etkinleştirici 'yi başlatmak için **Başlat** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="66545-180">Click the **Start** button to start the activator.</span></span>  
  
3. <span data-ttu-id="66545-181">Etkinleştirici başlatıldıktan sonra, bir komut penceresinden Client.exe çalıştırarak istemci kodunu çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66545-181">Once the activator is started, you can run the client code by running Client.exe from a command window.</span></span> <span data-ttu-id="66545-182">Örnek çıktı aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="66545-182">The following is the sample output:</span></span>  
  
    ```console  
    Testing Udp Activation.  
    Start the status service.  
    Sending UDP datagrams.  
    Type a word that you want to say to the server: Hello, world!  
        Sending datagram: Hello, world![0]  
        Sending datagram: Hello, world![1]  
        Sending datagram: Hello, world![2]  
        Sending datagram: Hello, world![3]  
        Sending datagram: Hello, world![4]  
    Calling UDP duplex contract (ICalculatorContract).  
        0 + 0 = 0  
        1 + 2 = 3  
        2 + 4 = 6  
        3 + 6 = 9  
        4 + 8 = 12  
    Getting status and dump server traces:  
        Operation 'Hello' is called: Hello, world![0]  
        Operation 'Hello' is called: Hello, world![1]  
        Operation 'Hello' is called: Hello, world![2]  
        Operation 'Hello' is called: Hello, world![3]  
        Operation 'Hello' is called: Hello, world![4]  
        Operation 'Add' is called: 0 + 0  
        Operation 'Add' is called: 1 + 2  
        Operation 'Add' is called: 2 + 4  
        Operation 'Add' is called: 3 + 6  
        Operation 'Add' is called: 4 + 8  
    Press <ENTER> to complete test.  
    ```  
  
> [!IMPORTANT]
> <span data-ttu-id="66545-183">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="66545-183">The samples may already be installed on your machine.</span></span> <span data-ttu-id="66545-184">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="66545-184">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="66545-185">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="66545-185">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="66545-186">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="66545-186">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\UdpActivation`  
