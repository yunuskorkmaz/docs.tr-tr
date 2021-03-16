---
title: <typeparamref> -C# Programlama Kılavuzu
description: XML etiketi hakkında bilgi edinin <typeparamref> . Bu etiket, belge dosyası tüketicilerinin sözcüğü farklı bir şekilde (örneğin, italik) biçimlendirmesini sağlar.
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: 1bb9a73f4122f3b9d521565a7172a9b8f75f7a98
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477667"
---
# <a name="typeparamref-c-programming-guide"></a>\<typeparamref> (C# Programlama Kılavuzu)

## <a name="syntax"></a>Sözdizimi

```xml
<typeparamref name="name"/>
```

## <a name="parameters"></a>Parametreler

- `name`

  Tür parametresinin adı. Adı çift tırnak işareti ("") içine alın.

## <a name="remarks"></a>Açıklamalar

Genel türlerde ve yöntemlerde tür parametreleri hakkında daha fazla bilgi için bkz. [Genel türler](../generics/index.md).

Belge dosyasının tüketicilerini farklı bir şekilde (örneğin, italik) biçimlendirmesini sağlamak için bu etiketi kullanın.

Belge açıklamalarını bir dosyaya işlemek için [**belgelerimdosyası**](../../language-reference/compiler-options/output.md#documentationfile) ile derleyin.

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# programlama kılavuzu](../index.md)
- [Belge açıklamaları için önerilen etiketler](./recommended-tags-for-documentation-comments.md)
