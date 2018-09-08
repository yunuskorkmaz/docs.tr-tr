---
title: UDP Etkinleştirme
ms.date: 03/30/2017
ms.assetid: 4b0ccd10-0dfb-4603-93f9-f0857c581cb7
ms.openlocfilehash: c64540db555d7cac56dd46c6ffb63ec95ca81f91
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44138363"
---
# <a name="udp-activation"></a><span data-ttu-id="ebcf3-102">UDP Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="ebcf3-102">UDP Activation</span></span>
<span data-ttu-id="ebcf3-103">Bu örnek dayanır [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-103">This sample is based on the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span> <span data-ttu-id="ebcf3-104">Bunu genişleten [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) Windows İşlem Etkinleştirme Hizmeti (WAS) kullanarak işlem etkinleştirmeyi desteklemek için örnek.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-104">It extends the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample to support process activation using the Windows Process Activation Service (WAS).</span></span>  
  
 <span data-ttu-id="ebcf3-105">Örnek üç ana parçalarını oluşur:</span><span class="sxs-lookup"><span data-stu-id="ebcf3-105">The sample consists of three major pieces:</span></span>  
  
-   <span data-ttu-id="ebcf3-106">Bir UDP protokolünü Etkinleştirici, etkinleştirilecek olan uygulamaları adına UDP iletiler alan bir tek başına işlemi.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-106">A UDP Protocol Activator, a standalone process that receives UDP messages on behalf of applications that are to be activated.</span></span>  
  
-   <span data-ttu-id="ebcf3-107">İleti göndermek için özel UDP taşıma kullanan bir istemci.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-107">A client that uses the UDP custom transport to send messages.</span></span>  
  
-   <span data-ttu-id="ebcf3-108">UDP özel taşıma iletileri alır (WAS tarafından etkinleştirilen bir çalışan işleminin içinde barındırılan) bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-108">A service (hosted in a worker process activated by WAS) that receives messages over the UDP custom transport.</span></span>  
  
## <a name="udp-protocol-activator"></a><span data-ttu-id="ebcf3-109">UDP protokolünü etkinleştiricisi</span><span class="sxs-lookup"><span data-stu-id="ebcf3-109">UDP Protocol Activator</span></span>  
 <span data-ttu-id="ebcf3-110">UDP protokolünü Etkinleştirici WCF istemcisini ve WCF hizmeti arasında bir köprü ' dir.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-110">The UDP Protocol Activator is a bridge between the WCF client and the WCF service.</span></span> <span data-ttu-id="ebcf3-111">Bu aktarım katmanında UDP protokolünü aracılığıyla veri iletişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-111">It provides data communication through the UDP protocol at the transport layer.</span></span> <span data-ttu-id="ebcf3-112">İki ana işlev içerir:</span><span class="sxs-lookup"><span data-stu-id="ebcf3-112">It has two major functions:</span></span>  
  
-   <span data-ttu-id="ebcf3-113">Dinleyici Bağdaştırıcısı (gelen iletilere yanıt olarak işlemleri etkinleştirmeyi WAS ile iş Birliği yapar, LA), oldu.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-113">WAS Listener Adapter (LA), which collaborates with WAS to activate processes in response to incoming messages.</span></span>  
  
-   <span data-ttu-id="ebcf3-114">UDP protokolünü UDP iletileri etkinleştirilecek olan uygulamaları adına kabul eden dinleyici.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-114">UDP Protocol Listener, which accepts UDP messages on behalf of applications that are to be activated.</span></span>  
  
 <span data-ttu-id="ebcf3-115">Etkinleştirici sunucunuz üzerinde bağımsız bir program olarak çalıştırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-115">The activator must be running as a standalone program on the server machine.</span></span> <span data-ttu-id="ebcf3-116">Normalde, WAS dinleyici bağdaştırıcıları (örneğin, NetTcpActivator ve NetPipeActivator) uzun süre çalışan Windows Hizmetleri uygulanır.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-116">Normally, WAS listener adapters (such as the NetTcpActivator and the NetPipeActivator) are implemented in long-running Windows services.</span></span> <span data-ttu-id="ebcf3-117">Ancak, Basitlik ve Anlaşılırlık için bu örnek, Protokolü Etkinleştirici tek başına uygulama'e uygular.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-117">However, for simplicity and clarity, this sample implements the protocol activator as a standalone application.</span></span>  
  
### <a name="was-listener-adapter"></a><span data-ttu-id="ebcf3-118">Dinleyici Bağdaştırıcısı OLUŞTU</span><span class="sxs-lookup"><span data-stu-id="ebcf3-118">WAS Listener Adapter</span></span>  
 <span data-ttu-id="ebcf3-119">UDP için olan dinleyici bağdaştırıcısı uygulanan `UdpListenerAdapter` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-119">The WAS Listener Adapter for UDP is implemented in the `UdpListenerAdapter` class.</span></span> <span data-ttu-id="ebcf3-120">WAS uygulama etkinleştirme için UDP protokolünü gerçekleştirmek için etkileşimde modüldür.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-120">It is the module that interacts with WAS to perform application activation for the UDP protocol.</span></span> <span data-ttu-id="ebcf3-121">Bu, aşağıdaki Web barındırma API'ları çağırarak sağlanır:</span><span class="sxs-lookup"><span data-stu-id="ebcf3-121">This is achieved by calling the following Webhost APIs:</span></span>  
  
-   `WebhostRegisterProtocol`  
  
-   `WebhostUnregisterProtocol`  
  
-   `WebhostOpenListenerChannelInstance`  
  
-   `WebhostCloseAllListenerChannelInstances`  
  
 <span data-ttu-id="ebcf3-122">Başlangıçta çağrıldıktan sonra `WebhostRegisterProtocol`, dinleyici bağdaştırıcısı geri çağırma alır `ApplicationCreated` WAS tüm uygulamalar için gelen applicationHost.config (windir%\system32\inetsrv içinde bulunur) kaydedildi.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-122">After initially calling `WebhostRegisterProtocol`, the listener adapter receives the callback `ApplicationCreated` from WAS for all of the applications registered in applicationHost.config (located in %windir%\system32\inetsrv).</span></span> <span data-ttu-id="ebcf3-123">Bu örnekte biz yalnızca etkin uygulamalarla UDP protokolünü ("net.udp" olarak Protokolü kimliği ile) işleyin.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-123">In this sample, we only handle the applications with the UDP protocol (with the protocol id as "net.udp") enabled.</span></span> <span data-ttu-id="ebcf3-124">Diğer uygulamalar gibi uygulamaları (örneğin, bir uygulamanın durumundan etkin, devre dışı) uygulamaya dinamik yapılandırma değişikliklerine yanıt verme durumunda bu farklı şekilde işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-124">Other implementations may handle this differently if such implementations respond to dynamic configuration changes to the application (for example, an application transition from disabled to enabled).</span></span>  
  
 <span data-ttu-id="ebcf3-125">Zaman geri çağırma `ConfigManagerInitializationCompleted` alınan, gösterir, WAS tüm başlatma protokolü için bildirim bitirdi.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-125">When the callback `ConfigManagerInitializationCompleted` is received, it indicates that WAS has finished all of the notifications for the initialization of the protocol.</span></span> <span data-ttu-id="ebcf3-126">Şu anda Dinleyici Bağdaştırıcısı etkinleştirme isteklerini işlemek hazırdır.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-126">At this time, the listener adapter is ready to process activation requests.</span></span>  
  
 <span data-ttu-id="ebcf3-127">Bir uygulama için ilk saatteki yeni bir istek geldiğinde, dinleyici bağdaştırıcısı çağırır `WebhostOpenListenerChannelInstance` WAS içinde çalışan işlemi henüz başlatılmamışsa başlatan.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-127">When a new request comes in the first time for an application, the listener adapter calls `WebhostOpenListenerChannelInstance` into WAS, which starts the worker process if it is not started yet.</span></span> <span data-ttu-id="ebcf3-128">Ardından protokol işleyiciler yüklenir ve Dinleyici Bağdaştırıcısı ile sanal uygulama arasındaki iletişimi başlayabilir.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-128">Then the protocol handlers are loaded and the communication between the listener adapter and the virtual application can start.</span></span>  
  
 <span data-ttu-id="ebcf3-129">Dinleyici Bağdaştırıcısı içinde %SystemRoot%\System32\inetsrv\ApplicationHost.config kaydedilmiştir <`listenerAdapters`> bölümünde aşağıdaki gibi:</span><span class="sxs-lookup"><span data-stu-id="ebcf3-129">The listener adapter is registered in the %SystemRoot%\System32\inetsrv\ApplicationHost.config in the <`listenerAdapters`> section as following:</span></span>  
  
```xml  
<add name="net.udp" identity="S-1-5-21-2127521184-1604012920-1887927527-387045" />  
```  
  
### <a name="protocol-listener"></a><span data-ttu-id="ebcf3-130">Dinleyici Protokolü</span><span class="sxs-lookup"><span data-stu-id="ebcf3-130">Protocol Listener</span></span>  
 <span data-ttu-id="ebcf3-131">UDP protokolünü dinleyicisi UDP uç noktada dinleyen adına sanal uygulama protokolü Etkinleştirici içinde bir modüldür.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-131">The UDP protocol listener is a module inside the protocol activator that listens at a UDP endpoint on behalf of the virtual application.</span></span> <span data-ttu-id="ebcf3-132">Bu sınıfta uygulandığını `UdpSocketListener`.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-132">It is implemented in the class `UdpSocketListener`.</span></span> <span data-ttu-id="ebcf3-133">Uç nokta olarak temsil edilen `IPEndpoint` Protokolü site için bağlamayı, bağlantı noktası numarasını ayıklanan için.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-133">The endpoint is represented as `IPEndpoint` for which the port number is extracted from the binding of the protocol for the site.</span></span>  
  
### <a name="control-service"></a><span data-ttu-id="ebcf3-134">Hizmet denetimi</span><span class="sxs-lookup"><span data-stu-id="ebcf3-134">Control Service</span></span>  
 <span data-ttu-id="ebcf3-135">Bu örnekte, WCF Etkinleştirici ve WAS alt işlem arasında iletişim kurmak için kullanırız.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-135">In this sample, we use WCF to communicate between the activator and the WAS worker process.</span></span> <span data-ttu-id="ebcf3-136">Etkinleştirici içinde bulunan hizmet denetim hizmeti olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-136">The service that resides in the activator is called the Control Service.</span></span>  
  
## <a name="protocol-handlers"></a><span data-ttu-id="ebcf3-137">Protokol işleyiciler</span><span class="sxs-lookup"><span data-stu-id="ebcf3-137">Protocol Handlers</span></span>  
 <span data-ttu-id="ebcf3-138">Dinleyici Bağdaştırıcısı çağırdıktan sonra `WebhostOpenListenerChannelInstance`, onu başlatılmadığında WAS İşlem Yöneticisi'ni çalışan işlemi başlatır.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-138">After the listener adapter calls `WebhostOpenListenerChannelInstance`, the WAS process manager starts the worker process if it is not started.</span></span> <span data-ttu-id="ebcf3-139">Çalışan işlemi içinde uygulama Yöneticisi daha sonra UDP işlem protokol işleyicisi (PPH) söz konusu istekle yükler `ListenerChannelId`.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-139">The application manager inside the worker process then loads the UDP Process Protocol Handler (PPH) with the request for that `ListenerChannelId`.</span></span> <span data-ttu-id="ebcf3-140">Sırayla çağrılarındaki PPH `IAdphManager`.`StartAppDomainProtocolListenerChannel`</span><span class="sxs-lookup"><span data-stu-id="ebcf3-140">The PPH in turns calls `IAdphManager`.`StartAppDomainProtocolListenerChannel`</span></span> <span data-ttu-id="ebcf3-141">UDP AppDomain protokol işleyicisi (ADPH) başlatmak için.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-141">to start the UDP AppDomain Protocol Handler (ADPH).</span></span>  
  
## <a name="hostedudptransportconfiguration"></a><span data-ttu-id="ebcf3-142">HostedUDPTransportConfiguration</span><span class="sxs-lookup"><span data-stu-id="ebcf3-142">HostedUDPTransportConfiguration</span></span>  
 <span data-ttu-id="ebcf3-143">Bilgiler, Web.config dosyasında şu şekilde kaydedilir:</span><span class="sxs-lookup"><span data-stu-id="ebcf3-143">The information is registered in the Web.config as follows:</span></span>  
  
```xml  
<serviceHostingEnvironment>  
<add name="net.udp" transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />  
</serviceHostingEnvironment>  
```  
  
## <a name="special-setup-for-this-sample"></a><span data-ttu-id="ebcf3-144">Bu örnek için özel kurulum</span><span class="sxs-lookup"><span data-stu-id="ebcf3-144">Special Setup for This Sample</span></span>  
 <span data-ttu-id="ebcf3-145">Bu örnek yalnızca oluşturulan ve Windows Vista, Windows Server 2008 veya Windows 7 üzerinde çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-145">This sample can be only built and run on Windows Vista, Windows Server 2008, or Windows 7.</span></span> <span data-ttu-id="ebcf3-146">Örneği çalıştırmak için önce tüm bileşenlerin doğru bir şekilde ayarlandığından almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-146">To run the sample, you must first get all of the components set up correctly.</span></span> <span data-ttu-id="ebcf3-147">Örneği yüklemek için aşağıdaki adımları kullanın.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-147">Use the following steps to install the sample.</span></span>  
  
#### <a name="to-set-up-this-sample"></a><span data-ttu-id="ebcf3-148">Bu örneğini kurmak için</span><span class="sxs-lookup"><span data-stu-id="ebcf3-148">To set up this sample</span></span>  
  
1.  <span data-ttu-id="ebcf3-149">Yükleme [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aşağıdaki komutu kullanarak 4.0.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-149">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="ebcf3-150">Windows Vista'da projeyi derleyin.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-150">Build the project on Windows Vista.</span></span> <span data-ttu-id="ebcf3-151">Derlemeden sonra ayrıca derleme sonrası aşamasında aşağıdaki işlemleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="ebcf3-151">After compilation, it also performs the following operations in the post-build phase:</span></span>  
  
    -   <span data-ttu-id="ebcf3-152">UDP bağlama "varsayılan Web sitesi" alanına yükler.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-152">Installs the UDP binding to the site "Default Web Site".</span></span>  
  
    -   <span data-ttu-id="ebcf3-153">Fiziksel yolu işaret edecek şekilde sanal uygulama "ServiceModelSamples" oluşturur: "% SystemDrive%\inetpub\wwwroot\servicemodelsamples".</span><span class="sxs-lookup"><span data-stu-id="ebcf3-153">Creates the virtual application "ServiceModelSamples" to point to the physical path: "%SystemDrive%\inetpub\wwwroot\servicemodelsamples".</span></span>  
  
    -   <span data-ttu-id="ebcf3-154">Ayrıca, bu sanal uygulama için "net.udp" protokol sağlar.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-154">It also enables "net.udp" protocol for this virtual application.</span></span>  
  
3.  <span data-ttu-id="ebcf3-155">"WasNetActivator.exe" kullanıcı arabirimi uygulamasını başlatın.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-155">Start the user interface application "WasNetActivator.exe".</span></span> <span data-ttu-id="ebcf3-156">Tıklayın **Kurulum** sekmesinde, aşağıdaki onay kutularını işaretleyin ve ardından **yükleme** bunları yüklemek için:</span><span class="sxs-lookup"><span data-stu-id="ebcf3-156">Click the **Setup** tab, check the following check boxes and then click **Install** to install them:</span></span>  
  
    -   <span data-ttu-id="ebcf3-157">UDP Dinleyici Bağdaştırıcısı</span><span class="sxs-lookup"><span data-stu-id="ebcf3-157">UDP Listener Adapter</span></span>  
  
    -   <span data-ttu-id="ebcf3-158">UDP protokol işleyiciler</span><span class="sxs-lookup"><span data-stu-id="ebcf3-158">UDP Protocol Handlers</span></span>  
  
4.  <span data-ttu-id="ebcf3-159">Tıklayın **etkinleştirme** sekmesinde kullanıcı arabirimi uygulamasını "WasNetActivator.exe".</span><span class="sxs-lookup"><span data-stu-id="ebcf3-159">Click the **Activation** tab of the user interface application "WasNetActivator.exe".</span></span> <span data-ttu-id="ebcf3-160">Tıklayın **Başlat** dinleyici bağdaştırıcısını başlatma düğmesi.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-160">Click the **Start** button to start the listener adapter.</span></span> <span data-ttu-id="ebcf3-161">Programı çalıştırmak hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-161">Now you are ready to run the program.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ebcf3-162">Bu örnek ile işiniz bittiğinde, "varsayılan Web sitesinden" net.udp bağlamayı kaldırmak Cleanup.bat çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-162">When you are finished with this sample, you must run Cleanup.bat to remove the net.udp binding from the "Default Web Site".</span></span>  
  
## <a name="sample-usage"></a><span data-ttu-id="ebcf3-163">Örnek kullanımı</span><span class="sxs-lookup"><span data-stu-id="ebcf3-163">Sample Usage</span></span>  
 <span data-ttu-id="ebcf3-164">Derleme oluşturulan dört farklı ikili dosyaları vardır:</span><span class="sxs-lookup"><span data-stu-id="ebcf3-164">After compilation, there are four different binaries generated:</span></span>  
  
-   <span data-ttu-id="ebcf3-165">Client.exe: İstemci kodu.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-165">Client.exe: The client code.</span></span> <span data-ttu-id="ebcf3-166">App.config Client.exe.config istemci yapılandırma dosyasına derlenir.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-166">The App.config is compiled into the client configuration file Client.exe.config.</span></span>  
  
-   <span data-ttu-id="ebcf3-167">UDPActivation.dll: tüm önemli UDP uygulamaları içeren kitaplık.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-167">UDPActivation.dll: the library that contains all of the major UDP implementations.</span></span>  
  
-   <span data-ttu-id="ebcf3-168">Service.dll: Hizmet kodu.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-168">Service.dll: The service code.</span></span> <span data-ttu-id="ebcf3-169">Bu sanal uygulama ServiceModelSamples \bin dizinine kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-169">This is copied to the \bin directory of the virtual application ServiceModelSamples.</span></span> <span data-ttu-id="ebcf3-170">Web.config yapılandırma dosyasıdır ve Service.svc hizmet dosyasıdır. Derleme şu konuma kopyalanır: % SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-170">The service file is Service.svc and the configuration file is Web.config. After compilation, they are copied to the following location: %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.</span></span>  
  
-   <span data-ttu-id="ebcf3-171">WasNetActivator: UDP Etkinleştirici program.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-171">WasNetActivator: The UDP activator program.</span></span>  
  
-   <span data-ttu-id="ebcf3-172">Tüm gerekli parçaları düzgün yüklendiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-172">Ensure that all of the required pieces are installed correctly.</span></span> <span data-ttu-id="ebcf3-173">Aşağıdaki adımlarda, örnek çalıştırmak gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ebcf3-173">The following steps show how to run the sample:</span></span>  
  
1.  <span data-ttu-id="ebcf3-174">Aşağıdaki Windows Hizmetleri başlatıldığından emin olun:</span><span class="sxs-lookup"><span data-stu-id="ebcf3-174">Ensure that the following Windows services have been started:</span></span>  
  
    -   <span data-ttu-id="ebcf3-175">Windows İşlem Etkinleştirme Hizmeti (WAS).</span><span class="sxs-lookup"><span data-stu-id="ebcf3-175">Windows Process Activation Service (WAS).</span></span>  
  
    -   <span data-ttu-id="ebcf3-176">Internet Information Services (IIS): W3SVC.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-176">Internet Information Services (IIS): W3SVC.</span></span>  
  
2.  <span data-ttu-id="ebcf3-177">Daha sonra WasNetActivator.exe Etkinleştirici başlatın.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-177">Then start the activator, WasNetActivator.exe.</span></span> <span data-ttu-id="ebcf3-178">Altında **etkinleştirme** sekmesi, tek protokol **UDP**, aşağı açılan listeden seçilir.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-178">Under the **Activation** tab, the only protocol, **UDP**, is selected in the drop down list.</span></span> <span data-ttu-id="ebcf3-179">Tıklayın **Başlat** düğmesi Etkinleştirici başlatılamadı.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-179">Click the **Start** button to start the activator.</span></span>  
  
3.  <span data-ttu-id="ebcf3-180">Etkinleştirici başlatıldıktan sonra bir komut penceresinden Client.exe çalıştırarak, istemci kodu çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-180">Once the activator is started, you can run the client code by running Client.exe from a command window.</span></span> <span data-ttu-id="ebcf3-181">Örnek çıktı verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="ebcf3-181">The following is the sample output:</span></span>  
  
    ```  
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
>  <span data-ttu-id="ebcf3-182">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-182">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ebcf3-183">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-183">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ebcf3-184">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-184">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ebcf3-185">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-185">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\UdpActivation`  
  
## <a name="see-also"></a><span data-ttu-id="ebcf3-186">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ebcf3-186">See Also</span></span>
