---
title: <returns> -C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- returns
- <returns>
helpviewer_keywords:
- <returns> C# XML tag
- returns C# XML tag
ms.assetid: bb2d9958-62fc-47c7-9511-6311171f119f
ms.openlocfilehash: 7bc950a8d89a3ac2b5c3b7a68e05c7778e97f85c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287239"
---
# <a name="returns-c-programming-guide"></a>\<returns>(C# Programlama Kılavuzu)

## <a name="syntax"></a>Söz dizimi

```xml
<returns>description</returns>
```

## <a name="parameters"></a>Parametreler

- `description`

  Dönüş değerinin açıklaması.

## <a name="remarks"></a>Açıklamalar

`<returns>`Etiket, dönüş değerini betimleyen bir yöntem bildirimine ilişkin açıklamada kullanılmalıdır.

Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideDocComments#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#10)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# programlama kılavuzu](../index.md)
- [Belge açıklamaları için önerilen etiketler](./recommended-tags-for-documentation-comments.md)
