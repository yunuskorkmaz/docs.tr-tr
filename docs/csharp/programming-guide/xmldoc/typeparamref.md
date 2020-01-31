---
title: <typeparamref> C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: 266eadad322fd3c4167c7a911cb57ef1e1333012
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789654"
---
# <a name="typeparamref-c-programming-guide"></a>\<typeparamref > (C# Programlama Kılavuzu)

## <a name="syntax"></a>Sözdizimi

```xml
<typeparamref name="name"/>
```

## <a name="parameters"></a>Parametreler

- `name`

  Tür parametresinin adı. Adı çift tırnak işareti ("") içine alın.

## <a name="remarks"></a>Açıklamalar

Genel türlerde ve yöntemlerde tür parametreleri hakkında daha fazla bilgi için bkz. [Genel türler](../generics/index.md).

Belge dosyasının tüketicilerini farklı bir şekilde (örneğin, italik) biçimlendirmesini sağlamak için bu etiketi kullanın.

Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#Programlama Kılavuzu](../index.md)
- [Belge açıklamaları için önerilen Etiketler](./recommended-tags-for-documentation-comments.md)
