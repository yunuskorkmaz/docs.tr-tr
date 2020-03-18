---
title: <typeparamref>- C# programlama kılavuzu
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: 266eadad322fd3c4167c7a911cb57ef1e1333012
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789654"
---
# <a name="typeparamref-c-programming-guide"></a>\<typeparamref> (C# programlama kılavuzu)

## <a name="syntax"></a>Sözdizimi

```xml
<typeparamref name="name"/>
```

## <a name="parameters"></a>Parametreler

- `name`

  Tür parametresinin adı. Adı çift tırnak işaretlerine (" ") ekin.

## <a name="remarks"></a>Açıklamalar

Genel tür ve yöntemlerdeki tür parametreleri hakkında daha fazla bilgi için [Genel Bilgiler'e](../generics/index.md)bakın.

Belge dosyasının tüketicilerinsözcüğü farklı şekillerde biçimlendirmesini sağlamak için bu etiketi kullanın, örneğin italik durumlarda.

Belge yorumlarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derle.

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# programlama kılavuzu](../index.md)
- [Belge açıklamaları için önerilen etiketler](./recommended-tags-for-documentation-comments.md)
