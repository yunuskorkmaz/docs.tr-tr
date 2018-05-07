---
title: x:Null İşaretleme Uzantısı
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
ms.openlocfilehash: 94cfaee9a0a9a9f3892b9df50ac59103709a3b14
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="xnull-markup-extension"></a>x:Null İşaretleme Uzantısı
Belirtir `null` XAML üyesi için bir değer olarak.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xaml  
<object property="{x:Null}" .../>  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Bir null başvuru C# anahtar sözcüğü ve [!INCLUDE[TLA#tla_cpp](../../../includes/tlasharptla-cpp-md.md)] null. Microsoft Visual Basic anahtar sözcüğü bir null başvuru için `Nothing`, ancak her zaman kullanmanız `{x:Null}` arka plan kod dili XAML ile ilişkilendirmek XAML kullanımı bağımsız olarak.  
  
 `x:Null` Biçimlendirme uzantısı olan ayarlanabilir özellik yok.  
  
 Bir null kullanımı genellikle bir CLR XAML üye riskini ile ilişkilendirilen <xref:System.Nullable%601> değeri.  
  
 `x:Null` Tüm XAML biçimlendirme uzantıları gibi biçimlendirme uzantısı kullanır küme ayraçları (`{,}`) öznitelik değerlerini değişmez değerleri veya olay işleyicisi başvuruları dışında olacak şekilde işlenmesini kaçış için. Öznitelik sözdizimi bu biçimlendirme uzantısı ile en sık kullanılan sözdizimi şeklindedir. Bir nesne öğesi sözdizimi `<x:Null />` teknik olarak mümkün olmakla birlikte, çünkü nadiren kullanılır `x:Null` biçimlendirme uzantısı hiçbir konumsal parametreler ya da yapım bağımsız değişken içeriyor.  
  
 Biçimlendirme uzantıları hakkında daha fazla bilgi için bkz: [biçimlendirme uzantıları ve WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
 .NET Framework XAML hizmetlerinde bu biçimlendirme uzantısı işlenmesi tarafından tanımlanan <xref:System.Windows.Markup.NullExtension> sınıfı.  
  
## <a name="wpf-usage-notes"></a>WPF kullanım notları  
 Unutmayın `null` mutlaka bir başvuru türü bağımlılık özelliği için ilk unset değer değil. İlk varsayılan değer her bağımlılık özelliği için farklı olabilir ve özelliklere özgü meta verileri temel alarak. Pek çok bağımlılık özellikleri kabul `null` olarak işaretleme veya kod kendi doğrulama geri çağırma uygulamalarını nedeniyle yoluyla bir değer. Bağımlılık özellikleri hakkında daha fazla bilgi için bkz: [bağımlılık özelliklerine genel bakış](../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.DependencyProperty.UnsetValue>  
 [XAML'ye Genel Bakış (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [İşaretleme Uzantıları ve WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
