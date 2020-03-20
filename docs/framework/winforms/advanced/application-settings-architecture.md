---
title: Uygulama Ayarları Mimarisi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application settings [Windows Forms], architecture
ms.assetid: c8eb2ad0-fac6-4ea2-9140-675a4a44d562
ms.openlocfilehash: 078b5f3fc1cd4273af282580f41e68ca9bd8ff51
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182623"
---
# <a name="application-settings-architecture"></a>Uygulama Ayarları Mimarisi
Bu konu, Uygulama Ayarları mimarisinin nasıl çalıştığını açıklar ve gruplanmış ayarlar ve ayarlar anahtarları gibi mimarinin gelişmiş özelliklerini inceler.

 Uygulama ayarları mimarisi, uygulama veya kullanıcı kapsamıyla güçlü bir şekilde yazılan ayarları tanımlamayı ve uygulama oturumları arasındaki ayarları kalıcı olarak desteklemektedir. Mimari, ayarları kaydetmek ve yerel dosya sisteminden yüklemek için varsayılan bir kalıcılık altyapısı sağlar. Mimari de özel bir kalıcılık altyapısı sağlamak için arabirimleri tanımlar.

 Özel bileşenlerin bir uygulamada barındırıldığında kendi ayarlarını devam etmesini sağlayan arabirimler sağlanır. Bileşenler, ayarlar anahtarlarını kullanarak bileşenin birden çok örneğinin ayarlarını ayrı tutabilir.

## <a name="defining-settings"></a>Ayarları Tanımlama
 Uygulama ayarları mimarisi hem ASP.NET hem de Windows Forms içinde kullanılır ve her iki ortam arasında paylaşılan bir dizi temel sınıf içerir. En <xref:System.Configuration.SettingsBase>önemlisi, bir koleksiyon aracılığıyla ayarlara erişim sağlayan ve ayarları yükleme ve kaydetme için düşük düzeyli yöntemler sağlayan dır. Her ortam, o ortam <xref:System.Configuration.SettingsBase> için ek ayarlar işlevselliği sağlamak için türetilen kendi sınıfını uygular. Windows Forms tabanlı bir uygulamada, tüm uygulama ayarları <xref:System.Configuration.ApplicationSettingsBase> nın sınıftan türetilen bir sınıfta tanımlanması gerekir ve bu da temel sınıfa aşağıdaki işlevleri ekler:

- Üst düzey yükleme ve kaydetme işlemleri

- Kullanıcı kapsamı namına ayarlar için destek

- Kullanıcının ayarlarını önceden tanımlanmış varsayılanlara geri verme

- Ayarları önceki uygulama sürümünden yükseltme

- Ayarları, değiştirilmeden veya kaydedilmeden önce doğrulama

 <xref:System.Configuration> Ayarlar, ad alanı içinde tanımlanan bir dizi öznitelik kullanılarak tanımlanabilir; bunlar Uygulama [Ayarları Öznitelikleri](application-settings-attributes.md)açıklanmıştır. Bir ayar tanımladığınızda, ayarın tüm <xref:System.Configuration.ApplicationScopedSettingAttribute> <xref:System.Configuration.UserScopedSettingAttribute>uygulama için mi yoksa yalnızca geçerli kullanıcı için mi geçerli olduğunu açıklayan bir ayarı veya yalnızca geçerli kullanıcı için mi uygulamanız gerekir.

 Aşağıdaki kod örneği, `BackgroundColor`tek bir ayarı olan özel ayarlar sınıfını tanımlar.

 [!code-csharp[ApplicationSettings.Create#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
 [!code-vb[ApplicationSettings.Create#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]

## <a name="settings-persistence"></a>Ayarlar Kalıcılığı
 Sınıfın <xref:System.Configuration.ApplicationSettingsBase> kendisi devam etmez veya ayarlarını yüklemez; bu iş ayarlar sağlayıcı, türetilmiştir bir <xref:System.Configuration.SettingsProvider>sınıf düşüyor. Türetilmiş bir <xref:System.Configuration.ApplicationSettingsBase> sınıf <xref:System.Configuration.SettingsProviderAttribute>, sonra varsayılan sağlayıcı, üzerinden <xref:System.Configuration.LocalFileSettingsProvider>bir ayar sağlayıcısı belirtmezse, kullanılır.

 .NET Framework ile ilk olarak yayımlanan yapılandırma sistemi, yerel bilgisayarın machine.config dosyası veya uygulamanızla birlikte `app.`dağıttığınız bir exe.config dosyası içinde statik uygulama yapılandırma verilerinin sağlanmasını destekler. Sınıf <xref:System.Configuration.LocalFileSettingsProvider> bu yerel desteği aşağıdaki şekillerde genişletir:

- Uygulama kapsamlı ayarlar machine.config veya `app.`exe.config dosyalarında saklanabilir. Machine.config her zaman salt `app`okunurken,.exe.config çoğu uygulama için yalnızca okunan güvenlik konularıyla sınırlandırılmıştır.

- Kullanıcı kapsamı ayarları .exe.config dosyalarında `app`depolanabilir ve bu durumda bunlar statik varsayılan olarak kabul edilir.

- Varsayılan olmayan kullanıcı kapsamı ayarları, *kullanıcının* uygulamayı şu anda yürüten kişinin kullanıcı adı olduğu yeni bir dosyada, *kullanıcı*.config'de depolanır. Kullanıcı kapsamı nasahip bir ayar için <xref:System.Configuration.DefaultSettingValueAttribute>varsayılan bir değer belirtebilirsiniz. Kullanıcı kapsamı ayarları uygulama yürütme sırasında `user`sık sık değiştiğinden, .config her zaman okunur/yazar.

 Her üç yapılandırma dosyası da ayarları XML biçiminde depolar. Uygulama kapsamı namına ayarlar için üst `<appSettings>`düzey `<userSettings>` XML öğesi, kullanıcı kapsamı ayarları için kullanılırken. Kullanıcı `app`kapsamı namına ayarlar için hem uygulama kapsamı hem de varsayılan ayarları içeren bir .exe.config dosyası aşağıdaki gibi görünür:

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

 Yapılandırma dosyasının uygulama ayarları bölümündeki öğelerin tanımı için [Bkz. Uygulama Ayarları Şeması.](../../configure-apps/file-schema/application-settings-schema.md)

### <a name="settings-bindings"></a>Ayar Bağlamalar
 Uygulama ayarları, ayarlar nesnesi ve bileşenleri arasında ayarlar güncelleştirmelerinin çift yönlü iletişimini sağlamak için Windows Forms veri bağlama mimarisini kullanır. Uygulama ayarları oluşturmak ve bunları bileşen özelliklerine atamak için Visual Studio'yu kullanırsanız, bu bağlamalar otomatik olarak oluşturulur.

 Bir uygulama ayarını yalnızca <xref:System.Windows.Forms.IBindableComponent> arabirimi destekleyen bir bileşene bağlayabilirsiniz. Ayrıca, bileşenin belirli bir bağlı özellik için bir değişiklik olayı uygulaması veya <xref:System.ComponentModel.INotifyPropertyChanged> uygulama ayarlarını özelliğin arabirim üzerinden değiştiğini bildirmesi gerekir. Bileşen uygulanmazsa <xref:System.Windows.Forms.IBindableComponent> ve Visual Studio aracılığıyla bağlayıcı iseniz, bağlı özellikleri ilk kez ayarlanır, ancak güncelleştirmez. Bileşen özellik değişikliği <xref:System.Windows.Forms.IBindableComponent> bildirimlerini uygular ancak desteklemiyorsa, özellik değiştirildiğinde bağlama ayarlar dosyasında güncelleştirmez.

 Bazı Windows Forms bileşenleri, örneğin, <xref:System.Windows.Forms.ToolStripItem>ayarlar bağlamaları desteklemez.

### <a name="settings-serialization"></a>Ayarlar Serileştirme
 Ayarları <xref:System.Configuration.LocalFileSettingsProvider> diske kaydetmek gerektiğinde, aşağıdaki eylemleri gerçekleştirir:

1. Türemiş sınıfınızda <xref:System.Configuration.ApplicationSettingsBase> tanımlanan tüm özellikleri incelemek için yansımayı kullanır, <xref:System.Configuration.UserScopedSettingAttribute>bu özellikleri ya da <xref:System.Configuration.ApplicationScopedSettingAttribute> .

2. Özelliği diske seri hale getirir. İlk olarak, türün <xref:System.ComponentModel.TypeConverter.ConvertFromString%2A> ilişkili <xref:System.ComponentModel.TypeConverter>veya ilişkili arama çalışır. <xref:System.ComponentModel.TypeConverter.ConvertToString%2A> Bu başarılı olmazsa, bunun yerine XML serileştirme kullanır.

3. Ayarın özniteliğine göre hangi ayarların hangi dosyalara gideceğini belirler.

 Kendi ayarlar sınıfını uygularsanız, numaralandırmayı kullanarak ikili veya özel serileştirme <xref:System.Configuration.SettingsSerializeAs> ayarını işaretlemek için bu ayarı kullanabilirsiniz. <xref:System.Configuration.SettingsSerializeAsAttribute> Kodda kendi ayarlar sınıfOluşturma hakkında daha fazla bilgi için [bkz: Uygulama Ayarları oluştur](how-to-create-application-settings.md).

### <a name="settings-file-locations"></a>Ayarlar Dosya Konumları
 `app`.exe.config ve *kullanıcı*.config dosyalarının konumu, uygulamanın nasıl yüklendiğinde göre farklılık gösterir. Yerel bilgisayara kopyalanan Windows Forms tabanlı bir `app`uygulama için .exe.config, uygulamanın ana yürütülebilir dosyasının temel diziniyle aynı dizinde yer alacaktır ve <xref:System.Windows.Forms.Application.LocalUserAppDataPath%2A?displayProperty=nameWithType> *kullanıcı*.config özellik tarafından belirtilen konumda yer alacaktır. ClickOnce ile yüklenen bir uygulama için, bu dosyaların her ikisi de ClickOnce Veri Dizini'nde %InstallRoot%\Documents and Settings\\kullanıcı*adı*\Yerel Ayarlar altında bulunur.

 Bir kullanıcı, bir etki alanındaki diğer bilgisayarları kullanırken farklı Windows ve uygulama ayarlarını tanımlamasına olanak tanıyan dolaşım profillerini etkinleştirmişse, bu dosyaların depolama konumu biraz farklıdır. Bu durumda, clickonce uygulamaları ve ClickOnce olmayan uygulamalar `app`%InstallRoot%\Documents *user*and Settings\\kullanıcı*adı*\Application Data altında depolanan .exe.config ve kullanıcı .config dosyalarına sahip olacaktır.

 Uygulama Ayarları özelliğinin yeni dağıtım teknolojisiyle nasıl çalıştığı hakkında daha fazla bilgi için [ClickOnce ve Uygulama Ayarları'na](/visualstudio/deployment/clickonce-and-application-settings)bakın. ClickOnce Veri Dizini hakkında daha fazla bilgi için [ClickOnce Uygulamalarında Yerel ve Uzak Verilere Erişim'e](/visualstudio/deployment/accessing-local-and-remote-data-in-clickonce-applications)bakın.

## <a name="application-settings-and-security"></a>Uygulama Ayarları ve Güvenlik
 Uygulama ayarları, Internet veya intranet üzerinden barındırılan Windows Forms uygulamaları için varsayılan olan kısıtlı bir ortam olan kısmi güven de çalışacak şekilde tasarlanmıştır. Varsayılan ayarlar sağlayıcısıyla uygulama ayarlarını kullanmak için kısmi güvenin ötesinde özel izinler gerekmez.

 Uygulama ayarları ClickOnce uygulamasında `user`kullanıldığında,.config dosyası ClickOnce veri dizininde depolanır. Uygulamanın `user`.config dosyasının boyutu ClickOnce tarafından ayarlanan veri dizini kotasını aşamaz. Daha fazla bilgi için [ClickOnce ve Uygulama Ayarları'na](/visualstudio/deployment/clickonce-and-application-settings)bakın.

## <a name="custom-settings-providers"></a>Özel Ayarlar Sağlayıcıları
 Uygulama Ayarları mimarisinde, uygulama ayarları sarıcı sınıfı arasında gevşek bir <xref:System.Configuration.ApplicationSettingsBase>bağlantı vardır, türetilmiş , <xref:System.Configuration.SettingsProvider>ve ilişkili ayarlar sağlayıcı veya sağlayıcılar, türetilmiştir. Bu ilişkilendirme yalnızca <xref:System.Configuration.SettingsProviderAttribute> sarıcı sınıfına uygulanan veya bireysel özellikleri yle tanımlanır. Bir ayar sağlayıcısı açıkça belirtilmemişse, <xref:System.Configuration.LocalFileSettingsProvider>varsayılan sağlayıcı kullanılır. Sonuç olarak, bu mimari özel ayarlar sağlayıcıları oluşturmayı ve kullanmayı destekler.

 Örneğin, tüm ayarları verileri bir `SqlSettingsProvider`Microsoft SQL Server veritabanında depolayacak bir sağlayıcı olan bir sağlayıcı geliştirmek ve kullanmak istediğinizi varsayalım. Türetilmiş sınıfınız <xref:System.Configuration.SettingsProvider>bu bilgileri `Initialize` kendi yönteminde bir <xref:System.Collections.Specialized.NameValueCollection?displayProperty=nameWithType>tür parametresi olarak alır. Daha sonra, <xref:System.Configuration.SettingsProvider.GetPropertyValues%2A> ayarlarınızı veri deposundan almak ve <xref:System.Configuration.SettingsProvider.SetPropertyValues%2A> bunları kaydetmek için bu yöntemi uygularsınız. Sağlayıcınız, <xref:System.Configuration.SettingsPropertyCollection> sağlanan <xref:System.Configuration.SettingsProvider.GetPropertyValues%2A> özelliğin adını, türünü ve kapsamını ve söz le ilgili tanımlanan diğer ayarları belirlemek için kullanabilir.

 Sağlayıcınızın, uygulamaları açık olmayan bir özellik ve bir yöntem uygulaması gerekir. Özellik <xref:System.Configuration.SettingsProvider.ApplicationName%2A> soyut bir <xref:System.Configuration.SettingsProvider>özelliktir; aşağıdakileri döndürmek için programlamanız gerekir:

 [!code-csharp[ApplicationSettings.Architecture#2](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#2)]
 [!code-vb[ApplicationSettings.Architecture#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#2)]

 Türemiş sınıfınız `Initialize` da hiçbir bağımsız değişken alır ve hiçbir değer döndürür bir yöntem uygulaması gerekir. Bu yöntem ile <xref:System.Configuration.SettingsProvider>tanımlanmaz.

 Son olarak, <xref:System.Configuration.IApplicationSettingsProvider> ayarları yenilemek, ayarları varsayılanlarına geri getirmek ve ayarları bir uygulama sürümünden diğerine yükseltmek için sağlayıcınıza destek sağlarsınız.

 Sağlayıcınızı uyguladıktan ve derledikten sonra, ayarlar sınıfınıza varsayılan yerine bu sağlayıcıyı kullanması için talimat vermeniz gerekir. Bunu . <xref:System.Configuration.SettingsProviderAttribute> Tüm ayarlar sınıfına uygulanırsa, sağlayıcı sınıfın tanımladığı her ayar için kullanılır; tek tek ayarlara uygulanırsa, Uygulama Ayarları mimarisi yalnızca <xref:System.Configuration.LocalFileSettingsProvider> bu ayarlar için bu sağlayıcıyı kullanır ve geri kalanı için kullanır. Aşağıdaki kod örneği, ayarlar sınıfına özel sağlayıcınızı kullanmasını nasıl talimatı verilebildiğini gösterir.

 [!code-csharp[ApplicationSettings.Architecture#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#1)]
 [!code-vb[ApplicationSettings.Architecture#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#1)]

 Bir sağlayıcı aynı anda birden çok iş parçacığı ndan çağrılabilir, ancak her zaman aynı depolama konumuna yazar; bu nedenle, Uygulama Ayarları mimarisi sağlayıcı sınıfınızın yalnızca tek bir örneğini anında alacaktır.

> [!IMPORTANT]
> Sağlayıcınızın iş parçacığı için güvenli olduğundan ve yapılandırma dosyalarına yazmak için aynı anda yalnızca bir iş parçacığına izin vermelisiniz.

 Sağlayıcınızın <xref:System.Configuration?displayProperty=nameWithType> ad alanında tanımlanan tüm ayarları desteklemesi gerekmez, ancak en az destek <xref:System.Configuration.ApplicationScopedSettingAttribute> <xref:System.Configuration.UserScopedSettingAttribute>ve desteklemesi <xref:System.Configuration.DefaultSettingValueAttribute>gerekir. Desteklemediği bu öznitelikler için sağlayıcınız bildirimde bulunulmadan başarısız olmalıdır; bir istisna atmamalıdır. Ayarlar sınıfı geçersiz bir öznitelikler birleşimi kullanıyorsa, <xref:System.Configuration.ApplicationScopedSettingAttribute> ancak <xref:System.Configuration.UserScopedSettingAttribute> (uygulama ve aynı ayara gibi) sağlayıcınız bir özel durum oluşturmalı ve işlemi durdurmalıdır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.SettingsProvider>
- <xref:System.Configuration.LocalFileSettingsProvider>
- [Uygulama Ayarlarına Genel Bakış](application-settings-overview.md)
- [Özel Denetimler için Uygulama Ayarları](application-settings-for-custom-controls.md)
- [ClickOnce ve Uygulama Ayarları](/visualstudio/deployment/clickonce-and-application-settings)
- [Uygulama Ayarları Şeması](../../configure-apps/file-schema/application-settings-schema.md)
