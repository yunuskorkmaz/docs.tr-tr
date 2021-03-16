---
title: <paramref> -C# Programlama Kılavuzu
description: XML etiketi hakkında bilgi edinin <paramref> . Bu etiket, koddaki bir sözcüğün bir parametre olduğunu göstermek için bir yol sağlar.
ms.date: 07/20/2015
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
ms.openlocfilehash: e559a899aad7806bb7ccef32be49954fabed6a32
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477878"
---
# <a name="paramref-c-programming-guide"></a>\<paramref> (C# Programlama Kılavuzu)

## <a name="syntax"></a>Sözdizimi

```xml
<paramref name="name"/>
```

## <a name="parameters"></a>Parametreler

- `name`

  Başvurabileceğiniz parametrenin adı. Adı çift tırnak işareti ("") içine alın.

## <a name="remarks"></a>Açıklamalar

`<paramref>`Etiketi, kod açıklamalarındaki bir sözcüğün, örneğin bir `<summary>` veya bloğunda bir parametreye başvurduğunu göstermek için bir yol sağlar `<remarks>` . Bu sözcüğü, kalın veya italik yazı tipiyle olduğu gibi farklı bir şekilde biçimlendirmek için XML dosyası işlenebilir.

Belge açıklamalarını bir dosyaya işlemek için [**belgelerimdosyası**](../../language-reference/compiler-options/output.md#documentationfile) ile derleyin.

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideDocComments#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#7)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Belge açıklamaları için önerilen etiketler](./recommended-tags-for-documentation-comments.md)
