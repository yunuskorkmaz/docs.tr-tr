---
title: <remarks> - C# programlama kılavuzu
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: e37dac9cb9fed1df6ca027f09f2c95dbbc8ea66d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793379"
---
# <a name="remarks-c-programming-guide"></a>\<açıklamalar> (C# programlama kılavuzu)

## <a name="syntax"></a>Sözdizimi

```xml
<remarks>description</remarks>
```

## <a name="parameters"></a>Parametreler

- `Description`

  Üyenin açıklaması.

## <a name="remarks"></a>Açıklamalar

Etiketler> \<açıklamalar, [ \<özet>](./summary.md)ile belirtilen bilgileri tamamlayarak, bir tür hakkında bilgi eklemek için kullanılır. Bu bilgiler Nesne Tarayıcı penceresinde görüntülenir.

Belge yorumlarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derle.

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Belge açıklamaları için önerilen etiketler](./recommended-tags-for-documentation-comments.md)
