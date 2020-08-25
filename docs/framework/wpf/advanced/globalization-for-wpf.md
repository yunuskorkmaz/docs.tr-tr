---
title: Genelleştirme
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], international user interface
- XAML [WPF], globalization
- international user interface [WPF], XAML
- globalization [WPF]
ms.assetid: 4571ccfe-8a60-4f06-9b37-7ac0b1c2d10f
ms.openlocfilehash: 2d7cf73e37fe8c4bbdbef3d356f1dbb8903815f3
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812334"
---
# <a name="globalization-for-wpf"></a>WPF için Genelleştirme
Bu konu başlığı altında, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] küresel pazara yönelik uygulamalar yazarken bilmeniz gereken sorunlar açıklanır. Genelleştirme programlama öğeleri ad alanında .NET içinde tanımlanmıştır <xref:System.Globalization> .

<a name="xaml_globalization"></a>
## <a name="xaml-globalization"></a>XAML Genelleştirme
 Extensible Application Markup Language (XAML), XML 'i temel alır ve XML belirtiminde tanımlanan Genelleştirme desteğinden yararlanır. Aşağıdaki bölümlerde, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bilmeniz gereken bazı özellikler açıklanır.

<a name="char_reference"></a>
### <a name="character-references"></a>Karakter başvuruları
Bir karakter başvurusu, ondalık ya da onaltılı olarak temsil ettiği belirli Unicode karakterinin UTF16 Code birimini verir. Aşağıdaki örnek, KıPTI büyük harfle veya ' Ϩ ' için ondalık bir karakter başvurusunu gösterir:

```xaml
&#1000;
```

Aşağıdaki örnekte, onaltılı bir karakter başvurusu gösterilmektedir. Onaltılık sayının önünde bir **x** olduğuna dikkat edin.

```xaml
&#x3E8;
```

<a name="encoding"></a>
### <a name="encoding"></a>Encoding
 Tarafından desteklenen kodlama [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ASCII, UNICODE UTF-16 ve UTF-8 ' dir. Encoding deyimleri belgenin başlangıcında bulunur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] . Kodlama özniteliği yoksa ve hiçbir bayt sırası yoksa, ayrıştırıcı varsayılan olarak UTF-8 ' i belirler. UTF-8 ve UTF-16, tercih edilen kodlamalardır. UTF-7 desteklenmez. Aşağıdaki örnek, bir dosyada UTF-8 kodlamasının nasıl belirtileceğini göstermektedir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] .

```xaml
?xml encoding="UTF-8"?
```

<a name="lang_attrib"></a>
### <a name="language-attribute"></a>Language özniteliği
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bir öğenin Language özniteliğini temsil etmek için [XML: lang](../../../desktop-wpf/xaml-services/xml-language-handling.md) kullanır.  Sınıfından yararlanmak için <xref:System.Globalization.CultureInfo> , Language özniteliği değeri tarafından önceden tanımlanan kültür adlarından biri olmalıdır <xref:System.Globalization.CultureInfo> . [XML: lang](../../../desktop-wpf/xaml-services/xml-language-handling.md) , öğe ağacında (bağımlılık özelliği devralımı nedeniyle DEĞIL, XML kuralları tarafından) devralınabilir ve açıkça atanmamışsa boş bir dize olur.

 Language özniteliği, dialarcts 'yi belirtmek için çok yararlıdır. Örneğin, Fransızca Fransa, Quebec, Belçika ve Isviçre 'de farklı yazım, sözlük ve telaffuz vardır. Ayrıca Çince, Japonca ve Korece kod noktalarını Unicode olarak paylaşır, ancak İdeografik biçimleri farklıdır ve tamamen farklı yazı tiplerini kullanır.

 Aşağıdaki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örnek, `fr-CA` Kanada Fransızcası belirtmek için Language özniteliğini kullanır.

```xaml
<TextBlock xml:lang="fr-CA">Découvrir la France</TextBlock>
```

<a name="unicode"></a>
### <a name="unicode"></a>Unicode
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Yedeklerin dahil olduğu tüm Unicode özelliklerini destekler. Karakter kümesi Unicode ile eşlenebilir olduğu sürece, desteklenir. Örneğin, GB18030 Çince, Japonca ve Kore dili (CFK) uzantısı A ve B ve vekil çiftleri ile eşlenen bazı karakterleri tanıtır, bu nedenle tam olarak desteklenmektedir. Bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama, <xref:System.Globalization.StringInfo> temsilci çiftleri mi yoksa birleştirme karakterleri mi olduğunu anlamak zorunda kalmadan dizeleri işlemek için kullanabilir.

<a name="design_intl_ui_with_xaml"></a>
## <a name="designing-an-international-user-interface-with-xaml"></a>XAML ile uluslararası bir kullanıcı arabirimi tasarlama
 Bu bölümde [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] , bir uygulamayı yazarken göz önünde bulundurmanız gereken özellikler açıklanmaktadır.

<a name="intl_text"></a>
### <a name="international-text"></a>Uluslararası metin
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , tüm Microsoft .NET Framework yazma sistemlerini destekleyen yerleşik işleme içerir.

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

 * Bu yayında Tay dilindeki metnin görüntülenmesi ve düzenlemesi desteklenir; sözcük bölünmesi değil.

 Şu betikler Şu anda desteklenmemektedir:

- Khmer

- Kore dili Eski Hangul

- Myanmar

- Sinhali

 Tüm yazma sistemi motorları OpenType yazı tiplerini destekler. OpenType yazı tipleri, yazı tipi oluşturucularının daha iyi uluslararası ve yüksek kaliteli tipografik yazı tiplerini tasarlamasını sağlayan OpenType Düzen tablolarını içerebilir. OpenType yazı tipi düzen tabloları, metin düzenini geliştirmek için metin işleme uygulamalarını etkinleştiren glif değiştirmeleri, glif konumlandırma, gerekçe ve temel konumlandırma hakkında bilgiler içerir.

 OpenType yazı tipleri, Unicode kodlaması kullanarak büyük karakter kümelerinin işlenmesine izin verir. Bu tür bir kodlama, uluslararası ve tipografik glif çeşitleri için geniş uluslararası destek sunar.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] metin işleme, çözüm bağımsızlığını destekleyen Microsoft ClearType alt piksel teknolojisi tarafından desteklenmektedir. Bu, okunabilirliği önemli ölçüde artırır ve tüm betikler için yüksek kaliteli dergi stil belgelerini destekleme yeteneği sağlar.

<a name="intl_layout"></a>
### <a name="international-layout"></a>Uluslararası düzen
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Yatay, çift yönlü ve dikey düzenleri desteklemek için çok kullanışlı bir yol sağlar. Sunum çerçevesinde, <xref:System.Windows.FrameworkElement.FlowDirection%2A> özelliği düzeni tanımlamak için kullanılabilir. Akış yönü desenleri şunlardır:

- Latin, Doğu Asya ve benzeri için *Solttoright* -yatay düzeni.

- *RightToLeft* -Arapça, İbranice ve diğerleri için çift yönlü.

<a name="developing_localizable_apps"></a>
## <a name="developing-localizable-applications"></a>Yerelleştirilebilir uygulamalar geliştirme
 Küresel tüketim için bir uygulama yazdığınızda, uygulamanın yerelleştirilebilir olması gerektiğini aklınızda bulundurmanız gerekir. Aşağıdaki konular göz önünde bulundurmanız gereken noktaları işaret etmektedir.

<a name="mui"></a>
### <a name="multilingual-user-interface"></a>Çok dilli kullanıcı arabirimi
 Çok dilli kullanıcı arabirimleri (MUI), tek bir dilden diğerine geçiş yapmak için Microsoft desteği sağlar. Bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama, MUI 'yi desteklemek için derleme modelini kullanır. Tek bir uygulama dilden bağımsız derlemeler ve dile bağlı uydu kaynak derlemeleri içerir. Giriş noktası yönetilen bir. EXE ana derlemede.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kaynak yükleyicisi, kaynak aramasını ve geri dönüşü desteklemek için Framework 'ün Resource Manager 'ın avantajlarından yararlanır. Birden çok dil uydu derlemesi aynı ana derlemeyle çalışır. Yüklenen kaynak bütünleştirilmiş kodu, <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> geçerli iş parçacığının öğesine bağlıdır.

<a name="localizable_ui"></a>
### <a name="localizable-user-interface"></a>Yerelleştirilebilir kullanıcı arabirimi
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , bunları tanımlamak için kullanır [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] . [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] geliştiricilerin bir dizi özellik ve mantığa sahip nesneler hiyerarşisi belirlemesine izin verir. ' Nin birincil kullanımı [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , uygulamaları geliştirmektir, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ancak herhangi bir ortak dil çalışma zamanı (CLR) nesnesinin hiyerarşisini belirtmek için kullanılabilir. Çoğu geliştirici [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] kullanıcı etkileşimine yanıt vermek için uygulamasının uygulama ve C# gibi bir programlama dilini kullanması için kullanır.

 Bir görünüm kaynak noktasından, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dile bağlı bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] kaynak öğesidir ve bu nedenle son dağıtım biçimi Uluslararası dilleri desteklemek için yerelleştirilebilir olmalıdır. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]Olayları işleyemediği için birçok [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] uygulama, bunu yapmak için kod blokları içerir. Daha fazla bilgi için bkz. [xaml genel bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md). Bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Dosya, XAML 'ın BAML biçiminde simgeleştirilir, kod çıkarılır ve farklı ikili dosyalara derlenir. XAML dosyalarının, görüntülerinin ve diğer yönetilen kaynak nesne türlerinin BAML formu, uydu kaynak derlemesine katıştırılır. Bu, diğer dillere yerelleştirilebilir veya yerelleştirme gerekli olmadığında ana derlemedir.

> [!NOTE]
> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar dize tabloları, görüntüleri vb. dahil olmak üzere tüm FrameworkCLR kaynaklarını destekler.

<a name="building_localizable_apps"></a>
### <a name="building-localizable-applications"></a>Yerelleştirilebilir uygulamalar oluşturma
 Yerelleştirme, farklı kültürlere uyarlamanız anlamına gelir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] . Bir uygulamayı yerelleştirilebilir hale getirmek için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] geliştiricilerin tüm yerelleştirilebilir kaynakları bir kaynak derlemesinde oluşturması gerekir. Kaynak derlemesi farklı dillere yereldir ve arka plan kodu, yüklemek için kaynak yönetimi API kullanır. Bir uygulama için gerekli dosyalardan biri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir proje dosyasıdır (. proj). Uygulamanızda kullandığınız tüm kaynaklar proje dosyasına eklenmelidir. Bir. csproj dosyasından aşağıdaki örnek bunun nasıl yapılacağını gösterir.

```xml
<Resource Include="data\picture1.jpg"/>
<EmbeddedResource Include="data\stringtable.en-US.restext"/>
```

 Uygulamanızdaki bir kaynağı kullanmak için bir oluşturun <xref:System.Resources.ResourceManager> ve kullanmak istediğiniz kaynağı yükleyin. Aşağıdaki örnek bunun nasıl yapılacağını göstermektedir.

 [!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]

<a name="using_clickonce"></a>
## <a name="using-clickonce-with-localized-applications"></a>Yerelleştirilmiş uygulamalarla ClickOnce kullanma
 ClickOnce, Visual Studio 2005 ile birlikte gönderilecek yeni bir Windows Forms dağıtım teknolojisidir. Web uygulamalarının uygulama yükleme ve yükseltme yapmasına izin vermez. ClickOnce ile dağıtılan bir uygulama yerelleştirildiği zaman, yalnızca yerelleştirilmiş kültür üzerinde görüntülenebilir. Örneğin, dağıtılmış bir uygulama Japonca 'ya yerelleştirilir bu, yalnızca Ingilizce Windows üzerinde olmayan Japonca Microsoft Windows 'ta görüntülenebilir. Bu, Japonca kullanıcıların Windows 'un Ingilizce sürümünü çalıştırmasına yönelik yaygın bir senaryo olduğundan bir sorun oluşturur.

 Bu soruna yönelik çözüm, Nötr dil geri dönüş özniteliğini ayarlamadır. Uygulama geliştiricisi, isteğe bağlı olarak ana derlemeden kaynakları kaldırabilir ve belirli bir kültüre karşılık gelen bir uydu derlemesinde kaynakların bulunmamasını belirtebilir. Bu işlemi denetlemek için öğesini kullanın <xref:System.Resources.NeutralResourcesLanguageAttribute> . Sınıfının Oluşturucusu, <xref:System.Resources.NeutralResourcesLanguageAttribute> <xref:System.Resources.UltimateResourceFallbackLocation> geri dönüş kaynaklarını Ayıklanacak konumu belirtmek için bir parametre alan iki imzaya sahiptir <xref:System.Resources.ResourceManager> : ana derleme veya uydu bütünleştirilmiş kodu. Aşağıdaki örnek, özniteliğini nasıl kullanacağınızı gösterir. Son geri dönüş konumu için, kod, <xref:System.Resources.ResourceManager> Şu anda yürütülmekte olan derlemenin dizininin "de" alt dizinindeki kaynakları aramaya neden olur.

```csharp
[assembly: NeutralResourcesLanguageAttribute(
    "de" , UltimateResourceFallbackLocation.Satellite)]
```

## <a name="see-also"></a>Ayrıca bkz.

- [WPF Genelleştirmesi ve Yerelleştirmesine Genel Bakış](wpf-globalization-and-localization-overview.md)
