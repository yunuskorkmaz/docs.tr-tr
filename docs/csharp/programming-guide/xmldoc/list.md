---
title: <list> - C# Programlama Kılavuzu
ms.custom: seodec18
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
ms.openlocfilehash: 0df6653171aa0366f555c39e4644f13b2b7384f9
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523435"
---
# <a name="list-c-programming-guide"></a><span data-ttu-id="a5181-102">\<list > (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="a5181-102">\<list> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="a5181-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a5181-103">Syntax</span></span>  
  
```xml  
<list type="bullet" | "number" | "table">  
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
  
## <a name="parameters"></a><span data-ttu-id="a5181-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a5181-104">Parameters</span></span>  
 `term`  
 <span data-ttu-id="a5181-105">@No__t_0 tanımlanacak bir terim.</span><span class="sxs-lookup"><span data-stu-id="a5181-105">A term to define, which will be defined in `description`.</span></span>  
  
 `description`  
 <span data-ttu-id="a5181-106">Bir madde işareti veya numaralandırılmış listedeki bir öğe ya da bir `term` tanımı.</span><span class="sxs-lookup"><span data-stu-id="a5181-106">Either an item in a bullet or numbered list or the definition of a `term`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5181-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a5181-107">Remarks</span></span>  
 <span data-ttu-id="a5181-108">@No__t_0listheader > bloğu, bir tablo ya da tanım listesinin başlık satırını tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a5181-108">The \<listheader> block is used to define the heading row of either a table or definition list.</span></span> <span data-ttu-id="a5181-109">Bir tablo tanımlarken, yalnızca başlıktaki terim için bir giriş sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a5181-109">When defining a table, you only need to supply an entry for term in the heading.</span></span>  
  
 <span data-ttu-id="a5181-110">Listedeki her öğe bir \<item > bloğu ile belirtilir.</span><span class="sxs-lookup"><span data-stu-id="a5181-110">Each item in the list is specified with an \<item> block.</span></span> <span data-ttu-id="a5181-111">Tanım listesi oluştururken hem `term` hem de `description` belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a5181-111">When creating a definition list, you will need to specify both `term` and `description`.</span></span> <span data-ttu-id="a5181-112">Ancak, bir tablo, madde işaretli liste veya numaralandırılmış liste için yalnızca `description` için bir giriş sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a5181-112">However, for a table, bulleted list, or numbered list, you only need to supply an entry for `description`.</span></span>  
  
 <span data-ttu-id="a5181-113">Bir liste veya tablo, gereken sayıda > blobundan \<item sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="a5181-113">A list or table can have as many \<item> blocks as needed.</span></span>  
  
 <span data-ttu-id="a5181-114">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="a5181-114">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5181-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="a5181-115">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#6)]  
  
## <a name="see-also"></a><span data-ttu-id="a5181-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a5181-116">See also</span></span>

- [<span data-ttu-id="a5181-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a5181-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a5181-118">Belge Açıklamaları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="a5181-118">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
