---
title: '&lt;typeparam&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
ms.openlocfilehash: 73ffb1319e6724a13a80b3cd1ca6985e4cbac05c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54567067"
---
# <a name="lttypeparamgt-visual-basic"></a><span data-ttu-id="eede1-102">&lt;typeparam&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eede1-102">&lt;typeparam&gt; (Visual Basic)</span></span>
<span data-ttu-id="eede1-103">Bir tür parametresi ad ve açıklama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="eede1-103">Defines a type parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eede1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eede1-104">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eede1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="eede1-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="eede1-106">Tür parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="eede1-106">The name of the type parameter.</span></span> <span data-ttu-id="eede1-107">Adı çift tırnak içine alın ("").</span><span class="sxs-lookup"><span data-stu-id="eede1-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="eede1-108">Tür parametresinin açıklaması.</span><span class="sxs-lookup"><span data-stu-id="eede1-108">A description of the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eede1-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eede1-109">Remarks</span></span>  
 <span data-ttu-id="eede1-110">Kullanım `<typeparam>` genel bir türün veya genel üye bildirimi bir tür parametrelerinin açıklamak yorum etiketi.</span><span class="sxs-lookup"><span data-stu-id="eede1-110">Use the `<typeparam>` tag in the comment for a generic type or generic member declaration to describe one of the type parameters.</span></span>  
  
 <span data-ttu-id="eede1-111">Derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="eede1-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eede1-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="eede1-112">Example</span></span>  
 <span data-ttu-id="eede1-113">Bu örnekte `<typeparam>` açıklamak için etiket `id` parametresi.</span><span class="sxs-lookup"><span data-stu-id="eede1-113">This example uses the `<typeparam>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#8](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/typeparam_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="eede1-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eede1-114">See also</span></span>
- [<span data-ttu-id="eede1-115">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="eede1-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
