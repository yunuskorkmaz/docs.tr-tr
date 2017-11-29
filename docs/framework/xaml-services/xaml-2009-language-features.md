---
title: "XAML 2009 Dil Özellikleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML 2009 [XAML Services]
- XAML [XAML Services], XAML 2009
ms.assetid: f6bb18d8-c86a-4549-8862-323e6b32a8dd
caps.latest.revision: "11"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 6299a29cb79650eb59df3f198c3ea3fcd49d0076
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="xaml-2009-language-features"></a>XAML 2009 Dil Özellikleri
XAML 2009 varolan XAML dil belirtimi genişleten yeni XAML dil özellikleri için toplu terimdir. XAML 2009 birkaç yeni yönergeleri ve yapıları tanıtır. Bunlar[x: Arguments yönergesi](../../../docs/framework/xaml-services/x-arguments-directive.md); [x: FactoryMethod yönergesi](../../../docs/framework/xaml-services/x-factorymethod-directive.md); [x: Reference işaretleme uzantısı](../../../docs/framework/xaml-services/x-reference-markup-extension.md); [x: TypeArguments yönergesi ](../../../docs/framework/xaml-services/x-typearguments-directive.md); ve ortak dil temelleri için yerleşik türleri (örneğin `x:Char`).  
  
<a name="xaml_2009_support_in_wpf_and_visual_studio"></a>   
## <a name="xaml-2009-support-in-wpf-and-visual-studio"></a>WPF ve Visual Studio XAML 2009 desteği  
 WPF'de XAML 2009 özellikleri kullanabilirsiniz, ancak yalnızca XAML için WPF biçimlendirme derlenmiş değil. XAML biçimlendirme derlenmiş ve XAML BAML form, XAML 2009 dil anahtar sözcükleri ve özellikleri şu anda desteklemez.  
  
 WPF gevşek XAML'de yüklenmesi için varolan teknikleri de biçimlendirme derlenmiş XAML için daha kısıtlayıcı daha CLR türlerine ve tür sistemi olası güvenlik ve erişim kısıtlamaları gerektiğini unutmayın. Daha fazla bilgi için bkz: [güvenlik (WPF)](../../../docs/framework/wpf/security-wpf.md) veya [WPF güvenlik stratejisi - Platform güvenliği](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md).  
  
 XAML 2009 ya da önceki XAML 2006 değiştirme ek özellikler de sunar yapıları ya da temel biçimlendirme forms değiştirin.  
  
### <a name="xkey-as-an-object-element"></a>x: Key Object öğesi olarak  
 XAML 2009 destekleyebilmesi `x:Key` bir nesne (nesne öğesi değerine sahip bir özellik öğesi); ancak, XAML 2006 yalnızca desteklenen `x:Key` özniteliği olarak. "XAML 2009" bölümüne bakın [x: Key yönergesi](../../../docs/framework/xaml-services/x-key-directive.md).  
  
### <a name="xmlns-on-property-elements"></a>Özellik öğelerde xmlns  
 XAML 2009 XAML ad alanı (xmlns) tanımları özelliği öğelerde destekler; Ancak, XAML 2006 yalnızca nesne öğelerde xmlns tanımları destekler.  
  
### <a name="event-attributes"></a>Olay öznitelikleri  
 Olaylar tarafından yedeklenen öznitelikleri için XAML 2006 biçimlendirmesi derleme karmaşıktır ve biçimlendirme derleme olaylara gönderdikten varsayar. XAML 2009 olay kablolama çalıştırma ayrıştırma ve XAML yükleme kadar erteler biçimlendirme uzantısı benzer bir işaretleme biçimini destekler. Ancak, WPF uygulamaları ve XAML senaryoları WPF UI için bu özellik genellikle kullanmayın. WPF ve XAML 2006 uygulaması için tanımlanan yönlendirilmiş olaylar için olay işleyicisi kablolama bileşimini kullanır <xref:System.Windows.UIElement> düzeyi ve biçimlendirme derleyici adım büyük bir olay özniteliği işlemesi için. Biçimlendirme derleyici burada biçimlendirme derleyici kullanılır yapı eylemleri bildirmek XAML'de bulunan tüm olay öznitelikler de preprocesses.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XAML genel bakış (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
