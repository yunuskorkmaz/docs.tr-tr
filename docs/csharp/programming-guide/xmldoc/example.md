---
title: <example> -C# Programlama Kılavuzu
description: XML hakkında bilgi edinin <example> Etiket. Bu etiket, bir yöntemin veya diğer kitaplık üyesinin nasıl kullanılacağına ilişkin bir örnek belirtmenize imkan sağlar.
ms.date: 07/20/2015
f1_keywords:
- <example>
- example
helpviewer_keywords:
- <example> C# XML tag
- example C# XML tag
ms.assetid: 32d6e73b-2554-4abb-83ee-a1e321334fd2
ms.openlocfilehash: 8f9b4fa4ac447b853008576a46be9beeb583b018
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103479126"
---
# <a name="example-c-programming-guide"></a><span data-ttu-id="bd828-105">\<example> (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="bd828-105">\<example> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="bd828-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bd828-106">Syntax</span></span>

```xml
<example>description</example>
```

## <a name="parameters"></a><span data-ttu-id="bd828-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bd828-107">Parameters</span></span>

- `description`

  <span data-ttu-id="bd828-108">Kod örneğinin açıklaması.</span><span class="sxs-lookup"><span data-stu-id="bd828-108">A description of the code sample.</span></span>

## <a name="remarks"></a><span data-ttu-id="bd828-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bd828-109">Remarks</span></span>

<span data-ttu-id="bd828-110">`<example>`Etiketi, bir yöntemi veya diğer kitaplık üyesini nasıl kullanacağınızı gösteren bir örnek belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="bd828-110">The `<example>` tag lets you specify an example of how to use a method or other library member.</span></span> <span data-ttu-id="bd828-111">Bu genellikle etiketinin kullanılmasını içerir [\<code>](./code.md) .</span><span class="sxs-lookup"><span data-stu-id="bd828-111">This commonly involves using the [\<code>](./code.md) tag.</span></span>

<span data-ttu-id="bd828-112">Belge açıklamalarını bir dosyaya işlemek için [**belgelerimdosyası**](../../language-reference/compiler-options/output.md#documentationfile) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="bd828-112">Compile with [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="bd828-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="bd828-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#3)]

## <a name="see-also"></a><span data-ttu-id="bd828-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd828-114">See also</span></span>

- [<span data-ttu-id="bd828-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="bd828-115">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="bd828-116">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="bd828-116">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
