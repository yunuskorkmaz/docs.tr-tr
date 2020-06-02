---
title: <remarks> -C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: 739027786e02e559d86f990bf614e261b497c76f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287291"
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
