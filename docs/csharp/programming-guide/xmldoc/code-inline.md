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
# <a name="c-c-programming-guide"></a><span data-ttu-id="68b46-104">\<c>(C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="68b46-104">\<c> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="68b46-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="68b46-105">Syntax</span></span>

```xml
<c>text</c>
```

## <a name="parameters"></a><span data-ttu-id="68b46-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="68b46-106">Parameters</span></span>

- `text`

  <span data-ttu-id="68b46-107">Kod olarak göstermek istediğiniz metin.</span><span class="sxs-lookup"><span data-stu-id="68b46-107">The text you would like to indicate as code.</span></span>

## <a name="remarks"></a><span data-ttu-id="68b46-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="68b46-108">Remarks</span></span>

<span data-ttu-id="68b46-109">`<c>`Etiketi, bir açıklama içindeki metnin kod olarak işaretlenmesi gerektiğini göstermek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="68b46-109">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="68b46-110">[\<code>](./code.md)Birden çok satırı kod olarak göstermek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="68b46-110">Use [\<code>](./code.md) to indicate multiple lines as code.</span></span>

<span data-ttu-id="68b46-111">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="68b46-111">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="68b46-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="68b46-112">Example</span></span>

[!code-csharp[csProgGuideDocComments#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#2)]
  
## <a name="see-also"></a><span data-ttu-id="68b46-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68b46-113">See also</span></span>

- [<span data-ttu-id="68b46-114">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="68b46-114">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="68b46-115">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="68b46-115">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
