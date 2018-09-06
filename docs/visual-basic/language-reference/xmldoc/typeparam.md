---
title: '&lt;typeparam&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
ms.openlocfilehash: d362f181921a39d274eaee78e85976522ce4fc15
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43736198"
---
# <a name="lttypeparamgt-visual-basic"></a><span data-ttu-id="8dd77-102">&lt;typeparam&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8dd77-102">&lt;typeparam&gt; (Visual Basic)</span></span>
<span data-ttu-id="8dd77-103">Bir tür parametresi ad ve açıklama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8dd77-103">Defines a type parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8dd77-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8dd77-104">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8dd77-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8dd77-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="8dd77-106">Tür parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="8dd77-106">The name of the type parameter.</span></span> <span data-ttu-id="8dd77-107">Adı çift tırnak içine alın ("").</span><span class="sxs-lookup"><span data-stu-id="8dd77-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="8dd77-108">Tür parametresinin açıklaması.</span><span class="sxs-lookup"><span data-stu-id="8dd77-108">A description of the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8dd77-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8dd77-109">Remarks</span></span>  
 <span data-ttu-id="8dd77-110">Kullanım `<typeparam>` genel bir türün veya genel üye bildirimi bir tür parametrelerinin açıklamak yorum etiketi.</span><span class="sxs-lookup"><span data-stu-id="8dd77-110">Use the `<typeparam>` tag in the comment for a generic type or generic member declaration to describe one of the type parameters.</span></span>  
  
 <span data-ttu-id="8dd77-111">Derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="8dd77-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8dd77-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="8dd77-112">Example</span></span>  
 <span data-ttu-id="8dd77-113">Bu örnekte `<typeparam>` açıklamak için etiket `id` parametresi.</span><span class="sxs-lookup"><span data-stu-id="8dd77-113">This example uses the `<typeparam>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#8](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/typeparam_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="8dd77-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8dd77-114">See Also</span></span>  
 [<span data-ttu-id="8dd77-115">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="8dd77-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
