---
title: WPF için Genelleştirme
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], international user interface
- XAML [WPF], globalization
- international user interface [WPF], XAML
- globalization [WPF]
ms.assetid: 4571ccfe-8a60-4f06-9b37-7ac0b1c2d10f
ms.openlocfilehash: bcd0a11aef2372cc6e5830892eb3b71fa841ba2f
ms.sourcegitcommit: 43761fcee10aeefcf851ea81cea3f3c691420856
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69545256"
---
# <a name="globalization-for-wpf"></a>WPF için Genelleştirme
Bu konu başlığı altında, küresel pazara yönelik uygulamalar yazarken [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] bilmeniz gereken sorunlar açıklanır. Genelleştirme programlama öğeleri [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] içinde `System.Globalization`tanımlanmıştır.

<a name="xaml_globalization"></a>
## <a name="xaml-globalization"></a>XAML Genelleştirme
 [!INCLUDE[TLA#tla_xaml#initcap](../../../../includes/tlasharptla-xamlsharpinitcap-md.md)]tabanlıdır [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] ve [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] belirtiminde tanımlanan Genelleştirme desteğinden yararlanır. Aşağıdaki bölümlerde, bilmeniz gereken [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bazı özellikler açıklanır.

<a name="char_reference"></a>
### <a name="character-references"></a>Karakter başvuruları
Bir karakter başvurusu, ondalık ya da onaltılı olarak gösterdiği belirli [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] karakterin UTF16 Code birimini sağlar. Aşağıdaki örnek, KıPTI büyük harfle veya ' Ϩ ' için ondalık bir karakter başvurusunu gösterir:

```
&#1000;
```

Aşağıdaki örnekte, onaltılı bir karakter başvurusu gösterilmektedir. Onaltılık sayının önünde bir **x** olduğuna dikkat edin.

```
&#x3E8;
```

<a name="encoding"></a>
### <a name="encoding"></a>Encoding
 Tarafından [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] desteklenen kodlama ASCII, [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] UTF-16 ve UTF-8 ' dir. Encoding deyimleri [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] belgenin başlangıcında bulunur. Kodlama özniteliği yoksa ve hiçbir bayt sırası yoksa, ayrıştırıcı varsayılan olarak UTF-8 ' i belirler. UTF-8 ve UTF-16, tercih edilen kodlamalardır. UTF-7 desteklenmez. Aşağıdaki örnek, bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyada UTF-8 kodlamasının nasıl belirtileceğini göstermektedir.

```
?xml encoding="UTF-8"?
```

<a name="lang_attrib"></a>
### <a name="language-attribute"></a>Language özniteliği
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]bir öğenin Language özniteliğini temsil etmek için [XML: lang](../../xaml-services/xml-lang-handling-in-xaml.md) kullanır.  <xref:System.Globalization.CultureInfo> Sınıfından yararlanmak için, Language özniteliği değeri tarafından <xref:System.Globalization.CultureInfo>önceden tanımlanan kültür adlarından biri olmalıdır. [XML: lang](../../xaml-services/xml-lang-handling-in-xaml.md) , öğe ağacında (bağımlılık özelliği devralımı nedeniyle DEĞIL, XML kuralları tarafından) devralınabilir ve açıkça atanmamışsa boş bir dize olur.

 Language özniteliği, dialarcts 'yi belirtmek için çok yararlıdır. Örneğin, Fransızca Fransa, Quebec, Belçika ve Isviçre 'de farklı yazım, sözlük ve telaffuz vardır. Ayrıca Çince, Japonca ve Korece kod noktalarını [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)]paylaşır, ancak İdeografik biçimleri farklıdır ve tamamen farklı yazı tiplerini kullanır.

 Aşağıdaki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örnek, Kanada Fransızcası `fr-CA` belirtmek için Language özniteliğini kullanır.

```xml
<TextBlock xml:lang="fr-CA">Découvrir la France</TextBlock>
```

<a name="unicode"></a>
### <a name="unicode"></a>Unicode
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]Yedeklerin dahil [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] tüm özellikleri destekler. Karakter kümesi eşlenebilir [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)]olduğu sürece, desteklenir. Örneğin, GB18030 Çince, Japonca ve Kore dili (CFK) uzantısı A ve B ve vekil çiftleri ile eşlenen bazı karakterleri tanıtır, bu nedenle tam olarak desteklenmektedir. Bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama, temsilci <xref:System.Globalization.StringInfo> çiftleri mi yoksa birleştirme karakterleri mi olduğunu anlamak zorunda kalmadan dizeleri işlemek için kullanabilir.

<a name="design_intl_ui_with_xaml"></a>
## <a name="designing-an-international-user-interface-with-xaml"></a>XAML ile uluslararası bir kullanıcı arabirimi tasarlama
 Bu bölümde, [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] bir uygulamayı yazarken göz önünde bulundurmanız gereken özellikler açıklanmaktadır.

<a name="intl_text"></a>
### <a name="international-text"></a>Uluslararası metin
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], tüm Microsoft .NET Framework yazma sistemlerini destekleyen yerleşik işleme içerir.

 Şu betikler Şu anda destekleniyor:

- Arapça

- Bengali

- Devanagari

- V

- Yunanca

- Gucerat dili

- Gurmukhi

- İbranice

- İdeografik betikler

- Kannada dili

- Laos

- Tin

- Malayalam dili

- Moğolca

- Odia

- Yani

- Tamil dili

- Telugu dili

- Thaana

- D

- Dili

 \* Bu yayında Tay dilindeki metnin görüntülenmesi ve düzenlemesi desteklenir; sözcük bölünmesi değil.

 Şu betikler Şu anda desteklenmemektedir:

- Khmer

- Kore dili Eski Hangul

- Myanmar

- Sinhali

 Tüm yazma sistemi motorları OpenType yazı tiplerini destekler. OpenType yazı tipleri, yazı tipi oluşturucularının daha iyi uluslararası ve yüksek kaliteli tipografik yazı tiplerini tasarlamasını sağlayan OpenType Düzen tablolarını içerebilir. OpenType yazı tipi düzen tabloları, metin düzenini geliştirmek için metin işleme uygulamalarını etkinleştiren glif değiştirmeleri, glif konumlandırma, gerekçe ve temel konumlandırma hakkında bilgiler içerir.

 OpenType yazı tipleri, kodlama kullanarak [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] büyük karakter kümelerinin işlenmesine izin verir. Bu tür bir kodlama, uluslararası ve tipografik glif çeşitleri için geniş uluslararası destek sunar.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]metin işleme, çözüm bağımsızlığını destekleyen Microsoft ClearType alt piksel teknolojisi tarafından desteklenmektedir. Bu, okunabilirliği önemli ölçüde artırır ve tüm betikler için yüksek kaliteli dergi stil belgelerini destekleme yeteneği sağlar.

<a name="intl_layout"></a>
### <a name="international-layout"></a>Uluslararası düzen
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Yatay, çift yönlü ve dikey düzenleri desteklemek için çok kullanışlı bir yol sağlar. Sunum çerçevesinde, <xref:System.Windows.FrameworkElement.FlowDirection%2A> özelliği düzeni tanımlamak için kullanılabilir. Akış yönü desenleri şunlardır:

- Latin, Doğu Asya ve benzeri için *Solttoright* -yatay düzeni.

- *RightToLeft* -Arapça, İbranice ve diğerleri için çift yönlü.

<a name="developing_localizable_apps"></a>
## <a name="developing-localizable-applications"></a>Yerelleştirilebilir uygulamalar geliştirme
 Küresel tüketim için bir uygulama yazdığınızda, uygulamanın yerelleştirilebilir olması gerektiğini aklınızda bulundurmanız gerekir. Aşağıdaki konular göz önünde bulundurmanız gereken noktaları işaret etmektedir.

<a name="mui"></a>
### <a name="multilingual-user-interface"></a>Çok dilli kullanıcı arabirimi
 Çok dilli kullanıcı arabirimleri (MUI), [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] bir dilden diğerine [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] geçiş desteği sağlar. Bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama, MUI 'yi desteklemek için derleme modelini kullanır. Tek bir uygulama dilden bağımsız derlemeler ve dile bağlı uydu kaynak derlemeleri içerir. Giriş noktası yönetilen bir. EXE ana derlemede.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]kaynak yükleyicisi, [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)]kaynak aramasını ve geri dönüşü desteklemek için Resource Manager 'ın avantajlarından yararlanır. Birden çok dil uydu derlemesi aynı ana derlemeyle çalışır. Yüklenen kaynak bütünleştirilmiş kodu, geçerli iş parçacığının öğesine <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> bağlıdır.

<a name="localizable_ui"></a>
### <a name="localizable-user-interface"></a>Yerelleştirilebilir kullanıcı arabirimi
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]uygulamalar, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bunları [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]tanımlamak için kullanır. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]geliştiricilerin bir dizi özellik ve mantığa sahip nesneler hiyerarşisi belirlemesine izin verir. ' Nin [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] birincil kullanımı, uygulamaları geliştirmektir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , ancak herhangi bir ortak dil çalışma zamanı (CLR) nesnesinin hiyerarşisini belirtmek için kullanılabilir. Çoğu geliştirici, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] uygulamasının uygulamasını belirtmek için kullanır ve kullanıcı etkileşimine tepki vermek için gibi C# bir programlama dili kullanır.

 Bir görünüm kaynak noktasından, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dile bağlı [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] bir kaynak öğesidir ve bu nedenle son dağıtım biçimi Uluslararası dilleri desteklemek için yerelleştirilebilir olmalıdır. Olayları işleyemediği için birçok [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] uygulama, bunu yapmak için kod blokları içerir. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Daha fazla bilgi için bkz. [xaml genel bakış (WPF)](xaml-overview-wpf.md). Bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya, XAML 'in BAML biçiminde simgeleştirilir, kod çıkarılır ve farklı ikili dosyalara derlenir. XAML dosyalarının, görüntülerinin ve diğer yönetilen kaynak nesne türlerinin BAML formu, uydu kaynak derlemesine katıştırılır. Bu, diğer dillere yerelleştirilebilir veya yerelleştirme gerekli olmadığında ana derlemedir.

> [!NOTE]
>  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]uygulamalar dize tabloları, [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)]görüntüleri vb. dahil olmak üzere tüm clr kaynaklarını destekler.

<a name="building_localizable_apps"></a>
### <a name="building-localizable-applications"></a>Yerelleştirilebilir uygulamalar oluşturma
 Yerelleştirme, farklı kültürlere [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] uyarlamanız anlamına gelir. Bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamayı yerelleştirilebilir hale getirmek için geliştiricilerin tüm yerelleştirilebilir kaynakları bir kaynak derlemesinde oluşturması gerekir. Kaynak derlemesi farklı dillere yereldir ve arka plan kodu, yüklemek için kaynak yönetimi API kullanır. Bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama için gerekli dosyalardan biri bir proje dosyasıdır (. proj). Uygulamanızda kullandığınız tüm kaynaklar proje dosyasına eklenmelidir. Bir. csproj dosyasından aşağıdaki örnek bunun nasıl yapılacağını gösterir.

```xml
<Resource Include="data\picture1.jpg"/>
<EmbeddedResource Include="data\stringtable.en-US.restext"/>
```

 Uygulamanızdaki bir kaynağı kullanmak için bir <xref:System.Resources.ResourceManager> oluşturun ve kullanmak istediğiniz kaynağı yükleyin. Aşağıdaki örnek bunun nasıl yapılacağını göstermektedir.

 [!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]

<a name="using_clickonce"></a>
## <a name="using-clickonce-with-localized-applications"></a>Yerelleştirilmiş uygulamalarla ClickOnce kullanma
 ClickOnce, Visual Studio 2005 ile birlikte gönderilecek yeni bir Windows Forms dağıtım teknolojisidir. Web uygulamalarının uygulama yükleme ve yükseltme yapmasına izin vermez. ClickOnce ile dağıtılan bir uygulama yerelleştirildiği zaman, yalnızca yerelleştirilmiş kültür üzerinde görüntülenebilir. Örneğin, dağıtılan bir uygulama Japonca 'ya yerelleştirilmiştir, yalnızca İngilizce 'de değil, Japonca [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] 'da görüntülenebilir. Bu, Japonca kullanıcıların Windows 'un Ingilizce sürümünü çalıştırmasına yönelik yaygın bir senaryo olduğundan bir sorun oluşturur.

 Bu soruna yönelik çözüm, Nötr dil geri dönüş özniteliğini ayarlamadır. Uygulama geliştiricisi, isteğe bağlı olarak ana derlemeden kaynakları kaldırabilir ve belirli bir kültüre karşılık gelen bir uydu derlemesinde kaynakların bulunmamasını belirtebilir. Bu işlemi denetlemek için öğesini kullanın <xref:System.Resources.NeutralResourcesLanguageAttribute>. <xref:System.Resources.NeutralResourcesLanguageAttribute> Sınıfının Oluşturucusu, geri dönüş kaynaklarını Ayıklanacak konumu <xref:System.Resources.ResourceManager> belirtmek için bir <xref:System.Resources.UltimateResourceFallbackLocation> parametre alan iki imzaya sahiptir: ana derleme veya uydu bütünleştirilmiş kodu. Aşağıdaki örnek, özniteliğini nasıl kullanacağınızı gösterir. Son geri dönüş konumu için, kod, şu anda <xref:System.Resources.ResourceManager> yürütülmekte olan derlemenin dizininin "de" alt dizinindeki kaynakları aramaya neden olur.

```
[assembly: NeutralResourcesLanguageAttribute(
    "de" , UltimateResourceFallbackLocation.Satellite)]
```

## <a name="see-also"></a>Ayrıca bkz.

- [WPF Genelleştirmesi ve Yerelleştirmesine Genel Bakış](wpf-globalization-and-localization-overview.md)
