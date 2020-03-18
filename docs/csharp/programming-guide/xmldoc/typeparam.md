---
title: <typeparam> - C# programlama kılavuzu
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: 867ecacf58f95533395ded203a8f17bc92558ccf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793360"
---
# <a name="typeparam-c-programming-guide"></a>\<typeparam> (C# programlama kılavuzu)

## <a name="syntax"></a>Sözdizimi

```xml
<typeparam name="name">description</typeparam>
```

## <a name="parameters"></a>Parametreler

- `name`

  Tür parametresinin adı. Adı çift tırnak işaretlerine (" ") ekin.

- `description`

  Tür parametresi için bir açıklama.

## <a name="remarks"></a>Açıklamalar

Etiket, `<typeparam>` bir tür parametresini açıklamak için genel bir tür veya yöntem bildirimi için yorumda kullanılmalıdır. Genel tür veya yöntemin her tür parametresi için bir etiket ekleyin.

Daha fazla bilgi için [Genel Bilgiler'e](../generics/index.md)bakın.

Etiketin `<typeparam>` metni, [Nesne Tarayıcı Penceresi](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) kodu yorum web raporu olan IntelliSense'de görüntülenir.

Belge yorumlarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derle.

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../../language-reference/index.md)
- [C# programlama kılavuzu](../index.md)
- [Belge açıklamaları için önerilen etiketler](./recommended-tags-for-documentation-comments.md)
