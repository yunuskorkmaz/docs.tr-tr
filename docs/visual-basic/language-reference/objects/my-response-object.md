---
title: My. Response nesnesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: a50701998011c25c600c2a3763459c1aba3cc59a
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567459"
---
# <a name="myresponse-object"></a><span data-ttu-id="d412f-102">My.Response Nesnesi</span><span class="sxs-lookup"><span data-stu-id="d412f-102">My.Response Object</span></span>
<span data-ttu-id="d412f-103">İle ilişkili <xref:System.Web.HttpResponse> nesneyi alır <xref:System.Web.UI.Page>.</span><span class="sxs-lookup"><span data-stu-id="d412f-103">Gets the <xref:System.Web.HttpResponse> object associated with the <xref:System.Web.UI.Page>.</span></span> <span data-ttu-id="d412f-104">Bu nesne bir istemciye HTTP yanıt verileri göndermenizi ve bu yanıt hakkındaki bilgileri eklemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d412f-104">This object allows you to send HTTP response data to a client and contains information about that response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d412f-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d412f-105">Remarks</span></span>  
 <span data-ttu-id="d412f-106">Nesne, sayfayla ilişkili geçerli <xref:System.Web.HttpResponse> nesneyi içerir. `My.Response`</span><span class="sxs-lookup"><span data-stu-id="d412f-106">The `My.Response` object contains the current <xref:System.Web.HttpResponse> object associated with the page.</span></span>  
  
 <span data-ttu-id="d412f-107">`My.Response` Nesne yalnızca ASP.NET uygulamalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d412f-107">The `My.Response` object is only available for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d412f-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="d412f-108">Example</span></span>  
 <span data-ttu-id="d412f-109">Aşağıdaki örnek, `My.Request` nesnesinden üstbilgi koleksiyonunu alır ve `My.Response` nesneyi ASP.NET sayfasına yazmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="d412f-109">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d412f-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d412f-110">See also</span></span>

- <xref:System.Web.HttpResponse>
- [<span data-ttu-id="d412f-111">My.Request Nesnesi</span><span class="sxs-lookup"><span data-stu-id="d412f-111">My.Request Object</span></span>](../../../visual-basic/language-reference/objects/my-request-object.md)
