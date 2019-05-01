---
title: x:Reference Biçimlendirme Uzantısı
ms.date: 03/30/2017
helpviewer_keywords:
- x:Reference markup extension [XAML Services]
- XAML [XAML Services], x:Reference Markup Extension
- Reference markup extension [XAML Services]
ms.assetid: 2982e68b-d26b-4aa3-826a-34c57a9c5199
ms.openlocfilehash: 960f5c0e4192df72090c1a571dfc2fc5e3fd8ba3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938885"
---
# <a name="xreference-markup-extension"></a>x:Reference Biçimlendirme Uzantısı
XAML biçimlendirme içinde başka bir yerde bildirilmiş bir örneğine başvurur. Bir öğenin başvurusu başvuruyor `x:Name`.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xaml  
<object property="{x:Reference instancexName}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a>XAML Nesne Öğesi Kullanımı  
  
```xaml  
<object>  
  <object.property>  
    <x:Reference Name="instancexName"/>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`instancexName`|`x:Name` Değeri (veya değerini <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>-özelliği tanımlanmış) başvurulan örnek.|  
  
## <a name="remarks"></a>Açıklamalar  
 `x:Reference` Aksi takdirde WPF gibi belirli çerçeveleri içinde uygulanmış bir öğe başvurusu kavramı için XAML dili düzeyinde destek sağlar.  
  
## <a name="xreference-and-wpf"></a>x: Reference ve WPF  
 WPF ve XAML 2006'öğesi başvuru çerçeve düzeyi özelliği tarafından gönderilen <xref:System.Windows.Data.Binding.ElementName%2A> bağlama. Çoğu WPF uygulamaları ve senaryolar için <xref:System.Windows.Data.Binding.ElementName%2A> bağlama yine de kullanılmalıdır. Veri bağlamı veya veri bağlama pratik hale diğer kapsanan konular olduğu ve işaretleme derleme sürecine dahil değildir, bu genel kılavuz için özel durumlar durumları içerebilir.  
  
 `x:Reference` XAML 2009'dan bir yapı tanımlanır. WPF, XAML 2009 özelliklerini kullanabilirsiniz, ancak yalnızca XAML için WPF biçimlendirme derlenmiş değil. Biçimlendirme derlenmiş XAML ve BAML formu, XAML, XAML 2009 dil anahtar sözcükleri ve özellikleri şu anda desteklemez.
