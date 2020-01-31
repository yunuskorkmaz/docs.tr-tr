---
title: <returns> - C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- returns
- <returns>
helpviewer_keywords:
- <returns> C# XML tag
- returns C# XML tag
ms.assetid: bb2d9958-62fc-47c7-9511-6311171f119f
ms.openlocfilehash: 784d9effa589c962b8a2b982fd199f74309fb4dc
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789704"
---
# <a name="returns-c-programming-guide"></a><span data-ttu-id="4fb32-102">\<> döndürür (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="4fb32-102">\<returns> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="4fb32-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4fb32-103">Syntax</span></span>

```xml
<returns>description</returns>
```

## <a name="parameters"></a><span data-ttu-id="4fb32-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4fb32-104">Parameters</span></span>

- `description`

  <span data-ttu-id="4fb32-105">Dönüş değerinin açıklaması.</span><span class="sxs-lookup"><span data-stu-id="4fb32-105">A description of the return value.</span></span>

## <a name="remarks"></a><span data-ttu-id="4fb32-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4fb32-106">Remarks</span></span>

<span data-ttu-id="4fb32-107">\<, dönüş değerini açıklayacak bir yöntem bildirimine ilişkin açıklamada > etiketini döndürür.</span><span class="sxs-lookup"><span data-stu-id="4fb32-107">The \<returns> tag should be used in the comment for a method declaration to describe the return value.</span></span>

<span data-ttu-id="4fb32-108">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="4fb32-108">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="4fb32-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="4fb32-109">Example</span></span>

[!code-csharp[csProgGuideDocComments#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#10)]

## <a name="see-also"></a><span data-ttu-id="4fb32-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4fb32-110">See also</span></span>

- [<span data-ttu-id="4fb32-111">C#Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4fb32-111">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="4fb32-112">Belge açıklamaları için önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="4fb32-112">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
