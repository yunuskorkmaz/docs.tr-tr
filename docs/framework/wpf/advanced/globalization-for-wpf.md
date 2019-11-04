---
title: WPF için Genelleştirme
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], international user interface
- XAML [WPF], globalization
- international user interface [WPF], XAML
- globalization [WPF]
ms.assetid: 4571ccfe-8a60-4f06-9b37-7ac0b1c2d10f
ms.openlocfilehash: 04001f88e0f59fd4eb3ca84d846456be7740737e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460489"
---
# <a name="globalization-for-wpf"></a>WPF için Genelleştirme
Bu konu başlığı altında, küresel pazara yönelik [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamalar yazarken bilmeniz gereken sorunlar açıklanır. Genelleştirme programlama öğeleri <xref:System.Globalization> ad alanında .NET içinde tanımlanmıştır.

<a name="xaml_globalization"></a>
## <a name="xaml-globalization"></a>XAML Genelleştirme
 Extensible Application Markup Language (XAML) [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] tabanlıdır ve [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] belirtiminde tanımlanan Genelleştirme desteğinden faydalanır. Aşağıdaki bölümlerde, bilmeniz gereken bazı [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] özellikleri açıklanır.

<a name="char_reference"></a>
### <a name="character-references"></a>Karakter başvuruları
Bir karakter başvurusu, ondalık ya da onaltılı olarak temsil ettiği belirli Unicode karakterinin UTF16 Code birimini verir. Aşağıdaki örnek, KıPTI büyük harfle veya ' Ϩ ' için ondalık bir karakter başvurusunu gösterir:

```
&#1000;
```

Aşağıdaki örnekte, onaltılı bir karakter başvurusu gösterilmektedir. Onaltılık sayının önünde bir **x** olduğuna dikkat edin.

```
&#x3E8;
```

<a name="encoding"></a>
### <a name="encoding"></a>Şifreleme
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tarafından desteklenen kodlama ASCII, Unicode UTF-16 ve UTF-8 ' dir. Encoding deyimleri [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] belgenin başlangıcında bulunur. Kodlama özniteliği yoksa ve hiçbir bayt sırası yoksa, ayrıştırıcı varsayılan olarak UTF-8 ' i belirler. UTF-8 ve UTF-16, tercih edilen kodlamalardır. UTF-7 desteklenmez. Aşağıdaki örnekte, bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyasında UTF-8 kodlamasının nasıl belirtileceği gösterilmektedir.

```xaml
?xml encoding="UTF-8"?
```

<a name="lang_attrib"></a>
### <a name="language-attribute"></a>Language özniteliği
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], bir öğenin Language özniteliğini temsil etmek için [XML: lang](../../xaml-services/xml-lang-handling-in-xaml.md) kullanır.  <xref:System.Globalization.CultureInfo> sınıfından yararlanmak için dil özniteliği değeri, <xref:System.Globalization.CultureInfo>tarafından önceden tanımlanan kültür adlarından biri olmalıdır. [XML: lang](../../xaml-services/xml-lang-handling-in-xaml.md) , öğe ağacında (bağımlılık özelliği devralımı nedeniyle DEĞIL, XML kuralları tarafından) devralınabilir ve açıkça atanmamışsa boş bir dize olur.

 Language özniteliği, dialarcts 'yi belirtmek için çok yararlıdır. Örneğin, Fransızca Fransa, Quebec, Belçika ve Isviçre 'de farklı yazım, sözlük ve telaffuz vardır. Ayrıca Çince, Japonca ve Korece kod noktalarını Unicode olarak paylaşır, ancak İdeografik biçimleri farklıdır ve tamamen farklı yazı tiplerini kullanır.

 Aşağıdaki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örnek, Kanada Fransızcası belirtmek için `fr-CA` Language özniteliğini kullanır.

```xaml
<TextBlock xml:lang="fr-CA">Découvrir la France</TextBlock>
```

<a name="unicode"></a>
### <a name="unicode"></a>Unicode
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], yedekleri dahil tüm Unicode özelliklerini destekler. Karakter kümesi Unicode ile eşlenebilir olduğu sürece, desteklenir. Örneğin, GB18030 Çince, Japonca ve Kore dili (CFK) uzantısı A ve B ve vekil çiftleri ile eşlenen bazı karakterleri tanıtır, bu nedenle tam olarak desteklenmektedir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir uygulama, vekil çiftleri mi yoksa birleştirme karakterleri mi olduğunu anlamak zorunda kalmadan dizeleri işlemek için <xref:System.Globalization.StringInfo> kullanabilir.

<a name="design_intl_ui_with_xaml"></a>
## <a name="designing-an-international-user-interface-with-xaml"></a>XAML ile uluslararası bir kullanıcı arabirimi tasarlama
 Bu bölümde, bir uygulamayı yazarken göz önünde bulundurmanız gereken [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] özellikler açıklanmaktadır.

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

 OpenType yazı tipleri, Unicode kodlaması kullanarak büyük karakter kümelerinin işlenmesine izin verir. Bu tür bir kodlama, uluslararası ve tipografik glif çeşitleri için geniş uluslararası destek sunar.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] metin işleme, çözüm bağımsızlığını destekleyen Microsoft ClearType alt piksel teknolojisi tarafından desteklenir. Bu, okunabilirliği önemli ölçüde artırır ve tüm betikler için yüksek kaliteli dergi stil belgelerini destekleme yeteneği sağlar.

<a name="intl_layout"></a>
### <a name="international-layout"></a>Uluslararası düzen
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yatay, çift yönlü ve dikey düzenleri desteklemek için çok kullanışlı bir yol sağlar. Sunum çerçevesinde <xref:System.Windows.FrameworkElement.FlowDirection%2A> özelliği düzeni tanımlamak için kullanılabilir. Akış yönü desenleri şunlardır:

- Latin, Doğu Asya ve benzeri için *Solttoright* -yatay düzeni.

- *RightToLeft* -Arapça, İbranice ve diğerleri için çift yönlü.

<a name="developing_localizable_apps"></a>
## <a name="developing-localizable-applications"></a>Yerelleştirilebilir uygulamalar geliştirme
 Küresel tüketim için bir uygulama yazdığınızda, uygulamanın yerelleştirilebilir olması gerektiğini aklınızda bulundurmanız gerekir. Aşağıdaki konular göz önünde bulundurmanız gereken noktaları işaret etmektedir.

<a name="mui"></a>
### <a name="multilingual-user-interface"></a>Çok dilli kullanıcı arabirimi
 Çok dilli kullanıcı arabirimleri (MUI), tek bir dilden diğerine geçiş yapmak için Microsoft desteği sağlar. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir uygulama, MUI 'yi desteklemek için bütünleştirilmiş kod modelini kullanır. Tek bir uygulama dilden bağımsız derlemeler ve dile bağlı uydu kaynak derlemeleri içerir. Giriş noktası yönetilen bir. EXE ana derlemede.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kaynak yükleyicisi, kaynak aramasını ve geri dönüşü desteklemek için [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)]Resource Manager 'dan yararlanır. Birden çok dil uydu derlemesi aynı ana derlemeyle çalışır. Yüklenen kaynak derlemesi, geçerli iş parçacığının <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> bağlıdır.

<a name="localizable_ui"></a>
### <a name="localizable-user-interface"></a>Yerelleştirilebilir kullanıcı arabirimi
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]tanımlamak için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kullanır. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], geliştiricilerin bir dizi özellik ve mantığa sahip bir nesne hiyerarşisi belirlemesine izin verir. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] birincil kullanımı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar geliştirmektir, ancak herhangi bir ortak dil çalışma zamanı (CLR) nesnesinin hiyerarşisini belirtmek için kullanılabilir. Çoğu geliştirici, uygulamasının [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] belirtmek için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kullanır ve kullanıcı etkileşimine tepki vermek için gibi C# bir programlama dili kullanır.

 Bir kaynak görünümünden, dile bağlı [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] tanımlamakta tasarlanan bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyası bir kaynak öğesidir ve bu nedenle, son dağıtım biçimi Uluslararası dilleri destekleyecek şekilde yerelleştirilebilir olmalıdır. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] olayları işleyemediği için, çoğu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] uygulama bunu yapmak için kod blokları içerir. Daha fazla bilgi için bkz. [xaml genel bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md). Kod çıkarılır ve bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyası XAML 'in BAML biçiminde simgeleştirilir, farklı ikililerin derlenmesi. XAML dosyalarının, görüntülerinin ve diğer yönetilen kaynak nesne türlerinin BAML formu, uydu kaynak derlemesine katıştırılır. Bu, diğer dillere yerelleştirilebilir veya yerelleştirme gerekli olmadığında ana derlemedir.

> [!NOTE]
> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar dize tabloları, görüntüleri ve benzeri tüm [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)]CLR kaynaklarını destekler.

<a name="building_localizable_apps"></a>
### <a name="building-localizable-applications"></a>Yerelleştirilebilir uygulamalar oluşturma
 Yerelleştirme, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] farklı kültürlere uyarlanmasıdır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir uygulamayı yerelleştirilebilir hale getirmek için, geliştiricilerin tüm yerelleştirilebilir kaynakları bir kaynak derlemesinde oluşturması gerekir. Kaynak derlemesi farklı dillere yereldir ve arka plan kodu, yüklemek için kaynak yönetimi API kullanır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir uygulama için gerekli dosyalardan biri bir proje dosyasıdır (. proj). Uygulamanızda kullandığınız tüm kaynaklar proje dosyasına eklenmelidir. Bir. csproj dosyasından aşağıdaki örnek bunun nasıl yapılacağını gösterir.

```xml
<Resource Include="data\picture1.jpg"/>
<EmbeddedResource Include="data\stringtable.en-US.restext"/>
```

 Uygulamanızdaki bir kaynağı kullanmak için bir <xref:System.Resources.ResourceManager> oluşturun ve kullanmak istediğiniz kaynağı yükleyin. Aşağıdaki örnek bunun nasıl yapılacağını göstermektedir.

 [!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]

<a name="using_clickonce"></a>
## <a name="using-clickonce-with-localized-applications"></a>Yerelleştirilmiş uygulamalarla ClickOnce kullanma
 ClickOnce, Visual Studio 2005 ile birlikte gönderilecek yeni bir Windows Forms dağıtım teknolojisidir. Web uygulamalarının uygulama yükleme ve yükseltme yapmasına izin vermez. ClickOnce ile dağıtılan bir uygulama yerelleştirildiği zaman, yalnızca yerelleştirilmiş kültür üzerinde görüntülenebilir. Örneğin, dağıtılmış bir uygulama Japonca 'ya yerelleştirilir bu, yalnızca Ingilizce Windows üzerinde olmayan Japonca Microsoft Windows 'ta görüntülenebilir. Bu, Japonca kullanıcıların Windows 'un Ingilizce sürümünü çalıştırmasına yönelik yaygın bir senaryo olduğundan bir sorun oluşturur.

 Bu soruna yönelik çözüm, Nötr dil geri dönüş özniteliğini ayarlamadır. Uygulama geliştiricisi, isteğe bağlı olarak ana derlemeden kaynakları kaldırabilir ve belirli bir kültüre karşılık gelen bir uydu derlemesinde kaynakların bulunmamasını belirtebilir. Bu işlemi denetlemek için <xref:System.Resources.NeutralResourcesLanguageAttribute> kullanın. <xref:System.Resources.NeutralResourcesLanguageAttribute> sınıfının Oluşturucusu iki imzaya sahiptir ve bu, <xref:System.Resources.ResourceManager> geri dönüş kaynaklarını ayıklayacağı konumu belirtmek için bir <xref:System.Resources.UltimateResourceFallbackLocation> parametresi alır: ana derleme veya uydu bütünleştirilmiş kodu. Aşağıdaki örnek, özniteliğini nasıl kullanacağınızı gösterir. Son geri dönüş konumu için, kod, <xref:System.Resources.ResourceManager> ' ın şu anda yürütülmekte olan derlemenin dizininin "de" alt dizinindeki kaynakları aramaya neden olur.

```csharp
[assembly: NeutralResourcesLanguageAttribute(
    "de" , UltimateResourceFallbackLocation.Satellite)]
```

## <a name="see-also"></a>Ayrıca bkz.

- [WPF Genelleştirmesi ve Yerelleştirmesine Genel Bakış](wpf-globalization-and-localization-overview.md)
