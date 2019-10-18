---
title: <list> (Visual Basic)
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
ms.openlocfilehash: 5d4295d485611e75e8b6c8d8f95e079654f0cfa3
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524756"
---
# <a name="list-visual-basic"></a><span data-ttu-id="81bfc-102">\<list > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="81bfc-102">\<list> (Visual Basic)</span></span>
<span data-ttu-id="81bfc-103">Bir liste veya tablo tanımlar.</span><span class="sxs-lookup"><span data-stu-id="81bfc-103">Defines a list or table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81bfc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="81bfc-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="81bfc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="81bfc-105">Parameters</span></span>  
 `type`  
 <span data-ttu-id="81bfc-106">Listenin türü.</span><span class="sxs-lookup"><span data-stu-id="81bfc-106">The type of the list.</span></span> <span data-ttu-id="81bfc-107">Bir madde işaretli liste için "madde işareti", numaralandırılmış liste için "numara" veya iki sütunlu bir tablo için "Tablo" olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="81bfc-107">Must be a "bullet" for a bulleted list, "number" for a numbered list, or "table" for a two-column table.</span></span>  
  
 `term`  
 <span data-ttu-id="81bfc-108">Yalnızca `type` "Table" olduğunda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="81bfc-108">Only used when `type` is "table."</span></span> <span data-ttu-id="81bfc-109">Description etiketinde tanımlanan, tanımlanacak bir terim.</span><span class="sxs-lookup"><span data-stu-id="81bfc-109">A term to define, which is defined in the description tag.</span></span>  
  
 `description`  
 <span data-ttu-id="81bfc-110">@No__t_0 "Bullet" veya "Number" olduğunda `description`, `type` "Tablo" olduğunda, `description` `term` tanımıdır.</span><span class="sxs-lookup"><span data-stu-id="81bfc-110">When `type` is "bullet" or "number," `description` is an item in the list When `type` is "table," `description` is the definition of `term`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81bfc-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="81bfc-111">Remarks</span></span>  
 <span data-ttu-id="81bfc-112">@No__t_0 bloğu, bir tablo ya da tanım listesinin başlığını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="81bfc-112">The `<listheader>` block defines the heading of either a table or definition list.</span></span> <span data-ttu-id="81bfc-113">Tablo tanımlarken, yalnızca başlıktaki `term` için bir giriş sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="81bfc-113">When defining a table, you only have to supply an entry for `term` in the heading.</span></span>  
  
 <span data-ttu-id="81bfc-114">Listedeki her öğe `<item>` bloğuyla belirtilir.</span><span class="sxs-lookup"><span data-stu-id="81bfc-114">Each item in the list is specified with an `<item>` block.</span></span> <span data-ttu-id="81bfc-115">Tanım listesi oluştururken hem `term` hem de `description` belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="81bfc-115">When creating a definition list, you must specify both `term` and `description`.</span></span> <span data-ttu-id="81bfc-116">Ancak, bir tablo, madde işaretli liste veya numaralandırılmış liste için yalnızca `description` bir giriş sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="81bfc-116">However, for a table, bulleted list, or numbered list, you only have to supply an entry for `description`.</span></span>  
  
 <span data-ttu-id="81bfc-117">Bir liste veya tablo gerektiği kadar çok sayıda `<item>` bloğuyla bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="81bfc-117">A list or table can have as many `<item>` blocks as needed.</span></span>  
  
 <span data-ttu-id="81bfc-118">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="81bfc-118">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81bfc-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="81bfc-119">Example</span></span>  
 <span data-ttu-id="81bfc-120">Bu örnek, açıklamalar bölümünde madde işaretli bir liste tanımlamak için `<list>` etiketini kullanır.</span><span class="sxs-lookup"><span data-stu-id="81bfc-120">This example uses the `<list>` tag to define a bulleted list in the remarks section.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="81bfc-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="81bfc-121">See also</span></span>

- [<span data-ttu-id="81bfc-122">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="81bfc-122">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
