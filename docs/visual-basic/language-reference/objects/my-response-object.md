---
description: ': My. Response nesnem hakkında daha fazla bilgi edinin'
title: My.Response Nesnesi
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: 551528356040539994251cb66a905d0249f482da
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640621"
---
# <a name="myresponse-object"></a><span data-ttu-id="0b8d7-103">My.Response Nesnesi</span><span class="sxs-lookup"><span data-stu-id="0b8d7-103">My.Response Object</span></span>

<span data-ttu-id="0b8d7-104"><xref:System.Web.HttpResponse>İle ilişkili nesneyi alır <xref:System.Web.UI.Page> .</span><span class="sxs-lookup"><span data-stu-id="0b8d7-104">Gets the <xref:System.Web.HttpResponse> object associated with the <xref:System.Web.UI.Page>.</span></span> <span data-ttu-id="0b8d7-105">Bu nesne bir istemciye HTTP yanıt verileri göndermenizi ve bu yanıt hakkındaki bilgileri eklemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="0b8d7-105">This object allows you to send HTTP response data to a client and contains information about that response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b8d7-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0b8d7-106">Remarks</span></span>  

 <span data-ttu-id="0b8d7-107">`My.Response`Nesne, <xref:System.Web.HttpResponse> sayfayla ilişkili geçerli nesneyi içerir.</span><span class="sxs-lookup"><span data-stu-id="0b8d7-107">The `My.Response` object contains the current <xref:System.Web.HttpResponse> object associated with the page.</span></span>  
  
 <span data-ttu-id="0b8d7-108">`My.Response`Nesne yalnızca ASP.NET uygulamalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0b8d7-108">The `My.Response` object is only available for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b8d7-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="0b8d7-109">Example</span></span>  

 <span data-ttu-id="0b8d7-110">Aşağıdaki örnek, nesnesinden üstbilgi koleksiyonunu alır `My.Request` ve `My.Response` nesneyi ASP.NET sayfasına yazmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="0b8d7-110">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a><span data-ttu-id="0b8d7-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b8d7-111">See also</span></span>

- <xref:System.Web.HttpResponse>
- [<span data-ttu-id="0b8d7-112">My.Request Nesnesi</span><span class="sxs-lookup"><span data-stu-id="0b8d7-112">My.Request Object</span></span>](my-request-object.md)
