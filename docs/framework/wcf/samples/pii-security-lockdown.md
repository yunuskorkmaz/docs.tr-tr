---
title: PII Güvenlik Kilidi
ms.date: 03/30/2017
ms.assetid: c44fb338-9527-4dd0-8607-b8787d15acb4
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: ca85a620638509e183703f7e80c01ea20fadbc81
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43555202"
---
# <a name="pii-security-lockdown"></a><span data-ttu-id="e32c8-102">PII Güvenlik Kilidi</span><span class="sxs-lookup"><span data-stu-id="e32c8-102">PII Security Lockdown</span></span>
<span data-ttu-id="e32c8-103">Bu örnek, bir Windows Communication Foundation (WCF) hizmeti tarafından güvenlikle ilgili çeşitli özelliklerini denetlemek nasıl gösterir:</span><span class="sxs-lookup"><span data-stu-id="e32c8-103">This sample demonstrates how to control several security-related features of a Windows Communication Foundation (WCF) service by:</span></span>  
  
-   <span data-ttu-id="e32c8-104">Bir hizmetin yapılandırma dosyasındaki hassas bilgileri şifrelemek üzere.</span><span class="sxs-lookup"><span data-stu-id="e32c8-104">Encrypting sensitive information in a service's configuration file.</span></span>  
  
-   <span data-ttu-id="e32c8-105">Böylece hizmet alt dizinleri iç içe öğeleri yapılandırma dosyasındaki kilitleme ayarları geçersiz kılamazsınız.</span><span class="sxs-lookup"><span data-stu-id="e32c8-105">Locking elements in the configuration file so that nested service subdirectories cannot override settings.</span></span>  
  
-   <span data-ttu-id="e32c8-106">İzleme ve ileti günlükleri, kişisel bilgilerin (PII) günlüğüne denetleme.</span><span class="sxs-lookup"><span data-stu-id="e32c8-106">Controlling the logging of Personally Identifiable Information (PII) in trace and message logs.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e32c8-107">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="e32c8-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="e32c8-108">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="e32c8-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e32c8-109">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="e32c8-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e32c8-110">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="e32c8-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\SecurityLockdown`  
  
## <a name="discussion"></a><span data-ttu-id="e32c8-111">Tartışma</span><span class="sxs-lookup"><span data-stu-id="e32c8-111">Discussion</span></span>  
 <span data-ttu-id="e32c8-112">Bu özelliklerin her biri ayrı ayrı veya birlikte bir hizmetin güvenlik denetimi yönleri için olabilir.</span><span class="sxs-lookup"><span data-stu-id="e32c8-112">Each of these features can be used separately or together to control aspects of a service's security.</span></span> <span data-ttu-id="e32c8-113">Bu, bir WCF Hizmeti güvenli hale getirme için kesin bir kılavuz değildir.</span><span class="sxs-lookup"><span data-stu-id="e32c8-113">This is not a definitive guide to securing a WCF service.</span></span>  
  
 <span data-ttu-id="e32c8-114">.NET Framework yapılandırma dosyalarının veritabanlarına bağlanmak için bağlantı dizeleri gibi hassas bilgiler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="e32c8-114">The .NET Framework configuration files can contain sensitive information such as connection strings to connect to databases.</span></span> <span data-ttu-id="e32c8-115">Paylaşılan ve Web barındırılan senaryolarda yapılandırma dosyasının içinde yer alan verileri sıradan görüntülemeye dayanıklı olması için bir hizmet yapılandırma dosyasında bu bilgileri şifrelemek için istenebilir.</span><span class="sxs-lookup"><span data-stu-id="e32c8-115">In shared, Web-hosted scenarios it may be desirable to encrypt this information in the configuration file for a service so that the data contained within the configuration file is resistant to casual viewing.</span></span> <span data-ttu-id="e32c8-116">.NET framework 2.0 ve sonraki Windows veri koruma uygulama programlama arabirimi (DPAPI) veya RSA şifreleme sağlayıcısını kullanarak yapılandırma dosyasının bölümlerini şifreler özelliğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e32c8-116">.NET Framework 2.0 and later has the ability to encrypt portions of the configuration file using the Windows Data Protection application programming interface (DPAPI) or the RSA Cryptographic provider.</span></span> <span data-ttu-id="e32c8-117">Bir yapılandırma dosyası seçme bölümlerini aspnet_regiis.exe DPAPI veya RSA kullanarak şifreleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e32c8-117">The aspnet_regiis.exe using the DPAPI or RSA can encrypt select portions of a configuration file.</span></span>  
  
 <span data-ttu-id="e32c8-118">Web barındırılan senaryolarda Hizmetleri diğer hizmetlerin dizinlerde olması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="e32c8-118">In Web-hosted scenarios it is possible to have services in subdirectories of other services.</span></span> <span data-ttu-id="e32c8-119">Varsayılan yapılandırma değerlerini belirlemek için anlamsal üst dizinindeki yapılandırma değerleri geçersiz kılmak için iç içe geçmiş dizinleri yapılandırma dosyalarında sağlar.</span><span class="sxs-lookup"><span data-stu-id="e32c8-119">The default semantic for determining configuration values allows configuration files in the nested directories to override the configuration values in the parent directory.</span></span> <span data-ttu-id="e32c8-120">Belirli durumlarda bu istenmeyen çeşitli nedenlerden dolayı olabilir.</span><span class="sxs-lookup"><span data-stu-id="e32c8-120">In certain situations this may be undesirable for a variety of reasons.</span></span> <span data-ttu-id="e32c8-121">WCF hizmeti yapılandırma destekleyen iç içe geçmiş bir hizmet kullanarak çalıştırıldığında yapılandırma değerlerini, böylece yapılandırma iç içe geçmiş kilitleme özel durum oluşturur, yapılandırma değerleri geçersiz.</span><span class="sxs-lookup"><span data-stu-id="e32c8-121">WCF service configuration supports the locking of configuration values so that nested configuration generates exceptions when a nested service is run using overridden configuration values.</span></span>  
  
 <span data-ttu-id="e32c8-122">Bu örnek, bilinen kişisel bilgilerin (PII) kullanıcı adı ve parola gibi izleme ve ileti günlüklerde günlüğe kaydetmeyi denetlemek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="e32c8-122">This sample demonstrates how to control the logging of known Personally Identifiable Information (PII) in trace and message logs, such as username and password.</span></span> <span data-ttu-id="e32c8-123">Belirli durumlarda PII günlüğe bir uygulamada hata ayıklama içinde önemli olabilir ancak varsayılan olarak, bilinen PII günlüğünü devre dışı.</span><span class="sxs-lookup"><span data-stu-id="e32c8-123">By default, logging of known PII is disabled however in certain situations logging of PII can be important in debugging an application.</span></span> <span data-ttu-id="e32c8-124">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="e32c8-124">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="e32c8-125">Ayrıca, bu örnek, izleme ve iletileri günlüğe kaydetme kullanır.</span><span class="sxs-lookup"><span data-stu-id="e32c8-125">In addition, this sample uses tracing and message logging.</span></span> <span data-ttu-id="e32c8-126">Daha fazla bilgi için [izleme ve ileti günlüğe kaydetme](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="e32c8-126">For more information, see the [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) sample.</span></span>  
  
## <a name="encrypting-configuration-file-elements"></a><span data-ttu-id="e32c8-127">Yapılandırma dosyası öğeleri şifreleme</span><span class="sxs-lookup"><span data-stu-id="e32c8-127">Encrypting Configuration File Elements</span></span>  
 <span data-ttu-id="e32c8-128">Paylaşılan Web barındırma ortamında güvenlik nedenleriyle, hassas bilgiler içerebilir, veritabanı bağlantı dizeleri gibi belirli yapılandırma öğelerini şifreleme istenebilir.</span><span class="sxs-lookup"><span data-stu-id="e32c8-128">For security purposes in a shared Web-hosting environment, it may be desirable to encrypt certain configuration elements, such as database connection strings that may contain sensitive information.</span></span> <span data-ttu-id="e32c8-129">Örneğin, % WINDIR%\Micrsoft.NET\Framework\v4.0.20728 .NET Framework klasörde bulunan aspnet_regiis.exe aracını kullanarak bir yapılandırma öğesi şifrelenmelidir.</span><span class="sxs-lookup"><span data-stu-id="e32c8-129">A configuration element may be encrypted using the aspnet_regiis.exe tool found in the .NET Framework folder For example, %WINDIR%\Micrsoft.NET\Framework\v4.0.20728.</span></span>  
  
#### <a name="to-encrypt-the-values-in-the-appsettings-section-in-webconfig-for-the-sample"></a><span data-ttu-id="e32c8-130">Değerleri için örnek Web.config dosyasındaki appSettings bölümündeki şifrelemek için</span><span class="sxs-lookup"><span data-stu-id="e32c8-130">To encrypt the values in the appSettings section in Web.config for the sample</span></span>  
  
1.  <span data-ttu-id="e32c8-131">Açık bir komut istemi kullanarak Başlat -> Çalıştır...</span><span class="sxs-lookup"><span data-stu-id="e32c8-131">Open a command prompt by using Start->Run….</span></span> <span data-ttu-id="e32c8-132">Yazın `cmd` tıklatıp **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="e32c8-132">Type in `cmd` and click **OK**.</span></span>  
  
2.  <span data-ttu-id="e32c8-133">Aşağıdaki komutu gönderdikten tarafından geçerli .NET Framework dizinine gidin: `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`.</span><span class="sxs-lookup"><span data-stu-id="e32c8-133">Navigate to the current .NET Framework directory by issuing the following command: `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`.</span></span>  
  
3.  <span data-ttu-id="e32c8-134">Aşağıdaki komutu gönderdikten tarafından Web.config klasöründe appSettings yapılandırma ayarlarını şifrele: `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`.</span><span class="sxs-lookup"><span data-stu-id="e32c8-134">Encrypt the appSettings configuration settings in the Web.config folder by issuing the following command: `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`.</span></span>  
  
 <span data-ttu-id="e32c8-135">ASP.NET yapılandırması dpapı'ye bir nasıl yapılır okuyarak yapılandırma dosyalarını bölümlerini şifreleme hakkında daha fazla bilgi bulunabilir ([Güvenli ASP.NET uygulamaları: kimlik doğrulaması, yetkilendirme ve güvenli iletişimi](https://go.microsoft.com/fwlink/?LinkId=95137)) ve ASP.NET yapılandırma RSA üzerinde bir nasıl yapılır ([nasıl yapılır: ASP.NET 2.0 kullanarak RSA şifreleme yapılandırma bölümlerde](https://go.microsoft.com/fwlink/?LinkId=95138)).</span><span class="sxs-lookup"><span data-stu-id="e32c8-135">More information about encrypting sections of configuration files can be found by reading a how-to on DPAPI in ASP.NET configuration ([Building Secure ASP.NET Applications: Authentication, Authorization, and Secure Communication](https://go.microsoft.com/fwlink/?LinkId=95137)) and a how-to on RSA in ASP.NET configuration ([How To: Encrypt Configuration Sections in ASP.NET 2.0 Using RSA](https://go.microsoft.com/fwlink/?LinkId=95138)).</span></span>  
  
## <a name="locking-configuration-file-elements"></a><span data-ttu-id="e32c8-136">Kilitleme yapılandırma dosyası öğeleri</span><span class="sxs-lookup"><span data-stu-id="e32c8-136">Locking configuration file elements</span></span>  
 <span data-ttu-id="e32c8-137">Web barındırılan senaryolarda Hizmetleri Hizmetleri dizinlerde olması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="e32c8-137">In Web-hosted scenarios, it is possible to have services in subdirectories of services.</span></span> <span data-ttu-id="e32c8-138">Bu gibi durumlarda, hizmet alt dizinindeki yapılandırma değerlerini Machine.Config'deki değerlerini inceleme ve sırayla tüm üst dizinlerin dizin ağacında taşıma ve son birleştirme Web.config dosyalarında ile birleştiriliyor hesaplanır Web.config dosyasında hizmet içeren dizin.</span><span class="sxs-lookup"><span data-stu-id="e32c8-138">In these situations, configuration values for the service in the subdirectory are calculated by examining values in Machine.config and successively merging with any Web.config files in parent directories moving down the directory tree and finally merging the Web.config file in the directory that contains the service.</span></span> <span data-ttu-id="e32c8-139">Çoğu yapılandırma öğeleri için varsayılan davranış, alt üst dizinlerin ayarlanan değerleri geçersiz kılmak için yapılandırma dosyalarında izin vermektir.</span><span class="sxs-lookup"><span data-stu-id="e32c8-139">The default behavior for most configuration elements is to allow configuration files in subdirectories to override the values set in parent directories.</span></span> <span data-ttu-id="e32c8-140">Belirli durumlarda alt dizinleri yapılandırma dosyalarında üst dizini yapılandırma değerleri geçersiz kılmasını önlemek için istenebilir.</span><span class="sxs-lookup"><span data-stu-id="e32c8-140">In certain situations it may be desirable to prevent configuration files in subdirectories from overriding values set in parent directory configuration.</span></span>  
  
 <span data-ttu-id="e32c8-141">.NET Framework yapılandırma dosyası öğeleri kilitli yapılandırma öğeleri geçersiz kılan yapılandırmaları çalışma zamanı özel durumlar, kilitlemek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="e32c8-141">The .NET Framework provides a way to lock configuration file elements so that configurations that override locked configuration elements throw run-time exceptions.</span></span>  
  
 <span data-ttu-id="e32c8-142">Bir yapılandırma öğesi belirterek kilitlenip `lockItem` öznitelik yapılandırma dosyasında bir düğüm için örneğin, böylece hesaplayıcı Hizmetleri'nde yapılandırma dosyalarını içe CalculatorServiceBehavior düğüm yapılandırma dosyasındaki kilitlemek için değişiklik davranışı, aşağıdaki yapılandırma kullanılabilir olamaz.</span><span class="sxs-lookup"><span data-stu-id="e32c8-142">A configuration element can be locked by specifying the `lockItem` attribute for a node in the configuration file, for example, to lock the CalculatorServiceBehavior node in the configuration file so that calculator services in nested configuration files cannot change the behavior, the following configuration can be used.</span></span>  
  
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
  
 <span data-ttu-id="e32c8-143">Yapılandırma öğelerini kilitleme daha belirli olabilir.</span><span class="sxs-lookup"><span data-stu-id="e32c8-143">Locking of configuration elements can be more specific.</span></span> <span data-ttu-id="e32c8-144">Öğelerinin bir listesini görmek için bir değer olarak belirtilebilir `lockElements` bir dizi öğeleri alt öğelerinin koleksiyonu içinde kilitlenemedi.</span><span class="sxs-lookup"><span data-stu-id="e32c8-144">A list of elements can be specified as the value to the `lockElements` to lock a set of elements within a collection of sub-elements.</span></span> <span data-ttu-id="e32c8-145">Özniteliklerin bir listesi için değer olarak belirtilen `lockAttributes` öznitelikleri bir öğe içinde bir dizi kilitlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="e32c8-145">A list of attributes can be specified as the value to the `lockAttributes` to lock a set of attributes within an element.</span></span> <span data-ttu-id="e32c8-146">Bir koleksiyonun tamamını öğeler veya öznitelikleri belirterek dışında belirtilen bir liste kilitlenebilir `lockAllElementsExcept` veya `lockAllAttributesExcept` düğümünde öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="e32c8-146">An entire collection of elements or attributes can be locked except for a specified list by specifying the `lockAllElementsExcept` or `lockAllAttributesExcept` attributes on a node.</span></span>  
  
## <a name="pii-logging-configuration"></a><span data-ttu-id="e32c8-147">PII günlük kaydı yapılandırması</span><span class="sxs-lookup"><span data-stu-id="e32c8-147">PII Logging Configuration</span></span>  
 <span data-ttu-id="e32c8-148">PII günlüğe iki anahtar tarafından denetlenir: bilgisayar genelinde bir ayar izin veren veya reddeden PII PII günlüğe her geçiş yapmak bir uygulama Yöneticisi izin veren bir uygulama ayarı ve günlüğe kaydetme için bilgisayar yöneticisi veren Machine.config bulundu Kaynak Web.config veya App.config dosyasında.</span><span class="sxs-lookup"><span data-stu-id="e32c8-148">Logging of PII is controlled by two switches: a computer-wide setting found in Machine.config that allows a computer administrator to permit or deny logging of PII and an application setting that allows an application administrator to toggle logging of PII for each source in a Web.config or App.config file.</span></span>  
  
 <span data-ttu-id="e32c8-149">Bilgisayar genelinde ayarı ayarlanmasıyla denetlenir `enableLoggingKnownPii` için `true` veya `false`, `machineSettings` Machine.config öğesinde. Örneğin, aşağıdaki uygulamaların PII, günlüğü etkinleştirmek sağlar.</span><span class="sxs-lookup"><span data-stu-id="e32c8-149">The computer-wide setting is controlled by setting `enableLoggingKnownPii` to `true` or `false`, in the `machineSettings` element in Machine.config. For example, the following allows applications to turn on logging of PII.</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <machineSettings enableLoggingKnownPii="true" />  
    </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
>  <span data-ttu-id="e32c8-150">Machine.config dosyasının varsayılan konum vardır: % WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.</span><span class="sxs-lookup"><span data-stu-id="e32c8-150">The Machine.config file has a default location: %WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.</span></span>  
  
 <span data-ttu-id="e32c8-151">Varsa `enableLoggingKnownPii` Machine.config dosyasına öznitelik yoksa, PII günlüğe izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="e32c8-151">If the `enableLoggingKnownPii` attribute is not present in Machine.config, logging of PII is not allowed.</span></span>  
  
 <span data-ttu-id="e32c8-152">Bir uygulama ayarlayarak yapılır için PII günlüğü etkinleştirme `logKnownPii` için kaynak öğesinin özniteliği `true` veya `false` Web.config veya App.config dosyasında.</span><span class="sxs-lookup"><span data-stu-id="e32c8-152">Enabling logging of PII for an application is done by setting the `logKnownPii` attribute of the source element to `true` or `false` in the Web.config or App.config file.</span></span> <span data-ttu-id="e32c8-153">Örneğin, aşağıdaki PII, hem ileti günlüğe kaydetme ve izleme günlüğü için günlük kaydını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="e32c8-153">For example, the following enables logging of PII for both message logging and trace logging.</span></span>  
  
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
  
 <span data-ttu-id="e32c8-154">Varsa `logKnownPii` özniteliği belirtilmezse, ardından PII günlüğe kaydedilmez.</span><span class="sxs-lookup"><span data-stu-id="e32c8-154">If the `logKnownPii` attribute is not specified, then PII is not logged.</span></span>  
  
 <span data-ttu-id="e32c8-155">PII hem de yalnızca oturum `enableLoggingKnownPii` ayarlanır `true`, ve `logKnownPii` ayarlanır `true`.</span><span class="sxs-lookup"><span data-stu-id="e32c8-155">PII is only logged if both `enableLoggingKnownPii` is set to `true`, and `logKnownPii` is set to `true`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e32c8-156">System.Diagnostics yapılandırma dosyasında listelenen ilk öğe dışında tüm kaynaklarında tüm öznitelikler yok sayar.</span><span class="sxs-lookup"><span data-stu-id="e32c8-156">System.Diagnostics ignores all attributes on all sources except the first one listed in the configuration file.</span></span> <span data-ttu-id="e32c8-157">Ekleme `logKnownPii` yapılandırma dosyasındaki ikinci kaynağına özniteliği etkisizdir.</span><span class="sxs-lookup"><span data-stu-id="e32c8-157">Adding the `logKnownPii` attribute to the second source in the configuration file has no effect.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e32c8-158">Bu örneği çalıştırmak için Machine.config el ile değiştirilmesini içerir. Yanlış değer veya sözdizimi Machine.config değiştirmek tüm .NET Framework uygulamaların çalıştırılmasını engelleyebilir dikkatli olunması.</span><span class="sxs-lookup"><span data-stu-id="e32c8-158">To run this sample involves manual modification of Machine.config. Care should be taken when modifying Machine.config as incorrect values or syntax may prevent all .NET Framework applications from running.</span></span>  
  
 <span data-ttu-id="e32c8-159">Yapılandırma dosyası öğelerini DPAPI ve RSA kullanarak şifreleme de mümkündür.</span><span class="sxs-lookup"><span data-stu-id="e32c8-159">It is also possible to encrypt configuration file elements using DPAPI and RSA.</span></span> <span data-ttu-id="e32c8-160">Daha fazla bilgi için aşağıdaki bağlantılara bakın:</span><span class="sxs-lookup"><span data-stu-id="e32c8-160">For more information, see the following links:</span></span>  
  
-   [<span data-ttu-id="e32c8-161">Güvenli bir ASP.NET uygulamaları: Kimlik doğrulaması, yetkilendirme ve güvenli iletişim</span><span class="sxs-lookup"><span data-stu-id="e32c8-161">Building Secure ASP.NET Applications: Authentication, Authorization, and Secure Communication</span></span>](https://go.microsoft.com/fwlink/?LinkId=95137)  
  
-   [<span data-ttu-id="e32c8-162">Nasıl yapılır: ASP.NET 2.0 yapılandırma bölümleri şifrelemek RSA kullanarak</span><span class="sxs-lookup"><span data-stu-id="e32c8-162">How To: Encrypt Configuration Sections in ASP.NET 2.0 Using RSA</span></span>](https://go.microsoft.com/fwlink/?LinkId=95138)  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e32c8-163">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="e32c8-163">To set up, build and run the sample</span></span>  
  
1.  <span data-ttu-id="e32c8-164">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e32c8-164">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="e32c8-165">Ayarlanacak Machine.config Düzenle `enableLoggingKnownPii` özniteliğini `true`, gerekirse, üst düğümleri ekleme.</span><span class="sxs-lookup"><span data-stu-id="e32c8-165">Edit Machine.config to set the `enableLoggingKnownPii` attribute to `true`, adding the parent nodes if necessary.</span></span>  
  
3.  <span data-ttu-id="e32c8-166">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e32c8-166">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="e32c8-167">Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e32c8-167">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
#### <a name="to-clean-up-the-sample"></a><span data-ttu-id="e32c8-168">Örneği temizlemek için</span><span class="sxs-lookup"><span data-stu-id="e32c8-168">To clean up the sample</span></span>  
  
1.  <span data-ttu-id="e32c8-169">Ayarlanacak Machine.config Düzenle `enableLoggingKnownPii` özniteliğini `false`.</span><span class="sxs-lookup"><span data-stu-id="e32c8-169">Edit Machine.config to set the `enableLoggingKnownPii` attribute to `false`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e32c8-170">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e32c8-170">See Also</span></span>  
 [<span data-ttu-id="e32c8-171">AppFabric izleme örnekleri</span><span class="sxs-lookup"><span data-stu-id="e32c8-171">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
