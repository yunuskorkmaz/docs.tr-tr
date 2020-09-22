---
title: My.Response Nesnesi
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: 53e8012e762c46e6efbd8e9d2191aa62d58aa42b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870034"
---
# <a name="myresponse-object"></a><span data-ttu-id="e1932-102">My.Response Nesnesi</span><span class="sxs-lookup"><span data-stu-id="e1932-102">My.Response Object</span></span>

<span data-ttu-id="e1932-103"><xref:System.Web.HttpResponse>İle ilişkili nesneyi alır <xref:System.Web.UI.Page> .</span><span class="sxs-lookup"><span data-stu-id="e1932-103">Gets the <xref:System.Web.HttpResponse> object associated with the <xref:System.Web.UI.Page>.</span></span> <span data-ttu-id="e1932-104">Bu nesne bir istemciye HTTP yanıt verileri göndermenizi ve bu yanıt hakkındaki bilgileri eklemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e1932-104">This object allows you to send HTTP response data to a client and contains information about that response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1932-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e1932-105">Remarks</span></span>  

 <span data-ttu-id="e1932-106">`My.Response`Nesne, <xref:System.Web.HttpResponse> sayfayla ilişkili geçerli nesneyi içerir.</span><span class="sxs-lookup"><span data-stu-id="e1932-106">The `My.Response` object contains the current <xref:System.Web.HttpResponse> object associated with the page.</span></span>  
  
 <span data-ttu-id="e1932-107">`My.Response`Nesne yalnızca ASP.NET uygulamalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e1932-107">The `My.Response` object is only available for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1932-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="e1932-108">Example</span></span>  

 <span data-ttu-id="e1932-109">Aşağıdaki örnek, nesnesinden üstbilgi koleksiyonunu alır `My.Request` ve `My.Response` nesneyi ASP.NET sayfasına yazmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="e1932-109">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e1932-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1932-110">See also</span></span>

- <xref:System.Web.HttpResponse>
- [<span data-ttu-id="e1932-111">My.Request Nesnesi</span><span class="sxs-lookup"><span data-stu-id="e1932-111">My.Request Object</span></span>](my-request-object.md)
