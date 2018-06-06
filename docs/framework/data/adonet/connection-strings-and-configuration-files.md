---
title: Bağlantı dizeleri ve yapılandırma dosyaları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 37df2641-661e-407a-a3fb-7bf9540f01e8
ms.openlocfilehash: 629d08b60330125a7bb491a58499b5e2bc7d2091
ms.sourcegitcommit: fc70fcb9c789b6a4aefcdace46f3643fd076450f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2018
ms.locfileid: "34805691"
---
# <a name="connection-strings-and-configuration-files"></a>Bağlantı dizeleri ve yapılandırma dosyaları
Uygulamanızın kodda bağlantı dizelerini katıştırma Güvenlik Açıkları ve Bakım sorunlarına yol açabilir. Bir uygulamanın kaynak koda derlenmiş şifrelenmemiş bir bağlantı dizeleri kullanılarak görüntülenebilir [Ildasm.exe (IL ayrıştırıcı)](../../../../docs/framework/tools/ildasm-exe-il-disassembler.md) aracı. Bağlantı dizesi hiç değişirse, ayrıca, uygulamanızı yeniden derlenmesi gerekiyor. Bu nedenlerle, bir uygulama yapılandırma dosyasında bağlantı dizeleri depolamanızı öneririz.  
  
## <a name="working-with-application-configuration-files"></a>Uygulama yapılandırma dosyaları ile çalışma  
 Uygulama yapılandırma dosyaları, belirli bir uygulamaya özgü ayarları içerir. Örneğin, bir ASP.NET uygulaması bir veya daha fazla olabilir **web.config** dosyaları ve bir Windows uygulaması olabilir isteğe bağlı bir **app.config** dosya. Bir yapılandırma dosyası konumunu ve adını uygulamanın ana bağlı olarak farklılık gösterir ancak ortak öğeler, yapılandırma dosyalarını paylaşın.  
  
### <a name="the-connectionstrings-section"></a>Bölüm connectionStrings  
 Bağlantı dizeleri, anahtar/değer çiftleri olarak depolanabilir **connectionStrings** bölümünü **yapılandırma** uygulama yapılandırma dosyası öğesi. Alt öğeler içerir **ekleme**, **temizleyin**, ve **kaldırmak**.  
  
 Aşağıdaki yapılandırma dosyası parça şeması ve bir bağlantı dizesi depolamak için sözdizimi gösterilmektedir. **Adı** özniteliktir, böylece çalışma zamanında alınabilmesi için bir bağlantı dizesi benzersiz şekilde tanımlamak için sağlayan bir ad. **ProviderName** machine.config dosyasında kayıtlı .NET Framework veri sağlayıcısı değişmez adı.  
  
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
>  Bir yapılandırma dosyasında bir bağlantı dizesi parçası kaydedip kullanabileceğiniz <xref:System.Data.Common.DbConnectionStringBuilder> çalışma zamanında tamamlamak için sınıf. Bu, burada vaktinden ya da yapılandırma dosyasında hassas bilgileri kaydetmek istiyor musunuz bağlantı dizesinin öğeleri bilmiyorsanız senaryolarda kullanışlıdır. Daha fazla bilgi için bkz: [bağlantı dizesi oluşturucular](../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
### <a name="using-external-configuration-files"></a>Dış yapılandırma dosyalarını kullanma  
 Dış yapılandırma dosyalarını, tek bir bölümden oluşan bir yapılandırma dosyası bir parçasını içeren ayrı dosyalarıdır. Dış yapılandırma dosyası sonra ana yapılandırma dosyası tarafından başvuruluyor. Depolama **connectionStrings** fiziksel olarak ayrı bir dosya bölümünde burada bağlantı dizeleri düzenlenmesi uygulama dağıtıldıktan sonra durumlarda yararlıdır. Örneğin, standart ASP.NET davranışını yapılandırma dosyalarını değiştirildiğinde, durum bilgilerini kaybolmasına sonuçlanır uygulama etki alanını yeniden başlatmaktır. Ancak, bir dış yapılandırma dosyasını değiştirerek uygulama yeniden başlatma neden olmaz. Dış yapılandırma dosyalarını, ASP.NET ile sınırlı değildir; Windows uygulamaları tarafından da kullanılabilir. Ayrıca, dosya erişim güvenliği ve izinleri dış yapılandırma dosyalara erişimi kısıtlamak için kullanılabilir. Çalışma zamanında dış yapılandırma dosyalarıyla çalışma saydamdır ve hiçbir özel kodlama gerektirir.  
  
 Bağlantı dizeleri bir dış yapılandırma dosyasında depolamak için yalnızca içeren ayrı bir dosya oluşturmak **connectionStrings** bölümü. Herhangi bir ek öğeler, bölümleri veya öznitelikler eklemeyin. Bu örnek, bir dış yapılandırma dosyası sözdizimi gösterir.  
  
```xml  
<connectionStrings>  
  <add name="Name"   
   providerName="System.Data.ProviderName"   
   connectionString="Valid Connection String;" />  
</connectionStrings>  
```  
  
 Ana uygulama yapılandırma dosyasında kullandığınız **configSource** tam adını ve dış dosyanın konumunu belirtmek için özniteliği. Bu örnek adlı bir dış yapılandırma dosyasına başvuruyor `connections.config`.  
  
```xml  
<?xml version='1.0' encoding='utf-8'?>  
<configuration>  
    <connectionStrings configSource="connections.config"/>  
</configuration>  
```  
  
## <a name="retrieving-connection-strings-at-run-time"></a>Çalışma zamanında bağlantı dizeleri alma  
 .NET Framework 2.0 yeni sınıflar sunulan <xref:System.Configuration> yapılandırma dosyaları alınıyor bağlantı dizeleri çalışma zamanında basitleştirmek için ad alanı. Bir bağlantı dizesi adı veya sağlayıcı adı tarafından program aracılığıyla alabilir.  
  
> [!NOTE]
>  **Machine.config** dosyasında bir **connectionStrings** bölümünde, Visual Studio tarafından kullanılan bağlantı dizeleri içerir. Bağlantı dizeleri sağlayıcı adı tarafından alınırken **app.config** bağlantı dizeleri olan bir Windows uygulaması dosyasında **machine.config** yüklenen ilk ve girişleri alma**app.config**. Ekleme **temizleyin** hemen sonra **connectionStrings** öğesi devralınan tüm başvuruları kaldırır, bellekte veri yapısından böylece yalnızca bağlantı dizeleri yerel tanımlanan**app.config** dosya olarak kabul edilir.  
  
### <a name="working-with-the-configuration-classes"></a>Yapılandırma sınıfları ile çalışma  
 .NET Framework 2.0 ile başlayan <xref:System.Configuration.ConfigurationManager> kullanım dışı değiştirerek yerel bilgisayarda yapılandırma dosyaları ile çalışırken kullanılan <xref:System.Configuration.ConfigurationSettings>. <xref:System.Web.Configuration.WebConfigurationManager> ASP.NET yapılandırma dosyaları ile çalışmak için kullanılır. Bir Web sunucusundaki yapılandırma dosyaları ile çalışmak üzere tasarlanmış ve yapılandırma dosyası bölümleri için programlı erişim gibi izin verir **system.web**.  
  
> [!NOTE]
>  Yapılandırma dosyaları çalışma zamanında erişme izinleri çağırana verme gerektirir; gerekli izinleri uygulama ve yapılandırma dosyası konumu türüne bağlıdır. Daha fazla bilgi için bkz: [yapılandırma sınıfları kullanma](http://msdn.microsoft.com/library/98d2b386-baf6-4a17-974b-76e3b4c87acc) ve <xref:System.Web.Configuration.WebConfigurationManager> ASP.NET uygulamaları için ve <xref:System.Configuration.ConfigurationManager> Windows uygulamaları için.  
  
 Kullanabileceğiniz <xref:System.Configuration.ConnectionStringSettingsCollection> uygulama yapılandırma dosyalarından bağlantı dizeleri alınamadı. Bir koleksiyonu içerir <xref:System.Configuration.ConnectionStringSettings> nesneleri, her biri tek bir giriş temsil eden **connectionStrings** bölümü. Bir bağlantı dizesi adı veya sağlayıcı adı belirterek almanıza olanak sağlayan bağlantı dizesi öznitelikleri için özellikleriyle eşleyin.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Configuration.ConnectionStringSettings.Name%2A>|Bağlantı dizesi adı. Eşlendiği **adı** özniteliği.|  
|<xref:System.Configuration.ConnectionStringSettings.ProviderName%2A>|Tam sağlayıcı adı. Eşlendiği **providerName** özniteliği.|  
|<xref:System.Configuration.ConnectionStringSettings.ConnectionString%2A>|Bağlantı dizesi. Eşlendiği **connectionString** özniteliği.|  
  
### <a name="example-listing-all-connection-strings"></a>Örnek: Tüm bağlantı dizeleri listeleme  
 Bu örnek dolaşır `ConnectionStringSettings` toplama ve görüntüler <xref:System.Configuration.ConnectionStringSettings.Name%2A>, <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A>, ve <xref:System.Configuration.ConnectionStringSettings.ConnectionString%2A> konsol penceresinde özellikler.  
  
> [!NOTE]
>  System.Configuration.dll içindeki tüm proje türler bulunmaz ve yapılandırma sınıfları kullanmak için bir başvuru ayarlamanız gerekebilir. Belirli bir uygulama yapılandırma dosyasının konumunu ve adını, uygulama ve barındırma işlemi türüne göre değişir.  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfig#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfig/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfig#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfig/VB/source.vb#1)]  
  
### <a name="example-retrieving-a-connection-string-by-name"></a>Örnek: bir bağlantı dizesi ada göre alma  
 Bu örnek adını belirterek bir yapılandırma dosyasından bağlantı dizesini almak nasıl gösterir. Kod oluşturur bir <xref:System.Configuration.ConnectionStringSettings> sağlanan giriş parametresi olarak eşleşen nesne <xref:System.Configuration.ConfigurationManager.ConnectionStrings%2A> adı. Eşleşen ad bulunursa işlevi döndürür `null` (`Nothing` Visual Basic'te).  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByName#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByName/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByName#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByName/VB/source.vb#1)]  
  
### <a name="example-retrieving-a-connection-string-by-provider-name"></a>Örnek: bir bağlantı dizesi sağlayıcı ada göre alma  
 Bu örnek bir bağlantı dizesi şu biçimde sağlayıcı değişmez değer adı belirterek almayı gösterir *System.Data.ProviderName*. Kod dolaşır <xref:System.Configuration.ConnectionStringSettingsCollection> ve ilk bağlantı dizesini döndürür <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> bulundu. Sağlayıcı adı bulunamazsa, işlevi döndürür `null` (`Nothing` Visual Basic'te).  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/VB/source.vb#1)]  
  
## <a name="encrypting-configuration-file-sections-using-protected-configuration"></a>Yapılandırma dosyası bölümleri kullanarak şifreleme korumalı yapılandırma  
 ASP.NET 2.0 sunulan adlı yeni bir özellik *yapılandırma korumalı*, bir yapılandırma dosyası gizli bilgileri şifrelemek etkinleştirir. Öncelikli olarak ASP.NET için tasarlanmış olsa da, korumalı yapılandırma Windows uygulamalarında yapılandırma dosyası bölümleri şifrelemek için de kullanılabilir. Korumalı yapılandırma özellikleri ayrıntılı bir açıklaması için bkz: [şifreleme yapılandırma bilgilerini kullanarak korumalı Yapılandırması](http://msdn.microsoft.com/library/51cdfe5b-9d82-458c-94ff-c551c4f38ed1).  
  
 Aşağıdaki yapılandırma dosyası gösterir parçalara **connectionStrings** şifrelenmiş sahip sonra bölüm. **ConfigProtectionProvider** şifrelemek ve bağlantı dizeleri şifresini çözmek için kullanılan korumalı yapılandırma sağlayıcısı belirtir. **EncryptedData** bölüm şifreli metin içerir.  
  
```xml  
<connectionStrings configProtectionProvider="DataProtectionConfigurationProvider">  
  <EncryptedData>  
    <CipherData>  
      <CipherValue>AQAAANCMnd8BFdERjHoAwE/Cl+sBAAAAH2... </CipherValue>  
    </CipherData>  
  </EncryptedData>  
</connectionStrings>  
```  
  
 .NET Framework belirtilen sağlayıcı şifreli bir bağlantı dizesi çalışma zamanında alındığında şifresini çözmek için kullanır. **CipherValue** ve uygulamanız için kullanılabilir hale getirin. Şifre çözme işlemini yönetmek için herhangi bir ek kod yazmanız gerekmez.  
  
### <a name="protected-configuration-providers"></a>Korumalı yapılandırma sağlayıcıları  
 İçinde kayıtlı korumalı yapılandırma sağlayıcı **configProtectedData** bölümünü **machine.config** iki gösteren aşağıdaki parçasında gösterildiği gibi yerel bilgisayarda dosya .NET Framework ile sağlanan bir yapılandırma sağlayıcısı korumalı. Burada gösterilen değerleri okunabilirlik için kesildi.  
  
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
  
 Ek korumalı yapılandırma sağlayıcıları ekleyerek yapılandırabileceğiniz **machine.config** dosya. Kendi korumalı yapılandırma sağlayıcısı devralarak oluşturabilirsiniz <xref:System.Configuration.ProtectedConfigurationProvider> soyut taban sınıfı. Aşağıdaki tabloda .NET Framework ile dahil iki yapılandırma dosyalarını açıklar.  
  
|Sağlayıcı|Açıklama|  
|--------------|-----------------|  
|<xref:System.Configuration.RsaProtectedConfigurationProvider>|Şifrelemek ve verilerin şifresini çözmek için RSA şifreleme algoritması kullanır. RSA algoritması, ortak anahtar şifreleme ve dijital imzalar için kullanılabilir. İki farklı anahtarlara nedeniyledir "ortak anahtarı" ya da değiştirip asimetrik şifreleme olarak da bilinir değil. Kullanabileceğiniz [ASP.NET IIS Kayıt Aracı (Aspnet_regiis.exe)](http://msdn.microsoft.com/library/6491c41e-e2b0-481f-9863-db3614d5f96b) Web.config dosyasında bölümleri şifrelemek ve şifreleme anahtarlarını yönetmek için. Dosyayı işlediğinde, ASP.NET yapılandırma dosyasının şifresini çözer. ASP.NET uygulaması kimliğinin şifrelemek ve şifrelenmiş bölümlerindeki şifreyi çözmek için kullanılan şifreleme anahtarını okuma erişimi olmalıdır.|  
|<xref:System.Configuration.DpapiProtectedConfigurationProvider>|Yapılandırma bölümleri şifrelemek için Windows Data Protection API (DPAPI) kullanır. Windows yerleşik Şifreleme Hizmetleri kullanır ve makine özgü veya kullanıcı hesabı özel koruma için yapılandırılabilir. Makine özgü koruma bilgi paylaşmak için gereken aynı sunucuda birden çok uygulama için yararlıdır. Kullanıcı hesabı özel koruma, paylaşılan bir barındırma ortamı gibi belirli kullanıcı kimliği ile çalışan hizmetler ile kullanılabilir. Her uygulama dosyaları ve veritabanları gibi kaynaklara erişimi kısıtlayan ayrı bir kimlik altında çalışır.|  
  
 Her iki sağlayıcıları veri güçlü şifreleme sunar. Ancak, bir Web grubu gibi yalnızca birden çok sunucuda aynı şifrelenmiş yapılandırma dosyası kullanmak planlama, `RsaProtectedConfigurationProvider` , verileri şifrelemek ve başka bir sunucuda almak için kullanılan şifreleme anahtarlarını vermenize olanak sağlar. Daha fazla bilgi için bkz: [alma ve verme korumalı yapılandırma RSA anahtar kapsayıcıları](http://msdn.microsoft.com/library/f3022b39-f17f-48c1-b067-025eab0ce8bc).  
  
### <a name="using-the-configuration-classes"></a>Yapılandırma sınıflarını kullanma  
 <xref:System.Configuration> Ad alanı yapılandırma ayarları ile çalışmak için sınıflar sağlar programlı olarak. <xref:System.Configuration.ConfigurationManager> Sınıfı makine, uygulama ve kullanıcı yapılandırma dosyalarına erişim sağlar. Bir ASP.NET uygulaması oluşturuyorsanız, kullanabileceğiniz <xref:System.Web.Configuration.WebConfigurationManager> da olanlar gibi ASP.NET uygulamaları özgü ayarları erişmesine olanak tanıyan bulundu ancak, aynı işlevselliği sağlayan sınıf  **\< System.Web >**.  
  
> [!NOTE]
>  <xref:System.Security.Cryptography> Ad alanı, şifreleme ve verilerin şifresini çözmek için ek seçenekler sağlayan sınıflar içerir. Kullanılabilir kullanarak olmayan Şifreleme Hizmetleri Yapılandırması korumalı gerekiyorsa bu sınıfların kullanın. Başkalarının tamamen yönetilen uygulamaları çalışırken bu sınıfların yönetilmeyen Microsoft CryptoAPI için sarmalayıcıları bazılarıdır. Daha fazla bilgi için bkz: [Şifreleme Hizmetleri](http://msdn.microsoft.com/library/68a1e844-c63c-44af-9247-f6716eb23781).  
  
### <a name="appconfig-example"></a>App.config örneği  
 Bu örnek şifreleme geçiş yapmayı gösteren **connectionStrings** bölümüne bir **app.config** dosyası bir Windows uygulaması için. Bu örnekte, yordam bağımsız değişken, örneğin, "MyApplication.exe" olarak uygulama adını alır. **App.config** dosya sonra şifrelenir ve yürütülebilir dosya adı "MyApplication.exe.config" altında içeren klasöre kopyalanır.  
  
> [!NOTE]
>  Bağlantı dizesi şifrelenmiş olan bilgisayarda yalnızca şifresi çözülebilir.  
  
 Kod kullanan <xref:System.Configuration.ConfigurationManager.OpenExeConfiguration%2A> açmak için yöntemi **app.config** düzenleme, dosya ve <xref:System.Configuration.ConfigurationManager.GetSection%2A> yöntemi döndürür **connectionStrings** bölüm. Kod sonra denetler <xref:System.Configuration.SectionInformation.IsProtected%2A> özelliği, arama <xref:System.Configuration.SectionInformation.ProtectSection%2A> , şifreli değilse bölüm şifrelemek için. <xref:System.Configuration.SectionInformation.UnprotectSection%2A> Yöntemi bölüm şifresini çözmek için çağrılır. <xref:System.Configuration.Configuration.Save%2A> Yöntemi işlemi tamamlandıktan ve değişiklikleri kaydeder.  
  
> [!NOTE]
>  Bir başvuru ayarlamalısınız `System.Configuration.dll` projenizdeki çalıştırmak için kod.  
  
 [!code-csharp[DataWorks ConnectionStrings.Encrypt#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStrings.Encrypt/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStrings.Encrypt#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStrings.Encrypt/VB/source.vb#1)]  
  
### <a name="webconfig-example"></a>Web.config örneği  
 Bu örnekte <xref:System.Web.Configuration.WebConfigurationManager.OpenWebConfiguration%2A> yöntemi `WebConfigurationManager`. Bu durumda, göreli yol sağlayabiliyor Not **Web.config** bir tilde kullanarak dosya. Kod bir başvuru gerektirir `System.Web.Configuration` sınıfı.  
  
 [!code-csharp[DataWorks ConnectionStringsWeb.Encrypt#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringsWeb.Encrypt/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringsWeb.Encrypt#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringsWeb.Encrypt/VB/source.vb#1)]  
  
 ASP.NET uygulamalarının güvenliğini sağlama daha fazla bilgi için bkz: [NIB: ASP.NET güvenlik](http://msdn.microsoft.com/library/04b37532-18d9-40b4-8e5f-ee09a70b311d) ve [ASP.NET 2.0 güvenlik uygulamaları bir bakışta](http://go.microsoft.com/fwlink/?LinkId=59997) ASP.NET Geliştirici Merkezi'ndeki.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bağlantı Dizesi Oluşturucular](../../../../docs/framework/data/adonet/connection-string-builders.md)  
 [Bağlantı Bilgilerini Koruma](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 [Yapılandırma sınıflarını kullanma](http://msdn.microsoft.com/library/98d2b386-baf6-4a17-974b-76e3b4c87acc)  
 [Uygulamaları Yapılandırma](../../../../docs/framework/configure-apps/index.md)  
 [ASP.NET Web sitesi yönetimi](http://msdn.microsoft.com/library/1298034b-5f7d-464d-abd1-ad9e6b3eeb7e)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
