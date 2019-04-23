---
title: XAML 2009 Dil Özellikleri
ms.date: 03/30/2017
helpviewer_keywords:
- XAML 2009 [XAML Services]
- XAML [XAML Services], XAML 2009
ms.assetid: f6bb18d8-c86a-4549-8862-323e6b32a8dd
ms.openlocfilehash: 05f811cd0d95f7605963dae851430fb6bf0e9f7a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59162286"
---
# <a name="xaml-2009-language-features"></a>XAML 2009 Dil Özellikleri
XAML 2009, mevcut XAML dil belirtimi genişleten yeni XAML dil özellikleri toplu terimdir. XAML 2009, birkaç yeni yönergeleri ve yapıları sunar. Bunlar [x: Arguments yönergesi](x-arguments-directive.md); [x: FactoryMethod yönergesi](x-factorymethod-directive.md); [x: Reference işaretleme uzantısı](x-reference-markup-extension.md); [x: TypeArguments yönergesi ](x-typearguments-directive.md); ve dili ortak temelleri için yerleşik türler (örneğin `x:Char`).  
  
<a name="xaml_2009_support_in_wpf_and_visual_studio"></a>   
## <a name="xaml-2009-support-in-wpf-and-visual-studio"></a>WPF ve Visual Studio XAML 2009 desteği  
 WPF, XAML 2009 özelliklerini kullanabilirsiniz, ancak yalnızca XAML için WPF biçimlendirme derlenmiş değil. Biçimlendirme derlenmiş XAML ve BAML formu, XAML, XAML 2009 dil anahtar sözcükleri ve özellikleri şu anda desteklemez.  
  
 Gevşek XAML ' WPF'de yüklemeye yönelik var olan teknikleri biçimlendirme derlenmiş XAML için daha kısıtlayıcı CLR türlerine ve tür sistemine olası güvenlik ve erişim kısıtlamasına sahip olmadığını unutmayın. Daha fazla bilgi için [güvenlik (WPF)](../wpf/security-wpf.md) veya [WPF güvenlik stratejisi - Platform güvenliği](../wpf/wpf-security-strategy-platform-security.md).  
  
 XAML 2009 ya da önceki XAML 2006 değiştirme ek özellikler de sunar yapıları ya da temel biçimlendirme forms değiştirin.  
  
### <a name="xkey-as-an-object-element"></a>x: Key bir nesne öğesi olarak  
 XAML 2009 destekleyebilir `x:Key` nesne (nesne öğesi değerine sahip bir özellik öğesi); ancak, XAML 2006'ı yalnızca desteklenen `x:Key` özniteliği olarak. "XAML 2009" bölümüne bakın [x: Key yönergesi](x-key-directive.md).  
  
### <a name="xmlns-on-property-elements"></a>Özellik öğelerde xmlns  
 XAML 2009 XAML ad alanı (xmlns) tanımları üzerinde özellik öğeleri destekler; Ancak, XAML 2006 nesne öğelerde xmlns tanımları yalnızca destekler.  
  
### <a name="event-attributes"></a>Olay öznitelikleri  
 Olaylar tarafından desteklenen öznitelikleri için XAML 2006 biçimlendirmesi derleme karmaşıktır ve biçimlendirme derleme olayları gönderen varsayılır. XAML 2009, çalışma zamanı ayrıştırma ve XAML yükleme kadar olay kablolama erteler bir işaretleme uzantısı benzer bir biçimlendirme biçimini destekler. Ancak, WPF uygulamaları ve WPF kullanıcı Arabirimi için XAML senaryolar bu özellik genellikle kullanmayın. WPF ve XAML 2006 uygulaması tanımlanan yönlendirilmiş olaylar için olay işleyicisi kablolama birleşimini kullanan <xref:System.Windows.UIElement> düzeyi ve bunun biçimlendirme derleyici adım çok olay özniteliği işlemesi için. Biçimlendirme derleyici ayrıca XAML biçimlendirme derleyici kullanılır yapı eylemleri yeri bildirin içinde bulunan herhangi bir olay özniteliği önceden işler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XAML'ye Genel Bakış (WPF)](../wpf/advanced/xaml-overview-wpf.md)
