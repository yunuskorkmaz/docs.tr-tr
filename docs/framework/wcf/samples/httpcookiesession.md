---
title: HttpCookieSession
ms.date: 03/30/2017
ms.assetid: 101cb624-8303-448a-a3af-933247c1e109
ms.openlocfilehash: 6b7a72fdd814aa9d2e0f125cf4dbdaf63ba753e5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183625"
---
# <a name="httpcookiesession"></a><span data-ttu-id="2345c-102">HttpCookieSession</span><span class="sxs-lookup"><span data-stu-id="2345c-102">HttpCookieSession</span></span>
<span data-ttu-id="2345c-103">Bu örnek, oturum yönetimi için HTTP tanımlama bilgilerini kullanmak üzere özel bir iletişim kanalının nasıl oluşturulabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="2345c-103">This sample demonstrates how to build a custom protocol channel to use HTTP cookies for session management.</span></span> <span data-ttu-id="2345c-104">Bu kanal, Windows Communication Foundation (WCF) hizmetleri ile ASMX istemcileri arasında veya WCF istemcileri ile ASMX hizmetleri arasında iletişim ilerler.</span><span class="sxs-lookup"><span data-stu-id="2345c-104">This channel enables communication between Windows Communication Foundation (WCF) services and ASMX clients or between WCF clients and ASMX services.</span></span>  
  
 <span data-ttu-id="2345c-105">Bir istemci oturum tabanlı bir ASMX Web hizmetinde bir Web yöntemi ni aradığında, ASP.NET altyapısı aşağıdakileri yapar:</span><span class="sxs-lookup"><span data-stu-id="2345c-105">When a client calls a Web method in an ASMX Web service that is session-based, the ASP.NET engine does the following:</span></span>  
  
- <span data-ttu-id="2345c-106">Benzersiz bir kimlik (oturum kimliği) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2345c-106">Generates a unique ID (session ID).</span></span>  
  
- <span data-ttu-id="2345c-107">Oturum nesnesini oluşturur ve benzersiz kimlikle ilişkilendirer.</span><span class="sxs-lookup"><span data-stu-id="2345c-107">Generates the session object and associates it with the unique ID.</span></span>  
  
- <span data-ttu-id="2345c-108">Set-Cookie HTTP yanıt üstbilgisine benzersiz kimliği ekler ve istemciye gönderir.</span><span class="sxs-lookup"><span data-stu-id="2345c-108">Adds the unique ID to a Set-Cookie HTTP response header and sends it to the client.</span></span>  
  
- <span data-ttu-id="2345c-109">İstemciyi, kendisine gönderdiği oturum kimliğine göre sonraki aramalarda tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2345c-109">Identifies the client on subsequent calls based on the session ID it sends to it.</span></span>  
  
 <span data-ttu-id="2345c-110">İstemci, sunucuya sonraki isteklerinde bu oturum kimliğini içerir.</span><span class="sxs-lookup"><span data-stu-id="2345c-110">The client includes this session ID in its subsequent requests to the server.</span></span> <span data-ttu-id="2345c-111">Sunucu, geçerli HTTP bağlamı için uygun oturum nesnesini yüklemek için istemciden gelen oturum kimliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="2345c-111">The server uses the session ID from the client to load the appropriate session object for the current HTTP context.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2345c-112">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="2345c-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2345c-113">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="2345c-113">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="2345c-114">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="2345c-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2345c-115">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="2345c-115">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpCookieSession`  
  
## <a name="httpcookiesession-channel-message-exchange-pattern"></a><span data-ttu-id="2345c-116">httpcookiesession kanal ileti alışverişi deseni</span><span class="sxs-lookup"><span data-stu-id="2345c-116">HttpCookieSession Channel Message Exchange Pattern</span></span>  
 <span data-ttu-id="2345c-117">Bu örnek, ASMX benzeri senaryolar için oturumlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="2345c-117">This sample enables sessions for ASMX-like scenarios.</span></span> <span data-ttu-id="2345c-118">Kanal yığınımızın alt kısmında, http ulaşımı <xref:System.ServiceModel.Channels.IRequestChannel> destekler <xref:System.ServiceModel.Channels.IReplyChannel>ve .</span><span class="sxs-lookup"><span data-stu-id="2345c-118">At the bottom of our channel stack, we have the HTTP transport that supports <xref:System.ServiceModel.Channels.IRequestChannel> and <xref:System.ServiceModel.Channels.IReplyChannel>.</span></span> <span data-ttu-id="2345c-119">Kanal yığınının daha yüksek seviyelerine oturumlar sağlamak kanalın işidir.</span><span class="sxs-lookup"><span data-stu-id="2345c-119">It is the job of the channel to provide sessions to the higher levels of the channel stack.</span></span> <span data-ttu-id="2345c-120">Örnek,<xref:System.ServiceModel.Channels.IRequestSessionChannel> <xref:System.ServiceModel.Channels.IReplySessionChannel>oturumları destekleyen iki kanal uygular.</span><span class="sxs-lookup"><span data-stu-id="2345c-120">The sample implements two channels, (<xref:System.ServiceModel.Channels.IRequestSessionChannel> and <xref:System.ServiceModel.Channels.IReplySessionChannel>) that support sessions.</span></span>  
  
## <a name="service-channel"></a><span data-ttu-id="2345c-121">Servis Kanalı</span><span class="sxs-lookup"><span data-stu-id="2345c-121">Service Channel</span></span>  
 <span data-ttu-id="2345c-122">`HttpCookieReplySessionChannelListener` Örnek, sınıfta bir servis kanalı sağlar.</span><span class="sxs-lookup"><span data-stu-id="2345c-122">The sample provides a service channel in the `HttpCookieReplySessionChannelListener` class.</span></span> <span data-ttu-id="2345c-123">Bu sınıf <xref:System.ServiceModel.Channels.IChannelListener> arabirimi uygular ve <xref:System.ServiceModel.Channels.IReplyChannel> kanalı kanal yığınının alt <xref:System.ServiceModel.Channels.IReplySessionChannel>tan bir ' e dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="2345c-123">This class implements the <xref:System.ServiceModel.Channels.IChannelListener> interface and converts the <xref:System.ServiceModel.Channels.IReplyChannel> channel from lower in the channel stack to a <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span></span> <span data-ttu-id="2345c-124">Bu işlem aşağıdaki bölümlere ayrılabilir:</span><span class="sxs-lookup"><span data-stu-id="2345c-124">This process can be divided into the following parts:</span></span>  
  
- <span data-ttu-id="2345c-125">Kanal dinleyicisi açıldığında, iç dinleyicisinden bir iç kanalı kabul eder.</span><span class="sxs-lookup"><span data-stu-id="2345c-125">When the channel listener is opened, it accepts an inner channel from its inner listener.</span></span> <span data-ttu-id="2345c-126">İç dinleyici bir datagram dinleyici sayıldığından ve kabul edilen bir kanalın ömrü dinleyicinin ömründen ayrıştırıldığı için, iç dinleyiciyi kapatabilir ve yalnızca iç kanala tutunabiliriz.</span><span class="sxs-lookup"><span data-stu-id="2345c-126">Because the inner listener is a datagram listener and the lifetime of an accepted channel is decoupled from the lifetime of the listener, we can close the inner listener and only hold on to the inner channel</span></span>  
  
    ```csharp  
                this.innerChannelListener.Open(timeoutHelper.RemainingTime());  
    this.innerChannel = this.innerChannelListener.AcceptChannel(timeoutHelper.RemainingTime());  
    this.innerChannel.Open(timeoutHelper.RemainingTime());  
    this.innerChannelListener.Close(timeoutHelper.RemainingTime());  
    ```  
  
- <span data-ttu-id="2345c-127">Açık işlem tamamlandığında, iç kanaldan ileti almak için bir ileti döngüsü oluştururuz.</span><span class="sxs-lookup"><span data-stu-id="2345c-127">When the open process completes, we set up a message loop to receive messages from the inner channel.</span></span>  
  
    ```csharp  
    IAsyncResult result = BeginInnerReceiveRequest();  
    if (result != null && result.CompletedSynchronously)  
    {  
       // do not block the user thread  
       this.completeReceiveCallback ??= new WaitCallback(CompleteReceiveCallback);
       ThreadPool.QueueUserWorkItem(this.completeReceiveCallback, result);  
    }  
    ```  
  
- <span data-ttu-id="2345c-128">Bir ileti geldiğinde, servis kanalı oturum tanımlayıcısını inceler ve uygun oturum kanalına çok katlı ları inceler.</span><span class="sxs-lookup"><span data-stu-id="2345c-128">When a message arrives, the service channel examines the session identifier and de-multiplexes to the appropriate session channel.</span></span> <span data-ttu-id="2345c-129">Kanal dinleyicisi, oturum tanımlayıcılarını oturum kanalı örnekleriyle eşleyen bir sözlük tutar.</span><span class="sxs-lookup"><span data-stu-id="2345c-129">The channel listener maintains a dictionary that maps the session identifiers to the session channel instances.</span></span>  
  
    ```csharp  
    Dictionary<string, IReplySessionChannel> channelMapping;  
    ```  
  
 <span data-ttu-id="2345c-130">Sınıf `HttpCookieReplySessionChannel` uygular. <xref:System.ServiceModel.Channels.IReplySessionChannel></span><span class="sxs-lookup"><span data-stu-id="2345c-130">The `HttpCookieReplySessionChannel` class implements <xref:System.ServiceModel.Channels.IReplySessionChannel>.</span></span> <span data-ttu-id="2345c-131">Kanal yığınının daha yüksek <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> düzeyleri, bu oturum için isteklerini okumak için yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="2345c-131">Higher levels of the channel stack call the <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> method to read requests for this session.</span></span> <span data-ttu-id="2345c-132">Her oturum kanalının, hizmet kanalı tarafından doldurulan özel bir ileti sırası vardır.</span><span class="sxs-lookup"><span data-stu-id="2345c-132">Each session channel has a private message queue that is populated by the service channel.</span></span>  
  
```csharp  
InputQueue<RequestContext> requestQueue;  
```  
  
 <span data-ttu-id="2345c-133">Birisi <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> yöntemi aradığında ve ileti kuyruğunda ileti yoksa, kanal kendisini kapatmadan önce belirli bir süre bekler.</span><span class="sxs-lookup"><span data-stu-id="2345c-133">In the case when someone calls the <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> method and there are no messages in the message queue, the channel waits for a specified amount of time before shutting itself down.</span></span> <span data-ttu-id="2345c-134">Bu, WCF olmayan istemciler için oluşturulan oturum kanallarını temizler.</span><span class="sxs-lookup"><span data-stu-id="2345c-134">This cleans up the session channels created for non-WCF clients.</span></span>  
  
 <span data-ttu-id="2345c-135">Biz izlemek `channelMapping` için `ReplySessionChannels`kullanın , ve tüm `innerChannel` kabul edilen kanallar kapatılmış kadar bizim temel kapatmaz.</span><span class="sxs-lookup"><span data-stu-id="2345c-135">We use the `channelMapping` to track the `ReplySessionChannels`, and we do not close our underlying `innerChannel` until all the accepted channels have been closed.</span></span> <span data-ttu-id="2345c-136">Bu `HttpCookieReplySessionChannel` yol ömrü boyunca `HttpCookieReplySessionChannelListener`var olabilir.</span><span class="sxs-lookup"><span data-stu-id="2345c-136">This way `HttpCookieReplySessionChannel` can exist beyond the lifetime of `HttpCookieReplySessionChannelListener`.</span></span> <span data-ttu-id="2345c-137">Ayrıca, kabul edilen kanallar `OnClosed` geri arama yoluyla dinleyicilerine bir referans tuttuğu ndan, dinleyicinin altımızda çöp toplanması konusunda endişelenmemize de gerek yok.</span><span class="sxs-lookup"><span data-stu-id="2345c-137">We also do not have to worry about the listener getting garbage collected underneath us because the accepted channels keep a reference to their listener through the `OnClosed` callback.</span></span>  
  
## <a name="client-channel"></a><span data-ttu-id="2345c-138">İstemci kanalı</span><span class="sxs-lookup"><span data-stu-id="2345c-138">Client channel</span></span>  
 <span data-ttu-id="2345c-139">Karşılık gelen istemci kanalı `HttpCookieSessionChannelFactory` sınıfta.</span><span class="sxs-lookup"><span data-stu-id="2345c-139">The corresponding client channel is in the `HttpCookieSessionChannelFactory` class.</span></span> <span data-ttu-id="2345c-140">Kanal oluşturma sırasında, kanal fabrikası iç istek `HttpCookieRequestSessionChannel`kanalını bir .</span><span class="sxs-lookup"><span data-stu-id="2345c-140">During channel creation, the channel factory wraps the inner request channel with an `HttpCookieRequestSessionChannel`.</span></span> <span data-ttu-id="2345c-141">Sınıf `HttpCookieRequestSessionChannel` çağrıları temel istek kanalına ileter.</span><span class="sxs-lookup"><span data-stu-id="2345c-141">The `HttpCookieRequestSessionChannel` class forwards the calls to the underlying request channel.</span></span> <span data-ttu-id="2345c-142">İstemci proxy'yi `HttpCookieRequestSessionChannel` kapattığında, hizmete kanalın kapatıldığını belirten bir ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="2345c-142">When the client closes the proxy, `HttpCookieRequestSessionChannel` sends a message to the service that indicates that the channel is being closed.</span></span> <span data-ttu-id="2345c-143">Böylece, servis kanalı yığını kullanılmakta olan oturum kanalını düzgün bir şekilde kapatabilir.</span><span class="sxs-lookup"><span data-stu-id="2345c-143">Thus, the service channel stack can gracefully shutdown the session channel that is in use.</span></span>  
  
## <a name="binding-and-binding-element"></a><span data-ttu-id="2345c-144">Bağlama ve Bağlama Elemanı</span><span class="sxs-lookup"><span data-stu-id="2345c-144">Binding and Binding Element</span></span>  
 <span data-ttu-id="2345c-145">Hizmet ve istemci kanalları oluşturulduktan sonra, bir sonraki adım bunları WCF çalışma süresine entegre etmektir.</span><span class="sxs-lookup"><span data-stu-id="2345c-145">After creating the service and client channels, the next step is to integrate them into the WCF runtime.</span></span> <span data-ttu-id="2345c-146">Kanallar bağlamalar ve bağlama öğeleri aracılığıyla WCF'ye maruz kalır.</span><span class="sxs-lookup"><span data-stu-id="2345c-146">Channels are exposed to WCF through bindings and binding elements.</span></span> <span data-ttu-id="2345c-147">Bağlama bir veya birkaç bağlama öğesinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="2345c-147">A binding consists of one or many binding elements.</span></span> <span data-ttu-id="2345c-148">WCF çeşitli sistem tanımlı bağlamalar sunar; örneğin, Temel HttpBinding veya WSHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="2345c-148">WCF offers several system-defined bindings; for example, BasicHttpBinding or WSHttpBinding.</span></span> <span data-ttu-id="2345c-149">Sınıf `HttpCookieSessionBindingElement` bağlama öğesi için uygulama içerir.</span><span class="sxs-lookup"><span data-stu-id="2345c-149">The `HttpCookieSessionBindingElement` class contains the implementation for the binding element.</span></span> <span data-ttu-id="2345c-150">Gerekli kanal dinleyicisi veya kanal fabrika anlık yapmak için kanal dinleyicive kanal fabrika oluşturma yöntemleri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="2345c-150">It overrides the channel listener and channel factory creation methods to do the necessary channel listener or channel factory instantiations.</span></span>  
  
 <span data-ttu-id="2345c-151">Örnek, hizmet açıklaması için ilke iddialarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="2345c-151">The sample uses policy assertions for the service description.</span></span> <span data-ttu-id="2345c-152">Bu, örnek kanalı gereksinimlerini hizmeti tüketebilecek diğer istemcilere yayımlamaolanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="2345c-152">This allows the sample to publish its channel requirements to other clients that can consume the service.</span></span> <span data-ttu-id="2345c-153">Örneğin, bu bağlayıcı öğe, olası istemcilere oturumları desteklediğini bildirmek için ilke iddiaları yayımlar.</span><span class="sxs-lookup"><span data-stu-id="2345c-153">For example, this binding element publishes policy assertions to let potential clients know that it supports sessions.</span></span> <span data-ttu-id="2345c-154">Örnek bağlama öğesi `ExchangeTerminateMessage` yapılandırmasında özelliği etkinleştirdiği için, hizmetoturum konuşma sona erdirmek için ek bir ileti alışverişi eylemi desteklediğini göstermek için gerekli iddiaları ekler.</span><span class="sxs-lookup"><span data-stu-id="2345c-154">Because the sample enables the `ExchangeTerminateMessage` property in the binding element configuration, it adds the necessary assertions to show that the service supports an extra message exchange action to terminate the session conversation.</span></span> <span data-ttu-id="2345c-155">İstemciler daha sonra bu eylemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2345c-155">Clients can then use this action.</span></span> <span data-ttu-id="2345c-156">Aşağıdaki WSDL kodu, `HttpCookieSessionBindingElement`.'dan oluşturulan ilke iddialarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2345c-156">The following WSDL code shows the policy assertions created from the `HttpCookieSessionBindingElement`.</span></span>  
  
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
  
 <span data-ttu-id="2345c-157">Sınıf, `HttpCookieSessionBinding` daha önce açıklanan bağlama öğesini kullanan bir sistem sağlanan bağlamadır.</span><span class="sxs-lookup"><span data-stu-id="2345c-157">The `HttpCookieSessionBinding` class is a system-provided binding that uses the binding element described previously.</span></span>  
  
## <a name="adding-the-channel-to-the-configuration-system"></a><span data-ttu-id="2345c-158">Yapılandırma Sistemine Kanal Ekleme</span><span class="sxs-lookup"><span data-stu-id="2345c-158">Adding the Channel to the Configuration System</span></span>  
 <span data-ttu-id="2345c-159">Örnek, yapılandırma yoluyla örnek kanalı ortaya çıkaran iki sınıf sağlar.</span><span class="sxs-lookup"><span data-stu-id="2345c-159">The sample provides two classes that expose the sample channel through configuration.</span></span> <span data-ttu-id="2345c-160">İlki için <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> `HttpCookieSessionBindingElement`bir.</span><span class="sxs-lookup"><span data-stu-id="2345c-160">The first is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> for the `HttpCookieSessionBindingElement`.</span></span> <span data-ttu-id="2345c-161">Uygulamanın büyük bir kısmı `HttpCookieSessionBindingConfigurationElement`, ' den <xref:System.ServiceModel.Configuration.StandardBindingElement>türetilen .</span><span class="sxs-lookup"><span data-stu-id="2345c-161">The bulk of the implementation is delegated to the `HttpCookieSessionBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="2345c-162">Üzerinde `HttpCookieSessionBindingConfigurationElement` özellikleri karşılık gelen özelliklere `HttpCookieSessionBindingElement`sahiptir.</span><span class="sxs-lookup"><span data-stu-id="2345c-162">The `HttpCookieSessionBindingConfigurationElement` has properties that correspond to the properties on `HttpCookieSessionBindingElement`.</span></span>  
  
### <a name="binding-element-extension-section"></a><span data-ttu-id="2345c-163">Bağlama Elemanı Uzatma Bölümü</span><span class="sxs-lookup"><span data-stu-id="2345c-163">Binding Element Extension Section</span></span>  
 <span data-ttu-id="2345c-164">Bölüm, `HttpCookieSessionBindingElementSection` yapılandırma <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> sistemine `HttpCookieSessionBindingElement` maruz kalan bir bölümdür.</span><span class="sxs-lookup"><span data-stu-id="2345c-164">The section `HttpCookieSessionBindingElementSection` is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> that exposes `HttpCookieSessionBindingElement` to the configuration system.</span></span> <span data-ttu-id="2345c-165">Yapılandırma bölüm adını birkaç geçersiz kılar, bağlama öğesinin türü ve bağlama öğesi oluşturmak için nasıl tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="2345c-165">With a few overrides the configuration section name, the type of the binding element and how to create the binding element are defined.</span></span> <span data-ttu-id="2345c-166">Daha sonra uzantı bölümünü bir yapılandırma dosyasına aşağıdaki gibi kaydedebiliriz:</span><span class="sxs-lookup"><span data-stu-id="2345c-166">We can then register the extension section in a configuration file as follows:</span></span>  
  
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
  
## <a name="test-code"></a><span data-ttu-id="2345c-167">Test Kodu</span><span class="sxs-lookup"><span data-stu-id="2345c-167">Test Code</span></span>  
 <span data-ttu-id="2345c-168">Bu örnek aktarımı kullanmak için test kodu İstemci ve Hizmet dizinlerinde mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="2345c-168">Test code for using this sample transport is available in the Client and Service directories.</span></span> <span data-ttu-id="2345c-169">İki testten oluşur- bir test `allowCookies` istemciye `true` ayarlanmış bir bağlama kullanır.</span><span class="sxs-lookup"><span data-stu-id="2345c-169">It consists of two tests—one test uses a binding with `allowCookies` set to `true` on the client.</span></span> <span data-ttu-id="2345c-170">İkinci sınama, bağlamada açık kapatmayı (sonlandırma iletisi değişimini kullanarak) sağlar.</span><span class="sxs-lookup"><span data-stu-id="2345c-170">The second test enables explicit shutdown (using the terminate message exchange) on the binding.</span></span>  
  
 <span data-ttu-id="2345c-171">Örneği çalıştırdığınızda, aşağıdaki çıktıyı görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="2345c-171">When you run the sample, you should see the following output:</span></span>  
  
```console  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2345c-172">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="2345c-172">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="2345c-173">Aşağıdaki komutu kullanarak 4.0 ASP.NET yükleyin.</span><span class="sxs-lookup"><span data-stu-id="2345c-173">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="2345c-174">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="2345c-174">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="2345c-175">Çözümü oluşturmak için, Windows [Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="2345c-175">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="2345c-176">Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="2345c-176">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
