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
ms.openlocfilehash: 2227dd8bd4d81f5fda8cf529e18c7a613cca6b8e
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477818"
---
# <a name="remarks-c-programming-guide"></a><span data-ttu-id="b7d5e-106">\<remarks> (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="b7d5e-106">\<remarks> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="b7d5e-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b7d5e-107">Syntax</span></span>

```xml
<remarks>description</remarks>
```

## <a name="parameters"></a><span data-ttu-id="b7d5e-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b7d5e-108">Parameters</span></span>

- `Description`

  <span data-ttu-id="b7d5e-109">Üyenin açıklaması.</span><span class="sxs-lookup"><span data-stu-id="b7d5e-109">A description of the member.</span></span>

## <a name="remarks"></a><span data-ttu-id="b7d5e-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b7d5e-110">Remarks</span></span>

<span data-ttu-id="b7d5e-111">`<remarks>`Etiketi, ile belirtilen bilgileri kullanarak bir tür hakkında bilgi eklemek için kullanılır [\<summary>](./summary.md) .</span><span class="sxs-lookup"><span data-stu-id="b7d5e-111">The `<remarks>` tag is used to add information about a type, supplementing the information specified with [\<summary>](./summary.md).</span></span> <span data-ttu-id="b7d5e-112">Bu bilgiler Nesne Tarayıcısı penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b7d5e-112">This information is displayed in the Object Browser window.</span></span>

<span data-ttu-id="b7d5e-113">Belge açıklamalarını bir dosyaya işlemek için [**belgelerimdosyası**](../../language-reference/compiler-options/output.md#documentationfile) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="b7d5e-113">Compile with [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="b7d5e-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="b7d5e-114">Example</span></span>

[!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]

## <a name="see-also"></a><span data-ttu-id="b7d5e-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b7d5e-115">See also</span></span>

- [<span data-ttu-id="b7d5e-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b7d5e-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b7d5e-117">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="b7d5e-117">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
