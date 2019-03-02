---
title: My.Request nesnesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Request
- My.Request
helpviewer_keywords:
- My.Request object
ms.assetid: 93d5f0e2-6b60-4a2c-8652-d90216f6ad10
ms.openlocfilehash: 7a4e292968cf1d30977b8cacdc8f77152e5cc770
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57200968"
---
# <a name="myrequest-object"></a><span data-ttu-id="38754-102">My.Request Nesnesi</span><span class="sxs-lookup"><span data-stu-id="38754-102">My.Request Object</span></span>
<span data-ttu-id="38754-103">Alır <xref:System.Web.HttpRequest> istenen sayfa nesnesi.</span><span class="sxs-lookup"><span data-stu-id="38754-103">Gets the <xref:System.Web.HttpRequest> object for the requested page.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38754-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="38754-104">Remarks</span></span>  
 <span data-ttu-id="38754-105">`My.Request` Nesnesi geçerli HTTP isteğiyle ilgili bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="38754-105">The `My.Request` object contains information about the current HTTP request.</span></span>  
  
 <span data-ttu-id="38754-106">`My.Request` Nesne yalnızca ASP.NET uygulamaları için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="38754-106">The `My.Request` object is available only for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="38754-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="38754-107">Example</span></span>  
 <span data-ttu-id="38754-108">Aşağıdaki örnek, üst bilgi koleksiyondan alır `My.Request` nesne ve kullandığı `My.Response` ASP.NET sayfasına yazılacak nesne.</span><span class="sxs-lookup"><span data-stu-id="38754-108">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a><span data-ttu-id="38754-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38754-109">See also</span></span>
- <xref:System.Web.HttpRequest>
- [<span data-ttu-id="38754-110">My.Response Nesnesi</span><span class="sxs-lookup"><span data-stu-id="38754-110">My.Response Object</span></span>](../../../visual-basic/language-reference/objects/my-response-object.md)
