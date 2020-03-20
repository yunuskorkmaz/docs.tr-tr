---
title: PII Güvenlik Kilidi
ms.date: 03/30/2017
ms.assetid: c44fb338-9527-4dd0-8607-b8787d15acb4
ms.openlocfilehash: ad4f4a024b04a028b815faedded58713e001cab0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144272"
---
# <a name="pii-security-lockdown"></a><span data-ttu-id="82276-102">PII Güvenlik Kilidi</span><span class="sxs-lookup"><span data-stu-id="82276-102">PII Security Lockdown</span></span>
<span data-ttu-id="82276-103">Bu örnek, bir Windows Communication Foundation (WCF) hizmetinin güvenlikle ilgili çeşitli özelliklerinin nasıl denetlenir olduğunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="82276-103">This sample demonstrates how to control several security-related features of a Windows Communication Foundation (WCF) service by:</span></span>  
  
- <span data-ttu-id="82276-104">Bir hizmetin yapılandırma dosyasındaki hassas bilgileri şifreleme.</span><span class="sxs-lookup"><span data-stu-id="82276-104">Encrypting sensitive information in a service's configuration file.</span></span>  
  
- <span data-ttu-id="82276-105">İç içe hizmet alt dizinlerinin ayarları geçersiz kılamaması için yapılandırma dosyasındaki öğeleri kilitleme.</span><span class="sxs-lookup"><span data-stu-id="82276-105">Locking elements in the configuration file so that nested service subdirectories cannot override settings.</span></span>  
  
- <span data-ttu-id="82276-106">İzleme ve ileti günlüklerinde Kişisel Olarak Tanımlanabilir Bilgilerin (PII) günlüğe kaydedilmesini denetleme.</span><span class="sxs-lookup"><span data-stu-id="82276-106">Controlling the logging of Personally Identifiable Information (PII) in trace and message logs.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="82276-107">Örnekler bilgisayarınıza zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="82276-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="82276-108">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="82276-108">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="82276-109">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="82276-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="82276-110">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="82276-110">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\SecurityLockdown`  
  
## <a name="discussion"></a><span data-ttu-id="82276-111">Tartışma</span><span class="sxs-lookup"><span data-stu-id="82276-111">Discussion</span></span>  
 <span data-ttu-id="82276-112">Bu özelliklerin her biri, bir hizmetin güvenliğinin yönlerini denetlemek için ayrı ayrı veya birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="82276-112">Each of these features can be used separately or together to control aspects of a service's security.</span></span> <span data-ttu-id="82276-113">Bu, bir WCF hizmetini güvence altına almak için kesin bir kılavuz değildir.</span><span class="sxs-lookup"><span data-stu-id="82276-113">This is not a definitive guide to securing a WCF service.</span></span>  
  
 <span data-ttu-id="82276-114">.NET Framework yapılandırma dosyaları veritabanlarına bağlanmak için bağlantı dizeleri gibi hassas bilgiler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="82276-114">The .NET Framework configuration files can contain sensitive information such as connection strings to connect to databases.</span></span> <span data-ttu-id="82276-115">Paylaşılan, Web tarafından barındırılan senaryolarda, yapılandırma dosyasında bulunan verilerin gündelik görüntülemeye karşı dayanıklı olması için bu bilgileri bir hizmet için yapılandırma dosyasında şifrelemek istenebilir.</span><span class="sxs-lookup"><span data-stu-id="82276-115">In shared, Web-hosted scenarios it may be desirable to encrypt this information in the configuration file for a service so that the data contained within the configuration file is resistant to casual viewing.</span></span> <span data-ttu-id="82276-116">.NET Framework 2.0 ve daha sonra Windows Veri Koruma uygulama programlama arabirimi (DPAPI) veya RSA Şifreleme sağlayıcısı kullanarak yapılandırma dosyasının bölümlerini şifreleme yeteneğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="82276-116">.NET Framework 2.0 and later has the ability to encrypt portions of the configuration file using the Windows Data Protection application programming interface (DPAPI) or the RSA Cryptographic provider.</span></span> <span data-ttu-id="82276-117">DPAPI veya RSA kullanan aspnet_regiis.exe, yapılandırma dosyasının belirli bölümlerini şifreleyebilir.</span><span class="sxs-lookup"><span data-stu-id="82276-117">The aspnet_regiis.exe using the DPAPI or RSA can encrypt select portions of a configuration file.</span></span>  
  
 <span data-ttu-id="82276-118">Web tarafından barındırılan senaryolarda, diğer hizmetlerin alt dizilişlerinde hizmetlerin olması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="82276-118">In Web-hosted scenarios it is possible to have services in subdirectories of other services.</span></span> <span data-ttu-id="82276-119">Yapılandırma değerlerini belirlemek için varsayılan anlamsal, iç içe alınan dizinlerde bulunan yapılandırma dosyalarının üst dizindeki yapılandırma değerlerini geçersiz kılmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="82276-119">The default semantic for determining configuration values allows configuration files in the nested directories to override the configuration values in the parent directory.</span></span> <span data-ttu-id="82276-120">Bazı durumlarda bu çeşitli nedenlerle istenmeyen olabilir.</span><span class="sxs-lookup"><span data-stu-id="82276-120">In certain situations this may be undesirable for a variety of reasons.</span></span> <span data-ttu-id="82276-121">WCF hizmet yapılandırması yapılandırma değerlerinin kilitlenmesini destekler, böylece iç içe geçmiş yapılandırma, iç içe geçmiş bir hizmet geçersiz yapılandırma değerleri kullanılarak çalıştırıldığında özel durumlar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="82276-121">WCF service configuration supports the locking of configuration values so that nested configuration generates exceptions when a nested service is run using overridden configuration values.</span></span>  
  
 <span data-ttu-id="82276-122">Bu örnek, kullanıcı adı ve parola gibi izleme ve ileti günlüklerinde bilinen Kişisel Tanıtıcı Bilgilerin (PII) günlüğe kaydetmenin nasıl denetlenir olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="82276-122">This sample demonstrates how to control the logging of known Personally Identifiable Information (PII) in trace and message logs, such as username and password.</span></span> <span data-ttu-id="82276-123">Varsayılan olarak, bilinen KIŞISEL Bilgiler'in günlüğe kaydedilmesi devre dışı bırakılır, ancak bazı durumlarda kişisel bilgi nin günlüğe kaydedilmesi bir uygulamanın hata ayıklanmasında önemli olabilir.</span><span class="sxs-lookup"><span data-stu-id="82276-123">By default, logging of known PII is disabled however in certain situations logging of PII can be important in debugging an application.</span></span> <span data-ttu-id="82276-124">Bu örnek [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="82276-124">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="82276-125">Buna ek olarak, bu örnek izleme ve ileti günlüğe kaydetme kullanır.</span><span class="sxs-lookup"><span data-stu-id="82276-125">In addition, this sample uses tracing and message logging.</span></span> <span data-ttu-id="82276-126">Daha fazla bilgi için [İzleme ve İleti Günlüğü](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) örneğine bakın.</span><span class="sxs-lookup"><span data-stu-id="82276-126">For more information, see the [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) sample.</span></span>  
  
## <a name="encrypting-configuration-file-elements"></a><span data-ttu-id="82276-127">Yapılandırma Dosya Öğelerini Şifreleme</span><span class="sxs-lookup"><span data-stu-id="82276-127">Encrypting Configuration File Elements</span></span>  
 <span data-ttu-id="82276-128">Paylaşılan bir Web barındırma ortamındaki güvenlik amacıyla, hassas bilgiler içerebilecek veritabanı bağlantı dizeleri gibi belirli yapılandırma öğelerini şifrelemek isteolabilir.</span><span class="sxs-lookup"><span data-stu-id="82276-128">For security purposes in a shared Web-hosting environment, it may be desirable to encrypt certain configuration elements, such as database connection strings that may contain sensitive information.</span></span> <span data-ttu-id="82276-129">Bir yapılandırma öğesi .NET Framework klasöründe bulunan aspnet_regiis.exe aracı kullanılarak şifrelenebilir Örneğin, %WINDIR%\Microsoft.NET\Framework\v4.0.20728.</span><span class="sxs-lookup"><span data-stu-id="82276-129">A configuration element may be encrypted using the aspnet_regiis.exe tool found in the .NET Framework folder For example, %WINDIR%\Microsoft.NET\Framework\v4.0.20728.</span></span>  
  
#### <a name="to-encrypt-the-values-in-the-appsettings-section-in-webconfig-for-the-sample"></a><span data-ttu-id="82276-130">Örnek için Web.config'deki uygulama Ayarlar bölümündeki değerleri şifrelemek için</span><span class="sxs-lookup"><span data-stu-id="82276-130">To encrypt the values in the appSettings section in Web.config for the sample</span></span>  
  
1. <span data-ttu-id="82276-131">Başlat->Çalıştır'ı kullanarak komut istemini açın....</span><span class="sxs-lookup"><span data-stu-id="82276-131">Open a command prompt by using Start->Run….</span></span> <span data-ttu-id="82276-132">Yazın `cmd` ve **Tamam'ı**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="82276-132">Type in `cmd` and click **OK**.</span></span>  
  
2. <span data-ttu-id="82276-133">Aşağıdaki komutu vererek geçerli .NET Framework dizinine `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`gidin: .</span><span class="sxs-lookup"><span data-stu-id="82276-133">Navigate to the current .NET Framework directory by issuing the following command: `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`.</span></span>  
  
3. <span data-ttu-id="82276-134">Aşağıdaki komutu vererek Web.config klasöründeki uygulama Ayarları `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`ayarlarını şifreleyin: .</span><span class="sxs-lookup"><span data-stu-id="82276-134">Encrypt the appSettings configuration settings in the Web.config folder by issuing the following command: `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`.</span></span>  
  
 <span data-ttu-id="82276-135">Yapılandırma dosyalarının bölümlerini şifreleme hakkında daha fazla bilgi, ASP.NET yapılandırmada DPAPI'de nasıl yapılır[(Güvenli ASP.NET Uygulamaları Oluşturma: Kimlik Doğrulama, Yetkilendirme ve Güvenli İletişim)](https://docs.microsoft.com/previous-versions/msp-n-p/ff649248(v=pandp.10))ve ASP.NET yapılandırmada RSA'da nasıl yapılır[(2.0'da yapılandırma bölümlerini ASP.NET'da nasıl şifrelenir) okuyarak](https://docs.microsoft.com/previous-versions/msp-n-p/ff650304(v=pandp.10))bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="82276-135">More information about encrypting sections of configuration files can be found by reading a how-to on DPAPI in ASP.NET configuration ([Building Secure ASP.NET Applications: Authentication, Authorization, and Secure Communication](https://docs.microsoft.com/previous-versions/msp-n-p/ff649248(v=pandp.10))) and a how-to on RSA in ASP.NET configuration ([How To: Encrypt Configuration Sections in ASP.NET 2.0 Using RSA](https://docs.microsoft.com/previous-versions/msp-n-p/ff650304(v=pandp.10))).</span></span>  
  
## <a name="locking-configuration-file-elements"></a><span data-ttu-id="82276-136">Yapılandırma dosya öğelerini kilitleme</span><span class="sxs-lookup"><span data-stu-id="82276-136">Locking configuration file elements</span></span>  
 <span data-ttu-id="82276-137">Web tarafından barındırılan senaryolarda, hizmetlerin alt dizilişlerinde hizmetlerin olması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="82276-137">In Web-hosted scenarios, it is possible to have services in subdirectories of services.</span></span> <span data-ttu-id="82276-138">Bu gibi durumlarda, alt dizindeki hizmetin yapılandırma değerleri Machine.config'deki değerler incelenerek hesaplanır ve ana dizinlerde herhangi bir Web.config dosyasıyla art arda birleştirilerek dizin ağacından aşağı iner ve son olarak Hizmeti içeren dizindeki Web.config dosyası.</span><span class="sxs-lookup"><span data-stu-id="82276-138">In these situations, configuration values for the service in the subdirectory are calculated by examining values in Machine.config and successively merging with any Web.config files in parent directories moving down the directory tree and finally merging the Web.config file in the directory that contains the service.</span></span> <span data-ttu-id="82276-139">Yapılandırma öğelerinin çoğu için varsayılan davranış, alt dizinlerde yapılandırma dosyalarının üst dizinlerde ayarlanan değerleri geçersiz kılmasına izin vermektir.</span><span class="sxs-lookup"><span data-stu-id="82276-139">The default behavior for most configuration elements is to allow configuration files in subdirectories to override the values set in parent directories.</span></span> <span data-ttu-id="82276-140">Bazı durumlarda, alt dizinlerde yapılandırma dosyalarının üst dizin yapılandırmasında ayarlanan değerleri geçersiz kılmasından öngörmek istenebilir.</span><span class="sxs-lookup"><span data-stu-id="82276-140">In certain situations it may be desirable to prevent configuration files in subdirectories from overriding values set in parent directory configuration.</span></span>  
  
 <span data-ttu-id="82276-141">.NET Framework, kilitli yapılandırma öğelerini geçersiz kılan yapılandırmaların çalışma zamanı özel durumları atmasını sağlayacak şekilde yapılandırma dosya öğelerini kilitlemenin bir yolunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="82276-141">The .NET Framework provides a way to lock configuration file elements so that configurations that override locked configuration elements throw run-time exceptions.</span></span>  
  
 <span data-ttu-id="82276-142">Yapılandırma öğesi, iç içe olan `lockItem` yapılandırma dosyalarındaki hesap makinesi hizmetlerinin davranışı değiştirememesi için yapılandırma dosyasındaki Hesap Makinesi Davranışı düğümünü kilitlemek için yapılandırma dosyasındaki bir düğümün özniteliğini belirterek kilitlenebilir, aşağıdaki yapılandırma kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="82276-142">A configuration element can be locked by specifying the `lockItem` attribute for a node in the configuration file, for example, to lock the CalculatorServiceBehavior node in the configuration file so that calculator services in nested configuration files cannot change the behavior, the following configuration can be used.</span></span>  
  
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
  
 <span data-ttu-id="82276-143">Yapılandırma öğelerinin kilitlenme daha spesifik olabilir.</span><span class="sxs-lookup"><span data-stu-id="82276-143">Locking of configuration elements can be more specific.</span></span> <span data-ttu-id="82276-144">Öğelerin listesi, alt öğeler koleksiyonundaki `lockElements` bir öğe kümesini kilitlemek için gereken değer olarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="82276-144">A list of elements can be specified as the value to the `lockElements` to lock a set of elements within a collection of sub-elements.</span></span> <span data-ttu-id="82276-145">Özniteliklerin listesi, bir öğe içindeki `lockAttributes` öznitelikler kümesini kilitlemek için gereken değer olarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="82276-145">A list of attributes can be specified as the value to the `lockAttributes` to lock a set of attributes within an element.</span></span> <span data-ttu-id="82276-146">Bir düğüm üzerinde `lockAllElementsExcept` öznitelikleri belirterek belirli bir liste dışında `lockAllAttributesExcept` öğeler in tüm bir koleksiyon kilitlenebilir.</span><span class="sxs-lookup"><span data-stu-id="82276-146">An entire collection of elements or attributes can be locked except for a specified list by specifying the `lockAllElementsExcept` or `lockAllAttributesExcept` attributes on a node.</span></span>  
  
## <a name="pii-logging-configuration"></a><span data-ttu-id="82276-147">PII Günlük Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="82276-147">PII Logging Configuration</span></span>  
 <span data-ttu-id="82276-148">KIŞISEL Bilgiler'in günlüğe kaydetmesi iki anahtarla denetlenir: Machine.config'de bulunan ve bilgisayar yöneticisinin KIŞISEL Bilgiler günlüğe kaydetmesine veya reddetmesine olanak tanıyan bilgisayar çapında bir ayar ve uygulama yöneticisinin her biri için kişisel bilgi günleme günlemasını geçişini sağlayan bir uygulama ayarı bir Web.config veya App.config dosyasında kaynak.</span><span class="sxs-lookup"><span data-stu-id="82276-148">Logging of PII is controlled by two switches: a computer-wide setting found in Machine.config that allows a computer administrator to permit or deny logging of PII and an application setting that allows an application administrator to toggle logging of PII for each source in a Web.config or App.config file.</span></span>  
  
 <span data-ttu-id="82276-149">Bilgisayar genelindeayar, `enableLoggingKnownPii` Machine.config'deki `true` `false` `machineSettings` elemana ayarlayarak veya , Örneğin, aşağıdaki uygulamaların KIŞISEL Bilgiler günlüğe kaydetmeyi açmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="82276-149">The computer-wide setting is controlled by setting `enableLoggingKnownPii` to `true` or `false`, in the `machineSettings` element in Machine.config. For example, the following allows applications to turn on logging of PII.</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <machineSettings enableLoggingKnownPii="true" />  
    </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
> <span data-ttu-id="82276-150">Machine.config dosyası varsayılan bir konuma sahiptir: %WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.</span><span class="sxs-lookup"><span data-stu-id="82276-150">The Machine.config file has a default location: %WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.</span></span>  
  
 <span data-ttu-id="82276-151">`enableLoggingKnownPii` Özellik Machine.config'de yoksa, KIŞISEL Bilgiler'in günlüğe kaydetmesine izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="82276-151">If the `enableLoggingKnownPii` attribute is not present in Machine.config, logging of PII is not allowed.</span></span>  
  
 <span data-ttu-id="82276-152">Bir uygulama için KIŞISEL Bilgiler'in günlüğe `logKnownPii` kaydedilmesini etkinleştirme, `true` `false` kaynak öğenin özniteliğini Web.config veya App.config dosyasına veya bu dosyaya ayarlayarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="82276-152">Enabling logging of PII for an application is done by setting the `logKnownPii` attribute of the source element to `true` or `false` in the Web.config or App.config file.</span></span> <span data-ttu-id="82276-153">Örneğin, aşağıdaki, hem ileti günlüğe kaydetme hem de izleme günlüğü için KIŞISEL Bilgiler günlüğe kaydetmeyi sağlar.</span><span class="sxs-lookup"><span data-stu-id="82276-153">For example, the following enables logging of PII for both message logging and trace logging.</span></span>  
  
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
  
 <span data-ttu-id="82276-154">`logKnownPii` Öznitelik belirtilmemişse, kişisel bilgiler günlüğe kaydedilmez.</span><span class="sxs-lookup"><span data-stu-id="82276-154">If the `logKnownPii` attribute is not specified, then PII is not logged.</span></span>  
  
 <span data-ttu-id="82276-155">Kişisel Bilgiler yalnızca her `enableLoggingKnownPii` ikisi de `true`ayarlanmışsa `logKnownPii` `true`ve .'ye ayarlanmışsa günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="82276-155">PII is only logged if both `enableLoggingKnownPii` is set to `true`, and `logKnownPii` is set to `true`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="82276-156">System.Diagnostics, yapılandırma dosyasında listelenen ilk i</span><span class="sxs-lookup"><span data-stu-id="82276-156">System.Diagnostics ignores all attributes on all sources except the first one listed in the configuration file.</span></span> <span data-ttu-id="82276-157">`logKnownPii` Yapılandırma dosyasındaki ikinci kaynağa öznitelik eklemenin hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="82276-157">Adding the `logKnownPii` attribute to the second source in the configuration file has no effect.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="82276-158">Bu örneği çalıştırmak için Machine.config manuel modifikasyon içerir. Machine.config'i yanlış değerler veya sözdizimi olarak değiştirirken tüm .NET Framework uygulamalarının çalışmasını engelleyebilir.</span><span class="sxs-lookup"><span data-stu-id="82276-158">To run this sample involves manual modification of Machine.config. Care should be taken when modifying Machine.config as incorrect values or syntax may prevent all .NET Framework applications from running.</span></span>  
  
 <span data-ttu-id="82276-159">DPAPI ve RSA kullanarak yapılandırma dosya öğelerini şifrelemek de mümkündür.</span><span class="sxs-lookup"><span data-stu-id="82276-159">It is also possible to encrypt configuration file elements using DPAPI and RSA.</span></span> <span data-ttu-id="82276-160">Daha fazla bilgi için aşağıdaki bağlantılara bakın:</span><span class="sxs-lookup"><span data-stu-id="82276-160">For more information, see the following links:</span></span>  
  
- <span data-ttu-id="82276-161">[Bina Güvenli ASP.NET Uygulamaları: Kimlik Doğrulama, Yetkilendirme ve Güvenli İletişim](https://docs.microsoft.com/previous-versions/msp-n-p/ff649248(v=pandp.10))</span><span class="sxs-lookup"><span data-stu-id="82276-161">[Building Secure ASP.NET Applications: Authentication, Authorization, and Secure Communication](https://docs.microsoft.com/previous-versions/msp-n-p/ff649248(v=pandp.10))</span></span>  
  
- <span data-ttu-id="82276-162">[Nasıl YapılSın: RSA kullanarak ASP.NET 2.0'da Yapılandırma Bölümlerini Şifreleme](https://docs.microsoft.com/previous-versions/msp-n-p/ff650304(v=pandp.10))</span><span class="sxs-lookup"><span data-stu-id="82276-162">[How To: Encrypt Configuration Sections in ASP.NET 2.0 Using RSA](https://docs.microsoft.com/previous-versions/msp-n-p/ff650304(v=pandp.10))</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="82276-163">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="82276-163">To set up, build and run the sample</span></span>  
  
1. <span data-ttu-id="82276-164">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="82276-164">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="82276-165">Gerekirse ana düğümleri ekleyerek `enableLoggingKnownPii` özniteliği `true`ayarlamak için Machine.config'i edin.</span><span class="sxs-lookup"><span data-stu-id="82276-165">Edit Machine.config to set the `enableLoggingKnownPii` attribute to `true`, adding the parent nodes if necessary.</span></span>  
  
3. <span data-ttu-id="82276-166">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="82276-166">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="82276-167">Örneği tek veya bilgisayar lar arası yapılandırmada çalıştırmak [için, Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="82276-167">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
#### <a name="to-clean-up-the-sample"></a><span data-ttu-id="82276-168">Örneği temizlemek için</span><span class="sxs-lookup"><span data-stu-id="82276-168">To clean up the sample</span></span>  
  
1. <span data-ttu-id="82276-169">Özniteliğini ayarlamak `enableLoggingKnownPii` için Machine.config'i `false`edin.</span><span class="sxs-lookup"><span data-stu-id="82276-169">Edit Machine.config to set the `enableLoggingKnownPii` attribute to `false`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82276-170">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82276-170">See also</span></span>

- <span data-ttu-id="82276-171">[AppFabric İzleme Örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="82276-171">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
