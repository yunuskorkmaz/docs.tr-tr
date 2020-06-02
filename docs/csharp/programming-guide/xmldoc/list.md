---
title: <list> -C# Programlama Kılavuzu
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
ms.openlocfilehash: 78eec992671dab1aa59717a007a8e3a2662f6e87
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287343"
---
# <a name="list-c-programming-guide"></a><span data-ttu-id="fdfc5-102">\<list>(C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="fdfc5-102">\<list> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="fdfc5-103">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="fdfc5-103">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="fdfc5-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fdfc5-104">Parameters</span></span>

- `term`

  <span data-ttu-id="fdfc5-105">' De tanımlanacak bir terim `description` .</span><span class="sxs-lookup"><span data-stu-id="fdfc5-105">A term to define, which will be defined in `description`.</span></span>

- `description`

  <span data-ttu-id="fdfc5-106">Bir madde işareti veya numaralandırılmış listedeki bir öğe ya da bir tanımı `term` .</span><span class="sxs-lookup"><span data-stu-id="fdfc5-106">Either an item in a bullet or numbered list or the definition of a `term`.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="fdfc5-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fdfc5-107">Remarks</span></span>

<span data-ttu-id="fdfc5-108">`<listheader>`Blok, bir tablo ya da tanım listesinin başlık satırını tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fdfc5-108">The `<listheader>` block is used to define the heading row of either a table or definition list.</span></span> <span data-ttu-id="fdfc5-109">Bir tablo tanımlarken, yalnızca başlıktaki terim için bir giriş sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fdfc5-109">When defining a table, you only need to supply an entry for term in the heading.</span></span>

<span data-ttu-id="fdfc5-110">Listedeki her öğe bir `<item>` blokla belirtilir.</span><span class="sxs-lookup"><span data-stu-id="fdfc5-110">Each item in the list is specified with an `<item>` block.</span></span> <span data-ttu-id="fdfc5-111">Bir tanım listesi oluştururken, hem hem de belirtmeniz gerekecektir `term` `description` .</span><span class="sxs-lookup"><span data-stu-id="fdfc5-111">When creating a definition list, you will need to specify both `term` and `description`.</span></span> <span data-ttu-id="fdfc5-112">Ancak, bir tablo, madde işaretli liste veya numaralandırılmış liste için yalnızca bir giriş sağlamanız gerekir `description` .</span><span class="sxs-lookup"><span data-stu-id="fdfc5-112">However, for a table, bulleted list, or numbered list, you only need to supply an entry for `description`.</span></span>

<span data-ttu-id="fdfc5-113">Bir liste veya tablo gerektiği kadar çok `<item>` blok içerebilir.</span><span class="sxs-lookup"><span data-stu-id="fdfc5-113">A list or table can have as many `<item>` blocks as needed.</span></span>

<span data-ttu-id="fdfc5-114">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="fdfc5-114">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="fdfc5-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="fdfc5-115">Example</span></span>

[!code-csharp[csProgGuideDocComments#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#6)]

## <a name="see-also"></a><span data-ttu-id="fdfc5-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fdfc5-116">See also</span></span>

- [<span data-ttu-id="fdfc5-117">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="fdfc5-117">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="fdfc5-118">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="fdfc5-118">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
