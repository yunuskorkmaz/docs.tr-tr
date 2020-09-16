---
title: PII Güvenlik Kilidi
ms.date: 03/30/2017
ms.assetid: c44fb338-9527-4dd0-8607-b8787d15acb4
ms.openlocfilehash: 62e1495927cad669771c560603919e8f6b94d863
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559382"
---
# <a name="pii-security-lockdown"></a><span data-ttu-id="6dc69-102">PII Güvenlik Kilidi</span><span class="sxs-lookup"><span data-stu-id="6dc69-102">PII Security Lockdown</span></span>
<span data-ttu-id="6dc69-103">Bu örnek, bir Windows Communication Foundation (WCF) hizmetinin güvenlikle ilgili birkaç özelliğinin nasıl kontrol altına alınacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="6dc69-103">This sample demonstrates how to control several security-related features of a Windows Communication Foundation (WCF) service by:</span></span>  
  
- <span data-ttu-id="6dc69-104">Bir hizmetin yapılandırma dosyasındaki hassas bilgileri şifreleme.</span><span class="sxs-lookup"><span data-stu-id="6dc69-104">Encrypting sensitive information in a service's configuration file.</span></span>  
  
- <span data-ttu-id="6dc69-105">İç içe geçmiş hizmet alt dizinleri ayarları geçersiz kılamaması için yapılandırma dosyasındaki öğeleri kilitleme.</span><span class="sxs-lookup"><span data-stu-id="6dc69-105">Locking elements in the configuration file so that nested service subdirectories cannot override settings.</span></span>  
  
- <span data-ttu-id="6dc69-106">Kişisel bilgilerin (PII) izleme ve ileti günlüklerinde günlüğe kaydedilmesini denetleme.</span><span class="sxs-lookup"><span data-stu-id="6dc69-106">Controlling the logging of Personally Identifiable Information (PII) in trace and message logs.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6dc69-107">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="6dc69-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="6dc69-108">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="6dc69-108">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="6dc69-109">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="6dc69-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6dc69-110">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="6dc69-110">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\SecurityLockdown`  
  
## <a name="discussion"></a><span data-ttu-id="6dc69-111">Tartışma</span><span class="sxs-lookup"><span data-stu-id="6dc69-111">Discussion</span></span>  
 <span data-ttu-id="6dc69-112">Bu özelliklerin her biri, bir hizmetin güvenliğinin yönlerini denetlemek için ayrı olarak veya birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6dc69-112">Each of these features can be used separately or together to control aspects of a service's security.</span></span> <span data-ttu-id="6dc69-113">Bu bir WCF hizmetini güvenli hale getirmek için kesin bir kılavuz değildir.</span><span class="sxs-lookup"><span data-stu-id="6dc69-113">This is not a definitive guide to securing a WCF service.</span></span>  
  
 <span data-ttu-id="6dc69-114">.NET Framework yapılandırma dosyaları, veritabanlarına bağlanmak için bağlantı dizeleri gibi gizli bilgiler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="6dc69-114">The .NET Framework configuration files can contain sensitive information such as connection strings to connect to databases.</span></span> <span data-ttu-id="6dc69-115">Paylaşılan, Web 'de barındırılan senaryolarda, yapılandırma dosyası içinde yer alan verilerin rastgele görüntülemeye dayanıklı olması için bu bilgileri bir hizmetin yapılandırma dosyasında şifrelemek istenebilir.</span><span class="sxs-lookup"><span data-stu-id="6dc69-115">In shared, Web-hosted scenarios it may be desirable to encrypt this information in the configuration file for a service so that the data contained within the configuration file is resistant to casual viewing.</span></span> <span data-ttu-id="6dc69-116">.NET Framework 2,0 ve üzeri, Windows Data Protection uygulama programlama arabirimi (DPAPI) veya RSA şifreleme sağlayıcısını kullanarak yapılandırma dosyasının bölümlerini şifreleyebilme özelliğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="6dc69-116">.NET Framework 2.0 and later has the ability to encrypt portions of the configuration file using the Windows Data Protection application programming interface (DPAPI) or the RSA Cryptographic provider.</span></span> <span data-ttu-id="6dc69-117">DPAPI veya RSA kullanan aspnet_regiis.exe, bir yapılandırma dosyasının seçim bölümlerini şifreleyebilir.</span><span class="sxs-lookup"><span data-stu-id="6dc69-117">The aspnet_regiis.exe using the DPAPI or RSA can encrypt select portions of a configuration file.</span></span>  
  
 <span data-ttu-id="6dc69-118">Web 'de barındırılan senaryolarda, diğer hizmetlerin alt dizinlerinde Hizmetleri olması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="6dc69-118">In Web-hosted scenarios it is possible to have services in subdirectories of other services.</span></span> <span data-ttu-id="6dc69-119">Yapılandırma değerlerini belirlemek için varsayılan anlam, iç dizindeki yapılandırma değerlerini geçersiz kılmak üzere iç içe dizinler içindeki yapılandırma dosyalarının izin verir.</span><span class="sxs-lookup"><span data-stu-id="6dc69-119">The default semantic for determining configuration values allows configuration files in the nested directories to override the configuration values in the parent directory.</span></span> <span data-ttu-id="6dc69-120">Bazı durumlarda bu, çeşitli nedenlerle istenmeyen bir durum olabilir.</span><span class="sxs-lookup"><span data-stu-id="6dc69-120">In certain situations this may be undesirable for a variety of reasons.</span></span> <span data-ttu-id="6dc69-121">WCF hizmeti yapılandırması, iç içe geçmiş bir hizmet geçersiz kılınan yapılandırma değerleri kullanılarak çalıştırıldığında, iç içe yapılandırmanın özel durumlar oluşturması için yapılandırma değerlerinin kilitlenmesini destekler.</span><span class="sxs-lookup"><span data-stu-id="6dc69-121">WCF service configuration supports the locking of configuration values so that nested configuration generates exceptions when a nested service is run using overridden configuration values.</span></span>  
  
 <span data-ttu-id="6dc69-122">Bu örnek, Kullanıcı adı ve parola gibi, izleme ve ileti günlüklerinde bilinen kişisel bilgilerin (PII) günlüğe kaydedilmesini nasıl denetleyeceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="6dc69-122">This sample demonstrates how to control the logging of known Personally Identifiable Information (PII) in trace and message logs, such as username and password.</span></span> <span data-ttu-id="6dc69-123">Varsayılan olarak, bilinen PII günlüğe kaydetme devre dışıdır, ancak bazı durumlarda PII günlüğü, bir uygulamada hata ayıklaması yapmak için önemli olabilir.</span><span class="sxs-lookup"><span data-stu-id="6dc69-123">By default, logging of known PII is disabled however in certain situations logging of PII can be important in debugging an application.</span></span> <span data-ttu-id="6dc69-124">Bu örnek, [Başlarken](getting-started-sample.md)' i temel alır.</span><span class="sxs-lookup"><span data-stu-id="6dc69-124">This sample is based on the [Getting Started](getting-started-sample.md).</span></span> <span data-ttu-id="6dc69-125">Ayrıca, bu örnek izleme ve ileti günlüğe kaydetme kullanır.</span><span class="sxs-lookup"><span data-stu-id="6dc69-125">In addition, this sample uses tracing and message logging.</span></span> <span data-ttu-id="6dc69-126">Daha fazla bilgi için [izleme ve mesaj günlüğü](tracing-and-message-logging.md) örneğine bakın.</span><span class="sxs-lookup"><span data-stu-id="6dc69-126">For more information, see the [Tracing and Message Logging](tracing-and-message-logging.md) sample.</span></span>  
  
## <a name="encrypting-configuration-file-elements"></a><span data-ttu-id="6dc69-127">Yapılandırma dosyası öğelerini şifreleme</span><span class="sxs-lookup"><span data-stu-id="6dc69-127">Encrypting Configuration File Elements</span></span>  
 <span data-ttu-id="6dc69-128">Paylaşılan bir Web barındırma ortamındaki güvenlik amaçları için, gizli bilgiler içerebilen veritabanı bağlantı dizeleri gibi belirli yapılandırma öğelerini şifrelemek istenebilir.</span><span class="sxs-lookup"><span data-stu-id="6dc69-128">For security purposes in a shared Web-hosting environment, it may be desirable to encrypt certain configuration elements, such as database connection strings that may contain sensitive information.</span></span> <span data-ttu-id="6dc69-129">Bir yapılandırma öğesi, .NET Framework klasöründe bulunan aspnet_regiis.exe Aracı kullanılarak şifrelenmiş olabilir, örneğin,%WINDIR%\Microsoft.NET\Framework\v4.0.20728.</span><span class="sxs-lookup"><span data-stu-id="6dc69-129">A configuration element may be encrypted using the aspnet_regiis.exe tool found in the .NET Framework folder For example, %WINDIR%\Microsoft.NET\Framework\v4.0.20728.</span></span>  
  
#### <a name="to-encrypt-the-values-in-the-appsettings-section-in-webconfig-for-the-sample"></a><span data-ttu-id="6dc69-130">Örnek için Web.config appSettings bölümündeki değerleri şifrelemek için</span><span class="sxs-lookup"><span data-stu-id="6dc69-130">To encrypt the values in the appSettings section in Web.config for the sample</span></span>  
  
1. <span data-ttu-id="6dc69-131">Başlat->Çalıştır komutunu kullanarak bir komut istemi açın...</span><span class="sxs-lookup"><span data-stu-id="6dc69-131">Open a command prompt by using Start->Run….</span></span> <span data-ttu-id="6dc69-132">Yazın `cmd` ve **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="6dc69-132">Type in `cmd` and click **OK**.</span></span>  
  
2. <span data-ttu-id="6dc69-133">Şu komutu yayımlayarak geçerli .NET Framework dizinine gidin: `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728` .</span><span class="sxs-lookup"><span data-stu-id="6dc69-133">Navigate to the current .NET Framework directory by issuing the following command: `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`.</span></span>  
  
3. <span data-ttu-id="6dc69-134">Aşağıdaki komutu yayımlayarak Web.config klasöründeki appSettings yapılandırma ayarlarını şifreleyin: `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"` .</span><span class="sxs-lookup"><span data-stu-id="6dc69-134">Encrypt the appSettings configuration settings in the Web.config folder by issuing the following command: `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`.</span></span>  
  
 <span data-ttu-id="6dc69-135">Yapılandırma dosyalarını şifreleme hakkında daha fazla bilgi, ASP.NET yapılandırmasındaki ([güvenli ASP.NET uygulamalar oluşturma: kimlik doğrulaması, yetkilendirme ve güvenli iletişim](/previous-versions/msp-n-p/ff649248(v=pandp.10))) ve ASP.NET yapılandırmasında nasıl yapılır RSA ([nasıl yapılır: rsa kullanılarak ASP.NET 2,0 ' de yapılandırma bölümlerini şifreleme](/previous-versions/msp-n-p/ff650304(v=pandp.10))) hakkında daha fazla bilgi bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="6dc69-135">More information about encrypting sections of configuration files can be found by reading a how-to on DPAPI in ASP.NET configuration ([Building Secure ASP.NET Applications: Authentication, Authorization, and Secure Communication](/previous-versions/msp-n-p/ff649248(v=pandp.10))) and a how-to on RSA in ASP.NET configuration ([How To: Encrypt Configuration Sections in ASP.NET 2.0 Using RSA](/previous-versions/msp-n-p/ff650304(v=pandp.10))).</span></span>  
  
## <a name="locking-configuration-file-elements"></a><span data-ttu-id="6dc69-136">Yapılandırma dosyası öğelerini kilitleme</span><span class="sxs-lookup"><span data-stu-id="6dc69-136">Locking configuration file elements</span></span>  
 <span data-ttu-id="6dc69-137">Web 'de barındırılan senaryolarda, hizmetlerin alt dizinlerinde Hizmetleri olması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="6dc69-137">In Web-hosted scenarios, it is possible to have services in subdirectories of services.</span></span> <span data-ttu-id="6dc69-138">Bu durumlarda, alt dizindeki hizmetin yapılandırma değerleri, Machine.config değerler incelenerek ve üst dizinlerdeki tüm Web.config dosyalarla, dizin ağacında aşağı doğru bir şekilde birleştirme ve son olarak Web.config dosyasını hizmeti içeren dizinde Birleştirme yoluyla hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="6dc69-138">In these situations, configuration values for the service in the subdirectory are calculated by examining values in Machine.config and successively merging with any Web.config files in parent directories moving down the directory tree and finally merging the Web.config file in the directory that contains the service.</span></span> <span data-ttu-id="6dc69-139">Çoğu yapılandırma öğesinin varsayılan davranışı, alt dizinlerindeki yapılandırma dosyalarının üst dizinlerde ayarlanan değerleri geçersiz kılmasına izin verdir.</span><span class="sxs-lookup"><span data-stu-id="6dc69-139">The default behavior for most configuration elements is to allow configuration files in subdirectories to override the values set in parent directories.</span></span> <span data-ttu-id="6dc69-140">Belirli durumlarda, alt dizinlerdeki yapılandırma dosyalarının üst dizin yapılandırmasında ayarlanan değerleri geçersiz kılmasını engellemek istenebilir.</span><span class="sxs-lookup"><span data-stu-id="6dc69-140">In certain situations it may be desirable to prevent configuration files in subdirectories from overriding values set in parent directory configuration.</span></span>  
  
 <span data-ttu-id="6dc69-141">.NET Framework, kilitli yapılandırma öğelerini geçersiz kılan yapılandırmaların çalışma zamanı özel durumları oluşturması için yapılandırma dosyası öğelerini kilitlemek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="6dc69-141">The .NET Framework provides a way to lock configuration file elements so that configurations that override locked configuration elements throw run-time exceptions.</span></span>  
  
 <span data-ttu-id="6dc69-142">Yapılandırma öğesi, yapılandırma dosyasındaki `lockItem` bir düğümün özniteliği belirtilerek, örneğin, iç içe yapılandırma dosyalarındaki Hesaplayıcı hizmetlerinin davranışı değiştirememesi için yapılandırma dosyasında bir düğüm için özniteliği belirtilerek kilitlenebilir.</span><span class="sxs-lookup"><span data-stu-id="6dc69-142">A configuration element can be locked by specifying the `lockItem` attribute for a node in the configuration file, for example, to lock the CalculatorServiceBehavior node in the configuration file so that calculator services in nested configuration files cannot change the behavior, the following configuration can be used.</span></span>  
  
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
  
 <span data-ttu-id="6dc69-143">Yapılandırma öğelerinin kilitlenmesi daha belirgin olabilir.</span><span class="sxs-lookup"><span data-stu-id="6dc69-143">Locking of configuration elements can be more specific.</span></span> <span data-ttu-id="6dc69-144">Öğe listesi, `lockElements` alt öğeleri koleksiyonundaki öğelerin bir kümesini kilitlemek için öğesine değer olarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="6dc69-144">A list of elements can be specified as the value to the `lockElements` to lock a set of elements within a collection of sub-elements.</span></span> <span data-ttu-id="6dc69-145">Bir `lockAttributes` öğe içindeki bir öznitelik kümesini kilitlemek için, bir öznitelik listesi, öğesine değer olarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="6dc69-145">A list of attributes can be specified as the value to the `lockAttributes` to lock a set of attributes within an element.</span></span> <span data-ttu-id="6dc69-146">`lockAllElementsExcept`Bir düğüm üzerindeki veya özniteliklerini belirterek, belirtilen bir liste hariç tüm öğe veya öznitelik koleksiyonu kilitlenebilir `lockAllAttributesExcept` .</span><span class="sxs-lookup"><span data-stu-id="6dc69-146">An entire collection of elements or attributes can be locked except for a specified list by specifying the `lockAllElementsExcept` or `lockAllAttributesExcept` attributes on a node.</span></span>  
  
## <a name="pii-logging-configuration"></a><span data-ttu-id="6dc69-147">PII günlük kaydı yapılandırması</span><span class="sxs-lookup"><span data-stu-id="6dc69-147">PII Logging Configuration</span></span>  
 <span data-ttu-id="6dc69-148">PII günlüğü iki anahtarla denetlenir: bilgisayar yöneticisinin PII kaydına izin verip vermemesini ve bir uygulama ayarının, bir Web.config veya App.config dosyasında her bir kaynak için PII günlüğe kaydedilmesini değiştirmesine izin veren bir uygulama ayarı olan Machine.config ' de bilgisayar genelindeki bir ayar bulunur.</span><span class="sxs-lookup"><span data-stu-id="6dc69-148">Logging of PII is controlled by two switches: a computer-wide setting found in Machine.config that allows a computer administrator to permit or deny logging of PII and an application setting that allows an application administrator to toggle logging of PII for each source in a Web.config or App.config file.</span></span>  
  
 <span data-ttu-id="6dc69-149">Bilgisayar genelindeki ayar, `enableLoggingKnownPii` `true` `false` Machine.config öğesinde veya olarak ayarlanarak denetlenir `machineSettings` . Örneğin, aşağıdakiler uygulamaların PII günlük kaydını açmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="6dc69-149">The computer-wide setting is controlled by setting `enableLoggingKnownPii` to `true` or `false`, in the `machineSettings` element in Machine.config. For example, the following allows applications to turn on logging of PII.</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <machineSettings enableLoggingKnownPii="true" />  
    </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
> <span data-ttu-id="6dc69-150">Machine.config dosyası varsayılan bir konuma sahiptir:%WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.</span><span class="sxs-lookup"><span data-stu-id="6dc69-150">The Machine.config file has a default location: %WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.</span></span>  
  
 <span data-ttu-id="6dc69-151">`enableLoggingKnownPii`Öznitelik Machine.config yoksa PII kaydına izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="6dc69-151">If the `enableLoggingKnownPii` attribute is not present in Machine.config, logging of PII is not allowed.</span></span>  
  
 <span data-ttu-id="6dc69-152">Bir uygulama için PII günlük kaydının etkinleştirilmesi, `logKnownPii` kaynak öğenin özniteliği `true` `false` Web.config veya App.config dosyasına ayarlanarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="6dc69-152">Enabling logging of PII for an application is done by setting the `logKnownPii` attribute of the source element to `true` or `false` in the Web.config or App.config file.</span></span> <span data-ttu-id="6dc69-153">Örneğin, aşağıdaki ileti günlüğe kaydetme ve izleme günlüğü için PII günlüğe kaydedilmesini mümkün bir şekilde sunar.</span><span class="sxs-lookup"><span data-stu-id="6dc69-153">For example, the following enables logging of PII for both message logging and trace logging.</span></span>  
  
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
  
 <span data-ttu-id="6dc69-154">`logKnownPii`Öznitelik BELIRTILMEMIŞSE PII günlüğe kaydedilmez.</span><span class="sxs-lookup"><span data-stu-id="6dc69-154">If the `logKnownPii` attribute is not specified, then PII is not logged.</span></span>  
  
 <span data-ttu-id="6dc69-155">PII, her ikisi de olarak `enableLoggingKnownPii` ayarlanmışsa günlüğe kaydedilir `true` ve `logKnownPii` olarak ayarlanır `true` .</span><span class="sxs-lookup"><span data-stu-id="6dc69-155">PII is only logged if both `enableLoggingKnownPii` is set to `true`, and `logKnownPii` is set to `true`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6dc69-156">System. Diagnostics, yapılandırma dosyasında listelenenden ilki hariç tüm kaynaklardaki tüm öznitelikleri yoksayar.</span><span class="sxs-lookup"><span data-stu-id="6dc69-156">System.Diagnostics ignores all attributes on all sources except the first one listed in the configuration file.</span></span> <span data-ttu-id="6dc69-157">`logKnownPii`Yapılandırma dosyasındaki ikinci kaynağa özniteliğini eklemek etkisizdir.</span><span class="sxs-lookup"><span data-stu-id="6dc69-157">Adding the `logKnownPii` attribute to the second source in the configuration file has no effect.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6dc69-158">Bu örneği çalıştırmak için Machine.config el ile değiştirilmesi gerekir. Yanlış değerler veya sözdizimi olarak Machine.config değiştirilirken dikkatli olunmalıdır, tüm .NET Framework uygulamalarının çalışmasını engelleyebilir.</span><span class="sxs-lookup"><span data-stu-id="6dc69-158">To run this sample involves manual modification of Machine.config. Care should be taken when modifying Machine.config as incorrect values or syntax may prevent all .NET Framework applications from running.</span></span>  
  
 <span data-ttu-id="6dc69-159">Ayrıca, DPAPI ve RSA kullanılarak yapılandırma dosyası öğelerini şifrelemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="6dc69-159">It is also possible to encrypt configuration file elements using DPAPI and RSA.</span></span> <span data-ttu-id="6dc69-160">Daha fazla bilgi için aşağıdaki bağlantılara bakın:</span><span class="sxs-lookup"><span data-stu-id="6dc69-160">For more information, see the following links:</span></span>  
  
- <span data-ttu-id="6dc69-161">[Güvenli ASP.NET uygulamaları oluşturma: kimlik doğrulama, yetkilendirme ve güvenli Iletişim](/previous-versions/msp-n-p/ff649248(v=pandp.10))</span><span class="sxs-lookup"><span data-stu-id="6dc69-161">[Building Secure ASP.NET Applications: Authentication, Authorization, and Secure Communication](/previous-versions/msp-n-p/ff649248(v=pandp.10))</span></span>  
  
- <span data-ttu-id="6dc69-162">[Nasıl yapılır: ASP.NET 2,0 ' de yapılandırma bölümlerini RSA kullanarak şifreleme](/previous-versions/msp-n-p/ff650304(v=pandp.10))</span><span class="sxs-lookup"><span data-stu-id="6dc69-162">[How To: Encrypt Configuration Sections in ASP.NET 2.0 Using RSA](/previous-versions/msp-n-p/ff650304(v=pandp.10))</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6dc69-163">Bunu ayarlamak için örneği oluşturun ve çalıştırın</span><span class="sxs-lookup"><span data-stu-id="6dc69-163">To set up, build and run the sample</span></span>  
  
1. <span data-ttu-id="6dc69-164">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="6dc69-164">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="6dc69-165">Özniteliği olarak ayarlamak için Machine.config düzenleyin `enableLoggingKnownPii` `true` , gerekirse üst düğümleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6dc69-165">Edit Machine.config to set the `enableLoggingKnownPii` attribute to `true`, adding the parent nodes if necessary.</span></span>  
  
3. <span data-ttu-id="6dc69-166">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="6dc69-166">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="6dc69-167">Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="6dc69-167">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
#### <a name="to-clean-up-the-sample"></a><span data-ttu-id="6dc69-168">Örneği temizlemek için</span><span class="sxs-lookup"><span data-stu-id="6dc69-168">To clean up the sample</span></span>  
  
1. <span data-ttu-id="6dc69-169">Özniteliğini olarak ayarlamak için Machine.config düzenleyin `enableLoggingKnownPii` `false` .</span><span class="sxs-lookup"><span data-stu-id="6dc69-169">Edit Machine.config to set the `enableLoggingKnownPii` attribute to `false`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dc69-170">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6dc69-170">See also</span></span>

- <span data-ttu-id="6dc69-171">[AppFabric Izleme örnekleri](/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="6dc69-171">[AppFabric Monitoring Samples](/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
