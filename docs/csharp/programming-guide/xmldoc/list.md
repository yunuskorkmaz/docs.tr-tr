---
title: <list> - C# programlama kılavuzu
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
ms.openlocfilehash: cb289b26e9bc12d561892c421fb40da18d8c3513
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789746"
---
# <a name="list-c-programming-guide"></a>\<liste> (C# programlama kılavuzu)

## <a name="syntax"></a>Sözdizimi

```xml
<list type="bullet|number|table">
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

## <a name="parameters"></a>Parametreler

- `term`

  Tanımlanacak bir terim, hangi `description`olarak tanımlanır.

- `description`

  Madde işareti veya numaralanmış listedeki bir öğe `term`veya bir .
  
## <a name="remarks"></a>Açıklamalar

> \<engeli, tablo veya tanım listesinin başlık satırını tanımlamak için kullanılır. Bir tablo tanımlarken, yalnızca başlıkta dönem için bir giriş sağlamanız gerekir.

Listedeki her öğe bir \<öğe> blokile belirtilir. Tanım listesi oluştururken, hem de `term` `description`. Ancak, bir tablo, madde işaretli liste veya numaralanmış liste için `description`yalnızca .

Bir liste veya tablo, \<gerektiğinde sayıda öğe> ye sahip olabilir.

Belge yorumlarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derle.

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideDocComments#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#6)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# programlama kılavuzu](../index.md)
- [Belge açıklamaları için önerilen etiketler](./recommended-tags-for-documentation-comments.md)
