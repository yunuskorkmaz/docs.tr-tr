---
title: <param> -C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: 396ed716c246091a674268020261069f36dd2be8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287330"
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
