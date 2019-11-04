---
title: UDP Etkinleştirme
ms.date: 03/30/2017
ms.assetid: 4b0ccd10-0dfb-4603-93f9-f0857c581cb7
ms.openlocfilehash: 6e8d2f4428e85c71571021e2735f90e2e0a9d35a
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424184"
---
# <a name="udp-activation"></a><span data-ttu-id="57b52-102">UDP Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="57b52-102">UDP Activation</span></span>
<span data-ttu-id="57b52-103">Bu örnek, [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örneğine dayalıdır.</span><span class="sxs-lookup"><span data-stu-id="57b52-103">This sample is based on the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span> <span data-ttu-id="57b52-104">Bu işlem, Windows Işlem etkinleştirme hizmeti 'ni (WAS) kullanarak işlem etkinleştirmeyi desteklemek için [iletim: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örneğini genişletir.</span><span class="sxs-lookup"><span data-stu-id="57b52-104">It extends the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample to support process activation using the Windows Process Activation Service (WAS).</span></span>  
  
 <span data-ttu-id="57b52-105">Örnek üç ana parçadan oluşur:</span><span class="sxs-lookup"><span data-stu-id="57b52-105">The sample consists of three major pieces:</span></span>  
  
- <span data-ttu-id="57b52-106">Etkinleştirilecek uygulamalar adına UDP iletileri alan tek başına bir işlem olan UDP protokol Etkinleştirici.</span><span class="sxs-lookup"><span data-stu-id="57b52-106">A UDP Protocol Activator, a standalone process that receives UDP messages on behalf of applications that are to be activated.</span></span>  
  
- <span data-ttu-id="57b52-107">İleti göndermek için UDP özel aktarımını kullanan bir istemci.</span><span class="sxs-lookup"><span data-stu-id="57b52-107">A client that uses the UDP custom transport to send messages.</span></span>  
  
- <span data-ttu-id="57b52-108">UDP özel aktarımı üzerinden ileti alan bir hizmet (tarafından etkinleştirilen bir çalışan işleminde barındırılan).</span><span class="sxs-lookup"><span data-stu-id="57b52-108">A service (hosted in a worker process activated by WAS) that receives messages over the UDP custom transport.</span></span>  
  
## <a name="udp-protocol-activator"></a><span data-ttu-id="57b52-109">UDP protokol Etkinleştirici</span><span class="sxs-lookup"><span data-stu-id="57b52-109">UDP Protocol Activator</span></span>  
 <span data-ttu-id="57b52-110">UDP protokol Etkinleştirici, WCF istemcisi ile WCF hizmeti arasında bir köprüdir.</span><span class="sxs-lookup"><span data-stu-id="57b52-110">The UDP Protocol Activator is a bridge between the WCF client and the WCF service.</span></span> <span data-ttu-id="57b52-111">Aktarım katmanında UDP protokolü aracılığıyla veri iletişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="57b52-111">It provides data communication through the UDP protocol at the transport layer.</span></span> <span data-ttu-id="57b52-112">İki ana işleve sahiptir:</span><span class="sxs-lookup"><span data-stu-id="57b52-112">It has two major functions:</span></span>  
  
- <span data-ttu-id="57b52-113">İle işbirliği yapılan dinleyici bağdaştırıcısı (LA), gelen iletilere yanıt olarak işlemlerin ETKINLEŞTIRILME süreciydi.</span><span class="sxs-lookup"><span data-stu-id="57b52-113">WAS Listener Adapter (LA), which collaborates with WAS to activate processes in response to incoming messages.</span></span>  
  
- <span data-ttu-id="57b52-114">Etkinleştirilecek uygulamalar adına UDP iletileri kabul eden UDP Protokol dinleyicisi.</span><span class="sxs-lookup"><span data-stu-id="57b52-114">UDP Protocol Listener, which accepts UDP messages on behalf of applications that are to be activated.</span></span>  
  
 <span data-ttu-id="57b52-115">Etkinleştirici, sunucu makinesinde tek başına bir program olarak çalışıyor olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="57b52-115">The activator must be running as a standalone program on the server machine.</span></span> <span data-ttu-id="57b52-116">Normal olarak, WAS (Nettcpetkinleştirici ve Netpipeetkinleştirici gibi), uzun süre çalışan Windows hizmetlerinde uygulanan dinleyici bağdaştırıcılarıdır.</span><span class="sxs-lookup"><span data-stu-id="57b52-116">Normally, WAS listener adapters (such as the NetTcpActivator and the NetPipeActivator) are implemented in long-running Windows services.</span></span> <span data-ttu-id="57b52-117">Ancak kolaylık sağlaması ve açıklık için bu örnek, bağımsız bir uygulama olarak protokol Etkinleştirici uygular.</span><span class="sxs-lookup"><span data-stu-id="57b52-117">However, for simplicity and clarity, this sample implements the protocol activator as a standalone application.</span></span>  
  
### <a name="was-listener-adapter"></a><span data-ttu-id="57b52-118">WAS dinleyicisi bağdaştırıcısı</span><span class="sxs-lookup"><span data-stu-id="57b52-118">WAS Listener Adapter</span></span>  
 <span data-ttu-id="57b52-119">UDP için WAS dinleyicisi bağdaştırıcısı `UdpListenerAdapter` sınıfında uygulanır.</span><span class="sxs-lookup"><span data-stu-id="57b52-119">The WAS Listener Adapter for UDP is implemented in the `UdpListenerAdapter` class.</span></span> <span data-ttu-id="57b52-120">Bu, ile etkileşim kuran modüldür.</span><span class="sxs-lookup"><span data-stu-id="57b52-120">It is the module that interacts with WAS to perform application activation for the UDP protocol.</span></span> <span data-ttu-id="57b52-121">Bu, aşağıdaki Webhost API 'Leri çağırarak elde edilir:</span><span class="sxs-lookup"><span data-stu-id="57b52-121">This is achieved by calling the following Webhost APIs:</span></span>  
  
- `WebhostRegisterProtocol`  
  
- `WebhostUnregisterProtocol`  
  
- `WebhostOpenListenerChannelInstance`  
  
- `WebhostCloseAllListenerChannelInstances`  
  
 <span data-ttu-id="57b52-122">İlk olarak `WebhostRegisterProtocol`çağrıldıktan sonra, dinleyici bağdaştırıcısı applicationHost. config dosyasında kayıtlı tüm uygulamalar için WAS `ApplicationCreated` geri çağırma işlemini alır (%Windir%\System32\inetsrv içinde bulunur).</span><span class="sxs-lookup"><span data-stu-id="57b52-122">After initially calling `WebhostRegisterProtocol`, the listener adapter receives the callback `ApplicationCreated` from WAS for all of the applications registered in applicationHost.config (located in %windir%\system32\inetsrv).</span></span> <span data-ttu-id="57b52-123">Bu örnekte, yalnızca UDP protokolüne sahip uygulamaları (Protokol Kimliği "net. UDP") etkin olarak işleyeceğiz.</span><span class="sxs-lookup"><span data-stu-id="57b52-123">In this sample, we only handle the applications with the UDP protocol (with the protocol id as "net.udp") enabled.</span></span> <span data-ttu-id="57b52-124">Bu tür uygulamalar uygulamaya dinamik yapılandırma değişikliklerine yanıt vermezse (örneğin, devre dışı durumundan etkin 'e geçiş), diğer uygulamalar bunu farklı şekilde işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="57b52-124">Other implementations may handle this differently if such implementations respond to dynamic configuration changes to the application (for example, an application transition from disabled to enabled).</span></span>  
  
 <span data-ttu-id="57b52-125">Geri çağırma `ConfigManagerInitializationCompleted` alındığında, bu, protokolünün başlatılmasına yönelik tüm bildirimlerin tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="57b52-125">When the callback `ConfigManagerInitializationCompleted` is received, it indicates that WAS has finished all of the notifications for the initialization of the protocol.</span></span> <span data-ttu-id="57b52-126">Şu anda, dinleyici bağdaştırıcısı etkinleştirme isteklerini işlemeye hazırlanıyor.</span><span class="sxs-lookup"><span data-stu-id="57b52-126">At this time, the listener adapter is ready to process activation requests.</span></span>  
  
 <span data-ttu-id="57b52-127">Bir uygulama için yeni bir istek ilk kez geldiğinde, dinleyici bağdaştırıcısı henüz başlatılmadıysa çalışan işlemini başlatan WAS ' a `WebhostOpenListenerChannelInstance` çağırır.</span><span class="sxs-lookup"><span data-stu-id="57b52-127">When a new request comes in the first time for an application, the listener adapter calls `WebhostOpenListenerChannelInstance` into WAS, which starts the worker process if it is not started yet.</span></span> <span data-ttu-id="57b52-128">Ardından protokol işleyicileri yüklenir ve dinleyici bağdaştırıcısı ile sanal uygulama arasındaki iletişim başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="57b52-128">Then the protocol handlers are loaded and the communication between the listener adapter and the virtual application can start.</span></span>  
  
 <span data-ttu-id="57b52-129">Dinleyici bağdaştırıcısı, aşağıdaki gibi <`listenerAdapters`> bölümünde%SystemRoot%\system32\inetsrv\applicationhost,config dosyasına kaydedilir:</span><span class="sxs-lookup"><span data-stu-id="57b52-129">The listener adapter is registered in the %SystemRoot%\System32\inetsrv\ApplicationHost.config in the <`listenerAdapters`> section as following:</span></span>  
  
```xml  
<add name="net.udp" identity="S-1-5-21-2127521184-1604012920-1887927527-387045" />  
```  
  
### <a name="protocol-listener"></a><span data-ttu-id="57b52-130">Protokol dinleyicisi</span><span class="sxs-lookup"><span data-stu-id="57b52-130">Protocol Listener</span></span>  
 <span data-ttu-id="57b52-131">UDP Protokol dinleyicisi, sanal uygulama adına bir UDP uç noktasında dinleme yapan protokol Etkinleştirici içindeki bir modüldür.</span><span class="sxs-lookup"><span data-stu-id="57b52-131">The UDP protocol listener is a module inside the protocol activator that listens at a UDP endpoint on behalf of the virtual application.</span></span> <span data-ttu-id="57b52-132">`UdpSocketListener`sınıfında uygulanır.</span><span class="sxs-lookup"><span data-stu-id="57b52-132">It is implemented in the class `UdpSocketListener`.</span></span> <span data-ttu-id="57b52-133">Uç nokta, site için protokol bağlamalarından bağlantı noktası numarasının ayıklandığı `IPEndpoint` olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="57b52-133">The endpoint is represented as `IPEndpoint` for which the port number is extracted from the binding of the protocol for the site.</span></span>  
  
### <a name="control-service"></a><span data-ttu-id="57b52-134">Denetim Hizmeti</span><span class="sxs-lookup"><span data-stu-id="57b52-134">Control Service</span></span>  
 <span data-ttu-id="57b52-135">Bu örnekte, Etkinleştirici ile WAS çalışan işlemi arasında iletişim kurmak için WCF kullanırız.</span><span class="sxs-lookup"><span data-stu-id="57b52-135">In this sample, we use WCF to communicate between the activator and the WAS worker process.</span></span> <span data-ttu-id="57b52-136">Etkinleştirici içinde bulunan hizmete denetim hizmeti denir.</span><span class="sxs-lookup"><span data-stu-id="57b52-136">The service that resides in the activator is called the Control Service.</span></span>  
  
## <a name="protocol-handlers"></a><span data-ttu-id="57b52-137">Protokol Işleyicileri</span><span class="sxs-lookup"><span data-stu-id="57b52-137">Protocol Handlers</span></span>  
 <span data-ttu-id="57b52-138">Dinleyici bağdaştırıcısı `WebhostOpenListenerChannelInstance`çağırdıktan sonra, WAS işlem yöneticisi başlatılmamışsa çalışan işlemini başlatır.</span><span class="sxs-lookup"><span data-stu-id="57b52-138">After the listener adapter calls `WebhostOpenListenerChannelInstance`, the WAS process manager starts the worker process if it is not started.</span></span> <span data-ttu-id="57b52-139">Çalışan işleminin içindeki uygulama Yöneticisi daha sonra bu `ListenerChannelId`isteği ile UDP Işlem Protokolü Işleyicisini (PPH) yükler.</span><span class="sxs-lookup"><span data-stu-id="57b52-139">The application manager inside the worker process then loads the UDP Process Protocol Handler (PPH) with the request for that `ListenerChannelId`.</span></span> <span data-ttu-id="57b52-140">İçindeki PPH, `IAdphManager`çağırır.`StartAppDomainProtocolListenerChannel`</span><span class="sxs-lookup"><span data-stu-id="57b52-140">The PPH in turns calls `IAdphManager`.`StartAppDomainProtocolListenerChannel`</span></span> <span data-ttu-id="57b52-141">UDP AppDomain protokol Işleyicisini (ADPH) başlatmak için.</span><span class="sxs-lookup"><span data-stu-id="57b52-141">to start the UDP AppDomain Protocol Handler (ADPH).</span></span>  
  
## <a name="hostedudptransportconfiguration"></a><span data-ttu-id="57b52-142">HostedUDPTransportConfiguration</span><span class="sxs-lookup"><span data-stu-id="57b52-142">HostedUDPTransportConfiguration</span></span>  
 <span data-ttu-id="57b52-143">Bilgiler, Web. config dosyasına aşağıdaki şekilde kaydedilir:</span><span class="sxs-lookup"><span data-stu-id="57b52-143">The information is registered in the Web.config as follows:</span></span>  
  
```xml  
<serviceHostingEnvironment>  
<add name="net.udp" transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />  
</serviceHostingEnvironment>  
```  
  
## <a name="special-setup-for-this-sample"></a><span data-ttu-id="57b52-144">Bu örnek için özel kurulum</span><span class="sxs-lookup"><span data-stu-id="57b52-144">Special Setup for This Sample</span></span>  
 <span data-ttu-id="57b52-145">Bu örnek yalnızca Windows Vista, Windows Server 2008 veya Windows 7 üzerinde oluşturulup çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="57b52-145">This sample can be only built and run on Windows Vista, Windows Server 2008, or Windows 7.</span></span> <span data-ttu-id="57b52-146">Örneği çalıştırmak için, önce tüm bileşenlerin doğru şekilde ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="57b52-146">To run the sample, you must first get all of the components set up correctly.</span></span> <span data-ttu-id="57b52-147">Örneği yüklemek için aşağıdaki adımları kullanın.</span><span class="sxs-lookup"><span data-stu-id="57b52-147">Use the following steps to install the sample.</span></span>  
  
#### <a name="to-set-up-this-sample"></a><span data-ttu-id="57b52-148">Bu örneği ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="57b52-148">To set up this sample</span></span>  
  
1. <span data-ttu-id="57b52-149">Aşağıdaki komutu kullanarak ASP.NET 4,0 ' ü yükler.</span><span class="sxs-lookup"><span data-stu-id="57b52-149">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="57b52-150">Projeyi Windows Vista 'da derleyin.</span><span class="sxs-lookup"><span data-stu-id="57b52-150">Build the project on Windows Vista.</span></span> <span data-ttu-id="57b52-151">Derlemeden sonra, derleme sonrası aşamasında aşağıdaki işlemleri de gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="57b52-151">After compilation, it also performs the following operations in the post-build phase:</span></span>  
  
    - <span data-ttu-id="57b52-152">"Default Web site" sitesine UDP bağlamasını kurar.</span><span class="sxs-lookup"><span data-stu-id="57b52-152">Installs the UDP binding to the site "Default Web Site".</span></span>  
  
    - <span data-ttu-id="57b52-153">"ServiceModelSamples" sanal uygulamasını "%SystemDrive%\inetpub\wwwroot\servicemodelsamples" fiziksel yolunu işaret etmek üzere oluşturur.</span><span class="sxs-lookup"><span data-stu-id="57b52-153">Creates the virtual application "ServiceModelSamples" to point to the physical path: "%SystemDrive%\inetpub\wwwroot\servicemodelsamples".</span></span>  
  
    - <span data-ttu-id="57b52-154">Ayrıca, bu sanal uygulama için "net. UDP" protokolünü de sunar.</span><span class="sxs-lookup"><span data-stu-id="57b52-154">It also enables "net.udp" protocol for this virtual application.</span></span>  
  
3. <span data-ttu-id="57b52-155">"Tnewtactivator. exe" Kullanıcı arabirimi uygulamasını başlatın.</span><span class="sxs-lookup"><span data-stu-id="57b52-155">Start the user interface application "WasNetActivator.exe".</span></span> <span data-ttu-id="57b52-156">**Kurulum** sekmesine tıklayın, aşağıdaki onay kutularını işaretleyin ve ardından yüklemek için **yükleme** ' ye tıklayın:</span><span class="sxs-lookup"><span data-stu-id="57b52-156">Click the **Setup** tab, check the following check boxes and then click **Install** to install them:</span></span>  
  
    - <span data-ttu-id="57b52-157">UDP dinleyicisi bağdaştırıcısı</span><span class="sxs-lookup"><span data-stu-id="57b52-157">UDP Listener Adapter</span></span>  
  
    - <span data-ttu-id="57b52-158">UDP protokol Işleyicileri</span><span class="sxs-lookup"><span data-stu-id="57b52-158">UDP Protocol Handlers</span></span>  
  
4. <span data-ttu-id="57b52-159">"Lınetactivator. exe" Kullanıcı arabirimi uygulamasının **etkinleştirme** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="57b52-159">Click the **Activation** tab of the user interface application "WasNetActivator.exe".</span></span> <span data-ttu-id="57b52-160">Dinleyici bağdaştırıcısını başlatmak için **Başlat** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="57b52-160">Click the **Start** button to start the listener adapter.</span></span> <span data-ttu-id="57b52-161">Şimdi programı çalıştırmaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="57b52-161">Now you are ready to run the program.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="57b52-162">Bu örnekle işiniz bittiğinde, "Default Web site" kaynağından net. UDP bağlamasını kaldırmak için Cleanup. bat dosyasını çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="57b52-162">When you are finished with this sample, you must run Cleanup.bat to remove the net.udp binding from the "Default Web Site".</span></span>  
  
## <a name="sample-usage"></a><span data-ttu-id="57b52-163">Örnek kullanım</span><span class="sxs-lookup"><span data-stu-id="57b52-163">Sample Usage</span></span>  
 <span data-ttu-id="57b52-164">Derlemeden sonra oluşturulan dört farklı ikili dosya vardır:</span><span class="sxs-lookup"><span data-stu-id="57b52-164">After compilation, there are four different binaries generated:</span></span>  
  
- <span data-ttu-id="57b52-165">Client. exe: istemci kodu.</span><span class="sxs-lookup"><span data-stu-id="57b52-165">Client.exe: The client code.</span></span> <span data-ttu-id="57b52-166">App. config Client. exe. config istemci yapılandırma dosyasına derlenir.</span><span class="sxs-lookup"><span data-stu-id="57b52-166">The App.config is compiled into the client configuration file Client.exe.config.</span></span>  
  
- <span data-ttu-id="57b52-167">UDPActivation. dll: tüm ana UDP uygulamalarını içeren kitaplık.</span><span class="sxs-lookup"><span data-stu-id="57b52-167">UDPActivation.dll: the library that contains all of the major UDP implementations.</span></span>  
  
- <span data-ttu-id="57b52-168">Service. dll: hizmet kodu.</span><span class="sxs-lookup"><span data-stu-id="57b52-168">Service.dll: The service code.</span></span> <span data-ttu-id="57b52-169">Bu, ServiceModelSamples sanal uygulamasının \bin dizinine kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="57b52-169">This is copied to the \bin directory of the virtual application ServiceModelSamples.</span></span> <span data-ttu-id="57b52-170">Hizmet dosyası, Service. svc ve yapılandırma dosyası Web. config ' dir. Derlemeden sonra, bunlar şu konuma kopyalanır:%SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="57b52-170">The service file is Service.svc and the configuration file is Web.config. After compilation, they are copied to the following location: %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.</span></span>  
  
- <span data-ttu-id="57b52-171">Lınetactivator: UDP Etkinleştirici programı.</span><span class="sxs-lookup"><span data-stu-id="57b52-171">WasNetActivator: The UDP activator program.</span></span>  
  
- <span data-ttu-id="57b52-172">Tüm gerekli parçaların düzgün yüklendiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="57b52-172">Ensure that all of the required pieces are installed correctly.</span></span> <span data-ttu-id="57b52-173">Aşağıdaki adımlar, örneğin nasıl çalıştırılacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="57b52-173">The following steps show how to run the sample:</span></span>  
  
1. <span data-ttu-id="57b52-174">Aşağıdaki Windows hizmetlerinin başlatıldığından emin olun:</span><span class="sxs-lookup"><span data-stu-id="57b52-174">Ensure that the following Windows services have been started:</span></span>  
  
    - <span data-ttu-id="57b52-175">Windows Işlem etkinleştirme hizmeti (WAS).</span><span class="sxs-lookup"><span data-stu-id="57b52-175">Windows Process Activation Service (WAS).</span></span>  
  
    - <span data-ttu-id="57b52-176">Internet Information Services (IIS): W3SVC.</span><span class="sxs-lookup"><span data-stu-id="57b52-176">Internet Information Services (IIS): W3SVC.</span></span>  
  
2. <span data-ttu-id="57b52-177">Ardından, etkinleştirentactivator. exe ' yi başlatın.</span><span class="sxs-lookup"><span data-stu-id="57b52-177">Then start the activator, WasNetActivator.exe.</span></span> <span data-ttu-id="57b52-178">**Etkinleştirme** sekmesi altında, iletişim kutusunda yalnızca **UDP**olan protokol seçilidir.</span><span class="sxs-lookup"><span data-stu-id="57b52-178">Under the **Activation** tab, the only protocol, **UDP**, is selected in the drop down list.</span></span> <span data-ttu-id="57b52-179">Etkinleştirici 'yi başlatmak için **Başlat** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="57b52-179">Click the **Start** button to start the activator.</span></span>  
  
3. <span data-ttu-id="57b52-180">Etkinleştirici başlatıldıktan sonra, bir komut penceresinden Client. exe ' yi çalıştırarak istemci kodunu çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="57b52-180">Once the activator is started, you can run the client code by running Client.exe from a command window.</span></span> <span data-ttu-id="57b52-181">Örnek çıktı aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="57b52-181">The following is the sample output:</span></span>  
  
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
> <span data-ttu-id="57b52-182">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="57b52-182">The samples may already be installed on your machine.</span></span> <span data-ttu-id="57b52-183">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="57b52-183">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="57b52-184">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://go.microsoft.com/fwlink/?LinkId=150780) gidin.</span><span class="sxs-lookup"><span data-stu-id="57b52-184">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="57b52-185">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="57b52-185">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\UdpActivation`  
