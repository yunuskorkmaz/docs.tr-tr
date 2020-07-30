---
title: <c>-C# Programlama Kılavuzu
description: XML etiketi hakkında bilgi edinin <c> . Bu etiket, bir açıklamada tek satırlık metni kod olarak işaretler, ancak <code>indicates multiple lines.
ms.date: 07/20/2015
f1_keywords:
- c
- <c>
helpviewer_keywords:
- text, marking as code [C#]
- code, marking text as [C#]
- c C# XML tag
- <c> C# XML tag
ms.assetid: aad5b16e-a29e-445e-bd0d-eea0b138d7b2
ms.openlocfilehash: 78e59e1df4b096782e0a97b6d12c21c843a1cb21
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87382028"
---
# <a name="c-c-programming-guide"></a>\<c>(C# Programlama Kılavuzu)

## <a name="syntax"></a>Söz dizimi

```xml
<c>text</c>
```

## <a name="parameters"></a>Parametreler

- `text`

  Kod olarak göstermek istediğiniz metin.

## <a name="remarks"></a>Açıklamalar

`<c>`Etiketi, bir açıklama içindeki metnin kod olarak işaretlenmesi gerektiğini göstermek için bir yol sağlar. [\<code>](./code.md)Birden çok satırı kod olarak göstermek için kullanın.

Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideDocComments#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#2)]
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# programlama kılavuzu](../index.md)
- [Belge açıklamaları için önerilen etiketler](./recommended-tags-for-documentation-comments.md)
