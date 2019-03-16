---
title: x:Null Biçimlendirme Uzantısı
ms.date: 03/30/2017
f1_keywords:
- NullExtension
- x:NullExtension
- x:Null
- "Null"
- xNull
helpviewer_keywords:
- Null markup extension in XAML [XAML Services]
- x:Null markup extension [XAML Services]
- XAML [XAML Services], x:Null markup extension
ms.assetid: 2e3ccc21-4996-481d-91b5-3910d8b3bfa3
ms.openlocfilehash: 34a2de71bec9b0929070aa908741de38b5904643
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2019
ms.locfileid: "58029368"
---
# <a name="xnull-markup-extension"></a>x:Null Biçimlendirme Uzantısı
Belirtir `null` XAML üyesi için bir değer olarak.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xaml  
<object property="{x:Null}" .../>  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Null başvuru anahtar sözcüğü C# ve [!INCLUDE[TLA#tla_cpp](../../../includes/tlasharptla-cpp-md.md)] null. Bir null başvuru için Microsoft Visual Basic anahtar `Nothing`, ancak her zaman `{x:Null}` arka plan kod dili ile XAML ilişkilendirmek XAML kullanım bakılmaksızın olarak.  
  
 `x:Null` İşaretleme uzantısı ayarlanabilir özelliğe sahiptir.  
  
 Bir null kullanımı genellikle bir CLR XAML üye açığa ile ilişkilendirilir <xref:System.Nullable%601> değeri.  
  
 `x:Null` Tüm XAML biçimlendirme uzantıları gibi işaretleme uzantısı ayraçlar kullanır (`{,}`) değişmez değerler veya olay işleyicisi başvuruları dışındaki öznitelik değerlerinin işlenmesi kaçış. Öznitelik sözdizimi, bu işaretleme uzantısı ile en sık kullanılan sözdizimidir. Bir nesne öğesi sözdizimi `<x:Null />` teknik olarak mümkündür, ancak nadiren kullanılır çünkü `x:Null` biçimlendirme uzantısına sahip hiçbir konumsal parametreler ya da yapı bağımsız değişkenler.  
  
 Biçimlendirme uzantıları hakkında daha fazla bilgi için bkz. [biçimlendirme uzantıları ve WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
 .NET Framework XAML hizmetlerinde bu işaretleme uzantısının işlenmesi tarafından tanımlanan <xref:System.Windows.Markup.NullExtension> sınıfı.  
  
## <a name="wpf-usage-notes"></a>WPF kullanım notları  
 Unutmayın `null` mutlaka bir başvuru türü bağımlılık özelliği için başlangıç unset değeri değil. İlk varsayılan değer, her bir bağımlılık özelliği için değişebilir ve özelliklere özgü meta veriler hakkında temel alabilir. Birçok bağımlılık özellikleri kabul `null` bir değer olarak işaretleme ya da kendi doğrulama geri çağırma uygulamaları nedeniyle kod aracılığıyla. Bağımlılık özellikleri hakkında daha fazla bilgi için bkz: [bağımlılık özelliklerine genel bakış](../wpf/advanced/dependency-properties-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.DependencyProperty.UnsetValue>
- [XAML'ye Genel Bakış (WPF)](../wpf/advanced/xaml-overview-wpf.md)
- [İşaretleme Uzantıları ve WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
