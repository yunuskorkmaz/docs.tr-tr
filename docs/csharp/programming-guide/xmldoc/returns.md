---
title: <returns> -C# Programlama Kılavuzu
description: XML hakkında bilgi edinin <returns> Etiket. Bu etiket, dönüş değerini anlatmak için bir yöntem bildirimi açıklamasında kullanılır.
ms.date: 07/20/2015
f1_keywords:
- returns
- <returns>
helpviewer_keywords:
- <returns> C# XML tag
- returns C# XML tag
ms.assetid: bb2d9958-62fc-47c7-9511-6311171f119f
ms.openlocfilehash: 6a098208a51ca31fe2278b7c696deb15a13f8e1e
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477812"
---
# <a name="returns-c-programming-guide"></a>\<returns> (C# Programlama Kılavuzu)

## <a name="syntax"></a>Sözdizimi

```xml
<returns>description</returns>
```

## <a name="parameters"></a>Parametreler

- `description`

  Dönüş değerinin açıklaması.

## <a name="remarks"></a>Açıklamalar

`<returns>`Etiket, dönüş değerini betimleyen bir yöntem bildirimine ilişkin açıklamada kullanılmalıdır.

Belge açıklamalarını bir dosyaya işlemek için [**belgelerimdosyası**](../../language-reference/compiler-options/output.md#documentationfile) ile derleyin.

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideDocComments#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#10)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# programlama kılavuzu](../index.md)
- [Belge açıklamaları için önerilen etiketler](./recommended-tags-for-documentation-comments.md)
