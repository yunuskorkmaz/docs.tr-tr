---
title: My.Response Nesnesi
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: 522814ad48fb7548032b8a37779bb3ff6ca62413
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350651"
---
# <a name="myresponse-object"></a><span data-ttu-id="20843-102">My.Response Nesnesi</span><span class="sxs-lookup"><span data-stu-id="20843-102">My.Response Object</span></span>
<span data-ttu-id="20843-103"><xref:System.Web.UI.Page>ilişkili <xref:System.Web.HttpResponse> nesnesini alır.</span><span class="sxs-lookup"><span data-stu-id="20843-103">Gets the <xref:System.Web.HttpResponse> object associated with the <xref:System.Web.UI.Page>.</span></span> <span data-ttu-id="20843-104">Bu nesne bir istemciye HTTP yanıt verileri göndermenizi ve bu yanıt hakkındaki bilgileri eklemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="20843-104">This object allows you to send HTTP response data to a client and contains information about that response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20843-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="20843-105">Remarks</span></span>  
 <span data-ttu-id="20843-106">`My.Response` nesnesi sayfayla ilişkili geçerli <xref:System.Web.HttpResponse> nesnesini içerir.</span><span class="sxs-lookup"><span data-stu-id="20843-106">The `My.Response` object contains the current <xref:System.Web.HttpResponse> object associated with the page.</span></span>  
  
 <span data-ttu-id="20843-107">`My.Response` nesnesi yalnızca ASP.NET uygulamalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="20843-107">The `My.Response` object is only available for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="20843-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="20843-108">Example</span></span>  
 <span data-ttu-id="20843-109">Aşağıdaki örnek, `My.Request` nesnesinden üst bilgi koleksiyonunu alır ve ASP.NET sayfasına yazmak için `My.Response` nesnesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="20843-109">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a><span data-ttu-id="20843-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="20843-110">See also</span></span>

- <xref:System.Web.HttpResponse>
- [<span data-ttu-id="20843-111">My.Request Nesnesi</span><span class="sxs-lookup"><span data-stu-id="20843-111">My.Request Object</span></span>](../../../visual-basic/language-reference/objects/my-request-object.md)
