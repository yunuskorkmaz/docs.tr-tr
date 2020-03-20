---
title: WCF Sorun Giderme Hızlı Başlangıç
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], troubleshooting
- Windows Communication Foundation [WCF], troubleshooting
ms.assetid: a9ea7a53-f31a-46eb-806e-898e465a4992
ms.openlocfilehash: f85d37fde19767d7fd1e3002776b4816666cc7e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183049"
---
# <a name="wcf-troubleshooting-quickstart"></a><span data-ttu-id="34550-102">WCF Sorun Giderme Hızlı Başlangıç</span><span class="sxs-lookup"><span data-stu-id="34550-102">WCF Troubleshooting Quickstart</span></span>
<span data-ttu-id="34550-103">Bu konu, müşterilerin WCF istemcileri ve hizmetleri geliştirirken karşılaştıkları bilinen bir dizi sorunu listeler.</span><span class="sxs-lookup"><span data-stu-id="34550-103">This topic lists a number of known issues customers have run into while developing WCF clients and services.</span></span> <span data-ttu-id="34550-104">Üzerinde durmaktadırsorun bu listede değilse, hizmetiniz için izleme yapılandırmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="34550-104">If the issue you are running into is not in this list, we recommend you configure tracing for your service.</span></span> <span data-ttu-id="34550-105">Bu, izleme dosyası görüntüleyicisiyle görüntüleyebileceğiniz bir izleme dosyası oluşturur ve hizmet içinde oluşabilecek özel durumlar hakkında ayrıntılı bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="34550-105">This will generate a trace file that you can view with the trace file viewer and get detailed information about exceptions that may be occurring within the service.</span></span> <span data-ttu-id="34550-106">İzlemeyi yapılandırma hakkında daha fazla bilgi için bkz: [İzlemeyi yapılandırma.](./diagnostics/tracing/configuring-tracing.md)</span><span class="sxs-lookup"><span data-stu-id="34550-106">For more information on configuring tracing, see: [Configuring Tracing](./diagnostics/tracing/configuring-tracing.md).</span></span> <span data-ttu-id="34550-107">İzleme dosyası görüntüleyici hakkında daha fazla bilgi için bkz: [Service Trace Viewer Tool (SvcTraceViewer.exe)](service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="34550-107">For more information on the trace file viewer, see: [Service Trace Viewer Tool (SvcTraceViewer.exe)](service-trace-viewer-tool-svctraceviewer-exe.md).</span></span>  
  
1. [<span data-ttu-id="34550-108">Windows 7 ve IIS'yi yükledikten sonra, bir WCF hizmetine göz atmaya çalışırken aşağıdaki hata iletisini alıyorum: HTTP Hatası 404.3 – Bulunamadı</span><span class="sxs-lookup"><span data-stu-id="34550-108">After installing Windows 7 and IIS, when I attempt to browse to a WCF service I get the following error message: HTTP Error 404.3 – Not Found</span></span>](#bkmk_0)  
  
     <span data-ttu-id="34550-109">HTTP Hata 404.3 – Bulunamadı İstediğiniz sayfa uzantı yapılandırması nedeniyle servis edilemez.</span><span class="sxs-lookup"><span data-stu-id="34550-109">HTTP Error 404.3 – Not FoundThe page you are requesting cannot be served because of the extension configuration.</span></span> <span data-ttu-id="34550-110">Sayfa bir komut dosyasıysa, bir işleyici ekleyin.</span><span class="sxs-lookup"><span data-stu-id="34550-110">If the page is a script, add a handler.</span></span> <span data-ttu-id="34550-111">Dosya indirilecekse, bir MIME eşlemi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="34550-111">If the file should be downloaded, add a MIME map.</span></span> <span data-ttu-id="34550-112">Detaylı Hata Bilgisi Modülü StaticFileModule.</span><span class="sxs-lookup"><span data-stu-id="34550-112">Detailed Error InformationModule StaticFileModule.</span></span>  
  
2. [<span data-ttu-id="34550-113">Bazen müşterim ilk istekten sonra bir süre boşta ise ikinci istek üzerine bir MessageSecurityException alırsınız. Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="34550-113">Sometimes I receive a MessageSecurityException on the second request if my client is idle for a while after the first request. What is happening?</span></span>](#BKMK_q1)  
  
3. [<span data-ttu-id="34550-114">Hizmetim, yaklaşık 10 istemci yle etkileşime geçtikten sonra yeni istemcileri reddetmeye başlar. Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="34550-114">My service starts to reject new clients after about 10 clients are interacting with it. What is happening?</span></span>](#BKMK_q2)  
  
4. [<span data-ttu-id="34550-115">Hizmet yapılandırmamı WCF uygulamasının yapılandırma dosyası dışında bir yerden yükleyebilir miyim?</span><span class="sxs-lookup"><span data-stu-id="34550-115">Can I load my service configuration from somewhere other than the WCF application’s configuration file?</span></span>](#BKMK_q3)  
  
5. [<span data-ttu-id="34550-116">Hizmetim ve istemcim harika çalışıyor, ancak istemci başka bir bilgisayarda yken onları çalıştıramıyorum? Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="34550-116">My service and client work great, but I can’t get them to work when the client is on another computer? What’s happening?</span></span>](#BKMK_q4)  
  
6. [<span data-ttu-id="34550-117">Tür özel durum\<> bir Hata Özel Durum atandığımda, her zaman istemci değil, genel türü genel bir Hata Özel Durum türü alırsınız. Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="34550-117">When I throw a FaultException\<Exception> where the type is an exception, I always receive a general FaultException type on the client and not the generic type. What’s happening?</span></span>](#BKMK_q5)  
  
7. [<span data-ttu-id="34550-118">Yanıt hiçbir veri içerdiğinde, tek yönlü ve istek yanıtlama işlemleri kabaca aynı hızda geri dönüyor gibi görünüyor. Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="34550-118">It seems like one-way and request-reply operations return at roughly the same speed when the reply contains no data. What's happening?</span></span>](#BKMK_q6)  
  
8. [<span data-ttu-id="34550-119">Hizmetimde X.509 sertifikası kullanıyorum ve System.Security.Cryptography.CryptographicException alıyorum. Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="34550-119">I’m using an X.509 certificate with my service and I get a System.Security.Cryptography.CryptographicException. What’s happening?</span></span>](#BKMK_q77)  
  
9. [<span data-ttu-id="34550-120">Bir işlemin ilk parametresini büyük harften küçük harfe değiştirdim; Şimdi müvekkilim bir istisna atıyor. Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="34550-120">I changed the first parameter of an operation from uppercase to lowercase; now my client throws an exception. What's happening?</span></span>](#BKMK_q88)  
  
10. [<span data-ttu-id="34550-121">Benim izleme araçlarından birini kullanıyorum ve bir EndpointNotFoundException olsun. Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="34550-121">I’m using one of my tracing tools and I get an EndpointNotFoundException. What’s happening?</span></span>](#BKMK_q99)  
  
11. [<span data-ttu-id="34550-122">WCF SOAP uygulamasından WCF Web HTTP uygulamasını ararken hizmet aşağıdaki hatayı döndürür: 405 Yöntem İzin Verilmez</span><span class="sxs-lookup"><span data-stu-id="34550-122">When calling a WCF Web HTTP application from a WCF SOAP application the service returns the following error: 405 Method Not Allowed</span></span>](#BK_MK99)  
  
 [<span data-ttu-id="34550-123">Temel adres nedir? Bitiş noktası adresiyle ne ilgisi var?</span><span class="sxs-lookup"><span data-stu-id="34550-123">What is the base address? How does it relate to an endpoint address?</span></span>](#BKMK_q10)  
  
<a name="bkmk_0"></a>
## <a name="after-installing-windows-7-and-iis-when-i-attempt-to-browse-to-a-wcf-service-i-get-the-following-error-message-http-error-4043--not-found"></a><span data-ttu-id="34550-124">Windows 7 ve IIS'yi yükledikten sonra, bir WCF hizmetine göz atmaya çalışırken aşağıdaki hata iletisini alıyorum: HTTP Hatası 404.3 – Bulunamadı</span><span class="sxs-lookup"><span data-stu-id="34550-124">After installing Windows 7 and IIS, when I attempt to browse to a WCF service I get the following error message: HTTP Error 404.3 – Not Found</span></span>  
 <span data-ttu-id="34550-125">Tam hata iletisi:</span><span class="sxs-lookup"><span data-stu-id="34550-125">The full error message is:</span></span>  
  
 <span data-ttu-id="34550-126">HTTP Hata 404.3 – Bulunamadı İstediğiniz sayfa uzantı yapılandırması nedeniyle servis edilemez.</span><span class="sxs-lookup"><span data-stu-id="34550-126">HTTP Error 404.3 – Not FoundThe page you are requesting cannot be served because of the extension configuration.</span></span> <span data-ttu-id="34550-127">Sayfa bir komut dosyasıysa, bir işleyici ekleyin.</span><span class="sxs-lookup"><span data-stu-id="34550-127">If the page is a script, add a handler.</span></span> <span data-ttu-id="34550-128">Dosya indirilecekse, bir MIME eşlemi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="34550-128">If the file should be downloaded, add a MIME map.</span></span> <span data-ttu-id="34550-129">Detaylı Hata Bilgisi Modülü StaticFileModule.</span><span class="sxs-lookup"><span data-stu-id="34550-129">Detailed Error InformationModule StaticFileModule.</span></span>  
  
 <span data-ttu-id="34550-130">Bu hata iletisi, "Windows Communication Foundation HTTP Etkinleştirme" Denetim Masası'nda açıkça ayarlanmadığında oluşur.</span><span class="sxs-lookup"><span data-stu-id="34550-130">This error message occurs when "Windows Communication Foundation HTTP Activation" is not explicitly set in the Control Panel.</span></span> <span data-ttu-id="34550-131">Bunu Denetim Masası'na ayarlamak için pencerenin sol alt köşesindeki Programlar'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="34550-131">To set this go to the Control Panel, click Programs in the lower left-hand corner of the window.</span></span> <span data-ttu-id="34550-132">Windows özelliklerini aç veya kapat'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="34550-132">Click Turn Windows features on or off.</span></span> <span data-ttu-id="34550-133">Microsoft .NET Framework 3.5.1'i genişletin ve Windows Communication Foundation HTTP Etkinleştirme'yi seçin.</span><span class="sxs-lookup"><span data-stu-id="34550-133">Expand Microsoft .NET Framework 3.5.1 and select Windows Communication Foundation HTTP Activation.</span></span>  
  
<a name="BKMK_q1"></a>
## <a name="sometimes-i-receive-a-messagesecurityexception-on-the-second-request-if-my-client-is-idle-for-a-while-after-the-first-request-what-is-happening"></a><span data-ttu-id="34550-134">Bazen müşterim ilk istekten sonra bir süre boşta ise ikinci istek üzerine bir MessageSecurityException alırsınız.</span><span class="sxs-lookup"><span data-stu-id="34550-134">Sometimes I receive a MessageSecurityException on the second request if my client is idle for a while after the first request.</span></span> <span data-ttu-id="34550-135">Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="34550-135">What is happening?</span></span>  
 <span data-ttu-id="34550-136">İkinci istek öncelikle iki nedenden dolayı başarısız olabilir: (1) oturum zamanlanmış veya (2) hizmeti barındıran Web sunucusu geri dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="34550-136">The second request can fail primarily for two reasons: (1) the session has timed out or (2) the Web server that is hosting the service is recycled.</span></span> <span data-ttu-id="34550-137">İlk durumda, oturum hizmet saatleri bitene kadar geçerlidir. Hizmet, hizmetin bağlayıcısında belirtilen süre içinde istemciden bir istek almadığı<xref:System.ServiceModel.Channels.Binding.ReceiveTimeout%2A>nda ( ), hizmet güvenlik oturumunu sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="34550-137">In the first case, the session is valid until the service times out. When the service does not receive a request from the client within the period of time specified in the service's binding (<xref:System.ServiceModel.Channels.Binding.ReceiveTimeout%2A>), the service terminates the security session.</span></span> <span data-ttu-id="34550-138">Sonraki istemci iletileri <xref:System.ServiceModel.Security.MessageSecurityException>.</span><span class="sxs-lookup"><span data-stu-id="34550-138">Subsequent client messages result in the <xref:System.ServiceModel.Security.MessageSecurityException>.</span></span> <span data-ttu-id="34550-139">İstemci, gelecekteki iletileri göndermek veya durum salkınlı bir güvenlik bağlamı belirteci kullanmak için hizmetle güvenli bir oturum oluşturmalı.</span><span class="sxs-lookup"><span data-stu-id="34550-139">The client must re-establish a secure session with the service to send future messages or use a stateful security context token.</span></span> <span data-ttu-id="34550-140">Durumsal güvenlik bağlam belirteçleri, güvenli bir oturumun geri dönüştürülen bir Web sunucusundan hayatta kalmasına da olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="34550-140">Stateful security context tokens also allow a secure session to survive a Web server being recycled.</span></span> <span data-ttu-id="34550-141">Güvenli bir oturumda durum bilgisine uygun güvenli bağlam belirteçleri kullanma hakkında daha fazla bilgi için [bkz.](./feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)</span><span class="sxs-lookup"><span data-stu-id="34550-141">For more information about using stateful secure context tokens in a secure session, see [How to: Create a Security Context Token for a Secure Session](./feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span></span> <span data-ttu-id="34550-142">Alternatif olarak, güvenli oturumları devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="34550-142">Alternatively, you can disable secure sessions.</span></span> <span data-ttu-id="34550-143">wsHttpBinding>bağlamayı kullandığınızda, `establishSecurityContext` özelliği güvenli `false` oturumları devre dışı bırakacak şekilde ayarlayabilirsiniz. [ \<](../configure-apps/file-schema/wcf/wshttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="34550-143">When you use the [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) binding, you can set the `establishSecurityContext` property to `false` to disable secure sessions.</span></span> <span data-ttu-id="34550-144">Diğer bağlamalar için güvenli oturumları devre dışı bırakabilmek için özel bir bağlama oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="34550-144">To disable secure sessions for other bindings, you must create a custom binding.</span></span> <span data-ttu-id="34550-145">Özel bir bağlama oluşturma yla ilgili ayrıntılar için [bkz: SecurityBindingElement'i kullanarak Özel Bağlama Oluşturma.](./feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)</span><span class="sxs-lookup"><span data-stu-id="34550-145">For details about creating a custom binding, see [How to: Create a Custom Binding Using the SecurityBindingElement](./feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span> <span data-ttu-id="34550-146">Bu seçeneklerden herhangi birini uygulamadan önce, uygulamanızın güvenlik gereksinimlerini anlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="34550-146">Before you apply any of these options, you must understand your application's security requirements.</span></span>  
  
<a name="BKMK_q2"></a>
## <a name="my-service-starts-to-reject-new-clients-after-about-10-clients-are-interacting-with-it-what-is-happening"></a><span data-ttu-id="34550-147">Hizmetim, yaklaşık 10 istemci yle etkileşime geçtikten sonra yeni istemcileri reddetmeye başlar.</span><span class="sxs-lookup"><span data-stu-id="34550-147">My service starts to reject new clients after about 10 clients are interacting with it.</span></span> <span data-ttu-id="34550-148">Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="34550-148">What is happening?</span></span>  
 <span data-ttu-id="34550-149">Varsayılan olarak, hizmetlerin yalnızca 10 eşzamanlı oturumu olabilir.</span><span class="sxs-lookup"><span data-stu-id="34550-149">By default, services can have only 10 concurrent sessions.</span></span> <span data-ttu-id="34550-150">Bu nedenle, hizmet oturumları kullanırsa, hizmet bu sayıya ulaşana kadar yeni istemci bağlantılarını kabul eder ve ardından geçerli oturumlardan biri sona erene kadar yeni istemci bağlantılarını reddeder.</span><span class="sxs-lookup"><span data-stu-id="34550-150">Therefore, if the service bindings use sessions, the service accepts new client connections until it reaches that number, after which it refuses new client connections until one of the current sessions ends.</span></span> <span data-ttu-id="34550-151">Daha fazla istemciyi çeşitli yollarla destekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="34550-151">You can support more clients in a number of ways.</span></span> <span data-ttu-id="34550-152">Hizmetiniz oturum gerektirmiyorsa, oturumlu bir bağlama kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="34550-152">If your service does not require sessions, do not use a sessionful binding.</span></span> <span data-ttu-id="34550-153">(Daha fazla bilgi için [bkz.](using-sessions.md) Başka bir seçenek, <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A> özelliğin değerini durumunuza uygun sayıyla değiştirerek oturum sınırını artırmaktır.</span><span class="sxs-lookup"><span data-stu-id="34550-153">(For more information, see [Using Sessions](using-sessions.md).) Another option is to increase the session limit by changing the value of the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A> property to the number appropriate to your circumstance.</span></span>  
  
<a name="BKMK_q3"></a>
## <a name="can-i-load-my-service-configuration-from-somewhere-other-than-the-wcf-applications-configuration-file"></a><span data-ttu-id="34550-154">Hizmet yapılandırmamı WCF uygulamasının yapılandırma dosyası dışında bir yerden yükleyebilir miyim?</span><span class="sxs-lookup"><span data-stu-id="34550-154">Can I load my service configuration from somewhere other than the WCF application’s configuration file?</span></span>  
 <span data-ttu-id="34550-155">Evet, ancak, <xref:System.ServiceModel.ServiceHost> <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> yöntemi geçersiz kılan özel bir sınıf oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="34550-155">Yes, however, you have to create a custom <xref:System.ServiceModel.ServiceHost> class that overrides the <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> method.</span></span> <span data-ttu-id="34550-156">Bu yöntemin içinde, önce yapılandırmayı yüklemek için tabanı arayabilirsiniz (standart yapılandırma bilgilerini de yüklemek istiyorsanız) ancak yapılandırma yükleme sistemini tamamen değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="34550-156">Inside that method, you can call the base to load configuration first (if you want to load the standard configuration information as well) but you can also entirely replace the configuration loading system.</span></span> <span data-ttu-id="34550-157">Yapılandırmayı uygulama yapılandırma dosyasından farklı bir yapılandırma dosyasından yüklemek istiyorsanız, yapılandırma dosyasını kendiniz ayrıştırmalı ve yapılandırmayı yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="34550-157">If you want to load configuration from a configuration file that is different from the application configuration file, you must parse the configuration file yourself and load the configuration.</span></span>  
  
 <span data-ttu-id="34550-158">Aşağıdaki kod örneği, yöntemi nasıl <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> geçersiz kılınan ve bir bitiş noktasının doğrudan nasıl yapılandırılabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="34550-158">The following code example shows how to override the <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> method and directly configure an endpoint.</span></span>  
  
```csharp
public class MyServiceHost : ServiceHost  
{  
    public MyServiceHost(Type serviceType, params Uri[] baseAddresses)
      : base(serviceType, baseAddresses)  
    {
        Console.WriteLine("MyServiceHost Constructor");
    }  
  
    protected override void ApplyConfiguration()  
    {  
        string straddress = GetAddress();  
        Uri address = new Uri(straddress);  
        Binding binding = GetBinding();  
        base.AddServiceEndpoint(typeof(IData), binding, address);  
    }  
  
    string GetAddress()  
    {
        return "http://MyMachine:7777/MyEndpointAddress/";
    }  
  
    Binding GetBinding()  
    {  
        WSHttpBinding binding = new WSHttpBinding();  
        binding.Security.Mode = SecurityMode.None;  
        return binding;  
    }  
}  
```  
  
<a name="BKMK_q4"></a>
## <a name="my-service-and-client-work-great-but-i-cant-get-them-to-work-when-the-client-is-on-another-computer-whats-happening"></a><span data-ttu-id="34550-159">Hizmetim ve istemcim harika çalışıyor, ancak istemci başka bir bilgisayarda yken onları çalıştıramıyorum?</span><span class="sxs-lookup"><span data-stu-id="34550-159">My service and client work great, but I can’t get them to work when the client is on another computer?</span></span> <span data-ttu-id="34550-160">Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="34550-160">What’s happening?</span></span>  
 <span data-ttu-id="34550-161">Özel duruma bağlı olarak, çeşitli sorunlar olabilir:</span><span class="sxs-lookup"><span data-stu-id="34550-161">Depending upon the exception, there may be several issues:</span></span>  
  
- <span data-ttu-id="34550-162">İstemci bitiş noktası adreslerini "localhost" değil, ana bilgisayar adı olarak değiştirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="34550-162">You might need to change the client endpoint addresses to the host name and not "localhost".</span></span>  
  
- <span data-ttu-id="34550-163">Bağlantı noktasını uygulamaya açmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="34550-163">You might need to open the port to the application.</span></span> <span data-ttu-id="34550-164">Ayrıntılar için, SDK örneklerinden [Güvenlik Duvarı Yönergeleri'ne](./samples/firewall-instructions.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="34550-164">For details, see [Firewall Instructions](./samples/firewall-instructions.md) from the SDK samples.</span></span>  
  
- <span data-ttu-id="34550-165">Diğer olası sorunlar için, [Windows Communication Foundation Samples'ı çalıştıran](./samples/running-the-samples.md)örnekler konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="34550-165">For other possible issues, see the samples topic [Running the Windows Communication Foundation Samples](./samples/running-the-samples.md).</span></span>  
  
- <span data-ttu-id="34550-166">İstemciniz Windows kimlik bilgilerini kullanıyorsa ve özel durum kerberos'u <xref:System.ServiceModel.Security.SecurityNegotiationException>aşağıdaki gibi yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="34550-166">If your client is using Windows credentials and the exception is a <xref:System.ServiceModel.Security.SecurityNegotiationException>, configure Kerberos as follows.</span></span>  
  
    1. <span data-ttu-id="34550-167">Kimlik bilgilerini istemcinin App.config dosyasındaki bitiş noktası öğesine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="34550-167">Add the identity credentials to the endpoint element in the client’s App.config file:</span></span>  
  
        ```xml
        <endpoint
          address="http://MyServer:8000/MyService/"
          binding="wsHttpBinding"
          bindingConfiguration="WSHttpBinding_IServiceExample"
          contract="IServiceExample"
          behaviorConfiguration="ClientCredBehavior"
          name="WSHttpBinding_IServiceExample">  
          <identity>  
            <userPrincipalName value="name@corp.contoso.com"/>  
          </identity>  
        </endpoint>  
        ```  
  
    2. <span data-ttu-id="34550-168">Sistem veya NetworkService hesabı altında kendi kendine barındırılan hizmeti çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="34550-168">Run the self-hosted service under the System or NetworkService account.</span></span> <span data-ttu-id="34550-169">Sistem hesabının altında bir komut penceresi oluşturmak için bu komutu çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="34550-169">You can run this command to create a command window under the System account:</span></span>  
  
        ```console
        at 12:36 /interactive "cmd.exe"  
        ```  
  
    3. <span data-ttu-id="34550-170">Hizmeti, varsayılan olarak hizmet ana adı (SPN) hesabını kullanan Internet Information Services (IIS) altında barındırın.</span><span class="sxs-lookup"><span data-stu-id="34550-170">Host the service under Internet Information Services (IIS), which, by default, uses the service principal name (SPN) account.</span></span>  
  
    4. <span data-ttu-id="34550-171">SetSPN kullanarak etki alanına yeni bir SPN kaydedin.</span><span class="sxs-lookup"><span data-stu-id="34550-171">Register a new SPN with the domain using SetSPN.</span></span> <span data-ttu-id="34550-172">Bunu yapmak için bir etki alanı yöneticisi olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="34550-172">You need to be a domain administrator in order to do this.</span></span>  
  
 <span data-ttu-id="34550-173">Kerberos protokolü hakkında daha fazla bilgi için [WCF'de Kullanılan Güvenlik Kavramları'na](./feature-details/security-concepts-used-in-wcf.md) bakın ve:</span><span class="sxs-lookup"><span data-stu-id="34550-173">For more information about the Kerberos protocol, see [Security Concepts Used in WCF](./feature-details/security-concepts-used-in-wcf.md) and:</span></span>  
  
- [<span data-ttu-id="34550-174">Windows Kimlik Doğrulama Hatalarını Ayıklama</span><span class="sxs-lookup"><span data-stu-id="34550-174">Debugging Windows Authentication Errors</span></span>](./feature-details/debugging-windows-authentication-errors.md)  
  
- <span data-ttu-id="34550-175">[Http.sys kullanarak Kerberos Hizmet Müdür Adları Kayıt](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms178119(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="34550-175">[Registering Kerberos Service Principal Names by Using Http.sys](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms178119(v=sql.105))</span></span>  
  
- <span data-ttu-id="34550-176">[Kerberos Açıklaması](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-2000-server/bb742516(v%3dtechnet.10))</span><span class="sxs-lookup"><span data-stu-id="34550-176">[Kerberos Explained](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-2000-server/bb742516(v%3dtechnet.10))</span></span>  
  
<a name="BKMK_q5"></a>
## <a name="when-i-throw-a-faultexceptionexception-where-the-type-is-an-exception-i-always-receive-a-general-faultexception-type-on-the-client-and-not-the-generic-type-whats-happening"></a><span data-ttu-id="34550-177">Tür özel durum\<> bir Hata Özel Durum atandığımda, her zaman istemci değil, genel türü genel bir Hata Özel Durum türü alırsınız.</span><span class="sxs-lookup"><span data-stu-id="34550-177">When I throw a FaultException\<Exception> where the type is an exception, I always receive a general FaultException type on the client and not the generic type.</span></span> <span data-ttu-id="34550-178">Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="34550-178">What’s happening?</span></span>  
 <span data-ttu-id="34550-179">Kendi özel hata veri türünü oluşturmanız ve hata sözleşmenizdeki ayrıntı türü olarak bunu beyan etmeniz önerilir.</span><span class="sxs-lookup"><span data-stu-id="34550-179">It is highly recommended that you create your own custom error data type and declare that as the detail type in your fault contract.</span></span> <span data-ttu-id="34550-180">Bunun nedeni, sistem tarafından sağlanan özel durum türlerini kullanarak:</span><span class="sxs-lookup"><span data-stu-id="34550-180">The reason is that using system-provided exception types:</span></span>  
  
- <span data-ttu-id="34550-181">Hizmet yönelimli uygulamaların en büyük güçlü yanlarından birini kaldıran bir tür bağımlılık oluşturur.</span><span class="sxs-lookup"><span data-stu-id="34550-181">Creates a type dependency that removes one of the biggest strengths of service-oriented applications.</span></span>  
  
- <span data-ttu-id="34550-182">Standart bir şekilde seri hale getirme özel durumlara bağlı olamaz.</span><span class="sxs-lookup"><span data-stu-id="34550-182">Cannot depend upon exceptions serializing in a standard way.</span></span> <span data-ttu-id="34550-183">Bazı-gibi <xref:System.Security.SecurityException>—hiç serializable olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="34550-183">Some—like <xref:System.Security.SecurityException>—may not be serializable at all.</span></span>  
  
- <span data-ttu-id="34550-184">Dahili uygulama ayrıntılarını istemcilere karşı ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="34550-184">Exposes internal implementation details to clients.</span></span> <span data-ttu-id="34550-185">Daha fazla bilgi için [bkz.](specifying-and-handling-faults-in-contracts-and-services.md)</span><span class="sxs-lookup"><span data-stu-id="34550-185">For more information, see [Specifying and Handling Faults in Contracts and Services](specifying-and-handling-faults-in-contracts-and-services.md).</span></span>  
  
 <span data-ttu-id="34550-186">Ancak, bir uygulamayı hata ayıklıyorsanız, özel durum bilgilerini serihale getirebilir ve <xref:System.ServiceModel.Description.ServiceDebugBehavior> sınıfı kullanarak istemciye döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="34550-186">If you are debugging an application, however, you can serialize exception information and return it to the client by using the <xref:System.ServiceModel.Description.ServiceDebugBehavior> class.</span></span>  
  
<a name="BKMK_q6"></a>
## <a name="it-seems-like-one-way-and-request-reply-operations-return-at-roughly-the-same-speed-when-the-reply-contains-no-data-whats-happening"></a><span data-ttu-id="34550-187">Yanıt hiçbir veri içerdiğinde, tek yönlü ve istek yanıtlama işlemleri kabaca aynı hızda geri dönüyor gibi görünüyor.</span><span class="sxs-lookup"><span data-stu-id="34550-187">It seems like one-way and request-reply operations return at roughly the same speed when the reply contains no data.</span></span> <span data-ttu-id="34550-188">Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="34550-188">What's happening?</span></span>  
 <span data-ttu-id="34550-189">Bir işlemin tek bir yol olduğunu belirtmek, yalnızca işlem sözleşmesinin bir giriş iletisi kabul ettiği ve çıktı iletisi döndürmemesi anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="34550-189">Specifying that an operation is one way means only that the operation contract accepts an input message and does not return an output message.</span></span> <span data-ttu-id="34550-190">WCF'de, giden veriler kabloya yazıldığında veya bir özel durum atıldığında tüm istemci çağrıları geri döner.</span><span class="sxs-lookup"><span data-stu-id="34550-190">In WCF, all client invocations return when the outbound data has been written to the wire or an exception is thrown.</span></span> <span data-ttu-id="34550-191">Tek yönlü işlemler aynı şekilde çalışır ve hizmet inanın ağından verileri kabul etmeye hazır değilse, hizmet bulunamıyorsa veya engellenemezse atabilirler.</span><span class="sxs-lookup"><span data-stu-id="34550-191">One-way operations work the same way, and they can throw if the service cannot be located or block if the service is not prepared to accept the data from the network.</span></span> <span data-ttu-id="34550-192">Genellikle WCF'de, bu durum istemciye istek-yanıttan daha hızlı dönen tek yönlü aramalarla sonuçlanır; ancak giden verilerin ağ üzerinden gönderilmesini yavaşlatan herhangi bir koşul, tek yönlü işlemlerin yanı sıra istek yanıtlama işlemlerini de yavaşlatıyor.</span><span class="sxs-lookup"><span data-stu-id="34550-192">Typically in WCF, this results in one-way calls returning to the client more quickly than request-reply; but any condition that slows the sending of the outbound data over the network slows one-way operations as well as request-reply operations.</span></span> <span data-ttu-id="34550-193">Daha fazla bilgi için [WCF İstemci Kullanarak](./feature-details/accessing-services-using-a-client.md) [Tek Yönlü Hizmetler](./feature-details/one-way-services.md) ve Hizmetlere Erişim'e bakın.</span><span class="sxs-lookup"><span data-stu-id="34550-193">For more information, see [One-Way Services](./feature-details/one-way-services.md) and [Accessing Services Using a WCF Client](./feature-details/accessing-services-using-a-client.md).</span></span>  
  
<a name="BKMK_q77"></a>
## <a name="im-using-an-x509-certificate-with-my-service-and-i-get-a-systemsecuritycryptographycryptographicexception-whats-happening"></a><span data-ttu-id="34550-194">Hizmetimde X.509 sertifikası kullanıyorum ve System.Security.Cryptography.CryptographicException alıyorum.</span><span class="sxs-lookup"><span data-stu-id="34550-194">I’m using an X.509 certificate with my service and I get a System.Security.Cryptography.CryptographicException.</span></span> <span data-ttu-id="34550-195">Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="34550-195">What’s happening?</span></span>  
 <span data-ttu-id="34550-196">Bu genellikle IIS alt işleminin çalıştığı kullanıcı hesabını değiştirdikten sonra oluşur.</span><span class="sxs-lookup"><span data-stu-id="34550-196">This commonly occurs after changing the user account under which the IIS worker process runs.</span></span> <span data-ttu-id="34550-197">Örneğin, Windows XP'de Aspnet_wp.exe'nin altında çalıştığı varsayılan kullanıcı hesabını ASPNET'ten özel bir kullanıcı hesabına değiştirirseniz, bu hatayı görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="34550-197">For example, in Windows XP, if you change the default user account that the Aspnet_wp.exe runs under from ASPNET to a custom user account, you may see this error.</span></span> <span data-ttu-id="34550-198">Özel bir anahtar kullanıyorsanız, bu anahtarı depolayan dosyaya erişmek için izinlere sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="34550-198">If using a private key, the process that uses it will need to have permissions to access the file storing that key.</span></span>  
  
 <span data-ttu-id="34550-199">Bu durumda, özel anahtarı içeren dosya için işlemin hesabına okuma erişimi ayrıcalıkları vermeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="34550-199">If this is the case, you must give read access privileges to the process's account for the file containing the private key.</span></span> <span data-ttu-id="34550-200">Örneğin, IIS alt işlemi Bob hesabı altında çalışıyorsa, Bob'a özel anahtarı içeren dosyaya okuma erişimi vermeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="34550-200">For example, if the IIS worker process is running under the Bob account, then you will need to give Bob read access to the file containing the private key.</span></span>  
  
 <span data-ttu-id="34550-201">Belirli bir X.509 sertifikası için özel anahtarı içeren dosyaya doğru kullanıcı hesabına erişim innasıl verilebildiği hakkında daha fazla bilgi için [bkz.](./feature-details/how-to-make-x-509-certificates-accessible-to-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="34550-201">For more information about how to give the correct user account access to the file that contains the private key for a specific X.509 certificate, see [How to: Make X.509 Certificates Accessible to WCF](./feature-details/how-to-make-x-509-certificates-accessible-to-wcf.md).</span></span>  
  
<a name="BKMK_q88"></a>
## <a name="i-changed-the-first-parameter-of-an-operation-from-uppercase-to-lowercase-now-my-client-throws-an-exception-whats-happening"></a><span data-ttu-id="34550-202">Bir işlemin ilk parametresini büyük harften küçük harfe değiştirdim; Şimdi müvekkilim bir istisna atıyor.</span><span class="sxs-lookup"><span data-stu-id="34550-202">I changed the first parameter of an operation from uppercase to lowercase; now my client throws an exception.</span></span> <span data-ttu-id="34550-203">Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="34550-203">What's happening?</span></span>  
 <span data-ttu-id="34550-204">İşlem imzasındaki parametre adlarının değerleri sözleşmenin bir parçasıdır ve büyük/küçük harf duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="34550-204">The values of the parameter names in the operation signature are part of the contract and are case-sensitive.</span></span> <span data-ttu-id="34550-205"><xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType> Yerel parametre adı ile istemci uygulamaları için işlemi açıklayan meta verileri birbirinden ayırmanız gerektiğinde özniteliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="34550-205">Use the <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType> attribute when you need to distinguish between the local parameter name and the metadata that describes the operation for client applications.</span></span>  
  
<a name="BKMK_q99"></a>
## <a name="im-using-one-of-my-tracing-tools-and-i-get-an-endpointnotfoundexception-whats-happening"></a><span data-ttu-id="34550-206">Benim izleme araçlarından birini kullanıyorum ve bir EndpointNotFoundException olsun.</span><span class="sxs-lookup"><span data-stu-id="34550-206">I’m using one of my tracing tools and I get an EndpointNotFoundException.</span></span> <span data-ttu-id="34550-207">Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="34550-207">What’s happening?</span></span>  
 <span data-ttu-id="34550-208">Sistem tarafından sağlanan WCF izleme mekanizması olmayan bir izleme aracı kullanıyorsanız <xref:System.ServiceModel.EndpointNotFoundException> ve bir adres filtresi uyuşmazlığı olduğunu gösteren bir <xref:System.ServiceModel.Description.ClientViaBehavior> izleme aracı alırsanız, iletileri izleme yardımcı programına yönlendirmek için sınıfı kullanmanız ve yardımcı programın bu iletileri hizmet adresine yönlendirmesini sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="34550-208">If you are using a tracing tool that is not the system-provided WCF tracing mechanism and you receive an <xref:System.ServiceModel.EndpointNotFoundException> that indicates that there was an address filter mismatch, you need to use the <xref:System.ServiceModel.Description.ClientViaBehavior> class to direct the messages to the tracing utility and have the utility redirect those messages to the service address.</span></span> <span data-ttu-id="34550-209">Sınıf, <xref:System.ServiceModel.Description.ClientViaBehavior> adresüstle belirtilen bir sonraki ağ adresini nihai alıcıdan ayrı olarak belirtmek için `Via` adres üstbilgisini `To` değiştirir.</span><span class="sxs-lookup"><span data-stu-id="34550-209">The <xref:System.ServiceModel.Description.ClientViaBehavior> class alters the `Via` addressing header to specify the next network address separately from the ultimate receiver, indicated by the `To` addressing header.</span></span> <span data-ttu-id="34550-210">Ancak, bunu yaparken, değeri oluşturmak için kullanılan bitiş noktası `To` adresini değiştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="34550-210">When doing this, however, do not change the endpoint address, which is used to establish the `To` value.</span></span>  
  
 <span data-ttu-id="34550-211">Aşağıdaki kod örneği bir örnek istemci yapılandırma dosyasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="34550-211">The following code example shows an example client configuration file.</span></span>  
  
```xml
<endpoint
  address="http://localhost:8000/MyServer/"  
  binding="wsHttpBinding"  
  bindingConfiguration="WSHttpBinding_IMyContract"  
  behaviorConfiguration="MyClient"
  contract="IMyContract"
  name="WSHttpBinding_IMyContract">  
</endpoint>  
<behaviors>  
  <endpointBehaviors>  
    <behavior name="MyClient">  
      <clientVia viaUri="http://localhost:8001/MyServer/"/>  
    </behavior>  
  </endpointBehaviors>  
</behaviors>  
```  
  
<a name="BKMK_q10"></a>
## <a name="what-is-the-base-address-how-does-it-relate-to-an-endpoint-address"></a><span data-ttu-id="34550-212">Temel adres nedir?</span><span class="sxs-lookup"><span data-stu-id="34550-212">What is the base address?</span></span> <span data-ttu-id="34550-213">Bitiş noktası adresiyle ne ilgisi var?</span><span class="sxs-lookup"><span data-stu-id="34550-213">How does it relate to an endpoint address?</span></span>  
 <span data-ttu-id="34550-214">Temel adres, bir <xref:System.ServiceModel.ServiceHost> sınıfın kök adresidir.</span><span class="sxs-lookup"><span data-stu-id="34550-214">A base address is the root address for a <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="34550-215">Varsayılan olarak, hizmet <xref:System.ServiceModel.Description.ServiceMetadataBehavior> yapılandırmanıza bir sınıf eklerseniz, ana bilgisayar yayımları tüm uç noktalar için Web Hizmetleri Açıklama Dili (WSDL), http temel adresinden ve meta veri davranışına sağlanan göreli adreslerden artı "?wsdl" olarak alınır.</span><span class="sxs-lookup"><span data-stu-id="34550-215">By default, if you add a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class into your service configuration, the Web Services Description Language (WSDL) for all endpoints the host publishes are retrieved from the HTTP base address, plus any relative address provided to the metadata behavior, plus "?wsdl".</span></span> <span data-ttu-id="34550-216">ASP.NET ve IIS'yi biliyorsanız, temel adres sanal dizine eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="34550-216">If you are familiar with ASP.NET and IIS, the base address is equivalent to the virtual directory.</span></span>  
  
## <a name="sharing-a-port-between-a-service-endpoint-and-a-mex-endpoint-using-the-nettcpbinding"></a><span data-ttu-id="34550-217">NetTcpBinding kullanarak bir hizmet bitiş noktası ile mex bitiş noktası arasında bağlantı noktası paylaşımı</span><span class="sxs-lookup"><span data-stu-id="34550-217">Sharing a port between a service endpoint and a mex endpoint using the NetTcpBinding</span></span>  
 <span data-ttu-id="34550-218">Bir hizmetin temel adresini net.tcp://MyServer:8080/MyService olarak belirtir ve aşağıdaki uç noktaları eklerseniz:</span><span class="sxs-lookup"><span data-stu-id="34550-218">If you specify the base address for a service as net.tcp://MyServer:8080/MyService and add the following endpoints:</span></span>  
  
```xml  
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
 <span data-ttu-id="34550-219">NetTcpBinding ayarlarından birini aşağıdaki yapılandırma snippet'inde gösterildiği gibi değiştirirseniz:</span><span class="sxs-lookup"><span data-stu-id="34550-219">And if you modify one of the NetTcpBinding settings as shown in the following configuration snippet:</span></span>  
  
```xml  
<bindings>  
  <netTcpBinding>  
    <binding closeTimeout="00:01:00" openTimeout="00:01:00" receiveTimeout="00:10:00" sendTimeout="00:01:00" transactionFlow="false" transferMode="Buffered" transactionProtocol="OleTransactions" hostNameComparisonMode="StrongWildcard" listenBacklog="10" maxBufferPoolSize="524288" maxBufferSize="65536" maxConnections="11" maxReceivedMessageSize="65536">  
      <readerQuotas maxDepth="32" maxStringContentLength="8192" maxArrayLength="16384" maxBytesPerRead="4096" maxNameTableCharCount="16384"/>  
      <reliableSession ordered="true" inactivityTimeout="00:10:00" enabled="false"/>  
      <security mode="Transport">  
        <transport clientCredentialType="Windows" protectionLevel="EncryptAndSign"/>  
      </security>  
    </binding>  
  </netTcpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="34550-220">Aşağıdaki gibi bir hata göreceksiniz: İşlenmemiş Özel Durum: System.ServiceModel.AddressAlreadyInUseException: IP uç noktası 0.0.0.0:9000 üzerinde zaten bir dinleyici var farklı bir bağlantı noktası ile tam nitelikli bir URL belirterek bu hata nın üzerinde çalışabilirsiniz aşağıdaki yapılandırma snippet gösterildiği gibi MEX bitiş noktası:</span><span class="sxs-lookup"><span data-stu-id="34550-220">You will see an error like the following: Unhandled Exception: System.ServiceModel.AddressAlreadyInUseException: There is already a listener on IP endpoint 0.0.0.0:9000 You can work around this error by specifying a fully qualified URL with a different port for the MEX endpoint as shown in the following configuration snippet:</span></span>  
  
```xml
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="net.tcp://localhost:9001/servicemodelsamples/mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
<a name="BK_MK99"></a>
## <a name="when-calling-a-wcf-web-http-application-from-a-wcf-soap-application-the-service-returns-the-following-error-405-method-not-allowed"></a><span data-ttu-id="34550-221">WCF SOAP uygulamasından WCF Web HTTP uygulamasını ararken hizmet aşağıdaki hatayı döndürür: 405 Yöntem İzin Verilmez</span><span class="sxs-lookup"><span data-stu-id="34550-221">When calling a WCF Web HTTP application from a WCF SOAP application the service returns the following error: 405 Method Not Allowed</span></span>  
 <span data-ttu-id="34550-222">Bir WCF Web HTTP uygulamasını (wcf hizmetinden <xref:System.ServiceModel.WebHttpBinding> kullanan ve <xref:System.ServiceModel.Description.WebHttpBehavior>kullanan bir ``Unhandled Exception: System.ServiceModel.FaultException`1[System.ServiceModel.ExceptionDetail]: The remote server returned an unexpected response: (405) Method Not Allowed.`` hizmet) çağırmak aşağıdaki özel durumu oluşturabilir: Bu <xref:System.ServiceModel.OperationContext>özel durum, WCF'nin gelenlerle giden inin <xref:System.ServiceModel.OperationContext> üzerine yazması nedeniyle oluşur.</span><span class="sxs-lookup"><span data-stu-id="34550-222">Calling a WCF Web HTTP application (a service that uses the <xref:System.ServiceModel.WebHttpBinding> and <xref:System.ServiceModel.Description.WebHttpBehavior>) from a WCF service may generate the following exception: ``Unhandled Exception: System.ServiceModel.FaultException`1[System.ServiceModel.ExceptionDetail]: The remote server returned an unexpected response: (405) Method Not Allowed.`` This exception occurs because WCF overwrites the outgoing <xref:System.ServiceModel.OperationContext> with the incoming <xref:System.ServiceModel.OperationContext>.</span></span> <span data-ttu-id="34550-223">Bu sorunu çözmek için, WCF Web HTTP hizmet işlemi içinde bir <xref:System.ServiceModel.OperationContextScope> oluşturun.</span><span class="sxs-lookup"><span data-stu-id="34550-223">To solve this problem, create an <xref:System.ServiceModel.OperationContextScope> within the WCF Web HTTP service operation.</span></span> <span data-ttu-id="34550-224">Örnek:</span><span class="sxs-lookup"><span data-stu-id="34550-224">For example:</span></span>  
  
```csharp
public string Echo(string input)  
{  
    using (new OperationContextScope(this.InnerChannel))  
    {  
        return base.Channel.Echo(input);  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="34550-225">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34550-225">See also</span></span>

- [<span data-ttu-id="34550-226">Windows Kimlik Doğrulama Hatalarını Ayıklama</span><span class="sxs-lookup"><span data-stu-id="34550-226">Debugging Windows Authentication Errors</span></span>](./feature-details/debugging-windows-authentication-errors.md)
