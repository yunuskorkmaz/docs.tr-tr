---
title: <typeparam> -C# Programlama Kılavuzu
description: XML hakkında bilgi edinin <typeparam> Etiket. Bu etiket, bir tür parametresini anlatmak için genel bir tür veya yöntem bildirimi açıklamasında kullanılır.
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: 1b9d5d30c1a507e3bb7938ee0c036cdac3ef2f90
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477686"
---
# <a name="typeparam-c-programming-guide"></a>\<typeparam> (C# Programlama Kılavuzu)

## <a name="syntax"></a>Sözdizimi

```xml
<typeparam name="name">description</typeparam>
```

## <a name="parameters"></a>Parametreler

- `name`

  Tür parametresinin adı. Adı çift tırnak işareti ("") içine alın.

- `description`

  Tür parametresi için bir açıklama.

## <a name="remarks"></a>Açıklamalar

`<typeparam>`Etiket, bir tür parametresini betimleyen genel tür veya yöntem bildirimine ilişkin açıklamada kullanılmalıdır. Genel tür veya metodun her tür parametresi için bir etiket ekleyin.

Daha fazla bilgi için bkz. [Genel türler](../generics/index.md).

`<typeparam>`Etiketin metni IntelliSense 'de, [nesne tarayıcısı pencere](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) kodu açıklama Web raporu ' nda görüntülenir.

Belge açıklamalarını bir dosyaya işlemek için [**belgelerimdosyası**](../../language-reference/compiler-options/output.md#documentationfile) ile derleyin.

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../../language-reference/index.md)
- [C# programlama kılavuzu](../index.md)
- [Belge açıklamaları için önerilen etiketler](./recommended-tags-for-documentation-comments.md)
