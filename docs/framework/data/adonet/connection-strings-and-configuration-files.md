---
title: Bağlantı Dizeleri ve Yapılandırma Dosyaları
description: Güvenlik ve bakım için en iyi yöntem olarak, bir uygulama yapılandırma dosyasında ADO.NET uygulamaları için bağlantı dizelerini nasıl depolayacağınızı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 37df2641-661e-407a-a3fb-7bf9540f01e8
ms.openlocfilehash: e2bea3d962998b2778d22e232e7f7062cfda3143
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148418"
---
# <a name="connection-strings-and-configuration-files"></a>Bağlantı Dizeleri ve Yapılandırma Dosyaları

Uygulamanızın koduna bağlantı dizeleri katıştırmak, güvenlik açıklarına ve bakım sorunlarına yol açabilir. Bir uygulamanın kaynak kodunda derlenen şifrelenmemiş bağlantı dizeleri [Ildasm.exe (IL Disassembler)](../../tools/ildasm-exe-il-disassembler.md) Aracı kullanılarak görüntülenebilir. Ayrıca, bağlantı dizesi herhangi bir zaman değişirse uygulamanızın yeniden derlenmesi gerekir. Bu nedenlerden dolayı, bağlantı dizelerini bir uygulama yapılandırma dosyasında depolamanızı öneririz.  
  
## <a name="working-with-application-configuration-files"></a>Uygulama yapılandırma dosyalarıyla çalışma  

 Uygulama yapılandırma dosyaları, belirli bir uygulamaya özgü ayarları içerir. Örneğin, bir ASP.NET uygulamasının bir veya daha fazla **web.config** dosyası olabilir ve bir Windows uygulaması isteğe bağlı bir **app.config** dosyasına sahip olabilir. Yapılandırma dosyaları ortak öğeleri paylaşır, ancak bir yapılandırma dosyasının adı ve konumu uygulamanın ana bilgisayarına bağlı olarak değişir.  
  
### <a name="the-connectionstrings-section"></a>ConnectionStrings bölümü  

 Bağlantı dizeleri, bir uygulama yapılandırma dosyasının **yapılandırma** öğesinin **connectionStrings** bölümünde anahtar/değer çiftleri olarak depolanabilir. Alt öğeler **ekleme**, **Temizleme**ve **kaldırma**içerir.  
  
 Aşağıdaki yapılandırma dosyası parçası, bir bağlantı dizesini depolamak için şemayı ve sözdizimini gösterir. **Ad** özniteliği, bir bağlantı dizesini, çalışma zamanında alınabilmesi için benzersiz şekilde tanımlamak için sağladığınız addır. **ProviderName** , machine.config dosyasında kayıtlı .NET Framework veri sağlayıcısının sabit adıdır.  
  
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
> Bir bağlantı dizesinin bir bölümünü yapılandırma dosyasına kaydedebilir ve <xref:System.Data.Common.DbConnectionStringBuilder> çalışma zamanında bunu gerçekleştirmek için sınıfını kullanabilirsiniz. Bu, bağlantı dizesinin, zaman içinde veya bir yapılandırma dosyasına hassas bilgileri kaydetmek istemediğiniz senaryolarda faydalıdır... Daha fazla bilgi için bkz. [bağlantı dizesi oluşturucuları](connection-string-builders.md).  
  
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
  
 Ana uygulama yapılandırma dosyasında, dış dosyanın tam adını ve konumunu belirtmek için **configSource** özniteliğini kullanırsınız. Bu örnek adlı bir dış yapılandırma dosyası anlamına gelir `connections.config` .  
  
```xml  
<?xml version='1.0' encoding='utf-8'?>  
<configuration>  
    <connectionStrings configSource="connections.config"/>  
</configuration>  
```  
  
## <a name="retrieving-connection-strings-at-run-time"></a>Çalışma zamanında bağlantı dizelerini alma  

 .NET Framework 2,0, <xref:System.Configuration> çalışma zamanında yapılandırma dosyalarından bağlantı dizelerini almayı kolaylaştırmak için ad alanına yeni sınıflar getirmiştir. Bir bağlantı dizesini ada veya sağlayıcı adına göre program aracılığıyla alabilirsiniz.  
  
> [!NOTE]
> **machine.config** dosyası, Visual Studio tarafından kullanılan bağlantı dizelerini Içeren bir **connectionStrings** bölümü de içerir. Bir Windows uygulamasındaki **app.config** dosyasından sağlayıcı adına göre bağlantı dizeleri alınırken, **machine.config** bağlantı dizeleri önce yüklenir, sonra da **app.config**girdileri alınır. **ConnectionString** öğesinden hemen sonra **clear seçeneğinin** eklenmesi, yalnızca yerel **app.config** dosyasında tanımlanan bağlantı dizelerinin kabul edilmesi için bellekteki veri yapısındaki tüm devralınan başvuruları kaldırır.  
  
### <a name="working-with-the-configuration-classes"></a>Yapılandırma sınıflarıyla çalışma  

 .NET Framework 2,0 ' den başlayarak, <xref:System.Configuration.ConfigurationManager> yerel bilgisayardaki yapılandırma dosyalarıyla çalışırken kullanım dışı olarak değiştirilerek kullanılır <xref:System.Configuration.ConfigurationSettings> . <xref:System.Web.Configuration.WebConfigurationManager> , ASP.NET yapılandırma dosyalarıyla çalışmak için kullanılır. Bir Web sunucusunda yapılandırma dosyalarıyla çalışmak üzere tasarlanmıştır ve **System. Web**gibi yapılandırma dosyası bölümlerine programlı erişim sağlar.  
  
> [!NOTE]
> Çalışma zamanında yapılandırma dosyalarına erişilmesi arayan için izin verilmesini gerektirir; gerekli izinler, uygulamanın, yapılandırma dosyasının ve konumun türüne bağlıdır. Daha fazla bilgi için bkz. [yapılandırma sınıflarını](/previous-versions/aspnet/ms228063(v=vs.100)) ve <xref:System.Web.Configuration.WebConfigurationManager> ASP.NET uygulamalarını kullanma ve <xref:System.Configuration.ConfigurationManager> Windows uygulamaları için.  
  
 <xref:System.Configuration.ConnectionStringSettingsCollection>Uygulama yapılandırma dosyalarından bağlantı dizelerini almak için öğesini kullanabilirsiniz. <xref:System.Configuration.ConnectionStringSettings>Her biri **ConnectionString** bölümünde tek bir girişi temsil eden bir nesne koleksiyonu içerir. Özellikleri bağlantı dizesi öznitelikleriyle eşlenir ve ad ya da sağlayıcı adını belirterek bir bağlantı dizesi almanızı sağlar.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Configuration.ConnectionStringSettings.Name%2A>|Bağlantı dizesinin adı. **Ad** özniteliğiyle eşlenir.|  
|<xref:System.Configuration.ConnectionStringSettings.ProviderName%2A>|Tam sağlayıcı adı. **ProviderName** özniteliğiyle eşlenir.|  
|<xref:System.Configuration.ConnectionStringSettings.ConnectionString%2A>|Bağlantı dizesi. **ConnectionString** özniteliğiyle eşlenir.|  
  
### <a name="example-listing-all-connection-strings"></a>Örnek: tüm bağlantı dizelerini listeleme  

 Bu örnek içinde yinelenir <xref:System.Configuration.ConnectionStringSettingsCollection> ve <xref:System.Configuration.ConnectionStringSettings.Name%2A?displayProperty=nameWithType> konsol penceresinde,, <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A?displayProperty=nameWithType> ve <xref:System.Configuration.ConnectionStringSettings.ConnectionString%2A?displayProperty=nameWithType> özelliklerini görüntüler.  
  
> [!NOTE]
> System.Configuration.dll tüm proje türlerine dahil değildir ve yapılandırma sınıflarını kullanabilmeniz için buna bir başvuru ayarlamanız gerekebilir. Belirli bir uygulama yapılandırma dosyasının adı ve konumu, uygulama türüne ve barındırma işlemine göre farklılık gösterir.  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfig#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfig/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfig#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfig/VB/source.vb#1)]  
  
### <a name="example-retrieving-a-connection-string-by-name"></a>Örnek: bir bağlantı dizesini ada göre alma  

 Bu örnek, bir yapılandırma dosyasından adını belirterek bir bağlantı dizesinin nasıl alınacağını gösterir. Kod, <xref:System.Configuration.ConnectionStringSettings> adı verilen giriş parametresiyle eşleşen bir nesne oluşturur <xref:System.Configuration.ConfigurationManager.ConnectionStrings%2A> . Eşleşen ad bulunamazsa, işlev döndürür `null` ( `Nothing` Visual Basic).  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByName#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByName/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByName#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByName/VB/source.vb#1)]  
  
### <a name="example-retrieving-a-connection-string-by-provider-name"></a>Örnek: sağlayıcı adına göre bir bağlantı dizesi alma  

 Bu örnek, *System. Data. ProviderName*biçiminde sağlayıcı-sabit adı belirtilerek bir bağlantı dizesinin nasıl alınacağını gösterir. Kod üzerinden yinelenir <xref:System.Configuration.ConnectionStringSettingsCollection> ve ilk bulunan için bağlantı dizesini döndürür <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> . Sağlayıcı adı bulunamazsa, işlev döndürür `null` ( `Nothing` Visual Basic).  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/VB/source.vb#1)]  
  
## <a name="encrypting-configuration-file-sections-using-protected-configuration"></a>Korumalı yapılandırma kullanarak yapılandırma dosyası bölümlerini şifreleme  

 ASP.NET 2,0, *korunan yapılandırma*adlı, önemli bilgileri bir yapılandırma dosyasında şifrelemenizi sağlayan yeni bir özellik sunmuştur. Birincil olarak ASP.NET için tasarlanmış olsa da, korumalı yapılandırma Windows uygulamalarındaki yapılandırma dosyası bölümlerini şifrelemek için de kullanılabilir. Korunan yapılandırma özelliklerine ilişkin ayrıntılı bir açıklama için bkz. [korumalı yapılandırma kullanarak yapılandırma bilgilerini şifreleme](/previous-versions/aspnet/53tyfkaw(v=vs.100)).  
  
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

 Korumalı yapılandırma sağlayıcıları, .NET Framework birlikte sağlanan iki korumalı yapılandırma sağlayıcısını gösteren aşağıdaki parçada gösterildiği gibi, yerel bilgisayardaki **machine.config** dosyasının **configProtectedData** bölümüne kaydedilir. Burada gösterilen değerler okunabilirlik için kesildi.  
  
```xml  
<configProtectedData defaultProvider="RsaProtectedConfigurationProvider">  
  <providers>  
    <add name="RsaProtectedConfigurationProvider"
      type="System.Configuration.RsaProtectedConfigurationProvider" />  
    <add name="DataProtectionConfigurationProvider"
      type="System.Configuration.DpapiProtectedConfigurationProvider" />  
  </providers>  
</configProtectedData>  
```  
  
 **machine.config** dosyasına ekleyerek, ek korumalı yapılandırma sağlayıcıları yapılandırabilirsiniz. Soyut temel sınıftan devralarak, kendi korumalı yapılandırma sağlayıcınızı de oluşturabilirsiniz <xref:System.Configuration.ProtectedConfigurationProvider> . Aşağıdaki tabloda .NET Framework eklenen iki yapılandırma dosyası açıklanmaktadır.  
  
|Sağlayıcı|Açıklama|  
|--------------|-----------------|  
|<xref:System.Configuration.RsaProtectedConfigurationProvider>|, Verileri şifrelemek ve şifrelerini çözmek için RSA şifreleme algoritmasını kullanır. RSA algoritması, hem ortak anahtar şifrelemesi hem de dijital imzalar için kullanılabilir. İki farklı anahtar kullandığından, "ortak anahtar" veya asymmetrik şifreleme olarak da bilinir. Bir Web.config dosyasındaki bölümleri şifrelemek ve şifreleme anahtarlarını yönetmek için [ASP.NET IIS kayıt aracı 'nı (Aspnet_regiis.exe)](/previous-versions/dotnet/netframework-3.5/k6h9cz8h(v=vs.90)) kullanabilirsiniz. ASP.NET, dosyayı işlerken yapılandırma dosyasının şifresini çözer. ASP.NET uygulamasının kimliği, şifrelenmiş bölümleri şifrelemek ve şifresini çözmek için kullanılan şifreleme anahtarına okuma erişimine sahip olmalıdır.|  
|<xref:System.Configuration.DpapiProtectedConfigurationProvider>|Yapılandırma bölümlerini şifrelemek için Windows Data Protection API 'YI (DPAPI) kullanır. Windows yerleşik şifreleme hizmetlerini kullanır ve makineye özgü ya da kullanıcıya özgü koruma için yapılandırılabilir. Makineye özgü koruma, aynı sunucuda bilgi paylaşması gereken birden çok uygulama için yararlıdır. Kullanıcı hesabına özgü koruma, paylaşılan barındırma ortamı gibi belirli bir kullanıcı kimliğiyle çalışan hizmetlerle birlikte kullanılabilir. Her uygulama, dosyalar ve veritabanları gibi kaynaklarla erişimi kısıtlayan ayrı bir kimlik altında çalışır.|  
  
 Her iki sağlayıcı de verilerin güçlü şifrelenmesini sağlar. Ancak, aynı şifrelenmiş yapılandırma dosyasını bir Web grubu gibi birden çok sunucuda kullanmayı planlıyorsanız, yalnızca, <xref:System.Configuration.RsaProtectedConfigurationProvider> verileri şifrelemek ve başka bir sunucuya aktarmak için kullanılan şifreleme anahtarlarını dışarı aktarmanızı sağlar. Daha fazla bilgi için bkz. [korumalı yapılandırma RSA anahtar kapsayıcılarını içeri ve dışarı aktarma](/previous-versions/aspnet/yxw286t2(v=vs.100)).  
  
### <a name="using-the-configuration-classes"></a>Yapılandırma sınıflarını kullanma  

 <xref:System.Configuration>Ad alanı, sınıfların yapılandırma ayarları aracılığıyla programlı olarak çalışmasını sağlar. <xref:System.Configuration.ConfigurationManager>Sınıfı, makine, uygulama ve Kullanıcı yapılandırma dosyalarına erişim sağlar. Bir ASP.NET uygulaması oluşturuyorsanız, <xref:System.Web.Configuration.WebConfigurationManager> aynı işlevselliği sağlayan sınıfını kullanabilirsiniz. Bu, Ayrıca, ' de bulunan gibi ASP.NET uygulamalarına özgü ayarlara erişmenize izin verir **\<system.web>** .  
  
> [!NOTE]
> <xref:System.Security.Cryptography>Ad alanı, verileri şifrelemek ve şifrelerini çözmek için ek seçenekler sağlayan sınıflar içerir. Korunan yapılandırma kullanılarak kullanılamayan şifreleme hizmetleri istiyorsanız bu sınıfları kullanın. Bu sınıflardan bazıları yönetilmeyen Microsoft CryptoAPI için sarmalayıcılardır, diğerleri ise yalnızca yönetilen uygulamalardır. Daha fazla bilgi için bkz. [Şifreleme Hizmetleri](/previous-versions/visualstudio/visual-studio-2008/93bskf9z(v=vs.90)).  
  
### <a name="appconfig-example"></a>App.config örneği  

 Bu örnek, bir Windows uygulaması için bir **app.config** dosyasındaki **ConnectionString** bölümünün nasıl şifreleyeceğinizi gösterir. Bu örnekte, yordam uygulamanın adını bağımsız değişken olarak alır (örneğin, "MyApplication.exe"). **app.config** dosyası şifrelenir ve "MyApplication.exe.config" adı altında yürütülebilir dosyayı içeren klasöre kopyalanabilir.  
  
> [!NOTE]
> Bağlantı dizesinin şifresi yalnızca şifreli olduğu bilgisayarda çözülür.  
  
 Kod, <xref:System.Configuration.ConfigurationManager.OpenExeConfiguration%2A> öğesini düzenlenmek üzere **app.config** dosyasını açmak için yöntemini kullanır ve <xref:System.Configuration.ConfigurationManager.GetSection%2A> yöntemi **ConnectionString** bölümünü döndürür. Daha sonra kod, <xref:System.Configuration.SectionInformation.IsProtected%2A> <xref:System.Configuration.SectionInformation.ProtectSection%2A> şifrelenmemişse bölümü şifrelemek için öğesini çağırarak özelliği denetler. <xref:System.Configuration.SectionInformation.UnprotectSection%2A>Yöntemi, bölümün şifresini çözmek için çağrılır. <xref:System.Configuration.Configuration.Save%2A>Yöntemi işlemi tamamlar ve değişiklikleri kaydeder.  
  
> [!NOTE]
> `System.Configuration.dll`Kodun çalışması için projenizde bir başvuru ayarlamanız gerekir.  
  
 [!code-csharp[DataWorks ConnectionStrings.Encrypt#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStrings.Encrypt/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStrings.Encrypt#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStrings.Encrypt/VB/source.vb#1)]  
  
### <a name="webconfig-example"></a>Web.config örneği  

 Bu örnek <xref:System.Web.Configuration.WebConfigurationManager.OpenWebConfiguration%2A> , yöntemini kullanır `WebConfigurationManager` . Bu durumda, **Web.config** dosyasına göreli yolu bir tilde kullanarak sağlayabileceğinizi unutmayın. Kod, sınıfa bir başvuru gerektirir `System.Web.Configuration` .  
  
 [!code-csharp[DataWorks ConnectionStringsWeb.Encrypt#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringsWeb.Encrypt/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringsWeb.Encrypt#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringsWeb.Encrypt/VB/source.vb#1)]  
  
 ASP.NET uygulamalarının güvenliğini sağlama hakkında daha fazla bilgi için bkz. [Web sitelerini güvenli hale getirme](/previous-versions/aspnet/91f66yxt(v=vs.100)).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağlantı Dizesi Oluşturucular](connection-string-builders.md)
- [Bağlantı Bilgilerini Koruma](protecting-connection-information.md)
- [Yapılandırma sınıflarını kullanma](/previous-versions/visualstudio/visual-studio-2008/ms228063(v=vs.90))
- [Uygulamaları Yapılandırma](../../configure-apps/index.md)
- [ASP.NET Web sitesi yönetimi](/previous-versions/aspnet/6hy1xzbw(v=vs.100))
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
