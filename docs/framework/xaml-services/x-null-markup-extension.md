---
title: "x:Null İşaretleme Uzantısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- NullExtension
- x:NullExtension
- x:Null
- Null
- xNull
helpviewer_keywords:
- Null markup extension in XAML [XAML Services]
- x:Null markup extension [XAML Services]
- XAML [XAML Services], x:Null markup extension
ms.assetid: 2e3ccc21-4996-481d-91b5-3910d8b3bfa3
caps.latest.revision: "20"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: a60d74bdf3343d02eaf912ac7700f36a649f659c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="xnull-markup-extension"></a>x:Null İşaretleme Uzantısı
Belirtir `null` XAML üyesi için bir değer olarak.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xaml  
<object property="{x:Null}" .../>  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Bir null başvuru anahtar sözcüğü [!INCLUDE[TLA#tla_cshrp](../../../includes/tlasharptla-cshrp-md.md)] ve [!INCLUDE[TLA#tla_cpp](../../../includes/tlasharptla-cpp-md.md)] null. [!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)] Anahtar sözcüğü bir null başvuru için `Nothing`, ancak her zaman kullanmanız `{x:Null}` arka plan kod dili XAML ile ilişkilendirmek XAML kullanımı bağımsız olarak.  
  
 `x:Null` Biçimlendirme uzantısı olan ayarlanabilir özellik yok.  
  
 Bir null kullanımı genellikle bir CLR XAML üye riskini ile ilişkilendirilen <xref:System.Nullable%601> değeri.  
  
 `x:Null` Tüm XAML biçimlendirme uzantıları gibi biçimlendirme uzantısı kullanır küme ayraçları (`{,}`) öznitelik değerlerini değişmez değerleri veya olay işleyicisi başvuruları dışında olacak şekilde işlenmesini kaçış için. Öznitelik sözdizimi bu biçimlendirme uzantısı ile en sık kullanılan sözdizimi şeklindedir. Bir nesne öğesi sözdizimi `<x:Null />` teknik olarak mümkün olmakla birlikte, çünkü nadiren kullanılır `x:Null` biçimlendirme uzantısı hiçbir konumsal parametreler ya da yapım bağımsız değişken içeriyor.  
  
 Biçimlendirme uzantıları hakkında daha fazla bilgi için bkz: [biçimlendirme uzantıları ve WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
 .NET Framework XAML hizmetlerinde bu biçimlendirme uzantısı işlenmesi tarafından tanımlanan <xref:System.Windows.Markup.NullExtension> sınıfı.  
  
## <a name="wpf-usage-notes"></a>WPF kullanım notları  
 Unutmayın `null` mutlaka bir başvuru türü bağımlılık özelliği için ilk unset değer değil. İlk varsayılan değer her bağımlılık özelliği için farklı olabilir ve özelliklere özgü meta verileri temel alarak. Pek çok bağımlılık özellikleri kabul `null` olarak işaretleme veya kod kendi doğrulama geri çağırma uygulamalarını nedeniyle yoluyla bir değer. Bağımlılık özellikleri hakkında daha fazla bilgi için bkz: [bağımlılık özelliklerine genel bakış](../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.DependencyProperty.UnsetValue>  
 [XAML genel bakış (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Biçimlendirme uzantıları ve WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
