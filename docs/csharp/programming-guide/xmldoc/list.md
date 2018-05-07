---
title: '&lt;Liste&gt; (C# programlama Kılavuzu)'
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
ms.openlocfilehash: 768490424403f1235873a681ffba3367e3f128b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="ltlistgt-c-programming-guide"></a>&lt;Liste&gt; (C# programlama Kılavuzu)
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
 Her iki öğeyi madde işareti veya numaralı liste ya da tanımı bir `term`.  
  
## <a name="remarks"></a>Açıklamalar  
 \<Listheader > bloğu bir tablo veya tanım listesi başlık satırının tanımlamak için kullanılır. Bir tablo tanımlarken, yalnızca bir giriş başlığı'nda terim için sağlamanız gerekir.  
  
 Listedeki her bir öğe ile belirtilen bir \<öğesi > bloğu. Bir tanım listesi oluştururken, her ikisi de belirtmeniz gerekir `term` ve `description`. Ancak, bir tablo, listeyi veya numaralandırılmış listesi için yalnızca bir giriş için sağlamanız gerekir `description`.  
  
 Bir liste veya tablo kadar olabilir \<öğesi > gerektiğinde engeller.  
  
 İle derleme [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) bir dosyaya işlem belgesi açıklamaları için.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideDocComments#6](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/list_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Belge Açıklamaları için Önerilen Etiketler](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
