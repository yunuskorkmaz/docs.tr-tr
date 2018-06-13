---
title: Uygulama Ayarları Mimarisi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application settings [Windows Forms], architecture
ms.assetid: c8eb2ad0-fac6-4ea2-9140-675a4a44d562
ms.openlocfilehash: 769077ddbe42d4d774d359de75417bdca6bcaeb5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520009"
---
# <a name="application-settings-architecture"></a>Uygulama Ayarları Mimarisi
Uygulama ayarları mimarisi nasıl çalıştığını, bu konuda açıklar ve mimarisinin gruplandırılmış ayarları ve ayarları anahtarları gibi gelişmiş özellikler araştırır.  
  
 Uygulama ayarları mimarisi ya da uygulama veya kullanıcı kapsamı ve uygulama oturumları arasında ayarları kalıcı tanımlama kesin türü belirtilmiş ayarlarla destekler. Mimari ayarları kaydetme ve yerel dosya sisteminden yükleme için varsayılan Kalıcılık altyapısı sağlar. Mimari, ayrıca özel Kalıcılık altyapısı sağladığını arabirimleri tanımlar.  
  
 Bir uygulamada barındırıldığında kendi ayarlarını sürdürmek özel bileşenler etkinleştirmek arabirimleri sağlanır. Ayarları tuşlarını kullanarak bileşenleri bileşen birden çok örneğini ayarlarını ayrı kullanmaya devam edebilir.  
  
## <a name="defining-settings"></a>Ayarları tanımlama  
 Uygulama ayarları mimarisi içinde hem de kullanılan [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ve Windows Forms ve onu içeren iki ortamlar genelinde paylaşılan temel sınıfların sayısı. En önemlisi <xref:System.Configuration.SettingsBase>, bir koleksiyonu aracılığıyla ayarlarına erişim sağlar ve yükleme ve ayarları kaydetme için alt düzey yöntemleri sağlar. Her ortam türetilmiş kendi sınıfı uygulayan <xref:System.Configuration.SettingsBase> bu ortam için ek ayarlar işlevselliği sağlamak için. Windows Forms tabanlı bir uygulama, tüm uygulama ayarlarını türetilmiş bir sınıf tanımlanmalıdır <xref:System.Configuration.ApplicationSettingsBase> aşağıdaki işlevselliği için temel sınıf ekler sınıfı:  
  
-   Üst düzey yükleme ve işlemleri kaydetme  
  
-   Kullanıcı kapsamlı ayarları desteği  
  
-   Bir kullanıcının ayarlarını önceden tanımlanmış varsayılanlarına geri alma  
  
-   Önceki bir uygulama sürümünden yükseltme ayarları  
  
-   Ayarlar doğrulanıyor, değiştirilmiş olmaları önce ya da önce kaydedilmeden  
  
 Ayarları içinde tanımlanan öznitelik sayısı kullanılarak tanımlanabilir <xref:System.Configuration> ad alanı; bunlar [uygulama ayarları öznitelikleri](../../../../docs/framework/winforms/advanced/application-settings-attributes.md). Bir ayar tanımladığınızda, onu biriyle uygulamalısınız <xref:System.Configuration.ApplicationScopedSettingAttribute> veya <xref:System.Configuration.UserScopedSettingAttribute>, ayarı tüm uygulama veya yalnızca geçerli kullanıcı için geçerli olup olmadığını açıklar.  
  
 Aşağıdaki kod örneğinde tek bir ayar ile özel ayarları sınıfı tanımlar `BackgroundColor`.  
  
 [!code-csharp[ApplicationSettings.Create#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
 [!code-vb[ApplicationSettings.Create#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]  
  
## <a name="settings-persistence"></a>Ayarları kalıcılığı  
 <xref:System.Configuration.ApplicationSettingsBase> Sınıfı değil kendisini kalıcı ayarlarını yükleyin; veya bu işin ayarları sağlayıcısı, türeyen bir sınıf düşer <xref:System.Configuration.SettingsProvider>. Türetilen bir sınıftan varsa <xref:System.Configuration.ApplicationSettingsBase> ayarları sağlayıcısı üzerinden belirtmiyor <xref:System.Configuration.SettingsProviderAttribute>, ardından varsayılan sağlayıcı <xref:System.Configuration.LocalFileSettingsProvider>, kullanılır.  
  
 İle yayımlanan yapılandırma sistemi [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] statik uygulama yapılandırma verileri yerel bilgisayarın machine.config dosyasının veya içinde sağlayan destekleyen bir `app.`ile dağıttığınız exe.config dosyası Uygulamanızı. <xref:System.Configuration.LocalFileSettingsProvider> Sınıfı aşağıdaki yollarla bu yerel destek genişletir:  
  
-   Uygulama kapsamlı ayarları ya da machine.config içinde depolanabilir veya `app.`exe.config dosyaları. Machine.config her zaman salt okunur sırasında `app`. exe.config çoğu uygulamalar için güvenlik konuları salt okunur tarafından kısıtlanan.  
  
-   Kullanıcı kapsamlı ayarları depolanabilir `app`. exe.config dosyaları, bu durumda statik varsayılan olarak değerlendirilir.  
  
-   Varsayılan dışı kullanıcı kapsamlı ayarları, yeni bir dosyada depolanır *kullanıcı*.config, burada *kullanıcı* uygulama şu anda yürütülmekte olan kişi kullanıcı adıdır. Bir kullanıcı kapsamlı ayarı için varsayılan belirtebilirsiniz <xref:System.Configuration.DefaultSettingValueAttribute>. Kullanıcı kapsamlı ayarları genellikle uygulama yürütmesi sırasında değiştiğinden `user`.config olduğundan her zaman okuma/yazma.  
  
 Tüm üç yapılandırma dosyalarını, XML biçiminde ayarları depolar. Uygulama kapsamlı ayarları için en üst düzey XML öğesi `<appSettings>`, sırada `<userSettings>` kullanıcı kapsamlı ayarları için kullanılır. Bir `app`. kullanıcı kapsamlı ayarları şuna benzer için uygulama kapsamlı ayarları ve Varsayılanları içeren exe.config dosyası:  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
    <configSections>  
        <sectionGroup name="applicationSettings" type="System.Configuration.ApplicationSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" >  
            <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
        </sectionGroup>  
        <sectionGroup name="userSettings" type="System.Configuration.UserSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" >  
            <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" allowExeDefinition="MachineToLocalUser" />  
        </sectionGroup>  
    </configSections>  
    <applicationSettings>  
        <WindowsApplication1.Properties.Settings>  
            <setting name="Cursor" serializeAs="String">  
                <value>Default</value>  
            </setting>  
            <setting name="DoubleBuffering" serializeAs="String">  
                <value>False</value>  
            </setting>  
        </WindowsApplication1.Properties.Settings>  
    </applicationSettings>  
    <userSettings>  
        <WindowsApplication1.Properties.Settings>  
            <setting name="FormTitle" serializeAs="String">  
                <value>Form1</value>  
            </setting>  
            <setting name="FormSize" serializeAs="String">  
                <value>595, 536</value>  
            </setting>  
        </WindowsApplication1.Properties.Settings>  
    </userSettings>  
</configuration>  
```  
  
 Bir yapılandırma dosyası uygulama ayarları bölümünde içindeki öğelerin tanımı için bkz: [uygulama ayarları şeması](../../../../docs/framework/configure-apps/file-schema/application-settings-schema.md).  
  
### <a name="settings-bindings"></a>Ayarları bağlamaları  
 Uygulama ayarları, ayarları güncelleştirme ayarları nesnesi ve bileşenler arasında iki yönlü iletişim sağlamak için Windows Forms veri bağlama mimarisi kullanır. Uygulama ayarları oluşturmak ve bunları bileşeni özellikleri atamak için Visual Studio kullanıyorsanız bu bağlamaların otomatik olarak oluşturulur.  
  
 Yalnızca bir uygulama ayarı destekleyen bir bileşeni bağlayabilirsiniz <xref:System.Windows.Forms.IBindableComponent> arabirimi. Ayrıca, bileşen gerekir belirli bir özellik ilişkin bir değişikliği olay uygulamak veya özelliği aracılığıyla değişti uygulama ayarları bildir <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi. Bileşen uygulamazsa <xref:System.Windows.Forms.IBindableComponent> ve Visual Studio üzerinden bağlama, ilişkili özellikler ilk kez ayarlanır ancak değil güncelleştirir. Bileşen uyguluyorsa <xref:System.Windows.Forms.IBindableComponent> ancak desteği özelliğini bildirimleri değişmez, özelliği değiştirildiğinde bağlama ayarları dosyasında güncelleştirmez.  
  
 Bazı Windows Forms bileşenleri gibi <xref:System.Windows.Forms.ToolStripItem>, ayarları bağlamaları desteklemiyor.  
  
### <a name="settings-serialization"></a>Ayarları seri hale getirme  
 Zaman <xref:System.Configuration.LocalFileSettingsProvider> ayarları diske kaydetmelisiniz aşağıdaki eylemleri gerçekleştirir:  
  
1.  Üzerinde tanımlanan tüm özellikler incelemek için yansıma kullanır, <xref:System.Configuration.ApplicationSettingsBase> türetilmiş sınıf ile ya da uygulanan bu bulma, <xref:System.Configuration.ApplicationScopedSettingAttribute> veya <xref:System.Configuration.UserScopedSettingAttribute>.  
  
2.  Disk özelliğine serileştirir. Önce çağrılacak dener <xref:System.ComponentModel.TypeConverter.ConvertToString%2A> veya <xref:System.ComponentModel.TypeConverter.ConvertFromString%2A> üzerinde türü ilişkili <xref:System.ComponentModel.TypeConverter>. Bu başarılı olmazsa, bunun yerine XML serileştirme kullanır.  
  
3.  Hangi ayarların hangi dosyalarında Git belirler ayarın özniteliğine dayanarak.  
  
 Kendi ayarları sınıfı uygularsanız, kullanabileceğiniz <xref:System.Configuration.SettingsSerializeAsAttribute> ikili veya özel serileştirme kullanmak için bir ayar işaretlemek için <xref:System.Configuration.SettingsSerializeAs> numaralandırması. Kodda, kendi ayarları sınıfı oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: uygulama ayarları oluştur](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md).  
  
### <a name="settings-file-locations"></a>Ayarları dosya konumları  
 Konumunu `app`. exe.config ve *kullanıcı*.config dosyaları farklı dayalı olarak uygulama nasıl yüklenir. Yerel bilgisayara kopyalanır ve Windows Forms tabanlı bir uygulama için `app`. exe.config, uygulamanın ana yürütülebilir dosyası, temel dizini ile aynı dizinde bulunacağı ve *kullanıcı*.config bulunacağı Belirtilen konum <xref:System.Windows.Forms.Application.LocalUserAppDataPath%2A?displayProperty=nameWithType> özelliği. Yoluyla yüklü bir uygulama için [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)], bu dosyaların her ikisini de içinde yer alacağını [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] %InstallRoot%\Documents ve ayarları altında veri dizini\\*kullanıcıadı*\Local ayarlar.  
  
 Bu dosyalar depolama konumunu bir kullanıcının gezici profiller etkinleştirilmişse ve çözemiyorsa diğer bilgisayarlar bir etki alanı içinde kullanırken farklı Windows ve uygulama ayarlarını tanımlamak bir kullanıcı sağlayan biraz farklıdır. Bu durumda, her ikisi de [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] uygulamaları ve olmayan-[!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] uygulamaları olacaktır kendi `app`. exe.config ve *kullanıcı*%InstallRoot%\Documents ve ayarları altında depolanan .config dosyaları\\ *kullanıcıadı*\Application veri.  
  
 Uygulama ayarları özelliğinin yeni dağıtım teknolojisi ile nasıl çalıştığı hakkında daha fazla bilgi için bkz: [ClickOnce ve uygulama ayarlarını](/visualstudio/deployment/clickonce-and-application-settings). Hakkında daha fazla bilgi için [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] veri dizini bkz [erişme yerel ve uzak veri ClickOnce uygulamalarında](/visualstudio/deployment/accessing-local-and-remote-data-in-clickonce-applications).  
  
## <a name="application-settings-and-security"></a>Uygulama ayarları ve güvenlik  
 Uygulama ayarları, kısmi güven, Internet veya intranet üzerinden barındırılan Windows Forms uygulamaları için varsayılan değer kısıtlı bir ortam çalışmak üzere tasarlanmıştır. Kısmi güven ötesinde özel izinler, uygulama ayarları varsayılan ayarları sağlayıcısı ile kullanmak için gereklidir.  
  
 Ne zaman uygulama ayarları kullanıldığı bir [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] uygulama `user`.config dosyası depolanır [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] veri dizini. Uygulamanın boyutunu `user`.config dosyası tarafından belirlenen veri dizini kotasını aşamaz [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)]. Daha fazla bilgi için bkz: [ClickOnce ve uygulama ayarlarını](/visualstudio/deployment/clickonce-and-application-settings).  
  
## <a name="custom-settings-providers"></a>Özel ayarlar sağlayıcıları  
 Uygulama ayarları mimarisinde türetilmiş sarmalayıcı sınıfı uygulamaları ayarları arasında gevşek bağlantı yoktur <xref:System.Configuration.ApplicationSettingsBase>, ve ilgili ayarları sağlayıcı veya sağlayıcıları, türetilen <xref:System.Configuration.SettingsProvider>. Bu ilişkilendirme yalnızca tanımlı <xref:System.Configuration.SettingsProviderAttribute> sarmalayıcı sınıfı veya tek tek özellikleri uygulanır. Sağlayıcısı değil açıkça ayarları belirtilirse, varsayılan sağlayıcı <xref:System.Configuration.LocalFileSettingsProvider>, kullanılır. Sonuç olarak, bu mimarisi oluşturma ve özel ayarları sağlayıcılar kullanarak destekler.  
  
 Örneğin, geliştirme ve kullanmak istediğinizi varsayalım `SqlSettingsProvider`, tüm ayarları verilerini bir Microsoft SQL Server veritabanında depolayacak bir sağlayıcı. <xref:System.Configuration.SettingsProvider>-Türetilmiş sınıf bu bilgileri almak kendi `Initialize` yöntemi türünde bir parametre olarak <xref:System.Collections.Specialized.NameValueCollection?displayProperty=nameWithType>. Ardından uygulamak <xref:System.Configuration.SettingsProvider.GetPropertyValues%2A> ayarlarınızı veri deposundan almak için yöntemini ve <xref:System.Configuration.SettingsProvider.SetPropertyValues%2A> bunları kaydetmek için. Sağlayıcınız kullanabilirsiniz <xref:System.Configuration.SettingsPropertyCollection> için sağlanan <xref:System.Configuration.SettingsProvider.GetPropertyValues%2A> yanı diğer ayarları öznitelikleri özelliğin adını, türünü ve kapsamını belirlemek için bu özellik için tanımlanmış.  
  
 Sağlayıcınız uygulanacağı bir özellik ve uygulamaları belirgin olmayabilir bir yöntem gerekir. <xref:System.Configuration.SettingsProvider.ApplicationName%2A> Özelliği olan bir Özet özelliği <xref:System.Configuration.SettingsProvider>; aşağıdaki dönmek için program:  
  
 [!code-csharp[ApplicationSettings.Architecture#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#2)]
 [!code-vb[ApplicationSettings.Architecture#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#2)]  
  
 Türetilmiş sınıf ayrıca uygulamalıdır bir `Initialize` yöntemi bağımsız değişken almayan gösterir ve herhangi bir değer döndürür. Bu yöntem tarafından tanımlı değil <xref:System.Configuration.SettingsProvider>.  
  
 Son olarak, uygulamanız <xref:System.Configuration.IApplicationSettingsProvider> ayarları yenilemek için desteği sağlamak için sağlayıcınız üzerinde varsayılan ayarlarına geri döndürmeyi ve ayarları bir uygulama sürümünden yükseltme.  
  
 Uygulanan ve sağlayıcınız derlenmiş sonra bu sağlayıcı yerine varsayılan kullanmak üzere ayarları sınıfınız istemeniz gerekir. Bunu aracılığıyla <xref:System.Configuration.SettingsProviderAttribute>. Ayarları sınıfının tümüne uyguladıysanız, sağlayıcı sınıfı tanımlayan her ayar için kullanılır; tek tek ayarlar uygulandığında, uygulama ayarları mimarisi için bu ayarları yalnızca bu sağlayıcıyı kullanır ve kullanan <xref:System.Configuration.LocalFileSettingsProvider> kalan için. Aşağıdaki kod örneğinde, özel sağlayıcınızın kullanılacak ayarları sınıfı istemek üzere gösterilmiştir.  
  
 [!code-csharp[ApplicationSettings.Architecture#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#1)]
 [!code-vb[ApplicationSettings.Architecture#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#1)]  
  
 Bir sağlayıcı birden çok iş parçacığı tarafından eşzamanlı olarak adlandırılmış olabilir, ancak her zaman aynı depolama konumuna yazacak; Bu nedenle, uygulama ayarları mimarisi her zaman sadece bir tek sağlayıcı sınıfının örneği.  
  
> [!IMPORTANT]
>  Sağlayıcınız iş parçacığı güvenlidir ve yalnızca yapılandırma dosyalarını yazmak için bir anda bir iş parçacığı verir olmanız gerekir.  
  
 Sağlayıcınız öznitelikleri tanımlanan tüm ayarlar destek gerekmez <xref:System.Configuration?displayProperty=nameWithType> ad alanı, en az bir destek gerekir ancak <xref:System.Configuration.ApplicationScopedSettingAttribute> ve <xref:System.Configuration.UserScopedSettingAttribute>ve ayrıca desteklemelidir <xref:System.Configuration.DefaultSettingValueAttribute>. Özniteliklerle her zaman desteklemediği sağlayıcınız yalnızca bildirim başarısız olması; bir özel durum oluşturmamalıdır. Ayarları sınıfı öznitelikleri için geçersiz bir birleşim ancak kullanıp kullanmadığını — uygulama gibi <xref:System.Configuration.ApplicationScopedSettingAttribute> ve <xref:System.Configuration.UserScopedSettingAttribute> aynı ayarı — sağlayıcınızı ve bir özel durum işlemi sona.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Configuration.ApplicationSettingsBase>  
 <xref:System.Configuration.SettingsProvider>  
 <xref:System.Configuration.LocalFileSettingsProvider>  
 [Uygulama Ayarlarına Genel Bakış](../../../../docs/framework/winforms/advanced/application-settings-overview.md)  
 [Özel Denetimler için Uygulama Ayarları](../../../../docs/framework/winforms/advanced/application-settings-for-custom-controls.md)  
 [ClickOnce ve Uygulama Ayarları](/visualstudio/deployment/clickonce-and-application-settings)  
 [Uygulama Ayarları Şeması](../../../../docs/framework/configure-apps/file-schema/application-settings-schema.md)
