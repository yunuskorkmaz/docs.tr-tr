---
title: <returns> - C# programlama kılavuzu
ms.date: 07/20/2015
f1_keywords:
- returns
- <returns>
helpviewer_keywords:
- <returns> C# XML tag
- returns C# XML tag
ms.assetid: bb2d9958-62fc-47c7-9511-6311171f119f
ms.openlocfilehash: 784d9effa589c962b8a2b982fd199f74309fb4dc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789704"
---
# <a name="returns-c-programming-guide"></a>\<> döndürür (C# programlama kılavuzu)

## <a name="syntax"></a>Sözdizimi

```xml
<returns>description</returns>
```

## <a name="parameters"></a>Parametreler

- `description`

  İade değerinin açıklaması.

## <a name="remarks"></a>Açıklamalar

İade \<> etiketi, iade değerini açıklamak için bir yöntem bildirimi için yorumda kullanılmalıdır.

Belge yorumlarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derle.

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideDocComments#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#10)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# programlama kılavuzu](../index.md)
- [Belge açıklamaları için önerilen etiketler](./recommended-tags-for-documentation-comments.md)
