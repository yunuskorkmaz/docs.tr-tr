---
title: x:Reference İşaretleme Uzantısı
ms.date: 03/30/2017
helpviewer_keywords:
- x:Reference markup extension [XAML Services]
- XAML [XAML Services], x:Reference Markup Extension
- Reference markup extension [XAML Services]
ms.assetid: 2982e68b-d26b-4aa3-826a-34c57a9c5199
ms.openlocfilehash: 960f5c0e4192df72090c1a571dfc2fc5e3fd8ba3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562251"
---
# <a name="xreference-markup-extension"></a>x:Reference İşaretleme Uzantısı
XAML biçimlendirme içinde başka bir yerde bildirilmiş bir örneği başvurur. Bir öğenin başvuruyor `x:Name`.  
  
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
|`instancexName`|`x:Name` Değeri (veya değerini <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>-özelliği tanımlanan) başvurulan örneği.|  
  
## <a name="remarks"></a>Açıklamalar  
 `x:Reference` Aksi takdirde WPF gibi belirli çerçeveleri uygulanmıştır bir öğe başvurusu kavram XAML dil düzeyi desteği sağlar.  
  
## <a name="xreference-and-wpf"></a>x: Reference ve WPF  
 WPF ve XAML 2006 öğesi başvuruları çerçeve düzeyi özelliği tarafından ele alınan <xref:System.Windows.Data.Binding.ElementName%2A> bağlama. Çoğu WPF uygulamaları ve senaryoları için <xref:System.Windows.Data.Binding.ElementName%2A> bağlama hala kullanılmalıdır. Bu genel rehberlik için özel durumlar, veri bağlamı veya veri bağlama pratik hale diğer kapsayan konuları olduğu ve biçimlendirme derleme değil söz konusu olduğunda durumları içerebilir.  
  
 `x:Reference` bir yapı XAML 2009'tanımlanır. WPF'de XAML 2009 özellikleri kullanabilirsiniz, ancak yalnızca XAML için WPF biçimlendirme derlenmiş değil. XAML biçimlendirme derlenmiş ve XAML BAML form, XAML 2009 dil anahtar sözcükleri ve özellikleri şu anda desteklemez.
