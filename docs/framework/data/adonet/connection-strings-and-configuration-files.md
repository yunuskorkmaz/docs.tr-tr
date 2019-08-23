---
title: Bağlantı Dizeleri ve Yapılandırma Dosyaları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 37df2641-661e-407a-a3fb-7bf9540f01e8
ms.openlocfilehash: 3a1b0b947b97eac52e06626d2ed6d47bb9700147
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949456"
---
# <a name="connection-strings-and-configuration-files"></a>Bağlantı Dizeleri ve Yapılandırma Dosyaları
Uygulamanızın koduna bağlantı dizeleri katıştırmak, güvenlik açıklarına ve bakım sorunlarına yol açabilir. Bir uygulamanın kaynak kodunda derlenen şifrelenmemiş bağlantı dizeleri [ıldadsm. exe (IL Disassembler)](../../../../docs/framework/tools/ildasm-exe-il-disassembler.md) Aracı kullanılarak görüntülenebilir. Ayrıca, bağlantı dizesi herhangi bir zaman değişirse uygulamanızın yeniden derlenmesi gerekir. Bu nedenlerden dolayı, bağlantı dizelerini bir uygulama yapılandırma dosyasında depolamanızı öneririz.  
  
## <a name="working-with-application-configuration-files"></a>Uygulama yapılandırma dosyalarıyla çalışma  
 Uygulama yapılandırma dosyaları, belirli bir uygulamaya özgü ayarları içerir. Örneğin, bir ASP.NET uygulamasının bir veya daha fazla **Web. config** dosyası olabilir ve bir Windows uygulaması isteğe bağlı bir **app. config** dosyasına sahip olabilir. Yapılandırma dosyaları ortak öğeleri paylaşır, ancak bir yapılandırma dosyasının adı ve konumu uygulamanın ana bilgisayarına bağlı olarak değişir.  
  
### <a name="the-connectionstrings-section"></a>ConnectionStrings bölümü  
 Bağlantı dizeleri, bir uygulama yapılandırma dosyasının **yapılandırma** öğesinin **connectionStrings** bölümünde anahtar/değer çiftleri olarak depolanabilir. Alt öğeler **ekleme**, **Temizleme**ve **kaldırma**içerir.  
  
 Aşağıdaki yapılandırma dosyası parçası, bir bağlantı dizesini depolamak için şemayı ve sözdizimini gösterir. **Ad** özniteliği, bir bağlantı dizesini, çalışma zamanında alınabilmesi için benzersiz şekilde tanımlamak için sağladığınız addır. **ProviderName** , Machine. config dosyasında kayıtlı olan .NET Framework veri sağlayıcısının sabit adıdır.  
  
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
> Bir bağlantı dizesinin bir bölümünü yapılandırma dosyasına kaydedebilir ve çalışma zamanında bunu gerçekleştirmek için <xref:System.Data.Common.DbConnectionStringBuilder> sınıfını kullanabilirsiniz. Bu, bağlantı dizesinin, zaman içinde veya bir yapılandırma dosyasına hassas bilgileri kaydetmek istemediğiniz senaryolarda faydalıdır... Daha fazla bilgi için bkz. [bağlantı dizesi oluşturucuları](../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
### <a name="using-external-configuration-files"></a>Dış yapılandırma dosyalarını kullanma  
 Dış yapılandırma dosyaları, tek bir bölümden oluşan bir yapılandırma dosyasının bir parçasını içeren ayrı dosyalardır. Dış yapılandırma dosyasına daha sonra ana yapılandırma dosyası tarafından başvurulur. **ConnectionString** bölümünü fiziksel olarak ayrı bir dosyada depolamak, uygulama dağıtıldıktan sonra bağlantı dizelerinin düzenlenebileceği durumlarda faydalıdır. Örneğin, standart ASP.NET davranışı yapılandırma dosyaları değiştirildiğinde bir uygulama etki alanını yeniden başlatmakta, bu da durum bilgilerinin kaybolmasına neden olur. Ancak, bir dış yapılandırma dosyasının değiştirilmesi, uygulamanın yeniden başlatılmasına neden olmaz. Dış yapılandırma dosyaları ASP.NET ile sınırlı değildir; Bunlar, Windows uygulamaları tarafından da kullanılabilir. Ayrıca, dosya erişimi güvenliği ve izinleri dış yapılandırma dosyalarına erişimi kısıtlamak için kullanılabilir. Çalışma zamanında dış yapılandırma dosyalarıyla çalışma işlemi saydamdır ve özel bir kodlama gerektirmez.  
  
 Bağlantı dizelerini bir dış yapılandırma dosyasında depolamak için, yalnızca **connectionStrings** bölümünü içeren ayrı bir dosya oluşturun. Herhangi bir ek öğe, bölüm veya öznitelik eklemeyin. Bu örnek, bir dış yapılandırma dosyası için söz dizimini gösterir.  
  
```xml  
<connectionStrings>  
  <add name="Name"   
   providerName="System.Data.ProviderName"   
   connectionString="Valid Connection String;" />  
</connectionStrings>  
```  
  
 Ana uygulama yapılandırma dosyasında, dış dosyanın tam adını ve konumunu belirtmek için **configSource** özniteliğini kullanırsınız. Bu örnek adlı `connections.config`bir dış yapılandırma dosyası anlamına gelir.  
  
```xml  
<?xml version='1.0' encoding='utf-8'?>  
<configuration>  
    <connectionStrings configSource="connections.config"/>  
</configuration>  
```  
  
## <a name="retrieving-connection-strings-at-run-time"></a>Çalışma zamanında bağlantı dizelerini alma  
 .NET Framework 2,0, çalışma zamanında yapılandırma dosyalarından bağlantı <xref:System.Configuration> dizelerini almayı kolaylaştırmak için ad alanına yeni sınıflar getirmiştir. Bir bağlantı dizesini ada veya sağlayıcı adına göre program aracılığıyla alabilirsiniz.  
  
> [!NOTE]
> **Machine. config** dosyası Ayrıca, Visual Studio tarafından kullanılan bağlantı dizelerini Içeren bir **connectionStrings** bölümü içerir. Bir Windows uygulamasındaki **app. config** dosyasından sağlayıcı adına göre bağlantı dizeleri alınırken, **Machine. config** dosyasındaki bağlantı dizeleri önce yüklenir, sonra **app. config**' den girişler. **ConnectionString** öğesinden hemen sonra **clear seçeneğinin** eklenmesi, yalnızca yerel **app. config** dosyasında tanımlanan bağlantı dizelerinin kabul edilmesi için bellekteki veri yapısındaki tüm devralınan başvuruları kaldırır.  
  
### <a name="working-with-the-configuration-classes"></a>Yapılandırma sınıflarıyla çalışma  
 .NET Framework 2,0 ' den başlayarak, <xref:System.Configuration.ConfigurationManager> yerel bilgisayardaki yapılandırma dosyalarıyla çalışırken kullanım dışı <xref:System.Configuration.ConfigurationSettings>olarak değiştirilerek kullanılır. <xref:System.Web.Configuration.WebConfigurationManager>, ASP.NET yapılandırma dosyalarıyla çalışmak için kullanılır. Bir Web sunucusunda yapılandırma dosyalarıyla çalışmak üzere tasarlanmıştır ve **System. Web**gibi yapılandırma dosyası bölümlerine programlı erişim sağlar.  
  
> [!NOTE]
> Çalışma zamanında yapılandırma dosyalarına erişilmesi arayan için izin verilmesini gerektirir; gerekli izinler, uygulamanın, yapılandırma dosyasının ve konumun türüne bağlıdır. Daha fazla bilgi için bkz. [yapılandırma sınıflarını](https://docs.microsoft.com/previous-versions/aspnet/ms228063(v=vs.100)) ve <xref:System.Web.Configuration.WebConfigurationManager> ASP.NET uygulamalarını kullanma ve <xref:System.Configuration.ConfigurationManager> Windows uygulamaları için.  
  
 Uygulama yapılandırma dosyalarından bağlantı <xref:System.Configuration.ConnectionStringSettingsCollection> dizelerini almak için öğesini kullanabilirsiniz. Her biri **ConnectionString** bölümünde tek <xref:System.Configuration.ConnectionStringSettings> bir girişi temsil eden bir nesne koleksiyonu içerir. Özellikleri bağlantı dizesi öznitelikleriyle eşlenir ve ad ya da sağlayıcı adını belirterek bir bağlantı dizesi almanızı sağlar.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Configuration.ConnectionStringSettings.Name%2A>|Bağlantı dizesinin adı. **Ad** özniteliğiyle eşlenir.|  
|<xref:System.Configuration.ConnectionStringSettings.ProviderName%2A>|Tam sağlayıcı adı. **ProviderName** özniteliğiyle eşlenir.|  
|<xref:System.Configuration.ConnectionStringSettings.ConnectionString%2A>|Bağlantı dizesi. **ConnectionString** özniteliğiyle eşlenir.|  
  
### <a name="example-listing-all-connection-strings"></a>Örnek: Tüm bağlantı dizelerini listeleme  
 Bu örnek içinde <xref:System.Configuration.ConnectionStringSettingsCollection> yinelenir ve konsol penceresinde <xref:System.Configuration.ConnectionStringSettings.Name%2A?displayProperty=nameWithType>, <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A?displayProperty=nameWithType>, ve <xref:System.Configuration.ConnectionStringSettings.ConnectionString%2A?displayProperty=nameWithType> özelliklerini görüntüler.  
  
> [!NOTE]
> System. Configuration. dll tüm proje türlerine dahil değildir ve yapılandırma sınıflarını kullanmak için buna bir başvuru ayarlamanız gerekebilir. Belirli bir uygulama yapılandırma dosyasının adı ve konumu, uygulama türüne ve barındırma işlemine göre farklılık gösterir.  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfig#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfig/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfig#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfig/VB/source.vb#1)]  
  
### <a name="example-retrieving-a-connection-string-by-name"></a>Örnek: Bir bağlantı dizesini ada göre alma  
 Bu örnek, bir yapılandırma dosyasından adını belirterek bir bağlantı dizesinin nasıl alınacağını gösterir. Kod, <xref:System.Configuration.ConfigurationManager.ConnectionStrings%2A> adı verilen <xref:System.Configuration.ConnectionStringSettings> giriş parametresiyle eşleşen bir nesne oluşturur. Eşleşen ad bulunamazsa, işlev döndürür `null` (`Nothing` Visual Basic).  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByName#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByName/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByName#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByName/VB/source.vb#1)]  
  
### <a name="example-retrieving-a-connection-string-by-provider-name"></a>Örnek: Sağlayıcı adına göre bir bağlantı dizesi alınıyor  
 Bu örnek, *System. Data. ProviderName*biçiminde sağlayıcı-sabit adı belirtilerek bir bağlantı dizesinin nasıl alınacağını gösterir. Kod üzerinden <xref:System.Configuration.ConnectionStringSettingsCollection> yinelenir ve ilk <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> bulunan için bağlantı dizesini döndürür. Sağlayıcı adı bulunamazsa, işlev döndürür `null` (`Nothing` Visual Basic).  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/VB/source.vb#1)]  
  
## <a name="encrypting-configuration-file-sections-using-protected-configuration"></a>Korumalı yapılandırma kullanarak yapılandırma dosyası bölümlerini şifreleme  
 ASP.NET 2,0, *korunan yapılandırma*adlı, önemli bilgileri bir yapılandırma dosyasında şifrelemenizi sağlayan yeni bir özellik sunmuştur. Birincil olarak ASP.NET için tasarlanmış olsa da, korumalı yapılandırma Windows uygulamalarındaki yapılandırma dosyası bölümlerini şifrelemek için de kullanılabilir. Korunan yapılandırma özelliklerine ilişkin ayrıntılı bir açıklama için bkz. [korumalı yapılandırma kullanarak yapılandırma bilgilerini şifreleme](https://docs.microsoft.com/previous-versions/aspnet/53tyfkaw(v=vs.100)).  
  
 Aşağıdaki yapılandırma dosyası parçası, şifrelendikten sonra **ConnectionString** bölümünü gösterir. **ConfigProtectionProvider** , bağlantı dizelerini şifrelemek ve şifresini çözmek için kullanılan korumalı yapılandırma sağlayıcısını belirtir. **EncryptedData** bölümü şifre metnini içerir.  
  
```xml  
<connectionStrings configProtectionProvider="DataProtectionConfigurationProvider">  
  <EncryptedData>  
    <CipherData>  
      <CipherValue>AQAAANCMnd8BFdERjHoAwE/Cl+sBAAAAH2... </CipherValue>  
    </CipherData>  
  </EncryptedData>  
</connectionStrings>  
```  
  
 Şifrelenmiş bağlantı dizesi çalışma zamanında alındığında, .NET Framework **CipherValue** şifresini çözmek ve uygulamanızda kullanılabilir hale getirmek için belirtilen sağlayıcıyı kullanır. Şifre çözme işlemini yönetmek için ek kod yazmanız gerekmez.  
  
### <a name="protected-configuration-providers"></a>Korumalı yapılandırma sağlayıcıları  
 Korumalı yapılandırma sağlayıcıları, ile sağlanan iki korumalı yapılandırma sağlayıcısını gösteren aşağıdaki parçada gösterildiği gibi, yerel bilgisayardaki **Machine. config** dosyasının **configProtectedData** bölümüne kaydedilir. .NET Framework. Burada gösterilen değerler okunabilirlik için kesildi.  
  
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
  
 **Machine. config** dosyasına ekleyerek, ek korumalı yapılandırma sağlayıcıları yapılandırabilirsiniz. <xref:System.Configuration.ProtectedConfigurationProvider> Soyut temel sınıftan devralarak, kendi korumalı yapılandırma sağlayıcınızı de oluşturabilirsiniz. Aşağıdaki tabloda .NET Framework eklenen iki yapılandırma dosyası açıklanmaktadır.  
  
|Sağlayıcı|Açıklama|  
|--------------|-----------------|  
|<xref:System.Configuration.RsaProtectedConfigurationProvider>|, Verileri şifrelemek ve şifrelerini çözmek için RSA şifreleme algoritmasını kullanır. RSA algoritması, hem ortak anahtar şifrelemesi hem de dijital imzalar için kullanılabilir. İki farklı anahtar kullandığından, "ortak anahtar" veya asymmetrik şifreleme olarak da bilinir. Bir Web. config dosyasındaki bölümleri şifrelemek ve şifreleme anahtarlarını yönetmek için [ASP.NET IIS kayıt aracı 'nı (Aspnet_regiis. exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/k6h9cz8h(v=vs.90)) kullanabilirsiniz. ASP.NET, dosyayı işlerken yapılandırma dosyasının şifresini çözer. ASP.NET uygulamasının kimliği, şifrelenmiş bölümleri şifrelemek ve şifresini çözmek için kullanılan şifreleme anahtarına okuma erişimine sahip olmalıdır.|  
|<xref:System.Configuration.DpapiProtectedConfigurationProvider>|Yapılandırma bölümlerini şifrelemek için Windows Data Protection API 'YI (DPAPI) kullanır. Windows yerleşik şifreleme hizmetlerini kullanır ve makineye özgü ya da kullanıcıya özgü koruma için yapılandırılabilir. Makineye özgü koruma, aynı sunucuda bilgi paylaşması gereken birden çok uygulama için yararlıdır. Kullanıcı hesabına özgü koruma, paylaşılan barındırma ortamı gibi belirli bir kullanıcı kimliğiyle çalışan hizmetlerle birlikte kullanılabilir. Her uygulama, dosyalar ve veritabanları gibi kaynaklarla erişimi kısıtlayan ayrı bir kimlik altında çalışır.|  
  
 Her iki sağlayıcı de verilerin güçlü şifrelenmesini sağlar. Ancak, aynı şifrelenmiş yapılandırma dosyasını bir Web grubu gibi birden çok sunucuda kullanmayı planlıyorsanız, yalnızca, <xref:System.Configuration.RsaProtectedConfigurationProvider> verileri şifrelemek ve başka bir sunucuya aktarmak için kullanılan şifreleme anahtarlarını dışarı aktarmanızı sağlar. Daha fazla bilgi için bkz. [korumalı yapılandırma RSA anahtar kapsayıcılarını içeri ve dışarı aktarma](https://docs.microsoft.com/previous-versions/aspnet/yxw286t2(v=vs.100)).  
  
### <a name="using-the-configuration-classes"></a>Yapılandırma sınıflarını kullanma  
 Ad <xref:System.Configuration> alanı, sınıfların yapılandırma ayarları aracılığıyla programlı olarak çalışmasını sağlar. <xref:System.Configuration.ConfigurationManager> Sınıfı, makine, uygulama ve Kullanıcı yapılandırma dosyalarına erişim sağlar. Bir ASP.NET uygulaması oluşturuyorsanız, aynı işlevselliği sağlayan <xref:System.Web.Configuration.WebConfigurationManager> sınıfını kullanarak, **\<System. Web > gibi ASP.NET uygulamalarına özgü ayarlara da erişmenize izin vermiş olursunuz.** .  
  
> [!NOTE]
> Ad <xref:System.Security.Cryptography> alanı, verileri şifrelemek ve şifrelerini çözmek için ek seçenekler sağlayan sınıflar içerir. Korunan yapılandırma kullanılarak kullanılamayan şifreleme hizmetleri istiyorsanız bu sınıfları kullanın. Bu sınıflardan bazıları yönetilmeyen Microsoft CryptoAPI için sarmalayıcılardır, diğerleri ise yalnızca yönetilen uygulamalardır. Daha fazla bilgi için bkz. [Şifreleme Hizmetleri](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/93bskf9z(v=vs.90)).  
  
### <a name="appconfig-example"></a>App. config örneği  
 Bu örnek, bir Windows uygulaması için **app. config** dosyasında **connectionStrings** bölümünün nasıl şifrelendiğini gösterir. Bu örnekte, yordam uygulamanın adını bağımsız değişken olarak alır (örneğin, "MyApplication. exe"). Daha sonra **app. config** dosyası şifrelenir ve "MyApplication. exe. config" adı altındaki yürütülebilir dosyayı içeren klasöre kopyalanacaktır.  
  
> [!NOTE]
> Bağlantı dizesinin şifresi yalnızca şifreli olduğu bilgisayarda çözülür.  
  
 Kod <xref:System.Configuration.ConfigurationManager.OpenExeConfiguration%2A> yöntemi, **düzenlenecek App. config** dosyasını açmak için yöntemini kullanır ve yöntemiConnectionStringbölümünüdöndürür.<xref:System.Configuration.ConfigurationManager.GetSection%2A> Daha sonra kod, şifrelenmemişse bölümü şifrelemek <xref:System.Configuration.SectionInformation.IsProtected%2A> <xref:System.Configuration.SectionInformation.ProtectSection%2A> için öğesini çağırarak özelliği denetler. <xref:System.Configuration.SectionInformation.UnprotectSection%2A> Yöntemi, bölümün şifresini çözmek için çağrılır. <xref:System.Configuration.Configuration.Save%2A> Yöntemi işlemi tamamlar ve değişiklikleri kaydeder.  
  
> [!NOTE]
> Kodun çalışması için projenizde bir başvuru `System.Configuration.dll` ayarlamanız gerekir.  
  
 [!code-csharp[DataWorks ConnectionStrings.Encrypt#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStrings.Encrypt/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStrings.Encrypt#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStrings.Encrypt/VB/source.vb#1)]  
  
### <a name="webconfig-example"></a>Web. config örneği  
 Bu örnek, <xref:System.Web.Configuration.WebConfigurationManager.OpenWebConfiguration%2A> `WebConfigurationManager`yöntemini kullanır. Bu durumda, bir tilde kullanarak **Web. config** dosyasının göreli yolunu sağlayabileceğinizi unutmayın. Kod, `System.Web.Configuration` sınıfa bir başvuru gerektirir.  
  
 [!code-csharp[DataWorks ConnectionStringsWeb.Encrypt#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringsWeb.Encrypt/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringsWeb.Encrypt#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringsWeb.Encrypt/VB/source.vb#1)]  
  
 ASP.NET uygulamalarının güvenliğini sağlama hakkında daha fazla bilgi için bkz. [Web sitelerini güvenli hale getirme](https://docs.microsoft.com/previous-versions/aspnet/91f66yxt(v=vs.100)).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağlantı Dizesi Oluşturucular](../../../../docs/framework/data/adonet/connection-string-builders.md)
- [Bağlantı Bilgilerini Koruma](../../../../docs/framework/data/adonet/protecting-connection-information.md)
- [Yapılandırma sınıflarını kullanma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ms228063(v=vs.90))
- [Uygulamaları Yapılandırma](../../../../docs/framework/configure-apps/index.md)
- [ASP.NET Web sitesi yönetimi](https://docs.microsoft.com/previous-versions/aspnet/6hy1xzbw(v=vs.100))
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
