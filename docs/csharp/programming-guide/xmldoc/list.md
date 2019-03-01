---
title: <list> - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- list
- <list>
helpviewer_keywords:
- list C# XML tag
- listheader C# XML tag
- <listheader> C# XML tag
- item C# XML tag
- <item> C# XML tag
- <list> C# XML tag
ms.assetid: c9620b1b-c2e6-43f1-ab88-8ab47308ffec
ms.openlocfilehash: 888f6c823313c137be4b89e82f0c4cd1c50cf771
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977480"
---
# <a name="list-c-programming-guide"></a>\<Liste > (C# Programlama Kılavuzu)
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<list type="bullet" | "number" | "table">  
    <listheader>  
        <term>term</term>  
        <description>description</description>  
    </listheader>  
    <item>  
        <term>term</term>  
        <description>description</description>  
    </item>  
</list>  
```  
  
#### <a name="parameters"></a>Parametreler  
 `term`  
 İçinde tanımlanan tanımlamak için bir terim `description`.  
  
 `description`  
 Bir ya da öğe bir madde işareti veya numaralı liste tanımını bir `term`.  
  
## <a name="remarks"></a>Açıklamalar  
 \<Listheader > blok satırında bir tablo veya tanım listesi tanımlamak için kullanılır. Bir tablo tanımlarken, yalnızca bir giriş başlığı hükmün sağlamanız gerekir.  
  
 Listedeki her bir öğe ile belirtilen bir \<öğesi > bloğu. Tanım listesi oluştururken, her ikisi de belirtmeniz gerekir `term` ve `description`. Ancak, bir tablo, madde işaretli liste veya numaralı liste için bir giriş sağlamanız yeterlidir `description`.  
  
 Bir listeyi veya tabloyu kadar olabilir \<öğesi > gerektiğinde engeller.  
  
 Derleme [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) işlem belgeleri açıklamaları için bir dosya için.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideDocComments#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Belge Açıklamaları için Önerilen Etiketler](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
