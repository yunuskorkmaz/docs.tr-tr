---
title: <c> C# Programlama Kılavuzu
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
ms.openlocfilehash: d5b28ee6db52d191f8454592d792ac0a1e1dc73b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793452"
---
# <a name="c-c-programming-guide"></a><span data-ttu-id="2be2a-102">\<c > (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="2be2a-102">\<c> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="2be2a-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2be2a-103">Syntax</span></span>

```xml
<c>text</c>
```

## <a name="parameters"></a><span data-ttu-id="2be2a-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2be2a-104">Parameters</span></span>

- `text`

  <span data-ttu-id="2be2a-105">Kod olarak göstermek istediğiniz metin.</span><span class="sxs-lookup"><span data-stu-id="2be2a-105">The text you would like to indicate as code.</span></span>

## <a name="remarks"></a><span data-ttu-id="2be2a-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2be2a-106">Remarks</span></span>

<span data-ttu-id="2be2a-107">\<c > etiketi, bir açıklama içindeki metnin kod olarak işaretlenmesi gerektiğini belirtmek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="2be2a-107">The \<c> tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="2be2a-108">Birden çok satırı kod olarak göstermek için [\<kodu >](./code.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="2be2a-108">Use [\<code>](./code.md) to indicate multiple lines as code.</span></span>

<span data-ttu-id="2be2a-109">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="2be2a-109">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="2be2a-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="2be2a-110">Example</span></span>

[!code-csharp[csProgGuideDocComments#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#2)]
  
## <a name="see-also"></a><span data-ttu-id="2be2a-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2be2a-111">See also</span></span>

- [<span data-ttu-id="2be2a-112">C#Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2be2a-112">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="2be2a-113">Belge açıklamaları için önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="2be2a-113">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
