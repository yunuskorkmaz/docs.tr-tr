---
title: WCF Sorun Giderme Hızlı Başlangıç
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], troubleshooting
- Windows Communication Foundation [WCF], troubleshooting
ms.assetid: a9ea7a53-f31a-46eb-806e-898e465a4992
ms.openlocfilehash: 86aab2b39aaa9c7d7d92f7d5738482723cf6852f
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320189"
---
# <a name="wcf-troubleshooting-quickstart"></a><span data-ttu-id="4c123-102">WCF Sorun Giderme Hızlı Başlangıç</span><span class="sxs-lookup"><span data-stu-id="4c123-102">WCF Troubleshooting Quickstart</span></span>
<span data-ttu-id="4c123-103">Bu konuda, müşterilerin, WCF istemcileri ve Hizmetleri geliştirirken çalıştırdığı bazı bilinen sorunlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="4c123-103">This topic lists a number of known issues customers have run into while developing WCF clients and services.</span></span> <span data-ttu-id="4c123-104">Çalıştırmakta olduğunuz sorun bu listede yoksa, hizmetiniz için izlemeyi yapılandırmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="4c123-104">If the issue you are running into is not in this list, we recommend you configure tracing for your service.</span></span> <span data-ttu-id="4c123-105">Bu, izleme dosyası görüntüleyiciyle görüntüleyebileceğiniz bir izleme dosyası oluşturur ve hizmet içinde oluşabilecek özel durumlar hakkında ayrıntılı bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c123-105">This will generate a trace file that you can view with the trace file viewer and get detailed information about exceptions that may be occurring within the service.</span></span> <span data-ttu-id="4c123-106">İzlemeyi yapılandırma hakkında daha fazla bilgi için bkz: [Izlemeyi yapılandırma](./diagnostics/tracing/configuring-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="4c123-106">For more information on configuring tracing, see: [Configuring Tracing](./diagnostics/tracing/configuring-tracing.md).</span></span> <span data-ttu-id="4c123-107">İzleme dosyası Görüntüleyicisi hakkında daha fazla bilgi için bkz. [hizmet Izleme Görüntüleyicisi Aracı (SvcTraceViewer. exe)](service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="4c123-107">For more information on the trace file viewer, see: [Service Trace Viewer Tool (SvcTraceViewer.exe)](service-trace-viewer-tool-svctraceviewer-exe.md).</span></span>  
  
1. [<span data-ttu-id="4c123-108">Windows 7 ve IIS yükledikten sonra, bir WCF hizmetine gözatmaya çalıştıklarında şu hata iletisini alıyorum: HTTP hatası 404,3 – bulunamadı</span><span class="sxs-lookup"><span data-stu-id="4c123-108">After installing Windows 7 and IIS, when I attempt to browse to a WCF service I get the following error message: HTTP Error 404.3 – Not Found</span></span>](#bkmk_0)  
  
     <span data-ttu-id="4c123-109">HTTP hatası 404,3 – bulunamadı sayfası uzantı yapılandırması nedeniyle sunulamıyor.</span><span class="sxs-lookup"><span data-stu-id="4c123-109">HTTP Error 404.3 – Not FoundThe page you are requesting cannot be served because of the extension configuration.</span></span> <span data-ttu-id="4c123-110">Sayfa bir komut dosyası ise, bir işleyici ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4c123-110">If the page is a script, add a handler.</span></span> <span data-ttu-id="4c123-111">Dosya indirildiyse, bir MIME eşlemesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4c123-111">If the file should be downloaded, add a MIME map.</span></span> <span data-ttu-id="4c123-112">Ayrıntılı hata InformationModule StaticFileModule.</span><span class="sxs-lookup"><span data-stu-id="4c123-112">Detailed Error InformationModule StaticFileModule.</span></span>  
  
2. [<span data-ttu-id="4c123-113">Bazen, istemciniz ilk istekten sonraki bir sırada boşta kalırsa ikinci istekte bir MessageSecurityException aldım. Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="4c123-113">Sometimes I receive a MessageSecurityException on the second request if my client is idle for a while after the first request. What is happening?</span></span>](#BKMK_q1)  
  
3. [<span data-ttu-id="4c123-114">Hizmet, yaklaşık 10 istemci etkileşim kurduktan sonra yeni istemcileri reddedecek şekilde başlatılır. Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="4c123-114">My service starts to reject new clients after about 10 clients are interacting with it. What is happening?</span></span>](#BKMK_q2)  
  
4. [<span data-ttu-id="4c123-115">Hizmet yapılandırmadan WCF uygulamasının yapılandırma dosyası dışında bir yerde yükleyebilir miyim?</span><span class="sxs-lookup"><span data-stu-id="4c123-115">Can I load my service configuration from somewhere other than the WCF application’s configuration file?</span></span>](#BKMK_q3)  
  
5. [<span data-ttu-id="4c123-116">Kullandığım hizmet ve istemci harika çalışıyor, ancak istemci başka bir bilgisayarda olduğunda bunları çalışmayacak mıyım? Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="4c123-116">My service and client work great, but I can’t get them to work when the client is on another computer? What’s happening?</span></span>](#BKMK_q4)  
  
6. [<span data-ttu-id="4c123-117">Türün bir istisna olduğu bir FaultException @ no__t-1özel durumu >, genel tür değil, her zaman istemcide genel bir FaultException türü aldım. Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="4c123-117">When I throw a FaultException\<Exception> where the type is an exception, I always receive a general FaultException type on the client and not the generic type. What’s happening?</span></span>](#BKMK_q5)  
  
7. [<span data-ttu-id="4c123-118">Yanıt bir veri içerdiğinde tek yönlü ve istek-yanıt işlemleri kabaca aynı hızda döndürülür. Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="4c123-118">It seems like one-way and request-reply operations return at roughly the same speed when the reply contains no data. What's happening?</span></span>](#BKMK_q6)  
  
8. [<span data-ttu-id="4c123-119">Kullandığım bir X. 509.440 sertifikası kullanıyorum ve bir System. Security. Cryptography. CryptographicException aldım. Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="4c123-119">I’m using an X.509 certificate with my service and I get a System.Security.Cryptography.CryptographicException. What’s happening?</span></span>](#BKMK_q77)  
  
9. [<span data-ttu-id="4c123-120">Bir işlemin ilk parametresini büyük harften küçük harfe kadar değiştirdim; Artık istemcim bir özel durum oluşturuyor. Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="4c123-120">I changed the first parameter of an operation from uppercase to lowercase; now my client throws an exception. What's happening?</span></span>](#BKMK_q88)  
  
10. [<span data-ttu-id="4c123-121">İzleme araçlarından birini kullanıyorum ve bir EndpointNotFoundException aldım. Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="4c123-121">I’m using one of my tracing tools and I get an EndpointNotFoundException. What’s happening?</span></span>](#BKMK_q99)  
  
11. [<span data-ttu-id="4c123-122">WCF SOAP uygulamasından bir WCF Web HTTP uygulaması çağrılırken hizmet şu hatayı döndürür: 405 yöntemine Izin verilmiyor</span><span class="sxs-lookup"><span data-stu-id="4c123-122">When calling a WCF Web HTTP application from a WCF SOAP application the service returns the following error: 405 Method Not Allowed</span></span>](#BK_MK99)  
  
 [<span data-ttu-id="4c123-123">Temel adres nedir? Bir uç nokta adresiyle nasıl ilişki vardır?</span><span class="sxs-lookup"><span data-stu-id="4c123-123">What is the base address? How does it relate to an endpoint address?</span></span>](#BKMK_q10)  
  
<a name="bkmk_0"></a>   
## <a name="after-installing-windows-7-and-iis-when-i-attempt-to-browse-to-a-wcf-service-i-get-the-following-error-message-http-error-4043--not-found"></a><span data-ttu-id="4c123-124">Windows 7 ve IIS yükledikten sonra, bir WCF hizmetine gözatmaya çalıştıklarında şu hata iletisini alıyorum: HTTP hatası 404,3 – bulunamadı</span><span class="sxs-lookup"><span data-stu-id="4c123-124">After installing Windows 7 and IIS, when I attempt to browse to a WCF service I get the following error message: HTTP Error 404.3 – Not Found</span></span>  
 <span data-ttu-id="4c123-125">Tam hata iletisi:</span><span class="sxs-lookup"><span data-stu-id="4c123-125">The full error message is:</span></span>  
  
 <span data-ttu-id="4c123-126">HTTP hatası 404,3 – bulunamadı sayfası uzantı yapılandırması nedeniyle sunulamıyor.</span><span class="sxs-lookup"><span data-stu-id="4c123-126">HTTP Error 404.3 – Not FoundThe page you are requesting cannot be served because of the extension configuration.</span></span> <span data-ttu-id="4c123-127">Sayfa bir komut dosyası ise, bir işleyici ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4c123-127">If the page is a script, add a handler.</span></span> <span data-ttu-id="4c123-128">Dosya indirildiyse, bir MIME eşlemesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4c123-128">If the file should be downloaded, add a MIME map.</span></span> <span data-ttu-id="4c123-129">Ayrıntılı hata InformationModule StaticFileModule.</span><span class="sxs-lookup"><span data-stu-id="4c123-129">Detailed Error InformationModule StaticFileModule.</span></span>  
  
 <span data-ttu-id="4c123-130">Bu hata iletisi, "Windows Communication Foundation HTTP etkinleştirmesi" açıkça Denetim Masası 'nda ayarlanmamışsa oluşur.</span><span class="sxs-lookup"><span data-stu-id="4c123-130">This error message occurs when "Windows Communication Foundation HTTP Activation" is not explicitly set in the Control Panel.</span></span> <span data-ttu-id="4c123-131">Bunu ayarlamak için, Denetim Masası 'na gidin, pencerenin sol alt köşesindeki Programlar ' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4c123-131">To set this go to the Control Panel, click Programs in the lower left hand corner of the window.</span></span> <span data-ttu-id="4c123-132">Windows özelliklerini aç veya Kapat ' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4c123-132">Click Turn Windows features on or off.</span></span> <span data-ttu-id="4c123-133">Microsoft .NET Framework 3.5.1 ' i genişletin ve Windows Communication Foundation HTTP etkinleştirmesi ' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="4c123-133">Expand Microsoft .NET Framework 3.5.1 and select Windows Communication Foundation HTTP Activation.</span></span>  
  
<a name="BKMK_q1"></a>   
## <a name="sometimes-i-receive-a-messagesecurityexception-on-the-second-request-if-my-client-is-idle-for-a-while-after-the-first-request-what-is-happening"></a><span data-ttu-id="4c123-134">Bazen, istemciniz ilk istekten sonraki bir sırada boşta kalırsa ikinci istekte bir MessageSecurityException aldım.</span><span class="sxs-lookup"><span data-stu-id="4c123-134">Sometimes I receive a MessageSecurityException on the second request if my client is idle for a while after the first request.</span></span> <span data-ttu-id="4c123-135">Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="4c123-135">What is happening?</span></span>  
 <span data-ttu-id="4c123-136">İkinci istek birincil olarak iki nedenden dolayı başarısız olabilir: (1) oturum zaman aşımına uğradı veya (2) hizmeti barındıran Web sunucusu geri dönüştürüldü.</span><span class="sxs-lookup"><span data-stu-id="4c123-136">The second request can fail primarily for two reasons: (1) the session has timed out or (2) the Web server that is hosting the service is recycled.</span></span> <span data-ttu-id="4c123-137">İlk durumda, oturum hizmetin zaman aşımına uğrayana kadar geçerli olur. Hizmet, hizmetin bağlamasında (<xref:System.ServiceModel.Channels.Binding.ReceiveTimeout%2A>) belirtilen süre içinde istemciden bir istek almadığında, hizmet güvenlik oturumunu sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="4c123-137">In the first case, the session is valid until the service times out. When the service does not receive a request from the client within the period of time specified in the service's binding (<xref:System.ServiceModel.Channels.Binding.ReceiveTimeout%2A>), the service terminates the security session.</span></span> <span data-ttu-id="4c123-138">Sonraki istemci iletileri <xref:System.ServiceModel.Security.MessageSecurityException> ' a sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="4c123-138">Subsequent client messages result in the <xref:System.ServiceModel.Security.MessageSecurityException>.</span></span> <span data-ttu-id="4c123-139">İstemci gelecek iletileri göndermek ya da durum bilgisi olan bir güvenlik bağlamı belirteci kullanmak için hizmetle güvenli bir oturum yeniden kurması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4c123-139">The client must re-establish a secure session with the service to send future messages or use a stateful security context token.</span></span> <span data-ttu-id="4c123-140">Durum bilgisi olan güvenlik bağlamı belirteçleri Ayrıca, güvenli bir oturumun, bir Web sunucusunun geri dönüştürülmekte olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="4c123-140">Stateful security context tokens also allow a secure session to survive a Web server being recycled.</span></span> <span data-ttu-id="4c123-141">Güvenli bir oturumda durum bilgisi olan güvenli bağlam belirteçleri kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: güvenli bir oturum Için güvenlik bağlamı belirteci oluşturma](./feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span><span class="sxs-lookup"><span data-stu-id="4c123-141">For more information about using stateful secure context tokens in a secure session, see [How to: Create a Security Context Token for a Secure Session](./feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span></span> <span data-ttu-id="4c123-142">Alternatif olarak, güvenli oturumları devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c123-142">Alternatively, you can disable secure sessions.</span></span> <span data-ttu-id="4c123-143">[@No__t-1wsHttpBinding >](../configure-apps/file-schema/wcf/wshttpbinding.md) bağlamayı kullandığınızda, güvenli oturumları devre dışı bırakmak için `establishSecurityContext` özelliğini `false` olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c123-143">When you use the [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) binding, you can set the `establishSecurityContext` property to `false` to disable secure sessions.</span></span> <span data-ttu-id="4c123-144">Diğer bağlamalara yönelik güvenli oturumları devre dışı bırakmak için özel bir bağlama oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4c123-144">To disable secure sessions for other bindings, you must create a custom binding.</span></span> <span data-ttu-id="4c123-145">Özel bağlama oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](./feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="4c123-145">For details about creating a custom binding, see [How to: Create a Custom Binding Using the SecurityBindingElement](./feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span> <span data-ttu-id="4c123-146">Bu seçeneklerden herhangi birini uygulamadan önce, uygulamanızın güvenlik gereksinimlerini anlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4c123-146">Before you apply any of these options, you must understand your application's security requirements.</span></span>  
  
<a name="BKMK_q2"></a>   
## <a name="my-service-starts-to-reject-new-clients-after-about-10-clients-are-interacting-with-it-what-is-happening"></a><span data-ttu-id="4c123-147">Hizmet, yaklaşık 10 istemci etkileşim kurduktan sonra yeni istemcileri reddedecek şekilde başlatılır.</span><span class="sxs-lookup"><span data-stu-id="4c123-147">My service starts to reject new clients after about 10 clients are interacting with it.</span></span> <span data-ttu-id="4c123-148">Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="4c123-148">What is happening?</span></span>  
 <span data-ttu-id="4c123-149">Varsayılan olarak, hizmetlerde yalnızca 10 eşzamanlı oturum olabilir.</span><span class="sxs-lookup"><span data-stu-id="4c123-149">By default, services can have only 10 concurrent sessions.</span></span> <span data-ttu-id="4c123-150">Bu nedenle, hizmet bağlamaları oturumlar kullanıyorsa, hizmet bu sayıya ulaşana kadar yeni istemci bağlantılarını kabul eder ve ardından geçerli oturumlardan biri sonlanana kadar yeni istemci bağlantılarını reddeder.</span><span class="sxs-lookup"><span data-stu-id="4c123-150">Therefore, if the service bindings use sessions, the service accepts new client connections until it reaches that number, after which it refuses new client connections until one of the current sessions ends.</span></span> <span data-ttu-id="4c123-151">Birkaç yolla daha fazla istemci destekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c123-151">You can support more clients in a number of ways.</span></span> <span data-ttu-id="4c123-152">Hizmetiniz oturum gerektirmiyorsa, oturumsuz bağlama kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="4c123-152">If your service does not require sessions, do not use a sessionful binding.</span></span> <span data-ttu-id="4c123-153">(Daha fazla bilgi için bkz. [oturumları kullanma](using-sessions.md).) Diğer bir seçenek de <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A> özelliğinin değerini, sizin için uygun olan sayı ile değiştirerek oturum sınırını artırmaya yönelik bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="4c123-153">(For more information, see [Using Sessions](using-sessions.md).) Another option is to increase the session limit by changing the value of the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A> property to the number appropriate to your circumstance.</span></span>  
  
<a name="BKMK_q3"></a>   
## <a name="can-i-load-my-service-configuration-from-somewhere-other-than-the-wcf-applications-configuration-file"></a><span data-ttu-id="4c123-154">Hizmet yapılandırmadan WCF uygulamasının yapılandırma dosyası dışında bir yerde yükleyebilir miyim?</span><span class="sxs-lookup"><span data-stu-id="4c123-154">Can I load my service configuration from somewhere other than the WCF application’s configuration file?</span></span>  
 <span data-ttu-id="4c123-155">Evet, ancak, <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> yöntemini geçersiz kılan özel bir <xref:System.ServiceModel.ServiceHost> sınıfı oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4c123-155">Yes, however, you have to create a custom <xref:System.ServiceModel.ServiceHost> class that overrides the <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> method.</span></span> <span data-ttu-id="4c123-156">Bu yöntemin içinde, önce yapılandırmayı yüklemek için temel çağırabilirsiniz (Standart yapılandırma bilgilerini de yüklemek istiyorsanız), ancak yapılandırma yükleme sistemini tamamen değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c123-156">Inside that method, you can call the base to load configuration first (if you want to load the standard configuration information as well) but you can also entirely replace the configuration loading system.</span></span> <span data-ttu-id="4c123-157">Yapılandırmayı uygulama yapılandırma dosyasından farklı bir yapılandırma dosyasından yüklemek isterseniz, yapılandırma dosyasını kendiniz ayrıştırabilmeniz ve yapılandırmayı yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4c123-157">Note that if you want to load configuration from a configuration file that is different from the application configuration file, you must parse the configuration file yourself and load the configuration.</span></span>  
  
 <span data-ttu-id="4c123-158">Aşağıdaki kod örneği, <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> yönteminin nasıl geçersiz kılınacağını ve bir uç noktanın doğrudan nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4c123-158">The following code example shows how to override the <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> method and directly configure an endpoint.</span></span>  
  
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
## <a name="my-service-and-client-work-great-but-i-cant-get-them-to-work-when-the-client-is-on-another-computer-whats-happening"></a><span data-ttu-id="4c123-159">Kullandığım hizmet ve istemci harika çalışıyor, ancak istemci başka bir bilgisayarda olduğunda bunları çalışmayacak mıyım?</span><span class="sxs-lookup"><span data-stu-id="4c123-159">My service and client work great, but I can’t get them to work when the client is on another computer?</span></span> <span data-ttu-id="4c123-160">Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="4c123-160">What’s happening?</span></span>  
 <span data-ttu-id="4c123-161">Özel duruma bağlı olarak birkaç sorun olabilir:</span><span class="sxs-lookup"><span data-stu-id="4c123-161">Depending upon the exception, there may be several issues:</span></span>  
  
- <span data-ttu-id="4c123-162">İstemci uç noktası adreslerini "localhost" değil ana bilgisayar adıyla değiştirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="4c123-162">You might need to change the client endpoint addresses to the host name and not "localhost".</span></span>  
  
- <span data-ttu-id="4c123-163">Bağlantı noktasını uygulamaya açmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="4c123-163">You might need to open the port to the application.</span></span> <span data-ttu-id="4c123-164">Ayrıntılar için bkz. SDK örneklerinden [güvenlik duvarı yönergeleri](./samples/firewall-instructions.md) .</span><span class="sxs-lookup"><span data-stu-id="4c123-164">For details, see [Firewall Instructions](./samples/firewall-instructions.md) from the SDK samples.</span></span>  
  
- <span data-ttu-id="4c123-165">Olası diğer sorunlar için [Windows Communication Foundation Örnekleri çalıştıran](./samples/running-the-samples.md)örnekler konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="4c123-165">For other possible issues, see the samples topic [Running the Windows Communication Foundation Samples](./samples/running-the-samples.md).</span></span>  
  
- <span data-ttu-id="4c123-166">İstemciniz Windows kimlik bilgilerini kullanıyorsa ve özel durum bir <xref:System.ServiceModel.Security.SecurityNegotiationException> ise, Kerberos 'u aşağıdaki şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="4c123-166">If your client is using Windows credentials and the exception is a <xref:System.ServiceModel.Security.SecurityNegotiationException>, configure Kerberos as follows.</span></span>  
  
    1. <span data-ttu-id="4c123-167">Kimlik bilgilerini istemcinin App. config dosyasındaki Endpoint öğesine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="4c123-167">Add the identity credentials to the endpoint element in the client’s App.config file:</span></span>  
  
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
  
    2. <span data-ttu-id="4c123-168">Şirket içinde barındırılan hizmeti sistem veya NetworkService hesabı altında çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4c123-168">Run the self-hosted service under the System or NetworkService account.</span></span> <span data-ttu-id="4c123-169">Sistem hesabı altında bir komut penceresi oluşturmak için bu komutu çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="4c123-169">You can run this command to create a command window under the System account:</span></span>  
  
        ```console
        at 12:36 /interactive "cmd.exe"  
        ```  
  
    3. <span data-ttu-id="4c123-170">Hizmeti, varsayılan olarak hizmet asıl adı (SPN) hesabını kullanan Internet Information Services (IIS) altında barındırın.</span><span class="sxs-lookup"><span data-stu-id="4c123-170">Host the service under Internet Information Services (IIS), which, by default, uses the service principal name (SPN) account.</span></span>  
  
    4. <span data-ttu-id="4c123-171">SetSPN kullanarak etki alanı ile yeni bir SPN kaydettirin.</span><span class="sxs-lookup"><span data-stu-id="4c123-171">Register a new SPN with the domain using SetSPN.</span></span> <span data-ttu-id="4c123-172">Bunu yapmak için, bir etki alanı yöneticisi olmanız gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="4c123-172">Note that you will need to be a domain administrator in order to do this.</span></span>  
  
 <span data-ttu-id="4c123-173">Kerberos protokolü hakkında daha fazla bilgi için bkz. [WCF 'de kullanılan güvenlik kavramları](./feature-details/security-concepts-used-in-wcf.md) ve:</span><span class="sxs-lookup"><span data-stu-id="4c123-173">For more information about the Kerberos protocol, see [Security Concepts Used in WCF](./feature-details/security-concepts-used-in-wcf.md) and:</span></span>  
  
- [<span data-ttu-id="4c123-174">Windows Kimlik Doğrulama Hatalarını Ayıklama</span><span class="sxs-lookup"><span data-stu-id="4c123-174">Debugging Windows Authentication Errors</span></span>](./feature-details/debugging-windows-authentication-errors.md)  
  
- [<span data-ttu-id="4c123-175">Http. sys kullanarak Kerberos hizmet sorumlusu adlarını kaydetme</span><span class="sxs-lookup"><span data-stu-id="4c123-175">Registering Kerberos Service Principal Names by Using Http.sys</span></span>](https://go.microsoft.com/fwlink/?LinkId=86943)  
  
- [<span data-ttu-id="4c123-176">Açıklanan Kerberos</span><span class="sxs-lookup"><span data-stu-id="4c123-176">Kerberos Explained</span></span>](https://go.microsoft.com/fwlink/?LinkId=86946)  
  
<a name="BKMK_q5"></a>   
## <a name="when-i-throw-a-faultexceptionexception-where-the-type-is-an-exception-i-always-receive-a-general-faultexception-type-on-the-client-and-not-the-generic-type-whats-happening"></a><span data-ttu-id="4c123-177">Türün bir özel durum olduğu bir FaultException @ no__t-0Exception > oluştururken, genel tür değil, her zaman istemcide genel bir FaultException türü aldım.</span><span class="sxs-lookup"><span data-stu-id="4c123-177">When I throw a FaultException\<Exception> where the type is an exception, I always receive a general FaultException type on the client and not the generic type.</span></span> <span data-ttu-id="4c123-178">Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="4c123-178">What’s happening?</span></span>  
 <span data-ttu-id="4c123-179">Kendi özel hata veri türünü oluşturmanız ve bunu hata sözleşmenizin ayrıntı türü olarak bildirmeniz önemle tavsiye edilir.</span><span class="sxs-lookup"><span data-stu-id="4c123-179">It is highly recommended that you create your own custom error data type and declare that as the detail type in your fault contract.</span></span> <span data-ttu-id="4c123-180">Nedeni sistem tarafından sağlanmış özel durum türlerini kullanmaktır:</span><span class="sxs-lookup"><span data-stu-id="4c123-180">The reason is that using system-provided exception types:</span></span>  
  
- <span data-ttu-id="4c123-181">Hizmet odaklı uygulamaların en büyük güçlerinden birini kaldıran bir tür bağımlılığı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4c123-181">Creates a type dependency that removes one of the biggest strengths of service-oriented applications.</span></span>  
  
- <span data-ttu-id="4c123-182">Standart bir şekilde özel durum serileştirilme bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="4c123-182">Cannot depend upon exceptions serializing in a standard way.</span></span> <span data-ttu-id="4c123-183">Bazıları — <xref:System.Security.SecurityException> — gibi, seri hale getirilebilir.</span><span class="sxs-lookup"><span data-stu-id="4c123-183">Some—like <xref:System.Security.SecurityException>—may not be serializable at all.</span></span>  
  
- <span data-ttu-id="4c123-184">İstemcilere iç uygulama ayrıntılarını sunar.</span><span class="sxs-lookup"><span data-stu-id="4c123-184">Exposes internal implementation details to clients.</span></span> <span data-ttu-id="4c123-185">Daha fazla bilgi için bkz. [anlaşmalar ve hizmetlerde hataları belirtme ve işleme](specifying-and-handling-faults-in-contracts-and-services.md).</span><span class="sxs-lookup"><span data-stu-id="4c123-185">For more information, see [Specifying and Handling Faults in Contracts and Services](specifying-and-handling-faults-in-contracts-and-services.md).</span></span>  
  
 <span data-ttu-id="4c123-186">Ancak bir uygulamada hata ayıklaması yapıyorsanız, özel durum bilgilerini seri hale getirebilirsiniz ve <xref:System.ServiceModel.Description.ServiceDebugBehavior> sınıfını kullanarak istemciye döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c123-186">If you are debugging an application, however, you can serialize exception information and return it to the client by using the <xref:System.ServiceModel.Description.ServiceDebugBehavior> class.</span></span>  
  
<a name="BKMK_q6"></a>   
## <a name="it-seems-like-one-way-and-request-reply-operations-return-at-roughly-the-same-speed-when-the-reply-contains-no-data-whats-happening"></a><span data-ttu-id="4c123-187">Yanıt bir veri içerdiğinde tek yönlü ve istek-yanıt işlemleri kabaca aynı hızda döndürülür.</span><span class="sxs-lookup"><span data-stu-id="4c123-187">It seems like one-way and request-reply operations return at roughly the same speed when the reply contains no data.</span></span> <span data-ttu-id="4c123-188">Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="4c123-188">What's happening?</span></span>  
 <span data-ttu-id="4c123-189">Bir işlemin tek bir şekilde belirtilmesi, yalnızca işlem sözleşmesinin bir giriş iletisini kabul ettiği ve bir çıkış iletisi döndürmediği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="4c123-189">Specifying that an operation is one way means only that the operation contract accepts an input message and does not return an output message.</span></span> <span data-ttu-id="4c123-190">WCF 'de, giden veriler kabloya yazıldığında veya bir özel durum oluştuğunda tüm istemci etkinleştirmeleri döndürülür.</span><span class="sxs-lookup"><span data-stu-id="4c123-190">In WCF, all client invocations return when the outbound data has been written to the wire or an exception is thrown.</span></span> <span data-ttu-id="4c123-191">Tek yönlü işlemler aynı şekilde çalışır ve hizmet, ağdaki verileri kabul etmek üzere hazırlanmamışsa, hizmet bulunamıyorsa veya engellenmiyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="4c123-191">One-way operations work the same way, and they can throw if the service cannot be located or block if the service is not prepared to accept the data from the network.</span></span> <span data-ttu-id="4c123-192">Genellikle WCF 'de, bu, istemciye istek yanıtlamadan daha hızlı dönen tek yönlü çağrılara neden olur; Ancak, giden verilerin ağ üzerinden gönderilmesini yavaşlatan herhangi bir koşul, tek yönlü işlemlerin yanı sıra istek-yanıt işlemlerini yavaşlatır.</span><span class="sxs-lookup"><span data-stu-id="4c123-192">Typically in WCF, this results in one-way calls returning to the client more quickly than request-reply; but any condition that slows the sending of the outbound data over the network slows one-way operations as well as request-reply operations.</span></span> <span data-ttu-id="4c123-193">Daha fazla bilgi için bkz. [tek yönlü hizmetler](./feature-details/one-way-services.md) ve [WCF Istemcisi kullanarak hizmetlere erişme](./feature-details/accessing-services-using-a-client.md).</span><span class="sxs-lookup"><span data-stu-id="4c123-193">For more information, see [One-Way Services](./feature-details/one-way-services.md) and [Accessing Services Using a WCF Client](./feature-details/accessing-services-using-a-client.md).</span></span>  
  
<a name="BKMK_q77"></a>   
## <a name="im-using-an-x509-certificate-with-my-service-and-i-get-a-systemsecuritycryptographycryptographicexception-whats-happening"></a><span data-ttu-id="4c123-194">Kullandığım bir X. 509.440 sertifikası kullanıyorum ve bir System. Security. Cryptography. CryptographicException aldım.</span><span class="sxs-lookup"><span data-stu-id="4c123-194">I’m using an X.509 certificate with my service and I get a System.Security.Cryptography.CryptographicException.</span></span> <span data-ttu-id="4c123-195">Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="4c123-195">What’s happening?</span></span>  
 <span data-ttu-id="4c123-196">Bu, genellikle IIS çalışan işleminin çalıştırıldığı Kullanıcı hesabı değiştirildikten sonra oluşur.</span><span class="sxs-lookup"><span data-stu-id="4c123-196">This commonly occurs after changing the user account under which the IIS worker process runs.</span></span> <span data-ttu-id="4c123-197">Örneğin, [!INCLUDE[wxp](../../../includes/wxp-md.md)] ' da, Aspnet_wp. exe ' nin altında çalıştığı varsayılan kullanıcı hesabını özel bir kullanıcı hesabına değiştirirseniz, bu hatayı görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c123-197">For example, in [!INCLUDE[wxp](../../../includes/wxp-md.md)], if you change the default user account that the Aspnet_wp.exe runs under from ASPNET to a custom user account, you may see this error.</span></span> <span data-ttu-id="4c123-198">Özel anahtar kullanılıyorsa, onu kullanan işlemin bu anahtarı depolayan dosyaya erişmek için gerekli izinlere sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4c123-198">If using a private key, the process that uses it will need to have permissions to access the file storing that key.</span></span>  
  
 <span data-ttu-id="4c123-199">Bu durumda, özel anahtarı içeren dosya için işlem hesabına yönelik okuma erişim ayrıcalıklarına sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4c123-199">If this is the case, you must give read access privileges to the process's account for the file containing the private key.</span></span> <span data-ttu-id="4c123-200">Örneğin, IIS çalışan işlemi Bob hesabı altında çalışıyorsa, Bob 'un özel anahtarı içeren dosyaya okuma erişimi vermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="4c123-200">For example, if the IIS worker process is running under the Bob account, then you will need to give Bob read access to the file containing the private key.</span></span>  
  
 <span data-ttu-id="4c123-201">Belirli bir X. 509.952 sertifikası için özel anahtarı içeren dosyaya doğru Kullanıcı hesabına erişim verme hakkında daha fazla bilgi için bkz. [nasıl yapılır: X. 509.440 SERTIFIKALARıNı WCF 'ye erişilebilir hale getirme](./feature-details/how-to-make-x-509-certificates-accessible-to-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="4c123-201">For more information about how to give the correct user account access to the file that contains the private key for a specific X.509 certificate, see [How to: Make X.509 Certificates Accessible to WCF](./feature-details/how-to-make-x-509-certificates-accessible-to-wcf.md).</span></span>  
  
<a name="BKMK_q88"></a>   
## <a name="i-changed-the-first-parameter-of-an-operation-from-uppercase-to-lowercase-now-my-client-throws-an-exception-whats-happening"></a><span data-ttu-id="4c123-202">Bir işlemin ilk parametresini büyük harften küçük harfe kadar değiştirdim; Artık istemcim bir özel durum oluşturuyor.</span><span class="sxs-lookup"><span data-stu-id="4c123-202">I changed the first parameter of an operation from uppercase to lowercase; now my client throws an exception.</span></span> <span data-ttu-id="4c123-203">Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="4c123-203">What's happening?</span></span>  
 <span data-ttu-id="4c123-204">İşlem imzasında parametre adlarının değeri sözleşmenin bir parçasıdır ve büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="4c123-204">The value of the parameter names in the operation signature are part of the contract and are case-sensitive.</span></span> <span data-ttu-id="4c123-205">Yerel parametre adı ile istemci uygulamaları için işlemi açıklayan meta veriler arasında ayrım yapmanız gerektiğinde <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType> özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="4c123-205">Use the <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType> attribute when you need to distinguish between the local parameter name and the metadata that describes the operation for client applications.</span></span>  
  
<a name="BKMK_q99"></a>   
## <a name="im-using-one-of-my-tracing-tools-and-i-get-an-endpointnotfoundexception-whats-happening"></a><span data-ttu-id="4c123-206">İzleme araçlarından birini kullanıyorum ve bir EndpointNotFoundException aldım.</span><span class="sxs-lookup"><span data-stu-id="4c123-206">I’m using one of my tracing tools and I get an EndpointNotFoundException.</span></span> <span data-ttu-id="4c123-207">Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="4c123-207">What’s happening?</span></span>  
 <span data-ttu-id="4c123-208">Sistem tarafından sağlanmış WCF izleme mekanizması olmayan bir izleme aracı kullanıyorsanız ve bir adres filtresi uyumsuzluğu olduğunu belirten bir <xref:System.ServiceModel.EndpointNotFoundException> alırsanız, iletileri izleme yardımcı programına yönlendirmek için <xref:System.ServiceModel.Description.ClientViaBehavior> sınıfını kullanmanız gerekir ve yardımcı program bu iletileri hizmet adresine yeniden yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="4c123-208">If you are using a tracing tool that is not the system-provided WCF tracing mechanism and you receive an <xref:System.ServiceModel.EndpointNotFoundException> that indicates that there was an address filter mismatch, you need to use the <xref:System.ServiceModel.Description.ClientViaBehavior> class to direct the messages to the tracing utility and have the utility redirect those messages to the service address.</span></span> <span data-ttu-id="4c123-209">@No__t-0 sınıfı, sonraki ağ adresini, `To` adresleme üstbilgisiyle belirtilen son alıcıdan ayrı olarak belirtmek için `Via` adresleme üst bilgisini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="4c123-209">The <xref:System.ServiceModel.Description.ClientViaBehavior> class alters the `Via` addressing header to specify the next network address separately from the ultimate receiver, indicated by the `To` addressing header.</span></span> <span data-ttu-id="4c123-210">Ancak bunu yaparken, `To` değerini oluşturmak için kullanılan uç nokta adresini değiştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="4c123-210">When doing this, however, do not change the endpoint address, which is used to establish the `To` value.</span></span>  
  
 <span data-ttu-id="4c123-211">Aşağıdaki kod örneği bir örnek istemci yapılandırma dosyası gösterir.</span><span class="sxs-lookup"><span data-stu-id="4c123-211">The following code example shows an example client configuration file.</span></span>  
  
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
## <a name="what-is-the-base-address-how-does-it-relate-to-an-endpoint-address"></a><span data-ttu-id="4c123-212">Temel adres nedir?</span><span class="sxs-lookup"><span data-stu-id="4c123-212">What is the base address?</span></span> <span data-ttu-id="4c123-213">Bir uç nokta adresiyle nasıl ilişki vardır?</span><span class="sxs-lookup"><span data-stu-id="4c123-213">How does it relate to an endpoint address?</span></span>  
 <span data-ttu-id="4c123-214">Temel adres, <xref:System.ServiceModel.ServiceHost> sınıfının kök adresidir.</span><span class="sxs-lookup"><span data-stu-id="4c123-214">A base address is the root address for a <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="4c123-215">Varsayılan olarak, hizmet yapılandırmanıza bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior> sınıfı eklerseniz, ana bilgisayar yayımladığı tüm uç noktalar için Web Hizmetleri Açıklama Dili (WSDL) HTTP temel adresinden alınır ve meta veri davranışına ve "? wsdl ".</span><span class="sxs-lookup"><span data-stu-id="4c123-215">By default, if you add a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class into your service configuration, the Web Services Description Language (WSDL) for all endpoints the host publishes are retrieved from the HTTP base address, plus any relative address provided to the metadata behavior, plus "?wsdl".</span></span> <span data-ttu-id="4c123-216">ASP.NET ve IIS hakkında bilgi sahibiyseniz, taban adresi sanal dizine eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="4c123-216">If you are familiar with ASP.NET and IIS, the base address is equivalent to the virtual directory.</span></span>  
  
## <a name="sharing-a-port-between-a-service-endpoint-and-a-mex-endpoint-using-the-nettcpbinding"></a><span data-ttu-id="4c123-217">NetTcpBinding kullanarak bir hizmet uç noktası ve bir MEX uç noktası arasında bağlantı noktası paylaşma</span><span class="sxs-lookup"><span data-stu-id="4c123-217">Sharing a port between a service endpoint and a mex endpoint using the NetTcpBinding</span></span>  
 <span data-ttu-id="4c123-218">Bir hizmetin temel adresini net. TCP:/sunucum: 8080/hizmetim olarak belirtirseniz ve aşağıdaki uç noktaları eklemek için:</span><span class="sxs-lookup"><span data-stu-id="4c123-218">If you specify the base address for a service as net.tcp://MyServer:8080/MyService and add the following endpoints:</span></span>  
  
```xml  
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
 <span data-ttu-id="4c123-219">Ve NetTcpBinding ayarlarından birini aşağıdaki yapılandırma kod parçacığında gösterildiği gibi değiştirirseniz:</span><span class="sxs-lookup"><span data-stu-id="4c123-219">And if you modify one of the NetTcpBinding settings as shown in the following configuration snippet:</span></span>  
  
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
  
 <span data-ttu-id="4c123-220">Şu şekilde bir hata görürsünüz: Işlenmeyen özel durum: System. ServiceModel. Addressalreadınuseexception: IP bağlantı noktası 0.0.0.0:9000 üzerinde bir dinleyici zaten var Aşağıdaki yapılandırma kod parçacığında gösterildiği gibi, MEX uç noktası:</span><span class="sxs-lookup"><span data-stu-id="4c123-220">You will see an error like the following: Unhandled Exception: System.ServiceModel.AddressAlreadyInUseException: There is already a listener on IP endpoint 0.0.0.0:9000 You can work around this error by specifying a fully qualified URL with a different port for the MEX endpoint as shown in the following configuration snippet:</span></span>  
  
```xml
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="net.tcp://localhost:9001/servicemodelsamples/mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
<a name="BK_MK99"></a>   
## <a name="when-calling-a-wcf-web-http-application-from-a-wcf-soap-application-the-service-returns-the-following-error-405-method-not-allowed"></a><span data-ttu-id="4c123-221">WCF SOAP uygulamasından bir WCF Web HTTP uygulaması çağrılırken hizmet şu hatayı döndürür: 405 yöntemine Izin verilmiyor</span><span class="sxs-lookup"><span data-stu-id="4c123-221">When calling a WCF Web HTTP application from a WCF SOAP application the service returns the following error: 405 Method Not Allowed</span></span>  
 <span data-ttu-id="4c123-222">WCF Web HTTP uygulamasını çağırma (bir WCF hizmetinden <xref:System.ServiceModel.WebHttpBinding> ve <xref:System.ServiceModel.Description.WebHttpBehavior>) kullanan bir hizmet şu özel durumu oluşturabilir: `Unhandled Exception: System.ServiceModel.FaultException`1 [System. ServiceModel. ExceptionDetail]: uzak sunucu beklenmeyen bir yanıt döndürdü: (405) yöntemi değil İzin verildi. ' Bu özel durum, WCF giden <xref:System.ServiceModel.OperationContext> ' ü gelen <xref:System.ServiceModel.OperationContext> ile üzerine yazdığından oluşur.</span><span class="sxs-lookup"><span data-stu-id="4c123-222">Calling a WCF Web HTTP application (a service that uses the <xref:System.ServiceModel.WebHttpBinding> and <xref:System.ServiceModel.Description.WebHttpBehavior>) from a WCF service may generate the following exception: `Unhandled Exception: System.ServiceModel.FaultException`1[System.ServiceModel.ExceptionDetail]: The remote server returned an unexpected response: (405) Method Not Allowed.\` This exception occurs because WCF overwrites the outgoing <xref:System.ServiceModel.OperationContext> with the incoming <xref:System.ServiceModel.OperationContext>.</span></span> <span data-ttu-id="4c123-223">Bu sorunu çözmek için WCF Web HTTP hizmeti işlemi içinde <xref:System.ServiceModel.OperationContextScope> oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4c123-223">To solve this problem create an <xref:System.ServiceModel.OperationContextScope> within the WCF Web HTTP service operation.</span></span> <span data-ttu-id="4c123-224">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="4c123-224">For example:</span></span>  
  
```csharp
public string Echo(string input)  
{  
    using (new OperationContextScope(this.InnerChannel))  
    {  
        return base.Channel.Echo(input);  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="4c123-225">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4c123-225">See also</span></span>

- [<span data-ttu-id="4c123-226">Windows Kimlik Doğrulama Hatalarını Ayıklama</span><span class="sxs-lookup"><span data-stu-id="4c123-226">Debugging Windows Authentication Errors</span></span>](./feature-details/debugging-windows-authentication-errors.md)
