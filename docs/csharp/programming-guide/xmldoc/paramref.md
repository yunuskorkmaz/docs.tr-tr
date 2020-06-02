---
title: <paramref>-C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
ms.openlocfilehash: 4f3b521d24c8b4677a05b0b145cb36c31b2793f2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287317"
---
# <a name="paramref-c-programming-guide"></a>\<paramref>(C# Programlama Kılavuzu)

## <a name="syntax"></a>Söz dizimi

```xml
<paramref name="name"/>
```

## <a name="parameters"></a>Parametreler

- `name`

  Başvurabileceğiniz parametrenin adı. Adı çift tırnak işareti ("") içine alın.

## <a name="remarks"></a>Açıklamalar

`<paramref>`Etiketi, kod açıklamalarındaki bir sözcüğün, örneğin bir `<summary>` veya bloğunda bir parametreye başvurduğunu göstermek için bir yol sağlar `<remarks>` . Bu sözcüğü, kalın veya italik yazı tipiyle olduğu gibi farklı bir şekilde biçimlendirmek için XML dosyası işlenebilir.

Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideDocComments#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#7)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Belge açıklamaları için önerilen etiketler](./recommended-tags-for-documentation-comments.md)
