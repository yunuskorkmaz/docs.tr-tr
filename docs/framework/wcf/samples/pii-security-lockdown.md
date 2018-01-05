---
title: "PII Güvenlik Kilidi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c44fb338-9527-4dd0-8607-b8787d15acb4
caps.latest.revision: "25"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 39f805da7570b81ff1f6593e82f5d0a9310ee9c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="pii-security-lockdown"></a><span data-ttu-id="18fd9-102">PII Güvenlik Kilidi</span><span class="sxs-lookup"><span data-stu-id="18fd9-102">PII Security Lockdown</span></span>
<span data-ttu-id="18fd9-103">Bu örnek, güvenlikle ilgili çeşitli özellikleri denetlemek nasıl gösteren bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] tarafından hizmet:</span><span class="sxs-lookup"><span data-stu-id="18fd9-103">This sample demonstrates how to control several security-related features of a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service by:</span></span>  
  
-   <span data-ttu-id="18fd9-104">Bir hizmetin yapılandırma dosyasındaki hassas bilgilere şifreleme.</span><span class="sxs-lookup"><span data-stu-id="18fd9-104">Encrypting sensitive information in a service's configuration file.</span></span>  
  
-   <span data-ttu-id="18fd9-105">Böylece hizmet alt dizinleri iç içe öğelerin yapılandırma dosyasındaki kilitleme ayarları geçersiz kılamazsınız.</span><span class="sxs-lookup"><span data-stu-id="18fd9-105">Locking elements in the configuration file so that nested service subdirectories cannot override settings.</span></span>  
  
-   <span data-ttu-id="18fd9-106">İzleme ve ileti günlüklerinde, kişisel bilgilerin (PII) günlük kaydını denetleme.</span><span class="sxs-lookup"><span data-stu-id="18fd9-106">Controlling the logging of Personally Identifiable Information (PII) in trace and message logs.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="18fd9-107">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="18fd9-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="18fd9-108">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="18fd9-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="18fd9-109">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="18fd9-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="18fd9-110">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="18fd9-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\SecurityLockdown`  
  
## <a name="discussion"></a><span data-ttu-id="18fd9-111">Tartışma</span><span class="sxs-lookup"><span data-stu-id="18fd9-111">Discussion</span></span>  
 <span data-ttu-id="18fd9-112">Bu özelliklerin her biri ayrı ayrı veya birlikte bir hizmetin güvenlik denetim konuları için olabilir.</span><span class="sxs-lookup"><span data-stu-id="18fd9-112">Each of these features can be used separately or together to control aspects of a service's security.</span></span> <span data-ttu-id="18fd9-113">Bu güvenliğini sağlamak için eksiksiz bir kılavuz değildir bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet.</span><span class="sxs-lookup"><span data-stu-id="18fd9-113">This is not a definitive guide to securing a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
 <span data-ttu-id="18fd9-114">.NET Framework yapılandırma dosyalarını veritabanlarına bağlanmak için bağlantı dizelerini gibi hassas bilgiler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="18fd9-114">The .NET Framework configuration files can contain sensitive information such as connection strings to connect to databases.</span></span> <span data-ttu-id="18fd9-115">Paylaşılan ve Web barındırılan senaryolarda yapılandırma dosyasının içinde bulunan veriler için günlük görüntüleme dayanıklı olmasını sağlamak için bir hizmet yapılandırma dosyasında bu bilgileri şifrelemek için istenebilir.</span><span class="sxs-lookup"><span data-stu-id="18fd9-115">In shared, Web-hosted scenarios it may be desirable to encrypt this information in the configuration file for a service so that the data contained within the configuration file is resistant to casual viewing.</span></span> <span data-ttu-id="18fd9-116">.NET framework 2.0 ve sonraki Windows veri koruma uygulama programlama arabirimi (DPAPI) veya RSA şifreleme sağlayıcısı kullanarak yapılandırma dosyasını bölümlerini şifreleme olanağı vardır.</span><span class="sxs-lookup"><span data-stu-id="18fd9-116">.NET Framework 2.0 and later has the ability to encrypt portions of the configuration file using the Windows Data Protection application programming interface (DPAPI) or the RSA Cryptographic provider.</span></span> <span data-ttu-id="18fd9-117">DPAPI veya RSA kullanarak aspnet_regiis.exe bir yapılandırma dosyası seçme bölümlerini şifreleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="18fd9-117">The aspnet_regiis.exe using the DPAPI or RSA can encrypt select portions of a configuration file.</span></span>  
  
 <span data-ttu-id="18fd9-118">Web barındırılan senaryolarda hizmetler diğer hizmetlere dizinlerde olması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="18fd9-118">In Web-hosted scenarios it is possible to have services in subdirectories of other services.</span></span> <span data-ttu-id="18fd9-119">Varsayılan yapılandırma değerlerini belirlemek için anlamsal üst dizinindeki yapılandırma değerleri geçersiz kılmak için iç içe geçmiş dizinlerdeki yapılandırma dosyaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="18fd9-119">The default semantic for determining configuration values allows configuration files in the nested directories to override the configuration values in the parent directory.</span></span> <span data-ttu-id="18fd9-120">Belirli durumlarda bu çeşitli nedenlerle için istenmeyen olabilir.</span><span class="sxs-lookup"><span data-stu-id="18fd9-120">In certain situations this may be undesirable for a variety of reasons.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="18fd9-121">iç içe geçmiş bir hizmet kullanarak çalıştırıldığında yapılandırma değerlerini, böylece yapılandırma iç içe geçmiş kilitleme özel durumları oluşturur hizmet yapılandırma destekler yapılandırma değerleri geçersiz.</span><span class="sxs-lookup"><span data-stu-id="18fd9-121"> service configuration supports the locking of configuration values so that nested configuration generates exceptions when a nested service is run using overridden configuration values.</span></span>  
  
 <span data-ttu-id="18fd9-122">Bu örnek, bilinen kişisel bilgilerin (PII) kullanıcı adı ve parola gibi izleme ve ileti günlüklerinde günlük denetim gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="18fd9-122">This sample demonstrates how to control the logging of known Personally Identifiable Information (PII) in trace and message logs, such as username and password.</span></span> <span data-ttu-id="18fd9-123">Belirli durumlarda PII günlüğe bir uygulamada hata ayıklama önemli olabilir ancak varsayılan olarak bilinen PII günlüğünü devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="18fd9-123">By default, logging of known PII is disabled however in certain situations logging of PII can be important in debugging an application.</span></span> <span data-ttu-id="18fd9-124">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="18fd9-124">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="18fd9-125">Ayrıca, bu örnek, ileti izleme ve kaydetme kullanır.</span><span class="sxs-lookup"><span data-stu-id="18fd9-125">In addition, this sample uses tracing and message logging.</span></span> <span data-ttu-id="18fd9-126">Daha fazla bilgi için bkz: [izleme ve ileti günlüğe kaydetme](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="18fd9-126">For more information, see the [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) sample.</span></span>  
  
## <a name="encrypting-configuration-file-elements"></a><span data-ttu-id="18fd9-127">Yapılandırma dosyası öğeleri şifreleme</span><span class="sxs-lookup"><span data-stu-id="18fd9-127">Encrypting Configuration File Elements</span></span>  
 <span data-ttu-id="18fd9-128">Paylaşılan Web barındırma ortamında güvenlik nedenleriyle, hassas bilgiler içerebilir veritabanı bağlantı dizelerini gibi belirli yapılandırma öğelerini şifreleme istenebilir.</span><span class="sxs-lookup"><span data-stu-id="18fd9-128">For security purposes in a shared Web-hosting environment, it may be desirable to encrypt certain configuration elements, such as database connection strings that may contain sensitive information.</span></span> <span data-ttu-id="18fd9-129">Örneğin, % WINDIR%\Micrsoft.NET\Framework\v4.0.20728 .NET Framework klasöründe bulunan aspnet_regiis.exe aracını kullanarak bir yapılandırma öğesi şifrelenmelidir.</span><span class="sxs-lookup"><span data-stu-id="18fd9-129">A configuration element may be encrypted using the aspnet_regiis.exe tool found in the .NET Framework folder For example, %WINDIR%\Micrsoft.NET\Framework\v4.0.20728.</span></span>  
  
#### <a name="to-encrypt-the-values-in-the-appsettings-section-in-webconfig-for-the-sample"></a><span data-ttu-id="18fd9-130">Web.config dosyasındaki appSettings bölümünü örnek değerler şifrelemek için</span><span class="sxs-lookup"><span data-stu-id="18fd9-130">To encrypt the values in the appSettings section in Web.config for the sample</span></span>  
  
1.  <span data-ttu-id="18fd9-131">Açık başlangıç kullanarak bir komut istemi -> Çalıştır...</span><span class="sxs-lookup"><span data-stu-id="18fd9-131">Open a command prompt by using Start->Run….</span></span> <span data-ttu-id="18fd9-132">Yazın `cmd` tıklatıp **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="18fd9-132">Type in `cmd` and click **OK**.</span></span>  
  
2.  <span data-ttu-id="18fd9-133">Aşağıdaki komutu gönderdikten geçerli .NET Framework dizinine gidin: `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`.</span><span class="sxs-lookup"><span data-stu-id="18fd9-133">Navigate to the current .NET Framework directory by issuing the following command: `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`.</span></span>  
  
3.  <span data-ttu-id="18fd9-134">Aşağıdaki komutu gönderdikten Web.config klasörü appSettings yapılandırma ayarlarında şifrelemek: `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`.</span><span class="sxs-lookup"><span data-stu-id="18fd9-134">Encrypt the appSettings configuration settings in the Web.config folder by issuing the following command: `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`.</span></span>  
  
 <span data-ttu-id="18fd9-135">ASP.NET yapılandırma DPAPI üzerinde nasıl yapılır okuyarak yapılandırma dosyalarını bölümlerini şifreleme hakkında daha fazla bilgi bulunabilir ([Güvenli ASP.NET uygulamaları oluşturma: kimlik doğrulama, yetkilendirme ve güvenli iletişim](http://go.microsoft.com/fwlink/?LinkId=95137)) ve ASP.NET yapılandırmasında RSA üzerinde nasıl yapılır ([nasıl yapılır: ASP.NET 2.0 kullanarak RSA şifreleme yapılandırma bölümlerinin](http://go.microsoft.com/fwlink/?LinkId=95138)).</span><span class="sxs-lookup"><span data-stu-id="18fd9-135">More information about encrypting sections of configuration files can be found by reading a how-to on DPAPI in ASP.NET configuration ([Building Secure ASP.NET Applications: Authentication, Authorization, and Secure Communication](http://go.microsoft.com/fwlink/?LinkId=95137)) and a how-to on RSA in ASP.NET configuration ([How To: Encrypt Configuration Sections in ASP.NET 2.0 Using RSA](http://go.microsoft.com/fwlink/?LinkId=95138)).</span></span>  
  
## <a name="locking-configuration-file-elements"></a><span data-ttu-id="18fd9-136">Kilitleme yapılandırma dosyası öğeleri</span><span class="sxs-lookup"><span data-stu-id="18fd9-136">Locking configuration file elements</span></span>  
 <span data-ttu-id="18fd9-137">Web barındırılan senaryolarda Hizmetleri Hizmetleri dizinlerde olması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="18fd9-137">In Web-hosted scenarios, it is possible to have services in subdirectories of services.</span></span> <span data-ttu-id="18fd9-138">Bu durumlarda, hizmet alt dizinindeki yapılandırma değerlerini Machine.config değerlerde incelenerek ve dizin ağacında taşıma ve son olarak birleştirme üst dizinlerdeki herhangi Web.config dosyaları ile sırayla birleştirme tarafından hesaplanır Hizmet içeren dizine Web.config dosyasında.</span><span class="sxs-lookup"><span data-stu-id="18fd9-138">In these situations, configuration values for the service in the subdirectory are calculated by examining values in Machine.config and successively merging with any Web.config files in parent directories moving down the directory tree and finally merging the Web.config file in the directory that contains the service.</span></span> <span data-ttu-id="18fd9-139">Çoğu yapılandırma öğeleri için varsayılan davranış, alt dizinleri üst dizinlerde ayarlanan değerleri geçersiz kılmak için yapılandırma dosyalarında izin vermektir.</span><span class="sxs-lookup"><span data-stu-id="18fd9-139">The default behavior for most configuration elements is to allow configuration files in subdirectories to override the values set in parent directories.</span></span> <span data-ttu-id="18fd9-140">Belirli durumlarda dizinlerdeki yapılandırma dosyaları üst dizini yapılandırmasında değerleri geçersiz kılmasını önlemek istenebilir.</span><span class="sxs-lookup"><span data-stu-id="18fd9-140">In certain situations it may be desirable to prevent configuration files in subdirectories from overriding values set in parent directory configuration.</span></span>  
  
 <span data-ttu-id="18fd9-141">.NET Framework çalışma zamanı özel durumlar kilitli yapılandırma öğeleri geçersiz kılma yapılandırmaları oluşturma için yapılandırma dosyası öğelerini kilitlemek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="18fd9-141">The .NET Framework provides a way to lock configuration file elements so that configurations that override locked configuration elements throw run-time exceptions.</span></span>  
  
 <span data-ttu-id="18fd9-142">Bir yapılandırma öğesi belirterek kilitlenip `lockItem` özniteliği yapılandırma dosyasında bir düğüm için örneğin, böylece hesaplayıcı Hizmetleri'nde yapılandırma dosyalarını iç içe geçmiş yapılandırma dosyasında CalculatorServiceBehavior düğümü kilitlemek için değişiklik davranışı, aşağıdaki yapılandırma kullanılabilir olamaz.</span><span class="sxs-lookup"><span data-stu-id="18fd9-142">A configuration element can be locked by specifying the `lockItem` attribute for a node in the configuration file, for example, to lock the CalculatorServiceBehavior node in the configuration file so that calculator services in nested configuration files cannot change the behavior, the following configuration can be used.</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>   
          <serviceBehaviors>   
             <behavior name="CalculatorServiceBehavior" lockItem="true">   
               <serviceMetadata httpGetEnabled="True"/>   
               <serviceDebug includeExceptionDetailInFaults="False" />   
             </behavior>   
          </serviceBehaviors>   
       </behaviors>   
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="18fd9-143">Yapılandırma öğeleri kilitleme daha belirli olabilir.</span><span class="sxs-lookup"><span data-stu-id="18fd9-143">Locking of configuration elements can be more specific.</span></span> <span data-ttu-id="18fd9-144">Öğelerinin bir listesini değeri olarak belirtilen `lockElements` bir alt öğe koleksiyonunu içinde öğeleri kümesini kilitlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="18fd9-144">A list of elements can be specified as the value to the `lockElements` to lock a set of elements within a collection of sub-elements.</span></span> <span data-ttu-id="18fd9-145">Öznitelik listesi değeri olarak belirtilen `lockAttributes` öğe içindeki öznitelikler kümesi kilitlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="18fd9-145">A list of attributes can be specified as the value to the `lockAttributes` to lock a set of attributes within an element.</span></span> <span data-ttu-id="18fd9-146">Belirterek dışında belirtilen liste öğelerini veya özniteliklerin tüm bir koleksiyon kilitlenebilir `lockAllElementsExcept` veya `lockAllAttributesExcept` bir düğümde öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="18fd9-146">An entire collection of elements or attributes can be locked except for a specified list by specifying the `lockAllElementsExcept` or `lockAllAttributesExcept` attributes on a node.</span></span>  
  
## <a name="pii-logging-configuration"></a><span data-ttu-id="18fd9-147">PII günlüğü yapılandırması</span><span class="sxs-lookup"><span data-stu-id="18fd9-147">PII Logging Configuration</span></span>  
 <span data-ttu-id="18fd9-148">PII günlüğe iki anahtarları tarafından denetlenir: izin ver veya Reddet günlük PII ve PII günlüğü her geçiş yapmak bir uygulama Yöneticisi sağlayan bir uygulama ayarı için bilgisayar yöneticisi sağlayan Machine.config bilgisayar genelinde bir ayar bulundu Web.config veya App.config dosyasını kaynağında.</span><span class="sxs-lookup"><span data-stu-id="18fd9-148">Logging of PII is controlled by two switches: a computer-wide setting found in Machine.config that allows a computer administrator to permit or deny logging of PII and an application setting that allows an application administrator to toggle logging of PII for each source in a Web.config or App.config file.</span></span>  
  
 <span data-ttu-id="18fd9-149">Bilgisayar genelinde ayar ayarlayarak denetlenir `enableLoggingKnownPii` için `true` veya `false`, `machineSettings` Machine.config öğesinde. Örneğin, aşağıdaki uygulamaların PII günlük özelliğini açmak izin verir.</span><span class="sxs-lookup"><span data-stu-id="18fd9-149">The computer-wide setting is controlled by setting `enableLoggingKnownPii` to `true` or `false`, in the `machineSettings` element in Machine.config. For example, the following allows applications to turn on logging of PII.</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <machineSettings enableLoggingKnownPii="true" />  
    </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
>  <span data-ttu-id="18fd9-150">Machine.config dosyasının bir varsayılan konum vardır: % WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.</span><span class="sxs-lookup"><span data-stu-id="18fd9-150">The Machine.config file has a default location: %WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.</span></span>  
  
 <span data-ttu-id="18fd9-151">Varsa `enableLoggingKnownPii` özniteliği Machine.config içinde mevcut değil, PII günlüğe izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="18fd9-151">If the `enableLoggingKnownPii` attribute is not present in Machine.config, logging of PII is not allowed.</span></span>  
  
 <span data-ttu-id="18fd9-152">Bir uygulama ayarlayarak yapılır için PII günlüğe yazma etkinleştirildikten sonra `logKnownPii` için kaynak öğesinin özniteliği `true` veya `false` Web.config veya App.config dosyasının içinde.</span><span class="sxs-lookup"><span data-stu-id="18fd9-152">Enabling logging of PII for an application is done by setting the `logKnownPii` attribute of the source element to `true` or `false` in the Web.config or App.config file.</span></span> <span data-ttu-id="18fd9-153">Örneğin, aşağıdaki PII günlüğü ileti günlüğe kaydetme ve izleme günlük kaydını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="18fd9-153">For example, the following enables logging of PII for both message logging and trace logging.</span></span>  
  
```xml  
<configuration>  
    <system.diagnostics>  
        <sources>  
            <source name="System.ServiceModel.MessageLogging" logKnownPii="true">  
                <listeners>   
                ...   
                </listeners>  
            </source>  
            <source name="System.ServiceModel" switchValue="Verbose, ActivityTracing">  
            <listeners>  
        ...   
            </listeners>  
            </source>  
        </sources>  
    </system.diagnostics>  
</configuration>  
```  
  
 <span data-ttu-id="18fd9-154">Varsa `logKnownPii` özniteliği belirtilmezse, ardından PII günlüğe kaydedilmez.</span><span class="sxs-lookup"><span data-stu-id="18fd9-154">If the `logKnownPii` attribute is not specified, then PII is not logged.</span></span>  
  
 <span data-ttu-id="18fd9-155">PII her iki yalnızca oturum `enableLoggingKnownPii` ayarlanır `true`, ve `logKnownPii` ayarlanır `true`.</span><span class="sxs-lookup"><span data-stu-id="18fd9-155">PII is only logged if both `enableLoggingKnownPii` is set to `true`, and `logKnownPii` is set to `true`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="18fd9-156">System.Diagnostics tüm öznitelikleri yapılandırma dosyasında listelenen ilk dışındaki tüm kaynaklarında yoksayar.</span><span class="sxs-lookup"><span data-stu-id="18fd9-156">System.Diagnostics ignores all attributes on all sources except the first one listed in the configuration file.</span></span> <span data-ttu-id="18fd9-157">Ekleme `logKnownPii` özniteliği yapılandırma dosyasında ikinci kaynağına etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="18fd9-157">Adding the `logKnownPii` attribute to the second source in the configuration file has no effect.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="18fd9-158">Bu örneği çalıştırmak için Machine.config el ile değiştirilmesini içerir. Machine.config yanlış değer veya sözdizimi değiştirmek tüm .NET Framework uygulamaların çalıştırılmasını engelleyebilir zaman dikkatli olunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="18fd9-158">To run this sample involves manual modification of Machine.config. Care should be taken when modifying Machine.config as incorrect values or syntax may prevent all .NET Framework applications from running.</span></span>  
  
 <span data-ttu-id="18fd9-159">Yapılandırma dosyası öğeleri DPAPI ve RSA kullanarak şifrelemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="18fd9-159">It is also possible to encrypt configuration file elements using DPAPI and RSA.</span></span> <span data-ttu-id="18fd9-160">Daha fazla bilgi için aşağıdaki bağlantılara bakın:</span><span class="sxs-lookup"><span data-stu-id="18fd9-160">For more information, see the following links:</span></span>  
  
-   [<span data-ttu-id="18fd9-161">Güvenli ASP.NET uygulamaları oluşturma: Kimlik doğrulama, yetkilendirme ve güvenli iletişim</span><span class="sxs-lookup"><span data-stu-id="18fd9-161">Building Secure ASP.NET Applications: Authentication, Authorization, and Secure Communication</span></span>](http://go.microsoft.com/fwlink/?LinkId=95137)  
  
-   [<span data-ttu-id="18fd9-162">Nasıl yapılır: ASP.NET 2.0 yapılandırma bölümlerinin şifrelemek RSA kullanma</span><span class="sxs-lookup"><span data-stu-id="18fd9-162">How To: Encrypt Configuration Sections in ASP.NET 2.0 Using RSA</span></span>](http://go.microsoft.com/fwlink/?LinkId=95138)  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="18fd9-163">Ayarlamak için derleme ve örnek çalıştırma</span><span class="sxs-lookup"><span data-stu-id="18fd9-163">To set up, build and run the sample</span></span>  
  
1.  <span data-ttu-id="18fd9-164">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="18fd9-164">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="18fd9-165">Ayarlanacak Machine.config Düzenle `enableLoggingKnownPii` özniteliğini `true`, gerekirse üst düğüm ekleme.</span><span class="sxs-lookup"><span data-stu-id="18fd9-165">Edit Machine.config to set the `enableLoggingKnownPii` attribute to `true`, adding the parent nodes if necessary.</span></span>  
  
3.  <span data-ttu-id="18fd9-166">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="18fd9-166">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="18fd9-167">Tek veya çapraz bilgisayar yapılandırmasında örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="18fd9-167">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
#### <a name="to-clean-up-the-sample"></a><span data-ttu-id="18fd9-168">Örnek temizlemek için</span><span class="sxs-lookup"><span data-stu-id="18fd9-168">To clean up the sample</span></span>  
  
1.  <span data-ttu-id="18fd9-169">Ayarlanacak Machine.config Düzenle `enableLoggingKnownPii` özniteliğini `false`.</span><span class="sxs-lookup"><span data-stu-id="18fd9-169">Edit Machine.config to set the `enableLoggingKnownPii` attribute to `false`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18fd9-170">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="18fd9-170">See Also</span></span>  
 [<span data-ttu-id="18fd9-171">AppFabric izleme örnekleri</span><span class="sxs-lookup"><span data-stu-id="18fd9-171">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
