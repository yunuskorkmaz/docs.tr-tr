---
title: <paramref>- C# programlama kılavuzu
ms.date: 07/20/2015
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
ms.openlocfilehash: 12df257271369dc7f0a5c066b712a8d8e6c38761
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793398"
---
# <a name="paramref-c-programming-guide"></a>\<paramref> (C# programlama kılavuzu)

## <a name="syntax"></a>Sözdizimi

```xml
<paramref name="name"/>
```

## <a name="parameters"></a>Parametreler

- `name`

  Başvurmak için parametrenin adı. Adı çift tırnak işaretlerine (" ") ekin.

## <a name="remarks"></a>Açıklamalar

\<Paramref> etiketi, kod açıklamalarında, örneğin \<bir özet> veya \<blok> açıklamadaki bir sözcüğün bir parametreye atıfta bulunduğunu belirtmeniz için bir yol sunar. XML dosyası, bu sözcüğü kalın veya italik yazı tipi gibi farklı şekillerde biçimlendirmek için işlenebilir.

Belge yorumlarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derle.

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideDocComments#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#7)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Belge açıklamaları için önerilen etiketler](./recommended-tags-for-documentation-comments.md)
