---
title: <example> - C# programlama kılavuzu
ms.date: 07/20/2015
f1_keywords:
- <example>
- example
helpviewer_keywords:
- <example> C# XML tag
- example C# XML tag
ms.assetid: 32d6e73b-2554-4abb-83ee-a1e321334fd2
ms.openlocfilehash: 615eccbc427b6a5bbbed061acd0c8b0b9be7f46c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789812"
---
# <a name="example-c-programming-guide"></a>\<örnek> (C# programlama kılavuzu)

## <a name="syntax"></a>Sözdizimi

```xml
<example>description</example>
```

## <a name="parameters"></a>Parametreler

- `description`

  Kod örneğinin açıklaması.

## <a name="remarks"></a>Açıklamalar

Örnek \<> etiketi, bir yöntemin veya diğer kitaplık üyesinin nasıl kullanılacağına ilgili bir örnek belirtmenize olanak tanır. Bu genellikle [ \<kod>](./code.md) etiketini kullanmayı içerir.

Belge yorumlarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derle.

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideDocComments#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#3)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Belge açıklamaları için önerilen etiketler](./recommended-tags-for-documentation-comments.md)
