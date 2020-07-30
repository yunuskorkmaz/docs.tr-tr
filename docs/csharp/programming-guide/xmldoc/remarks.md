---
title: <remarks> -C# Programlama Kılavuzu
description: XML hakkında bilgi edinin <remarks> Etiket. Bu etiket, ile belirtilen bilgileri kullanarak bir tür hakkında bilgi eklemek için kullanılır <summary>.
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: d38905d100e24158e7a1412f6be9f01a7ced2382
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381508"
---
# <a name="remarks-c-programming-guide"></a>\<remarks>(C# Programlama Kılavuzu)

## <a name="syntax"></a>Söz dizimi

```xml
<remarks>description</remarks>
```

## <a name="parameters"></a>Parametreler

- `Description`

  Üyenin açıklaması.

## <a name="remarks"></a>Açıklamalar

`<remarks>`Etiketi, ile belirtilen bilgileri kullanarak bir tür hakkında bilgi eklemek için kullanılır [\<summary>](./summary.md) . Bu bilgiler Nesne Tarayıcısı penceresinde görüntülenir.

Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Belge açıklamaları için önerilen etiketler](./recommended-tags-for-documentation-comments.md)
