---
title: XAML 2009 Dil Özellikleri
ms.date: 03/30/2017
helpviewer_keywords:
- XAML 2009 [XAML Services]
- XAML [XAML Services], XAML 2009
ms.assetid: f6bb18d8-c86a-4549-8862-323e6b32a8dd
ms.openlocfilehash: 36b1ad197b5c8e38c77a9a6a92ba1b3b659efbb7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54661362"
---
# <a name="xaml-2009-language-features"></a>XAML 2009 Dil Özellikleri
XAML 2009, mevcut XAML dil belirtimi genişleten yeni XAML dil özellikleri toplu terimdir. XAML 2009, birkaç yeni yönergeleri ve yapıları sunar. Bunlar [x: Arguments yönergesi](../../../docs/framework/xaml-services/x-arguments-directive.md); [x: FactoryMethod yönergesi](../../../docs/framework/xaml-services/x-factorymethod-directive.md); [x: Reference işaretleme uzantısı](../../../docs/framework/xaml-services/x-reference-markup-extension.md); [x: TypeArguments yönergesi ](../../../docs/framework/xaml-services/x-typearguments-directive.md); ve dili ortak temelleri için yerleşik türler (örneğin `x:Char`).  
  
<a name="xaml_2009_support_in_wpf_and_visual_studio"></a>   
## <a name="xaml-2009-support-in-wpf-and-visual-studio"></a>WPF ve Visual Studio XAML 2009 desteği  
 WPF, XAML 2009 özelliklerini kullanabilirsiniz, ancak yalnızca XAML için WPF biçimlendirme derlenmiş değil. Biçimlendirme derlenmiş XAML ve BAML formu, XAML, XAML 2009 dil anahtar sözcükleri ve özellikleri şu anda desteklemez.  
  
 Gevşek XAML ' WPF'de yüklemeye yönelik var olan teknikleri biçimlendirme derlenmiş XAML için daha kısıtlayıcı CLR türlerine ve tür sistemine olası güvenlik ve erişim kısıtlamasına sahip olmadığını unutmayın. Daha fazla bilgi için [güvenlik (WPF)](../../../docs/framework/wpf/security-wpf.md) veya [WPF güvenlik stratejisi - Platform güvenliği](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md).  
  
 XAML 2009 ya da önceki XAML 2006 değiştirme ek özellikler de sunar yapıları ya da temel biçimlendirme forms değiştirin.  
  
### <a name="xkey-as-an-object-element"></a>x: Key bir nesne öğesi olarak  
 XAML 2009 destekleyebilir `x:Key` nesne (nesne öğesi değerine sahip bir özellik öğesi); ancak, XAML 2006'ı yalnızca desteklenen `x:Key` özniteliği olarak. "XAML 2009" bölümüne bakın [x: Key yönergesi](../../../docs/framework/xaml-services/x-key-directive.md).  
  
### <a name="xmlns-on-property-elements"></a>Özellik öğelerde xmlns  
 XAML 2009 XAML ad alanı (xmlns) tanımları üzerinde özellik öğeleri destekler; Ancak, XAML 2006 nesne öğelerde xmlns tanımları yalnızca destekler.  
  
### <a name="event-attributes"></a>Olay öznitelikleri  
 Olaylar tarafından desteklenen öznitelikleri için XAML 2006 biçimlendirmesi derleme karmaşıktır ve biçimlendirme derleme olayları gönderen varsayılır. XAML 2009, çalışma zamanı ayrıştırma ve XAML yükleme kadar olay kablolama erteler bir işaretleme uzantısı benzer bir biçimlendirme biçimini destekler. Ancak, WPF uygulamaları ve WPF kullanıcı Arabirimi için XAML senaryolar bu özellik genellikle kullanmayın. WPF ve XAML 2006 uygulaması tanımlanan yönlendirilmiş olaylar için olay işleyicisi kablolama birleşimini kullanan <xref:System.Windows.UIElement> düzeyi ve bunun biçimlendirme derleyici adım çok olay özniteliği işlemesi için. Biçimlendirme derleyici ayrıca XAML biçimlendirme derleyici kullanılır yapı eylemleri yeri bildirin içinde bulunan herhangi bir olay özniteliği önceden işler.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [XAML'ye Genel Bakış (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
