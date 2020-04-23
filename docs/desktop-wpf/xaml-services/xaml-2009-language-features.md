---
title: XAML 2009 Dil Özellikleri
ms.date: 03/30/2017
helpviewer_keywords:
- XAML 2009 [XAML Services]
- XAML [XAML Services], XAML 2009
ms.assetid: f6bb18d8-c86a-4549-8862-323e6b32a8dd
ms.openlocfilehash: e58e6757b88958bf8a3547c8a272c2e6298dcecb
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071600"
---
# <a name="xaml-2009-language-features"></a>XAML 2009 Dil Özellikleri
XAML 2009, varolan XAML dil belirtimini genişleten yeni XAML dil özelliklerinin kısaltma terimidir. XAML 2009 birkaç yeni yönerge ve yapı sunar. Bunlar [x:Bağımsız Değişkenler Yönergesi;](xarguments-directive.md) [x:FactoryMethod Direktifi](xfactorymethod-directive.md); [x:Referans Biçimlendirme Uzantısı](xreference-markup-extension.md); [x:TypeArguments Yönergesi](xtypearguments-directive.md); ve ortak dil ilkel (örneğin) `x:Char`için yerleşik türleri.

## <a name="xaml-2009-support-in-wpf-and-visual-studio"></a>XAML 2009 WPF ve Visual Studio Desteği

WPF'de XAML 2009 özelliklerini kullanabilirsiniz, ancak yalnızca WPF biçimlendirmesi derlenmiş olmayan XAML için kullanabilirsiniz. Biçimlendirmeyle derlenmiş XAML ve XAML'nin BAML formu şu anda XAML 2009 dil anahtar kelimelerini ve özelliklerini desteklemez.

WPF'de gevşek XAML yükleme için varolan tekniklerin, CLR türlerine ve biçimlendirmeyle derlenen XAML'ye göre daha kısıtlayıcı tür sistemine yönelik olası güvenlik ve erişim kısıtlamalarına da sahip olduğunu unutmayın. Daha fazla bilgi için [Güvenlik (WPF)](../../framework/wpf/security-wpf.md) veya [WPF Güvenlik Stratejisi - Platform Security](../../framework/wpf/wpf-security-strategy-platform-security.md)'ye bakın.

XAML 2009 ayrıca önceki XAML 2006 yapılarını değiştiren veya temel biçimlendirme formlarını değiştiren ek özellikler de sunar.

### <a name="xkey-as-an-object-element"></a>x:Nesne Öğesi Olarak Anahtar

XAML 2009 `x:Key` bir nesne (nesne öğesi değeri olan bir özellik öğesi) olarak destekleyebilir; ancak, XAML 2006 `x:Key` yalnızca bir öznitelik olarak desteklenir. Bkz. [x:Anahtar Yönergesi'nin](xkey-directive.md)"XAML 2009" bölümüne bakınız.

### <a name="xmlns-on-property-elements"></a>Özellik Elemanları üzerinde xmlns

XAML 2009 özellik öğeleri üzerinde XAML ad alanı (xmlns) tanımlarını destekleyebilir; ancak, XAML 2006 yalnızca nesne öğeleri üzerinde xmlns tanımlarını destekler.

### <a name="event-attributes"></a>Olay Öznitelikleri

Olaylar tarafından desteklenen öznitelikler için, XAML 2006 biçimlendirme derlemesinin söz konusu olduğunu varsalar ve olayları biçimlendirme derlemesine gönderir. XAML 2009, xaml'ın çalışma süresi ayrıştırılması ve yüklenmesi kadar olay kablolamasını erteleyen biçimlendirme uzantısını andıran bir biçimlendirme formunu destekler. Ancak, WPF Kullanıcı Arabirimi için WPF uygulamaları ve XAML senaryoları genellikle bu özelliği kullanmaz. WPF ve XAML 2006 uygulaması, olay öznitelik işlemenin büyük bir <xref:System.Windows.UIElement> kısmı için düzeyinde tanımlanan yönlendirilmiş olaylar için olay işleyicikablolamasının birleşimini ve biçimlendirme derleyicisi adımını kullanır. Biçimlendirme derleyicisi, xaml'da bulunan ve yapı eylemlerinin biçimlendirme derleyicisinin kullanıldığını bildirdiği tüm olay özniteliklerini de önceden işler.

## <a name="see-also"></a>Ayrıca bkz.

- [XAML'ye Genel Bakış (WPF)](../fundamentals/xaml.md)
