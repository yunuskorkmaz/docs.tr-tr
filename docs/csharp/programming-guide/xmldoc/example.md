---
title: <example> -C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- <example>
- example
helpviewer_keywords:
- <example> C# XML tag
- example C# XML tag
ms.assetid: 32d6e73b-2554-4abb-83ee-a1e321334fd2
ms.openlocfilehash: e8d26f82562cc5140662f5b32ea9fedf5481d8f8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287407"
---
# <a name="example-c-programming-guide"></a>\<example>(C# Programlama Kılavuzu)

## <a name="syntax"></a>Söz dizimi

```xml
<example>description</example>
```

## <a name="parameters"></a>Parametreler

- `description`

  Kod örneğinin açıklaması.

## <a name="remarks"></a>Açıklamalar

`<example>`Etiketi, bir yöntemi veya diğer kitaplık üyesini nasıl kullanacağınızı gösteren bir örnek belirtmenizi sağlar. Bu genellikle etiketinin kullanılmasını içerir [\<code>](./code.md) .

Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideDocComments#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#3)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Belge açıklamaları için önerilen etiketler](./recommended-tags-for-documentation-comments.md)
