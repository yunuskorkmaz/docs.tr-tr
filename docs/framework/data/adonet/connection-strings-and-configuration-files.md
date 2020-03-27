---
title: Bağlantı Dizeleri ve Yapılandırma Dosyaları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 37df2641-661e-407a-a3fb-7bf9540f01e8
ms.openlocfilehash: 8862aa34c2d2677f5bc3e737c01cc61036c243e1
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345055"
---
# <a name="connection-strings-and-configuration-files"></a>Bağlantı Dizeleri ve Yapılandırma Dosyaları

Bağlantı dizelerini uygulamanızın koduna yerleştirmek güvenlik açıklarına ve bakım sorunlarına neden olabilir. Bir uygulamanın kaynak kodunda derlenen şifrelenmemiş bağlantı dizeleri [Ildasm.exe (IL Desassembler)](../../tools/ildasm-exe-il-disassembler.md) aracı kullanılarak görüntülenebilir. Ayrıca, bağlantı dizesi hiç değişirse, uygulamanızın yeniden derlenmiş olması gerekir. Bu nedenlerden dolayı, bağlantı dizelerini bir uygulama yapılandırma dosyasında depolamanızı öneririz.  
  
## <a name="working-with-application-configuration-files"></a>Uygulama Yapılandırma Dosyalarıyla Çalışma  
 Uygulama yapılandırma dosyaları belirli bir uygulamaya özgü ayarlar içerir. Örneğin, bir ASP.NET uygulaması nda bir veya daha fazla **web.config** dosyası olabilir ve windows uygulaması isteğe bağlı bir **app.config** dosyasına sahip olabilir. Yapılandırma dosyasının adı ve konumu uygulamanın ana bilgisayarına bağlı olarak değişse de yapılandırma dosyaları ortak öğeleri paylaşır.  
  
### <a name="the-connectionstrings-section"></a>ConnectionStrings Bölümü  
 Bağlantı dizeleri, bir uygulama yapılandırma dosyasının **yapılandırma** öğesinin **bağlantıDizelleri** bölümünde anahtar/değer çiftleri olarak depolanabilir. Alt öğeler **ekle,** **temizleyin**ve **kaldırın.**  
  
 Aşağıdaki yapılandırma dosyası parçası, bağlantı dizesini depolamak için şema ve sözdizimini gösterir. **Ad** özniteliği, bir bağlantı dizesini çalışma zamanında alınabilmesi için benzersiz olarak tanımlamak için sağladığınız bir addır. **ProviderName,** machine.config dosyasında kayıtlı olan .NET Framework veri sağlayıcısının değişmez adıdır.  
  
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
> Bir bağlantı dizesinin bir kısmını yapılandırma dosyasına kaydedebilir ve çalışma zamanında tamamlamak için <xref:System.Data.Common.DbConnectionStringBuilder> sınıfı kullanabilirsiniz. Bu, bağlantı dizesinin öğelerini önceden bilmediğiniz veya hassas bilgileri yapılandırma dosyasına kaydetmek istemediğiniz senaryolarda yararlıdır. Daha fazla bilgi için [Bağlantı Dize Oluşturucuları'na](connection-string-builders.md)bakın.  
  
### <a name="using-external-configuration-files"></a>Dış Yapılandırma Dosyalarını Kullanma  
 Dış yapılandırma dosyaları, tek bir bölümden oluşan bir yapılandırma dosyasının bir parçasını içeren ayrı dosyalardır. Dış yapılandırma dosyası daha sonra ana yapılandırma dosyası tarafından başvurur. **BağlantıStrings** bölümünü fiziksel olarak ayrı bir dosyada depolamak, uygulama dağıtıldıktan sonra bağlantı dizeleri düzenlenebileceği durumlarda yararlıdır. Örneğin, standart ASP.NET davranışı, yapılandırma dosyaları değiştirildiğinde bir uygulama etki alanını yeniden başlatmaktır ve bu da durum bilgilerinin kaybolmasına neden olmaktadır. Ancak, harici bir yapılandırma dosyanın değiştirilmesi bir uygulamayeniden başlatmaya neden olmaz. Dış yapılandırma dosyaları ASP.NET ile sınırlı değildir; Windows uygulamaları tarafından da kullanılabilir. Ayrıca, dosya erişim güvenliği ve izinler harici yapılandırma dosyalarına erişimi kısıtlamak için kullanılabilir. Çalışma zamanında harici yapılandırma dosyalarıyla çalışmak saydamdır ve özel kodlama gerektirmez.  
  
 Bağlantı dizelerini harici bir yapılandırma dosyasında depolamak için yalnızca **bağlantıStrings** bölümünü içeren ayrı bir dosya oluşturun. Ek öğeler, bölümler veya öznitelikler eklemeyin. Bu örnek, harici bir yapılandırma dosyası için sözdizimini gösterir.  
  
```xml  
<connectionStrings>  
  <add name="Name"
   providerName="System.Data.ProviderName"
   connectionString="Valid Connection String;" />  
</connectionStrings>  
```  
  
 Ana uygulama yapılandırma dosyasında, dış dosyanın tam nitelikli adını ve konumunu belirtmek için **configSource** özniteliğini kullanırsınız. Bu örnek, adlı `connections.config`harici bir yapılandırma dosyası anlamına gelir.  
  
```xml  
<?xml version='1.0' encoding='utf-8'?>  
<configuration>  
    <connectionStrings configSource="connections.config"/>  
</configuration>  
```  
  
## <a name="retrieving-connection-strings-at-run-time"></a>Çalışma Zamanında Bağlantı Dizeleri Alma  
 .NET Framework 2.0, çalışma zamanında <xref:System.Configuration> yapılandırma dosyalarından bağlantı dizelerini almamayı kolaylaştırmak için ad alanında yeni sınıflar tanıttı. Bir bağlantı dizelerini ad veya sağlayıcı adına göre programlı olarak alabilirsiniz.  
  
> [!NOTE]
> **Machine.config** dosyası ayrıca Visual Studio tarafından kullanılan bağlantı dizeleri içeren bir **connectionStrings** bölümü içerir. Bir Windows uygulamasında **app.config** dosyasından sağlayıcı adına göre bağlantı dizeleri alırken, **machine.config'deki** bağlantı dizeleri önce yüklenir, ardından **app.config'den**girişler yüklenir. **ConnectionStrings** öğesi bellekteki veri yapısından tüm devralınan başvuruları kaldırır, böylece yalnızca yerel **app.config** dosyasında tanımlanan bağlantı dizeleri dikkate alınır sonra **net** ekleme.  
  
### <a name="working-with-the-configuration-classes"></a>Yapılandırma Sınıfları ile çalışma  
 .NET Framework 2.0 ile <xref:System.Configuration.ConfigurationManager> başlayarak, yerel bilgisayardaki yapılandırma dosyalarıyla çalışırken, amortismana alınanın <xref:System.Configuration.ConfigurationSettings>yerine kullanılır. <xref:System.Web.Configuration.WebConfigurationManager>yapılandırma dosyaları yla çalışmak için ASP.NET kullanılır. Bir Web sunucusundaki yapılandırma dosyalarıyla çalışmak üzere tasarlanmıştır ve **system.web**gibi yapılandırma dosyası bölümlerine programlı erişim sağlar.  
  
> [!NOTE]
> Yapılandırma dosyalarına çalışma zamanında erişmek için arayanın izni verilmesi; gerekli izinler uygulama türüne, yapılandırma dosyasına ve konuma bağlıdır. Daha fazla bilgi için yapılandırma <xref:System.Web.Configuration.WebConfigurationManager> [sınıflarını kullanma,](https://docs.microsoft.com/previous-versions/aspnet/ms228063(v=vs.100)) <xref:System.Configuration.ConfigurationManager> ASP.NET uygulamaları ve Windows uygulamaları için bkz.  
  
 Uygulama yapılandırma <xref:System.Configuration.ConnectionStringSettingsCollection> dosyalarından bağlantı dizeleri almak için kullanabilirsiniz. Her biri <xref:System.Configuration.ConnectionStringSettings> **connectionStrings** bölümünde tek bir girişi temsil eden bir nesne koleksiyonu içerir. Özellikleri bağlantı dizeözleri eşleyerek, adı veya sağlayıcı adını belirterek bir bağlantı dizesini almanıza olanak sağlar.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Configuration.ConnectionStringSettings.Name%2A>|Bağlantı dizesinin adı. **Ad** özniteliğine eşler.|  
|<xref:System.Configuration.ConnectionStringSettings.ProviderName%2A>|Tam nitelikli sağlayıcı adı. **SağlayıcıAd** özniteliğine eşler.|  
|<xref:System.Configuration.ConnectionStringSettings.ConnectionString%2A>|Bağlantı dizesi. **Bağlantıya eşlerString** özniteliği.|  
  
### <a name="example-listing-all-connection-strings"></a>Örnek: Tüm Bağlantı Dizeleri Listeleme  
 Bu <xref:System.Configuration.ConnectionStringSettingsCollection> örnek, konsol <xref:System.Configuration.ConnectionStringSettings.Name%2A?displayProperty=nameWithType>penceresindeki , <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A?displayProperty=nameWithType>ve <xref:System.Configuration.ConnectionStringSettings.ConnectionString%2A?displayProperty=nameWithType> özellikleri görüntüler.  
  
> [!NOTE]
> System.Configuration.dll tüm proje türlerine dahil değildir ve yapılandırma sınıflarını kullanmak için buna bir başvuru ayarlamanız gerekebilir. Belirli bir uygulama yapılandırma dosyasının adı ve konumu uygulama türüne ve barındırma işlemine göre değişir.  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfig#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfig/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfig#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfig/VB/source.vb#1)]  
  
### <a name="example-retrieving-a-connection-string-by-name"></a>Örnek: Bir Bağlantı Dizesini Ada Göre Alma  
 Bu örnek, adını belirterek bir yapılandırma dosyasından bağlantı dizesi nasıl alındığını gösterir. Kod, sağlanan <xref:System.Configuration.ConnectionStringSettings> giriş parametresini <xref:System.Configuration.ConfigurationManager.ConnectionStrings%2A> ada eşleştirecek bir nesne oluşturur. Eşleşen bir ad bulunamazsa, `null` `Nothing` işlev döndürür (Visual Basic'te).  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByName#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByName/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByName#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByName/VB/source.vb#1)]  
  
### <a name="example-retrieving-a-connection-string-by-provider-name"></a>Örnek: Sağlayıcı Adına Göre Bağlantı Dizesi Alma  
 Bu örnek, *System.Data.ProviderName*biçiminde sağlayıcı değişmez adını belirterek bir bağlantı dizesi nasıl alındığını gösterir. Kod, ilk <xref:System.Configuration.ConnectionStringSettingsCollection> <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> bulunanın bağlantı dizesini yineler ve döndürür. Sağlayıcı adı bulunamazsa, işlev `null` (Visual`Nothing` Basic'te) döndürür.  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/VB/source.vb#1)]  
  
## <a name="encrypting-configuration-file-sections-using-protected-configuration"></a>Korumalı Yapılandırmayı Kullanarak Yapılandırma Dosya Bölümlerini Şifreleme  
 ASP.NET 2.0, bir yapılandırma dosyasında hassas bilgileri şifrelemenize olanak tanıyan *korumalı yapılandırma*adı verilen yeni bir özellik sundu. Öncelikle ASP.NET için tasarlanmış olsa da, windows uygulamalarında yapılandırma dosya bölümlerini şifrelemek için korumalı yapılandırma da kullanılabilir. Korumalı yapılandırma özelliklerinin ayrıntılı açıklaması için, [Korumalı Yapılandırmayı Kullanarak Yapılandırma Bilgilerini Şifreleme](https://docs.microsoft.com/previous-versions/aspnet/53tyfkaw(v=vs.100))bölümüne bakın.  
  
 Aşağıdaki yapılandırma dosyası parçası şifrelendikten sonra **connectionStrings** bölümünü gösterir. **ConfigProtectionProvider,** bağlantı dizelerini şifrelemek ve çözmek için kullanılan korumalı yapılandırma sağlayıcısını belirtir. **EncryptedData** bölümünde şifre metni içerir.  
  
```xml  
<connectionStrings configProtectionProvider="DataProtectionConfigurationProvider">  
  <EncryptedData>  
    <CipherData>  
      <CipherValue>AQAAANCMnd8BFdERjHoAwE/Cl+sBAAAAH2... </CipherValue>  
    </CipherData>  
  </EncryptedData>  
</connectionStrings>  
```  
  
 Şifreli bağlantı dizesi çalışma zamanında alındığı zaman, .NET **Framework, CipherValue'nin** şifresini çözmek ve uygulamanız için kullanılabilir hale getirmek için belirtilen sağlayıcıyı kullanır. Şifre çözme işlemini yönetmek için ek kod yazmanız gerekmez.  
  
### <a name="protected-configuration-providers"></a>Korumalı Yapılandırma Sağlayıcıları  
 Korumalı yapılandırma sağlayıcıları, .NET Framework ile birlikte verilen iki korumalı yapılandırma sağlayıcısını gösteren aşağıdaki parçada gösterildiği gibi, **machine.config** dosyasının yerel bilgisayardaki **configProtectedData** bölümüne kaydedilir. Burada gösterilen değerler okunabilirlik için kesildi.  
  
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
  
 **Machine.config** dosyasına ekleyerek ek korumalı yapılandırma sağlayıcıları yapılandırabilirsiniz. <xref:System.Configuration.ProtectedConfigurationProvider> Ayrıca soyut taban sınıftan devralarak kendi korumalı yapılandırma sağlayıcınızı da oluşturabilirsiniz. Aşağıdaki tabloda .NET Framework ile birlikte iki yapılandırma dosyası açıklanmaktadır.  
  
|Sağlayıcı|Açıklama|  
|--------------|-----------------|  
|<xref:System.Configuration.RsaProtectedConfigurationProvider>|Verileri şifrelemek ve çözmek için RSA şifreleme algoritmasını kullanır. RSA algoritması hem ortak anahtar şifrelemesi hem de dijital imzalar için kullanılabilir. İki farklı anahtar kullandığından "ortak anahtar" veya asimetrik şifreleme olarak da bilinir. Bir Web.config dosyasındaki bölümleri şifrelemek ve şifreleme anahtarlarını yönetmek için [ASP.NET IIS Kayıt Aracı'nı (Aspnet_regiis.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/k6h9cz8h(v=vs.90)) kullanabilirsiniz. ASP.NET, dosyayı işlerken yapılandırma dosyasının şifresini çözer. ASP.NET uygulamasının kimliği, şifrelenmiş bölümleri şifrelemek ve şifresini çözmek için kullanılan şifreleme anahtarına okuma erişimine sahip olmalıdır.|  
|<xref:System.Configuration.DpapiProtectedConfigurationProvider>|Yapılandırma bölümlerini şifrelemek için Windows Veri Koruma API'sını (DPAPI) kullanır. Windows yerleşik şifreleme hizmetlerini kullanır ve makineye özgü veya kullanıcı hesabına özgü koruma için yapılandırılabilir. Makineye özgü koruma, aynı sunucuda bilgi paylaşması gereken birden çok uygulama için yararlıdır. Kullanıcı hesabına özgü koruma, paylaşılan barındırma ortamı gibi belirli bir kullanıcı kimliğiyle çalışan hizmetlerle kullanılabilir. Her uygulama, dosyalar ve veritabanları gibi kaynaklara erişimi kısıtlayan ayrı bir kimlik altında çalışır.|  
  
 Her iki sağlayıcı da güçlü veri şifrelemesi sunar. Ancak, web çiftliği gibi birden çok sunucuda aynı şifreli yapılandırma dosyasını kullanmayı <xref:System.Configuration.RsaProtectedConfigurationProvider> planlıyorsanız, yalnızca verileri şifrelemek ve bunları başka bir sunucuda aktarmak için kullanılan şifreleme anahtarlarını dışa aktarmaolanağı sağlar. Daha fazla bilgi için [bkz.](https://docs.microsoft.com/previous-versions/aspnet/yxw286t2(v=vs.100))  
  
### <a name="using-the-configuration-classes"></a>Yapılandırma Sınıflarını Kullanma  
 Ad <xref:System.Configuration> alanı, sınıfların yapılandırma ayarlarıyla programlı olarak çalışmasını sağlar. Sınıf <xref:System.Configuration.ConfigurationManager> makine, uygulama ve kullanıcı yapılandırma dosyalarına erişim sağlar. ASP.NET bir uygulama oluşturuyorsanız, aynı <xref:System.Web.Configuration.WebConfigurationManager> işlevselliği sağlayan sınıfı kullanabilirsiniz ve aynı zamanda ** \<system.web>'da **bulunanlar gibi ASP.NET uygulamalara özgü ayarlara erişmenizi de sağlayabilirsiniz.  
  
> [!NOTE]
> Ad <xref:System.Security.Cryptography> alanı, verileri şifrelemek ve çözmek için ek seçenekler sağlayan sınıflar içerir. Korumalı yapılandırma yı kullanarak kullanılamayan şifreleme hizmetlerine ihtiyaç duyuyorsanız bu sınıfları kullanın. Bu sınıflardan bazıları yönetilmeyen Microsoft CryptoAPI için paketleyiciler, diğerleri ise tamamen yönetilen uygulamalardır. Daha fazla bilgi için [Cryptographic Services'a](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/93bskf9z(v=vs.90))bakın.  
  
### <a name="appconfig-example"></a>App.config Örneği  
 Bu örnek, bir Windows uygulaması için **app.config** dosyasında **connectionStrings** bölümünün şifrelenmeyi nasıl gösterin. Bu örnekte, yordam, uygulamanın adını bir bağımsız değişken olarak alır, örneğin, "MyApplication.exe". **App.config** dosyası daha sonra şifrelenecek ve "MyApplication.exe.config" adı altında yürütülebilir içeren klasöre kopyalanır.  
  
> [!NOTE]
> Bağlantı dizesi yalnızca şifrelendiği bilgisayarda deşifre edilebilir.  
  
 Kod düzenleme <xref:System.Configuration.ConfigurationManager.OpenExeConfiguration%2A> için **app.config** dosyasını açmak için <xref:System.Configuration.ConfigurationManager.GetSection%2A> yöntemi kullanır ve yöntem **connectionStrings** bölümünü döndürür. Kod daha sonra <xref:System.Configuration.SectionInformation.IsProtected%2A> özelliği denetler ve şifrelenmemişse bölümü <xref:System.Configuration.SectionInformation.ProtectSection%2A> şifrelemek için çağırır. Yöntem, <xref:System.Configuration.SectionInformation.UnprotectSection%2A> bölümün şifresini çözmek için çağrılır. Yöntem <xref:System.Configuration.Configuration.Save%2A> işlemi tamamlar ve değişiklikleri kaydeder.  
  
> [!NOTE]
> Kodun çalışması için `System.Configuration.dll` projenizde bir başvuru ayarlamanız gerekir.  
  
 [!code-csharp[DataWorks ConnectionStrings.Encrypt#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStrings.Encrypt/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStrings.Encrypt#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStrings.Encrypt/VB/source.vb#1)]  
  
### <a name="webconfig-example"></a>Web.config Örneği  
 Bu örnekte <xref:System.Web.Configuration.WebConfigurationManager.OpenWebConfiguration%2A> `WebConfigurationManager`. Bu durumda, bir tilde kullanarak **Web.config** dosyasına göreli yolu sağlayabilirsiniz. Kod `System.Web.Configuration` sınıfa bir başvuru gerektirir.  
  
 [!code-csharp[DataWorks ConnectionStringsWeb.Encrypt#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringsWeb.Encrypt/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringsWeb.Encrypt#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringsWeb.Encrypt/VB/source.vb#1)]  
  
 ASP.NET uygulamalarının güvenliğini sağlama hakkında daha fazla bilgi [ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/91f66yxt(v=vs.100))için bkz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağlantı Dizesi Oluşturucular](connection-string-builders.md)
- [Bağlantı Bilgilerini Koruma](protecting-connection-information.md)
- [Yapılandırma Sınıflarını Kullanma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ms228063(v=vs.90))
- [Uygulamaları Yapılandırma](../../configure-apps/index.md)
- [ASP.NET Web Sitesi Yönetimi](https://docs.microsoft.com/previous-versions/aspnet/6hy1xzbw(v=vs.100))
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
