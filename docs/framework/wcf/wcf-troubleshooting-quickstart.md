---
description: 'Daha fazla bilgi edinin: WCF sorun giderme hızlı başlangıç'
title: WCF Sorun Giderme Hızlı Başlangıç
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], troubleshooting
- Windows Communication Foundation [WCF], troubleshooting
ms.assetid: a9ea7a53-f31a-46eb-806e-898e465a4992
ms.openlocfilehash: 686b008752704ed54700d9c49e2df71f9fc3fd98
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631664"
---
# <a name="wcf-troubleshooting-quickstart"></a><span data-ttu-id="0ad6b-103">WCF Sorun Giderme Hızlı Başlangıç</span><span class="sxs-lookup"><span data-stu-id="0ad6b-103">WCF Troubleshooting Quickstart</span></span>

<span data-ttu-id="0ad6b-104">Bu konuda, müşterilerin, WCF istemcileri ve Hizmetleri geliştirirken çalıştırdığı bazı bilinen sorunlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-104">This topic lists a number of known issues customers have run into while developing WCF clients and services.</span></span> <span data-ttu-id="0ad6b-105">Çalıştırmakta olduğunuz sorun bu listede yoksa, hizmetiniz için izlemeyi yapılandırmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-105">If the issue you are running into is not in this list, we recommend you configure tracing for your service.</span></span> <span data-ttu-id="0ad6b-106">Bu, izleme dosyası görüntüleyiciyle görüntüleyebileceğiniz bir izleme dosyası oluşturur ve hizmet içinde oluşabilecek özel durumlar hakkında ayrıntılı bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-106">This will generate a trace file that you can view with the trace file viewer and get detailed information about exceptions that may be occurring within the service.</span></span> <span data-ttu-id="0ad6b-107">İzlemeyi yapılandırma hakkında daha fazla bilgi için bkz: [Izlemeyi yapılandırma](./diagnostics/tracing/configuring-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="0ad6b-107">For more information on configuring tracing, see: [Configuring Tracing](./diagnostics/tracing/configuring-tracing.md).</span></span> <span data-ttu-id="0ad6b-108">İzleme dosyası Görüntüleyicisi hakkında daha fazla bilgi için bkz. [hizmet Izleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)](service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="0ad6b-108">For more information on the trace file viewer, see: [Service Trace Viewer Tool (SvcTraceViewer.exe)](service-trace-viewer-tool-svctraceviewer-exe.md).</span></span>  
  
1. [<span data-ttu-id="0ad6b-109">Windows 7 ve IIS yükledikten sonra, bir WCF hizmetine gözatmaya çalıştıklarında şu hata iletisini alıyorum: HTTP hatası 404,3 – bulunamadı</span><span class="sxs-lookup"><span data-stu-id="0ad6b-109">After installing Windows 7 and IIS, when I attempt to browse to a WCF service I get the following error message: HTTP Error 404.3 – Not Found</span></span>](#bkmk_0)  
  
     <span data-ttu-id="0ad6b-110">HTTP hatası 404,3 – bulunamadı sayfası uzantı yapılandırması nedeniyle sunulamıyor.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-110">HTTP Error 404.3 – Not FoundThe page you are requesting cannot be served because of the extension configuration.</span></span> <span data-ttu-id="0ad6b-111">Sayfa bir komut dosyası ise, bir işleyici ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-111">If the page is a script, add a handler.</span></span> <span data-ttu-id="0ad6b-112">Dosya indirildiyse, bir MIME eşlemesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-112">If the file should be downloaded, add a MIME map.</span></span> <span data-ttu-id="0ad6b-113">Ayrıntılı hata InformationModule StaticFileModule.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-113">Detailed Error InformationModule StaticFileModule.</span></span>  
  
2. [<span data-ttu-id="0ad6b-114">Bazen, istemciniz ilk istekten sonraki bir sırada boşta kalırsa ikinci istekte bir MessageSecurityException aldım. Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="0ad6b-114">Sometimes I receive a MessageSecurityException on the second request if my client is idle for a while after the first request. What is happening?</span></span>](#BKMK_q1)  
  
3. [<span data-ttu-id="0ad6b-115">Hizmet, yaklaşık 10 istemci etkileşim kurduktan sonra yeni istemcileri reddedecek şekilde başlatılır. Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="0ad6b-115">My service starts to reject new clients after about 10 clients are interacting with it. What is happening?</span></span>](#BKMK_q2)  
  
4. [<span data-ttu-id="0ad6b-116">Hizmet yapılandırmadan WCF uygulamasının yapılandırma dosyası dışında bir yerde yükleyebilir miyim?</span><span class="sxs-lookup"><span data-stu-id="0ad6b-116">Can I load my service configuration from somewhere other than the WCF application’s configuration file?</span></span>](#BKMK_q3)  
  
5. [<span data-ttu-id="0ad6b-117">Kullandığım hizmet ve istemci harika çalışıyor, ancak istemci başka bir bilgisayarda olduğunda bunları çalışmayacak mıyım? Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="0ad6b-117">My service and client work great, but I can’t get them to work when the client is on another computer? What’s happening?</span></span>](#BKMK_q4)  
  
6. [<span data-ttu-id="0ad6b-118">\<Exception>Türün bir özel durum olduğu bir FaultException oluşturdum, genel tür değil istemciye her zaman genel bir FaultException türü aldım. Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="0ad6b-118">When I throw a FaultException\<Exception> where the type is an exception, I always receive a general FaultException type on the client and not the generic type. What’s happening?</span></span>](#BKMK_q5)  
  
7. [<span data-ttu-id="0ad6b-119">Yanıt bir veri içerdiğinde tek yönlü ve istek-yanıt işlemleri kabaca aynı hızda döndürülür. Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="0ad6b-119">It seems like one-way and request-reply operations return at roughly the same speed when the reply contains no data. What's happening?</span></span>](#BKMK_q6)  
  
8. [<span data-ttu-id="0ad6b-120">Kullandığım bir X. 509.440 sertifikası kullanıyorum ve bir System. Security. Cryptography. CryptographicException aldım. Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="0ad6b-120">I’m using an X.509 certificate with my service and I get a System.Security.Cryptography.CryptographicException. What’s happening?</span></span>](#BKMK_q77)  
  
9. [<span data-ttu-id="0ad6b-121">Bir işlemin ilk parametresini büyük harften küçük harfe kadar değiştirdim; Artık istemcim bir özel durum oluşturuyor. Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="0ad6b-121">I changed the first parameter of an operation from uppercase to lowercase; now my client throws an exception. What's happening?</span></span>](#BKMK_q88)  
  
10. [<span data-ttu-id="0ad6b-122">İzleme araçlarından birini kullanıyorum ve bir EndpointNotFoundException aldım. Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="0ad6b-122">I’m using one of my tracing tools and I get an EndpointNotFoundException. What’s happening?</span></span>](#BKMK_q99)  
  
11. [<span data-ttu-id="0ad6b-123">WCF SOAP uygulamasından bir WCF Web HTTP uygulaması çağrılırken hizmet şu hatayı döndürür: 405 yöntemine Izin verilmiyor</span><span class="sxs-lookup"><span data-stu-id="0ad6b-123">When calling a WCF Web HTTP application from a WCF SOAP application the service returns the following error: 405 Method Not Allowed</span></span>](#BK_MK99)  
  
 [<span data-ttu-id="0ad6b-124">Temel adres nedir? Bir uç nokta adresiyle nasıl ilişki vardır?</span><span class="sxs-lookup"><span data-stu-id="0ad6b-124">What is the base address? How does it relate to an endpoint address?</span></span>](#BKMK_q10)  
  
<a name="bkmk_0"></a>

## <a name="after-installing-windows-7-and-iis-when-i-attempt-to-browse-to-a-wcf-service-i-get-the-following-error-message-http-error-4043--not-found"></a><span data-ttu-id="0ad6b-125">Windows 7 ve IIS yükledikten sonra, bir WCF hizmetine gözatmaya çalıştıklarında şu hata iletisini alıyorum: HTTP hatası 404,3 – bulunamadı</span><span class="sxs-lookup"><span data-stu-id="0ad6b-125">After installing Windows 7 and IIS, when I attempt to browse to a WCF service I get the following error message: HTTP Error 404.3 – Not Found</span></span>  

 <span data-ttu-id="0ad6b-126">Tam hata iletisi:</span><span class="sxs-lookup"><span data-stu-id="0ad6b-126">The full error message is:</span></span>  
  
 <span data-ttu-id="0ad6b-127">HTTP hatası 404,3 – bulunamadı sayfası uzantı yapılandırması nedeniyle sunulamıyor.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-127">HTTP Error 404.3 – Not FoundThe page you are requesting cannot be served because of the extension configuration.</span></span> <span data-ttu-id="0ad6b-128">Sayfa bir komut dosyası ise, bir işleyici ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-128">If the page is a script, add a handler.</span></span> <span data-ttu-id="0ad6b-129">Dosya indirildiyse, bir MIME eşlemesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-129">If the file should be downloaded, add a MIME map.</span></span> <span data-ttu-id="0ad6b-130">Ayrıntılı hata InformationModule StaticFileModule.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-130">Detailed Error InformationModule StaticFileModule.</span></span>  
  
 <span data-ttu-id="0ad6b-131">Bu hata iletisi, "Windows Communication Foundation HTTP etkinleştirmesi" açıkça Denetim Masası 'nda ayarlanmamışsa oluşur.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-131">This error message occurs when "Windows Communication Foundation HTTP Activation" is not explicitly set in the Control Panel.</span></span> <span data-ttu-id="0ad6b-132">Bunu ayarlamak için, Denetim Masası 'na gidin, pencerenin sol alt köşesindeki Programlar ' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-132">To set this go to the Control Panel, click Programs in the lower left-hand corner of the window.</span></span> <span data-ttu-id="0ad6b-133">Windows özelliklerini aç veya Kapat ' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-133">Click Turn Windows features on or off.</span></span> <span data-ttu-id="0ad6b-134">Microsoft .NET Framework 3.5.1 ' i genişletin ve Windows Communication Foundation HTTP etkinleştirmesi ' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-134">Expand Microsoft .NET Framework 3.5.1 and select Windows Communication Foundation HTTP Activation.</span></span>  
  
<a name="BKMK_q1"></a>

## <a name="sometimes-i-receive-a-messagesecurityexception-on-the-second-request-if-my-client-is-idle-for-a-while-after-the-first-request-what-is-happening"></a><span data-ttu-id="0ad6b-135">Bazen, istemciniz ilk istekten sonraki bir sırada boşta kalırsa ikinci istekte bir MessageSecurityException aldım.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-135">Sometimes I receive a MessageSecurityException on the second request if my client is idle for a while after the first request.</span></span> <span data-ttu-id="0ad6b-136">Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="0ad6b-136">What is happening?</span></span>  

 <span data-ttu-id="0ad6b-137">İkinci istek birincil olarak iki nedenden dolayı başarısız olabilir: (1) oturum zaman aşımına uğradı veya (2) hizmeti barındıran Web sunucusu geri dönüştürüldü.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-137">The second request can fail primarily for two reasons: (1) the session has timed out or (2) the Web server that is hosting the service is recycled.</span></span> <span data-ttu-id="0ad6b-138">İlk durumda, oturum hizmetin zaman aşımına uğrayana kadar geçerli olur. Hizmet, hizmetin bağlamasında () belirtilen süre içinde istemciden bir istek almadığında <xref:System.ServiceModel.Channels.Binding.ReceiveTimeout%2A> , hizmet güvenlik oturumunu sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-138">In the first case, the session is valid until the service times out. When the service does not receive a request from the client within the period of time specified in the service's binding (<xref:System.ServiceModel.Channels.Binding.ReceiveTimeout%2A>), the service terminates the security session.</span></span> <span data-ttu-id="0ad6b-139">Sonraki istemci iletileri ile sonuçlanır <xref:System.ServiceModel.Security.MessageSecurityException> .</span><span class="sxs-lookup"><span data-stu-id="0ad6b-139">Subsequent client messages result in the <xref:System.ServiceModel.Security.MessageSecurityException>.</span></span> <span data-ttu-id="0ad6b-140">İstemci gelecek iletileri göndermek ya da durum bilgisi olan bir güvenlik bağlamı belirteci kullanmak için hizmetle güvenli bir oturum yeniden kurması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-140">The client must re-establish a secure session with the service to send future messages or use a stateful security context token.</span></span> <span data-ttu-id="0ad6b-141">Durum bilgisi olan güvenlik bağlamı belirteçleri Ayrıca, güvenli bir oturumun, bir Web sunucusunun geri dönüştürülmekte olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-141">Stateful security context tokens also allow a secure session to survive a Web server being recycled.</span></span> <span data-ttu-id="0ad6b-142">Güvenli bir oturumda durum bilgisi olan güvenli bağlam belirteçleri kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: güvenli bir oturum Için güvenlik bağlamı belirteci oluşturma](./feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span><span class="sxs-lookup"><span data-stu-id="0ad6b-142">For more information about using stateful secure context tokens in a secure session, see [How to: Create a Security Context Token for a Secure Session](./feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span></span> <span data-ttu-id="0ad6b-143">Alternatif olarak, güvenli oturumları devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-143">Alternatively, you can disable secure sessions.</span></span> <span data-ttu-id="0ad6b-144">[\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md)Bağlamayı kullandığınızda, `establishSecurityContext` özelliğini `false` güvenli oturumları devre dışı bırakacak şekilde ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-144">When you use the [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) binding, you can set the `establishSecurityContext` property to `false` to disable secure sessions.</span></span> <span data-ttu-id="0ad6b-145">Diğer bağlamalara yönelik güvenli oturumları devre dışı bırakmak için özel bir bağlama oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-145">To disable secure sessions for other bindings, you must create a custom binding.</span></span> <span data-ttu-id="0ad6b-146">Özel bağlama oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](./feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="0ad6b-146">For details about creating a custom binding, see [How to: Create a Custom Binding Using the SecurityBindingElement](./feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span> <span data-ttu-id="0ad6b-147">Bu seçeneklerden herhangi birini uygulamadan önce, uygulamanızın güvenlik gereksinimlerini anlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-147">Before you apply any of these options, you must understand your application's security requirements.</span></span>  
  
<a name="BKMK_q2"></a>

## <a name="my-service-starts-to-reject-new-clients-after-about-10-clients-are-interacting-with-it-what-is-happening"></a><span data-ttu-id="0ad6b-148">Hizmet, yaklaşık 10 istemci etkileşim kurduktan sonra yeni istemcileri reddedecek şekilde başlatılır.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-148">My service starts to reject new clients after about 10 clients are interacting with it.</span></span> <span data-ttu-id="0ad6b-149">Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="0ad6b-149">What is happening?</span></span>  

 <span data-ttu-id="0ad6b-150">Varsayılan olarak, hizmetlerde yalnızca 10 eşzamanlı oturum olabilir.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-150">By default, services can have only 10 concurrent sessions.</span></span> <span data-ttu-id="0ad6b-151">Bu nedenle, hizmet bağlamaları oturumlar kullanıyorsa, hizmet bu sayıya ulaşana kadar yeni istemci bağlantılarını kabul eder ve ardından geçerli oturumlardan biri sonlanana kadar yeni istemci bağlantılarını reddeder.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-151">Therefore, if the service bindings use sessions, the service accepts new client connections until it reaches that number, after which it refuses new client connections until one of the current sessions ends.</span></span> <span data-ttu-id="0ad6b-152">Birkaç yolla daha fazla istemci destekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-152">You can support more clients in a number of ways.</span></span> <span data-ttu-id="0ad6b-153">Hizmetiniz oturum gerektirmiyorsa, oturumsuz bağlama kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-153">If your service does not require sessions, do not use a sessionful binding.</span></span> <span data-ttu-id="0ad6b-154">(Daha fazla bilgi için bkz. [oturumları kullanma](using-sessions.md).) Diğer bir seçenek de, özelliğin değerini, <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A> sizin için uygun olan sayı olarak değiştirerek oturum sınırını artırmaya yönelik bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-154">(For more information, see [Using Sessions](using-sessions.md).) Another option is to increase the session limit by changing the value of the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A> property to the number appropriate to your circumstance.</span></span>  
  
<a name="BKMK_q3"></a>

## <a name="can-i-load-my-service-configuration-from-somewhere-other-than-the-wcf-applications-configuration-file"></a><span data-ttu-id="0ad6b-155">Hizmet yapılandırmadan WCF uygulamasının yapılandırma dosyası dışında bir yerde yükleyebilir miyim?</span><span class="sxs-lookup"><span data-stu-id="0ad6b-155">Can I load my service configuration from somewhere other than the WCF application’s configuration file?</span></span>  

 <span data-ttu-id="0ad6b-156">Evet, ancak, <xref:System.ServiceModel.ServiceHost> yöntemini geçersiz kılan özel bir sınıf oluşturmanız gerekir <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> .</span><span class="sxs-lookup"><span data-stu-id="0ad6b-156">Yes, however, you have to create a custom <xref:System.ServiceModel.ServiceHost> class that overrides the <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> method.</span></span> <span data-ttu-id="0ad6b-157">Bu yöntemin içinde, önce yapılandırmayı yüklemek için temel çağırabilirsiniz (Standart yapılandırma bilgilerini de yüklemek istiyorsanız), ancak yapılandırma yükleme sistemini tamamen değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-157">Inside that method, you can call the base to load configuration first (if you want to load the standard configuration information as well) but you can also entirely replace the configuration loading system.</span></span> <span data-ttu-id="0ad6b-158">Yapılandırma dosyasından uygulama yapılandırma dosyasından farklı bir yapılandırma yüklemek istiyorsanız, yapılandırma dosyasını kendiniz ayrıştırmalısınız ve yapılandırmayı yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-158">If you want to load configuration from a configuration file that is different from the application configuration file, you must parse the configuration file yourself and load the configuration.</span></span>  
  
 <span data-ttu-id="0ad6b-159">Aşağıdaki kod örneği, yönteminin nasıl geçersiz kılınacağını <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> ve bir uç noktanın doğrudan nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-159">The following code example shows how to override the <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> method and directly configure an endpoint.</span></span>  
  
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

## <a name="my-service-and-client-work-great-but-i-cant-get-them-to-work-when-the-client-is-on-another-computer-whats-happening"></a><span data-ttu-id="0ad6b-160">Kullandığım hizmet ve istemci harika çalışıyor, ancak istemci başka bir bilgisayarda olduğunda bunları çalışmayacak mıyım?</span><span class="sxs-lookup"><span data-stu-id="0ad6b-160">My service and client work great, but I can’t get them to work when the client is on another computer?</span></span> <span data-ttu-id="0ad6b-161">Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="0ad6b-161">What’s happening?</span></span>  

 <span data-ttu-id="0ad6b-162">Özel duruma bağlı olarak birkaç sorun olabilir:</span><span class="sxs-lookup"><span data-stu-id="0ad6b-162">Depending upon the exception, there may be several issues:</span></span>  
  
- <span data-ttu-id="0ad6b-163">İstemci uç noktası adreslerini "localhost" değil ana bilgisayar adıyla değiştirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-163">You might need to change the client endpoint addresses to the host name and not "localhost".</span></span>  
  
- <span data-ttu-id="0ad6b-164">Bağlantı noktasını uygulamaya açmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-164">You might need to open the port to the application.</span></span> <span data-ttu-id="0ad6b-165">Ayrıntılar için bkz. SDK örneklerinden [güvenlik duvarı yönergeleri](./samples/firewall-instructions.md) .</span><span class="sxs-lookup"><span data-stu-id="0ad6b-165">For details, see [Firewall Instructions](./samples/firewall-instructions.md) from the SDK samples.</span></span>  
  
- <span data-ttu-id="0ad6b-166">Olası diğer sorunlar için [Windows Communication Foundation Örnekleri çalıştıran](./samples/running-the-samples.md)örnekler konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-166">For other possible issues, see the samples topic [Running the Windows Communication Foundation Samples](./samples/running-the-samples.md).</span></span>  
  
- <span data-ttu-id="0ad6b-167">İstemciniz Windows kimlik bilgilerini kullanıyorsa ve özel durum bir ise <xref:System.ServiceModel.Security.SecurityNegotiationException> , Kerberos 'u aşağıdaki şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-167">If your client is using Windows credentials and the exception is a <xref:System.ServiceModel.Security.SecurityNegotiationException>, configure Kerberos as follows.</span></span>  
  
    1. <span data-ttu-id="0ad6b-168">Kimlik bilgilerini istemcinin App.config dosyasındaki uç nokta öğesine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0ad6b-168">Add the identity credentials to the endpoint element in the client’s App.config file:</span></span>  
  
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
  
    2. <span data-ttu-id="0ad6b-169">Şirket içinde barındırılan hizmeti sistem veya NetworkService hesabı altında çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-169">Run the self-hosted service under the System or NetworkService account.</span></span> <span data-ttu-id="0ad6b-170">Sistem hesabı altında bir komut penceresi oluşturmak için bu komutu çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0ad6b-170">You can run this command to create a command window under the System account:</span></span>  
  
        ```console
        at 12:36 /interactive "cmd.exe"  
        ```  
  
    3. <span data-ttu-id="0ad6b-171">Hizmeti, varsayılan olarak hizmet asıl adı (SPN) hesabını kullanan Internet Information Services (IIS) altında barındırın.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-171">Host the service under Internet Information Services (IIS), which, by default, uses the service principal name (SPN) account.</span></span>  
  
    4. <span data-ttu-id="0ad6b-172">SetSPN kullanarak etki alanı ile yeni bir SPN kaydettirin.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-172">Register a new SPN with the domain using SetSPN.</span></span> <span data-ttu-id="0ad6b-173">Bunu yapmak için bir etki alanı yöneticisi olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-173">You need to be a domain administrator in order to do this.</span></span>  
  
 <span data-ttu-id="0ad6b-174">Kerberos protokolü hakkında daha fazla bilgi için bkz. [WCF 'de kullanılan güvenlik kavramları](./feature-details/security-concepts-used-in-wcf.md) ve:</span><span class="sxs-lookup"><span data-stu-id="0ad6b-174">For more information about the Kerberos protocol, see [Security Concepts Used in WCF](./feature-details/security-concepts-used-in-wcf.md) and:</span></span>  
  
- [<span data-ttu-id="0ad6b-175">Windows Kimlik Doğrulama Hatalarını Ayıklama</span><span class="sxs-lookup"><span data-stu-id="0ad6b-175">Debugging Windows Authentication Errors</span></span>](./feature-details/debugging-windows-authentication-errors.md)  
  
- <span data-ttu-id="0ad6b-176">[Http.syskullanarak Kerberos hizmet sorumlusu adlarını kaydetme ](/previous-versions/sql/sql-server-2008-r2/ms178119(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="0ad6b-176">[Registering Kerberos Service Principal Names by Using Http.sys](/previous-versions/sql/sql-server-2008-r2/ms178119(v=sql.105))</span></span>  
  
- <span data-ttu-id="0ad6b-177">[Açıklanan Kerberos](/previous-versions/windows/it-pro/windows-2000-server/bb742516(v=technet.10))</span><span class="sxs-lookup"><span data-stu-id="0ad6b-177">[Kerberos Explained](/previous-versions/windows/it-pro/windows-2000-server/bb742516(v=technet.10))</span></span>  
  
<a name="BKMK_q5"></a>

## <a name="when-i-throw-a-faultexceptionexception-where-the-type-is-an-exception-i-always-receive-a-general-faultexception-type-on-the-client-and-not-the-generic-type-whats-happening"></a><span data-ttu-id="0ad6b-178">\<Exception>Türün bir özel durum olduğu bir FaultException oluşturdum, genel tür değil istemciye her zaman genel bir FaultException türü aldım.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-178">When I throw a FaultException\<Exception> where the type is an exception, I always receive a general FaultException type on the client and not the generic type.</span></span> <span data-ttu-id="0ad6b-179">Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="0ad6b-179">What’s happening?</span></span>  

 <span data-ttu-id="0ad6b-180">Kendi özel hata veri türünü oluşturmanız ve bunu hata sözleşmenizin ayrıntı türü olarak bildirmeniz önemle tavsiye edilir.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-180">It is highly recommended that you create your own custom error data type and declare that as the detail type in your fault contract.</span></span> <span data-ttu-id="0ad6b-181">Nedeni sistem tarafından sağlanmış özel durum türlerini kullanmaktır:</span><span class="sxs-lookup"><span data-stu-id="0ad6b-181">The reason is that using system-provided exception types:</span></span>  
  
- <span data-ttu-id="0ad6b-182">Hizmet odaklı uygulamaların en büyük güçlerinden birini kaldıran bir tür bağımlılığı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-182">Creates a type dependency that removes one of the biggest strengths of service-oriented applications.</span></span>  
  
- <span data-ttu-id="0ad6b-183">Standart bir şekilde özel durum serileştirilme bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-183">Cannot depend upon exceptions serializing in a standard way.</span></span> <span data-ttu-id="0ad6b-184">Bazıları — örneğin <xref:System.Security.SecurityException> , hiçbir seri hale getirilebilir olamaz.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-184">Some—like <xref:System.Security.SecurityException>—may not be serializable at all.</span></span>  
  
- <span data-ttu-id="0ad6b-185">İstemcilere iç uygulama ayrıntılarını sunar.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-185">Exposes internal implementation details to clients.</span></span> <span data-ttu-id="0ad6b-186">Daha fazla bilgi için bkz. [anlaşmalar ve hizmetlerde hataları belirtme ve işleme](specifying-and-handling-faults-in-contracts-and-services.md).</span><span class="sxs-lookup"><span data-stu-id="0ad6b-186">For more information, see [Specifying and Handling Faults in Contracts and Services](specifying-and-handling-faults-in-contracts-and-services.md).</span></span>  
  
 <span data-ttu-id="0ad6b-187">Ancak bir uygulamada hata ayıklaması yapıyorsanız, özel durum bilgilerini seri hale getirebilirsiniz ve sınıfını kullanarak istemciye döndürebilirsiniz <xref:System.ServiceModel.Description.ServiceDebugBehavior> .</span><span class="sxs-lookup"><span data-stu-id="0ad6b-187">If you are debugging an application, however, you can serialize exception information and return it to the client by using the <xref:System.ServiceModel.Description.ServiceDebugBehavior> class.</span></span>  
  
<a name="BKMK_q6"></a>

## <a name="it-seems-like-one-way-and-request-reply-operations-return-at-roughly-the-same-speed-when-the-reply-contains-no-data-whats-happening"></a><span data-ttu-id="0ad6b-188">Yanıt bir veri içerdiğinde tek yönlü ve istek-yanıt işlemleri kabaca aynı hızda döndürülür.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-188">It seems like one-way and request-reply operations return at roughly the same speed when the reply contains no data.</span></span> <span data-ttu-id="0ad6b-189">Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="0ad6b-189">What's happening?</span></span>  

 <span data-ttu-id="0ad6b-190">Bir işlemin tek bir şekilde belirtilmesi, yalnızca işlem sözleşmesinin bir giriş iletisini kabul ettiği ve bir çıkış iletisi döndürmediği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-190">Specifying that an operation is one way means only that the operation contract accepts an input message and does not return an output message.</span></span> <span data-ttu-id="0ad6b-191">WCF 'de, giden veriler kabloya yazıldığında veya bir özel durum oluştuğunda tüm istemci etkinleştirmeleri döndürülür.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-191">In WCF, all client invocations return when the outbound data has been written to the wire or an exception is thrown.</span></span> <span data-ttu-id="0ad6b-192">Tek yönlü işlemler aynı şekilde çalışır ve hizmet, ağdaki verileri kabul etmek üzere hazırlanmamışsa, hizmet bulunamıyorsa veya engellenmiyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-192">One-way operations work the same way, and they can throw if the service cannot be located or block if the service is not prepared to accept the data from the network.</span></span> <span data-ttu-id="0ad6b-193">Genellikle WCF 'de, bu, istemciye istek yanıtlamadan daha hızlı dönen tek yönlü çağrılara neden olur; Ancak, giden verilerin ağ üzerinden gönderilmesini yavaşlatan herhangi bir koşul, tek yönlü işlemlerin yanı sıra istek-yanıt işlemlerini yavaşlatır.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-193">Typically in WCF, this results in one-way calls returning to the client more quickly than request-reply; but any condition that slows the sending of the outbound data over the network slows one-way operations as well as request-reply operations.</span></span> <span data-ttu-id="0ad6b-194">Daha fazla bilgi için bkz. [tek yönlü hizmetler](./feature-details/one-way-services.md) ve [WCF Istemcisi kullanarak hizmetlere erişme](./feature-details/accessing-services-using-a-client.md).</span><span class="sxs-lookup"><span data-stu-id="0ad6b-194">For more information, see [One-Way Services](./feature-details/one-way-services.md) and [Accessing Services Using a WCF Client](./feature-details/accessing-services-using-a-client.md).</span></span>  
  
<a name="BKMK_q77"></a>

## <a name="im-using-an-x509-certificate-with-my-service-and-i-get-a-systemsecuritycryptographycryptographicexception-whats-happening"></a><span data-ttu-id="0ad6b-195">Kullandığım bir X. 509.440 sertifikası kullanıyorum ve bir System. Security. Cryptography. CryptographicException aldım.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-195">I’m using an X.509 certificate with my service and I get a System.Security.Cryptography.CryptographicException.</span></span> <span data-ttu-id="0ad6b-196">Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="0ad6b-196">What’s happening?</span></span>  

 <span data-ttu-id="0ad6b-197">Bu, genellikle IIS çalışan işleminin çalıştırıldığı Kullanıcı hesabı değiştirildikten sonra oluşur.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-197">This commonly occurs after changing the user account under which the IIS worker process runs.</span></span> <span data-ttu-id="0ad6b-198">Örneğin, Windows XP 'de, Aspnet_wp.exe çalıştıran varsayılan kullanıcı hesabını ASPNET 'den özel bir kullanıcı hesabına değiştirirseniz, bu hatayı görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-198">For example, in Windows XP, if you change the default user account that the Aspnet_wp.exe runs under from ASPNET to a custom user account, you may see this error.</span></span> <span data-ttu-id="0ad6b-199">Özel anahtar kullanılıyorsa, onu kullanan işlemin bu anahtarı depolayan dosyaya erişmek için gerekli izinlere sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-199">If using a private key, the process that uses it will need to have permissions to access the file storing that key.</span></span>  
  
 <span data-ttu-id="0ad6b-200">Bu durumda, özel anahtarı içeren dosya için işlem hesabına yönelik okuma erişim ayrıcalıklarına sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-200">If this is the case, you must give read access privileges to the process's account for the file containing the private key.</span></span> <span data-ttu-id="0ad6b-201">Örneğin, IIS çalışan işlemi Bob hesabı altında çalışıyorsa, Bob 'un özel anahtarı içeren dosyaya okuma erişimi vermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-201">For example, if the IIS worker process is running under the Bob account, then you will need to give Bob read access to the file containing the private key.</span></span>  
  
 <span data-ttu-id="0ad6b-202">Belirli bir X. 509.952 sertifikası için özel anahtarı içeren dosyaya doğru Kullanıcı hesabına erişim verme hakkında daha fazla bilgi için bkz. [nasıl yapılır: X. 509.440 SERTIFIKALARıNı WCF 'ye erişilebilir hale getirme](./feature-details/how-to-make-x-509-certificates-accessible-to-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="0ad6b-202">For more information about how to give the correct user account access to the file that contains the private key for a specific X.509 certificate, see [How to: Make X.509 Certificates Accessible to WCF](./feature-details/how-to-make-x-509-certificates-accessible-to-wcf.md).</span></span>  
  
<a name="BKMK_q88"></a>

## <a name="i-changed-the-first-parameter-of-an-operation-from-uppercase-to-lowercase-now-my-client-throws-an-exception-whats-happening"></a><span data-ttu-id="0ad6b-203">Bir işlemin ilk parametresini büyük harften küçük harfe kadar değiştirdim; Artık istemcim bir özel durum oluşturuyor.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-203">I changed the first parameter of an operation from uppercase to lowercase; now my client throws an exception.</span></span> <span data-ttu-id="0ad6b-204">Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="0ad6b-204">What's happening?</span></span>  

 <span data-ttu-id="0ad6b-205">İşlem imzasında parametre adlarının değerleri sözleşmenin bir parçasıdır ve büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-205">The values of the parameter names in the operation signature are part of the contract and are case-sensitive.</span></span> <span data-ttu-id="0ad6b-206"><xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>Yerel parametre adı ile istemci uygulamaları için işlemi açıklayan meta veriler arasında ayrım yapmanız gerektiğinde özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-206">Use the <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType> attribute when you need to distinguish between the local parameter name and the metadata that describes the operation for client applications.</span></span>  
  
<a name="BKMK_q99"></a>

## <a name="im-using-one-of-my-tracing-tools-and-i-get-an-endpointnotfoundexception-whats-happening"></a><span data-ttu-id="0ad6b-207">İzleme araçlarından birini kullanıyorum ve bir EndpointNotFoundException aldım.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-207">I’m using one of my tracing tools and I get an EndpointNotFoundException.</span></span> <span data-ttu-id="0ad6b-208">Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="0ad6b-208">What’s happening?</span></span>  

 <span data-ttu-id="0ad6b-209">Sistem tarafından sağlanmış WCF izleme mekanizması olmayan bir izleme aracı kullanıyorsanız ve bir <xref:System.ServiceModel.EndpointNotFoundException> adres filtresi uyumsuzluğu olduğunu belirten bir ileti alırsanız, <xref:System.ServiceModel.Description.ClientViaBehavior> iletileri izleme yardımcı programına yönlendirmek için sınıfını kullanmanız ve yardımcı programın bu iletileri hizmet adresine yönlendirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-209">If you are using a tracing tool that is not the system-provided WCF tracing mechanism and you receive an <xref:System.ServiceModel.EndpointNotFoundException> that indicates that there was an address filter mismatch, you need to use the <xref:System.ServiceModel.Description.ClientViaBehavior> class to direct the messages to the tracing utility and have the utility redirect those messages to the service address.</span></span> <span data-ttu-id="0ad6b-210">Sınıfı, adres üst <xref:System.ServiceModel.Description.ClientViaBehavior> `Via` bilgisi tarafından belirtilen bir sonraki ağ adresini Ultimate alıcısından ayrı olarak belirtmek için adres üst bilgisini değiştirir `To` .</span><span class="sxs-lookup"><span data-stu-id="0ad6b-210">The <xref:System.ServiceModel.Description.ClientViaBehavior> class alters the `Via` addressing header to specify the next network address separately from the ultimate receiver, indicated by the `To` addressing header.</span></span> <span data-ttu-id="0ad6b-211">Ancak bunu yaparken, değeri oluşturmak için kullanılan uç nokta adresini değiştirmeyin `To` .</span><span class="sxs-lookup"><span data-stu-id="0ad6b-211">When doing this, however, do not change the endpoint address, which is used to establish the `To` value.</span></span>  
  
 <span data-ttu-id="0ad6b-212">Aşağıdaki kod örneği bir örnek istemci yapılandırma dosyası gösterir.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-212">The following code example shows an example client configuration file.</span></span>  
  
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

## <a name="what-is-the-base-address-how-does-it-relate-to-an-endpoint-address"></a><span data-ttu-id="0ad6b-213">Temel adres nedir?</span><span class="sxs-lookup"><span data-stu-id="0ad6b-213">What is the base address?</span></span> <span data-ttu-id="0ad6b-214">Bir uç nokta adresiyle nasıl ilişki vardır?</span><span class="sxs-lookup"><span data-stu-id="0ad6b-214">How does it relate to an endpoint address?</span></span>  

 <span data-ttu-id="0ad6b-215">Temel adres, bir sınıfın kök adresidir <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="0ad6b-215">A base address is the root address for a <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="0ad6b-216">Varsayılan olarak, <xref:System.ServiceModel.Description.ServiceMetadataBehavior> hizmet yapılandırmanıza bir sınıf eklerseniz, ana bilgisayar yayımladığı tüm uç noktalar Için Web Hizmetleri Açıklama Dili (wsdl), http taban adresinden ve meta veri davranışına ve "? wsdl" ile ilgili herhangi bir göreli adresle alınır.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-216">By default, if you add a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class into your service configuration, the Web Services Description Language (WSDL) for all endpoints the host publishes are retrieved from the HTTP base address, plus any relative address provided to the metadata behavior, plus "?wsdl".</span></span> <span data-ttu-id="0ad6b-217">ASP.NET ve IIS hakkında bilgi sahibiyseniz, taban adresi sanal dizine eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-217">If you are familiar with ASP.NET and IIS, the base address is equivalent to the virtual directory.</span></span>  
  
## <a name="sharing-a-port-between-a-service-endpoint-and-a-mex-endpoint-using-the-nettcpbinding"></a><span data-ttu-id="0ad6b-218">NetTcpBinding kullanarak bir hizmet uç noktası ve bir MEX uç noktası arasında bağlantı noktası paylaşma</span><span class="sxs-lookup"><span data-stu-id="0ad6b-218">Sharing a port between a service endpoint and a mex endpoint using the NetTcpBinding</span></span>  

 <span data-ttu-id="0ad6b-219">Bir hizmetin temel adresini net. TCP:/sunucum: 8080/hizmetim olarak belirtirseniz ve aşağıdaki uç noktaları eklemek için:</span><span class="sxs-lookup"><span data-stu-id="0ad6b-219">If you specify the base address for a service as net.tcp://MyServer:8080/MyService and add the following endpoints:</span></span>  
  
```xml  
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
 <span data-ttu-id="0ad6b-220">Ve NetTcpBinding ayarlarından birini aşağıdaki yapılandırma kod parçacığında gösterildiği gibi değiştirirseniz:</span><span class="sxs-lookup"><span data-stu-id="0ad6b-220">And if you modify one of the NetTcpBinding settings as shown in the following configuration snippet:</span></span>  
  
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
  
 <span data-ttu-id="0ad6b-221">Şu şekilde bir hata görürsünüz: Işlenmeyen özel durum: System. ServiceModel. Addressalreadınuseexception: IP uç noktası 0.0.0.0:9000 üzerinde zaten bir dinleyici var: aşağıdaki yapılandırma kod parçacığında gösterildiği gibi, MEX uç noktası için farklı bir bağlantı noktası ile tam URL belirterek bu hataya geçici bir çözüm bulabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0ad6b-221">You will see an error like the following: Unhandled Exception: System.ServiceModel.AddressAlreadyInUseException: There is already a listener on IP endpoint 0.0.0.0:9000 You can work around this error by specifying a fully qualified URL with a different port for the MEX endpoint as shown in the following configuration snippet:</span></span>  
  
```xml
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="net.tcp://localhost:9001/servicemodelsamples/mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
<a name="BK_MK99"></a>

## <a name="when-calling-a-wcf-web-http-application-from-a-wcf-soap-application-the-service-returns-the-following-error-405-method-not-allowed"></a><span data-ttu-id="0ad6b-222">WCF SOAP uygulamasından bir WCF Web HTTP uygulaması çağrılırken hizmet şu hatayı döndürür: 405 yöntemine Izin verilmiyor</span><span class="sxs-lookup"><span data-stu-id="0ad6b-222">When calling a WCF Web HTTP application from a WCF SOAP application the service returns the following error: 405 Method Not Allowed</span></span>  

 <span data-ttu-id="0ad6b-223">WCF Web HTTP uygulamasını (ve kullanan bir hizmet <xref:System.ServiceModel.WebHttpBinding> <xref:System.ServiceModel.Description.WebHttpBehavior> ) bir WCF hizmetinden çağırmak aşağıdaki özel durumu oluşturabilir: ``Unhandled Exception: System.ServiceModel.FaultException`1[System.ServiceModel.ExceptionDetail]: The remote server returned an unexpected response: (405) Method Not Allowed.`` Bu özel durum, WCF giden gelen ' i geçersiz yazmasından kaynaklanır <xref:System.ServiceModel.OperationContext> <xref:System.ServiceModel.OperationContext> .</span><span class="sxs-lookup"><span data-stu-id="0ad6b-223">Calling a WCF Web HTTP application (a service that uses the <xref:System.ServiceModel.WebHttpBinding> and <xref:System.ServiceModel.Description.WebHttpBehavior>) from a WCF service may generate the following exception: ``Unhandled Exception: System.ServiceModel.FaultException`1[System.ServiceModel.ExceptionDetail]: The remote server returned an unexpected response: (405) Method Not Allowed.`` This exception occurs because WCF overwrites the outgoing <xref:System.ServiceModel.OperationContext> with the incoming <xref:System.ServiceModel.OperationContext>.</span></span> <span data-ttu-id="0ad6b-224">Bu sorunu çözmek için <xref:System.ServiceModel.OperationContextScope> WCF Web http hizmeti işlemi içinde bir oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-224">To solve this problem, create an <xref:System.ServiceModel.OperationContextScope> within the WCF Web HTTP service operation.</span></span> <span data-ttu-id="0ad6b-225">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="0ad6b-225">For example:</span></span>  
  
```csharp
public string Echo(string input)  
{  
    using (new OperationContextScope(this.InnerChannel))  
    {  
        return base.Channel.Echo(input);  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="0ad6b-226">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ad6b-226">See also</span></span>

- [<span data-ttu-id="0ad6b-227">Windows Kimlik Doğrulama Hatalarını Ayıklama</span><span class="sxs-lookup"><span data-stu-id="0ad6b-227">Debugging Windows Authentication Errors</span></span>](./feature-details/debugging-windows-authentication-errors.md)
