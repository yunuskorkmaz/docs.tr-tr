---
title: "&lt;Liste&gt; (C# programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
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
caps.latest.revision: "11"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6d997f3692d21959daa8eaec9eeeac8c0a1dc9bb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltlistgt-c-programming-guide"></a><span data-ttu-id="48b43-102">&lt;Liste&gt; (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="48b43-102">&lt;list&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="48b43-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="48b43-103">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="48b43-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="48b43-104">Parameters</span></span>  
 `term`  
 <span data-ttu-id="48b43-105">İçinde tanımlanan tanımlamak için bir terim `description`.</span><span class="sxs-lookup"><span data-stu-id="48b43-105">A term to define, which will be defined in `description`.</span></span>  
  
 `description`  
 <span data-ttu-id="48b43-106">Her iki öğeyi madde işareti veya numaralı liste ya da tanımı bir `term`.</span><span class="sxs-lookup"><span data-stu-id="48b43-106">Either an item in a bullet or numbered list or the definition of a `term`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48b43-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="48b43-107">Remarks</span></span>  
 <span data-ttu-id="48b43-108">\<Listheader > bloğu bir tablo veya tanım listesi başlık satırının tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="48b43-108">The \<listheader> block is used to define the heading row of either a table or definition list.</span></span> <span data-ttu-id="48b43-109">Bir tablo tanımlarken, yalnızca bir giriş başlığı'nda terim için sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="48b43-109">When defining a table, you only need to supply an entry for term in the heading.</span></span>  
  
 <span data-ttu-id="48b43-110">Listedeki her bir öğe ile belirtilen bir \<öğesi > bloğu.</span><span class="sxs-lookup"><span data-stu-id="48b43-110">Each item in the list is specified with an \<item> block.</span></span> <span data-ttu-id="48b43-111">Bir tanım listesi oluştururken, her ikisi de belirtmeniz gerekir `term` ve `description`.</span><span class="sxs-lookup"><span data-stu-id="48b43-111">When creating a definition list, you will need to specify both `term` and `description`.</span></span> <span data-ttu-id="48b43-112">Ancak, bir tablo, listeyi veya numaralandırılmış listesi için yalnızca bir giriş için sağlamanız gerekir `description`.</span><span class="sxs-lookup"><span data-stu-id="48b43-112">However, for a table, bulleted list, or numbered list, you only need to supply an entry for `description`.</span></span>  
  
 <span data-ttu-id="48b43-113">Bir liste veya tablo kadar olabilir \<öğesi > gerektiğinde engeller.</span><span class="sxs-lookup"><span data-stu-id="48b43-113">A list or table can have as many \<item> blocks as needed.</span></span>  
  
 <span data-ttu-id="48b43-114">İle derleme [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) bir dosyaya işlem belgesi açıklamaları için.</span><span class="sxs-lookup"><span data-stu-id="48b43-114">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48b43-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="48b43-115">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#6](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/list_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="48b43-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="48b43-116">See Also</span></span>  
 [<span data-ttu-id="48b43-117">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="48b43-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="48b43-118">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="48b43-118">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
