---
title: '&lt;typeparam&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
ms.openlocfilehash: d362f181921a39d274eaee78e85976522ce4fc15
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863195"
---
# <a name="lttypeparamgt-visual-basic"></a><span data-ttu-id="9cc56-102">&lt;typeparam&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9cc56-102">&lt;typeparam&gt; (Visual Basic)</span></span>
<span data-ttu-id="9cc56-103">Bir tür parametresi ad ve açıklama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9cc56-103">Defines a type parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cc56-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9cc56-104">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9cc56-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9cc56-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="9cc56-106">Tür parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="9cc56-106">The name of the type parameter.</span></span> <span data-ttu-id="9cc56-107">Adı çift tırnak içine alın ("").</span><span class="sxs-lookup"><span data-stu-id="9cc56-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="9cc56-108">Tür parametresinin açıklaması.</span><span class="sxs-lookup"><span data-stu-id="9cc56-108">A description of the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9cc56-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9cc56-109">Remarks</span></span>  
 <span data-ttu-id="9cc56-110">Kullanım `<typeparam>` genel bir türün veya genel üye bildirimi bir tür parametrelerinin açıklamak yorum etiketi.</span><span class="sxs-lookup"><span data-stu-id="9cc56-110">Use the `<typeparam>` tag in the comment for a generic type or generic member declaration to describe one of the type parameters.</span></span>  
  
 <span data-ttu-id="9cc56-111">Derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="9cc56-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9cc56-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="9cc56-112">Example</span></span>  
 <span data-ttu-id="9cc56-113">Bu örnekte `<typeparam>` açıklamak için etiket `id` parametresi.</span><span class="sxs-lookup"><span data-stu-id="9cc56-113">This example uses the `<typeparam>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#8](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/typeparam_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9cc56-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9cc56-114">See Also</span></span>  
 [<span data-ttu-id="9cc56-115">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="9cc56-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
