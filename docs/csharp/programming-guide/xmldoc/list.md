---
title: '&lt;Liste&gt; (C# programlama Kılavuzu)'
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
ms.openlocfilehash: 768490424403f1235873a681ffba3367e3f128b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33337736"
---
# <a name="ltlistgt-c-programming-guide"></a><span data-ttu-id="c307f-102">&lt;Liste&gt; (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="c307f-102">&lt;list&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="c307f-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c307f-103">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="c307f-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c307f-104">Parameters</span></span>  
 `term`  
 <span data-ttu-id="c307f-105">İçinde tanımlanan tanımlamak için bir terim `description`.</span><span class="sxs-lookup"><span data-stu-id="c307f-105">A term to define, which will be defined in `description`.</span></span>  
  
 `description`  
 <span data-ttu-id="c307f-106">Her iki öğeyi madde işareti veya numaralı liste ya da tanımı bir `term`.</span><span class="sxs-lookup"><span data-stu-id="c307f-106">Either an item in a bullet or numbered list or the definition of a `term`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c307f-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c307f-107">Remarks</span></span>  
 <span data-ttu-id="c307f-108">\<Listheader > bloğu bir tablo veya tanım listesi başlık satırının tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c307f-108">The \<listheader> block is used to define the heading row of either a table or definition list.</span></span> <span data-ttu-id="c307f-109">Bir tablo tanımlarken, yalnızca bir giriş başlığı'nda terim için sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c307f-109">When defining a table, you only need to supply an entry for term in the heading.</span></span>  
  
 <span data-ttu-id="c307f-110">Listedeki her bir öğe ile belirtilen bir \<öğesi > bloğu.</span><span class="sxs-lookup"><span data-stu-id="c307f-110">Each item in the list is specified with an \<item> block.</span></span> <span data-ttu-id="c307f-111">Bir tanım listesi oluştururken, her ikisi de belirtmeniz gerekir `term` ve `description`.</span><span class="sxs-lookup"><span data-stu-id="c307f-111">When creating a definition list, you will need to specify both `term` and `description`.</span></span> <span data-ttu-id="c307f-112">Ancak, bir tablo, listeyi veya numaralandırılmış listesi için yalnızca bir giriş için sağlamanız gerekir `description`.</span><span class="sxs-lookup"><span data-stu-id="c307f-112">However, for a table, bulleted list, or numbered list, you only need to supply an entry for `description`.</span></span>  
  
 <span data-ttu-id="c307f-113">Bir liste veya tablo kadar olabilir \<öğesi > gerektiğinde engeller.</span><span class="sxs-lookup"><span data-stu-id="c307f-113">A list or table can have as many \<item> blocks as needed.</span></span>  
  
 <span data-ttu-id="c307f-114">İle derleme [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) bir dosyaya işlem belgesi açıklamaları için.</span><span class="sxs-lookup"><span data-stu-id="c307f-114">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c307f-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="c307f-115">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#6](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/list_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="c307f-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c307f-116">See Also</span></span>  
 [<span data-ttu-id="c307f-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c307f-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c307f-118">Belge Açıklamaları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="c307f-118">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
