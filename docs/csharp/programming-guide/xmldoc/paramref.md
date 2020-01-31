---
title: <paramref> C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
ms.openlocfilehash: 12df257271369dc7f0a5c066b712a8d8e6c38761
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793398"
---
# <a name="paramref-c-programming-guide"></a>\<paramref > (C# Programlama Kılavuzu)

## <a name="syntax"></a>Sözdizimi

```xml
<paramref name="name"/>
```

## <a name="parameters"></a>Parametreler

- `name`

  Başvurabileceğiniz parametrenin adı. Adı çift tırnak işareti ("") içine alın.

## <a name="remarks"></a>Açıklamalar

\<paramref > etiketi, kod açıklamalarındaki bir sözcüğün, örneğin \<Özet > veya \<Comments > bloğunun bir parametreye başvurduğunu göstermek için bir yol sağlar. Bu sözcüğü, kalın veya italik yazı tipiyle olduğu gibi farklı bir şekilde biçimlendirmek için XML dosyası işlenebilir.

Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideDocComments#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#7)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Belge açıklamaları için önerilen Etiketler](./recommended-tags-for-documentation-comments.md)
