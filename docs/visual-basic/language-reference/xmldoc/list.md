---
description: 'Aşağıdakiler hakkında daha fazla bilgi edinin: <list> (Visual Basic)'
title: <list>
ms.date: 07/20/2015
helpviewer_keywords:
- listheader XML tag
- <item> XML tag
- <list> XML tag
- <listheader> XML tag
- term XML tag
- list XML tag
- <description> XML tag
- description XML tag
- item XML tag
- <term> XML tag
ms.assetid: ec35fced-d58e-4520-a764-0691256e014b
ms.openlocfilehash: c9e2e8d1c370bfdeefae4a8f19b25acc6a336ecc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787441"
---
# <a name="list-visual-basic"></a><span data-ttu-id="5d203-103">\<list> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5d203-103">\<list> (Visual Basic)</span></span>

<span data-ttu-id="5d203-104">Bir liste veya tablo tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5d203-104">Defines a list or table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d203-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5d203-105">Syntax</span></span>  
  
```xml  
<list type="type">  
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
  
## <a name="parameters"></a><span data-ttu-id="5d203-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5d203-106">Parameters</span></span>  

 `type`  
 <span data-ttu-id="5d203-107">Listenin türü.</span><span class="sxs-lookup"><span data-stu-id="5d203-107">The type of the list.</span></span> <span data-ttu-id="5d203-108">Bir madde işaretli liste için "madde işareti", numaralandırılmış liste için "numara" veya iki sütunlu bir tablo için "Tablo" olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5d203-108">Must be a "bullet" for a bulleted list, "number" for a numbered list, or "table" for a two-column table.</span></span>  
  
 `term`  
 <span data-ttu-id="5d203-109">Yalnızca "Table" olduğunda kullanılır `type` .</span><span class="sxs-lookup"><span data-stu-id="5d203-109">Only used when `type` is "table."</span></span> <span data-ttu-id="5d203-110">Description etiketinde tanımlanan, tanımlanacak bir terim.</span><span class="sxs-lookup"><span data-stu-id="5d203-110">A term to define, which is defined in the description tag.</span></span>  
  
 `description`  
 <span data-ttu-id="5d203-111">" `type` İtem" veya "Number" olduğunda, " `description` Tablo", `type` `description` tanımdır `term` .</span><span class="sxs-lookup"><span data-stu-id="5d203-111">When `type` is "bullet" or "number," `description` is an item in the list When `type` is "table," `description` is the definition of `term`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d203-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5d203-112">Remarks</span></span>  

 <span data-ttu-id="5d203-113">`<listheader>`Blok, bir tablo ya da tanım listesinin başlığını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5d203-113">The `<listheader>` block defines the heading of either a table or definition list.</span></span> <span data-ttu-id="5d203-114">Tablo tanımlarken, yalnızca başlıkta bir giriş sağlamanız gerekir `term` .</span><span class="sxs-lookup"><span data-stu-id="5d203-114">When defining a table, you only have to supply an entry for `term` in the heading.</span></span>  
  
 <span data-ttu-id="5d203-115">Listedeki her öğe bir `<item>` blokla belirtilir.</span><span class="sxs-lookup"><span data-stu-id="5d203-115">Each item in the list is specified with an `<item>` block.</span></span> <span data-ttu-id="5d203-116">Bir tanım listesi oluştururken, hem hem de belirtmeniz gerekir `term` `description` .</span><span class="sxs-lookup"><span data-stu-id="5d203-116">When creating a definition list, you must specify both `term` and `description`.</span></span> <span data-ttu-id="5d203-117">Ancak, bir tablo, madde işaretli liste veya numaralandırılmış liste için yalnızca bir giriş sağlamanız gerekir `description` .</span><span class="sxs-lookup"><span data-stu-id="5d203-117">However, for a table, bulleted list, or numbered list, you only have to supply an entry for `description`.</span></span>  
  
 <span data-ttu-id="5d203-118">Bir liste veya tablo gerektiği kadar çok `<item>` blok içerebilir.</span><span class="sxs-lookup"><span data-stu-id="5d203-118">A list or table can have as many `<item>` blocks as needed.</span></span>  
  
 <span data-ttu-id="5d203-119">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="5d203-119">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d203-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="5d203-120">Example</span></span>  

 <span data-ttu-id="5d203-121">Bu örnek, `<list>` açıklamalar bölümünde madde işaretli bir liste tanımlamak için etiketini kullanır.</span><span class="sxs-lookup"><span data-stu-id="5d203-121">This example uses the `<list>` tag to define a bulleted list in the remarks section.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="5d203-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d203-122">See also</span></span>

- [<span data-ttu-id="5d203-123">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="5d203-123">XML Comment Tags</span></span>](index.md)
