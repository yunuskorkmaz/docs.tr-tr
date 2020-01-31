---
title: <typeparam> - C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: 867ecacf58f95533395ded203a8f17bc92558ccf
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793360"
---
# <a name="typeparam-c-programming-guide"></a>\<typeparam > (C# Programlama Kılavuzu)

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

`<typeparam>` etiketi, bir tür parametresini betimleyen genel tür veya yöntem bildirimine ilişkin açıklamada kullanılmalıdır. Genel tür veya metodun her tür parametresi için bir etiket ekleyin.

Daha fazla bilgi için bkz. [Genel türler](../generics/index.md).

`<typeparam>` etiketinin metni IntelliSense 'de, [nesne tarayıcısı pencere](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) kodu açıklama Web raporunda görüntülenir.

Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../../language-reference/index.md)
- [C#Programlama Kılavuzu](../index.md)
- [Belge açıklamaları için önerilen Etiketler](./recommended-tags-for-documentation-comments.md)
