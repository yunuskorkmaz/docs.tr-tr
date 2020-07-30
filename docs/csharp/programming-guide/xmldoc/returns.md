---
title: <returns> -C# Programlama Kılavuzu
description: XML hakkında bilgi edinin <returns> Etiket. Bu etiket, dönüş değerini anlatmak için bir yöntem bildirimi açıklamasında kullanılır.
ms.date: 07/20/2015
f1_keywords:
- returns
- <returns>
helpviewer_keywords:
- <returns> C# XML tag
- returns C# XML tag
ms.assetid: bb2d9958-62fc-47c7-9511-6311171f119f
ms.openlocfilehash: e461d46df619a351048ae7942e59847d39e490f9
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381404"
---
# <a name="returns-c-programming-guide"></a><span data-ttu-id="a8169-105">\<returns>(C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="a8169-105">\<returns> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="a8169-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a8169-106">Syntax</span></span>

```xml
<returns>description</returns>
```

## <a name="parameters"></a><span data-ttu-id="a8169-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a8169-107">Parameters</span></span>

- `description`

  <span data-ttu-id="a8169-108">Dönüş değerinin açıklaması.</span><span class="sxs-lookup"><span data-stu-id="a8169-108">A description of the return value.</span></span>

## <a name="remarks"></a><span data-ttu-id="a8169-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a8169-109">Remarks</span></span>

<span data-ttu-id="a8169-110">`<returns>`Etiket, dönüş değerini betimleyen bir yöntem bildirimine ilişkin açıklamada kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a8169-110">The `<returns>` tag should be used in the comment for a method declaration to describe the return value.</span></span>

<span data-ttu-id="a8169-111">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="a8169-111">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="a8169-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="a8169-112">Example</span></span>

[!code-csharp[csProgGuideDocComments#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#10)]

## <a name="see-also"></a><span data-ttu-id="a8169-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a8169-113">See also</span></span>

- [<span data-ttu-id="a8169-114">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a8169-114">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="a8169-115">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="a8169-115">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
