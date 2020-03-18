---
title: <returns> - C# programlama kılavuzu
ms.date: 07/20/2015
f1_keywords:
- returns
- <returns>
helpviewer_keywords:
- <returns> C# XML tag
- returns C# XML tag
ms.assetid: bb2d9958-62fc-47c7-9511-6311171f119f
ms.openlocfilehash: 784d9effa589c962b8a2b982fd199f74309fb4dc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789704"
---
# <a name="returns-c-programming-guide"></a><span data-ttu-id="6589b-102">\<> döndürür (C# programlama kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="6589b-102">\<returns> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="6589b-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6589b-103">Syntax</span></span>

```xml
<returns>description</returns>
```

## <a name="parameters"></a><span data-ttu-id="6589b-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6589b-104">Parameters</span></span>

- `description`

  <span data-ttu-id="6589b-105">İade değerinin açıklaması.</span><span class="sxs-lookup"><span data-stu-id="6589b-105">A description of the return value.</span></span>

## <a name="remarks"></a><span data-ttu-id="6589b-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6589b-106">Remarks</span></span>

<span data-ttu-id="6589b-107">İade \<> etiketi, iade değerini açıklamak için bir yöntem bildirimi için yorumda kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6589b-107">The \<returns> tag should be used in the comment for a method declaration to describe the return value.</span></span>

<span data-ttu-id="6589b-108">Belge yorumlarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derle.</span><span class="sxs-lookup"><span data-stu-id="6589b-108">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="6589b-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="6589b-109">Example</span></span>

[!code-csharp[csProgGuideDocComments#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#10)]

## <a name="see-also"></a><span data-ttu-id="6589b-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6589b-110">See also</span></span>

- [<span data-ttu-id="6589b-111">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6589b-111">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="6589b-112">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="6589b-112">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
