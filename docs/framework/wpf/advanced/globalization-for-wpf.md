---
title: WPF için Genelleştirme
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], international user interface
- XAML [WPF], globalization
- international user interface [WPF], XAML
- globalization [WPF]
ms.assetid: 4571ccfe-8a60-4f06-9b37-7ac0b1c2d10f
ms.openlocfilehash: 9a08fdeaa3517b1483af3f9958ad2db1c64648b8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59084173"
---
# <a name="globalization-for-wpf"></a>WPF için Genelleştirme
Bu konu yazarken farkında olmanız gereken sorunların tanıtır [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] küresel pazarda uygulamalar. Genelleştirme programlama öğeleri tanımlanan [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] içinde `System.Globalization`.

<a name="xaml_globalization"></a>
## <a name="xaml-globalization"></a>XAML Genelleştirme
 [!INCLUDE[TLA#tla_xaml#initcap](../../../../includes/tlasharptla-xamlsharpinitcap-md.md)] dayanır [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] ve içinde tanımlanan Genelleştirme desteğinden yararlanır [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] belirtimi. Aşağıdaki bölümlerde bazı açıklanmaktadır [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] farkında olmanız gereken özellikler.

<a name="char_reference"></a>
### <a name="character-references"></a>Karakter başvuruları
UTF16 kod birimi belirli bir karakter başvurusu verir [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] temsil ondalık veya onaltılı karakter. Aşağıdaki örnek, bir ondalık karakter başvurusu KOPTİKLERİ büyük harf YATAY ya da 'Ϩ' için gösterir:

```
&#1000;
```

Aşağıdaki örnek, bir onaltılık karakter başvurusu gösterir. Sahip olduğuna dikkat edin. bir **x** onaltılık sayı önünde.

```
&#x3E8;
```

<a name="encoding"></a>
### <a name="encoding"></a>Encoding
 Tarafından desteklenen kodlama [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] olan [!INCLUDE[TLA#tla_ascii](../../../../includes/tlasharptla-ascii-md.md)], [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] UTF-16 ve UTF-8. Kodlama bildirimi başlangıcında olup [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] belge. Kodlama özniteliği var ve bayt sırası varsa, ayrıştırıcının UTF-8 olarak varsayar. UTF-8 ve UTF-16 tercih edilen Kodlamalar var. UTF-7 desteklenmiyor. Aşağıdaki örnek, bir UTF-8 kodlamasını belirtmek gösterilmiştir bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya.

```
?xml encoding="UTF-8"?
```

<a name="lang_attrib"></a>
### <a name="language-attribute"></a>Language özniteliği
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kullanan [XML: lang](../../xaml-services/xml-lang-handling-in-xaml.md) öğenin dil özniteliğini temsil etmek için.  Yararlanmak için <xref:System.Globalization.CultureInfo> sınıfı dil özniteliği değeri tarafından önceden tanımlanmış kültür adlarının biri olması gerekir <xref:System.Globalization.CultureInfo>. [XML: lang](../../xaml-services/xml-lang-handling-in-xaml.md) devralınabilir öğe ağacında (tarafından XML kuralları, bağımlılık özelliği devralma nedeniyle gerekmez) ve açıkça atanmamışsa varsayılan değeri boş bir dizedir.

 Language özniteliği diyalektler belirtmek için kullanışlıdır. Örneğin, Fransızca, farklı yazım denetimi, sözlük ve Söyleniş Fransa, Quebec, Belçika, ve İsviçre vardır. Ayrıca kod noktaları Çince, Japonca ve Korece paylaşmak [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)], ancak kavramsal şekiller farklıdır ve bunlar tamamen farklı yazı tipleri kullanın.

 Aşağıdaki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örnekte `fr-CA` Kanada Fransızcası belirtmek için dil özniteliği.

```xml
<TextBlock xml:lang="fr-CA">Découvrir la France</TextBlock>
```

<a name="unicode"></a>
### <a name="unicode"></a>Unicode
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Tüm destekler [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] temsilciler dahil olmak üzere özellikleri. Karakter kümesi eşlenebilir sürece [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)], desteklenir. Örneğin, GB18030, Çince, Japonca ve Korece (CFK) uzantısı A ve B eşlenir ve çiftler bazı karakterler getirir, bu nedenle tam olarak desteklenir. A [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama kullanabileceğiniz <xref:System.Globalization.StringInfo> yedek çiftler sahip olup olmadığını anlamak veya birleştirme karakter dizeleri işlemek için.

<a name="design_intl_ui_with_xaml"></a>
## <a name="designing-an-international-user-interface-with-xaml"></a>Bir uluslararası kullanıcı arabirimi ile XAML tasarlama
 Bu bölümde açıklanmaktadır [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] bir uygulamayı yazarken göz önünde bulundurmanız gereken özellikler.

<a name="intl_text"></a>
### <a name="international-text"></a>Uluslararası metin
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tüm desteklenen Microsoft .NET Framework yazma sistemleri için yerleşik bir işlem içerir.

 Aşağıdaki komut, şu anda desteklenmektedir:

-   Arapça

-   Bengali

-   Devanagari

-   Kiril

-   Yunanca

-   Gucerat dili

-   Gurmuki

-   İbranice

-   Kavramsal betikler

-   Kannada dili

-   Lao dili

-   Latin

-   Malayalam dili

-   Moğolca

-   Odia

-   Süryanice

-   Tamil dili

-   Telugu dili

-   Thaana

-   Tay dili *

-   Tibet dili

 * Bu görünen bırakın ve Tay metni düzenleme desteklenir; sözcük bölme değil.

 Aşağıdaki komut, şu anda desteklenmemektedir:

-   Khmer

-   Eski Hangul Kore dili

-   Myanmar

-   Sinhala

 Tüm yazı sistemi destek altyapıları [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] yazı tipi. [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] yazı tipleri içerebilir [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] daha iyi uluslararası ve yüksek kaliteli tipografik yazı tipleri tasarlamak için yazı tipi oluşturucularını etkinleştiren Düzen tabloları. [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] Yazı tipi düzeni tablolar, metin düzenini iyileştirmek metin işleme uygulamalarını etkinleştirme glif değişimler, karakter konumlandırması, yaslama ve temel konumlandırma, ilgili bilgiler içerir.

 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] yazı tipleri izin büyük karakter işleme ayarlar kullanarak [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] kodlama. Böyle bir kodlama geniş uluslararası destek de tipografik karakter çeşitleri için etkinleştirir.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] metin işleme ile desteklenen [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)] çözünürlük bağımsızlığı destekleyen alt piksel teknolojisi. Bu önemli ölçüde okunabilirliği geliştirir ve yüksek kaliteli dergi stili belgeler için tüm betikleri olanağı sağlar.

<a name="intl_layout"></a>
### <a name="international-layout"></a>Uluslararası düzeni
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Yatay desteklemek için kullanışlı bir yol, çift yönlü ve dikey düzeni sağlar. Presentation Framework <xref:System.Windows.FrameworkElement.FlowDirection%2A> özelliği düzeni tanımlamak için kullanılabilir. Akış yönü modelleri şunlardır:

-   *LeftToRight* -Latin, Doğu Asya ve benzeri için yatay düzeni.

-   *RightToLeft* -Arapça, İbranice ve diğerleri için çift yönlü.

<a name="developing_localizable_apps"></a>
## <a name="developing-localizable-applications"></a>Yerelleştirilebilir Uygulamalar Geliştirme
 Genel kullanım için bir uygulama yazdığınızda uygulama yerelleştirilebilir akılda tutulması. Aşağıdaki konuları göz önünde bulundurulması gerekenler noktası.

<a name="mui"></a>
### <a name="multilingual-user-interface"></a>Çok dilli kullanıcı arabirimi
 Çok dilli kullanıcı arabirimi (MUI) bir [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] desteklemek için geçiş [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] bir dilden diğerine. A [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama MUI desteklemek için bütünleştirilmiş kod modeli kullanır. Bir uygulama dilden derlemeler ve bunun yanı sıra dile bağlı uydu kaynak derlemeleri içerir. Yönetilen bir giriş noktasıdır. EXE ana.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Kaynak yükleyici yararlanır [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)]ait kaynak araması ve geri dönüş desteklemek için Kaynak Yöneticisi. Birden çok dil uydu derlemeleri, aynı ana derleme ile çalışır. Yüklenen kaynak derlemesi bağımlı <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> geçerli iş parçacığının.

<a name="localizable_ui"></a>
### <a name="localizable-user-interface"></a>Yerelleştirilebilir kullanıcı arabirimi
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaları [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tanımlamak için kendi [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] özellikleri ve mantığı kümesiyle nesnelerin bir hiyerarşisini belirlemek geliştiriciler sağlar. Birincil kullanım alanının [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] geliştirmektir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] herhangi bir hiyerarşi belirtmek için uygulamalar, ancak kullanılabilir [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] nesneleri. Çoğu geliştirici [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] uygulama belirtmek için [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ve C# gibi bir programlama dili için kullanıcı etkileşimi tepki vermek için kullanın.

 Bir kaynak açısından, bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dile bağlı tanımlamak için tasarlanan dosya [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] kaynak öğesi ve bu nedenle, son dağıtım biçimi uluslararası dilleri desteklemek için yerelleştirilebilir olmalıdır. Çünkü [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] olayları birçok işleyemez [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] uygulamalar bunu yapmak için kod blokları içerir. Daha fazla bilgi için [XAML genel bakış (WPF)](xaml-overview-wpf.md). Kod çıkarılır ve farklı ikili dosyalar derlenir, bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya XAML BAML forma simgeleştirilmiş. XAML dosyaları, görüntüler ve diğer yönetilen kaynak nesne türlerini BAML formu katıştırıldığı diğer dillere yerelleştirilmesi, uydu kaynak derlemesi veya ana derleme yerelleştirme gerekli olmadığında.

> [!NOTE]
>  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamaları destekleyen tüm [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)][!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] dize tabloları, görüntüler ve diğerleri dahil olmak üzere kaynakları.

<a name="building_localizable_apps"></a>
### <a name="building-localizable-applications"></a>Yerelleştirilebilir Uygulamalar Oluşturma
 Yerelleştirme anlamına gelir uyum sağlamak bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] farklı kültürler için. Yapmak için bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yerelleştirilebilir geliştiricilerin gereken bir kaynağı derlemeye tüm yerelleştirilebilir kaynakları oluşturmak bir uygulama. Kaynak derlemesi farklı dilde yerelleştirilmiş olan ve kaynak yönetimi arka plan kod kullanır [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] yüklenemedi. İçin gerekli dosyaları birini bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir proje dosyası (.proj) uygulamasıdır. Uygulamanızda kullandığınız tüm kaynakları, proje dosyasında eklenmelidir. .Csproj dosyasını aşağıdaki örnekte, bunun nasıl yapılacağı gösterilmektedir.

```xml
<Resource Include="data\picture1.jpg"/>
<EmbeddedResource Include="data\stringtable.en-US.restext"/>
```

 Kullanılacak bir kaynak olarak uygulamanıza örneği bir <xref:System.Resources.ResourceManager> ve kullanmak istediğiniz kaynak yükleyin. Aşağıdaki örnek bunun nasıl yapılacağını göstermektedir.

 [!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]

<a name="using_clickonce"></a>
## <a name="using-clickonce-with-localized-applications"></a>ClickOnce yerelleştirilmiş uygulamalarıyla kullanma
 ClickOnce ile Visual Studio 2005 sevk edilir, yeni bir Windows Forms dağıtım teknolojisidir. Bu, uygulama yükleme ve Web uygulamalarının yükseltilmesini sağlar. ClickOnce ile dağıtılan bir uygulama yerelleştirilmiş yalnızca yerelleştirilmiş kültür üzerinde görüntülenebilir. Dağıtılan bir uygulama için Japonca yerelleştirilmiş ise, örneğin, bunu yalnızca Japonca üzerinde görüntülenebilir [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] İngilizce Windows üzerinde değil. Bu bir sorun oluşturur, çünkü Japonca kullanıcıların Windows İngilizce sürümünü çalıştırmak yaygın bir senaryodur.

 Bu sorunun çözümü dilden geri dönüş öznitelik ayarlıyor. İsteğe bağlı olarak bir uygulama geliştiricisi ana derlemesinden kaynakları kaldırmak ve kaynakların belirli bir kültüre karşılık gelen bir uydu derlemeye bulunabileceğini belirtin. Bu işlem kullanımını denetlemek için <xref:System.Resources.NeutralResourcesLanguageAttribute>. Oluşturucusuna <xref:System.Resources.NeutralResourcesLanguageAttribute> sınıfında süren iki imzaları bir <xref:System.Resources.UltimateResourceFallbackLocation> konumu belirtmek için parametre burada <xref:System.Resources.ResourceManager> geri dönüş kaynakları ayıklamak: ana derlemesine veya uydu derlemesine. Aşağıdaki örnek, öznitelik kullanma işlemini gösterir. Ultimate geri dönüş konumu için kod neden <xref:System.Resources.ResourceManager> şu anda çalıştırılan derlemenin dizin "de" alt kaynakları bulmak için.

```
[assembly: NeutralResourcesLanguageAttribute(
    "de" , UltimateResourceFallbackLocation.Satellite)]
```

## <a name="see-also"></a>Ayrıca bkz.

- [WPF Genelleştirmesi ve Yerelleştirmesine Genel Bakış](wpf-globalization-and-localization-overview.md)
