---
title: <c>-C# Programlama Kılavuzu
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
ms.openlocfilehash: a09bcd069e2f85f4a21736cb218c42c0e481d70b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287473"
---
# <a name="c-c-programming-guide"></a><span data-ttu-id="db330-102">\<c>(C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="db330-102">\<c> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="db330-103">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="db330-103">Syntax</span></span>

```xml
<c>text</c>
```

## <a name="parameters"></a><span data-ttu-id="db330-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="db330-104">Parameters</span></span>

- `text`

  <span data-ttu-id="db330-105">Kod olarak göstermek istediğiniz metin.</span><span class="sxs-lookup"><span data-stu-id="db330-105">The text you would like to indicate as code.</span></span>

## <a name="remarks"></a><span data-ttu-id="db330-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="db330-106">Remarks</span></span>

<span data-ttu-id="db330-107">`<c>`Etiketi, bir açıklama içindeki metnin kod olarak işaretlenmesi gerektiğini göstermek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="db330-107">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="db330-108">[\<code>](./code.md)Birden çok satırı kod olarak göstermek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="db330-108">Use [\<code>](./code.md) to indicate multiple lines as code.</span></span>

<span data-ttu-id="db330-109">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="db330-109">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="db330-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="db330-110">Example</span></span>

[!code-csharp[csProgGuideDocComments#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#2)]
  
## <a name="see-also"></a><span data-ttu-id="db330-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db330-111">See also</span></span>

- [<span data-ttu-id="db330-112">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="db330-112">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="db330-113">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="db330-113">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
