---
title: <returns> -C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- returns
- <returns>
helpviewer_keywords:
- <returns> C# XML tag
- returns C# XML tag
ms.assetid: bb2d9958-62fc-47c7-9511-6311171f119f
ms.openlocfilehash: 7bc950a8d89a3ac2b5c3b7a68e05c7778e97f85c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287239"
---
# <a name="returns-c-programming-guide"></a><span data-ttu-id="cfbc9-102">\<returns>(C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="cfbc9-102">\<returns> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="cfbc9-103">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="cfbc9-103">Syntax</span></span>

```xml
<returns>description</returns>
```

## <a name="parameters"></a><span data-ttu-id="cfbc9-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cfbc9-104">Parameters</span></span>

- `description`

  <span data-ttu-id="cfbc9-105">Dönüş değerinin açıklaması.</span><span class="sxs-lookup"><span data-stu-id="cfbc9-105">A description of the return value.</span></span>

## <a name="remarks"></a><span data-ttu-id="cfbc9-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cfbc9-106">Remarks</span></span>

<span data-ttu-id="cfbc9-107">`<returns>`Etiket, dönüş değerini betimleyen bir yöntem bildirimine ilişkin açıklamada kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cfbc9-107">The `<returns>` tag should be used in the comment for a method declaration to describe the return value.</span></span>

<span data-ttu-id="cfbc9-108">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="cfbc9-108">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="cfbc9-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="cfbc9-109">Example</span></span>

[!code-csharp[csProgGuideDocComments#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#10)]

## <a name="see-also"></a><span data-ttu-id="cfbc9-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cfbc9-110">See also</span></span>

- [<span data-ttu-id="cfbc9-111">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="cfbc9-111">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="cfbc9-112">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="cfbc9-112">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
