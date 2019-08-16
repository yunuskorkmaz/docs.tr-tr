---
title: Uygulama Ayarları Mimarisi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application settings [Windows Forms], architecture
ms.assetid: c8eb2ad0-fac6-4ea2-9140-675a4a44d562
ms.openlocfilehash: b5d5a4456bef925cd8093fe9c696145aff83660e
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039411"
---
# <a name="application-settings-architecture"></a>Uygulama Ayarları Mimarisi
Bu konu, uygulama ayarları mimarisinin nasıl çalıştığını açıklar ve mimarinin gruplanmış ayarlar ve ayarlar gibi gelişmiş özelliklerini araştırır.

 Uygulama ayarları mimarisi, kesin belirlenmiş ayarların uygulama veya Kullanıcı kapsamıyla tanımlanmasını ve uygulama oturumları arasındaki ayarları kalıcı hale getirmeyi destekler. Mimari, ayarları kaydetmek ve yerel dosya sistemine yüklemek için varsayılan bir kalıcılık altyapısı sağlar. Mimari Ayrıca özel bir kalıcılık altyapısı sağlamaya yönelik arabirimleri de tanımlar.

 Özel bileşenlerin bir uygulamada barındırıldığı zaman kendi ayarlarını kalıcı hale getirmek için arabirimler sağlanır. Ayarlar anahtarlar kullanılarak bileşenler, bileşenin birden çok örneği için ayarları ayrı tutabilir.

## <a name="defining-settings"></a>Ayarları tanımlama
 Uygulama ayarları mimarisi hem ASP.NET hem de Windows Forms içinde kullanılır ve her iki ortamda da paylaşılan bir dizi temel sınıf içerir. Bu, bir koleksiyon <xref:System.Configuration.SettingsBase>aracılığıyla ayarlara erişim sağlayan ve ayarları yüklemek ve kaydetmek için düşük düzey Yöntemler sağlayan en önemdir. Her ortam, bu ortam için ek ayar <xref:System.Configuration.SettingsBase> işlevselliği sağlamak üzere öğesinden türetilmiş kendi sınıfını uygular. Windows Forms tabanlı bir uygulamada, tüm uygulama ayarlarının <xref:System.Configuration.ApplicationSettingsBase> sınıfından türetilmiş bir sınıfta tanımlanması gerekir, bu, temel sınıfa aşağıdaki işlevselliği ekler:

- Daha yüksek düzey yükleme ve kaydetme işlemleri

- Kullanıcı kapsamlı ayarlar için destek

- Kullanıcının ayarlarını önceden tanımlanmış varsayılanlara geri döndürme

- Önceki bir uygulama sürümünden ayarları yükseltme

- Ayarları, değiştirildikleri veya kaydedilmeden önce doğrulanıyor

 Ayarlar, <xref:System.Configuration> ad alanı içinde tanımlanmış bir dizi öznitelik kullanılarak açıklanabilir; bunlar [uygulama ayarları özniteliklerinde](application-settings-attributes.md)açıklanmıştır. Bir ayar tanımladığınızda, ya da <xref:System.Configuration.ApplicationScopedSettingAttribute> ayarın uygulamanın tamamına mi yoksa yalnızca geçerli kullanıcıya mı uygulanacağını açıklayan veya <xref:System.Configuration.UserScopedSettingAttribute>ile uygulamanız gerekir.

 Aşağıdaki kod örneği, `BackgroundColor`tek bir ayarı olan özel bir ayarlar sınıfını tanımlar.

 [!code-csharp[ApplicationSettings.Create#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
 [!code-vb[ApplicationSettings.Create#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]

## <a name="settings-persistence"></a>Ayarların kalıcılığı
 Sınıf kendi kendine devam etmez veya ayarları yükler; bu iş, ' den <xref:System.Configuration.SettingsProvider>türetilen bir sınıf olan ayarlar sağlayıcısına denk gelir. <xref:System.Configuration.ApplicationSettingsBase> Türetilmiş bir sınıfı <xref:System.Configuration.ApplicationSettingsBase> <xref:System.Configuration.SettingsProviderAttribute>aracılığıyla bir ayar sağlayıcısı belirtmezse, varsayılan sağlayıcı <xref:System.Configuration.LocalFileSettingsProvider>kullanılır.

 .NET Framework ile ilk olarak yayınlanan yapılandırma sistemi, yerel bilgisayarın Machine. config dosyası veya ile dağıttığınız bir `app.`exe. config dosyası aracılığıyla statik uygulama yapılandırma verileri sağlamayı destekler. uygulamanız. <xref:System.Configuration.LocalFileSettingsProvider> Sınıfı bu yerel desteği aşağıdaki yollarla genişletir:

- Uygulama kapsamlı ayarlar, Machine. config veya `app.`exe. config dosyalarında depolanabilir. Machine. config her zaman salt okunurdur, `app`ancak. exe. config çoğu uygulama için salt okuma güvenlik konuları tarafından kısıtlanır.

- Kullanıcı kapsamlı ayarlar `app`. exe. config dosyalarında depolanabilir, bu durumda statik varsayılanlar olarak kabul edilir.

- Varsayılan olmayan kullanıcı tanımlı ayarlar yeni bir dosya olan *User*. config dosyasında depolanır; burada *Kullanıcı* uygulamayı çalıştırmakta olan kişinin kullanıcı adıdır. İle <xref:System.Configuration.DefaultSettingValueAttribute>kullanıcı kapsamlı bir ayar için varsayılan bir değer belirtebilirsiniz. Kullanıcı kapsamlı ayarlar uygulama yürütme sırasında sıklıkla değiştiğinden, `user`. config her zaman okuma/yazma olur.

 Tüm üç yapılandırma dosyası, ayarları XML biçiminde depolar. Uygulama kapsamlı ayarlar `<appSettings>`için en üst düzey xml öğesi `<userSettings>` , kullanıcı kapsamlı ayarlar için kullanılır. Uygulama `app`kapsamlı ayarları ve kullanıcı kapsamlı ayarlar için Varsayılanları içeren bir. exe. config dosyası şuna benzer:

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

 Yapılandırma dosyasının uygulama ayarları bölümündeki öğelerin tanımı için bkz. [uygulama ayarları şeması](../../configure-apps/file-schema/application-settings-schema.md).

### <a name="settings-bindings"></a>Ayarlar bağlamaları
 Uygulama ayarları, ayarlar nesnesi ve bileşenleri arasında ayar güncelleştirmeleriyle iki yönlü iletişim sağlamak için Windows Forms veri bağlama mimarisini kullanır. Uygulama ayarları oluşturmak ve bunları bileşen özelliklerine atamak için Visual Studio kullanıyorsanız, bu bağlamalar otomatik olarak oluşturulur.

 Bir uygulama ayarını yalnızca <xref:System.Windows.Forms.IBindableComponent> arabirimi destekleyen bir bileşene bağlayabilirsiniz. Ayrıca, bileşen belirli bir bağlantılı özellik için bir değişiklik olayı uygulamalıdır veya özelliğin <xref:System.ComponentModel.INotifyPropertyChanged> arabirim aracılığıyla değiştiği uygulama ayarlarını bilgilendirmelidir. Bileşen uygulamaz <xref:System.Windows.Forms.IBindableComponent> ve Visual Studio ile bağlıyorsanız, ilişkili özellikler ilk kez ayarlanır, ancak güncellemez. Bileşen, özellik değişikliği <xref:System.Windows.Forms.IBindableComponent> bildirimlerini uygulamaktadır ancak desteklemiyorsa, özellik değiştirildiğinde bağlama ayarlar dosyasında güncellemez.

 Gibi bazı Windows Forms bileşenleri <xref:System.Windows.Forms.ToolStripItem>, ayar bağlamalarını desteklemez.

### <a name="settings-serialization"></a>Ayarları serileştirme
 Ayarları <xref:System.Configuration.LocalFileSettingsProvider> diske kaydetmesi gereken zaman, aşağıdaki eylemleri gerçekleştirir:

1. , <xref:System.Configuration.ApplicationSettingsBase> <xref:System.Configuration.ApplicationScopedSettingAttribute> Veya ileuygulanmışolanlarıbulmakiçintüretilmişsınıfınızatanımlanmıştümözellikleriincelemekiçinyansımakullanır.<xref:System.Configuration.UserScopedSettingAttribute>

2. Özelliği diske dizleştirir. Önce türün ilişkili <xref:System.ComponentModel.TypeConverter.ConvertToString%2A> <xref:System.ComponentModel.TypeConverter.ConvertFromString%2A> 'iveyatürünüçağırmayıdener<xref:System.ComponentModel.TypeConverter>. Bu başarılı olmazsa bunun yerine XML serileştirme kullanır.

3. Ayarın özniteliğine bağlı olarak hangi ayarların hangi dosyalara gidebileceğini belirler.

 Kendi ayarlar sınıfınızı uygularsanız, <xref:System.Configuration.SettingsSerializeAsAttribute> <xref:System.Configuration.SettingsSerializeAs> sabit listesini kullanarak ikili veya özel serileştirme için bir ayarı işaretlemek üzere öğesini kullanabilirsiniz. Kodda kendi ayarlar sınıfınızı oluşturma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Uygulama ayarları](how-to-create-application-settings.md)oluşturun.

### <a name="settings-file-locations"></a>Ayarlar dosya konumları
 `app`. Exe. config ve *User*. config dosyalarının konumu uygulamanın nasıl yüklendiğine bağlı olarak farklılık gösterir. Yerel bilgisayara `app`kopyalanmış Windows Forms tabanlı bir uygulama için. exe. config, uygulamanın ana yürütülebilir dosyasının temel diziniyle aynı dizinde yer alır ve *User*. config, tarafından belirtilen konumda bulunur <xref:System.Windows.Forms.Application.LocalUserAppDataPath%2A?displayProperty=nameWithType> özelliği. ClickOnce aracılığıyla yüklenen bir uygulama için, bu dosyaların her ikisi de%InstallRoot%\Documents ve Settings\\*UserName*\Local Settings altındaki ClickOnce veri dizininde yer alır.

 Bir Kullanıcı bir etki alanı içindeki diğer bilgisayarları kullanırken farklı pencereler ve uygulama ayarları tanımlamasına olanak sağlayan gezici profilleri etkinleştirmişse, bu dosyaların depolama konumu biraz farklıdır. Bu durumda, hem ClickOnce uygulamaları hem de ClickOnce olmayan uygulamalar,%InstallRoot%\Documents ve Settings `app`\\*Kullanıcı adı*\Application Data altında depolanan. exe. config ve *User*. config dosyalarına sahip olur.

 Uygulama ayarları özelliğinin yeni dağıtım teknolojisiyle nasıl çalıştığı hakkında daha fazla bilgi için bkz. [ClickOnce ve uygulama ayarları](/visualstudio/deployment/clickonce-and-application-settings). ClickOnce veri dizini hakkında daha fazla bilgi için bkz. [ClickOnce uygulamalarında yerel ve uzak verilere erişme](/visualstudio/deployment/accessing-local-and-remote-data-in-clickonce-applications).

## <a name="application-settings-and-security"></a>Uygulama ayarları ve güvenlik
 Uygulama ayarları, Internet veya intranette barındırılan Windows Forms uygulamalar için varsayılan olan sınırlı bir ortam olan kısmi güvende çalışmak üzere tasarlanmıştır. Varsayılan ayar sağlayıcısı ile uygulama ayarlarını kullanmak için kısmi güvenin ötesinde hiçbir özel izin gerekmez.

 Uygulama ayarları bir ClickOnce uygulamasında kullanıldığında, `user`. config dosyası ClickOnce veri dizininde depolanır. Uygulamanın `user`. config dosyasının boyutu ClickOnce tarafından ayarlanan veri dizini kotasını aşamaz. Daha fazla bilgi için bkz. [ClickOnce ve uygulama ayarları](/visualstudio/deployment/clickonce-and-application-settings).

## <a name="custom-settings-providers"></a>Özel ayarlar sağlayıcıları
 Uygulama ayarları mimarisinde, uygulama ayarları sarmalayıcı sınıfı, öğesinden <xref:System.Configuration.ApplicationSettingsBase>türetilmişi ve ilişkili ayar sağlayıcısı veya sağlayıcılardan türetilmiş, öğesinden <xref:System.Configuration.SettingsProvider>türetilmiş bir gevşek bağ vardır. Bu ilişki yalnızca sarmalayıcı sınıfına veya tek <xref:System.Configuration.SettingsProviderAttribute> tek özelliklerine uygulanan tarafından tanımlanır. Bir ayar sağlayıcısı açıkça belirtilmemişse, varsayılan sağlayıcı <xref:System.Configuration.LocalFileSettingsProvider>kullanılır. Sonuç olarak, Bu mimaride özel ayar sağlayıcılarının oluşturulması ve kullanılması desteklenir.

 Örneğin, tüm ayar verilerini bir Microsoft SQL Server veritabanında depolayacak bir sağlayıcı `SqlSettingsProvider`geliştirmek ve kullanmak istediğinizi varsayalım. Türetilmiş sınıfınız, bu bilgileri kendi `Initialize` yönteminde türünde <xref:System.Collections.Specialized.NameValueCollection?displayProperty=nameWithType>bir parametre olarak alır. <xref:System.Configuration.SettingsProvider> Daha sonra, veri deposundan <xref:System.Configuration.SettingsProvider.GetPropertyValues%2A> ayarlarınızı almak ve <xref:System.Configuration.SettingsProvider.SetPropertyValues%2A> bunları kaydetmek için yöntemini uygulamalısınız. Sağlayıcınız, özelliğin adını, <xref:System.Configuration.SettingsPropertyCollection> türünü ve <xref:System.Configuration.SettingsProvider.GetPropertyValues%2A> kapsamını ve bu özellik için tanımlanan diğer ayar özniteliklerini öğrenmek için sağlanan ' yi kullanabilir.

 Sağlayıcınızın bir özellik ve uygulamaları belirgin olmayabilir bir yöntem uygulaması gerekir. Özelliği, öğesinin <xref:System.Configuration.SettingsProvider>soyut bir özelliğidir; aşağıdakini döndürecek şekilde programlayabilirsiniz: <xref:System.Configuration.SettingsProvider.ApplicationName%2A>

 [!code-csharp[ApplicationSettings.Architecture#2](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#2)]
 [!code-vb[ApplicationSettings.Architecture#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#2)]

 Türetilmiş sınıfınız Ayrıca bağımsız değişken içermeyen ve `Initialize` değer döndüren bir yöntemi uygulamalıdır. Bu yöntem tarafından <xref:System.Configuration.SettingsProvider>tanımlanmamıştır.

 Son olarak, ayarları <xref:System.Configuration.IApplicationSettingsProvider> yenileme, ayarlarını varsayılanlarına geri alma ve ayarları bir uygulama sürümünden diğerine yükseltme desteği sağlamak için sağlayıcınıza uygulanır.

 Sağlayıcınızı oluşturup derledikten sonra, ayarlar sınıfınızı varsayılan yerine bu sağlayıcıyı kullanmak üzere istemeniz gerekir. Bunu ile <xref:System.Configuration.SettingsProviderAttribute>gerçekleştirirsiniz. Tüm bir ayar sınıfına uygulanırsa, sağlayıcı, sınıfın tanımladığı her ayar için kullanılır; tek tek ayarlara uygulanırsa, uygulama ayarları mimarisi bu sağlayıcıyı yalnızca bu ayarlar için kullanır ve Rest için kullanır <xref:System.Configuration.LocalFileSettingsProvider> . Aşağıdaki kod örneği, özel sağlayıcınızı kullanmak için ayarlar sınıfının nasıl kullanıldığını gösterir.

 [!code-csharp[ApplicationSettings.Architecture#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#1)]
 [!code-vb[ApplicationSettings.Architecture#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#1)]

 Bir sağlayıcı aynı anda birden fazla iş parçacığından çağrılabilir, ancak her zaman aynı depolama konumuna yazılacak; Bu nedenle, uygulama ayarları mimarisi yalnızca sağlayıcı sınıfınızın tek bir örneğini örnekleymeyecektir.

> [!IMPORTANT]
>  Sağlayıcınızın iş parçacığı açısından güvenli olduğundan emin olun ve aynı anda yalnızca bir iş parçacığının yapılandırma dosyalarına yazmasını sağlar.

 Sağlayıcınızın, <xref:System.Configuration?displayProperty=nameWithType> ad alanında tanımlanan tüm ayar özniteliklerini desteklemesi gerekmez, ancak en düşük düzeyde destek <xref:System.Configuration.ApplicationScopedSettingAttribute> ve <xref:System.Configuration.UserScopedSettingAttribute>Ayrıca desteklemesi <xref:System.Configuration.DefaultSettingValueAttribute>gerekir. Desteklemediği öznitelikler için, sağlayıcınız yalnızca bildirim olmadan başarısız olur; özel durum oluşturmaz. Ayarlar sınıfı, ancak aynı ayarı uygulamak <xref:System.Configuration.ApplicationScopedSettingAttribute> <xref:System.Configuration.UserScopedSettingAttribute> gibi, özniteliklerin geçersiz bir birleşimini kullanıyorsa, sağlayıcınız bir özel durum ve bir işlem oluşturması gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.SettingsProvider>
- <xref:System.Configuration.LocalFileSettingsProvider>
- [Uygulama Ayarlarına Genel Bakış](application-settings-overview.md)
- [Özel Denetimler için Uygulama Ayarları](application-settings-for-custom-controls.md)
- [ClickOnce ve Uygulama Ayarları](/visualstudio/deployment/clickonce-and-application-settings)
- [Uygulama Ayarları Şeması](../../configure-apps/file-schema/application-settings-schema.md)
