---
title: <list> - C# Programlama Kılavuzu
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
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789746"
---
# <a name="list-c-programming-guide"></a>\<listesi > (C# Programlama Kılavuzu)

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

  `description`tanımlanacak bir terim.

- `description`

  Bir madde işareti veya numaralandırılmış listedeki bir öğe ya da bir `term`tanımı.
  
## <a name="remarks"></a>Açıklamalar

\<listheader > bloğu, bir tablo ya da tanım listesinin başlık satırını tanımlamak için kullanılır. Bir tablo tanımlarken, yalnızca başlıktaki terim için bir giriş sağlamanız gerekir.

Listedeki her öğe, bir \<öğesi > bloğu ile belirtilir. Tanım listesi oluştururken hem `term` hem de `description`belirtmeniz gerekir. Ancak, bir tablo, madde işaretli liste veya numaralandırılmış liste için yalnızca `description`için bir giriş sağlamanız gerekir.

Bir liste veya tablo, gereken sayıda \<öğe > bloğunu içerebilir.

Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideDocComments#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#6)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#Programlama Kılavuzu](../index.md)
- [Belge açıklamaları için önerilen Etiketler](./recommended-tags-for-documentation-comments.md)
