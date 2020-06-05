---
title: My.Response Nesnesi
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: 962108264563c5e0b2894c5c856a5f23a3c1a8b4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372472"
---
# <a name="myresponse-object"></a><span data-ttu-id="7ad39-102">My.Response Nesnesi</span><span class="sxs-lookup"><span data-stu-id="7ad39-102">My.Response Object</span></span>
<span data-ttu-id="7ad39-103"><xref:System.Web.HttpResponse>İle ilişkili nesneyi alır <xref:System.Web.UI.Page> .</span><span class="sxs-lookup"><span data-stu-id="7ad39-103">Gets the <xref:System.Web.HttpResponse> object associated with the <xref:System.Web.UI.Page>.</span></span> <span data-ttu-id="7ad39-104">Bu nesne bir istemciye HTTP yanıt verileri göndermenizi ve bu yanıt hakkındaki bilgileri eklemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="7ad39-104">This object allows you to send HTTP response data to a client and contains information about that response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ad39-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7ad39-105">Remarks</span></span>  
 <span data-ttu-id="7ad39-106">`My.Response`Nesne, <xref:System.Web.HttpResponse> sayfayla ilişkili geçerli nesneyi içerir.</span><span class="sxs-lookup"><span data-stu-id="7ad39-106">The `My.Response` object contains the current <xref:System.Web.HttpResponse> object associated with the page.</span></span>  
  
 <span data-ttu-id="7ad39-107">`My.Response`Nesne yalnızca ASP.NET uygulamalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7ad39-107">The `My.Response` object is only available for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ad39-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="7ad39-108">Example</span></span>  
 <span data-ttu-id="7ad39-109">Aşağıdaki örnek, nesnesinden üstbilgi koleksiyonunu alır `My.Request` ve `My.Response` nesneyi ASP.NET sayfasına yazmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="7ad39-109">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a><span data-ttu-id="7ad39-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ad39-110">See also</span></span>

- <xref:System.Web.HttpResponse>
- [<span data-ttu-id="7ad39-111">My.Request Nesnesi</span><span class="sxs-lookup"><span data-stu-id="7ad39-111">My.Request Object</span></span>](my-request-object.md)
