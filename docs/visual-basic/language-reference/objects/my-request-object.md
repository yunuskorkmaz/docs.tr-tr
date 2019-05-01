---
title: My.Request nesnesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Request
- My.Request
helpviewer_keywords:
- My.Request object
ms.assetid: 93d5f0e2-6b60-4a2c-8652-d90216f6ad10
ms.openlocfilehash: 08212dc5fe563ce84be02ab706b56195a0636894
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788641"
---
# <a name="myrequest-object"></a><span data-ttu-id="19681-102">My.Request Nesnesi</span><span class="sxs-lookup"><span data-stu-id="19681-102">My.Request Object</span></span>
<span data-ttu-id="19681-103">Alır <xref:System.Web.HttpRequest> istenen sayfa nesnesi.</span><span class="sxs-lookup"><span data-stu-id="19681-103">Gets the <xref:System.Web.HttpRequest> object for the requested page.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="19681-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="19681-104">Remarks</span></span>  
 <span data-ttu-id="19681-105">`My.Request` Nesnesi geçerli HTTP isteğiyle ilgili bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="19681-105">The `My.Request` object contains information about the current HTTP request.</span></span>  
  
 <span data-ttu-id="19681-106">`My.Request` Nesne yalnızca ASP.NET uygulamaları için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="19681-106">The `My.Request` object is available only for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19681-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="19681-107">Example</span></span>  
 <span data-ttu-id="19681-108">Aşağıdaki örnek, üst bilgi koleksiyondan alır `My.Request` nesne ve kullandığı `My.Response` ASP.NET sayfasına yazılacak nesne.</span><span class="sxs-lookup"><span data-stu-id="19681-108">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a><span data-ttu-id="19681-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19681-109">See also</span></span>

- <xref:System.Web.HttpRequest>
- [<span data-ttu-id="19681-110">My.Response Nesnesi</span><span class="sxs-lookup"><span data-stu-id="19681-110">My.Response Object</span></span>](../../../visual-basic/language-reference/objects/my-response-object.md)
