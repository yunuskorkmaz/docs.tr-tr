---
title: XAML 2009 Dil Özellikleri
ms.date: 03/30/2017
helpviewer_keywords:
- XAML 2009 [XAML Services]
- XAML [XAML Services], XAML 2009
ms.assetid: f6bb18d8-c86a-4549-8862-323e6b32a8dd
ms.openlocfilehash: dfa2841d8bc1ed1429372908f0dda97d178c4ac3
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556713"
---
# <a name="xaml-2009-language-features"></a>XAML 2009 Dil Özellikleri
XAML 2009, var olan XAML dil belirtimini genişleten yeni XAML dil özellikleri için Özet bir terimdir. XAML 2009 çeşitli yeni yönergeler ve yapılar sunar. Bu, [X:Arguments yönergesini](xarguments-directive.md)içerir; [X:FactoryMethod yönergesi](xfactorymethod-directive.md); [X:Reference Işaretleme uzantısı](xreference-markup-extension.md); [X:TypeArguments yönergesi](xtypearguments-directive.md); ve ortak dil temelleri için yerleşik türler (örneğin `x:Char` ).

## <a name="xaml-2009-support-in-wpf-and-visual-studio"></a>WPF ve Visual Studio 'da XAML 2009 desteği

WPF 'de XAML 2009 özelliklerini kullanabilirsiniz, ancak yalnızca WPF işaretleme ile derlenen XAML için. Biçimlendirme derlenmiş XAML ve XAML 'nin BAML formu şu anda XAML 2009 dil anahtar sözcüklerini ve özelliklerini desteklememektedir.

WPF 'de gevşek XAML yükleme tekniklerinin Ayrıca CLR türlerine ve biçimlendirme ile derlenen XAML için daha kısıtlayıcı olan tür sistemine yönelik güvenlik ve erişim kısıtlamalarına sahip olduğunu unutmayın. Daha fazla bilgi için bkz. [Güvenlik (WPF)](/dotnet/desktop/wpf/security-wpf) veya [WPF Güvenlik Stratejisi-Platform güvenliği](/dotnet/desktop/wpf/wpf-security-strategy-platform-security).

XAML 2009, önceki XAML 2006 yapılarını değiştiren veya temel biçimlendirme formlarını değiştiren ek özellikler de sunar.

### <a name="xkey-as-an-object-element"></a>bir nesne öğesi olarak x:Key

XAML 2009 `x:Key` , nesne (nesne öğesi değeri olan bir özellik öğesi) olarak destekleyebilir; ancak xaml 2006 yalnızca `x:Key` öznitelik olarak desteklenir. [X:Key yönergesinin](xkey-directive.md)"xaml 2009" bölümüne bakın.

### <a name="xmlns-on-property-elements"></a>Özellik öğelerinde xmlns

XAML 2009, özellik öğelerinde XAML ad alanı (xmlns) tanımlarını destekleyebilir; Ancak XAML 2006 yalnızca nesne öğelerinde xmlns tanımlarını destekler.

### <a name="event-attributes"></a>Olay öznitelikleri

Olaylar tarafından desteklenen özniteliklerde, XAML 2006, biçimlendirme derlemesinin dahil olduğunu varsayar ve olayları işaretleme derlemesine gönderir. XAML 2009, biçimlendirme uzantısına benzer bir biçimlendirme formunu destekler, bu da XAML 'in çalışma zamanı ayrıştırma ve yükleme tarihine kadar olay kablolarını erteler. Ancak WPF uygulamaları ve WPF Kullanıcı arabirimi için XAML senaryoları genellikle bu özelliği kullanmaz. WPF ve XAML 2006 uygulamasının, <xref:System.Windows.UIElement> olay özniteliği işlemenin büyük bir bölümü için, düzeyde ve biçimlendirme derleyicisi adımında tanımlanan yönlendirilmiş olaylar için olay işleyicisi kablolaması birleşimini kullanır. Biçimlendirme derleyicisi Ayrıca, derleme eylemlerinin biçimlendirme derleyicisinin kullanıldığını bildirildiği XAML 'de bulunan herhangi bir olay özniteliğini önceden işler.

## <a name="see-also"></a>Ayrıca bkz.

- [XAML'ye Genel Bakış (WPF)](../fundamentals/xaml.md)
