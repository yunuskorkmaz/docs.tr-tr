---
title: '&lt;Liste&gt; (Visual Basic)'
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
ms.openlocfilehash: f03924217393e1e909b086b282f1c62ddb471522
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603619"
---
# <a name="ltlistgt-visual-basic"></a><span data-ttu-id="d1ca6-102">&lt;Liste&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d1ca6-102">&lt;list&gt; (Visual Basic)</span></span>
<span data-ttu-id="d1ca6-103">Bir liste veya tablo tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d1ca6-103">Defines a list or table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1ca6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d1ca6-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="d1ca6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d1ca6-105">Parameters</span></span>  
 `type`  
 <span data-ttu-id="d1ca6-106">Liste türü.</span><span class="sxs-lookup"><span data-stu-id="d1ca6-106">The type of the list.</span></span> <span data-ttu-id="d1ca6-107">"Bullet" listeyi, bir numaralı liste veya iki sütunlu bir tablo için "Tablo" için "number" olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d1ca6-107">Must be a "bullet" for a bulleted list, "number" for a numbered list, or "table" for a two-column table.</span></span>  
  
 `term`  
 <span data-ttu-id="d1ca6-108">Yüklendiğinde yalnızca `type` "Tablo" olan</span><span class="sxs-lookup"><span data-stu-id="d1ca6-108">Only used when `type` is "table."</span></span> <span data-ttu-id="d1ca6-109">Açıklama etiketinde tanımlanan tanımlamak için bir terim.</span><span class="sxs-lookup"><span data-stu-id="d1ca6-109">A term to define, which is defined in the description tag.</span></span>  
  
 `description`  
 <span data-ttu-id="d1ca6-110">Zaman `type` "bullet" veya "number" `description` listedeki bir öğe olduğu zaman `type` "Tablo" olan `description` tanımıdır `term`.</span><span class="sxs-lookup"><span data-stu-id="d1ca6-110">When `type` is "bullet" or "number," `description` is an item in the list When `type` is "table," `description` is the definition of `term`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1ca6-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d1ca6-111">Remarks</span></span>  
 <span data-ttu-id="d1ca6-112">`<listheader>` Bloğu bir tablo veya tanım listesi başlığını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d1ca6-112">The `<listheader>` block defines the heading of either a table or definition list.</span></span> <span data-ttu-id="d1ca6-113">Bir tablo tanımlarken için bir giriş temin etmek yeterlidir `term` başlığı.</span><span class="sxs-lookup"><span data-stu-id="d1ca6-113">When defining a table, you only have to supply an entry for `term` in the heading.</span></span>  
  
 <span data-ttu-id="d1ca6-114">Listedeki her bir öğe ile belirtilen bir `<item>` bloğu.</span><span class="sxs-lookup"><span data-stu-id="d1ca6-114">Each item in the list is specified with an `<item>` block.</span></span> <span data-ttu-id="d1ca6-115">Bir tanım listesi oluştururken, her ikisini de belirtmelisiniz `term` ve `description`.</span><span class="sxs-lookup"><span data-stu-id="d1ca6-115">When creating a definition list, you must specify both `term` and `description`.</span></span> <span data-ttu-id="d1ca6-116">Ancak, bir tablo, madde işaretli liste veya numaralı liste için bir giriş temin etmek yeterlidir `description`.</span><span class="sxs-lookup"><span data-stu-id="d1ca6-116">However, for a table, bulleted list, or numbered list, you only have to supply an entry for `description`.</span></span>  
  
 <span data-ttu-id="d1ca6-117">Bir liste veya tablo kadar olabilir `<item>` gerektiğinde engeller.</span><span class="sxs-lookup"><span data-stu-id="d1ca6-117">A list or table can have as many `<item>` blocks as needed.</span></span>  
  
 <span data-ttu-id="d1ca6-118">İle derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) bir dosyaya işlem belgesi açıklamaları için.</span><span class="sxs-lookup"><span data-stu-id="d1ca6-118">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1ca6-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="d1ca6-119">Example</span></span>  
 <span data-ttu-id="d1ca6-120">Bu örnekte `<list>` açıklamalar bölümünde madde işaretli listesini tanımlamak için etiketi.</span><span class="sxs-lookup"><span data-stu-id="d1ca6-120">This example uses the `<list>` tag to define a bulleted list in the remarks section.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#5](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/list_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d1ca6-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d1ca6-121">See Also</span></span>  
 [<span data-ttu-id="d1ca6-122">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="d1ca6-122">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
