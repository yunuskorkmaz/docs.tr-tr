---
title: <list> -C# Programlama Kılavuzu
description: XML hakkında bilgi edinin <list> Etiket. Bu etiket, ' item ' blokları kullanılarak tablolar ve tanım, madde işaretli veya numaralandırılmış listeler oluşturmak için kullanılır.
ms.date: 07/20/2015
f1_keywords:
- list
- <list>
helpviewer_keywords:
- list C# XML tag
- listheader C# XML tag
- <listheader> C# XML tag
- item C# XML tag
- <item> C# XML tag
- <list> C# XML tag
ms.assetid: c9620b1b-c2e6-43f1-ab88-8ab47308ffec
ms.openlocfilehash: 361c2e6f343554a9b8519c3b2e41219b209e682d
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381872"
---
# <a name="list-c-programming-guide"></a><span data-ttu-id="14a05-105">\<list>(C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="14a05-105">\<list> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="14a05-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="14a05-106">Syntax</span></span>

```xml
<list type="bullet|number|table">
    <listheader>
        <term>term</term>
        <description>description</description>
    </listheader>
    <item>
        <term>term</term>
        <description>description</description>
    </item>
</list>
```

## <a name="parameters"></a><span data-ttu-id="14a05-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="14a05-107">Parameters</span></span>

- `term`

  <span data-ttu-id="14a05-108">' De tanımlanacak bir terim `description` .</span><span class="sxs-lookup"><span data-stu-id="14a05-108">A term to define, which will be defined in `description`.</span></span>

- `description`

  <span data-ttu-id="14a05-109">Bir madde işareti veya numaralandırılmış listedeki bir öğe ya da bir tanımı `term` .</span><span class="sxs-lookup"><span data-stu-id="14a05-109">Either an item in a bullet or numbered list or the definition of a `term`.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="14a05-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="14a05-110">Remarks</span></span>

<span data-ttu-id="14a05-111">`<listheader>`Blok, bir tablo ya da tanım listesinin başlık satırını tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="14a05-111">The `<listheader>` block is used to define the heading row of either a table or definition list.</span></span> <span data-ttu-id="14a05-112">Bir tablo tanımlarken, yalnızca başlıktaki terim için bir giriş sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="14a05-112">When defining a table, you only need to supply an entry for term in the heading.</span></span>

<span data-ttu-id="14a05-113">Listedeki her öğe bir `<item>` blokla belirtilir.</span><span class="sxs-lookup"><span data-stu-id="14a05-113">Each item in the list is specified with an `<item>` block.</span></span> <span data-ttu-id="14a05-114">Bir tanım listesi oluştururken, hem hem de belirtmeniz gerekecektir `term` `description` .</span><span class="sxs-lookup"><span data-stu-id="14a05-114">When creating a definition list, you will need to specify both `term` and `description`.</span></span> <span data-ttu-id="14a05-115">Ancak, bir tablo, madde işaretli liste veya numaralandırılmış liste için yalnızca bir giriş sağlamanız gerekir `description` .</span><span class="sxs-lookup"><span data-stu-id="14a05-115">However, for a table, bulleted list, or numbered list, you only need to supply an entry for `description`.</span></span>

<span data-ttu-id="14a05-116">Bir liste veya tablo gerektiği kadar çok `<item>` blok içerebilir.</span><span class="sxs-lookup"><span data-stu-id="14a05-116">A list or table can have as many `<item>` blocks as needed.</span></span>

<span data-ttu-id="14a05-117">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="14a05-117">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="14a05-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="14a05-118">Example</span></span>

[!code-csharp[csProgGuideDocComments#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#6)]

## <a name="see-also"></a><span data-ttu-id="14a05-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14a05-119">See also</span></span>

- [<span data-ttu-id="14a05-120">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="14a05-120">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="14a05-121">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="14a05-121">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
