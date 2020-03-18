---
title: <c>- C# programlama kılavuzu
ms.date: 07/20/2015
f1_keywords:
- c
- <c>
helpviewer_keywords:
- text, marking as code [C#]
- code, marking text as [C#]
- c C# XML tag
- <c> C# XML tag
ms.assetid: aad5b16e-a29e-445e-bd0d-eea0b138d7b2
ms.openlocfilehash: d5b28ee6db52d191f8454592d792ac0a1e1dc73b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793452"
---
# <a name="c-c-programming-guide"></a>\<c> (C# programlama kılavuzu)

## <a name="syntax"></a>Sözdizimi

```xml
<c>text</c>
```

## <a name="parameters"></a>Parametreler

- `text`

  Kod olarak belirtmek istediğiniz metin.

## <a name="remarks"></a>Açıklamalar

\<C> etiketi, açıklama içindeki metnin kod olarak işaretlemesi gerektiğini belirtmek için bir yol verir. Birden çok satırı kod olarak belirtmek için [ \<kod>](./code.md) kullanın.

Belge yorumlarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derle.

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideDocComments#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#2)]
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# programlama kılavuzu](../index.md)
- [Belge açıklamaları için önerilen etiketler](./recommended-tags-for-documentation-comments.md)
