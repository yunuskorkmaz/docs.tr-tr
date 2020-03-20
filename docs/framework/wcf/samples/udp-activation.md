---
title: UDP Etkinleştirme
ms.date: 03/30/2017
ms.assetid: 4b0ccd10-0dfb-4603-93f9-f0857c581cb7
ms.openlocfilehash: c0b351adb0b45f42404e94c74bdcff7785c2d0ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143726"
---
# <a name="udp-activation"></a><span data-ttu-id="87846-102">UDP Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="87846-102">UDP Activation</span></span>
<span data-ttu-id="87846-103">Bu örnek [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örneğine dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="87846-103">This sample is based on the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span> <span data-ttu-id="87846-104">Windows Process Etkinleştirme Hizmeti (WAS) kullanarak işlem etkinleştirme desteklemek için [Aktarım: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örnek genişletir.</span><span class="sxs-lookup"><span data-stu-id="87846-104">It extends the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample to support process activation using the Windows Process Activation Service (WAS).</span></span>  
  
 <span data-ttu-id="87846-105">Örnek üç ana parçadan oluşur:</span><span class="sxs-lookup"><span data-stu-id="87846-105">The sample consists of three major pieces:</span></span>  
  
- <span data-ttu-id="87846-106">Bir UDP Protokol Aktivatör, aktive edilecek uygulamalar adına UDP iletileri alan bağımsız bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="87846-106">A UDP Protocol Activator, a standalone process that receives UDP messages on behalf of applications that are to be activated.</span></span>  
  
- <span data-ttu-id="87846-107">İleti göndermek için UDP özel aktarımını kullanan bir istemci.</span><span class="sxs-lookup"><span data-stu-id="87846-107">A client that uses the UDP custom transport to send messages.</span></span>  
  
- <span data-ttu-id="87846-108">UDP özel aktarım üzerinden ileti alan bir hizmet (WAS tarafından etkinleştirilen bir alt işlemde barındırılan).</span><span class="sxs-lookup"><span data-stu-id="87846-108">A service (hosted in a worker process activated by WAS) that receives messages over the UDP custom transport.</span></span>  
  
## <a name="udp-protocol-activator"></a><span data-ttu-id="87846-109">UDP Protokol Aktivatör</span><span class="sxs-lookup"><span data-stu-id="87846-109">UDP Protocol Activator</span></span>  
 <span data-ttu-id="87846-110">UDP Protokol Aktivatör WCF istemcisi ve WCF hizmeti arasında bir köprüdür.</span><span class="sxs-lookup"><span data-stu-id="87846-110">The UDP Protocol Activator is a bridge between the WCF client and the WCF service.</span></span> <span data-ttu-id="87846-111">Aktarım katmanındaki UDP protokolü aracılığıyla veri iletişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="87846-111">It provides data communication through the UDP protocol at the transport layer.</span></span> <span data-ttu-id="87846-112">İki ana işlevi vardır:</span><span class="sxs-lookup"><span data-stu-id="87846-112">It has two major functions:</span></span>  
  
- <span data-ttu-id="87846-113">Gelen iletilere yanıt olarak süreçleri etkinleştirmek için WAS ile işbirliği yapan WAS Dinleyici Adaptörü (LA).</span><span class="sxs-lookup"><span data-stu-id="87846-113">WAS Listener Adapter (LA), which collaborates with WAS to activate processes in response to incoming messages.</span></span>  
  
- <span data-ttu-id="87846-114">UdP Protokol Dinleyicisi, aktive edilecek uygulamalar adına UDP iletilerini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="87846-114">UDP Protocol Listener, which accepts UDP messages on behalf of applications that are to be activated.</span></span>  
  
 <span data-ttu-id="87846-115">Etkinleştirme, sunucu makinesinde bağımsız bir program olarak çalışıyor olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="87846-115">The activator must be running as a standalone program on the server machine.</span></span> <span data-ttu-id="87846-116">Normalde, WAS dinleyici adaptörleri (NetTcpActivator ve NetPipeActivator gibi) uzun süredir çalışan Windows hizmetlerinde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="87846-116">Normally, WAS listener adapters (such as the NetTcpActivator and the NetPipeActivator) are implemented in long-running Windows services.</span></span> <span data-ttu-id="87846-117">Ancak, basitlik ve netlik için, bu örnek tek başına bir uygulama olarak protokol aktivatör uygular.</span><span class="sxs-lookup"><span data-stu-id="87846-117">However, for simplicity and clarity, this sample implements the protocol activator as a standalone application.</span></span>  
  
### <a name="was-listener-adapter"></a><span data-ttu-id="87846-118">WAS Dinleyici Adaptörü</span><span class="sxs-lookup"><span data-stu-id="87846-118">WAS Listener Adapter</span></span>  
 <span data-ttu-id="87846-119">UDP için WAS Dinleyici Adaptörü `UdpListenerAdapter` sınıfta uygulanır.</span><span class="sxs-lookup"><span data-stu-id="87846-119">The WAS Listener Adapter for UDP is implemented in the `UdpListenerAdapter` class.</span></span> <span data-ttu-id="87846-120">UDP protokolü için uygulama aktivasyonu gerçekleştirmek için WAS ile etkileşim modüldür.</span><span class="sxs-lookup"><span data-stu-id="87846-120">It is the module that interacts with WAS to perform application activation for the UDP protocol.</span></span> <span data-ttu-id="87846-121">Bu, aşağıdaki Web host API'lerini arayarak elde edilir:</span><span class="sxs-lookup"><span data-stu-id="87846-121">This is achieved by calling the following Webhost APIs:</span></span>  
  
- `WebhostRegisterProtocol`  
  
- `WebhostUnregisterProtocol`  
  
- `WebhostOpenListenerChannelInstance`  
  
- `WebhostCloseAllListenerChannelInstances`  
  
 <span data-ttu-id="87846-122">Başlangıçta aradıktan `WebhostRegisterProtocol`sonra, dinleyici adaptörü `ApplicationCreated` applicationHost.config kayıtlı tüm uygulamalar için WAS geri çağrı alır (% windir%\system32\inetsrv bulunur).</span><span class="sxs-lookup"><span data-stu-id="87846-122">After initially calling `WebhostRegisterProtocol`, the listener adapter receives the callback `ApplicationCreated` from WAS for all of the applications registered in applicationHost.config (located in %windir%\system32\inetsrv).</span></span> <span data-ttu-id="87846-123">Bu örnekte, uygulamaları yalnızca UDP protokolü (protokol kimliği "net.udp" olarak) etkinleştirilmiş olarak ele alıyoruz.</span><span class="sxs-lookup"><span data-stu-id="87846-123">In this sample, we only handle the applications with the UDP protocol (with the protocol id as "net.udp") enabled.</span></span> <span data-ttu-id="87846-124">Bu tür uygulamalar uygulamada dinamik yapılandırma değişikliklerine yanıt veriyorsa (örneğin, devre dışı bırakılan uygulamadan etkine bir uygulama geçişi) diğer uygulamalar bunu farklı şekilde işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="87846-124">Other implementations may handle this differently if such implementations respond to dynamic configuration changes to the application (for example, an application transition from disabled to enabled).</span></span>  
  
 <span data-ttu-id="87846-125">Geri arama `ConfigManagerInitializationCompleted` yapıldığında, bt protokolün başlatılması için tüm bildirimleri tamamladığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="87846-125">When the callback `ConfigManagerInitializationCompleted` is received, it indicates that WAS has finished all of the notifications for the initialization of the protocol.</span></span> <span data-ttu-id="87846-126">Şu anda, dinleyici bağdaştırıcı etkinleştirme isteklerini işlemeye hazırdır.</span><span class="sxs-lookup"><span data-stu-id="87846-126">At this time, the listener adapter is ready to process activation requests.</span></span>  
  
 <span data-ttu-id="87846-127">Bir uygulama için ilk kez yeni bir istek geldiğinde, `WebhostOpenListenerChannelInstance` dinleyici bağdaştırıcısı WAS'ı çağırır ve bu da henüz başlatılmazsa alt işlemi başlatır.</span><span class="sxs-lookup"><span data-stu-id="87846-127">When a new request comes in the first time for an application, the listener adapter calls `WebhostOpenListenerChannelInstance` into WAS, which starts the worker process if it is not started yet.</span></span> <span data-ttu-id="87846-128">Daha sonra protokol işleyicileri yüklenir ve dinleyici bağdaştırıcısı ile sanal uygulama arasındaki iletişim başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="87846-128">Then the protocol handlers are loaded and the communication between the listener adapter and the virtual application can start.</span></span>  
  
 <span data-ttu-id="87846-129">Dinleyici bağdaştırıcısı <`listenerAdapters`> bölümünde %SystemRoot%\System32\Inetsrv\ApplicationHost.config'de aşağıdaki gibi kaydedilir:</span><span class="sxs-lookup"><span data-stu-id="87846-129">The listener adapter is registered in the %SystemRoot%\System32\inetsrv\ApplicationHost.config in the <`listenerAdapters`> section as following:</span></span>  
  
```xml  
<add name="net.udp" identity="S-1-5-21-2127521184-1604012920-1887927527-387045" />  
```  
  
### <a name="protocol-listener"></a><span data-ttu-id="87846-130">Protokol Dinleyicisi</span><span class="sxs-lookup"><span data-stu-id="87846-130">Protocol Listener</span></span>  
 <span data-ttu-id="87846-131">UDP protokol dinleyicisi, sanal uygulama adına UDP bitiş noktasında dinleyen protokol aktivatörünün içindeki bir modüldür.</span><span class="sxs-lookup"><span data-stu-id="87846-131">The UDP protocol listener is a module inside the protocol activator that listens at a UDP endpoint on behalf of the virtual application.</span></span> <span data-ttu-id="87846-132">Bu sınıfta `UdpSocketListener`uygulanır.</span><span class="sxs-lookup"><span data-stu-id="87846-132">It is implemented in the class `UdpSocketListener`.</span></span> <span data-ttu-id="87846-133">Bitiş noktası, bağlantı `IPEndpoint` noktası numarasının site için protokol ün bağlayıcılığından ayıklandığı şekilde temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="87846-133">The endpoint is represented as `IPEndpoint` for which the port number is extracted from the binding of the protocol for the site.</span></span>  
  
### <a name="control-service"></a><span data-ttu-id="87846-134">Kontrol Hizmeti</span><span class="sxs-lookup"><span data-stu-id="87846-134">Control Service</span></span>  
 <span data-ttu-id="87846-135">Bu örnekte, aktivatör ve WAS alt süreci arasında iletişim kurmak için WCF'yi kullanırız.</span><span class="sxs-lookup"><span data-stu-id="87846-135">In this sample, we use WCF to communicate between the activator and the WAS worker process.</span></span> <span data-ttu-id="87846-136">Etkinleştirmede bulunan hizmete Denetim Hizmeti denir.</span><span class="sxs-lookup"><span data-stu-id="87846-136">The service that resides in the activator is called the Control Service.</span></span>  
  
## <a name="protocol-handlers"></a><span data-ttu-id="87846-137">Protokol Handleyicileri</span><span class="sxs-lookup"><span data-stu-id="87846-137">Protocol Handlers</span></span>  
 <span data-ttu-id="87846-138">Dinleyici bağdaştırıcısı çağrılarını `WebhostOpenListenerChannelInstance`yaptıktan sonra, başlatılmazsa WAS işlem yöneticisi alt işlemi başlatır.</span><span class="sxs-lookup"><span data-stu-id="87846-138">After the listener adapter calls `WebhostOpenListenerChannelInstance`, the WAS process manager starts the worker process if it is not started.</span></span> <span data-ttu-id="87846-139">Alt işlem içindeki uygulama yöneticisi daha sonra udp işlem protokolü işleyicisi `ListenerChannelId`(PPH) için istek yükler.</span><span class="sxs-lookup"><span data-stu-id="87846-139">The application manager inside the worker process then loads the UDP Process Protocol Handler (PPH) with the request for that `ListenerChannelId`.</span></span> <span data-ttu-id="87846-140">Sırayla PPH `IAdphManager`çağırır .`StartAppDomainProtocolListenerChannel`</span><span class="sxs-lookup"><span data-stu-id="87846-140">The PPH in turns calls `IAdphManager`.`StartAppDomainProtocolListenerChannel`</span></span> <span data-ttu-id="87846-141">UDP AppDomain Protokol Handizor'yu (ADPH) başlatmak için.</span><span class="sxs-lookup"><span data-stu-id="87846-141">to start the UDP AppDomain Protocol Handler (ADPH).</span></span>  
  
## <a name="hostedudptransportconfiguration"></a><span data-ttu-id="87846-142">HostedUDPTransportConfiguration</span><span class="sxs-lookup"><span data-stu-id="87846-142">HostedUDPTransportConfiguration</span></span>  
 <span data-ttu-id="87846-143">Bilgiler Web.config'de aşağıdaki gibi kaydedilir:</span><span class="sxs-lookup"><span data-stu-id="87846-143">The information is registered in the Web.config as follows:</span></span>  
  
```xml  
<serviceHostingEnvironment>  
<add name="net.udp" transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />  
</serviceHostingEnvironment>  
```  
  
## <a name="special-setup-for-this-sample"></a><span data-ttu-id="87846-144">Bu Örnek için Özel Kurulum</span><span class="sxs-lookup"><span data-stu-id="87846-144">Special Setup for This Sample</span></span>  
 <span data-ttu-id="87846-145">Bu örnek yalnızca Windows Vista, Windows Server 2008 veya Windows 7'de oluşturulabilir ve çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="87846-145">This sample can be only built and run on Windows Vista, Windows Server 2008, or Windows 7.</span></span> <span data-ttu-id="87846-146">Örneği çalıştırmak için öncelikle tüm bileşenleri doğru şekilde ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="87846-146">To run the sample, you must first get all of the components set up correctly.</span></span> <span data-ttu-id="87846-147">Örneği yüklemek için aşağıdaki adımları kullanın.</span><span class="sxs-lookup"><span data-stu-id="87846-147">Use the following steps to install the sample.</span></span>  
  
#### <a name="to-set-up-this-sample"></a><span data-ttu-id="87846-148">Bu örneği ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="87846-148">To set up this sample</span></span>  
  
1. <span data-ttu-id="87846-149">Aşağıdaki komutu kullanarak 4.0 ASP.NET yükleyin.</span><span class="sxs-lookup"><span data-stu-id="87846-149">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="87846-150">Projeyi Windows Vista'da oluşturun.</span><span class="sxs-lookup"><span data-stu-id="87846-150">Build the project on Windows Vista.</span></span> <span data-ttu-id="87846-151">Derlemeden sonra, yapı sonrası aşamada da aşağıdaki işlemleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="87846-151">After compilation, it also performs the following operations in the post-build phase:</span></span>  
  
    - <span data-ttu-id="87846-152">"Varsayılan Web Sitesi" sitesine bağlanan UDP'yi yükler.</span><span class="sxs-lookup"><span data-stu-id="87846-152">Installs the UDP binding to the site "Default Web Site".</span></span>  
  
    - <span data-ttu-id="87846-153">Fiziksel yolu işaret etmek için sanal uygulama "ServiceModelSamples" oluşturur: "%SystemDrive%\inetpub\wwwroot\servicemodelsamples".</span><span class="sxs-lookup"><span data-stu-id="87846-153">Creates the virtual application "ServiceModelSamples" to point to the physical path: "%SystemDrive%\inetpub\wwwroot\servicemodelsamples".</span></span>  
  
    - <span data-ttu-id="87846-154">Ayrıca bu sanal uygulama için "net.udp" protokolü sağlar.</span><span class="sxs-lookup"><span data-stu-id="87846-154">It also enables "net.udp" protocol for this virtual application.</span></span>  
  
3. <span data-ttu-id="87846-155">Kullanıcı arabirimi uygulamasını "WasNetActivator.exe" başlatın.</span><span class="sxs-lookup"><span data-stu-id="87846-155">Start the user interface application "WasNetActivator.exe".</span></span> <span data-ttu-id="87846-156">**Kurulum** sekmesini tıklatın, aşağıdaki onay kutularını işaretleyin ve sonra yüklemek için **Yükle'yi** tıklatın:</span><span class="sxs-lookup"><span data-stu-id="87846-156">Click the **Setup** tab, check the following check boxes and then click **Install** to install them:</span></span>  
  
    - <span data-ttu-id="87846-157">UDP Dinleyici Adaptörü</span><span class="sxs-lookup"><span data-stu-id="87846-157">UDP Listener Adapter</span></span>  
  
    - <span data-ttu-id="87846-158">UDP Protokol Handleyicileri</span><span class="sxs-lookup"><span data-stu-id="87846-158">UDP Protocol Handlers</span></span>  
  
4. <span data-ttu-id="87846-159">Kullanıcı arabirimi uygulaması "WasNetActivator.exe" **etkinleştirme** sekmesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="87846-159">Click the **Activation** tab of the user interface application "WasNetActivator.exe".</span></span> <span data-ttu-id="87846-160">Dinleyici bağdaştırıcısını başlatmak için **Başlat** düğmesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="87846-160">Click the **Start** button to start the listener adapter.</span></span> <span data-ttu-id="87846-161">Şimdi programı çalıştırmak için hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="87846-161">Now you are ready to run the program.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="87846-162">Bu örnekle bitirdiğinizde, "Varsayılan Web Sitesi"nden net.udp bağlamayı kaldırmak için Cleanup.bat'ı çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="87846-162">When you are finished with this sample, you must run Cleanup.bat to remove the net.udp binding from the "Default Web Site".</span></span>  
  
## <a name="sample-usage"></a><span data-ttu-id="87846-163">Örnek Kullanım</span><span class="sxs-lookup"><span data-stu-id="87846-163">Sample Usage</span></span>  
 <span data-ttu-id="87846-164">Derlemeden sonra oluşturulan dört farklı ikili vardır:</span><span class="sxs-lookup"><span data-stu-id="87846-164">After compilation, there are four different binaries generated:</span></span>  
  
- <span data-ttu-id="87846-165">Client.exe: İstemci kodu.</span><span class="sxs-lookup"><span data-stu-id="87846-165">Client.exe: The client code.</span></span> <span data-ttu-id="87846-166">App.config istemci yapılandırma dosyasıclient.exe.config derlenir.</span><span class="sxs-lookup"><span data-stu-id="87846-166">The App.config is compiled into the client configuration file Client.exe.config.</span></span>  
  
- <span data-ttu-id="87846-167">UDPActivation.dll: tüm önemli UDP uygulamalarını içeren kitaplık.</span><span class="sxs-lookup"><span data-stu-id="87846-167">UDPActivation.dll: the library that contains all of the major UDP implementations.</span></span>  
  
- <span data-ttu-id="87846-168">Service.dll: Servis kodu.</span><span class="sxs-lookup"><span data-stu-id="87846-168">Service.dll: The service code.</span></span> <span data-ttu-id="87846-169">Bu sanal uygulama ServiceModelSamples \bin dizinine kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="87846-169">This is copied to the \bin directory of the virtual application ServiceModelSamples.</span></span> <span data-ttu-id="87846-170">Hizmet dosyası Service.svc ve yapılandırma dosyası Web.config olduğunu. Derlemeden sonra aşağıdaki konuma kopyalanırlar: %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="87846-170">The service file is Service.svc and the configuration file is Web.config. After compilation, they are copied to the following location: %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.</span></span>  
  
- <span data-ttu-id="87846-171">WasNetActivator: UDP aktivatör programı.</span><span class="sxs-lookup"><span data-stu-id="87846-171">WasNetActivator: The UDP activator program.</span></span>  
  
- <span data-ttu-id="87846-172">Gerekli tüm parçaların doğru şekilde takıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="87846-172">Ensure that all of the required pieces are installed correctly.</span></span> <span data-ttu-id="87846-173">Aşağıdaki adımlar, örneğin nasıl çalıştırılsüreceğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="87846-173">The following steps show how to run the sample:</span></span>  
  
1. <span data-ttu-id="87846-174">Aşağıdaki Windows hizmetlerinin başlatıldığından emin olun:</span><span class="sxs-lookup"><span data-stu-id="87846-174">Ensure that the following Windows services have been started:</span></span>  
  
    - <span data-ttu-id="87846-175">Windows İşlem etkinleştirme Hizmeti (WAS).</span><span class="sxs-lookup"><span data-stu-id="87846-175">Windows Process Activation Service (WAS).</span></span>  
  
    - <span data-ttu-id="87846-176">İnternet Bilgi Hizmetleri (IIS): W3SVC.</span><span class="sxs-lookup"><span data-stu-id="87846-176">Internet Information Services (IIS): W3SVC.</span></span>  
  
2. <span data-ttu-id="87846-177">Sonra aktivatör, WasNetActivator.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="87846-177">Then start the activator, WasNetActivator.exe.</span></span> <span data-ttu-id="87846-178">**Etkinleştirme** sekmesialtında, tek protokol, **UDP**, açılır listede seçilir.</span><span class="sxs-lookup"><span data-stu-id="87846-178">Under the **Activation** tab, the only protocol, **UDP**, is selected in the drop down list.</span></span> <span data-ttu-id="87846-179">Etkinleştirme başlatmak için **Başlat** düğmesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="87846-179">Click the **Start** button to start the activator.</span></span>  
  
3. <span data-ttu-id="87846-180">Etkinleştirme başlatıldıktan sonra, istemci kodunu bir komut penceresinden Client.exe çalıştırarak çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87846-180">Once the activator is started, you can run the client code by running Client.exe from a command window.</span></span> <span data-ttu-id="87846-181">Örnek çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="87846-181">The following is the sample output:</span></span>  
  
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
> <span data-ttu-id="87846-182">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="87846-182">The samples may already be installed on your machine.</span></span> <span data-ttu-id="87846-183">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="87846-183">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="87846-184">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="87846-184">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="87846-185">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="87846-185">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\UdpActivation`  
