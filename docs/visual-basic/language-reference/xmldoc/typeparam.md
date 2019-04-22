---
title: <typeparam> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
ms.openlocfilehash: 014623be84f9d7eb8a25ac4aadcce450f158c154
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58827243"
---
# <a name="typeparam-visual-basic"></a><span data-ttu-id="45ecd-102">\<typeparam > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45ecd-102">\<typeparam> (Visual Basic)</span></span>
<span data-ttu-id="45ecd-103">Bir tür parametresi ad ve açıklama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="45ecd-103">Defines a type parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45ecd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="45ecd-104">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
## <a name="parameters"></a><span data-ttu-id="45ecd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="45ecd-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="45ecd-106">Tür parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="45ecd-106">The name of the type parameter.</span></span> <span data-ttu-id="45ecd-107">Adı çift tırnak içine alın ("").</span><span class="sxs-lookup"><span data-stu-id="45ecd-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="45ecd-108">Tür parametresinin açıklaması.</span><span class="sxs-lookup"><span data-stu-id="45ecd-108">A description of the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45ecd-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="45ecd-109">Remarks</span></span>  
 <span data-ttu-id="45ecd-110">Kullanım `<typeparam>` genel bir türün veya genel üye bildirimi bir tür parametrelerinin açıklamak yorum etiketi.</span><span class="sxs-lookup"><span data-stu-id="45ecd-110">Use the `<typeparam>` tag in the comment for a generic type or generic member declaration to describe one of the type parameters.</span></span>  
  
 <span data-ttu-id="45ecd-111">Derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="45ecd-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45ecd-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="45ecd-112">Example</span></span>  
 <span data-ttu-id="45ecd-113">Bu örnekte `<typeparam>` açıklamak için etiket `id` parametresi.</span><span class="sxs-lookup"><span data-stu-id="45ecd-113">This example uses the `<typeparam>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="45ecd-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="45ecd-114">See also</span></span>

- [<span data-ttu-id="45ecd-115">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="45ecd-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
