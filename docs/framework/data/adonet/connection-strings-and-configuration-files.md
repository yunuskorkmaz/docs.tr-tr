---
title: Bağlantı Dizeleri ve Yapılandırma Dosyaları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 37df2641-661e-407a-a3fb-7bf9540f01e8
ms.openlocfilehash: 786094bc426066b45fd1a214950ec1e030f0b731
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59088840"
---
# <a name="connection-strings-and-configuration-files"></a>Bağlantı Dizeleri ve Yapılandırma Dosyaları
Bağlantı dizelerini uygulamanızın kodunda ekleme güvenlik açıklarına ve Bakım sorunlarına yol açabilir. Bir uygulamanın kaynak kodunda JIT şifrelenmemiş bir bağlantı dizeleri kullanarak görüntülenebilir [Ildasm.exe (IL ayrıştırıcı)](../../../../docs/framework/tools/ildasm-exe-il-disassembler.md) aracı. Ayrıca, bağlantı dizesini hiç olmadığı kadar değişirse, uygulamanızı derlenmelidir. Bu nedenle, bir uygulama yapılandırma dosyasında bağlantı dizelerini depolamanızı öneririz.  
  
## <a name="working-with-application-configuration-files"></a>Uygulama yapılandırma dosyaları ile çalışma  
 Uygulama yapılandırma dosyaları, belirli bir uygulamaya özgü ayarları içerir. Örneğin, bir ASP.NET uygulaması bir veya daha fazla olabilir **web.config** dosyaları ve bir Windows uygulaması sahip isteğe bağlı **app.config** dosya. Bir yapılandırma dosyasının konumunu ve adını uygulamanın ana bilgisayar bağlı olarak farklılık gösterir ancak yapılandırma dosyaları ortak öğeler paylaşın.  
  
### <a name="the-connectionstrings-section"></a>ConnectionStrings bölümüne  
 Bağlantı dizeleri, anahtar/değer çiftlerinde olarak depolanabilir **connectionStrings** bölümünü **yapılandırma** uygulama yapılandırma dosyası öğesi. Alt öğeleri dahil **ekleme**, **Temizle**, ve **Kaldır**.  
  
 Aşağıdaki yapılandırma dosyası parçası, bir bağlantı dizesi depolamak için söz dizimi ve şema gösterir. **Adı** böylece çalışma zamanında alınabilmesi için bir bağlantı dizesi benzersiz şekilde tanımlamak için sağlayan bir ad özniteliğidir. **ProviderName** machine.config dosyasında kayıtlı olan .NET Framework Veri Sağlayıcısı'nın değişmez adı.  
  
```xml  
<?xml version='1.0' encoding='utf-8'?>  
  <configuration>  
    <connectionStrings>  
      <clear />  
      <add name="Name"   
       providerName="System.Data.ProviderName"   
       connectionString="Valid Connection String;" />  
    </connectionStrings>  
  </configuration>  
```  
  
> [!NOTE]
>  Bir yapılandırma dosyasında bir bağlantı dizesinin parçası kaydedip kullanabileceğiniz <xref:System.Data.Common.DbConnectionStringBuilder> çalışma zamanında tamamlamak için sınıf. Bu, burada öğeler önceden veya yapılandırma dosyasındaki hassas bilgileri kaydetmek istiyor musunuz, bağlantı dizesinin bilmiyorsanız senaryolarda kullanışlıdır. Daha fazla bilgi için [bağlantı dizesi oluşturucular](../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
### <a name="using-external-configuration-files"></a>Dış yapılandırma dosyalarını kullanma  
 Dış yapılandırma dosyalarını içeren tek bir bölümden oluşan bir yapılandırma dosyası bir parçasını ayrı dosyalarıdır. Dış yapılandırma dosyası, ardından ana yapılandırma dosyası tarafından başvuruluyor. Depolama **connectionStrings** bölümü fiziksel olarak ayrı bir dosyada nerede bağlantı dizelerini düzenlenmesi uygulama dağıtıldıktan sonra durumlarda yararlıdır. Örneğin, standart ASP.NET davranışını yapılandırma dosyaları değiştirildiğinde, durum bilgilerini kaybolmasını sonuçlanır bir uygulama etki alanı yeniden başlatmaktır. Ancak, bir dış yapılandırma dosyasını değiştirerek uygulamanın yeniden başlatılmasını neden olmaz. Dış yapılandırma dosyalarını, ASP.NET ile sınırlı değildir; Windows uygulamaları tarafından da kullanılabilir. Ayrıca, dosya erişim güvenliği ve izinleri dış yapılandırma dosyalarına erişimi kısıtlamak için kullanılabilir. Çalışma zamanında dış yapılandırma dosyaları ile çalışma saydamdır ve özel kodlama gerektirir.  
  
 Bağlantı dizeleri bir dış yapılandırma dosyasında saklamak için yalnızca içeren ayrı bir dosya oluşturun. **connectionStrings** bölümü. Herhangi bir ek öğeler, bölüm veya özniteliklerini içermez. Bu örnekte bir dış yapılandırma dosyası için sözdizimi gösterilmektedir.  
  
```xml  
<connectionStrings>  
  <add name="Name"   
   providerName="System.Data.ProviderName"   
   connectionString="Valid Connection String;" />  
</connectionStrings>  
```  
  
 Ana uygulama yapılandırma dosyasında kullandığınız **configSource** tam adını ve dış dosya konumunu belirtmek için özniteliği. Bu örnek adlı bir dış yapılandırma dosyasına başvuruyor `connections.config`.  
  
```xml  
<?xml version='1.0' encoding='utf-8'?>  
<configuration>  
    <connectionStrings configSource="connections.config"/>  
</configuration>  
```  
  
## <a name="retrieving-connection-strings-at-run-time"></a>Bağlantı dizeleri çalışma zamanında alınıyor  
 Yeni sınıflar, .NET Framework 2.0 sunulan <xref:System.Configuration> yapılandırma dosyalarından alma bağlantı dizeleri çalışma zamanında basitleştirmek için ad alanı. Program aracılığıyla bir bağlantı dizesi adı veya sağlayıcı adı elde edebilirsiniz.  
  
> [!NOTE]
>  **Machine.config** dosya da içeren bir **connectionStrings** bölümünde, Visual Studio tarafından kullanılan bağlantı dizeleri içerir. Bağlantı dizeleri sağlayıcı adı tarafından alınırken **app.config** bağlantı dizeleri bir Windows uygulaması **machine.config** yüklenen ilk ve girişleri alma**app.config**. Ekleme **Temizle** hemen sonra **connectionStrings** öğeyi kaldırır devralınan tüm başvurularını bellekte veri yapısından yerelbağlantıdizelerinitanımlananböylece**app.config** dosya olarak kabul edilir.  
  
### <a name="working-with-the-configuration-classes"></a>Yapılandırma sınıfları ile çalışma  
 .NET Framework 2.0 ile başlayarak <xref:System.Configuration.ConfigurationManager> yapılandırma dosyaları yerel bilgisayarda kullanım dışı değiştirme ile çalışırken kullanılan <xref:System.Configuration.ConfigurationSettings>. <xref:System.Web.Configuration.WebConfigurationManager> ASP.NET yapılandırma dosyaları ile çalışmak için kullanılır. Yapılandırma dosyalarını bir Web sunucusu ile çalışacak şekilde tasarlanmıştır ve gibi yapılandırma dosyanın bölümleri programlı erişim sağlayan **system.web**.  
  
> [!NOTE]
>  Yapılandırma dosyalarını çalışma zamanında erişme izinleri verme çağırana gerektirir; gerekli izinler, uygulama ve yapılandırma dosyası konumu türüne bağlıdır. Daha fazla bilgi için [yapılandırma sınıflarını kullanarak](https://docs.microsoft.com/previous-versions/aspnet/ms228063(v=vs.100)) ve <xref:System.Web.Configuration.WebConfigurationManager> ASP.NET uygulamaları için ve <xref:System.Configuration.ConfigurationManager> Windows uygulamaları için.  
  
 Kullanabileceğiniz <xref:System.Configuration.ConnectionStringSettingsCollection> uygulama yapılandırma dosyalarından bağlantı dizelerini almak için. Bir koleksiyonunu içeren <xref:System.Configuration.ConnectionStringSettings> tek giriş her biri temsil eden nesneleri **connectionStrings** bölümü. Bağlantı dizesi öznitelikleri, veya sağlayıcı adını belirterek bir bağlantı dizesi alma olanak tanıyan özelliklerini eşleyin.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Configuration.ConnectionStringSettings.Name%2A>|Bağlantı dizesinin adı. Eşlendiği **adı** özniteliği.|  
|<xref:System.Configuration.ConnectionStringSettings.ProviderName%2A>|Tam bir sağlayıcı adı. Eşlendiği **providerName** özniteliği.|  
|<xref:System.Configuration.ConnectionStringSettings.ConnectionString%2A>|Bağlantı dizesi. Eşlendiği **connectionString** özniteliği.|  
  
### <a name="example-listing-all-connection-strings"></a>Örnek: Tüm bağlantı dizelerini listeleme  
 Bu örnekte gezinir <xref:System.Configuration.ConnectionStringSettingsCollection> ve görüntüler <xref:System.Configuration.ConnectionStringSettings.Name%2A?displayProperty=nameWithType>, <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A?displayProperty=nameWithType>, ve <xref:System.Configuration.ConnectionStringSettings.ConnectionString%2A?displayProperty=nameWithType> konsol penceresinde özellikleri.  
  
> [!NOTE]
>  System.Configuration.dll dosyasına de tüm proje türlerine dahil değildir ve yapılandırma sınıflarını kullanmak için buna bir başvuru ayarlamanız gerekebilir. Belirli bir uygulama yapılandırma dosyasının konumunu ve adını, uygulama ve barındırma işlemi türüne göre değişir.  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfig#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfig/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfig#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfig/VB/source.vb#1)]  
  
### <a name="example-retrieving-a-connection-string-by-name"></a>Örnek: Adıyla bir bağlantı dizesini alma  
 Bu örnek adını belirterek bir yapılandırma dosyasından bağlantı dizesini almak nasıl gösterir. Kod oluşturur bir <xref:System.Configuration.ConnectionStringSettings> için sağlanan giriş parametresiyle eşleşen nesne <xref:System.Configuration.ConfigurationManager.ConnectionStrings%2A> adı. Hiç eşleşen adı bulunursa işlevi döndürür `null` (`Nothing` Visual Basic'te).  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByName#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByName/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByName#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByName/VB/source.vb#1)]  
  
### <a name="example-retrieving-a-connection-string-by-provider-name"></a>Örnek: Sağlayıcı adı ile bir bağlantı dizesini alma  
 Bu örnek biçiminde sağlayıcı değişmez değer adı belirterek bir bağlantı dizesini almak nasıl gösterir *System.Data.ProviderName*. Kod gezinir <xref:System.Configuration.ConnectionStringSettingsCollection> ve ilk bağlantı dizesini döndürür <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> bulunamadı. Sağlayıcı adı bulunamazsa, işlev döndürür `null` (`Nothing` Visual Basic'te).  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/VB/source.vb#1)]  
  
## <a name="encrypting-configuration-file-sections-using-protected-configuration"></a>Yapılandırma dosyası bölümleri kullanarak şifreleme korumalı yapılandırma  
 ASP.NET 2.0 kullanılmaya adlı yeni bir özellik *yapılandırmanın korumalı*, yapılandırma dosyasındaki hassas bilgileri şifrelemek etkinleştirir. Öncelikli olarak ASP.NET için tasarlanmış olsa da, Windows uygulamalarında yapılandırma dosyası bölümleri şifrelemek için korumalı yapılandırma de kullanılabilir. Korumalı yapılandırma özelliklerinin ayrıntılı bir açıklaması için bkz [şifreleme yapılandırma bilgilerini kullanarak korumalı Yapılandırması](https://docs.microsoft.com/previous-versions/aspnet/53tyfkaw(v=vs.100)).  
  
 Şu yapılandırma dosyasını gösterir parçalara **connectionStrings** şifrelenmiş sahip sonra bölüm. **ConfigProtectionProvider** şifreleme ve şifre çözme bağlantı dizeleri için kullanılan korumalı yapılandırma sağlayıcısını belirtir. **EncryptedData** bölüm şifre metni içerir.  
  
```xml  
<connectionStrings configProtectionProvider="DataProtectionConfigurationProvider">  
  <EncryptedData>  
    <CipherData>  
      <CipherValue>AQAAANCMnd8BFdERjHoAwE/Cl+sBAAAAH2... </CipherValue>  
    </CipherData>  
  </EncryptedData>  
</connectionStrings>  
```  
  
 .NET Framework belirtilen sağlayıcı şifreli bir bağlantı dizesi, çalışma zamanında alındığında şifresini çözmek için kullanır. **CipherValue** ve uygulamanızda kullanılabilir hale getirin. Şifre çözme işlemini yönetmek için ek kod yazmanız gerekmez.  
  
### <a name="protected-configuration-providers"></a>Korumalı yapılandırma sağlayıcıları  
 Korumalı yapılandırma sağlayıcıları kaydedilen **configProtectedData** bölümünü **machine.config** iki gösteren aşağıdaki parçası gösterildiği gibi yerel bilgisayarda dosya .NET Framework ile sağlanan yapılandırma sağlayıcıları korumalı. Burada gösterilen değerleri okunabilirlik için kesildi.  
  
```xml  
<configProtectedData defaultProvider="RsaProtectedConfigurationProvider">  
  <providers>  
    <add name="RsaProtectedConfigurationProvider"   
      type="System.Configuration.RsaProtectedConfigurationProvider, ... />  
    <add name="DataProtectionConfigurationProvider"   
      type="System.Configuration.DpapiProtectedConfigurationProvider, ... />  
  </providers>  
</configProtectedData>  
```  
  
 Ek korumalı yapılandırma sağlayıcıları ekleyerek yapılandırabilirsiniz **machine.config** dosya. Devralarak kendi korumalı yapılandırma sağlayıcısı oluşturabilirsiniz <xref:System.Configuration.ProtectedConfigurationProvider> soyut temel sınıf. Aşağıdaki tablo .NET Framework ile dahil iki yapılandırma dosyalarını açıklar.  
  
|Sağlayıcı|Açıklama|  
|--------------|-----------------|  
|<xref:System.Configuration.RsaProtectedConfigurationProvider>|Şifrelemek ve verilerin şifresini çözmek için RSA şifreleme algoritması kullanır. RSA algoritması, ortak anahtar şifreleme ve dijital imzalar için kullanılabilir. İki farklı anahtar kullanan olarak da bilinen "ortak anahtarı" ya da asimetrik şifreleme olmasıdır. Kullanabileceğiniz [ASP.NET IIS Kayıt Aracı (Aspnet_regiis.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/k6h9cz8h(v=vs.90)) Web.config dosyasında bölümleri şifrelemek ve şifreleme anahtarlarını yönetmek için. Dosya işlediğinde, ASP.NET yapılandırma dosyasının şifresini çözer. ASP.NET uygulamasını kimliği şifrelemek ve şifrelenmiş bölümlerindeki şifreyi çözmek için kullanılan şifreleme anahtarını okuma erişiminiz olması gerekir.|  
|<xref:System.Configuration.DpapiProtectedConfigurationProvider>|Yapılandırma bölümleri şifrelemek için Windows Data Protection API (DPAPI) kullanır. Windows yerleşik Şifreleme Hizmetleri kullanır ve makineye özgü ya da kullanıcı hesaplarına özgü koruması için yapılandırılabilir. Makineye özgü koruma, bilgi paylaşımı için gereken aynı sunucuda birden fazla uygulama için yararlıdır. Kullanıcı hesaplarına özgü koruma, paylaşılan bir barındırma ortamı gibi belirli bir kullanıcı kimliği ile çalışan hizmetler ile kullanılabilir. Her uygulama, dosyalar ve veritabanları gibi kaynaklara erişimi kısıtlayan ayrı bir kimlik altında çalışır.|  
  
 Her iki sağlayıcıları verileri güçlü şifreleme sağlar. Ancak, Web grubu gibi yalnızca birden çok sunucuda aynı şifrelenmiş yapılandırma dosyası kullanmayı planladığınıza varsa <xref:System.Configuration.RsaProtectedConfigurationProvider> verileri şifrelemek ve bunları başka bir sunucuya almak için kullanılan şifreleme anahtarlarını dışarı aktarmak sağlar. Daha fazla bilgi için [alma ve verme korumalı yapılandırma RSA anahtar kapsayıcılarının](https://docs.microsoft.com/previous-versions/aspnet/yxw286t2(v=vs.100)).  
  
### <a name="using-the-configuration-classes"></a>Yapılandırma sınıflarını kullanma  
 <xref:System.Configuration> Ad alanı yapılandırma ayarları ile çalışma için sınıflar sağlar programlı olarak. <xref:System.Configuration.ConfigurationManager> Sınıfı makine, uygulama ve kullanıcı yapılandırma dosyalarına erişim sağlar. Bir ASP.NET uygulaması oluşturuyorsanız, kullanabileceğiniz <xref:System.Web.Configuration.WebConfigurationManager> olsa da gibi ASP.NET uygulamalarının özgü ayarları erişmenize olanak tanıyan bulunan aynı işlevselliği sağlar sınıfını  **\< System.Web >**.  
  
> [!NOTE]
>  <xref:System.Security.Cryptography> Ad alanı, şifreleme ve verilerin şifresini çözmek için ek seçenekler sağlayan sınıflar içerir. Yapılandırma kullanılarak kullanılabilir olmayan Şifreleme Hizmetleri korumalı gerektiriyorsa, bu sınıfları kullanın. Diğerleri yalnızca yönetilen uygulamalar bu sınıfların bazıları için yönetilmeyen Microsoft CryptoAPI sarmalayıcıları bağlıdır. Daha fazla bilgi için [Şifreleme Hizmetleri](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/93bskf9z(v=vs.90)).  
  
### <a name="appconfig-example"></a>App.config örneği  
 Bu örnekte şifreleme geçiş yapmayı gösteren **connectionStrings** konusundaki bir **app.config** bir Windows uygulaması için dosya. Bu örnekte, yordam bağımsız değişkeni, örneğin, "MyApplication.exe" olarak uygulamanın adını alır. **App.config** dosya ardından şifrelenir ve "MyApplication.exe.config" adı altında yürütülebilir dosyayı içeren klasöre kopyalanır.  
  
> [!NOTE]
>  Bağlantı dizesini yalnızca şifrelenmiş olan bilgisayarda şifresi çözülebilir.  
  
 Kod <xref:System.Configuration.ConfigurationManager.OpenExeConfiguration%2A> açmak için yöntemi **app.config** düzenleme, dosya ve <xref:System.Configuration.ConfigurationManager.GetSection%2A> yöntemi döndürür **connectionStrings** bölümü. Ardından kod denetler <xref:System.Configuration.SectionInformation.IsProtected%2A> özelliği, arama <xref:System.Configuration.SectionInformation.ProtectSection%2A> , şifreli değilse bölüm şifrelemek için. <xref:System.Configuration.SectionInformation.UnprotectSection%2A> Yöntemi bölümü şifresini çözmek için çağrılır. <xref:System.Configuration.Configuration.Save%2A> Yöntemi işlemi tamamlandıktan ve değişiklikleri kaydeder.  
  
> [!NOTE]
>  Bir başvuru ayarlamanız gerekir `System.Configuration.dll` çalıştırmak kodu projenizdeki.  
  
 [!code-csharp[DataWorks ConnectionStrings.Encrypt#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStrings.Encrypt/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStrings.Encrypt#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStrings.Encrypt/VB/source.vb#1)]  
  
### <a name="webconfig-example"></a>Web.config örneği  
 Bu örnekte <xref:System.Web.Configuration.WebConfigurationManager.OpenWebConfiguration%2A> yöntemi `WebConfigurationManager`. Bu durumda, göreli yol sağlayabiliyor Not **Web.config** bir tilde işareti kullanarak dosya. Kod başvurusu gerektirir `System.Web.Configuration` sınıfı.  
  
 [!code-csharp[DataWorks ConnectionStringsWeb.Encrypt#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringsWeb.Encrypt/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringsWeb.Encrypt#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringsWeb.Encrypt/VB/source.vb#1)]  
  
 ASP.NET uygulamalarının güvenliğini sağlama hakkında daha fazla bilgi için bkz. [güvenli hale getirme ASP.NET web siteleri](https://docs.microsoft.com/previous-versions/aspnet/91f66yxt(v=vs.100)).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağlantı Dizesi Oluşturucular](../../../../docs/framework/data/adonet/connection-string-builders.md)
- [Bağlantı Bilgilerini Koruma](../../../../docs/framework/data/adonet/protecting-connection-information.md)
- [Yapılandırma sınıflarını kullanma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ms228063(v=vs.90))
- [Uygulamaları Yapılandırma](../../../../docs/framework/configure-apps/index.md)
- [ASP.NET Web sitesi yönetimi](https://docs.microsoft.com/previous-versions/aspnet/6hy1xzbw(v=vs.100))
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
