---
title: '&lt;Açıklamalar&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: 6e4e280760b9238fdc403ac5fe586743334e4c69
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33598211"
---
# <a name="ltremarksgt-visual-basic"></a><span data-ttu-id="e3d20-102">&lt;Açıklamalar&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e3d20-102">&lt;remarks&gt; (Visual Basic)</span></span>
<span data-ttu-id="e3d20-103">Açıklamalar bölümüne üye için belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3d20-103">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3d20-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e3d20-104">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e3d20-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e3d20-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="e3d20-106">Üye açıklaması.</span><span class="sxs-lookup"><span data-stu-id="e3d20-106">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3d20-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e3d20-107">Remarks</span></span>  
 <span data-ttu-id="e3d20-108">Kullanım `<remarks>` ile belirtilen bilgileri ekleme bir türü hakkında bilgi eklemek için etiket [ \<Özet >](../../../visual-basic/language-reference/xmldoc/summary.md).</span><span class="sxs-lookup"><span data-stu-id="e3d20-108">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md).</span></span>  
  
 <span data-ttu-id="e3d20-109">Bu bilgiler nesne tarayıcısında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e3d20-109">This information appears in the Object Browser.</span></span> <span data-ttu-id="e3d20-110">Nesne Tarayıcısı hakkında daha fazla bilgi için bkz: [kodunu yapısı görüntüleme](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="e3d20-110">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="e3d20-111">İle derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) bir dosyaya işlem belgesi açıklamaları için.</span><span class="sxs-lookup"><span data-stu-id="e3d20-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3d20-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="e3d20-112">Example</span></span>  
 <span data-ttu-id="e3d20-113">Bu örnekte `<remarks>` ne açıklamak için etiket `UpdateRecord` yöntemi yapar.</span><span class="sxs-lookup"><span data-stu-id="e3d20-113">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/remarks_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e3d20-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e3d20-114">See Also</span></span>  
 [<span data-ttu-id="e3d20-115">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="e3d20-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
