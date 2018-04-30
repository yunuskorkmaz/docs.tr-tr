---
title: WCF Sorun Giderme Hızlı Başlangıç
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF [WCF], troubleshooting
- Windows Communication Foundation [WCF], troubleshooting
ms.assetid: a9ea7a53-f31a-46eb-806e-898e465a4992
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 24ca6899e6ac2bb316c0543932d70abc13626aa2
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="wcf-troubleshooting-quickstart"></a><span data-ttu-id="52664-102">WCF Sorun Giderme Hızlı Başlangıç</span><span class="sxs-lookup"><span data-stu-id="52664-102">WCF Troubleshooting Quickstart</span></span>
<span data-ttu-id="52664-103">Bu konuda müşteriler içine geliştirme WCF istemcileri ve Hizmetleri sırasında çalıştırdığınız bilinen sorunlar sayısını listeler.</span><span class="sxs-lookup"><span data-stu-id="52664-103">This topic lists a number of known issues customers have run into while developing WCF clients and services.</span></span> <span data-ttu-id="52664-104">İçine çalıştırdığınız sorunu bu listede değilse, hizmetiniz için izleme yapılandırma öneririz.</span><span class="sxs-lookup"><span data-stu-id="52664-104">If the issue you are running into is not in this list, we recommend you configure tracing for your service.</span></span> <span data-ttu-id="52664-105">Bu bir izleme dosyası oluşturur izleme dosyası Görüntüleyici ile birlikte görüntülemek ve özel durumlar hakkında ayrıntılı bilgi almak hizmet içinde gerçekleşen.</span><span class="sxs-lookup"><span data-stu-id="52664-105">This will generate a trace file that you can view with the trace file viewer and get detailed information about exceptions that may be occurring within the service.</span></span> <span data-ttu-id="52664-106">İzlemeyi yapılandırma hakkında daha fazla bilgi için bkz: [yapılandırma izleme](../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="52664-106">For more information on configuring tracing, see: [Configuring Tracing](../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md).</span></span> <span data-ttu-id="52664-107">İzleme dosyası Görüntüleyici hakkında daha fazla bilgi için bkz: [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="52664-107">For more information on the trace file viewer, see: [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span>  
  
1.  [<span data-ttu-id="52664-108">Bir WCF hizmetine göz atmak çalıştığınızda Windows 7 ve IIS yükledikten sonra aşağıdaki hata iletisi alıyorum: HTTP Hata 404.3 – bulunamadı</span><span class="sxs-lookup"><span data-stu-id="52664-108">After installing Windows 7 and IIS, when I attempt to browse to a WCF service I get the following error message: HTTP Error 404.3 – Not Found</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#bkmk_0)  
  
     <span data-ttu-id="52664-109">HTTP Hatası 404.3 – değil isteyen FoundThe sayfa uzantı yapılandırması nedeniyle sunulamıyor.</span><span class="sxs-lookup"><span data-stu-id="52664-109">HTTP Error 404.3 – Not FoundThe page you are requesting cannot be served because of the extension configuration.</span></span> <span data-ttu-id="52664-110">Sayfa bir komut dosyası ise, bir işleyici ekleyin.</span><span class="sxs-lookup"><span data-stu-id="52664-110">If the page is a script, add a handler.</span></span> <span data-ttu-id="52664-111">Dosyanın indirilmesi gerekiyorsa, bir MIME eşlemesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="52664-111">If the file should be downloaded, add a MIME map.</span></span> <span data-ttu-id="52664-112">Ayrıntılı hata InformationModule StaticFileModule.</span><span class="sxs-lookup"><span data-stu-id="52664-112">Detailed Error InformationModule StaticFileModule.</span></span>  
  
2.  [<span data-ttu-id="52664-113">My istemci bir süre sonra ilk istek için boşta kalırsa bazen MessageSecurityException ikinci isteğinde alıyorum. Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="52664-113">Sometimes I receive a MessageSecurityException on the second request if my client is idle for a while after the first request. What is happening?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q1)  
  
3.  [<span data-ttu-id="52664-114">Yaklaşık 10 istemcileri ile etkileşim sonra yeni istemciler reddetmeye My hizmetini başlatır. Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="52664-114">My service starts to reject new clients after about 10 clients are interacting with it. What is happening?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q2)  
  
4.  [<span data-ttu-id="52664-115">Hizmet yapılandırma sıralandığından WCF uygulamanın yapılandırma dosyasında diğer gelen yükleyebilir?</span><span class="sxs-lookup"><span data-stu-id="52664-115">Can I load my service configuration from somewhere other than the WCF application’s configuration file?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q3)  
  
5.  [<span data-ttu-id="52664-116">Hizmetim ve istemci iş mükemmel, ancak bunları istemci başka bir bilgisayarda olduğunda iş alınamıyor? Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="52664-116">My service and client work great, but I can’t get them to work when the client is on another computer? What’s happening?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q4)  
  
6.  [<span data-ttu-id="52664-117">Bir FaultException ı throw zaman\<özel durum > türü özel bir durum olduğunda, her zaman istemci üzerinde genel bir FaultException tür ve genel tür alıyorum. Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="52664-117">When I throw a FaultException\<Exception> where the type is an exception, I always receive a general FaultException type on the client and not the generic type. What’s happening?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q5)  
  
7.  [<span data-ttu-id="52664-118">Gibi tek yönlü görünür ve yanıt hiçbir veri içerdiğinde istek-yanıt işlemleri kabaca aynı hızda döndürür. Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="52664-118">It seems like one-way and request-reply operations return at roughly the same speed when the reply contains no data. What's happening?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q6)  
  
8.  [<span data-ttu-id="52664-119">Bir X.509 sertifikası ile Hizmetim kullanıyorum ve bir System.Security.Cryptography.CryptographicException alın. Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="52664-119">I’m using an X.509 certificate with my service and I get a System.Security.Cryptography.CryptographicException. What’s happening?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q77)  
  
9. [<span data-ttu-id="52664-120">Bir işlemin ilk parametre gelen büyük değiştirdim küçük harf için; Şimdi my istemcisi bir özel durum oluşturur. Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="52664-120">I changed the first parameter of an operation from uppercase to lowercase; now my client throws an exception. What's happening?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q88)  
  
10. [<span data-ttu-id="52664-121">My izleme araçlarından birini kullanıyorum ve bir EndpointNotFoundException alın. Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="52664-121">I’m using one of my tracing tools and I get an EndpointNotFoundException. What’s happening?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q99)  
  
11. [<span data-ttu-id="52664-122">WCF Web HTTP uygulama hizmeti bir WCF SOAP uygulamasından çağırma döndüğünde aşağıdaki hata: 405 yöntemini verilmiyor</span><span class="sxs-lookup"><span data-stu-id="52664-122">When calling a WCF Web HTTP application from a WCF SOAP application the service returns the following error: 405 Method Not Allowed</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BK_MK99)  
  
 [<span data-ttu-id="52664-123">Temel adres nedir? Bu bir uç nokta adresine nasıl ilişkilidir?</span><span class="sxs-lookup"><span data-stu-id="52664-123">What is the base address? How does it relate to an endpoint address?</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q10)  
  
<a name="bkmk_0"></a>   
## <a name="after-installing-windows-7-and-iis-when-i-attempt-to-browse-to-a-wcf-service-i-get-the-following-error-message-http-error-4043--not-found"></a><span data-ttu-id="52664-124">Bir WCF hizmetine göz atmak çalıştığınızda Windows 7 ve IIS yükledikten sonra aşağıdaki hata iletisi alıyorum: HTTP Hata 404.3 – bulunamadı</span><span class="sxs-lookup"><span data-stu-id="52664-124">After installing Windows 7 and IIS, when I attempt to browse to a WCF service I get the following error message: HTTP Error 404.3 – Not Found</span></span>  
 <span data-ttu-id="52664-125">Tam hata iletisi şudur:</span><span class="sxs-lookup"><span data-stu-id="52664-125">The full error message is:</span></span>  
  
 <span data-ttu-id="52664-126">HTTP Hatası 404.3 – değil isteyen FoundThe sayfa uzantı yapılandırması nedeniyle sunulamıyor.</span><span class="sxs-lookup"><span data-stu-id="52664-126">HTTP Error 404.3 – Not FoundThe page you are requesting cannot be served because of the extension configuration.</span></span> <span data-ttu-id="52664-127">Sayfa bir komut dosyası ise, bir işleyici ekleyin.</span><span class="sxs-lookup"><span data-stu-id="52664-127">If the page is a script, add a handler.</span></span> <span data-ttu-id="52664-128">Dosyanın indirilmesi gerekiyorsa, bir MIME eşlemesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="52664-128">If the file should be downloaded, add a MIME map.</span></span> <span data-ttu-id="52664-129">Ayrıntılı hata InformationModule StaticFileModule.</span><span class="sxs-lookup"><span data-stu-id="52664-129">Detailed Error InformationModule StaticFileModule.</span></span>  
  
 <span data-ttu-id="52664-130">Bu hata iletisi, "Windows Communication Foundation HTTP etkinleştirme" Denetim Masası'nda açıkça ayarlanmadı oluşur.</span><span class="sxs-lookup"><span data-stu-id="52664-130">This error message occurs when "Windows Communication Foundation HTTP Activation" is not explicitly set in the Control Panel.</span></span> <span data-ttu-id="52664-131">Denetim Masası'na bu Git ayarlamak için pencerenin alt sol alt köşede Programlar'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="52664-131">To set this go to the Control Panel, click Programs in the lower left hand corner of the window.</span></span> <span data-ttu-id="52664-132">Windows özelliklerini açmak veya kapatmak'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="52664-132">Click Turn Windows features on or off.</span></span> <span data-ttu-id="52664-133">Microsoft .NET Framework 3.5.1 genişletin ve Windows Communication Foundation HTTP Etkinleştirmesi'ni seçin.</span><span class="sxs-lookup"><span data-stu-id="52664-133">Expand Microsoft .NET Framework 3.5.1 and select Windows Communication Foundation HTTP Activation.</span></span>  
  
<a name="BKMK_q1"></a>   
## <a name="sometimes-i-receive-a-messagesecurityexception-on-the-second-request-if-my-client-is-idle-for-a-while-after-the-first-request-what-is-happening"></a><span data-ttu-id="52664-134">My istemci bir süre sonra ilk istek için boşta kalırsa bazen MessageSecurityException ikinci isteğinde alıyorum.</span><span class="sxs-lookup"><span data-stu-id="52664-134">Sometimes I receive a MessageSecurityException on the second request if my client is idle for a while after the first request.</span></span> <span data-ttu-id="52664-135">Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="52664-135">What is happening?</span></span>  
 <span data-ttu-id="52664-136">İkinci bir istek temelde iki nedenden dolayı başarısız olabilir: (1 oturum zaman aşımına uğradı veya barındırma hizmeti (2 Web sunucusu dönüştürülmeden.</span><span class="sxs-lookup"><span data-stu-id="52664-136">The second request can fail primarily for two reasons: (1) the session has timed out or (2) the Web server that is hosting the service is recycled.</span></span> <span data-ttu-id="52664-137">İlk durumda hizmeti zaman aşımına uğrayana kadar oturum geçerli değil. Ne zaman hizmeti almaz bir istek istemciden hizmetin bağlamada belirtilen süre içinde (<xref:System.ServiceModel.Channels.Binding.ReceiveTimeout%2A>), hizmet güvenlik oturumu sona erer.</span><span class="sxs-lookup"><span data-stu-id="52664-137">In the first case, the session is valid until the service times out. When the service does not receive a request from the client within the period of time specified in the service's binding (<xref:System.ServiceModel.Channels.Binding.ReceiveTimeout%2A>), the service terminates the security session.</span></span> <span data-ttu-id="52664-138">Sonraki istemci iletileri neden <xref:System.ServiceModel.Security.MessageSecurityException>.</span><span class="sxs-lookup"><span data-stu-id="52664-138">Subsequent client messages result in the <xref:System.ServiceModel.Security.MessageSecurityException>.</span></span> <span data-ttu-id="52664-139">İstemci, gelecekteki iletileri göndermek veya bir durum bilgisi olan güvenlik bağlamı belirteci kullanmak için hizmet ile güvenli bir oturumu yeniden oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="52664-139">The client must re-establish a secure session with the service to send future messages or use a stateful security context token.</span></span> <span data-ttu-id="52664-140">Durum bilgisi olan güvenlik bağlamı belirteçleri dönüştürüldüğü bir Web sunucusu varlığını sürdürmesi güvenli bir oturum de olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="52664-140">Stateful security context tokens also allow a secure session to survive a Web server being recycled.</span></span> <span data-ttu-id="52664-141">Durum bilgisi olan güvenli içeriği belirteçleri güvenli bir oturumda kullanma hakkında daha fazla bilgi için bkz: [nasıl yapılır: güvenli oturum açmak için bir güvenlik bağlamı belirteci oluşturma](../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span><span class="sxs-lookup"><span data-stu-id="52664-141">For more information about using stateful secure context tokens in a secure session, see [How to: Create a Security Context Token for a Secure Session](../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span></span> <span data-ttu-id="52664-142">Alternatif olarak, güvenli oturumlar devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52664-142">Alternatively, you can disable secure sessions.</span></span> <span data-ttu-id="52664-143">Kullandığınızda [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) ayarlayabileceğiniz bağlama, `establishSecurityContext` özelliğine `false` güvenli oturumlar devre dışı bırakmak için.</span><span class="sxs-lookup"><span data-stu-id="52664-143">When you use the [\<wsHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) binding, you can set the `establishSecurityContext` property to `false` to disable secure sessions.</span></span> <span data-ttu-id="52664-144">Güvenli oturumlar diğer bağlantılar için devre dışı bırakmak için özel bağlama oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="52664-144">To disable secure sessions for other bindings, you must create a custom binding.</span></span> <span data-ttu-id="52664-145">Özel bağlama oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: SecurityBindingElement kullanarak özel bir bağlama oluşturun](../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="52664-145">For details about creating a custom binding, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span> <span data-ttu-id="52664-146">Bu seçeneklerin hiçbirini uygulamadan önce uygulamanızın güvenlik gereksinimlerini anlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="52664-146">Before you apply any of these options, you must understand your application's security requirements.</span></span>  
  
<a name="BKMK_q2"></a>   
## <a name="my-service-starts-to-reject-new-clients-after-about-10-clients-are-interacting-with-it-what-is-happening"></a><span data-ttu-id="52664-147">Yaklaşık 10 istemcileri ile etkileşim sonra yeni istemciler reddetmeye My hizmetini başlatır.</span><span class="sxs-lookup"><span data-stu-id="52664-147">My service starts to reject new clients after about 10 clients are interacting with it.</span></span> <span data-ttu-id="52664-148">Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="52664-148">What is happening?</span></span>  
 <span data-ttu-id="52664-149">Varsayılan olarak, yalnızca 10 eşzamanlı oturum Hizmetleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="52664-149">By default, services can have only 10 concurrent sessions.</span></span> <span data-ttu-id="52664-150">Hizmet bağlamaları oturumları kullanırsanız, daha sonra yeni istemci bağlantılarını bir geçerli oturum sona kadar reddediyor bu sayıyı ulaşana kadar bu nedenle, hizmetin yeni istemci bağlantılarını kabul eder.</span><span class="sxs-lookup"><span data-stu-id="52664-150">Therefore, if the service bindings use sessions, the service accepts new client connections until it reaches that number, after which it refuses new client connections until one of the current sessions ends.</span></span> <span data-ttu-id="52664-151">Daha fazla istemciyi çeşitli yollarla destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="52664-151">You can support more clients in a number of ways.</span></span> <span data-ttu-id="52664-152">Hizmetinizi oturumları gerektirmiyorsa, bir süre sonuyla bağlama kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="52664-152">If your service does not require sessions, do not use a sessionful binding.</span></span> <span data-ttu-id="52664-153">(Daha fazla bilgi için bkz: [kullanarak oturumları](../../../docs/framework/wcf/using-sessions.md).) Değerini değiştirerek oturum sınırı artırmak için başka bir seçenektir <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A> özelliği, koşullar uygun sayısı.</span><span class="sxs-lookup"><span data-stu-id="52664-153">(For more information, see [Using Sessions](../../../docs/framework/wcf/using-sessions.md).) Another option is to increase the session limit by changing the value of the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A> property to the number appropriate to your circumstance.</span></span>  
  
<a name="BKMK_q3"></a>   
## <a name="can-i-load-my-service-configuration-from-somewhere-other-than-the-wcf-applications-configuration-file"></a><span data-ttu-id="52664-154">Hizmet yapılandırma sıralandığından WCF uygulamanın yapılandırma dosyasında diğer gelen yükleyebilir?</span><span class="sxs-lookup"><span data-stu-id="52664-154">Can I load my service configuration from somewhere other than the WCF application’s configuration file?</span></span>  
 <span data-ttu-id="52664-155">Evet, ancak özel bir oluşturmak kullandığınız <xref:System.ServiceModel.ServiceHost> geçersiz kılmaları sınıf <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="52664-155">Yes, however, you have to create a custom <xref:System.ServiceModel.ServiceHost> class that overrides the <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> method.</span></span> <span data-ttu-id="52664-156">Bu yöntem içinde (Standart yapılandırma bilgilerini de yüklemek istiyorsanız) yapılandırma önce yüklemek için temel çağırabilir ancak sistemi yükleme yapılandırması da tamamen değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52664-156">Inside that method, you can call the base to load configuration first (if you want to load the standard configuration information as well) but you can also entirely replace the configuration loading system.</span></span> <span data-ttu-id="52664-157">Uygulama yapılandırma dosyasında farklı bir yapılandırma dosyasından yapılandırma yüklemek istiyorsanız, gerekir kendiniz yapılandırma dosyası ayrıştırma ve yapılandırmayı unutmayın.</span><span class="sxs-lookup"><span data-stu-id="52664-157">Note that if you want to load configuration from a configuration file that is different from the application configuration file, you must parse the configuration file yourself and load the configuration.</span></span>  
  
 <span data-ttu-id="52664-158">Aşağıdaki kod örneğinde nasıl geçersiz kılınacağını gösterir <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> yöntemi ve doğrudan bir uç noktasını yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="52664-158">The following code example shows how to override the <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> method and directly configure an endpoint.</span></span>  
  
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
## <a name="my-service-and-client-work-great-but-i-cant-get-them-to-work-when-the-client-is-on-another-computer-whats-happening"></a><span data-ttu-id="52664-159">Hizmetim ve istemci iş mükemmel, ancak bunları istemci başka bir bilgisayarda olduğunda iş alınamıyor?</span><span class="sxs-lookup"><span data-stu-id="52664-159">My service and client work great, but I can’t get them to work when the client is on another computer?</span></span> <span data-ttu-id="52664-160">Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="52664-160">What’s happening?</span></span>  
 <span data-ttu-id="52664-161">Özel duruma bağlı olarak, çeşitli sorunları olabilir:</span><span class="sxs-lookup"><span data-stu-id="52664-161">Depending upon the exception, there may be several issues:</span></span>  
  
-   <span data-ttu-id="52664-162">Ana bilgisayar adı ve değil "localhost" istemci uç nokta adresleri değiştirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="52664-162">You might need to change the client endpoint addresses to the host name and not "localhost".</span></span>  
  
-   <span data-ttu-id="52664-163">Uygulama bağlantı noktasını açmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="52664-163">You might need to open the port to the application.</span></span> <span data-ttu-id="52664-164">Ayrıntılar için bkz [güvenlik duvarı yönergeleri](../../../docs/framework/wcf/samples/firewall-instructions.md) SDK örnekleri gelen.</span><span class="sxs-lookup"><span data-stu-id="52664-164">For details, see [Firewall Instructions](../../../docs/framework/wcf/samples/firewall-instructions.md) from the SDK samples.</span></span>  
  
-   <span data-ttu-id="52664-165">Diğer olası sorunları için örnekleri konusuna [bir çalışma grubu ve üzerinden makineler örneklerini çalıştırma](http://msdn.microsoft.com/library/a451a525-e7ce-452d-9da9-620221260113).</span><span class="sxs-lookup"><span data-stu-id="52664-165">For other possible issues, see the samples topic [Running the Samples in a Workgroup and Across Machines](http://msdn.microsoft.com/library/a451a525-e7ce-452d-9da9-620221260113).</span></span>  
  
-   <span data-ttu-id="52664-166">İstemci Windows kimlik bilgilerini kullanarak ve özel durum bir <xref:System.ServiceModel.Security.SecurityNegotiationException>, Kerberos aşağıdaki gibi yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="52664-166">If your client is using Windows credentials and the exception is a <xref:System.ServiceModel.Security.SecurityNegotiationException>, configure Kerberos as follows.</span></span>  
  
    1.  <span data-ttu-id="52664-167">Kimlik bilgilerinin istemcinin App.config dosyasında son nokta öğesine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="52664-167">Add the identity credentials to the endpoint element in the client’s App.config file:</span></span>  
  
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
  
    2.  <span data-ttu-id="52664-168">Kendini barındıran hizmet Sistem veya ağ hizmeti hesabı altında çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="52664-168">Run the self-hosted service under the System or NetworkService account.</span></span> <span data-ttu-id="52664-169">Bu komutu bir komut penceresi sistem hesabı altında oluşturmak için çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="52664-169">You can run this command to create a command window under the System account:</span></span>  
  
        ```console
        at 12:36 /interactive "cmd.exe"  
        ```  
  
    3.  <span data-ttu-id="52664-170">Altında Internet Information Services (varsayılan olarak, hizmet asıl adı (SPN) hesabı kullanır, IIS), hizmetini barındırır.</span><span class="sxs-lookup"><span data-stu-id="52664-170">Host the service under Internet Information Services (IIS), which, by default, uses the service principal name (SPN) account.</span></span>  
  
    4.  <span data-ttu-id="52664-171">Yeni bir SPN SetSPN kullanarak etki alanı ile kaydedin.</span><span class="sxs-lookup"><span data-stu-id="52664-171">Register a new SPN with the domain using SetSPN.</span></span> <span data-ttu-id="52664-172">Bunu yapmak için bir etki alanı yöneticisi olması gerektiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="52664-172">Note that you will need to be a domain administrator in order to do this.</span></span>  
  
 <span data-ttu-id="52664-173">Kerberos protokolü hakkında daha fazla bilgi için bkz: [WCF güvenlik kavramları kullanılan](../../../docs/framework/wcf/feature-details/security-concepts-used-in-wcf.md) ve:</span><span class="sxs-lookup"><span data-stu-id="52664-173">For more information about the Kerberos protocol, see [Security Concepts Used in WCF](../../../docs/framework/wcf/feature-details/security-concepts-used-in-wcf.md) and:</span></span>  
  
-   [<span data-ttu-id="52664-174">Windows Kimlik Doğrulama Hatalarını Ayıklama</span><span class="sxs-lookup"><span data-stu-id="52664-174">Debugging Windows Authentication Errors</span></span>](../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)  
  
-   [<span data-ttu-id="52664-175">Http.sys kullanarak Kerberos hizmet asıl adlarını kaydetme</span><span class="sxs-lookup"><span data-stu-id="52664-175">Registering Kerberos Service Principal Names by Using Http.sys</span></span>](http://go.microsoft.com/fwlink/?LinkId=86943)  
  
-   [<span data-ttu-id="52664-176">Kerberos açıklanmıştır</span><span class="sxs-lookup"><span data-stu-id="52664-176">Kerberos Explained</span></span>](http://go.microsoft.com/fwlink/?LinkId=86946)  
  
<a name="BKMK_q5"></a>   
## <a name="when-i-throw-a-faultexceptionexception-where-the-type-is-an-exception-i-always-receive-a-general-faultexception-type-on-the-client-and-not-the-generic-type-whats-happening"></a><span data-ttu-id="52664-177">Bir FaultException ı throw zaman\<özel durum > türü özel bir durum olduğunda, her zaman istemci üzerinde genel bir FaultException tür ve genel tür alıyorum.</span><span class="sxs-lookup"><span data-stu-id="52664-177">When I throw a FaultException\<Exception> where the type is an exception, I always receive a general FaultException type on the client and not the generic type.</span></span> <span data-ttu-id="52664-178">Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="52664-178">What’s happening?</span></span>  
 <span data-ttu-id="52664-179">Veri türü ve, hatalı sözleşme ayrıntı türü olarak bildirme kendi özel hata oluşturmak önerilir.</span><span class="sxs-lookup"><span data-stu-id="52664-179">It is highly recommended that you create your own custom error data type and declare that as the detail type in your fault contract.</span></span> <span data-ttu-id="52664-180">Neden olan sistem tarafından sağlanan özel durum türleri kullanma:</span><span class="sxs-lookup"><span data-stu-id="52664-180">The reason is that using system-provided exception types:</span></span>  
  
-   <span data-ttu-id="52664-181">Hizmet odaklı uygulamalar büyük gücü birini kaldırır türü bağımlılığı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="52664-181">Creates a type dependency that removes one of the biggest strengths of service-oriented applications.</span></span>  
  
-   <span data-ttu-id="52664-182">Özel durumlar standart bir şekilde seri hale getirme sırasında bağımlı olamaz.</span><span class="sxs-lookup"><span data-stu-id="52664-182">Cannot depend upon exceptions serializing in a standard way.</span></span> <span data-ttu-id="52664-183">Bazı — gibi <xref:System.Security.SecurityException>— hiç seri hale getirilebilir olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="52664-183">Some—like <xref:System.Security.SecurityException>—may not be serializable at all.</span></span>  
  
-   <span data-ttu-id="52664-184">İstemcilere iç uygulama ayrıntılarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="52664-184">Exposes internal implementation details to clients.</span></span> <span data-ttu-id="52664-185">Daha fazla bilgi için bkz: [belirtme ve işleme hataları sözleşme ve hizmetlerde](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span><span class="sxs-lookup"><span data-stu-id="52664-185">For more information, see [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span></span>  
  
 <span data-ttu-id="52664-186">Bir uygulamada hata ayıklama yaparsanız, ancak, özel durum bilgilerini serileştirme ve kullanarak istemciye Döndür <xref:System.ServiceModel.Description.ServiceDebugBehavior> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="52664-186">If you are debugging an application, however, you can serialize exception information and return it to the client by using the <xref:System.ServiceModel.Description.ServiceDebugBehavior> class.</span></span>  
  
<a name="BKMK_q6"></a>   
## <a name="it-seems-like-one-way-and-request-reply-operations-return-at-roughly-the-same-speed-when-the-reply-contains-no-data-whats-happening"></a><span data-ttu-id="52664-187">Gibi tek yönlü görünür ve yanıt hiçbir veri içerdiğinde istek-yanıt işlemleri kabaca aynı hızda döndürür.</span><span class="sxs-lookup"><span data-stu-id="52664-187">It seems like one-way and request-reply operations return at roughly the same speed when the reply contains no data.</span></span> <span data-ttu-id="52664-188">Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="52664-188">What's happening?</span></span>  
 <span data-ttu-id="52664-189">Bir işlem bir yolu olduğunu belirten yalnızca işlem sözleşmesi bir giriş iletisi kabul eder ve bir çıktı iletisi döndürmüyor anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="52664-189">Specifying that an operation is one way means only that the operation contract accepts an input message and does not return an output message.</span></span> <span data-ttu-id="52664-190">İçinde [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], tüm istemci çağrılarını giden veri kablo için yazılmış veya bir özel durum döndürür.</span><span class="sxs-lookup"><span data-stu-id="52664-190">In [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], all client invocations return when the outbound data has been written to the wire or an exception is thrown.</span></span> <span data-ttu-id="52664-191">Tek yönlü işlemler aynı şekilde çalışır ve hizmet bulunması veya hizmet ağdan verileri kabul etmek için hazır değil bloke atabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52664-191">One-way operations work the same way, and they can throw if the service cannot be located or block if the service is not prepared to accept the data from the network.</span></span> <span data-ttu-id="52664-192">Genellikle, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], bu istemci istek-yanıt; daha hızlı döndüren tek yönlü çağrıları sonuçlanır ancak istek-yanıt işlemlerinin yanı sıra tek yönlü işlemler giden verilerin ağ üzerinden gönderilmesi yavaşlatır herhangi bir koşul yavaşlatır.</span><span class="sxs-lookup"><span data-stu-id="52664-192">Typically in [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], this results in one-way calls returning to the client more quickly than request-reply; but any condition that slows the sending of the outbound data over the network slows one-way operations as well as request-reply operations.</span></span> <span data-ttu-id="52664-193">Daha fazla bilgi için bkz: [One-Way Hizmetleri](../../../docs/framework/wcf/feature-details/one-way-services.md) ve [bir WCF istemcisi kullanarak hizmetlere erişme](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md).</span><span class="sxs-lookup"><span data-stu-id="52664-193">For more information, see [One-Way Services](../../../docs/framework/wcf/feature-details/one-way-services.md) and [Accessing Services Using a WCF Client](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md).</span></span>  
  
<a name="BKMK_q77"></a>   
## <a name="im-using-an-x509-certificate-with-my-service-and-i-get-a-systemsecuritycryptographycryptographicexception-whats-happening"></a><span data-ttu-id="52664-194">Bir X.509 sertifikası ile Hizmetim kullanıyorum ve bir System.Security.Cryptography.CryptographicException alın.</span><span class="sxs-lookup"><span data-stu-id="52664-194">I’m using an X.509 certificate with my service and I get a System.Security.Cryptography.CryptographicException.</span></span> <span data-ttu-id="52664-195">Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="52664-195">What’s happening?</span></span>  
 <span data-ttu-id="52664-196">Bu, genellikle IIS çalışan altında çalıştığı işlemi kullanıcı hesabı değiştirdikten sonra gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="52664-196">This commonly occurs after changing the user account under which the IIS worker process runs.</span></span> <span data-ttu-id="52664-197">Örneğin, [!INCLUDE[wxp](../../../includes/wxp-md.md)], Aspnet_wp.exe ASPNET bir özel kullanıcı hesabına çalıştığı varsayılan kullanıcı hesabını değiştirirseniz, bu hatayı görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52664-197">For example, in [!INCLUDE[wxp](../../../includes/wxp-md.md)], if you change the default user account that the Aspnet_wp.exe runs under from ASPNET to a custom user account, you may see this error.</span></span> <span data-ttu-id="52664-198">Özel anahtarı kullanıyorsanız, bunu kullanan işleme anahtara depolandığı dosya erişim iznine sahip gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="52664-198">If using a private key, the process that uses it will need to have permissions to access the file storing that key.</span></span>  
  
 <span data-ttu-id="52664-199">Bu durumda, özel anahtarı içeren dosyayı için işlemin hesaba okuma erişimi ayrıcalıkları vermeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="52664-199">If this is the case, you must give read access privileges to the process's account for the file containing the private key.</span></span> <span data-ttu-id="52664-200">Örneğin, IIS çalışan işlemi Bob hesabı altında çalışıyorsa, özel anahtarı içeren dosyanın Bob okuma erişimi verin gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="52664-200">For example, if the IIS worker process is running under the Bob account, then you will need to give Bob read access to the file containing the private key.</span></span>  
  
 <span data-ttu-id="52664-201">Belirli bir X.509 Sertifika özel anahtarı içeren dosyayı doğru kullanıcı hesabı erişimi vermek hakkında daha fazla bilgi için bkz: [nasıl yapılır: olun X.509 sertifikalarını WCF için erişilebilir](../../../docs/framework/wcf/feature-details/how-to-make-x-509-certificates-accessible-to-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="52664-201">For more information about how to give the correct user account access to the file that contains the private key for a specific X.509 certificate, see [How to: Make X.509 Certificates Accessible to WCF](../../../docs/framework/wcf/feature-details/how-to-make-x-509-certificates-accessible-to-wcf.md).</span></span>  
  
<a name="BKMK_q88"></a>   
## <a name="i-changed-the-first-parameter-of-an-operation-from-uppercase-to-lowercase-now-my-client-throws-an-exception-whats-happening"></a><span data-ttu-id="52664-202">Bir işlemin ilk parametre gelen büyük değiştirdim küçük harf için; Şimdi my istemcisi bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="52664-202">I changed the first parameter of an operation from uppercase to lowercase; now my client throws an exception.</span></span> <span data-ttu-id="52664-203">Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="52664-203">What's happening?</span></span>  
 <span data-ttu-id="52664-204">Parametre adları işlemi imzada değerini sözleşmenin parçası olan ve büyük küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="52664-204">The value of the parameter names in the operation signature are part of the contract and are case-sensitive.</span></span> <span data-ttu-id="52664-205">Kullanım <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType> özniteliği yerel parametre adını ve işlem istemci uygulamaları için açıklayan meta veriler arasında ayrım gerektiğinde.</span><span class="sxs-lookup"><span data-stu-id="52664-205">Use the <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType> attribute when you need to distinguish between the local parameter name and the metadata that describes the operation for client applications.</span></span>  
  
<a name="BKMK_q99"></a>   
## <a name="im-using-one-of-my-tracing-tools-and-i-get-an-endpointnotfoundexception-whats-happening"></a><span data-ttu-id="52664-206">My izleme araçlarından birini kullanıyorum ve bir EndpointNotFoundException alın.</span><span class="sxs-lookup"><span data-stu-id="52664-206">I’m using one of my tracing tools and I get an EndpointNotFoundException.</span></span> <span data-ttu-id="52664-207">Ne oluyor?</span><span class="sxs-lookup"><span data-stu-id="52664-207">What’s happening?</span></span>  
 <span data-ttu-id="52664-208">Sistem tarafından sağlanan değil bir izleme aracı kullanıyorsanız [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] izleme mekanizması ve alırsınız bir <xref:System.ServiceModel.EndpointNotFoundException> belirten bir adres filtresi uyuşmazlığı oluştu, kullanmanız gereken <xref:System.ServiceModel.Description.ClientViaBehavior> izleme iletilerini yönlendirmek için sınıfı yardımcı programı ve bu ileti hizmet adresine yönlendirmek yardımcı programı.</span><span class="sxs-lookup"><span data-stu-id="52664-208">If you are using a tracing tool that is not the system-provided [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] tracing mechanism and you receive an <xref:System.ServiceModel.EndpointNotFoundException> that indicates that there was an address filter mismatch, you need to use the <xref:System.ServiceModel.Description.ClientViaBehavior> class to direct the messages to the tracing utility and have the utility redirect those messages to the service address.</span></span> <span data-ttu-id="52664-209"><xref:System.ServiceModel.Description.ClientViaBehavior> Sınıfı değiştirir `Via` ayrı olarak alıcıdan ultimate, sonraki ağ adresini belirtmek için adresleme üstbilgi belirtilen tarafından `To` adresleme üstbilgi.</span><span class="sxs-lookup"><span data-stu-id="52664-209">The <xref:System.ServiceModel.Description.ClientViaBehavior> class alters the `Via` addressing header to specify the next network address separately from the ultimate receiver, indicated by the `To` addressing header.</span></span> <span data-ttu-id="52664-210">Bunu yaparken kurmak için kullanılan uç nokta adresi ancak değiştirmeyin `To` değeri.</span><span class="sxs-lookup"><span data-stu-id="52664-210">When doing this, however, do not change the endpoint address, which is used to establish the `To` value.</span></span>  
  
 <span data-ttu-id="52664-211">Aşağıdaki kod örneğinde bir örnek istemci yapılandırma dosyası gösterir.</span><span class="sxs-lookup"><span data-stu-id="52664-211">The following code example shows an example client configuration file.</span></span>  
  
```xml
<endpoint   
  address=http://localhost:8000/MyServer/  
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
## <a name="what-is-the-base-address-how-does-it-relate-to-an-endpoint-address"></a><span data-ttu-id="52664-212">Temel adres nedir?</span><span class="sxs-lookup"><span data-stu-id="52664-212">What is the base address?</span></span> <span data-ttu-id="52664-213">Bu bir uç nokta adresine nasıl ilişkilidir?</span><span class="sxs-lookup"><span data-stu-id="52664-213">How does it relate to an endpoint address?</span></span>  
 <span data-ttu-id="52664-214">Temel adres için kök adresidir bir <xref:System.ServiceModel.ServiceHost> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="52664-214">A base address is the root address for a <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="52664-215">Varsayılan olarak eklerseniz, bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior> konak yayımlar tüm uç noktaları HTTP temel adresi yanı sıra meta veri davranışı için sağlanan tüm göreli adresi alınır için Web Hizmetleri Açıklama Dili (WSDL), hizmet yapılandırması sınıfı artı "? wsdl".</span><span class="sxs-lookup"><span data-stu-id="52664-215">By default, if you add a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class into your service configuration, the Web Services Description Language (WSDL) for all endpoints the host publishes are retrieved from the HTTP base address, plus any relative address provided to the metadata behavior, plus "?wsdl".</span></span> <span data-ttu-id="52664-216">Hakkında bilginiz varsa [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] ve IIS, taban adresi sanal dizin ile eşdeğer ise.</span><span class="sxs-lookup"><span data-stu-id="52664-216">If you are familiar with [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] and IIS, the base address is equivalent to the virtual directory.</span></span>  
  
## <a name="sharing-a-port-between-a-service-endpoint-and-a-mex-endpoint-using-the-nettcpbinding"></a><span data-ttu-id="52664-217">Hizmet uç noktası ve NetTcpBinding kullanarak mex uç arasında bir bağlantı noktası paylaşımı</span><span class="sxs-lookup"><span data-stu-id="52664-217">Sharing a port between a service endpoint and a mex endpoint using the NetTcpBinding</span></span>  
 <span data-ttu-id="52664-218">Net.tcp://MyServer bir hizmet için taban adresi belirtirseniz: 8080/MyService ve şu uç noktalar ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="52664-218">If you specify the base address for a service as net.tcp://MyServer:8080/MyService and add the following endpoints:</span></span>  
  
```xml  
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
 <span data-ttu-id="52664-219">Ve NetTcpBinding ayarlarından birini aşağıdaki yapılandırma parçacığında gösterildiği gibi değiştirin:</span><span class="sxs-lookup"><span data-stu-id="52664-219">And if you modify one of the NetTcpBinding settings as shown in the following configuration snippet:</span></span>  
  
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
  
 <span data-ttu-id="52664-220">Aşağıdaki gibi bir hata görürsünüz: işlenmeyen özel durum: System.ServiceModel.addressalreadyınuseexception: olduğundan zaten bir dinleyici IP uç noktası 0.0.0.0:9000 için farklı bir bağlantı noktası ile tam bir URL belirterek bu hataya çalışabilir Aşağıdaki yapılandırma parçacığında gösterildiği gibi MEX uç noktası:</span><span class="sxs-lookup"><span data-stu-id="52664-220">You will see an error like the following: Unhandled Exception: System.ServiceModel.AddressAlreadyInUseException: There is already a listener on IP endpoint 0.0.0.0:9000 You can work around this error by specifying a fully qualified URL with a different port for the MEX endpoint as shown in the following configuration snippet:</span></span>  
  
```xml
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="net.tcp://localhost:9001/servicemodelsamples/mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
<a name="BK_MK99"></a>   
## <a name="when-calling-a-wcf-web-http-application-from-a-wcf-soap-application-the-service-returns-the-following-error-405-method-not-allowed"></a><span data-ttu-id="52664-221">WCF Web HTTP uygulama hizmeti bir WCF SOAP uygulamasından çağırma döndüğünde aşağıdaki hata: 405 yöntemini verilmiyor</span><span class="sxs-lookup"><span data-stu-id="52664-221">When calling a WCF Web HTTP application from a WCF SOAP application the service returns the following error: 405 Method Not Allowed</span></span>  
 <span data-ttu-id="52664-222">WCF Web HTTP uygulama çağırma (kullanan bir hizmet <xref:System.ServiceModel.WebHttpBinding> ve <xref:System.ServiceModel.Description.WebHttpBehavior>) bir WCF hizmeti şu özel durum oluşturabilir: `Unhandled Exception: System.ServiceModel.FaultException`1[System.ServiceModel.ExceptionDetail]: Uzak sunucu beklenmeyen bir yanıt döndürdü : (405) yöntemi değil izin verilir.' WCF giden yazdığından bu özel durum oluştu <xref:System.ServiceModel.OperationContext> gelen ile <xref:System.ServiceModel.OperationContext>.</span><span class="sxs-lookup"><span data-stu-id="52664-222">Calling a WCF Web HTTP application (a service that uses the <xref:System.ServiceModel.WebHttpBinding> and <xref:System.ServiceModel.Description.WebHttpBehavior>) from a WCF service may generate the following exception: `Unhandled Exception: System.ServiceModel.FaultException`1[System.ServiceModel.ExceptionDetail]: The remote server returned an unexpected response: (405) Method Not Allowed.\` This exception occurs because WCF overwrites the outgoing <xref:System.ServiceModel.OperationContext> with the incoming <xref:System.ServiceModel.OperationContext>.</span></span> <span data-ttu-id="52664-223">Bu sorunu çözmek için oluşturun bir <xref:System.ServiceModel.OperationContextScope> WCF Web HTTP hizmeti işlemi içinde.</span><span class="sxs-lookup"><span data-stu-id="52664-223">To solve this problem create an <xref:System.ServiceModel.OperationContextScope> within the WCF Web HTTP service operation.</span></span> <span data-ttu-id="52664-224">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="52664-224">For example:</span></span>  
  
```csharp
public string Echo(string input)  
{  
    using (new OperationContextScope(this.InnerChannel))  
    {  
        return base.Channel.Echo(input);  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="52664-225">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="52664-225">See Also</span></span>  
 [<span data-ttu-id="52664-226">Windows Kimlik Doğrulama Hatalarını Ayıklama</span><span class="sxs-lookup"><span data-stu-id="52664-226">Debugging Windows Authentication Errors</span></span>](../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)
