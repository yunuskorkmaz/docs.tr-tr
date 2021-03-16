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
ms.openlocfilehash: 6a098208a51ca31fe2278b7c696deb15a13f8e1e
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477812"
---
# <a name="returns-c-programming-guide"></a><span data-ttu-id="35df4-105">\<returns> (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="35df4-105">\<returns> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="35df4-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="35df4-106">Syntax</span></span>

```xml
<returns>description</returns>
```

## <a name="parameters"></a><span data-ttu-id="35df4-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="35df4-107">Parameters</span></span>

- `description`

  <span data-ttu-id="35df4-108">Dönüş değerinin açıklaması.</span><span class="sxs-lookup"><span data-stu-id="35df4-108">A description of the return value.</span></span>

## <a name="remarks"></a><span data-ttu-id="35df4-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="35df4-109">Remarks</span></span>

<span data-ttu-id="35df4-110">`<returns>`Etiket, dönüş değerini betimleyen bir yöntem bildirimine ilişkin açıklamada kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="35df4-110">The `<returns>` tag should be used in the comment for a method declaration to describe the return value.</span></span>

<span data-ttu-id="35df4-111">Belge açıklamalarını bir dosyaya işlemek için [**belgelerimdosyası**](../../language-reference/compiler-options/output.md#documentationfile) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="35df4-111">Compile with [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="35df4-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="35df4-112">Example</span></span>

[!code-csharp[csProgGuideDocComments#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#10)]

## <a name="see-also"></a><span data-ttu-id="35df4-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="35df4-113">See also</span></span>

- [<span data-ttu-id="35df4-114">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="35df4-114">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="35df4-115">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="35df4-115">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
