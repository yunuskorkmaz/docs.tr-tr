---
title: Arka Plan Kod ve WPF İçindeki XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], code-behind
- code-behind files [WPF], XAML
ms.assetid: 9df6d3c9-aed3-471c-af36-6859b19d999f
ms.openlocfilehash: 09d4f010ca53c5e3d2d9dede172e7ae2102261b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="code-behind-and-xaml-in-wpf"></a>Arka Plan Kod ve WPF İçindeki XAML
<a name="introduction"></a> Arka plan kodu biçimlendirme tanımlı nesneler ile birleştirilen kodu açıklamak için kullanılan bir terim olduğu durumlarda bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfası biçimlendirme derlenmiş. Bu konu, arka plan kodu için gereksinimler ve aynı zamanda kodu için bir alternatif satır içi kod mekanizmasının açıklar [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
-   [Önkoşulları](#Prerequisites)  
  
-   [Arka plan kod ve XAML dili](#codebehind_and_the_xaml_language)  
  
-   [Arka plan kodu, olay işleyicisi ve WPF parçalı sınıf gereksinimleri](#Code_behind__Event_Handler__and_Partial_Class)  
  
-   [x: Code](#x_Code)  
  
-   [Satır içi kod kısıtlamaları](#Inline_Code_Limitations)  
  
<a name="Prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuda, okuduğunuz varsayılır [XAML genel bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) ve bazı temel bilgiye sahip [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] ve nesne odaklı programlama.  
  
<a name="codebehind_and_the_xaml_language"></a>   
## <a name="code-behind-and-the-xaml-language"></a>Arka plan kod ve XAML dili  
 XAML dili biçimlendirme dosyalarından biçimlendirme dosyası tarafından kod dosyaları ilişkilendirmek olanaklı kılan dil düzeyi özellikleri içerir. Özellikle, XAML dili dil özelliklerini tanımlar [x: Class yönergesi](../../../../docs/framework/xaml-services/x-class-directive.md), [x: Subclass yönergesi](../../../../docs/framework/xaml-services/x-subclass-directive.md), ve [x: ClassModifier yönergesi](../../../../docs/framework/xaml-services/x-classmodifier-directive.md). Tam olarak kodu nasıl üretilen ve biçimlendirme ve kodun tümleştirme ne XAML dili belirtir. bir parçası değil. Kod tümleştirme belirlemek WPF gibi çerçeveleri kadar sola, uygulama ve programlama modelleri ve yapı XAML kullanmak için Eylemler veya diğer desteklemesi nasıl tüm bu gerektirir.  
  
<a name="Code_behind__Event_Handler__and_Partial_Class"></a>   
## <a name="code-behind-event-handler-and-partial-class-requirements-in-wpf"></a>Arka plan kodu, olay işleyicisi ve WPF parçalı sınıf gereksinimleri  
  
-   Parçalı sınıf kök öğesi yedekler türünden türetilmelidir.  
  
-   Biçimlendirme derleme yapı eylemlerinin varsayılan davranışını altında türetme arka plan kodu tarafında parçalı sınıf tanımı'nda boş bırakabilirsiniz olduğunu unutmayın. Bu belirtilmezse, derlenmiş sonuç sayfa kökünün yedekleme türünün parçalı sınıf için temel olarak varsayar. Ancak, bu davranışa güvenmek en iyi yöntem değildir.  
  
-   Arkasındaki kodda yazma olay işleyicileri örnek yöntemler olmalıdır ve statik yöntemler olamaz. Bu yöntemler tarafından tanımlanan CLR ad alanı içindeki parçalı sınıf tarafından tanımlanmalıdır `x:Class`. İstemek üzere bir olay işleyicisi adı hakkını kullanmaya devam eder bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci farklı sınıf kapsamı içindeki olay kablolama olay işleyicisi arayın.  
  
-   İşleyici yedekleme türü sistemindeki uygun olayı için temsilci eşleşmelidir.  
  
-   Microsoft Visual Basic dil için özellikle dile özgü kullanabileceğiniz `Handles` örnekleri ve öznitelikleri ile işleyicileri ekleme yerine işleyici bildiriminde olayları işleyicileri ilişkilendirmek için anahtar sözcüğü [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Ancak, bu teknik bazı sınırlamaları nedeniyle sahip `Handles` anahtar sözcüğü tüm belirli özelliklerini destekleyemez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] gibi belirli olay sistem yönlendirilmiş olay senaryoları veya ekli olaylar. Ayrıntılar için bkz [Visual Basic ve WPF olay işleme](../../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md).  
  
<a name="x_Code"></a>   
## <a name="xcode"></a>x: Code  
 [x: Code](../../../../docs/framework/xaml-services/x-code-intrinsic-xaml-type.md) yönerge öğesi tanımlanan [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Bir `x:Code` yönergesi öğesi, satır içi programlama kodu içerebilir. Satır içi olarak tanımlanan kod etkileşim kurabildikleri [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aynı sayfa üzerinde. Aşağıdaki örnek, satır içi C# kod gösterilmektedir. Kod içinde olduğuna dikkat edin `x:Code` öğesi ve kod tarafından alınmalıdır `<CDATA[`... `]]>` için içerik kaçınmak için [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)], böylece bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci (ya da yorumlama [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] şema veya [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] şema) içeriğini yorumlama denemez tam anlamıyla olarak [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)].  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithInlineCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page4.xaml#buttonwithinlinecode)]  
  
<a name="Inline_Code_Limitations"></a>   
## <a name="inline-code-limitations"></a>Satır içi kod kısıtlamaları  
 Önleme veya satır içi kod kullanımını sınırlama düşünmelisiniz. Mimari ve kodlama felsefesi açısından, biçimlendirme ve arka plan kodu arasında ayrım koruma tasarımcı ve geliştiricinin rollerini daha ayrı tutar. Her zaman içine yazıyorsanız olduğundan daha teknik bir düzeyde için satır içi kod yazmayı kod yazmak garip olabilir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] parçalı sınıf oluşturulur ve varsayılan XML ad alanı eşlemeleri yalnızca kullanabilirsiniz. Ekleyemezsiniz çünkü `using` deyimleri, gerekir tam olarak nitelemek birçok [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] yaptığınız çağrıları. Varsayılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] eşlemeleri dahil en ancak değil tüm [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] mevcut ad alanları [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] derlemeler; türleri ve diğer CLR ad içinde bulunan üye çağrıları tam olarak nitelemek gerekir. Parçalı sınıf dışında bir şey de satır içi kod tanımlayamaz ve tüm kullanıcı kodu varlıkları başvuru olarak bir üye veya değişken oluşturulan kısmi sınıf içinde bulunmalıdır. Dil belirli programlama gibi diğer özelliklerin makroları veya `#ifdef` genel değişkenler veya derleme değişkenleri karşı de kullanılamaz. Daha fazla bilgi için bkz: [x: Code iç XAML türü](../../../../docs/framework/xaml-services/x-code-intrinsic-xaml-type.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XAML'ye Genel Bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [x:Code İç XAML Türü](../../../../docs/framework/xaml-services/x-code-intrinsic-xaml-type.md)  
 [WPF Uygulaması Derleme](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)  
 [Ayrıntılı XAML Sözdizimi](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)
