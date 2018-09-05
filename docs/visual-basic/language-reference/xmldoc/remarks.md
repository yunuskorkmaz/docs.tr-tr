---
title: '&lt;Açıklamalar&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: 97fca8758d9c21ac0b8f15bf9d5831750fbabe77
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43557082"
---
# <a name="ltremarksgt-visual-basic"></a><span data-ttu-id="31311-102">&lt;Açıklamalar&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31311-102">&lt;remarks&gt; (Visual Basic)</span></span>
<span data-ttu-id="31311-103">Üye için Açıklamalar bölümüne belirtir.</span><span class="sxs-lookup"><span data-stu-id="31311-103">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31311-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="31311-104">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="31311-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="31311-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="31311-106">Üye açıklaması.</span><span class="sxs-lookup"><span data-stu-id="31311-106">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31311-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="31311-107">Remarks</span></span>  
 <span data-ttu-id="31311-108">Kullanım `<remarks>` ile belirtilen bilgileri ekleme, bir tür hakkında bilgi eklemek için etiket [ \<Özet >](../../../visual-basic/language-reference/xmldoc/summary.md).</span><span class="sxs-lookup"><span data-stu-id="31311-108">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md).</span></span>  
  
 <span data-ttu-id="31311-109">Bu bilgiler, Nesne Tarayıcısı'nda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="31311-109">This information appears in the Object Browser.</span></span> <span data-ttu-id="31311-110">Nesne tarayıcı hakkında daha fazla bilgi için bkz: [Structure of Code görüntüleme](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="31311-110">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="31311-111">Derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="31311-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="31311-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="31311-112">Example</span></span>  
 <span data-ttu-id="31311-113">Bu örnekte `<remarks>` ne açıklamak için etiket `UpdateRecord` yöntemi yapar.</span><span class="sxs-lookup"><span data-stu-id="31311-113">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/remarks_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="31311-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="31311-114">See Also</span></span>  
 [<span data-ttu-id="31311-115">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="31311-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
