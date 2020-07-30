---
title: <param> -C# Programlama Kılavuzu
description: XML hakkında bilgi edinin <param> Etiket. Bu etiket, yöntemi için olan parametrelerden birini açıklayacak bir yöntem bildirimi açıklamasında kullanılır.
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: a9e3b2e86528afcbe1330788e248f0143efb5c1b
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381560"
---
# <a name="param-c-programming-guide"></a>\<param>(C# Programlama Kılavuzu)

## <a name="syntax"></a>Söz dizimi

```xml
<param name="name">description</param>
```

## <a name="parameters"></a>Parametreler

- `name`

  Bir yöntem parametresinin adı. Adı çift tırnak işareti ("") içine alın.

- `description`

  Parametresi için bir açıklama.

## <a name="remarks"></a>Açıklamalar

`<param>`Yöntemi, yöntemin parametrelerinden birini açıklayacak bir yöntem bildirimine ilişkin açıklamada kullanılmalıdır. Birden çok parametreyi belgelemek için birden çok `<param>` etiket kullanın.

`<param>`Etiket metni IntelliSense, nesne tarayıcısı ve kod açıklaması Web raporu ' nda görüntülenir.

Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# programlama kılavuzu](../index.md)
- [Belge açıklamaları için önerilen etiketler](./recommended-tags-for-documentation-comments.md)
