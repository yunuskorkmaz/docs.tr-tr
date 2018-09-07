---
title: '&lt;değer&gt; (C# programlama Kılavuzu)'
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: 24ef4aba13668cd04e20f17ebffac9eb68e796ca
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44081862"
---
# <a name="ltvaluegt-c-programming-guide"></a>&lt;değer&gt; (C# programlama Kılavuzu)
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a>Parametreler  
 `property-description`  
 Bir özellik için bir açıklama.  
  
## <a name="remarks"></a>Açıklamalar  
 \<Değer > etiketi temsil eden bir özellik değeri tanımlamak olanak tanır. Visual Studio .NET geliştirme ortamında bir özellik kod Sihirbazı aracılığıyla eklediğinizde, bu ekleyeceksiniz Not bir [ \<Özet >](../../../csharp/programming-guide/xmldoc/summary.md) yeni bir özellik için etiket. Daha sonra el ile eklemelisiniz bir \<değer > özelliği temsil eden bir değeri açıklamak için etiket.  
  
 Derleme [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) işlem belgeleri açıklamaları için bir dosya için.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideDocComments#14](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/value_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Belge Açıklamaları için Önerilen Etiketler](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
