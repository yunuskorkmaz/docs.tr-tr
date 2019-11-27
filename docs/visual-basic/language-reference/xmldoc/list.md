---
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
ms.openlocfilehash: db5c571d2f2c59419c886f6596f4e4dbd30d7baf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352317"
---
# <a name="list-visual-basic"></a><span data-ttu-id="d683f-101">\<listesi > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d683f-101">\<list> (Visual Basic)</span></span>
<span data-ttu-id="d683f-102">Bir liste veya tablo tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d683f-102">Defines a list or table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d683f-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d683f-103">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d683f-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d683f-104">Parameters</span></span>  
 `type`  
 <span data-ttu-id="d683f-105">Listenin türü.</span><span class="sxs-lookup"><span data-stu-id="d683f-105">The type of the list.</span></span> <span data-ttu-id="d683f-106">Bir madde işaretli liste için "madde işareti", numaralandırılmış liste için "numara" veya iki sütunlu bir tablo için "Tablo" olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d683f-106">Must be a "bullet" for a bulleted list, "number" for a numbered list, or "table" for a two-column table.</span></span>  
  
 `term`  
 <span data-ttu-id="d683f-107">Yalnızca `type` "Table" olduğunda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d683f-107">Only used when `type` is "table."</span></span> <span data-ttu-id="d683f-108">Description etiketinde tanımlanan, tanımlanacak bir terim.</span><span class="sxs-lookup"><span data-stu-id="d683f-108">A term to define, which is defined in the description tag.</span></span>  
  
 `description`  
 <span data-ttu-id="d683f-109">`type` "Bullet" veya "Number" olduğunda `description`, `type` "Tablo" olduğunda, `description` `term`tanımıdır.</span><span class="sxs-lookup"><span data-stu-id="d683f-109">When `type` is "bullet" or "number," `description` is an item in the list When `type` is "table," `description` is the definition of `term`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d683f-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d683f-110">Remarks</span></span>  
 <span data-ttu-id="d683f-111">`<listheader>` bloğu, bir tablo ya da tanım listesinin başlığını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d683f-111">The `<listheader>` block defines the heading of either a table or definition list.</span></span> <span data-ttu-id="d683f-112">Tablo tanımlarken, yalnızca başlıktaki `term` için bir giriş sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d683f-112">When defining a table, you only have to supply an entry for `term` in the heading.</span></span>  
  
 <span data-ttu-id="d683f-113">Listedeki her öğe `<item>` bloğuyla belirtilir.</span><span class="sxs-lookup"><span data-stu-id="d683f-113">Each item in the list is specified with an `<item>` block.</span></span> <span data-ttu-id="d683f-114">Tanım listesi oluştururken hem `term` hem de `description`belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d683f-114">When creating a definition list, you must specify both `term` and `description`.</span></span> <span data-ttu-id="d683f-115">Ancak, bir tablo, madde işaretli liste veya numaralandırılmış liste için yalnızca `description`bir giriş sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d683f-115">However, for a table, bulleted list, or numbered list, you only have to supply an entry for `description`.</span></span>  
  
 <span data-ttu-id="d683f-116">Bir liste veya tablo gerektiği kadar çok sayıda `<item>` bloğuyla bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="d683f-116">A list or table can have as many `<item>` blocks as needed.</span></span>  
  
 <span data-ttu-id="d683f-117">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="d683f-117">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d683f-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="d683f-118">Example</span></span>  
 <span data-ttu-id="d683f-119">Bu örnek, açıklamalar bölümünde madde işaretli bir liste tanımlamak için `<list>` etiketini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d683f-119">This example uses the `<list>` tag to define a bulleted list in the remarks section.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="d683f-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d683f-120">See also</span></span>

- [<span data-ttu-id="d683f-121">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="d683f-121">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
