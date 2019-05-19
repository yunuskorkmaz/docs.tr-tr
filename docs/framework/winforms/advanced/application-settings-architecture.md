---
title: Uygulama Ayarları Mimarisi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application settings [Windows Forms], architecture
ms.assetid: c8eb2ad0-fac6-4ea2-9140-675a4a44d562
ms.openlocfilehash: a049bbe22d29f02acbc7889bb5d5010ec44f9d15
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65876217"
---
# <a name="application-settings-architecture"></a>Uygulama Ayarları Mimarisi
Bu konuda, uygulama ayarları mimarisi nasıl çalıştığını açıklanır ve mimarinin gruplandırılmış ayarları ve ayarları anahtarları gibi gelişmiş özellikleri keşfediyor.  
  
 Uygulama ayarları mimarisi ya da uygulama veya kullanıcı kapsamı ve ayarları uygulama oturumları arasında kalıcı tanımlama türü kesin belirlenmiş ayarlarla destekler. Mimari ayarları için kaydetme ve bunları yerel dosya sisteminden yükleme için varsayılan Kalıcılık altyapısı sağlar. Mimari ayrıca özel bir Kalıcılık altyapısı sağladığı için arabirimleri tanımlar.  
  
 Bir uygulamada barındırıldığında kendi ayarlarını kalıcı hale getirmek özel bileşenler sağlayan arabirimler sağlanır. Ayarları anahtarları kullanarak bileşenleri bileşenin birden çok örnek için ayarları ayrı kalmasını sağlayabilirsiniz.  
  
## <a name="defining-settings"></a>Ayarları tanımlama  
 Uygulama ayarları mimarisi, hem ASP.NET hem de Windows Formları içinde kullanılır ve her iki ortamlar genelinde paylaşılan, temel sınıfların bir sayı içerir. En önemlisi <xref:System.Configuration.SettingsBase>, koleksiyonu aracılığıyla ayarlarına erişim sağlar ve yükleme ve kaydetme ayarları için alt düzey yöntemler sağlar. Her ortamın kendi sınıfından türetilen uygulayan <xref:System.Configuration.SettingsBase> bu ortam için ek ayarlar işlevselliği sağlamak için. Windows Forms tabanlı bir uygulama, tüm uygulama ayarları türetilen bir sınıfta tanımlanmalıdır <xref:System.Configuration.ApplicationSettingsBase> temel sınıf için aşağıdaki işlevsellik ekleyen sınıfı:  
  
- Üst düzey yükleme ve kaydetme işlemleri  
  
- Kullanıcı kapsamlı ayarları için destek  
  
- Kullanıcı ayarları için önceden tanımlanmış varsayılan döndürülüyor  
  
- Uygulamanın önceki sürümden yükseltme ayarları  
  
- Ayarlar doğrulanıyor, bunlar değiştirilmeden önce ya da önce kaydedilmeden  
  
 Bir dizi içinde tanımlanan öznitelikleri kullanarak ayarları açıklanabilir <xref:System.Configuration> ad alanı; bunlar [uygulama ayarları öznitelikleri](application-settings-attributes.md). Bir ayar tanımlarken ile uygulamanız gerekir <xref:System.Configuration.ApplicationScopedSettingAttribute> veya <xref:System.Configuration.UserScopedSettingAttribute>, ayarı uygulamanın tamamı veya yalnızca geçerli kullanıcı için geçerli olup olmadığını açıklar.  
  
 Aşağıdaki kod örneği özel ayarlar ile tek bir ayarı tanımlar `BackgroundColor`.  
  
 [!code-csharp[ApplicationSettings.Create#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
 [!code-vb[ApplicationSettings.Create#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]  
  
## <a name="settings-persistence"></a>Kalıcılık ayarları  
 <xref:System.Configuration.ApplicationSettingsBase> Sınıfı değil kendisine kalıcı veya yük ayarları; bu iş öğesinden türetilen bir sınıf ayar sağlayıcısı düşer <xref:System.Configuration.SettingsProvider>. Türetilen bir sınıfı varsa <xref:System.Configuration.ApplicationSettingsBase> aracılığıyla bir ayar sağlayıcısı belirtmiyor <xref:System.Configuration.SettingsProviderAttribute>, ardından varsayılan sağlayıcı <xref:System.Configuration.LocalFileSettingsProvider>, kullanılır.  
  
 .NET Framework ile yayımlanan yapılandırma sistemi destekler yerel bilgisayarın machine.config dosyasının veya içinde statik uygulama yapılandırma verileri sağlayan bir `app.`ile dağıttığınız exe.config dosyası Uygulamanızı. <xref:System.Configuration.LocalFileSettingsProvider> Sınıfı bu yerel destek aşağıdaki yollarla genişletir:  
  
- Uygulama kapsamlı ayarlar ya da bir machine.config dosyasına depolanabilir veya `app.`exe.config dosyaları. Machine.config her zaman salt okunur, çalışırken `app`. exe.config uygulamalarının çoğu için güvenlik konuları salt okunur tarafından kısıtlanan.  
  
- Kullanıcı kapsamlı ayarları depolanabilir `app`. exe.config dosyaları, bu durumda bunlar statik varsayılan olarak kabul edilir.  
  
- Varsayılan olmayan kullanıcı kapsamlı ayarları yeni bir dosyada depolanan *kullanıcı*.config, burada *kullanıcı* uygulama şu anda yürüten kişinin kullanıcı adıdır. Bir kullanıcı kapsamlı ayarı için varsayılan belirtebilirsiniz <xref:System.Configuration.DefaultSettingValueAttribute>. Kullanıcı kapsamlı ayarları uygulama yürütme sırasında sıklıkla değiştiğinden `user`.config olduğundan her zaman okuma/yazma.  
  
 Tüm üç yapılandırma dosyaları XML biçiminde ayarları depolar. Uygulama kapsamlı ayarlar için üst düzey XML öğesi `<appSettings>`, ancak `<userSettings>` kullanıcı kapsamlı ayarları için kullanılır. Bir `app`. exe.config dosyasını kullanıcı kapsamlı ayarları şuna benzer için hem uygulama kapsamlı ayarlar ve varsayılanlar içerir:  
  
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
  
 Bir yapılandırma dosyası uygulama ayarları bölümüne içindeki öğelerin tanımı için bkz: [uygulama ayarları şeması](../../configure-apps/file-schema/application-settings-schema.md).  
  
### <a name="settings-bindings"></a>Ayarları bağlamaları  
 Uygulama ayarları, ayarları güncelleştirme ayarları nesnesi ve bileşenler arasında iki yönlü iletişim sağlamak için Windows Forms veri bağlama mimarisi kullanır. Uygulama ayarları oluşturma ve bunları bileşen özellikleri atamak için Visual Studio kullanıyorsanız, bu bağlamaları otomatik olarak oluşturulur.  
  
 Destekleyen bir bileşeni için yalnızca bir uygulama ayarı bağlayabilirsiniz <xref:System.Windows.Forms.IBindableComponent> arabirimi. Ayrıca, bileşen gerekir değişiklik olayı için belirli bir özelliğe uygulamak veya bildirim aracılığıyla özelliğin değiştirildiğini uygulama ayarları <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi. Bileşen uygulamazsa <xref:System.Windows.Forms.IBindableComponent> ve Visual Studio ile bağlıyorsanız, ilişkili özellikleri ilk kez ayarlanır, ancak değil güncelleştirir. Bileşen uyguluyorsa <xref:System.Windows.Forms.IBindableComponent> ancak desteği özelliğini bildirimleri değişiyor mu, özelliği değiştirildiğinde bağlama ayarları dosyasında güncelleştirmez.  
  
 Bazı Windows Forms bileşenleri gibi <xref:System.Windows.Forms.ToolStripItem>, ayarları bağlamaları desteklemiyor.  
  
### <a name="settings-serialization"></a>Ayarları seri hale getirme  
 Zaman <xref:System.Configuration.LocalFileSettingsProvider> ayarları diske kaydetmelisiniz aşağıdaki eylemleri gerçekleştirir:  
  
1. Tanımlanan tüm özellikler incelemek için yansıtma kullanır, <xref:System.Configuration.ApplicationSettingsBase> türetilmiş sınıf ile uygulanan bu bulma, <xref:System.Configuration.ApplicationScopedSettingAttribute> veya <xref:System.Configuration.UserScopedSettingAttribute>.  
  
2. Disk özelliğine serileştirir. Çağırmak ilk deneme <xref:System.ComponentModel.TypeConverter.ConvertToString%2A> veya <xref:System.ComponentModel.TypeConverter.ConvertFromString%2A> üzerinde türü ilişkili <xref:System.ComponentModel.TypeConverter>. Bu başarısız olursa, bunun yerine XML serileştirme kullanır.  
  
3. Hangi dosyaların ayarlarınız belirler ayarın özniteliğine dayanarak.  
  
 Kendi ayarları sınıfı uygularsanız, kullanabileceğiniz <xref:System.Configuration.SettingsSerializeAsAttribute> ikili veya özel serileştirme kullanmak için bir ayar işaretlemek için <xref:System.Configuration.SettingsSerializeAs> sabit listesi. Kodda kendi ayarları sınıfı oluşturma ile ilgili daha fazla bilgi için bkz: [nasıl yapılır: Uygulama ayarları oluşturma](how-to-create-application-settings.md).  
  
### <a name="settings-file-locations"></a>Ayarlar dosyası konumları  
 Konumunu `app`. exe.config ve *kullanıcı*.config dosyalar farklı bağlı olarak uygulama nasıl yüklenir. Yerel bilgisayara kopyalanır ve Windows Forms tabanlı bir uygulama için `app`. exe.config olarak, uygulamanın ana yürütülebilir dosyasını temel dizini ile aynı dizinde bulunacağı ve *kullanıcı*.config bulunacağı tarafından belirtilen konuma <xref:System.Windows.Forms.Application.LocalUserAppDataPath%2A?displayProperty=nameWithType> özelliği. Yoluyla yüklü bir uygulama için [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)], bu dosyaların her ikisini de yer alacağı [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] veri dizini %InstallRoot%\Documents ve ayarlar altındaki\\*kullanıcıadı*\Local ayarları.  
  
 Bu dosyalar depolama konumu, bir kullanıcının gezici profiller etkinleştirilmişse ve isterse diğer bilgisayarlar bir etki alanı içinde kullanıldığında farklı Windows ve uygulama ayarlarını tanımlamak bir kullanıcı sağlayan biraz farklıdır. Bu durumda, her ikisi de [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] uygulamaları ve olmayan-[!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] sahip olacak uygulamaları kendi `app`. exe.config ve *kullanıcı*%InstallRoot%\Documents ve ayarları altında depolanan .config dosyaları\\ *kullanıcıadı*\Application veri.  
  
 Yeni dağıtım teknolojisi ile uygulama ayarlarını özelliğinin işleyişi hakkında daha fazla bilgi için bkz. [ClickOnce ve uygulama ayarlarını](/visualstudio/deployment/clickonce-and-application-settings). Hakkında daha fazla bilgi için [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] veri dizini bkz [erişen yerel ve uzak veri ClickOnce uygulamalarında](/visualstudio/deployment/accessing-local-and-remote-data-in-clickonce-applications).  
  
## <a name="application-settings-and-security"></a>Uygulama ayarları ve güvenlik  
 Uygulama ayarları, kısmi güven, Internet veya intranet üzerinden barındırılan Windows Forms uygulamaları için varsayılan değer kısıtlı bir ortam içinde çalışacak şekilde tasarlanmıştır. Kısmi güven ötesinde özel izin uygulama ayarlarını varsayılan ayar sağlayıcısı ile kullanmak için gereklidir.  
  
 Ne zaman uygulama ayarları kullanılır bir [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] uygulama `user`.config dosyasında depolanan [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] veri dizini. Uygulamanın boyutunu `user`.config dosyasını belirlediği veri dizini kotasını aşamaz [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)]. Daha fazla bilgi için [ClickOnce ve uygulama ayarlarını](/visualstudio/deployment/clickonce-and-application-settings).  
  
## <a name="custom-settings-providers"></a>Özel ayarları sağlayıcıları  
 Uygulama ayarları mimaride sarmalayıcı sınıfından türetilen uygulamaları ayarları arasında gevşek bir bağlantı yoktur <xref:System.Configuration.ApplicationSettingsBase>, ve ilgili ayarları sağlayıcı veya sağlayıcıları, türetilen <xref:System.Configuration.SettingsProvider>. Bu ilişkilendirmeyi yalnızca tanımlanan <xref:System.Configuration.SettingsProviderAttribute> sarmalayıcı sınıfı veya özelliklerini tek tek uygulanır. Bir ayar sağlayıcısı değil açıkça belirtilmişse varsayılan sağlayıcı <xref:System.Configuration.LocalFileSettingsProvider>, kullanılır. Sonuç olarak, bu mimari, oluşturma ve özel ayarları sağlayıcılarını kullanarak destekler.  
  
 Örneğin, geliştirme ve kullanmak istediğinizi varsayalım `SqlSettingsProvider`, tüm ayarlarını verilerini bir Microsoft SQL Server veritabanında depolayacak bir sağlayıcı. <xref:System.Configuration.SettingsProvider>-Türetilmiş sınıf bu bilgileri almak kendi `Initialize` yöntemi türünde bir parametre olarak <xref:System.Collections.Specialized.NameValueCollection?displayProperty=nameWithType>. Ardından uygulamak <xref:System.Configuration.SettingsProvider.GetPropertyValues%2A> ayarlarınızı veri deposundan alınacak yöntemi ve <xref:System.Configuration.SettingsProvider.SetPropertyValues%2A> bunları kaydetmek için. Sağlayıcınız kullanabilirsiniz <xref:System.Configuration.SettingsPropertyCollection> sağlanan <xref:System.Configuration.SettingsProvider.GetPropertyValues%2A> yanı sıra tüm diğer ayarları öznitelikleri özelliğin adını, türünü ve kapsam belirlemek için bu özellik için tanımlanmış.  
  
 Sağlayıcınız bir özellik ve yöntem uygulamaları belirgin olmayabilir uygulamanız gerekir. <xref:System.Configuration.SettingsProvider.ApplicationName%2A> Özelliktir bir soyut özelliğini <xref:System.Configuration.SettingsProvider>; aşağıdaki döndürmek için program:  
  
 [!code-csharp[ApplicationSettings.Architecture#2](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#2)]
 [!code-vb[ApplicationSettings.Architecture#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#2)]  
  
 Türetilmiş sınıfınızın de uygulamalıdır bir `Initialize` yönteminin hiçbir bağımsız değişkeni alır ve herhangi bir değer döndürür. Bu yöntem tarafından tanımlı değil <xref:System.Configuration.SettingsProvider>.  
  
 Son olarak, uygulamanız <xref:System.Configuration.IApplicationSettingsProvider> ayarlarının yenilenmesi için destek sağlamak için sağlayıcı üzerinde varsayılan ayarlarına geri alma ve ayarlarını bir uygulama sürümünden yükseltme.  
  
 Uygulanan ve sağlayıcınız derlenmiş sonra bu sağlayıcıyı kullanmak yerine varsayılan ayarları sınıfınıza istemek gerekir. Bunun aracılığıyla <xref:System.Configuration.SettingsProviderAttribute>. Bir tüm ayarları sınıfa uygulandığında, sağlayıcı sınıfı tanımlayan her ayar için kullanılır; tek tek ayarlar uygulandığında, uygulama ayarları mimarisi bu sağlayıcı için bu ayarları yalnızca kullanır ve kullandığı <xref:System.Configuration.LocalFileSettingsProvider> geri kalanı için. Aşağıdaki kod örneği, özel sağlayıcınızın kullanılacak ayarları sınıfı isteyin gösterilmektedir.  
  
 [!code-csharp[ApplicationSettings.Architecture#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#1)]
 [!code-vb[ApplicationSettings.Architecture#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#1)]  
  
 Bir sağlayıcı birden çok iş parçacıklarından aynı anda çağrılabilir, ancak her zaman aynı depolama konumuna Yazar; Bu nedenle, uygulama ayarları mimarisi her zaman sadece tek bir örnek sağlayıcısı sınıfınızın örneği oluşturulmaz.  
  
> [!IMPORTANT]
>  Sağlayıcınız iş parçacığı açısından güvenlidir ve yalnızca tek bir iş parçacığı için yapılandırma dosyalarını yazmak için bir zaman izin verir emin olmalısınız.  
  
 Tüm öznitelikler tanımlanan ayarları desteklemek sağlayıcınıza gerekmez <xref:System.Configuration?displayProperty=nameWithType> ad alanı, en az bir destek gerekir ancak <xref:System.Configuration.ApplicationScopedSettingAttribute> ve <xref:System.Configuration.UserScopedSettingAttribute>ve ayrıca desteklemelidir <xref:System.Configuration.DefaultSettingValueAttribute>. Özniteliklerle her zaman desteklemediği sağlayıcınız yalnızca bildirimi başarısız olması; bir özel durum oluşturmamalıdır. Ayarları sınıfı öznitelikleri için geçersiz bir birleşim ancak kullanıp kullanmadığını — uygulama gibi <xref:System.Configuration.ApplicationScopedSettingAttribute> ve <xref:System.Configuration.UserScopedSettingAttribute> aynı ayarı — sağlayıcınız bir özel durum ve işlemin sona ermesi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.SettingsProvider>
- <xref:System.Configuration.LocalFileSettingsProvider>
- [Uygulama Ayarlarına Genel Bakış](application-settings-overview.md)
- [Özel Denetimler için Uygulama Ayarları](application-settings-for-custom-controls.md)
- [ClickOnce ve Uygulama Ayarları](/visualstudio/deployment/clickonce-and-application-settings)
- [Uygulama Ayarları Şeması](../../configure-apps/file-schema/application-settings-schema.md)
