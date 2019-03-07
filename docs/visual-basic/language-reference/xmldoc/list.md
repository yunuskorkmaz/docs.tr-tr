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
ms.openlocfilehash: 61b0b018b3d06a2307aa280a748b7d07c5fa7915
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496072"
---
# <a name="list-visual-basic"></a><span data-ttu-id="1bcf3-102">\<Liste > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1bcf3-102">\<list> (Visual Basic)</span></span>
<span data-ttu-id="1bcf3-103">Bir listeyi veya tabloyu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1bcf3-103">Defines a list or table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bcf3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1bcf3-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="1bcf3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1bcf3-105">Parameters</span></span>  
 `type`  
 <span data-ttu-id="1bcf3-106">Liste türü.</span><span class="sxs-lookup"><span data-stu-id="1bcf3-106">The type of the list.</span></span> <span data-ttu-id="1bcf3-107">"Bullet" bir madde işaretli liste, numaralandırılmış liste veya iki sütunlu bir tablo için "Tablo" için "number" olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1bcf3-107">Must be a "bullet" for a bulleted list, "number" for a numbered list, or "table" for a two-column table.</span></span>  
  
 `term`  
 <span data-ttu-id="1bcf3-108">Yalnızca ne zaman kullanılır `type` "Tablo" olan</span><span class="sxs-lookup"><span data-stu-id="1bcf3-108">Only used when `type` is "table."</span></span> <span data-ttu-id="1bcf3-109">Açıklama etiketi tanımlanan tanımlamak için bir terim.</span><span class="sxs-lookup"><span data-stu-id="1bcf3-109">A term to define, which is defined in the description tag.</span></span>  
  
 `description`  
 <span data-ttu-id="1bcf3-110">Zaman `type` "bullet" veya "number" `description` listesinde bir öğe olduğunda `type` "Tablo" olan `description` tanımı `term`.</span><span class="sxs-lookup"><span data-stu-id="1bcf3-110">When `type` is "bullet" or "number," `description` is an item in the list When `type` is "table," `description` is the definition of `term`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1bcf3-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1bcf3-111">Remarks</span></span>  
 <span data-ttu-id="1bcf3-112">`<listheader>` Blok başlığı bir tablo veya tanım listesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1bcf3-112">The `<listheader>` block defines the heading of either a table or definition list.</span></span> <span data-ttu-id="1bcf3-113">Bir tablo tanımlarken, yalnızca bir giriş sağlamanız gerekir `term` başlığı.</span><span class="sxs-lookup"><span data-stu-id="1bcf3-113">When defining a table, you only have to supply an entry for `term` in the heading.</span></span>  
  
 <span data-ttu-id="1bcf3-114">Listedeki her bir öğe ile belirtilen bir `<item>` blok.</span><span class="sxs-lookup"><span data-stu-id="1bcf3-114">Each item in the list is specified with an `<item>` block.</span></span> <span data-ttu-id="1bcf3-115">Tanım listesi oluştururken, her ikisini de belirtmelisiniz `term` ve `description`.</span><span class="sxs-lookup"><span data-stu-id="1bcf3-115">When creating a definition list, you must specify both `term` and `description`.</span></span> <span data-ttu-id="1bcf3-116">Ancak, bir tablo, madde işaretli liste veya numaralı liste için yalnızca bir giriş sağlamanız gerekir `description`.</span><span class="sxs-lookup"><span data-stu-id="1bcf3-116">However, for a table, bulleted list, or numbered list, you only have to supply an entry for `description`.</span></span>  
  
 <span data-ttu-id="1bcf3-117">Bir listeyi veya tabloyu kadar olabilir `<item>` gerektiğinde engeller.</span><span class="sxs-lookup"><span data-stu-id="1bcf3-117">A list or table can have as many `<item>` blocks as needed.</span></span>  
  
 <span data-ttu-id="1bcf3-118">Derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="1bcf3-118">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bcf3-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="1bcf3-119">Example</span></span>  
 <span data-ttu-id="1bcf3-120">Bu örnekte `<list>` etiket açıklamalar bölümünde bir madde işaretli liste tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="1bcf3-120">This example uses the `<list>` tag to define a bulleted list in the remarks section.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="1bcf3-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1bcf3-121">See also</span></span>
- [<span data-ttu-id="1bcf3-122">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="1bcf3-122">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
