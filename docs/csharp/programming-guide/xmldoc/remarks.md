---
title: <remarks> - C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: e37dac9cb9fed1df6ca027f09f2c95dbbc8ea66d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793379"
---
# <a name="remarks-c-programming-guide"></a>\<açıklamalar > (C# Programlama Kılavuzu)

## <a name="syntax"></a>Sözdizimi

```xml
<remarks>description</remarks>
```

## <a name="parameters"></a>Parametreler

- `Description`

  Üyenin açıklaması.

## <a name="remarks"></a>Açıklamalar

\<açıklamalar > etiketi, [\<özet >](./summary.md)ile belirtilen bilgileri kullanarak bir tür hakkında bilgi eklemek için kullanılır. Bu bilgiler Nesne Tarayıcısı penceresinde görüntülenir.

Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Belge açıklamaları için önerilen Etiketler](./recommended-tags-for-documentation-comments.md)
