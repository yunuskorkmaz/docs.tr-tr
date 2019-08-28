---
title: PII Güvenlik Kilidi
ms.date: 03/30/2017
ms.assetid: c44fb338-9527-4dd0-8607-b8787d15acb4
ms.openlocfilehash: f82d3f19a3bf6fc6a5ac038034880dafc03fcce1
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044793"
---
# <a name="pii-security-lockdown"></a><span data-ttu-id="cd027-102">PII Güvenlik Kilidi</span><span class="sxs-lookup"><span data-stu-id="cd027-102">PII Security Lockdown</span></span>
<span data-ttu-id="cd027-103">Bu örnek, bir Windows Communication Foundation (WCF) hizmetinin güvenlikle ilgili birkaç özelliğinin nasıl kontrol altına alınacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="cd027-103">This sample demonstrates how to control several security-related features of a Windows Communication Foundation (WCF) service by:</span></span>  
  
- <span data-ttu-id="cd027-104">Bir hizmetin yapılandırma dosyasındaki hassas bilgileri şifreleme.</span><span class="sxs-lookup"><span data-stu-id="cd027-104">Encrypting sensitive information in a service's configuration file.</span></span>  
  
- <span data-ttu-id="cd027-105">İç içe geçmiş hizmet alt dizinleri ayarları geçersiz kılamaması için yapılandırma dosyasındaki öğeleri kilitleme.</span><span class="sxs-lookup"><span data-stu-id="cd027-105">Locking elements in the configuration file so that nested service subdirectories cannot override settings.</span></span>  
  
- <span data-ttu-id="cd027-106">Kişisel bilgilerin (PII) izleme ve ileti günlüklerinde günlüğe kaydedilmesini denetleme.</span><span class="sxs-lookup"><span data-stu-id="cd027-106">Controlling the logging of Personally Identifiable Information (PII) in trace and message logs.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="cd027-107">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="cd027-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="cd027-108">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="cd027-108">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="cd027-109">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="cd027-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cd027-110">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="cd027-110">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\SecurityLockdown`  
  
## <a name="discussion"></a><span data-ttu-id="cd027-111">Tartışma</span><span class="sxs-lookup"><span data-stu-id="cd027-111">Discussion</span></span>  
 <span data-ttu-id="cd027-112">Bu özelliklerin her biri, bir hizmetin güvenliğinin yönlerini denetlemek için ayrı olarak veya birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cd027-112">Each of these features can be used separately or together to control aspects of a service's security.</span></span> <span data-ttu-id="cd027-113">Bu bir WCF hizmetini güvenli hale getirmek için kesin bir kılavuz değildir.</span><span class="sxs-lookup"><span data-stu-id="cd027-113">This is not a definitive guide to securing a WCF service.</span></span>  
  
 <span data-ttu-id="cd027-114">.NET Framework yapılandırma dosyaları, veritabanlarına bağlanmak için bağlantı dizeleri gibi gizli bilgiler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="cd027-114">The .NET Framework configuration files can contain sensitive information such as connection strings to connect to databases.</span></span> <span data-ttu-id="cd027-115">Paylaşılan, Web 'de barındırılan senaryolarda, yapılandırma dosyası içinde yer alan verilerin rastgele görüntülemeye dayanıklı olması için bu bilgileri bir hizmetin yapılandırma dosyasında şifrelemek istenebilir.</span><span class="sxs-lookup"><span data-stu-id="cd027-115">In shared, Web-hosted scenarios it may be desirable to encrypt this information in the configuration file for a service so that the data contained within the configuration file is resistant to casual viewing.</span></span> <span data-ttu-id="cd027-116">.NET Framework 2,0 ve üzeri, Windows Data Protection uygulama programlama arabirimi (DPAPI) veya RSA şifreleme sağlayıcısını kullanarak yapılandırma dosyasının bölümlerini şifreleyebilme özelliğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="cd027-116">.NET Framework 2.0 and later has the ability to encrypt portions of the configuration file using the Windows Data Protection application programming interface (DPAPI) or the RSA Cryptographic provider.</span></span> <span data-ttu-id="cd027-117">DPAPI veya RSA kullanan Aspnet_regiis. exe bir yapılandırma dosyasının seçim kısımlarını şifreleyebilir.</span><span class="sxs-lookup"><span data-stu-id="cd027-117">The aspnet_regiis.exe using the DPAPI or RSA can encrypt select portions of a configuration file.</span></span>  
  
 <span data-ttu-id="cd027-118">Web 'de barındırılan senaryolarda, diğer hizmetlerin alt dizinlerinde Hizmetleri olması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="cd027-118">In Web-hosted scenarios it is possible to have services in subdirectories of other services.</span></span> <span data-ttu-id="cd027-119">Yapılandırma değerlerini belirlemek için varsayılan anlam, iç dizindeki yapılandırma değerlerini geçersiz kılmak üzere iç içe dizinler içindeki yapılandırma dosyalarının izin verir.</span><span class="sxs-lookup"><span data-stu-id="cd027-119">The default semantic for determining configuration values allows configuration files in the nested directories to override the configuration values in the parent directory.</span></span> <span data-ttu-id="cd027-120">Bazı durumlarda bu, çeşitli nedenlerle istenmeyen bir durum olabilir.</span><span class="sxs-lookup"><span data-stu-id="cd027-120">In certain situations this may be undesirable for a variety of reasons.</span></span> <span data-ttu-id="cd027-121">WCF hizmeti yapılandırması, iç içe geçmiş bir hizmet geçersiz kılınan yapılandırma değerleri kullanılarak çalıştırıldığında, iç içe yapılandırmanın özel durumlar oluşturması için yapılandırma değerlerinin kilitlenmesini destekler.</span><span class="sxs-lookup"><span data-stu-id="cd027-121">WCF service configuration supports the locking of configuration values so that nested configuration generates exceptions when a nested service is run using overridden configuration values.</span></span>  
  
 <span data-ttu-id="cd027-122">Bu örnek, Kullanıcı adı ve parola gibi, izleme ve ileti günlüklerinde bilinen kişisel bilgilerin (PII) günlüğe kaydedilmesini nasıl denetleyeceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="cd027-122">This sample demonstrates how to control the logging of known Personally Identifiable Information (PII) in trace and message logs, such as username and password.</span></span> <span data-ttu-id="cd027-123">Varsayılan olarak, bilinen PII günlüğe kaydetme devre dışıdır, ancak bazı durumlarda PII günlüğü, bir uygulamada hata ayıklaması yapmak için önemli olabilir.</span><span class="sxs-lookup"><span data-stu-id="cd027-123">By default, logging of known PII is disabled however in certain situations logging of PII can be important in debugging an application.</span></span> <span data-ttu-id="cd027-124">Bu örnek, [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)' i temel alır.</span><span class="sxs-lookup"><span data-stu-id="cd027-124">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="cd027-125">Ayrıca, bu örnek izleme ve ileti günlüğe kaydetme kullanır.</span><span class="sxs-lookup"><span data-stu-id="cd027-125">In addition, this sample uses tracing and message logging.</span></span> <span data-ttu-id="cd027-126">Daha fazla bilgi için [izleme ve mesaj günlüğü](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) örneğine bakın.</span><span class="sxs-lookup"><span data-stu-id="cd027-126">For more information, see the [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) sample.</span></span>  
  
## <a name="encrypting-configuration-file-elements"></a><span data-ttu-id="cd027-127">Yapılandırma dosyası öğelerini şifreleme</span><span class="sxs-lookup"><span data-stu-id="cd027-127">Encrypting Configuration File Elements</span></span>  
 <span data-ttu-id="cd027-128">Paylaşılan bir Web barındırma ortamındaki güvenlik amaçları için, gizli bilgiler içerebilen veritabanı bağlantı dizeleri gibi belirli yapılandırma öğelerini şifrelemek istenebilir.</span><span class="sxs-lookup"><span data-stu-id="cd027-128">For security purposes in a shared Web-hosting environment, it may be desirable to encrypt certain configuration elements, such as database connection strings that may contain sensitive information.</span></span> <span data-ttu-id="cd027-129">Bir yapılandırma öğesi, .NET Framework klasöründe bulunan Aspnet_regiis. exe aracı kullanılarak şifrelenmiş olabilir, örneğin,%WINDIR%\Microsoft.NET\Framework\v4.0.20728.</span><span class="sxs-lookup"><span data-stu-id="cd027-129">A configuration element may be encrypted using the aspnet_regiis.exe tool found in the .NET Framework folder For example, %WINDIR%\Microsoft.NET\Framework\v4.0.20728.</span></span>  
  
#### <a name="to-encrypt-the-values-in-the-appsettings-section-in-webconfig-for-the-sample"></a><span data-ttu-id="cd027-130">Örnek için Web. config içindeki appSettings bölümündeki değerleri şifrelemek için</span><span class="sxs-lookup"><span data-stu-id="cd027-130">To encrypt the values in the appSettings section in Web.config for the sample</span></span>  
  
1. <span data-ttu-id="cd027-131">Başlat-> Çalıştır komutunu kullanarak bir komut istemi açın...</span><span class="sxs-lookup"><span data-stu-id="cd027-131">Open a command prompt by using Start->Run….</span></span> <span data-ttu-id="cd027-132">Yazın ve Tamam ' a tıklayın. `cmd`</span><span class="sxs-lookup"><span data-stu-id="cd027-132">Type in `cmd` and click **OK**.</span></span>  
  
2. <span data-ttu-id="cd027-133">Şu komutu yayımlayarak geçerli .NET Framework dizinine gidin: `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`.</span><span class="sxs-lookup"><span data-stu-id="cd027-133">Navigate to the current .NET Framework directory by issuing the following command: `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`.</span></span>  
  
3. <span data-ttu-id="cd027-134">Aşağıdaki komutu yayımlayarak Web. config klasöründeki appSettings yapılandırma ayarlarını şifreleyin: `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`.</span><span class="sxs-lookup"><span data-stu-id="cd027-134">Encrypt the appSettings configuration settings in the Web.config folder by issuing the following command: `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`.</span></span>  
  
 <span data-ttu-id="cd027-135">Yapılandırma dosyalarının şifreleniyor hakkında daha fazla bilgi, ASP.NET yapılandırması 'nda ([güvenli ASP.NET uygulamaları oluşturma) bir dizi DPAPI ile okunarak bulunabilir: Kimlik doğrulaması, yetkilendirme ve güvenli iletişim](https://go.microsoft.com/fwlink/?LinkId=95137)) ve ASP.NET yapılandırmasında nasıl yapılır RSA ([nasıl yapılır: ASP.NET 2,0 içindeki yapılandırma bölümlerini RSA](https://go.microsoft.com/fwlink/?LinkId=95138)kullanarak şifreleyin.</span><span class="sxs-lookup"><span data-stu-id="cd027-135">More information about encrypting sections of configuration files can be found by reading a how-to on DPAPI in ASP.NET configuration ([Building Secure ASP.NET Applications: Authentication, Authorization, and Secure Communication](https://go.microsoft.com/fwlink/?LinkId=95137)) and a how-to on RSA in ASP.NET configuration ([How To: Encrypt Configuration Sections in ASP.NET 2.0 Using RSA](https://go.microsoft.com/fwlink/?LinkId=95138)).</span></span>  
  
## <a name="locking-configuration-file-elements"></a><span data-ttu-id="cd027-136">Yapılandırma dosyası öğelerini kilitleme</span><span class="sxs-lookup"><span data-stu-id="cd027-136">Locking configuration file elements</span></span>  
 <span data-ttu-id="cd027-137">Web 'de barındırılan senaryolarda, hizmetlerin alt dizinlerinde Hizmetleri olması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="cd027-137">In Web-hosted scenarios, it is possible to have services in subdirectories of services.</span></span> <span data-ttu-id="cd027-138">Bu durumlarda, alt dizindeki hizmetin yapılandırma değerleri, Machine. config dosyasındaki değerleri inceleyerek ve üst dizinlerdeki herhangi bir Web. config dosyası ile çok büyük bir şekilde birleştirme işlemi, dizin ağacını aşağı doğru ve son olarak birleştirme sırasında hesaplanır. Hizmeti içeren dizinde Web. config dosyası.</span><span class="sxs-lookup"><span data-stu-id="cd027-138">In these situations, configuration values for the service in the subdirectory are calculated by examining values in Machine.config and successively merging with any Web.config files in parent directories moving down the directory tree and finally merging the Web.config file in the directory that contains the service.</span></span> <span data-ttu-id="cd027-139">Çoğu yapılandırma öğesinin varsayılan davranışı, alt dizinlerindeki yapılandırma dosyalarının üst dizinlerde ayarlanan değerleri geçersiz kılmasına izin verdir.</span><span class="sxs-lookup"><span data-stu-id="cd027-139">The default behavior for most configuration elements is to allow configuration files in subdirectories to override the values set in parent directories.</span></span> <span data-ttu-id="cd027-140">Belirli durumlarda, alt dizinlerdeki yapılandırma dosyalarının üst dizin yapılandırmasında ayarlanan değerleri geçersiz kılmasını engellemek istenebilir.</span><span class="sxs-lookup"><span data-stu-id="cd027-140">In certain situations it may be desirable to prevent configuration files in subdirectories from overriding values set in parent directory configuration.</span></span>  
  
 <span data-ttu-id="cd027-141">.NET Framework, kilitli yapılandırma öğelerini geçersiz kılan yapılandırmaların çalışma zamanı özel durumları oluşturması için yapılandırma dosyası öğelerini kilitlemek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="cd027-141">The .NET Framework provides a way to lock configuration file elements so that configurations that override locked configuration elements throw run-time exceptions.</span></span>  
  
 <span data-ttu-id="cd027-142">Yapılandırma öğesi, yapılandırma dosyasındaki bir düğümün özniteliği belirtilerek `lockItem` , örneğin, iç içe yapılandırma dosyalarında Hesaplayıcı Hizmetleri olacak şekilde yapılandırma dosyasındaki bir düğüm için özniteliği belirtilerek kilitlenebilir. davranış değiştirilemiyor, aşağıdaki yapılandırma kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cd027-142">A configuration element can be locked by specifying the `lockItem` attribute for a node in the configuration file, for example, to lock the CalculatorServiceBehavior node in the configuration file so that calculator services in nested configuration files cannot change the behavior, the following configuration can be used.</span></span>  
  
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
  
 <span data-ttu-id="cd027-143">Yapılandırma öğelerinin kilitlenmesi daha belirgin olabilir.</span><span class="sxs-lookup"><span data-stu-id="cd027-143">Locking of configuration elements can be more specific.</span></span> <span data-ttu-id="cd027-144">Öğe listesi, `lockElements` alt öğeleri koleksiyonundaki öğelerin bir kümesini kilitlemek için öğesine değer olarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="cd027-144">A list of elements can be specified as the value to the `lockElements` to lock a set of elements within a collection of sub-elements.</span></span> <span data-ttu-id="cd027-145">Bir öğe içindeki bir öznitelik kümesini kilitlemek için, bir öznitelik listesi `lockAttributes` , öğesine değer olarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="cd027-145">A list of attributes can be specified as the value to the `lockAttributes` to lock a set of attributes within an element.</span></span> <span data-ttu-id="cd027-146">Bir düğüm üzerindeki veya `lockAllElementsExcept` `lockAllAttributesExcept` özniteliklerini belirterek, belirtilen bir liste hariç tüm öğe veya öznitelik koleksiyonu kilitlenebilir.</span><span class="sxs-lookup"><span data-stu-id="cd027-146">An entire collection of elements or attributes can be locked except for a specified list by specifying the `lockAllElementsExcept` or `lockAllAttributesExcept` attributes on a node.</span></span>  
  
## <a name="pii-logging-configuration"></a><span data-ttu-id="cd027-147">PII günlük kaydı yapılandırması</span><span class="sxs-lookup"><span data-stu-id="cd027-147">PII Logging Configuration</span></span>  
 <span data-ttu-id="cd027-148">PII günlüğü iki anahtarla denetlenir: Machine. config dosyasında bir bilgisayar yöneticisinin PII günlüğe kaydedilmesine izin verilmesini veya reddetmesini sağlayan bir uygulama ayarı ve uygulama yöneticisinin her biri için PII günlüğe kaydedilmesini değiştirmesine izin veren bir uygulama ayarı bulunur. bir Web. config veya App. config dosyasında kaynak.</span><span class="sxs-lookup"><span data-stu-id="cd027-148">Logging of PII is controlled by two switches: a computer-wide setting found in Machine.config that allows a computer administrator to permit or deny logging of PII and an application setting that allows an application administrator to toggle logging of PII for each source in a Web.config or App.config file.</span></span>  
  
 <span data-ttu-id="cd027-149">Bilgisayar genelindeki ayar, Machine. `enableLoggingKnownPii` config 'deki `machineSettings` öğesinde `true` veya `false`olarak ayarlanarak denetlenir. Örneğin, aşağıdakiler uygulamaların PII günlük kaydını açmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="cd027-149">The computer-wide setting is controlled by setting `enableLoggingKnownPii` to `true` or `false`, in the `machineSettings` element in Machine.config. For example, the following allows applications to turn on logging of PII.</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <machineSettings enableLoggingKnownPii="true" />  
    </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
> <span data-ttu-id="cd027-150">Machine. config dosyası varsayılan bir konuma sahiptir:%WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.</span><span class="sxs-lookup"><span data-stu-id="cd027-150">The Machine.config file has a default location: %WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.</span></span>  
  
 <span data-ttu-id="cd027-151">`enableLoggingKnownPii` Özniteliği Machine. config dosyasında yoksa, PII günlüğüne izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="cd027-151">If the `enableLoggingKnownPii` attribute is not present in Machine.config, logging of PII is not allowed.</span></span>  
  
 <span data-ttu-id="cd027-152">Bir uygulama için PII günlük kaydının etkinleştirilmesi, kaynak `logKnownPii` `true` öğenin özniteliği veya `false` Web. config veya App. config dosyasına ayarlanarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="cd027-152">Enabling logging of PII for an application is done by setting the `logKnownPii` attribute of the source element to `true` or `false` in the Web.config or App.config file.</span></span> <span data-ttu-id="cd027-153">Örneğin, aşağıdaki ileti günlüğe kaydetme ve izleme günlüğü için PII günlüğe kaydedilmesini mümkün bir şekilde sunar.</span><span class="sxs-lookup"><span data-stu-id="cd027-153">For example, the following enables logging of PII for both message logging and trace logging.</span></span>  
  
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
  
 <span data-ttu-id="cd027-154">`logKnownPii` Öznitelik belirtilmemişse PII günlüğe kaydedilmez.</span><span class="sxs-lookup"><span data-stu-id="cd027-154">If the `logKnownPii` attribute is not specified, then PII is not logged.</span></span>  
  
 <span data-ttu-id="cd027-155">PII `enableLoggingKnownPii` `true`, her ikisi de olarak ayarlanmışsa günlüğe kaydedilir ve `logKnownPii` olarak `true`ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="cd027-155">PII is only logged if both `enableLoggingKnownPii` is set to `true`, and `logKnownPii` is set to `true`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cd027-156">System. Diagnostics, yapılandırma dosyasında listelenenden ilki hariç tüm kaynaklardaki tüm öznitelikleri yoksayar.</span><span class="sxs-lookup"><span data-stu-id="cd027-156">System.Diagnostics ignores all attributes on all sources except the first one listed in the configuration file.</span></span> <span data-ttu-id="cd027-157">Yapılandırma dosyasındaki ikinci kaynağa özniteliğinieklemeketkisizdir.`logKnownPii`</span><span class="sxs-lookup"><span data-stu-id="cd027-157">Adding the `logKnownPii` attribute to the second source in the configuration file has no effect.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="cd027-158">Bu örneği çalıştırmak için Machine. config dosyasının el ile değiştirilmesi gerekir. Machine. config dosyasının değiştirilmesi hatalı değerler veya sözdizimi olarak değiştirilirken gerçekleştirilmelidir. tüm .NET Framework uygulamalarının çalışmasını engelleyebilir.</span><span class="sxs-lookup"><span data-stu-id="cd027-158">To run this sample involves manual modification of Machine.config. Care should be taken when modifying Machine.config as incorrect values or syntax may prevent all .NET Framework applications from running.</span></span>  
  
 <span data-ttu-id="cd027-159">Ayrıca, DPAPI ve RSA kullanılarak yapılandırma dosyası öğelerini şifrelemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="cd027-159">It is also possible to encrypt configuration file elements using DPAPI and RSA.</span></span> <span data-ttu-id="cd027-160">Daha fazla bilgi için aşağıdaki bağlantılara bakın:</span><span class="sxs-lookup"><span data-stu-id="cd027-160">For more information, see the following links:</span></span>  
  
- [<span data-ttu-id="cd027-161">Güvenli ASP.NET uygulamaları oluşturma: Kimlik doğrulama, yetkilendirme ve güvenli Iletişim</span><span class="sxs-lookup"><span data-stu-id="cd027-161">Building Secure ASP.NET Applications: Authentication, Authorization, and Secure Communication</span></span>](https://go.microsoft.com/fwlink/?LinkId=95137)  
  
- [<span data-ttu-id="cd027-162">Nasıl yapılır: ASP.NET 2,0 içindeki yapılandırma bölümlerini RSA kullanarak şifreleme</span><span class="sxs-lookup"><span data-stu-id="cd027-162">How To: Encrypt Configuration Sections in ASP.NET 2.0 Using RSA</span></span>](https://go.microsoft.com/fwlink/?LinkId=95138)  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="cd027-163">Bunu ayarlamak için örneği oluşturun ve çalıştırın</span><span class="sxs-lookup"><span data-stu-id="cd027-163">To set up, build and run the sample</span></span>  
  
1. <span data-ttu-id="cd027-164">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="cd027-164">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="cd027-165">`enableLoggingKnownPii`Özniteliğiniayarlamak için Machine. config dosyasını düzenleyin ,gerekirse`true`üst düğümleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cd027-165">Edit Machine.config to set the `enableLoggingKnownPii` attribute to `true`, adding the parent nodes if necessary.</span></span>  
  
3. <span data-ttu-id="cd027-166">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="cd027-166">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="cd027-167">Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="cd027-167">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
#### <a name="to-clean-up-the-sample"></a><span data-ttu-id="cd027-168">Örneği temizlemek için</span><span class="sxs-lookup"><span data-stu-id="cd027-168">To clean up the sample</span></span>  
  
1. <span data-ttu-id="cd027-169">`enableLoggingKnownPii` Özniteliğini olarak`false`ayarlamak için Machine. config dosyasını düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="cd027-169">Edit Machine.config to set the `enableLoggingKnownPii` attribute to `false`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd027-170">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd027-170">See also</span></span>

- [<span data-ttu-id="cd027-171">AppFabric Izleme örnekleri</span><span class="sxs-lookup"><span data-stu-id="cd027-171">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
