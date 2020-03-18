---
title: <remarks> - C# programlama kılavuzu
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: e37dac9cb9fed1df6ca027f09f2c95dbbc8ea66d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793379"
---
# <a name="remarks-c-programming-guide"></a><span data-ttu-id="c2372-102">\<açıklamalar> (C# programlama kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="c2372-102">\<remarks> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="c2372-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c2372-103">Syntax</span></span>

```xml
<remarks>description</remarks>
```

## <a name="parameters"></a><span data-ttu-id="c2372-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c2372-104">Parameters</span></span>

- `Description`

  <span data-ttu-id="c2372-105">Üyenin açıklaması.</span><span class="sxs-lookup"><span data-stu-id="c2372-105">A description of the member.</span></span>

## <a name="remarks"></a><span data-ttu-id="c2372-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c2372-106">Remarks</span></span>

<span data-ttu-id="c2372-107">Etiketler> \<açıklamalar, [ \<özet>](./summary.md)ile belirtilen bilgileri tamamlayarak, bir tür hakkında bilgi eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c2372-107">The \<remarks> tag is used to add information about a type, supplementing the information specified with [\<summary>](./summary.md).</span></span> <span data-ttu-id="c2372-108">Bu bilgiler Nesne Tarayıcı penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c2372-108">This information is displayed in the Object Browser window.</span></span>

<span data-ttu-id="c2372-109">Belge yorumlarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derle.</span><span class="sxs-lookup"><span data-stu-id="c2372-109">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="c2372-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="c2372-110">Example</span></span>

[!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]

## <a name="see-also"></a><span data-ttu-id="c2372-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2372-111">See also</span></span>

- [<span data-ttu-id="c2372-112">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c2372-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c2372-113">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="c2372-113">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
