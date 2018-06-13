---
title: UDP Etkinleştirme
ms.date: 03/30/2017
ms.assetid: 4b0ccd10-0dfb-4603-93f9-f0857c581cb7
ms.openlocfilehash: 9f7600bff17c015f28c3fb94ed5360561d45c65b
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33810037"
---
# <a name="udp-activation"></a><span data-ttu-id="27177-102">UDP Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="27177-102">UDP Activation</span></span>
<span data-ttu-id="27177-103">Bu örnek dayanır [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="27177-103">This sample is based on the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span> <span data-ttu-id="27177-104">Bunu genişletir [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) Windows İşlem Etkinleştirme Hizmeti (WAS) kullanarak işlem etkinleştirmeyi desteklemek için örnek.</span><span class="sxs-lookup"><span data-stu-id="27177-104">It extends the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample to support process activation using the Windows Process Activation Service (WAS).</span></span>  
  
 <span data-ttu-id="27177-105">Örnek üç önemli parçaları oluşur:</span><span class="sxs-lookup"><span data-stu-id="27177-105">The sample consists of three major pieces:</span></span>  
  
-   <span data-ttu-id="27177-106">Bir UDP protokolünü Etkinleştirici, etkinleştirilmesi için olan uygulamaları adına UDP iletileri alan bir tek başına işlemi.</span><span class="sxs-lookup"><span data-stu-id="27177-106">A UDP Protocol Activator, a standalone process that receives UDP messages on behalf of applications that are to be activated.</span></span>  
  
-   <span data-ttu-id="27177-107">İleti göndermek için UDP özel taşıma kullanan istemci.</span><span class="sxs-lookup"><span data-stu-id="27177-107">A client that uses the UDP custom transport to send messages.</span></span>  
  
-   <span data-ttu-id="27177-108">UDP özel taşıma iletileri alan (WAS tarafından etkinleştirilen bir çalışan işlemde barındırılan) bir hizmet.</span><span class="sxs-lookup"><span data-stu-id="27177-108">A service (hosted in a worker process activated by WAS) that receives messages over the UDP custom transport.</span></span>  
  
## <a name="udp-protocol-activator"></a><span data-ttu-id="27177-109">UDP protokolünü Etkinleştirici</span><span class="sxs-lookup"><span data-stu-id="27177-109">UDP Protocol Activator</span></span>  
 <span data-ttu-id="27177-110">UDP protokolünü Etkinleştirici WCF istemcisini ve WCF hizmeti arasında bir köprü ' dir.</span><span class="sxs-lookup"><span data-stu-id="27177-110">The UDP Protocol Activator is a bridge between the WCF client and the WCF service.</span></span> <span data-ttu-id="27177-111">Aktarım katmanında UDP protokolü aracılığıyla veri iletişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="27177-111">It provides data communication through the UDP protocol at the transport layer.</span></span> <span data-ttu-id="27177-112">İki ana işlevi vardır:</span><span class="sxs-lookup"><span data-stu-id="27177-112">It has two major functions:</span></span>  
  
-   <span data-ttu-id="27177-113">Dinleyici Bağdaştırıcısı (hangi işlemleri gelen iletilere yanıt olarak etkinleştirmek için WAS ile güvenliktir LA), OLUŞTU.</span><span class="sxs-lookup"><span data-stu-id="27177-113">WAS Listener Adapter (LA), which collaborates with WAS to activate processes in response to incoming messages.</span></span>  
  
-   <span data-ttu-id="27177-114">UDP protokol UDP iletileri etkinleştirilmesi için olan uygulamaları adına kabul eden dinleyicisi.</span><span class="sxs-lookup"><span data-stu-id="27177-114">UDP Protocol Listener, which accepts UDP messages on behalf of applications that are to be activated.</span></span>  
  
 <span data-ttu-id="27177-115">Etkinleştirici bağımsız bir program olarak server makinesinde çalıştırması gerekir.</span><span class="sxs-lookup"><span data-stu-id="27177-115">The activator must be running as a standalone program on the server machine.</span></span> <span data-ttu-id="27177-116">Normalde, uzun süre çalışan Windows Hizmetleri (örneğin, NetTcpActivator ve NetPipeActivator) WAS dinleyici bağdaştırıcılarına uygulanır.</span><span class="sxs-lookup"><span data-stu-id="27177-116">Normally, WAS listener adapters (such as the NetTcpActivator and the NetPipeActivator) are implemented in long-running Windows services.</span></span> <span data-ttu-id="27177-117">Ancak, Basitlik ve daha anlaşılır olması için bu örnek, Protokolü Etkinleştirici bir tek başına uygulama olarak'e uygular.</span><span class="sxs-lookup"><span data-stu-id="27177-117">However, for simplicity and clarity, this sample implements the protocol activator as a standalone application.</span></span>  
  
### <a name="was-listener-adapter"></a><span data-ttu-id="27177-118">Dinleyici Bağdaştırıcısı edildi</span><span class="sxs-lookup"><span data-stu-id="27177-118">WAS Listener Adapter</span></span>  
 <span data-ttu-id="27177-119">UDP için olan dinleyici bağdaştırıcısı uygulanan `UdpListenerAdapter` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="27177-119">The WAS Listener Adapter for UDP is implemented in the `UdpListenerAdapter` class.</span></span> <span data-ttu-id="27177-120">WAS uygulama etkinleştirme için UDP protokolünü gerçekleştirmek için etkileşimde modüldür.</span><span class="sxs-lookup"><span data-stu-id="27177-120">It is the module that interacts with WAS to perform application activation for the UDP protocol.</span></span> <span data-ttu-id="27177-121">Bu, aşağıdaki Webhost API'ları çağırarak sağlanır:</span><span class="sxs-lookup"><span data-stu-id="27177-121">This is achieved by calling the following Webhost APIs:</span></span>  
  
-   `WebhostRegisterProtocol`  
  
-   `WebhostUnregisterProtocol`  
  
-   `WebhostOpenListenerChannelInstance`  
  
-   `WebhostCloseAllListenerChannelInstances`  
  
 <span data-ttu-id="27177-122">Başlangıçta çağrıldıktan sonra `WebhostRegisterProtocol`, geri çağırma Dinleyici Bağdaştırıcısı alır `ApplicationCreated` WAS tüm uygulamalar için gelen kayıtlı (windir%\system32\inetsrv içinde bulunur) applicationHost.config içinde.</span><span class="sxs-lookup"><span data-stu-id="27177-122">After initially calling `WebhostRegisterProtocol`, the listener adapter receives the callback `ApplicationCreated` from WAS for all of the applications registered in applicationHost.config (located in %windir%\system32\inetsrv).</span></span> <span data-ttu-id="27177-123">Bu örnekte, biz yalnızca etkin uygulamaları UDP protokolünü (kimlikli Protokolü "net.udp" olarak) ile işler.</span><span class="sxs-lookup"><span data-stu-id="27177-123">In this sample, we only handle the applications with the UDP protocol (with the protocol id as "net.udp") enabled.</span></span> <span data-ttu-id="27177-124">Bu tür uygulamalar (örneğin, etkin devre dışı bir uygulama geçiş) uygulamaya dinamik yapılandırma değişikliklerine yanıt verme durumunda diğer uygulamalar bu farklı şekilde işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="27177-124">Other implementations may handle this differently if such implementations respond to dynamic configuration changes to the application (for example, an application transition from disabled to enabled).</span></span>  
  
 <span data-ttu-id="27177-125">Zaman geri çağırma `ConfigManagerInitializationCompleted` alınan, belirtir, WAS protokol başlatma bildirimlerini tümünün bitirdi.</span><span class="sxs-lookup"><span data-stu-id="27177-125">When the callback `ConfigManagerInitializationCompleted` is received, it indicates that WAS has finished all of the notifications for the initialization of the protocol.</span></span> <span data-ttu-id="27177-126">Bu aşamada, etkinleştirme isteklerini işlemek Dinleyici Bağdaştırıcısı hazırdır.</span><span class="sxs-lookup"><span data-stu-id="27177-126">At this time, the listener adapter is ready to process activation requests.</span></span>  
  
 <span data-ttu-id="27177-127">Bir uygulamayı ilk kez içinde yeni bir istek geldiğinde, dinleyici bağdaştırıcısını çağırır `WebhostOpenListenerChannelInstance` WAS başladığı çalışan işlemi henüz başlamamışsa.</span><span class="sxs-lookup"><span data-stu-id="27177-127">When a new request comes in the first time for an application, the listener adapter calls `WebhostOpenListenerChannelInstance` into WAS, which starts the worker process if it is not started yet.</span></span> <span data-ttu-id="27177-128">Ardından protokol işleyici yüklenir ve sanal uygulama ile dinleyici bağdaştırıcısı arasındaki iletişimi başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27177-128">Then the protocol handlers are loaded and the communication between the listener adapter and the virtual application can start.</span></span>  
  
 <span data-ttu-id="27177-129">Dinleyici Bağdaştırıcısı %SystemRoot%\System32\inetsrv\ApplicationHost.config kayıtlı <`listenerAdapters`> bölümünde aşağıdaki gibi:</span><span class="sxs-lookup"><span data-stu-id="27177-129">The listener adapter is registered in the %SystemRoot%\System32\inetsrv\ApplicationHost.config in the <`listenerAdapters`> section as following:</span></span>  
  
```xml  
<add name="net.udp" identity="S-1-5-21-2127521184-1604012920-1887927527-387045" />  
```  
  
### <a name="protocol-listener"></a><span data-ttu-id="27177-130">Protokol dinleyicisi</span><span class="sxs-lookup"><span data-stu-id="27177-130">Protocol Listener</span></span>  
 <span data-ttu-id="27177-131">UDP protokolünü dinleyicisi UDP uç noktada sanal uygulama adına dinler Protokolü Etkinleştirici içinde bir modüldür.</span><span class="sxs-lookup"><span data-stu-id="27177-131">The UDP protocol listener is a module inside the protocol activator that listens at a UDP endpoint on behalf of the virtual application.</span></span> <span data-ttu-id="27177-132">Sınıfında uygulanır `UdpSocketListener`.</span><span class="sxs-lookup"><span data-stu-id="27177-132">It is implemented in the class `UdpSocketListener`.</span></span> <span data-ttu-id="27177-133">Uç nokta olarak temsil edilir `IPEndpoint` Protokolü bağlama site için hangi bağlantı noktası numarasını ayıklanan için.</span><span class="sxs-lookup"><span data-stu-id="27177-133">The endpoint is represented as `IPEndpoint` for which the port number is extracted from the binding of the protocol for the site.</span></span>  
  
### <a name="control-service"></a><span data-ttu-id="27177-134">Denetim Hizmeti</span><span class="sxs-lookup"><span data-stu-id="27177-134">Control Service</span></span>  
 <span data-ttu-id="27177-135">Bu örnekte, WCF Etkinleştirici ve WAS çalışan işlem arasında iletişim kurmak için kullanırız.</span><span class="sxs-lookup"><span data-stu-id="27177-135">In this sample, we use WCF to communicate between the activator and the WAS worker process.</span></span> <span data-ttu-id="27177-136">Etkinleştirici bulunduğu hizmet denetimi hizmeti adı verilir.</span><span class="sxs-lookup"><span data-stu-id="27177-136">The service that resides in the activator is called the Control Service.</span></span>  
  
## <a name="protocol-handlers"></a><span data-ttu-id="27177-137">Protokol işleyici</span><span class="sxs-lookup"><span data-stu-id="27177-137">Protocol Handlers</span></span>  
 <span data-ttu-id="27177-138">Dinleyici Bağdaştırıcısı çağrıları sonra `WebhostOpenListenerChannelInstance`, onu başlatılmadıysa WAS İşlem Yöneticisi'ni çalışan işlemi başlatır.</span><span class="sxs-lookup"><span data-stu-id="27177-138">After the listener adapter calls `WebhostOpenListenerChannelInstance`, the WAS process manager starts the worker process if it is not started.</span></span> <span data-ttu-id="27177-139">Çalışan işlemi içinde uygulama Yöneticisi daha sonra UDP işlem protokol işleyici (PPH) söz konusu bir istekle yükler `ListenerChannelId`.</span><span class="sxs-lookup"><span data-stu-id="27177-139">The application manager inside the worker process then loads the UDP Process Protocol Handler (PPH) with the request for that `ListenerChannelId`.</span></span> <span data-ttu-id="27177-140">Kapatır çağrılarında PPH `IAdphManager`.`StartAppDomainProtocolListenerChannel`</span><span class="sxs-lookup"><span data-stu-id="27177-140">The PPH in turns calls `IAdphManager`.`StartAppDomainProtocolListenerChannel`</span></span> <span data-ttu-id="27177-141">UDP AppDomain protokol işleyici (ADPH) başlatmak için.</span><span class="sxs-lookup"><span data-stu-id="27177-141">to start the UDP AppDomain Protocol Handler (ADPH).</span></span>  
  
## <a name="hostedudptransportconfiguration"></a><span data-ttu-id="27177-142">HostedUDPTransportConfiguration</span><span class="sxs-lookup"><span data-stu-id="27177-142">HostedUDPTransportConfiguration</span></span>  
 <span data-ttu-id="27177-143">Bilgiler Web.Config'de şu şekilde kaydedilir:</span><span class="sxs-lookup"><span data-stu-id="27177-143">The information is registered in the Web.config as follows:</span></span>  
  
```xml  
<serviceHostingEnvironment>  
<add name="net.udp" transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />  
</serviceHostingEnvironment>  
```  
  
## <a name="special-setup-for-this-sample"></a><span data-ttu-id="27177-144">Bu örnek için özel kurulum</span><span class="sxs-lookup"><span data-stu-id="27177-144">Special Setup for This Sample</span></span>  
 <span data-ttu-id="27177-145">Bu örnek yalnızca yerleşik ve Windows Vista, Windows Server 2008 veya Windows 7'yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="27177-145">This sample can be only built and run on Windows Vista, Windows Server 2008, or Windows 7.</span></span> <span data-ttu-id="27177-146">Örneği çalıştırmak için önce doğru olarak ayarlanmış tüm bileşenleri edinmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="27177-146">To run the sample, you must first get all of the components set up correctly.</span></span> <span data-ttu-id="27177-147">Örneği yüklemek için aşağıdaki adımları kullanın.</span><span class="sxs-lookup"><span data-stu-id="27177-147">Use the following steps to install the sample.</span></span>  
  
#### <a name="to-set-up-this-sample"></a><span data-ttu-id="27177-148">Bu örneğini kurmak için</span><span class="sxs-lookup"><span data-stu-id="27177-148">To set up this sample</span></span>  
  
1.  <span data-ttu-id="27177-149">Yükleme [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aşağıdaki komutu kullanarak 4.0.</span><span class="sxs-lookup"><span data-stu-id="27177-149">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="27177-150">Windows Vista'da projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="27177-150">Build the project on Windows Vista.</span></span> <span data-ttu-id="27177-151">Derleme sonra ayrıca oluşturma sonrası aşamasında aşağıdaki işlemleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="27177-151">After compilation, it also performs the following operations in the post-build phase:</span></span>  
  
    -   <span data-ttu-id="27177-152">UDP bağlama "Default Web Site" sitesine yükler.</span><span class="sxs-lookup"><span data-stu-id="27177-152">Installs the UDP binding to the site "Default Web Site".</span></span>  
  
    -   <span data-ttu-id="27177-153">Fiziksel yolu işaret edecek şekilde sanal uygulama "ServiceModelSamples" oluşturur: "% SystemDrive%\inetpub\wwwroot\servicemodelsamples".</span><span class="sxs-lookup"><span data-stu-id="27177-153">Creates the virtual application "ServiceModelSamples" to point to the physical path: "%SystemDrive%\inetpub\wwwroot\servicemodelsamples".</span></span>  
  
    -   <span data-ttu-id="27177-154">Ayrıca, bu sanal uygulama için "net.udp" Protokolü sağlar.</span><span class="sxs-lookup"><span data-stu-id="27177-154">It also enables "net.udp" protocol for this virtual application.</span></span>  
  
3.  <span data-ttu-id="27177-155">Kullanıcı arabirimini uygulaması "WasNetActivator.exe" başlatın.</span><span class="sxs-lookup"><span data-stu-id="27177-155">Start the user interface application "WasNetActivator.exe".</span></span> <span data-ttu-id="27177-156">Tıklatın **Kurulum** sekmesinde, aşağıdaki onay kutularını işaretleyin ve ardından **yükleme** bunları yüklemek için:</span><span class="sxs-lookup"><span data-stu-id="27177-156">Click the **Setup** tab, check the following check boxes and then click **Install** to install them:</span></span>  
  
    -   <span data-ttu-id="27177-157">UDP Dinleyici Bağdaştırıcısı</span><span class="sxs-lookup"><span data-stu-id="27177-157">UDP Listener Adapter</span></span>  
  
    -   <span data-ttu-id="27177-158">UDP protokol işleyici</span><span class="sxs-lookup"><span data-stu-id="27177-158">UDP Protocol Handlers</span></span>  
  
4.  <span data-ttu-id="27177-159">Tıklatın **etkinleştirme** kullanıcı arabirimini uygulaması "WasNetActivator.exe" sekmesinde.</span><span class="sxs-lookup"><span data-stu-id="27177-159">Click the **Activation** tab of the user interface application "WasNetActivator.exe".</span></span> <span data-ttu-id="27177-160">Tıklatın **Başlat** Dinleyici Bağdaştırıcısı başlamak için Başlat.</span><span class="sxs-lookup"><span data-stu-id="27177-160">Click the **Start** button to start the listener adapter.</span></span> <span data-ttu-id="27177-161">Şimdi program çalıştırılmaya hazır.</span><span class="sxs-lookup"><span data-stu-id="27177-161">Now you are ready to run the program.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="27177-162">Bu örnek ile işiniz bittiğinde, gelen "Default Web Site" net.udp bağlama kaldırmak için Cleanup.bat çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="27177-162">When you are finished with this sample, you must run Cleanup.bat to remove the net.udp binding from the "Default Web Site".</span></span>  
  
## <a name="sample-usage"></a><span data-ttu-id="27177-163">Örnek Kullanım</span><span class="sxs-lookup"><span data-stu-id="27177-163">Sample Usage</span></span>  
 <span data-ttu-id="27177-164">Derleme sonra oluşturulan dört farklı ikili dosyalar vardır:</span><span class="sxs-lookup"><span data-stu-id="27177-164">After compilation, there are four different binaries generated:</span></span>  
  
-   <span data-ttu-id="27177-165">Client.exe: İstemci kodu.</span><span class="sxs-lookup"><span data-stu-id="27177-165">Client.exe: The client code.</span></span> <span data-ttu-id="27177-166">App.config istemci yapılandırma dosyasına Client.exe.config derlenir.</span><span class="sxs-lookup"><span data-stu-id="27177-166">The App.config is compiled into the client configuration file Client.exe.config.</span></span>  
  
-   <span data-ttu-id="27177-167">UDPActivation.dll: tüm önemli UDP uygulamaları içeren kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="27177-167">UDPActivation.dll: the library that contains all of the major UDP implementations.</span></span>  
  
-   <span data-ttu-id="27177-168">Service.dll: Hizmet kodu.</span><span class="sxs-lookup"><span data-stu-id="27177-168">Service.dll: The service code.</span></span> <span data-ttu-id="27177-169">Bu sanal uygulama ServiceModelSamples \bin dizinine kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="27177-169">This is copied to the \bin directory of the virtual application ServiceModelSamples.</span></span> <span data-ttu-id="27177-170">Hizmet dosyası Service.svc ve Web.config yapılandırma dosyası değil. Derleme sonra aşağıdaki konuma kopyalanmadığı: % SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="27177-170">The service file is Service.svc and the configuration file is Web.config. After compilation, they are copied to the following location: %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.</span></span>  
  
-   <span data-ttu-id="27177-171">WasNetActivator: UDP Etkinleştirici program.</span><span class="sxs-lookup"><span data-stu-id="27177-171">WasNetActivator: The UDP activator program.</span></span>  
  
-   <span data-ttu-id="27177-172">Tüm gerekli parça doğru şekilde yüklendiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="27177-172">Ensure that all of the required pieces are installed correctly.</span></span> <span data-ttu-id="27177-173">Aşağıdaki adımlar örneği çalıştırma gösterir:</span><span class="sxs-lookup"><span data-stu-id="27177-173">The following steps show how to run the sample:</span></span>  
  
1.  <span data-ttu-id="27177-174">Aşağıdaki Windows hizmetlerin başlatıldığından emin olun:</span><span class="sxs-lookup"><span data-stu-id="27177-174">Ensure that the following Windows services have been started:</span></span>  
  
    -   <span data-ttu-id="27177-175">Windows İşlem Etkinleştirme Hizmeti (WAS).</span><span class="sxs-lookup"><span data-stu-id="27177-175">Windows Process Activation Service (WAS).</span></span>  
  
    -   <span data-ttu-id="27177-176">Internet Information Services (IIS): W3SVC.</span><span class="sxs-lookup"><span data-stu-id="27177-176">Internet Information Services (IIS): W3SVC.</span></span>  
  
2.  <span data-ttu-id="27177-177">Daha sonra WasNetActivator.exe Etkinleştirici başlatın.</span><span class="sxs-lookup"><span data-stu-id="27177-177">Then start the activator, WasNetActivator.exe.</span></span> <span data-ttu-id="27177-178">Altında **etkinleştirme** sekmesi, yalnızca Protokolü **UDP**, aşağı açılan listeden seçilir.</span><span class="sxs-lookup"><span data-stu-id="27177-178">Under the **Activation** tab, the only protocol, **UDP**, is selected in the drop down list.</span></span> <span data-ttu-id="27177-179">Tıklatın **Başlat** Etkinleştirici başlamak için Başlat.</span><span class="sxs-lookup"><span data-stu-id="27177-179">Click the **Start** button to start the activator.</span></span>  
  
3.  <span data-ttu-id="27177-180">Etkinleştirici başladıktan sonra bir komut penceresinde Client.exe çalıştırarak, istemci kodu çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27177-180">Once the activator is started, you can run the client code by running Client.exe from a command window.</span></span> <span data-ttu-id="27177-181">Örnek çıktı verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="27177-181">The following is the sample output:</span></span>  
  
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
>  <span data-ttu-id="27177-182">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="27177-182">The samples may already be installed on your machine.</span></span> <span data-ttu-id="27177-183">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="27177-183">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="27177-184">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="27177-184">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="27177-185">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="27177-185">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\UdpActivation`  
  
## <a name="see-also"></a><span data-ttu-id="27177-186">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="27177-186">See Also</span></span>
