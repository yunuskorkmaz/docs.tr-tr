---
title: <remarks> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: 90f358aad8e3219b2e3cb3e9b996a24b3138828b
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970837"
---
# <a name="remarks-visual-basic"></a><span data-ttu-id="27cdf-102">\<REMARKS > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="27cdf-102">\<remarks> (Visual Basic)</span></span>
<span data-ttu-id="27cdf-103">Üye için Açıklamalar bölümüne belirtir.</span><span class="sxs-lookup"><span data-stu-id="27cdf-103">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27cdf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="27cdf-104">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="27cdf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="27cdf-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="27cdf-106">Üye açıklaması.</span><span class="sxs-lookup"><span data-stu-id="27cdf-106">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27cdf-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="27cdf-107">Remarks</span></span>  
 <span data-ttu-id="27cdf-108">Kullanım `<remarks>` ile belirtilen bilgileri ekleme, bir tür hakkında bilgi eklemek için etiket [ \<Özet >](../../../visual-basic/language-reference/xmldoc/summary.md).</span><span class="sxs-lookup"><span data-stu-id="27cdf-108">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md).</span></span>  
  
 <span data-ttu-id="27cdf-109">Bu bilgiler, Nesne Tarayıcısı'nda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="27cdf-109">This information appears in the Object Browser.</span></span> <span data-ttu-id="27cdf-110">Nesne tarayıcı hakkında daha fazla bilgi için bkz: [Structure of Code görüntüleme](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="27cdf-110">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="27cdf-111">Derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="27cdf-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27cdf-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="27cdf-112">Example</span></span>  
 <span data-ttu-id="27cdf-113">Bu örnekte `<remarks>` ne açıklamak için etiket `UpdateRecord` yöntemi yapar.</span><span class="sxs-lookup"><span data-stu-id="27cdf-113">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="27cdf-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27cdf-114">See also</span></span>
- [<span data-ttu-id="27cdf-115">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="27cdf-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
