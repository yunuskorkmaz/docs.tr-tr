---
title: HttpCookieSession
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 101cb624-8303-448a-a3af-933247c1e109
caps.latest.revision: "31"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4c06efd7450afe93eaecca1e678eb6f8bf5de7a6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="httpcookiesession"></a><span data-ttu-id="54adb-102">HttpCookieSession</span><span class="sxs-lookup"><span data-stu-id="54adb-102">HttpCookieSession</span></span>
<span data-ttu-id="54adb-103">Bu örnek özel protokol kanalı oturum yönetimi için HTTP tanımlama bilgilerini kullanacak şekilde nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="54adb-103">This sample demonstrates how to build a custom protocol channel to use HTTP cookies for session management.</span></span> <span data-ttu-id="54adb-104">Bu kanal arasında iletişimi sağlayan [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Hizmetleri ve ASMX istemciler veya arasında [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemciler ve ASMX hizmetler.</span><span class="sxs-lookup"><span data-stu-id="54adb-104">This channel enables communication between [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services and ASMX clients or between [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients and ASMX services.</span></span>  
  
 <span data-ttu-id="54adb-105">Oturum tabanlı bir istemci Web yöntemi bir ASMX Web hizmetinde, çağırdığında [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] altyapısı şunları gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="54adb-105">When a client calls a Web method in an ASMX Web service that is session-based, the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] engine does the following:</span></span>  
  
-   <span data-ttu-id="54adb-106">Benzersiz bir kimliği (oturum kimliği) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="54adb-106">Generates a unique ID (session ID).</span></span>  
  
-   <span data-ttu-id="54adb-107">Oturum nesnesi oluşturur ve benzersiz kimliği ile ilişkilendirir</span><span class="sxs-lookup"><span data-stu-id="54adb-107">Generates the session object and associates it with the unique ID.</span></span>  
  
-   <span data-ttu-id="54adb-108">Set-Cookie HTTP yanıt üst bilgisi için benzersiz kimlik ekler ve istemciye gönderir.</span><span class="sxs-lookup"><span data-stu-id="54adb-108">Adds the unique ID to a Set-Cookie HTTP response header and sends it to the client.</span></span>  
  
-   <span data-ttu-id="54adb-109">Oturum kimliği temel alarak sonraki çağrılar için gönderir istemcide tanımlar.</span><span class="sxs-lookup"><span data-stu-id="54adb-109">Identifies the client on subsequent calls based on the session ID it sends to it.</span></span>  
  
 <span data-ttu-id="54adb-110">İstemci bu oturum kimliği, sonraki istekleri sunucuya içerir.</span><span class="sxs-lookup"><span data-stu-id="54adb-110">The client includes this session ID in its subsequent requests to the server.</span></span> <span data-ttu-id="54adb-111">Sunucu, geçerli HTTP bağlamı için uygun session nesnesi yüklemek için istemci oturum kimliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="54adb-111">The server uses the session ID from the client to load the appropriate session object for the current HTTP context.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="54adb-112">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="54adb-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="54adb-113">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="54adb-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="54adb-114">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="54adb-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="54adb-115">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="54adb-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpCookieSession`  
  
## <a name="httpcookiesession-channel-message-exchange-pattern"></a><span data-ttu-id="54adb-116">HttpCookieSession kanal ileti değişim deseni</span><span class="sxs-lookup"><span data-stu-id="54adb-116">HttpCookieSession Channel Message Exchange Pattern</span></span>  
 <span data-ttu-id="54adb-117">Bu örnek oturumları ASMX gibi senaryolar için etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="54adb-117">This sample enables sessions for ASMX-like scenarios.</span></span> <span data-ttu-id="54adb-118">Bizim kanal yığın alt kısmındaki sahibiz desteklediği HTTP taşıma <xref:System.ServiceModel.Channels.IRequestChannel> ve <xref:System.ServiceModel.Channels.IReplyChannel>.</span><span class="sxs-lookup"><span data-stu-id="54adb-118">At the bottom of our channel stack, we have the HTTP transport that supports <xref:System.ServiceModel.Channels.IRequestChannel> and <xref:System.ServiceModel.Channels.IReplyChannel>.</span></span> <span data-ttu-id="54adb-119">Kanal yığını daha yüksek düzeyde oturumları sağlamak için kanalının işidir.</span><span class="sxs-lookup"><span data-stu-id="54adb-119">It is the job of the channel to provide sessions to the higher levels of the channel stack.</span></span> <span data-ttu-id="54adb-120">Örnek iki kanalı uygular (<xref:System.ServiceModel.Channels.IRequestSessionChannel> ve <xref:System.ServiceModel.Channels.IReplySessionChannel>) oturumları destekler.</span><span class="sxs-lookup"><span data-stu-id="54adb-120">The sample implements two channels, (<xref:System.ServiceModel.Channels.IRequestSessionChannel> and <xref:System.ServiceModel.Channels.IReplySessionChannel>) that support sessions.</span></span>  
  
## <a name="service-channel"></a><span data-ttu-id="54adb-121">Hizmet kanal</span><span class="sxs-lookup"><span data-stu-id="54adb-121">Service Channel</span></span>  
 <span data-ttu-id="54adb-122">Örnek bir hizmet kanalda sağlar `HttpCookieReplySessionChannelListener` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="54adb-122">The sample provides a service channel in the `HttpCookieReplySessionChannelListener` class.</span></span> <span data-ttu-id="54adb-123">Bu sınıf uygulayan <xref:System.ServiceModel.Channels.IChannelListener> arabirimi ve dönüştürür <xref:System.ServiceModel.Channels.IReplyChannel> için kanal yığındaki alt kanalından bir <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span><span class="sxs-lookup"><span data-stu-id="54adb-123">This class implements the <xref:System.ServiceModel.Channels.IChannelListener> interface and converts the <xref:System.ServiceModel.Channels.IReplyChannel> channel from lower in the channel stack to a <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span></span> <span data-ttu-id="54adb-124">Bu işlem aşağıdaki bölümlere ayrılmıştır:</span><span class="sxs-lookup"><span data-stu-id="54adb-124">This process can be divided into the following parts:</span></span>  
  
-   <span data-ttu-id="54adb-125">Kanal dinleyicisi açıldığında, kendi iç dinleyici iç bir kanaldan kabul eder.</span><span class="sxs-lookup"><span data-stu-id="54adb-125">When the channel listener is opened, it accepts an inner channel from its inner listener.</span></span> <span data-ttu-id="54adb-126">Bir veri birimi dinleyicisi iç dinleyici olduğundan ve kabul edilen bir kanal ömrü dinleyicisi ömrü ayrılmış olduğundan, biz iç dinleyici kapatın ve yalnızca iç kanala tutun</span><span class="sxs-lookup"><span data-stu-id="54adb-126">Because the inner listener is a datagram listener and the lifetime of an accepted channel is decoupled from the lifetime of the listener, we can close the inner listener and only hold on to the inner channel</span></span>  
  
    ```  
                this.innerChannelListener.Open(timeoutHelper.RemainingTime());  
    this.innerChannel = this.innerChannelListener.AcceptChannel(timeoutHelper.RemainingTime());  
    this.innerChannel.Open(timeoutHelper.RemainingTime());  
    this.innerChannelListener.Close(timeoutHelper.RemainingTime());  
    ```  
  
-   <span data-ttu-id="54adb-127">Açma işlemi tamamlandıktan sonra bir ileti döngüsü iç kanaldan iletiler alan için ayarlarız.</span><span class="sxs-lookup"><span data-stu-id="54adb-127">When the open process completes, we set up a message loop to receive messages from the inner channel.</span></span>  
  
    ```  
    IAsyncResult result = BeginInnerReceiveRequest();  
    if (result != null && result.CompletedSynchronously)  
    {  
       // do not block the user thread  
       if (this.completeReceiveCallback == null)  
       {  
          this.completeReceiveCallback = new WaitCallback(CompleteReceiveCallback);  
       }  
       ThreadPool.QueueUserWorkItem(this.completeReceiveCallback, result);  
    }  
    ```  
  
-   <span data-ttu-id="54adb-128">Bir ileti geldiğinde hizmet kanalı oturum tanımlayıcısı inceler ve uygun oturum kanalı çoğullamasını.</span><span class="sxs-lookup"><span data-stu-id="54adb-128">When a message arrives, the service channel examines the session identifier and de-multiplexes to the appropriate session channel.</span></span> <span data-ttu-id="54adb-129">Kanal dinleyicisi oturum tanımlayıcıları oturum kanalı örneklerine eşleyen bir sözlüğü bulundurur.</span><span class="sxs-lookup"><span data-stu-id="54adb-129">The channel listener maintains a dictionary that maps the session identifiers to the session channel instances.</span></span>  
  
    ```  
    Dictionary<string, IReplySessionChannel> channelMapping;  
    ```  
  
 <span data-ttu-id="54adb-130">`HttpCookieReplySessionChannel` Uygulayan sınıf <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span><span class="sxs-lookup"><span data-stu-id="54adb-130">The `HttpCookieReplySessionChannel` class implements <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span></span> <span data-ttu-id="54adb-131">Kanal yüksek düzeyde çağrı yığınını <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> bu oturum için okunan isteklere yöntemi.</span><span class="sxs-lookup"><span data-stu-id="54adb-131">Higher levels of the channel stack call the <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> method to read requests for this session.</span></span> <span data-ttu-id="54adb-132">Her oturum kanalı hizmet kanal tarafından doldurulan bir özel ileti sırası vardır.</span><span class="sxs-lookup"><span data-stu-id="54adb-132">Each session channel has a private message queue that is populated by the service channel.</span></span>  
  
```  
InputQueue<RequestContext> requestQueue;  
```  
  
 <span data-ttu-id="54adb-133">Birisi çağırdığında durumda <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> yöntemi ve ileti sıraya iletiler yoktur, kendisini kapatmadan önce belirtilen bir süre için kanal bekler.</span><span class="sxs-lookup"><span data-stu-id="54adb-133">In the case when someone calls the <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> method and there are no messages in the message queue, the channel waits for a specified amount of time before shutting itself down.</span></span> <span data-ttu-id="54adb-134">Bunun için oluşturulan oturum kanalları temizler olmayan[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemciler.</span><span class="sxs-lookup"><span data-stu-id="54adb-134">This cleans up the session channels created for non-[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients.</span></span>  
  
 <span data-ttu-id="54adb-135">Kullanırız `channelMapping` izlemek için `ReplySessionChannels`, ve bizim temel kapatmayın `innerChannel` kabul edilen tüm kanalları kapatılana kadar.</span><span class="sxs-lookup"><span data-stu-id="54adb-135">We use the `channelMapping` to track the `ReplySessionChannels`, and we do not close our underlying `innerChannel` until all the accepted channels have been closed.</span></span> <span data-ttu-id="54adb-136">Bu şekilde `HttpCookieReplySessionChannel` ömrü bulunabilir `HttpCookieReplySessionChannelListener`.</span><span class="sxs-lookup"><span data-stu-id="54adb-136">This way `HttpCookieReplySessionChannel` can exist beyond the lifetime of `HttpCookieReplySessionChannelListener`.</span></span> <span data-ttu-id="54adb-137">Biz de kabul edilen kanallar kendi dinleyicisi başvuru korudukları için bize altında toplanacak alma dinleyicisi hakkında endişelenmeniz gerekmez `OnClosed` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="54adb-137">We also do not have to worry about the listener getting garbage collected underneath us because the accepted channels keep a reference to their listener through the `OnClosed` callback.</span></span>  
  
## <a name="client-channel"></a><span data-ttu-id="54adb-138">İstemci kanal</span><span class="sxs-lookup"><span data-stu-id="54adb-138">Client channel</span></span>  
 <span data-ttu-id="54adb-139">Karşılık gelen istemci kanal bulunduğu `HttpCookieSessionChannelFactory` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="54adb-139">The corresponding client channel is in the `HttpCookieSessionChannelFactory` class.</span></span> <span data-ttu-id="54adb-140">Kanal oluşturma sırasında kanal fabrikası iç isteği kanalıyla saran bir `HttpCookieRequestSessionChannel`.</span><span class="sxs-lookup"><span data-stu-id="54adb-140">During channel creation, the channel factory wraps the inner request channel with an `HttpCookieRequestSessionChannel`.</span></span> <span data-ttu-id="54adb-141">`HttpCookieRequestSessionChannel` Sınıfı, temel alınan istek kanalı çağrıları iletir.</span><span class="sxs-lookup"><span data-stu-id="54adb-141">The `HttpCookieRequestSessionChannel` class forwards the calls to the underlying request channel.</span></span> <span data-ttu-id="54adb-142">İstemci proxy kapandığında `HttpCookieRequestSessionChannel` kanal kapatıldığını gösterir hizmeti için bir ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="54adb-142">When the client closes the proxy, `HttpCookieRequestSessionChannel` sends a message to the service that indicates that the channel is being closed.</span></span> <span data-ttu-id="54adb-143">Bu nedenle, hizmet kanal yığını kapatılabilir düzgün biçimde kullanımda oturum kanalı.</span><span class="sxs-lookup"><span data-stu-id="54adb-143">Thus, the service channel stack can gracefully shutdown the session channel that is in use.</span></span>  
  
## <a name="binding-and-binding-element"></a><span data-ttu-id="54adb-144">Bağlama ve bağlama öğesi</span><span class="sxs-lookup"><span data-stu-id="54adb-144">Binding and Binding Element</span></span>  
 <span data-ttu-id="54adb-145">İstemci ve hizmet kanalları oluşturduktan sonra bunları tümleştirmek için sonraki adım olan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="54adb-145">After creating the service and client channels, the next step is to integrate them into the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime.</span></span> <span data-ttu-id="54adb-146">Kanallar için açığa [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bağlamalar ve bağlama öğeleri aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="54adb-146">Channels are exposed to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] through bindings and binding elements.</span></span> <span data-ttu-id="54adb-147">Bir bağlama bir veya daha çok bağlama öğelerden oluşur.</span><span class="sxs-lookup"><span data-stu-id="54adb-147">A binding consists of one or many binding elements.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="54adb-148">birkaç sistem tanımlı bağlamalar sunar. Örneğin, BasicHttpBinding veya WSHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="54adb-148"> offers several system-defined bindings; for example, BasicHttpBinding or WSHttpBinding.</span></span> <span data-ttu-id="54adb-149">`HttpCookieSessionBindingElement` Sınıfı bağlama öğesi uygulamasını içerir.</span><span class="sxs-lookup"><span data-stu-id="54adb-149">The `HttpCookieSessionBindingElement` class contains the implementation for the binding element.</span></span> <span data-ttu-id="54adb-150">Kanal fabrikası oluşturma yöntemleri ve kanal dinleyicisi gerekli kanal dinleyicisi veya kanal fabrikası örneklemesi yapmak için geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="54adb-150">It overrides the channel listener and channel factory creation methods to do the necessary channel listener or channel factory instantiations.</span></span>  
  
 <span data-ttu-id="54adb-151">Örnek ilke onaylamalarını hizmet açıklaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="54adb-151">The sample uses policy assertions for the service description.</span></span> <span data-ttu-id="54adb-152">Bu hizmet tüketebileceği diğer istemcilere kanal gereklilikleri yayımlamak örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="54adb-152">This allows the sample to publish its channel requirements to other clients that can consume the service.</span></span> <span data-ttu-id="54adb-153">Örneğin, bu bağlama öğesi oturumları desteklendiğini bilmesini potansiyel istemcilerin ilke onaylamalarını yayımlar.</span><span class="sxs-lookup"><span data-stu-id="54adb-153">For example, this binding element publishes policy assertions to let potential clients know that it supports sessions.</span></span> <span data-ttu-id="54adb-154">Örnek sağladığından `ExchangeTerminateMessage` bağlama öğesi yapılandırma özelliği, hizmet oturumu konuşma sonlandırmak için ek ileti exchange eylem desteklediğini göstermek için gerekli onaylar ekler.</span><span class="sxs-lookup"><span data-stu-id="54adb-154">Because the sample enables the `ExchangeTerminateMessage` property in the binding element configuration, it adds the necessary assertions to show that the service supports an extra message exchange action to terminate the session conversation.</span></span> <span data-ttu-id="54adb-155">İstemciler daha sonra bu eylemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="54adb-155">Clients can then use this action.</span></span> <span data-ttu-id="54adb-156">Aşağıdaki WSDL'ye oluşturulduğu ilke onaylamalarını gösterir `HttpCookieSessionBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="54adb-156">The following WSDL code shows the policy assertions created from the `HttpCookieSessionBindingElement`.</span></span>  
  
```xml  
<wsp:Policy wsu:Id="HttpCookieSessionBinding_IWcfCookieSessionService_policy" xmlns:wsp="http://schemas.xmlsoap.org/ws/2004/09/policy" xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
<wsp:ExactlyOne>  
<wsp:All>  
<wspe:Utf816FFFECharacterEncoding xmlns:wspe="http://schemas.xmlsoap.org/ws/2004/09/policy/encoding"/>  
<mhsc:httpSessionCookie xmlns:mhsc="http://samples.microsoft.com/wcf/mhsc/policy"/>  
</wsp:All>  
</wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 <span data-ttu-id="54adb-157">`HttpCookieSessionBinding` Daha önce açıklanan bağlama öğesi kullanan sistem tarafından sağlanan bir bağlamayı bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="54adb-157">The `HttpCookieSessionBinding` class is a system-provided binding that uses the binding element described previously.</span></span>  
  
## <a name="adding-the-channel-to-the-configuration-system"></a><span data-ttu-id="54adb-158">Yapılandırma sistemi kanal ekleme</span><span class="sxs-lookup"><span data-stu-id="54adb-158">Adding the Channel to the Configuration System</span></span>  
 <span data-ttu-id="54adb-159">Örnek örnek kanal yapılandırma aracılığıyla kullanıma iki sınıflar sağlar.</span><span class="sxs-lookup"><span data-stu-id="54adb-159">The sample provides two classes that expose the sample channel through configuration.</span></span> <span data-ttu-id="54adb-160">İlki bir <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> için `HttpCookieSessionBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="54adb-160">The first is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> for the `HttpCookieSessionBindingElement`.</span></span> <span data-ttu-id="54adb-161">Uygulama toplu temsilci için `HttpCookieSessionBindingConfigurationElement`, den türetilen <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="54adb-161">The bulk of the implementation is delegated to the `HttpCookieSessionBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="54adb-162">`HttpCookieSessionBindingConfigurationElement` Özellikler üzerinde karşılık gelen özelliklere sahip `HttpCookieSessionBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="54adb-162">The `HttpCookieSessionBindingConfigurationElement` has properties that correspond to the properties on `HttpCookieSessionBindingElement`.</span></span>  
  
### <a name="binding-element-extension-section"></a><span data-ttu-id="54adb-163">Bağlama öğesi uzantısı bölümü</span><span class="sxs-lookup"><span data-stu-id="54adb-163">Binding Element Extension Section</span></span>  
 <span data-ttu-id="54adb-164">Bölüm `HttpCookieSessionBindingElementSection` olan bir <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> kullanıma sunan `HttpCookieSessionBindingElement` yapılandırma sistemi.</span><span class="sxs-lookup"><span data-stu-id="54adb-164">The section `HttpCookieSessionBindingElementSection` is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> that exposes `HttpCookieSessionBindingElement` to the configuration system.</span></span> <span data-ttu-id="54adb-165">Birkaç geçersiz kılmalar, yapılandırma bölümü adı, bağlama öğesi türü ve bağlama öğesi oluşturmak nasıl tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="54adb-165">With a few overrides the configuration section name, the type of the binding element and how to create the binding element are defined.</span></span> <span data-ttu-id="54adb-166">Biz sonra uzantısı bölümüne bir yapılandırma dosyasında şu şekilde kaydedebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="54adb-166">We can then register the extension section in a configuration file as follows:</span></span>  
  
```xml  
<configuration>        
    <system.serviceModel>        
      <extensions>          
        <bindingElementExtensions>            
          <add name="httpCookieSession"   
               type=  
"Microsoft.ServiceModel.Samples.HttpCookieSessionBindingElementElement,   
                    HttpCookieSessionExtension, Version=1.0.0.0,   
                    Culture=neutral, PublicKeyToken=null"/>  
        </bindingElementExtensions >  
      </extensions>  
  
      <bindings>  
      <customBinding>  
        <binding name="allowCookiesBinding">  
          <textMessageEncoding messageVersion="Soap11WSAddressing10" />  
          <httpCookieSession sessionTimeout="10" exchangeTerminateMessage="true" />  
          <httpTransport allowCookies="true" />  
        </binding>  
      </customBinding>  
      </bindings>        
    </system.serviceModel>    
</configuration>  
```  
  
## <a name="test-code"></a><span data-ttu-id="54adb-167">Kodu test</span><span class="sxs-lookup"><span data-stu-id="54adb-167">Test Code</span></span>  
 <span data-ttu-id="54adb-168">Bu örnek aktarım kullanmak için test kodu, istemci ve hizmet dizinler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="54adb-168">Test code for using this sample transport is available in the Client and Service directories.</span></span> <span data-ttu-id="54adb-169">İki sınamaları oluşur — bir test kullanır sahip bir bağlama `allowCookies` kümesine `true` istemci üzerinde.</span><span class="sxs-lookup"><span data-stu-id="54adb-169">It consists of two tests—one test uses a binding with `allowCookies` set to `true` on the client.</span></span> <span data-ttu-id="54adb-170">İkinci test (Sonlandır iletisi exchange kullanarak) açık kapatma bağlamada sağlar.</span><span class="sxs-lookup"><span data-stu-id="54adb-170">The second test enables explicit shutdown (using the terminate message exchange) on the binding.</span></span>  
  
 <span data-ttu-id="54adb-171">Örneği çalıştırdığınızda, aşağıdaki çıktı görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="54adb-171">When you run the sample, you should see the following output:</span></span>  
  
```  
Simple binding:  
AddItem(10000,2): ItemCount=2  
AddItem(10550,5): ItemCount=7  
RemoveItem(10550,2): ItemCount=5  
Items  
10000, 2  
10550, 3  
Smart binding:  
AddItem(10000,2): ItemCount=2  
AddItem(10550,5): ItemCount=7  
RemoveItem(10550,2): ItemCount=5  
Items  
10000, 2  
10550, 3  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="54adb-172">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="54adb-172">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="54adb-173">Yükleme [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aşağıdaki komutu kullanarak 4.0.</span><span class="sxs-lookup"><span data-stu-id="54adb-173">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="54adb-174">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="54adb-174">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="54adb-175">Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="54adb-175">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="54adb-176">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="54adb-176">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54adb-177">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="54adb-177">See Also</span></span>
