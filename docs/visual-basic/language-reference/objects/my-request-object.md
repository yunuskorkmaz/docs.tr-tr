---
title: My.Request Nesnesi
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Request
- My.Request
helpviewer_keywords:
- My.Request object
ms.assetid: 93d5f0e2-6b60-4a2c-8652-d90216f6ad10
ms.openlocfilehash: d0459506994fb69ebfaa4186ba137044b6fe9464
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870073"
---
# <a name="myrequest-object"></a><span data-ttu-id="26434-102">My.Request Nesnesi</span><span class="sxs-lookup"><span data-stu-id="26434-102">My.Request Object</span></span>

<span data-ttu-id="26434-103"><xref:System.Web.HttpRequest>İstenen sayfa için nesneyi alır.</span><span class="sxs-lookup"><span data-stu-id="26434-103">Gets the <xref:System.Web.HttpRequest> object for the requested page.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26434-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="26434-104">Remarks</span></span>  

 <span data-ttu-id="26434-105">`My.Request`Nesne, GEÇERLI HTTP isteğiyle ilgili bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="26434-105">The `My.Request` object contains information about the current HTTP request.</span></span>  
  
 <span data-ttu-id="26434-106">`My.Request`Nesne yalnızca ASP.NET uygulamaları için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="26434-106">The `My.Request` object is available only for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26434-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="26434-107">Example</span></span>  

 <span data-ttu-id="26434-108">Aşağıdaki örnek, nesnesinden üstbilgi koleksiyonunu alır `My.Request` ve `My.Response` nesneyi ASP.NET sayfasına yazmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="26434-108">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a><span data-ttu-id="26434-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26434-109">See also</span></span>

- <xref:System.Web.HttpRequest>
- [<span data-ttu-id="26434-110">My.Response Nesnesi</span><span class="sxs-lookup"><span data-stu-id="26434-110">My.Response Object</span></span>](my-response-object.md)
