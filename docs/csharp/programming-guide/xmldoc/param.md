---
title: <param> - C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: d16070a82531519dd276b2ea999623017769d716
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789768"
---
# <a name="param-c-programming-guide"></a>\<param > (C# Programlama Kılavuzu)

## <a name="syntax"></a>Sözdizimi

```xml
<param name="name">description</param>
```

## <a name="parameters"></a>Parametreler

- `name`

  Bir yöntem parametresinin adı. Adı çift tırnak işareti ("") içine alın.

- `description`

  Parametresi için bir açıklama.

## <a name="remarks"></a>Açıklamalar

Yöntemin parametrelerinden birini açıklayacak bir yöntem bildirimi için açıklamasında \<param > etiketi kullanılmalıdır. Birden çok parametreyi belgelemek için, birden çok \<param > etiketi kullanın.

\<param > etiketinin metni IntelliSense 'de, Nesne Tarayıcısı ve kod yorumu Web raporunda görüntülenir.

Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#Programlama Kılavuzu](../index.md)
- [Belge açıklamaları için önerilen Etiketler](./recommended-tags-for-documentation-comments.md)
