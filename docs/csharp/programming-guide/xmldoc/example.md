---
title: <example> -C# Programlama Kılavuzu
description: XML hakkında bilgi edinin <example> Etiket. Bu etiket, bir yöntemin veya diğer kitaplık üyesinin nasıl kullanılacağına ilişkin bir örnek belirtmenize imkan sağlar.
ms.date: 07/20/2015
f1_keywords:
- <example>
- example
helpviewer_keywords:
- <example> C# XML tag
- example C# XML tag
ms.assetid: 32d6e73b-2554-4abb-83ee-a1e321334fd2
ms.openlocfilehash: 8f9b4fa4ac447b853008576a46be9beeb583b018
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103479126"
---
# <a name="example-c-programming-guide"></a>\<example> (C# Programlama Kılavuzu)

## <a name="syntax"></a>Sözdizimi

```xml
<example>description</example>
```

## <a name="parameters"></a>Parametreler

- `description`

  Kod örneğinin açıklaması.

## <a name="remarks"></a>Açıklamalar

`<example>`Etiketi, bir yöntemi veya diğer kitaplık üyesini nasıl kullanacağınızı gösteren bir örnek belirtmenizi sağlar. Bu genellikle etiketinin kullanılmasını içerir [\<code>](./code.md) .

Belge açıklamalarını bir dosyaya işlemek için [**belgelerimdosyası**](../../language-reference/compiler-options/output.md#documentationfile) ile derleyin.

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideDocComments#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#3)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Belge açıklamaları için önerilen etiketler](./recommended-tags-for-documentation-comments.md)
