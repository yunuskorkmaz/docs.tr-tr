---
title: Arka Plan Kod ve WPF İçindeki XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], code-behind
- code-behind files [WPF], XAML
ms.assetid: 9df6d3c9-aed3-471c-af36-6859b19d999f
ms.openlocfilehash: 4a77060661cb0d71b0209cbcdeba23ffc2c6e5c7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59088581"
---
# <a name="code-behind-and-xaml-in-wpf"></a>Arka Plan Kod ve WPF İçindeki XAML
<a name="introduction"></a> Arka plan kod biçimlendirme tanımlı nesneler ile birleştirilen kodu açıklamak için kullanılan bir terim olduğu durumlarda bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfasıdır biçimlendirme derlenmiş. Bu konuda, arka plan kod gereksinimleri yanı sıra bir kod için alternatif satır içi kod mekanizması açıklanmaktadır [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
-   [Önkoşullar](#Prerequisites)  
  
-   [Arka plan kod ve XAML dili](#codebehind_and_the_xaml_language)  
  
-   [Arka plan kod, olay işleyicisi ve kısmi sınıf gereksinimleri ' WPF'de](#Code_behind__Event_Handler__and_Partial_Class)  
  
-   [x: Code](#x_Code)  
  
-   [Satır içi kod sınırlamaları](#Inline_Code_Limitations)  
  
<a name="Prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuda, okuduğunuz varsayılır [XAML genel bakış (WPF)](xaml-overview-wpf.md) ve bazı temel bilgiye sahip [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] ve nesne yönelimli programlama.  
  
<a name="codebehind_and_the_xaml_language"></a>   
## <a name="code-behind-and-the-xaml-language"></a>Arka plan kod ve XAML dili  
 XAML dil biçimlendirme dosyalarıyla, biçimlendirme dosyası tarafından kod dosyaları ilişkilendirilecek olanaklı kılan dil düzeyi özellikleri içerir. Özellikle, XAML dili dil özellikleri tanımlar [x: Class yönergesi](../../xaml-services/x-class-directive.md), [x: Subclass yönergesi](../../xaml-services/x-subclass-directive.md), ve [x: ClassModifier yönergesi](../../xaml-services/x-classmodifier-directive.md). Tam kod üretme ve işaretleme ve kod, tümleştirme ne XAML dili belirtir bir parçası değil. Kodu tümleştirmek nasıl belirlemek için WPF gibi çerçeveleri kadar sola, XAML uygulama ve programlama modelleri ve yapı kullanmak için Eylemler veya diğer destek nasıl tüm bu gerektirir.  
  
<a name="Code_behind__Event_Handler__and_Partial_Class"></a>   
## <a name="code-behind-event-handler-and-partial-class-requirements-in-wpf"></a>Arka plan kod, olay işleyicisi ve kısmi sınıf gereksinimleri ' WPF'de  
  
-   Kısmi sınıf kök öğe yedekler türünden türetilmesi gerekir.  
  
-   Altında biçimlendirmesi derleme yapı eylemleri varsayılan davranışını türetme arka plan kod tarafında kısmi sınıf tanımında boş bırakabilirsiniz, unutmayın. Bunu belirtilmemiş olsa bile derlenen sonuçtaki sayfa kökünün yedekleme türünün kısmi bir sınıf için temel olarak varsayar. Ancak, bu davranışına güvenmek en iyi yöntem değildir.  
  
-   Gerideki kod yazma olay işleyicileri örnek yöntemleri olmalıdır ve statik yöntemler olamaz. Bu yöntemler tarafından kısmi bir sınıf tarafından tanımlanan CLR ad alanı içinde tanımlanmalıdır `x:Class`. İstemek için bir olay işleyicisi adı uygun edilemez bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] olay kablolama farklı sınıf kapsamı içinde bir olay işleyicisi aramak için işlemci.  
  
-   İşleyici yedekleme türü sistemindeki uygun olay için temsilci eşleşmelidir.  
  
-   Microsoft Visual Basic dili için özellikle, dile özgü kullanabileceğiniz `Handles` örnekler ve öznitelikleri ile işleyicileri eklemek yerine işleyici bildirimde, olaylara işleyiciler ilişkilendirmek için anahtar sözcüğü [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Ancak, bu tekniği bazı sınırlamalar nedeniyle sahip `Handles` anahtar sözcüğü belirli özelliklerin tümünü destekleyemez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] gibi belirli bir olay sistemi yönlendirilmiş olay senaryoları veya ekli olaylar. Ayrıntılar için bkz [Visual Basic ve WPF olay işleme](visual-basic-and-wpf-event-handling.md).  
  
<a name="x_Code"></a>   
## <a name="xcode"></a>x: Code  
 [x: Code](../../xaml-services/x-code-intrinsic-xaml-type.md) yönerge bir öğenin tanımlandığı [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Bir `x:Code` yönergesi öğesi, satır içi programlama kodu içerebilir. Satır içi olarak tanımlanan kod ile etkileşim kurabilir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aynı sayfa üzerinde. Aşağıdaki örnek, satır içi C# kodunu gösterir. Kod içinde olduğuna dikkat edin `x:Code` öğesi ve kod tarafından alınmalıdır `<CDATA[`... `]]>` içeriğini kaçış [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)], böylece bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci (ya da yorumlama [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] şema veya [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] şema) içeriği yorumlamak denemez tam anlamıyla olarak [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)].  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithInlineCode](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page4.xaml#buttonwithinlinecode)]  
  
<a name="Inline_Code_Limitations"></a>   
## <a name="inline-code-limitations"></a>Satır içi kod sınırlamaları  
 Engelleme veya satır içi kod kullanımını sınırlama düşünmelisiniz. Mimari ve kodlama felsefesi bakımından, biçimlendirme ve arka plan kod arasında ayrımları Tasarımcısı ve geliştirici rolleri çok daha farklı tutar. Her zaman içinde yazıyorsanız daha teknik bir düzeyde için satır içi kod yazdığınız kod yazmak garip olabilir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kısmi sınıf oluşturulur ve varsayılan XML ad alanı eşlemeleri yalnızca kullanabilirsiniz. Ekleme yapamazsınız çünkü `using` deyimleri, tam olarak nitelemeniz gerekir birçok [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] yaptığınız çağırır. Varsayılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] eşlemeleri dahil tümü değil en [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] bulunan ad alanlarını [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] derlemeler; türleri ve üyeleri bir CLR ad içinde yer alan çağrıları tam olarak nitelemek gerekir. Kısmi sınıf dışında herhangi bir şey de satır içi kod tanımlayamazsınız ve tüm kullanıcı kodu varlıkları başvuru olarak bir üye veya değişken üretilen kısmi sınıf içinde bulunmalıdır. Dil belirli programlama gibi diğer özelliklerin makroları veya `#ifdef` genel değişkenler veya yapı değişkenleri karşı da kullanılabilir değil. Daha fazla bilgi için [x: Code iç XAML türü](../../xaml-services/x-code-intrinsic-xaml-type.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XAML'ye Genel Bakış (WPF)](xaml-overview-wpf.md)
- [x:Code İç XAML Türü](../../xaml-services/x-code-intrinsic-xaml-type.md)
- [WPF Uygulaması Derleme](../app-development/building-a-wpf-application-wpf.md)
- [Ayrıntılı XAML Sözdizimi](xaml-syntax-in-detail.md)
