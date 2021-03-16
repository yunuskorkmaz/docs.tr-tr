---
title: <paramref> -C# Programlama Kılavuzu
description: XML etiketi hakkında bilgi edinin <paramref> . Bu etiket, koddaki bir sözcüğün bir parametre olduğunu göstermek için bir yol sağlar.
ms.date: 07/20/2015
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
ms.openlocfilehash: e559a899aad7806bb7ccef32be49954fabed6a32
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477878"
---
# <a name="paramref-c-programming-guide"></a><span data-ttu-id="7f763-104">\<paramref> (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="7f763-104">\<paramref> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="7f763-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7f763-105">Syntax</span></span>

```xml
<paramref name="name"/>
```

## <a name="parameters"></a><span data-ttu-id="7f763-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7f763-106">Parameters</span></span>

- `name`

  <span data-ttu-id="7f763-107">Başvurabileceğiniz parametrenin adı.</span><span class="sxs-lookup"><span data-stu-id="7f763-107">The name of the parameter to refer to.</span></span> <span data-ttu-id="7f763-108">Adı çift tırnak işareti ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="7f763-108">Enclose the name in double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="7f763-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7f763-109">Remarks</span></span>

<span data-ttu-id="7f763-110">`<paramref>`Etiketi, kod açıklamalarındaki bir sözcüğün, örneğin bir `<summary>` veya bloğunda bir parametreye başvurduğunu göstermek için bir yol sağlar `<remarks>` .</span><span class="sxs-lookup"><span data-stu-id="7f763-110">The `<paramref>` tag gives you a way to indicate that a word in the code comments, for example in a `<summary>` or `<remarks>` block refers to a parameter.</span></span> <span data-ttu-id="7f763-111">Bu sözcüğü, kalın veya italik yazı tipiyle olduğu gibi farklı bir şekilde biçimlendirmek için XML dosyası işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="7f763-111">The XML file can be processed to format this word in some distinct way, such as with a bold or italic font.</span></span>

<span data-ttu-id="7f763-112">Belge açıklamalarını bir dosyaya işlemek için [**belgelerimdosyası**](../../language-reference/compiler-options/output.md#documentationfile) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="7f763-112">Compile with [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="7f763-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="7f763-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#7)]

## <a name="see-also"></a><span data-ttu-id="7f763-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f763-114">See also</span></span>

- [<span data-ttu-id="7f763-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7f763-115">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="7f763-116">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="7f763-116">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
