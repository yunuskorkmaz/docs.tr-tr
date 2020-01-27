---
title: Arka plan kodu ve XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], code-behind
- code-behind files [WPF], XAML
ms.assetid: 9df6d3c9-aed3-471c-af36-6859b19d999f
ms.openlocfilehash: 212a37fb7fbcb7e66a669d96671333be793956df
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738096"
---
# <a name="code-behind-and-xaml-in-wpf"></a>Arka Plan Kod ve WPF İçindeki XAML
<a name="introduction"></a>Arka plan kodu, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bir sayfa biçimlendirme derlendiğinde, biçimlendirme tanımlı nesnelerle birleştirilen kodu tanımlayan bir terimdir. Bu konuda [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]kod için alternatif bir satır içi kod mekanizması ve arka plan kodu gereksinimleri açıklanmaktadır.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
- [Önkoşullar](#Prerequisites)  
  
- [Arka plan kodu ve XAML dili](#codebehind_and_the_xaml_language)  
  
- [WPF 'deki arka plan kod, olay Işleyicisi ve kısmi sınıf gereksinimleri](#Code_behind__Event_Handler__and_Partial_Class)  
  
- [x:Code](#x_Code)  
  
- [Satır içi kod sınırlamaları](#Inline_Code_Limitations)  
  
<a name="Prerequisites"></a>   
## <a name="prerequisites"></a>Prerequisites  
 Bu konu, [xaml 'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md) okuduğunuzu ve clr ve nesne odaklı programlama hakkında temel bilgiye sahip olduğunuzu varsayar.  
  
<a name="codebehind_and_the_xaml_language"></a>   
## <a name="code-behind-and-the-xaml-language"></a>Arka plan kodu ve XAML dili  
 XAML dili, biçimlendirme dosyası tarafındaki kod dosyalarını biçimlendirme dosyalarıyla ilişkilendirmeyi olanaklı kılan dil düzeyi özellikleri içerir. Özellikle XAML dili, [X:Class yönergesi](../../../desktop-wpf/xaml-services/xclass-directive.md), [x:alt sınıf yönergesi](../../../desktop-wpf/xaml-services/xsubclass-directive.md)ve [x:ClassModifier yönergesini](../../../desktop-wpf/xaml-services/xclassmodifier-directive.md)dil özelliklerini tanımlar. Kodun nasıl üretileceği, biçimlendirme ve kodun nasıl tümleştirileceği, XAML dilinin neyi belirttiği bir parçası değildir. Kodun nasıl tümleştirileceğini, uygulama ve programlama modellerinde XAML 'yi kullanmayı ve bunun gerektirdiği derleme eylemlerini veya diğer desteği öğrenmek için WPF gibi çerçevelere ayrıldınız.  
  
<a name="Code_behind__Event_Handler__and_Partial_Class"></a>   
## <a name="code-behind-event-handler-and-partial-class-requirements-in-wpf"></a>WPF 'deki arka plan kod, olay Işleyicisi ve kısmi sınıf gereksinimleri  
  
- Kısmi sınıf kök öğeyi yedekleyen türden türetilmelidir.  
  
- Biçimlendirme derlemesi oluşturma eylemlerinin varsayılan davranışı altında, türetme kodunu arka plan kod tarafında kısmi sınıf tanımında boş bırakabilirsiniz. Derlenmiş sonuç, belirtilmese de, sayfa kökünün yedekleme türünü kısmi sınıfın temeli olacak şekilde varsayar. Ancak, bu davranışa bağlı olarak en iyi yöntem değildir.  
  
- Arka planda yazdığınız olay işleyicileri örnek yöntemler olmalıdır ve statik yöntemler olamaz. Bu yöntemler, `x:Class`tarafından tanımlanan CLR ad alanı içindeki kısmi sınıf tarafından tanımlanmalıdır. Bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcinin, farklı bir sınıf kapsamındaki olay kablolaması için bir olay işleyicisini araması gerektiğini bildirmek üzere bir olay işleyicisinin adını niteleyemezsiniz.  
  
- İşleyici, yedekleme türü sistemindeki ilgili olay için temsilciyle eşleşmelidir.  
  
- Özel olarak Microsoft Visual Basic dili için, işleyicileri [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]özniteliklerle eklemek yerine, işleyicileri işleyici bildiriminde örnek ve olaylarla ilişkilendirmek için dile özgü `Handles` anahtar sözcüğünü kullanabilirsiniz. Ancak, `Handles` anahtar sözcüğü belirli yönlendirilmiş olay senaryoları veya ekli olaylar gibi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olay sisteminin tüm özelliklerini desteklemediğinden, bu teknik bazı sınırlamalara sahiptir. Ayrıntılar için bkz. [Visual Basic ve WPF olay işleme](visual-basic-and-wpf-event-handling.md).  
  
<a name="x_Code"></a>   
## <a name="xcode"></a>x:Code  
 [X:Code](../../../desktop-wpf/xaml-services/xcode-intrinsic-xaml-type.md) , [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]tanımlı bir Directive öğesidir. `x:Code` Directive öğesi, satır içi programlama kodu içerebilir. Satır içi tanımlı kod, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aynı sayfada etkileşim kurabilir. Aşağıdaki örnek, satır içi C# kodu gösterir. Kodun `x:Code` öğesinin içinde olduğuna ve kodun, bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcisinin ([!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] şemayı veya [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] şemasının yorumlanması) XML olarak, tam olarak XML olarak yorumlanmaya devam edebilmesi için, XML içeriğini kaçış`]]>` `<CDATA[`... ile çevrelendiğine dikkat edin.  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithInlineCode](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page4.xaml#buttonwithinlinecode)]  
  
<a name="Inline_Code_Limitations"></a>   
## <a name="inline-code-limitations"></a>Satır içi kod sınırlamaları  
 Satır içi kod kullanımının önlenmemesini veya sınırlandırmasını düşünmelisiniz. Mimari ve kodlama FI açısından, biçimlendirme ve arka plan arasındaki ayrımı korumak, tasarımcı ve geliştirici rollerinin çok daha belirgin kalmasını önler. Daha teknik bir düzeyde, her zaman [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] oluşturulan kısmi sınıfa yazmakta olduğunuzdan ve yalnızca varsayılan XML ad alanı eşlemelerini kullanabilmesi nedeniyle, satır içi kod için yazdığınız kod yazmak için çok fazla olabilir. `using` deyimleri ekleyemediği için, yaptığınız birçok API çağrısının çoğunu tam olarak nitelemeniz gerekir. Varsayılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] eşlemeleri, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] derlemelerinde bulunan tüm CLR ad alanlarını içermez; diğer CLR ad alanlarında bulunan türlere ve üyelere yönelik çağrıları tamamen nitelemeniz gerekir. Ayrıca, satır içi koddaki kısmi sınıfın ötesinde herhangi bir şey tanımlayamazsınız ve başvurmakta olduğunuz tüm Kullanıcı kodu varlıklarının, oluşturulan kısmi sınıf içinde bir üye veya değişken olarak mevcut olması gerekir. Makrolar veya genel değişkenlere veya derleme değişkenlerine karşı `#ifdef` gibi diğer dile özgü programlama özellikleri de kullanılamaz. Daha fazla bilgi için bkz. [X:Code IÇSEL xaml türü](../../../desktop-wpf/xaml-services/xcode-intrinsic-xaml-type.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XAML'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [x:Code İç XAML Türü](../../../desktop-wpf/xaml-services/xcode-intrinsic-xaml-type.md)
- [WPF Uygulaması Derleme](../app-development/building-a-wpf-application-wpf.md)
- [Ayrıntılı XAML Sözdizimi](xaml-syntax-in-detail.md)
