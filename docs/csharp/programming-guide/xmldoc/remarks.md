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
ms.openlocfilehash: 2227dd8bd4d81f5fda8cf529e18c7a613cca6b8e
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477818"
---
# <a name="remarks-c-programming-guide"></a>\<remarks> (C# Programlama Kılavuzu)

## <a name="syntax"></a>Sözdizimi

```xml
<remarks>description</remarks>
```

## <a name="parameters"></a>Parametreler

- `Description`

  Üyenin açıklaması.

## <a name="remarks"></a>Açıklamalar

`<remarks>`Etiketi, ile belirtilen bilgileri kullanarak bir tür hakkında bilgi eklemek için kullanılır [\<summary>](./summary.md) . Bu bilgiler Nesne Tarayıcısı penceresinde görüntülenir.

Belge açıklamalarını bir dosyaya işlemek için [**belgelerimdosyası**](../../language-reference/compiler-options/output.md#documentationfile) ile derleyin.

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Belge açıklamaları için önerilen etiketler](./recommended-tags-for-documentation-comments.md)
