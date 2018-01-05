---
title: "WPF için Genelleştirme"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-wpf
ms.topic: article
helpviewer_keywords:
- XAML [WPF], international user interface
- XAML [WPF], globalization
- international user interface [WPF], XAML
- globalization [WPF]
ms.assetid: 4571ccfe-8a60-4f06-9b37-7ac0b1c2d10f
caps.latest.revision: "35"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e6f39d40284e6212715d85fece545e653ff2e60a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="globalization-for-wpf"></a>WPF için Genelleştirme
Bu konuda yazarken bilmeniz gereken sorunlar açıklanır [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] küresel pazarda uygulamaları. Genelleştirme programlama öğeleri tanımlanan [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] içinde `System.Globalization`.  
  

  
<a name="xaml_globalization"></a>   
## <a name="xaml-globalization"></a>XAML Genelleştirme  
 [!INCLUDE[TLA#tla_xaml#initcap](../../../../includes/tlasharptla-xamlsharpinitcap-md.md)]dayanır [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] ve içinde tanımlanan Genelleştirme desteğinden yararlanır [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] belirtimi. Aşağıdaki bölümlerde bazı açıklanmaktadır [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bilincinde olmanız gereken özellikleri.  
  
<a name="char_reference"></a>   
### <a name="character-references"></a>Karakter başvuruları  
UTF16 kod birimi belirli bir karakter başvurusu verir [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] temsil eder, ondalık veya onaltılık karakter. Aşağıdaki örnek, KIPTİ büyük harf YATAY ya da 'Ϩ' için bir ondalık karakter başvurusu gösterir:

```
&#1000;
```

Aşağıdaki örnekte bir onaltılı karakter başvurusunu gösterir. Olan bildirimi bir **x** onaltılık önünde.

```
&#x3E8;
```

<a name="encoding"></a>   
### <a name="encoding"></a>Kodlama  
 Tarafından desteklenen kodlama [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] olan [!INCLUDE[TLA#tla_ascii](../../../../includes/tlasharptla-ascii-md.md)], [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] UTF-16 ve UTF-8. Kodlama deyimi başındadır [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] belge. Kodlama özniteliği var ve bayt sırası yoksa UTF-8'e ayrıştırıcı varsayılan olarak ayarlanır. UTF-8 ve UTF-16 tercih edilen kodlamaları desteklenmektedir. UTF-7 desteklenmez. Aşağıdaki örnek, bir UTF-8 kodlaması belirtmek gösterilmiştir bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyası.  
  
```  
?xml encoding="UTF-8"?  
```  
  
<a name="lang_attrib"></a>   
### <a name="language-attribute"></a>Language özniteliği  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]kullanan [XML: lang](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md) bir öğenin dil özniteliğini göstermek için.  Yararlanmak için <xref:System.Globalization.CultureInfo> sınıfı, dil öznitelik değeri tarafından önceden tanımlanmış kültür adlarından biri olması gerekir <xref:System.Globalization.CultureInfo>. [XML: lang](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md) (tarafından XML kuralları, bağımlılık özelliği devralma nedeniyle gerekmez) öğe ağacında devralınabilir ve açıkça atanmamışsa, varsayılan değer boş bir dizedir.  
  
 Language özniteliği Portekizce belirtmek için çok kullanışlıdır. Örneğin, Fransızca farklı yazımı, dağarcığı ve telaffuz Fransa, Quebec, Belçika ve İsviçre ' var. Çince, Japonca ve Korece kod noktaları ayrıca paylaşmak [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)], ancak kavramsal şekiller farklıdır ve farklı yazı tipleri kullanın.  
  
 Aşağıdaki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örnek kullanır `fr-CA` language özniteliği Kanada Fransızca belirtin.  
  
```xml  
<TextBlock xml:lang="fr-CA">Découvrir la France</TextBlock>  
```  
  
<a name="unicode"></a>   
### <a name="unicode"></a>Unicode  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]Tüm destekler [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] yedekleri dahil olmak üzere özellikleri. Karakter kümesi eşlenebilir sürece [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)], desteklenmiyor. Örneğin, Çince, Japonca ve Kore dili (CFK) uzantısı A ve B eşlenir ve çiftler bazı karakterler GB18030 sunar, bu nedenle tamamen desteklenir. A [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama kullanabileceğiniz <xref:System.Globalization.StringInfo> temsilci çiftleri yüklü olup olmadığını anlamak veya birleştirme karakterlerine dizeleri işlemek için.  
  
<a name="design_intl_ui_with_xaml"></a>   
## <a name="designing-an-international-user-interface-with-xaml"></a>XAML uluslararası kullanıcı arabirimiyle tasarlama  
 Bu bölümde açıklanmıştır [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] uygulama yazarken düşünmeniz gereken özellikleri.  
  
<a name="intl_text"></a>   
### <a name="international-text"></a>Uluslararası metin  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]tümü için yerleşik işleme içerir [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] yazı sistemlerinde desteklenir.  
  
 Aşağıdaki komut dosyaları şu anda desteklenir:  
  
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
  
-   Laos  
  
-   Latin  
  
-   Malayalam dili  
  
-   Moğolca  
  
-   Odia  
  
-   Süryanice  
  
-   Tamil dili  
  
-   Telugu dili  
  
-   Thaana alfabesi  
  
-   Tay dili *  
  
-   Tibet dili  
  
 * Bu görünen serbest bırakır ve Tay dili metnini düzenleme desteklenir; Sözcük bölünmesi desteklenmez.  
  
 Aşağıdaki komut dosyaları şu anda desteklenmez:  
  
-   Khmer dili  
  
-   Eski Hangul Kore dili  
  
-   Myanmar  
  
-   Sinhali dili  
  
 Tüm yazı sistemi altyapıları Destek [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] yazı tipi. [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)]yazı tipleri içerebilir [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] daha iyi uluslararası ve Gelişmiş tipografik yazı tipleri tasarlamak için yazı tipi oluşturucularını etkinleştiren Düzen tabloları. [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] Yazı tipi Düzen tabloları metin düzenini geliştirmek metin işleme uygulamalarını etkinleştirme karakter kısaltmaları, karakter konumlandırma, düzeltme ve temel konumlandırma, ilgili bilgiler içerir.  
  
 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)]yazı tipleri izin büyük karakter işlenmesini ayarlar kullanarak [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] kodlama. Bu tür kodlama geniş uluslararası destek de tipografik karakter türevleri ettirilmesi sağlar.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]metin işleme tarafından desteklenir [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)] çözümleme bağımsızlığı destekleyen alt piksel teknolojisi. Bu önemli ölçüde okunabilirliği artırır ve tüm betikler için yüksek kaliteli dergi stili belgelerini destekleme özelliği sağlar.  
  
<a name="intl_layout"></a>   
### <a name="international-layout"></a>Uluslararası düzeni  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Yatay desteklemek için çok uygun bir yol, çift yönlü ve dikey düzenleri sağlar. Sunum çerçevesinde <xref:System.Windows.FrameworkElement.FlowDirection%2A> özelliği düzeni tanımlamak için kullanılabilir. Akış yönü modelleri şunlardır:  
  
-   *LeftToRight* -Latin, Doğu Asya ve benzeri için yatay düzen.  
  
-   *RightToLeft* -Arapça, İbranice ve benzeri için çift yönlü.  
  
<a name="developing_localizable_apps"></a>   
## <a name="developing-localizable-applications"></a>Yerelleştirilebilir Uygulamalar Geliştirme  
 Genel tüketim için bir uygulama yazdığınızda uygulama yerelleştirilebilir göz önünde bulundurmanız. Aşağıdaki konuları göz önünde bulundurmanız gerekenler noktası.  
  
<a name="mui"></a>   
### <a name="multilingual-user-interface"></a>Çok Dilde Kullanıcı arabirimi  
 Çok Dilde Kullanıcı Arabirimi (MUI) bir [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] destek geçmek için [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] bir dilden diğerine. A [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama MUI desteklemek için bütünleştirilmiş kod modeli kullanır. Bir uygulama, dilden derlemeleri dile bağlı uydu kaynak derlemelerini içerir. Yönetilen giriş noktasıdır. Ana derleme EXE.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Kaynak yükleyicisi avantajlarından yararlanır [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)]ait kaynak araması ve geri dönüş desteklemek için Kaynak Yöneticisi. Birden çok dil uydu derlemeleri aynı ana bütünleştirilmiş kod ile çalışır. Yüklenen kaynak assembly bağlıdır <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> geçerli iş parçacığının.  
  
<a name="localizable_ui"></a>   
### <a name="localizable-user-interface"></a>Yerelleştirilebilir kullanıcı arabirimi  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]uygulamaları [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tanımlamak için kendi [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]geliştiricilerin özellikleri ve mantığı kümesiyle nesneleri hiyerarşisini belirtin olanak tanır. Birincil kullanımını [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] geliştirmek için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] herhangi bir hiyerarşi belirtmek için uygulamalar ancak kullanılabilir [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] nesneleri. Çoğu geliştiricilerin [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kendi uygulamanın belirtmek için [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ve bir programlama dili gibi kullandığınız [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] kullanıcı etkileşimi tepki vermek için.  
  
 Kaynak açısından, bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dile bağlı tanımlamak için tasarlanan dosya [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] bir kaynak öğesidir ve bu nedenle, son dağıtım biçimi uluslararası dilleri desteklemek için yerelleştirilebilir olmalıdır. Çünkü [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] olayları birçok işleyemez [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] uygulamalar bunu yapmak için kod blokları içerir. Daha fazla bilgi için bkz: [XAML genel bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md). Kod çıkarılır ve farklı ikili dosyalar içinde derlenir olduğunda bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya XAML BAML forma simgeleştirilmiş. XAML dosyaları, görüntüler ve diğer yönetilen kaynak nesne türlerini BAML biçiminde katıştırılmış diğer dillere yerelleştirilmesi, uydu kaynak assembly veya ana derleme yerelleştirme gerekli olmadığında.  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]uygulamaları destekleyen tüm [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)] [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] dize tabloları, görüntüler ve diğerleri de dahil olmak üzere kaynaklar.  
  
<a name="building_localizable_apps"></a>   
### <a name="building-localizable-applications"></a>Yerelleştirilebilir Uygulamalar Oluşturma  
 Yerelleştirme anlamına gelir uyarlamak bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] farklı kültürler için. Yapmak için bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama yerelleştirilebilir, geliştiricilerin yerelleştirilebilir tüm kaynakları kaynak derlemesine derlemeleri gerekir. Kaynak assembly farklı dillere yerelleştirilmiştir ve kaynak yönetimi arka plan kodu kullanır [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] yüklenemiyor. İçin gereken dosyalardan biri bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir proje dosyası (.proj) uygulamasıdır. Uygulamanızı kullanan tüm kaynakları proje dosyasında bulunması gerekir. .Csproj dosyasından alınan aşağıdaki örnekte bunun nasıl yapılacağı gösterilmektedir.  
  
```xml  
<Resource Include="data\picture1.jpg"/>  
<EmbeddedResource Include="data\stringtable.en-US.restext"/>  
```  
  
 Kullanmak için bir kaynak olarak uygulamanıza örneği bir <xref:System.Resources.ResourceManager> ve kullanmak istediğiniz kaynağı yüklenemiyor. Aşağıdaki örnek bunun nasıl yapılacağını göstermektedir.  
  
 [!code-csharp[LocalizationResources#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]  
  
<a name="using_clickonce"></a>   
## <a name="using-clickonce-with-localized-applications"></a>ClickOnce yerelleştirilmiş uygulamalarıyla kullanma  
 ClickOnce ile birlikte yeni bir Windows Forms dağıtım teknolojisi olan [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)]. Uygulama yükleme ve Web uygulamalarının yükseltilmesini sağlar. ClickOnce ile dağıtılan bir uygulama yerelleştirilmiş olduğunda yalnızca yerelleştirilmiş kültür üzerinde görüntülenebilir. Dağıtılan bir uygulama için Japonca yerelleştirilmiş ise, örneğin, bunu yalnızca üzerinde Japonca görüntülenebilir [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] İngilizce değil, [!INCLUDE[TLA2#tla_win](../../../../includes/tla2sharptla-win-md.md)]. Japonca kullanıcıların İngilizce sürümünü çalıştırması yaygın bir senaryo olduğundan bu bir sorun gösterir [!INCLUDE[TLA2#tla_win](../../../../includes/tla2sharptla-win-md.md)].  
  
 Bu sorun için çözüm dilden geri dönüş özniteliğini ayarlamaktır. Bir uygulama geliştiricisi isteğe bağlı olarak kaynakları ana bütünleştirilmiş koddan kaldırın ve kaynaklar için belirli bir kültür karşılık gelen bir uydu derlemesinde bulunabilir belirtin. Bu işlem kullanımı denetlemek için <xref:System.Resources.NeutralResourcesLanguageAttribute>. Oluşturucusunun <xref:System.Resources.NeutralResourcesLanguageAttribute> sınıfına sahip iki imzalar, bir alan bir <xref:System.Resources.UltimateResourceFallbackLocation> konumunu belirtmek için parametre nerede <xref:System.Resources.ResourceManager> geri dönüş kaynakları ayıklamak: ana derleme veya uydu derleme. Aşağıdaki örnek, özniteliğin nasıl kullanılacağını gösterir. Son geri dönüş konumu için kod neden <xref:System.Resources.ResourceManager> şu anda yürütülen bütünleştirilmiş dizininin "de" alt kaynakları aramak için.  
  
```  
[assembly: NeutralResourcesLanguageAttribute(  
    "de" , UltimateResourceFallbackLocation.Satellite)]  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF Genelleştirmesi ve Yerelleştirmesine Genel Bakış](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)
