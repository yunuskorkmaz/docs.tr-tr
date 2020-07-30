---
title: <remarks> -C# Programlama Kılavuzu
description: XML hakkında bilgi edinin <remarks> Etiket. Bu etiket, ile belirtilen bilgileri kullanarak bir tür hakkında bilgi eklemek için kullanılır <summary>.
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: d38905d100e24158e7a1412f6be9f01a7ced2382
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381508"
---
# <a name="remarks-c-programming-guide"></a><span data-ttu-id="a13f5-106">\<remarks>(C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="a13f5-106">\<remarks> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="a13f5-107">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a13f5-107">Syntax</span></span>

```xml
<remarks>description</remarks>
```

## <a name="parameters"></a><span data-ttu-id="a13f5-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a13f5-108">Parameters</span></span>

- `Description`

  <span data-ttu-id="a13f5-109">Üyenin açıklaması.</span><span class="sxs-lookup"><span data-stu-id="a13f5-109">A description of the member.</span></span>

## <a name="remarks"></a><span data-ttu-id="a13f5-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a13f5-110">Remarks</span></span>

<span data-ttu-id="a13f5-111">`<remarks>`Etiketi, ile belirtilen bilgileri kullanarak bir tür hakkında bilgi eklemek için kullanılır [\<summary>](./summary.md) .</span><span class="sxs-lookup"><span data-stu-id="a13f5-111">The `<remarks>` tag is used to add information about a type, supplementing the information specified with [\<summary>](./summary.md).</span></span> <span data-ttu-id="a13f5-112">Bu bilgiler Nesne Tarayıcısı penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a13f5-112">This information is displayed in the Object Browser window.</span></span>

<span data-ttu-id="a13f5-113">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="a13f5-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="a13f5-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="a13f5-114">Example</span></span>

[!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]

## <a name="see-also"></a><span data-ttu-id="a13f5-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a13f5-115">See also</span></span>

- [<span data-ttu-id="a13f5-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a13f5-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a13f5-117">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="a13f5-117">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
