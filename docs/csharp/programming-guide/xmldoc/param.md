---
title: <param> - C# programlama kılavuzu
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: d16070a82531519dd276b2ea999623017769d716
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789768"
---
# <a name="param-c-programming-guide"></a>\<param> (C# programlama kılavuzu)

## <a name="syntax"></a>Sözdizimi

```xml
<param name="name">description</param>
```

## <a name="parameters"></a>Parametreler

- `name`

  Yöntem parametresinin adı. Adı çift tırnak işaretlerine (" ") ekin.

- `description`

  Parametre için bir açıklama.

## <a name="remarks"></a>Açıklamalar

Param \<> etiketi, yöntemin parametrelerinden birini açıklamak için bir yöntem bildirimi için açıklama da kullanılmalıdır. Birden çok parametreyi \<belgelemek için birden çok param> etiketi kullanın.

Param> \<etiketinin metni IntelliSense, Object Browser ve Code Comment Web Report'ta görüntülenir.

Belge yorumlarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derle.

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# programlama kılavuzu](../index.md)
- [Belge açıklamaları için önerilen etiketler](./recommended-tags-for-documentation-comments.md)
