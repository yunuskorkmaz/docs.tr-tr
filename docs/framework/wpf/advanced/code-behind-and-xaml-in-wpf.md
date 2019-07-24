---
title: Arka Plan Kod ve WPF İçindeki XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], code-behind
- code-behind files [WPF], XAML
ms.assetid: 9df6d3c9-aed3-471c-af36-6859b19d999f
ms.openlocfilehash: acd8c9ff0a4ff718dba272958a3e63820bcf1354
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401615"
---
# <a name="code-behind-and-xaml-in-wpf"></a>Arka Plan Kod ve WPF İçindeki XAML
<a name="introduction"></a>Arka plan kodu, bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sayfa biçimlendirme derlendiğinde, biçimlendirme tanımlı nesneler ile birleştirilen kodu anlatmak için kullanılan bir terimdir. Bu konu, arka plan kod gereksinimlerinin yanı sıra içindeki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]kod için alternatif bir satır içi kod mekanizmasıyla ilgili gereksinimleri açıklamaktadır.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
- [Önkoşullar](#Prerequisites)  
  
- [Arka plan kodu ve XAML dili](#codebehind_and_the_xaml_language)  
  
- [WPF 'deki arka plan kod, olay Işleyicisi ve kısmi sınıf gereksinimleri](#Code_behind__Event_Handler__and_Partial_Class)  
  
- [x:Code](#x_Code)  
  
- [Satır içi kod sınırlamaları](#Inline_Code_Limitations)  
  
<a name="Prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konu, [xaml 'ye Genel Bakış (WPF)](xaml-overview-wpf.md) okuduğunuzu ve clr ve nesne odaklı programlama hakkında temel bilgiye sahip olduğunuzu varsayar.  
  
<a name="codebehind_and_the_xaml_language"></a>   
## <a name="code-behind-and-the-xaml-language"></a>Arka plan kodu ve XAML dili  
 XAML dili, biçimlendirme dosyası tarafındaki kod dosyalarını biçimlendirme dosyalarıyla ilişkilendirmeyi olanaklı kılan dil düzeyi özellikleri içerir. Özellikle XAML dili, [X:Class yönergesi](../../xaml-services/x-class-directive.md), [x:alt sınıf yönergesi](../../xaml-services/x-subclass-directive.md)ve [x:ClassModifier yönergesini](../../xaml-services/x-classmodifier-directive.md)dil özelliklerini tanımlar. Kodun nasıl üretileceği, biçimlendirme ve kodun nasıl tümleştirileceği, XAML dilinin neyi belirttiği bir parçası değildir. Kodun nasıl tümleştirileceğini, uygulama ve programlama modellerinde XAML 'yi kullanmayı ve bunun gerektirdiği derleme eylemlerini veya diğer desteği öğrenmek için WPF gibi çerçevelere ayrıldınız.  
  
<a name="Code_behind__Event_Handler__and_Partial_Class"></a>   
## <a name="code-behind-event-handler-and-partial-class-requirements-in-wpf"></a>WPF 'deki arka plan kod, olay Işleyicisi ve kısmi sınıf gereksinimleri  
  
- Kısmi sınıf kök öğeyi yedekleyen türden türetilmelidir.  
  
- Biçimlendirme derlemesi oluşturma eylemlerinin varsayılan davranışı altında, türetme kodunu arka plan kod tarafında kısmi sınıf tanımında boş bırakabilirsiniz. Derlenmiş sonuç, belirtilmese de, sayfa kökünün yedekleme türünü kısmi sınıfın temeli olacak şekilde varsayar. Ancak, bu davranışa bağlı olarak en iyi yöntem değildir.  
  
- Arka planda yazdığınız olay işleyicileri örnek yöntemler olmalıdır ve statik yöntemler olamaz. Bu yöntemlerin, tarafından `x:Class`tanımlanan clr ad alanı içindeki kısmi sınıf tarafından tanımlanması gerekir. Bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcinin, farklı bir sınıf kapsamındaki olay kablolaması için bir olay işleyicisini araması için bir olay işleyicisinin adını niteleyemezsiniz.  
  
- İşleyici, yedekleme türü sistemindeki ilgili olay için temsilciyle eşleşmelidir.  
  
- Özellikle Microsoft Visual Basic dili için, içindeki `Handles` [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]özniteliklere sahip işleyicileri eklemek yerine işleyicileri işleyici bildiriminde örnek ve olaylarla ilişkilendirmek için dile özgü anahtar sözcüğünü kullanabilirsiniz. Ancak, anahtar sözcüğü belirli yönlendirilmiş olay senaryoları veya ekli `Handles` olaylar gibi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olay sisteminin tüm özelliklerini destekleyemediği için bu teknik bazı sınırlamalara sahiptir. Ayrıntılar için bkz. [Visual Basic ve WPF olay işleme](visual-basic-and-wpf-event-handling.md).  
  
<a name="x_Code"></a>   
## <a name="xcode"></a>x:Code  
 [X:Code](../../xaml-services/x-code-intrinsic-xaml-type.md) , içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]tanımlanan bir Directive öğesidir. Bir `x:Code` Directive öğesi, satır içi programlama kodu içerebilir. Satır içi tanımlı kod, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aynı sayfada ile etkileşime geçebilir. Aşağıdaki örnek, satır içi C# kodu gösterir. Kodun `x:Code` öğenin içinde ve kodun `<CDATA[`çevrelenmeli... `]]>` [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]bir işlemcinin[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]( şemayı ya da Şemayıyorumlama)içeriği,tamolarakiçeriğiniyorumlamayaçalışmayın.[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithInlineCode](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page4.xaml#buttonwithinlinecode)]  
  
<a name="Inline_Code_Limitations"></a>   
## <a name="inline-code-limitations"></a>Satır içi kod sınırlamaları  
 Satır içi kod kullanımının önlenmemesini veya sınırlandırmasını düşünmelisiniz. Mimari ve kodlama FI açısından, biçimlendirme ve arka plan arasındaki ayrımı korumak, tasarımcı ve geliştirici rollerinin çok daha belirgin kalmasını önler. Daha teknik bir düzeyde, her zaman [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] oluşturulmuş kısmi sınıfa yazdığınız ve yalnızca varsayılan XML ad alanı eşlemelerini kullanabileceği için satır içi kod için yazdığınız kod yazmak için çok daha fazla olabilir. Deyim ekleyemediği `using` için, yaptığınız birçok API çağrısının çoğunu tam olarak nitelemeniz gerekir. Varsayılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] eşlemeler, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] derlemelerde bulunan tüm clr ad alanlarını içerir, ancak diğer CLR ad alanlarında bulunan türlere ve üyelere yönelik çağrıları tamamen nitelemeniz gerekir. Ayrıca, satır içi koddaki kısmi sınıfın ötesinde herhangi bir şey tanımlayamazsınız ve başvurmakta olduğunuz tüm Kullanıcı kodu varlıklarının, oluşturulan kısmi sınıf içinde bir üye veya değişken olarak mevcut olması gerekir. Makrolar veya `#ifdef` genel değişkenlere veya derleme değişkenlerine karşı diğer dile özgü programlama özellikleri de kullanılamaz. Daha fazla bilgi için bkz. [X:Code IÇSEL xaml türü](../../xaml-services/x-code-intrinsic-xaml-type.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XAML'ye Genel Bakış (WPF)](xaml-overview-wpf.md)
- [x:Code İç XAML Türü](../../xaml-services/x-code-intrinsic-xaml-type.md)
- [WPF Uygulaması Derleme](../app-development/building-a-wpf-application-wpf.md)
- [Ayrıntılı XAML Sözdizimi](xaml-syntax-in-detail.md)
