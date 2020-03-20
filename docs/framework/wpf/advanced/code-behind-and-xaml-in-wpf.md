---
title: Kod Arkası ve XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], code-behind
- code-behind files [WPF], XAML
ms.assetid: 9df6d3c9-aed3-471c-af36-6859b19d999f
ms.openlocfilehash: 32283d5b81bf92999a97711ded13a8b533ae3028
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145351"
---
# <a name="code-behind-and-xaml-in-wpf"></a>Arka Plan Kod ve WPF İçindeki XAML
<a name="introduction"></a>Kod arkası, bir sayfa biçimlendirme derlendiğinde biçimlendirme tanımlı nesnelerle birleşen kodu tanımlamak için kullanılan bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] terimdir. Bu konu, kod arkası gereksinimlerinin yanı sıra kod için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]alternatif bir satır içi kod mekanizmasını da açıklar.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
- [Önkoşullar](#Prerequisites)  
  
- [Kod Arkası ve XAML Dili](#codebehind_and_the_xaml_language)  
  
- [WPF'de Kod Arkası, Olay İşleyicisi ve Kısmi Sınıf Gereksinimleri](#Code_behind__Event_Handler__and_Partial_Class)  
  
- [x:Kod](#x_Code)  
  
- [Satır Satır Dalasınırlamaları](#Inline_Code_Limitations)  
  
<a name="Prerequisites"></a>
## <a name="prerequisites"></a>Önkoşullar  
 Bu konu, [XAML Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md) okudum ve CLR ve nesne yönelimli programlama bazı temel bilgilere sahip varsayar.  
  
<a name="codebehind_and_the_xaml_language"></a>
## <a name="code-behind-and-the-xaml-language"></a>Kod Arkası ve XAML Dili  
 XAML dili, kod dosyalarını biçimlendirme dosyası tarafından işaretleme dosyalarıyla ilişkilendirmemi mümkün hale getiren dil düzeyinde özellikler içerir. Özellikle, XAML dili dil özelliklerini tanımlar [x:Sınıf Yönergesi](../../../desktop-wpf/xaml-services/xclass-directive.md), [x:Alt Sınıf Yönergesi](../../../desktop-wpf/xaml-services/xsubclass-directive.md), ve [x:ClassModifier Yönergesi](../../../desktop-wpf/xaml-services/xclassmodifier-directive.md). Kodun tam olarak nasıl üretilmesi gerektiği ve biçimlendirme ve kodun nasıl tümleştirilecek olması XAML dilinin belirttiği bir parçası değildir. Kodun nasıl tümleştirilen, uygulama ve programlama modellerinde XAML'nin nasıl kullanılacağını ve tüm bunların gerektirdiği yapı eylemleri veya diğer desteği belirlemek WPF gibi çerçevelere bırakılır.  
  
<a name="Code_behind__Event_Handler__and_Partial_Class"></a>
## <a name="code-behind-event-handler-and-partial-class-requirements-in-wpf"></a>WPF'de Kod Arkası, Olay İşleyicisi ve Kısmi Sınıf Gereksinimleri  
  
- Kısmi sınıf, kök öğesini destekleyen türden türemelidir.  
  
- Biçimlendirme derleme yapı eylemlerinin varsayılan davranışı altında, türetmeyi kod arkası tarafındaki kısmi sınıf tanımında boş bırakabileceğinizi unutmayın. Derlenen sonuç, belirtilmese bile sayfa kökünü destekleyen türü kısmi sınıfın temeli olarak kabul eder. Ancak, bu davranışa güvenmek en iyi yöntem değildir.  
  
- Kod arkasında yazdığınız olay işleyicileri örnek yöntemleri olmalıdır ve statik yöntemler olamaz. Bu yöntemler, CLR ad alanı içinde kısmi sınıf `x:Class`tarafından tanımlanmalıdır. Olay işleyicisinin adını, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemciye farklı bir sınıf kapsamı içinde olay kablolama için olay işleyicisi aramasını öğretmek için nitelendiremezsiniz.  
  
- İşleyici, destek türü sisteminde uygun olay için temsilciyle eşleşmelidir.  
  
- Özellikle Microsoft Visual Basic dili için, işleyicileri işleyicileri 'deki özniteliklere `Handles` [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]eklemek yerine, işleyicileri örneklerle ve olaylarla ilişkilendirmek için dile özgü anahtar sözcüğü kullanabilirsiniz. Ancak, `Handles` anahtar kelime belirli yönlendirilmiş olay senaryoları veya ekli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olaylar gibi olay sisteminin tüm belirli özelliklerini destekleyemediğinden, bu tekniğin bazı sınırlamaları vardır. Ayrıntılar için [Visual Basic ve WPF Olay Yönetimi'ne](visual-basic-and-wpf-event-handling.md)bakın.  
  
<a name="x_Code"></a>
## <a name="xcode"></a>x:Kod  
 [x:Kod,](../../../desktop-wpf/xaml-services/xcode-intrinsic-xaml-type.md) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Bir `x:Code` yönerge öğesi satır içinde programlama kodu içerebilir. Satır içinde tanımlanan kod, aynı [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfada bulunanla etkileşimkurabilir. Aşağıdaki örnek, sıralı C# kodunu göstermektedir. Kodun öğenin `x:Code` içinde olduğuna ve kodun `<CDATA[`... `]]>` xml için içeriğini kaçmak için, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] böylece bir işlemci [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (şema [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] veya şema yorumlama) kelimenin tam anlamıyla XML olarak içeriğini yorumlamak için çalışacağız.  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithInlineCode](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page4.xaml#buttonwithinlinecode)]  
  
<a name="Inline_Code_Limitations"></a>
## <a name="inline-code-limitations"></a>Satır Satır Dalasınırlamaları  
 Satır kodu kullanmaktan kaçınmayı veya sınırlamayı düşünmelisiniz. Mimarlık ve kodlama felsefesi açısından, biçimlendirme ve kod arkası arasındaki ayrımı sürdürmek tasarımcı ve geliştirici rollerini çok daha farklı tutar. Daha teknik bir düzeyde, satır altı kod için yazdığınız kod yazmak zor olabilir, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] çünkü her zaman oluşturulan kısmi sınıfa yazıyorsunuz ve yalnızca varsayılan XML ad alanı eşlemelerini kullanabilirsiniz. İfade ekleyemediğiniz `using` için, yaptığınız API çağrılarının çoğunu tam olarak nitelemelisiniz. Varsayılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] eşlemeler [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] derlemelerde bulunan tüm CLR ad alanlarını içermez; diğer CLR ad alanlarında bulunan türlere ve üyelere yapılan aramaları tam olarak nitelemek zorunda kalmaktadır. Satır içi kodda kısmi sınıfın ötesinde hiçbir şey tanımlayamazsınız ve başlatınıza başlatınız olan tüm kullanıcı kodu varlıkları, oluşturulan kısmi sınıf içinde bir üye veya değişken olarak var olmalıdır. Makrolar veya genel değişkenler veya `#ifdef` yapı değişkenleri gibi diğer dile özgü programlama özellikleri de kullanılamaz. Daha fazla bilgi için [bkz: x:Code Intrinsic XAML Türü.](../../../desktop-wpf/xaml-services/xcode-intrinsic-xaml-type.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XAML'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [x:Code İç XAML Türü](../../../desktop-wpf/xaml-services/xcode-intrinsic-xaml-type.md)
- [WPF Uygulaması Derleme](../app-development/building-a-wpf-application-wpf.md)
- [Ayrıntılı XAML Sözdizimi](xaml-syntax-in-detail.md)
