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
ms.openlocfilehash: 9ac1d749d18a9d02ce28f8cf600495f345ec0e89
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489279"
---
# <a name="list-c-programming-guide"></a><span data-ttu-id="f0600-102">\<Liste > (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="f0600-102">\<list> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="f0600-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f0600-103">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="f0600-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f0600-104">Parameters</span></span>  
 `term`  
 <span data-ttu-id="f0600-105">İçinde tanımlanan tanımlamak için bir terim `description`.</span><span class="sxs-lookup"><span data-stu-id="f0600-105">A term to define, which will be defined in `description`.</span></span>  
  
 `description`  
 <span data-ttu-id="f0600-106">Bir ya da öğe bir madde işareti veya numaralı liste tanımını bir `term`.</span><span class="sxs-lookup"><span data-stu-id="f0600-106">Either an item in a bullet or numbered list or the definition of a `term`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0600-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f0600-107">Remarks</span></span>  
 <span data-ttu-id="f0600-108">\<Listheader > blok satırında bir tablo veya tanım listesi tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f0600-108">The \<listheader> block is used to define the heading row of either a table or definition list.</span></span> <span data-ttu-id="f0600-109">Bir tablo tanımlarken, yalnızca bir giriş başlığı hükmün sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f0600-109">When defining a table, you only need to supply an entry for term in the heading.</span></span>  
  
 <span data-ttu-id="f0600-110">Listedeki her bir öğe ile belirtilen bir \<öğesi > bloğu.</span><span class="sxs-lookup"><span data-stu-id="f0600-110">Each item in the list is specified with an \<item> block.</span></span> <span data-ttu-id="f0600-111">Tanım listesi oluştururken, her ikisi de belirtmeniz gerekir `term` ve `description`.</span><span class="sxs-lookup"><span data-stu-id="f0600-111">When creating a definition list, you will need to specify both `term` and `description`.</span></span> <span data-ttu-id="f0600-112">Ancak, bir tablo, madde işaretli liste veya numaralı liste için bir giriş sağlamanız yeterlidir `description`.</span><span class="sxs-lookup"><span data-stu-id="f0600-112">However, for a table, bulleted list, or numbered list, you only need to supply an entry for `description`.</span></span>  
  
 <span data-ttu-id="f0600-113">Bir listeyi veya tabloyu kadar olabilir \<öğesi > gerektiğinde engeller.</span><span class="sxs-lookup"><span data-stu-id="f0600-113">A list or table can have as many \<item> blocks as needed.</span></span>  
  
 <span data-ttu-id="f0600-114">Derleme [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="f0600-114">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0600-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="f0600-115">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#6)]  
  
## <a name="see-also"></a><span data-ttu-id="f0600-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0600-116">See also</span></span>

- [<span data-ttu-id="f0600-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f0600-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="f0600-118">Belge Açıklamaları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="f0600-118">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
