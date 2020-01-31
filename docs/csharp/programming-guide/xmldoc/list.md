---
title: <list> - C# Programlama Kılavuzu
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
ms.openlocfilehash: cb289b26e9bc12d561892c421fb40da18d8c3513
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789746"
---
# <a name="list-c-programming-guide"></a><span data-ttu-id="8e267-102">\<listesi > (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="8e267-102">\<list> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="8e267-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8e267-103">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="8e267-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8e267-104">Parameters</span></span>

- `term`

  <span data-ttu-id="8e267-105">`description`tanımlanacak bir terim.</span><span class="sxs-lookup"><span data-stu-id="8e267-105">A term to define, which will be defined in `description`.</span></span>

- `description`

  <span data-ttu-id="8e267-106">Bir madde işareti veya numaralandırılmış listedeki bir öğe ya da bir `term`tanımı.</span><span class="sxs-lookup"><span data-stu-id="8e267-106">Either an item in a bullet or numbered list or the definition of a `term`.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="8e267-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8e267-107">Remarks</span></span>

<span data-ttu-id="8e267-108">\<listheader > bloğu, bir tablo ya da tanım listesinin başlık satırını tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8e267-108">The \<listheader> block is used to define the heading row of either a table or definition list.</span></span> <span data-ttu-id="8e267-109">Bir tablo tanımlarken, yalnızca başlıktaki terim için bir giriş sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8e267-109">When defining a table, you only need to supply an entry for term in the heading.</span></span>

<span data-ttu-id="8e267-110">Listedeki her öğe, bir \<öğesi > bloğu ile belirtilir.</span><span class="sxs-lookup"><span data-stu-id="8e267-110">Each item in the list is specified with an \<item> block.</span></span> <span data-ttu-id="8e267-111">Tanım listesi oluştururken hem `term` hem de `description`belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8e267-111">When creating a definition list, you will need to specify both `term` and `description`.</span></span> <span data-ttu-id="8e267-112">Ancak, bir tablo, madde işaretli liste veya numaralandırılmış liste için yalnızca `description`için bir giriş sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8e267-112">However, for a table, bulleted list, or numbered list, you only need to supply an entry for `description`.</span></span>

<span data-ttu-id="8e267-113">Bir liste veya tablo, gereken sayıda \<öğe > bloğunu içerebilir.</span><span class="sxs-lookup"><span data-stu-id="8e267-113">A list or table can have as many \<item> blocks as needed.</span></span>

<span data-ttu-id="8e267-114">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="8e267-114">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="8e267-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="8e267-115">Example</span></span>

[!code-csharp[csProgGuideDocComments#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#6)]

## <a name="see-also"></a><span data-ttu-id="8e267-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e267-116">See also</span></span>

- [<span data-ttu-id="8e267-117">C#Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8e267-117">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="8e267-118">Belge açıklamaları için önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="8e267-118">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
