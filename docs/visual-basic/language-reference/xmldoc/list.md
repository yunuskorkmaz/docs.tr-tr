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
ms.openlocfilehash: 900cd8c467a21812d980cffa7e41120ae557704b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872782"
---
# <a name="list-visual-basic"></a><span data-ttu-id="d71f6-101">\<list> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d71f6-101">\<list> (Visual Basic)</span></span>

<span data-ttu-id="d71f6-102">Bir liste veya tablo tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d71f6-102">Defines a list or table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d71f6-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d71f6-103">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d71f6-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d71f6-104">Parameters</span></span>  

 `type`  
 <span data-ttu-id="d71f6-105">Listenin türü.</span><span class="sxs-lookup"><span data-stu-id="d71f6-105">The type of the list.</span></span> <span data-ttu-id="d71f6-106">Bir madde işaretli liste için "madde işareti", numaralandırılmış liste için "numara" veya iki sütunlu bir tablo için "Tablo" olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d71f6-106">Must be a "bullet" for a bulleted list, "number" for a numbered list, or "table" for a two-column table.</span></span>  
  
 `term`  
 <span data-ttu-id="d71f6-107">Yalnızca "Table" olduğunda kullanılır `type` .</span><span class="sxs-lookup"><span data-stu-id="d71f6-107">Only used when `type` is "table."</span></span> <span data-ttu-id="d71f6-108">Description etiketinde tanımlanan, tanımlanacak bir terim.</span><span class="sxs-lookup"><span data-stu-id="d71f6-108">A term to define, which is defined in the description tag.</span></span>  
  
 `description`  
 <span data-ttu-id="d71f6-109">" `type` İtem" veya "Number" olduğunda, " `description` Tablo", `type` `description` tanımdır `term` .</span><span class="sxs-lookup"><span data-stu-id="d71f6-109">When `type` is "bullet" or "number," `description` is an item in the list When `type` is "table," `description` is the definition of `term`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d71f6-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d71f6-110">Remarks</span></span>  

 <span data-ttu-id="d71f6-111">`<listheader>`Blok, bir tablo ya da tanım listesinin başlığını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d71f6-111">The `<listheader>` block defines the heading of either a table or definition list.</span></span> <span data-ttu-id="d71f6-112">Tablo tanımlarken, yalnızca başlıkta bir giriş sağlamanız gerekir `term` .</span><span class="sxs-lookup"><span data-stu-id="d71f6-112">When defining a table, you only have to supply an entry for `term` in the heading.</span></span>  
  
 <span data-ttu-id="d71f6-113">Listedeki her öğe bir `<item>` blokla belirtilir.</span><span class="sxs-lookup"><span data-stu-id="d71f6-113">Each item in the list is specified with an `<item>` block.</span></span> <span data-ttu-id="d71f6-114">Bir tanım listesi oluştururken, hem hem de belirtmeniz gerekir `term` `description` .</span><span class="sxs-lookup"><span data-stu-id="d71f6-114">When creating a definition list, you must specify both `term` and `description`.</span></span> <span data-ttu-id="d71f6-115">Ancak, bir tablo, madde işaretli liste veya numaralandırılmış liste için yalnızca bir giriş sağlamanız gerekir `description` .</span><span class="sxs-lookup"><span data-stu-id="d71f6-115">However, for a table, bulleted list, or numbered list, you only have to supply an entry for `description`.</span></span>  
  
 <span data-ttu-id="d71f6-116">Bir liste veya tablo gerektiği kadar çok `<item>` blok içerebilir.</span><span class="sxs-lookup"><span data-stu-id="d71f6-116">A list or table can have as many `<item>` blocks as needed.</span></span>  
  
 <span data-ttu-id="d71f6-117">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="d71f6-117">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d71f6-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="d71f6-118">Example</span></span>  

 <span data-ttu-id="d71f6-119">Bu örnek, `<list>` açıklamalar bölümünde madde işaretli bir liste tanımlamak için etiketini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d71f6-119">This example uses the `<list>` tag to define a bulleted list in the remarks section.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="d71f6-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d71f6-120">See also</span></span>

- [<span data-ttu-id="d71f6-121">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="d71f6-121">XML Comment Tags</span></span>](index.md)
