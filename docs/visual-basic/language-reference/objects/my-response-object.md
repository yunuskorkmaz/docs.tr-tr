---
title: My.Response nesnesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Response
- My.Response
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
ms.openlocfilehash: 2f72f493d99c1e0b0469150c041649486e5ed124
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61794998"
---
# <a name="myresponse-object"></a><span data-ttu-id="f7a15-102">My.Response Nesnesi</span><span class="sxs-lookup"><span data-stu-id="f7a15-102">My.Response Object</span></span>
<span data-ttu-id="f7a15-103">Alır <xref:System.Web.HttpResponse> ilişkili nesne <xref:System.Web.UI.Page>.</span><span class="sxs-lookup"><span data-stu-id="f7a15-103">Gets the <xref:System.Web.HttpResponse> object associated with the <xref:System.Web.UI.Page>.</span></span> <span data-ttu-id="f7a15-104">Bu nesne, HTTP yanıt verilerini istemciye göndermenize olanak sağlar ve bu yanıt hakkında bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="f7a15-104">This object allows you to send HTTP response data to a client and contains information about that response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7a15-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f7a15-105">Remarks</span></span>  
 <span data-ttu-id="f7a15-106">`My.Response` Nesnesini içeren geçerli <xref:System.Web.HttpResponse> sayfası ile ilişkili nesne.</span><span class="sxs-lookup"><span data-stu-id="f7a15-106">The `My.Response` object contains the current <xref:System.Web.HttpResponse> object associated with the page.</span></span>  
  
 <span data-ttu-id="f7a15-107">`My.Response` Nesne için kullanılabilir, yalnızca [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="f7a15-107">The `My.Response` object is only available for [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7a15-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="f7a15-108">Example</span></span>  
 <span data-ttu-id="f7a15-109">Aşağıdaki örnek, üst bilgi koleksiyondan alır `My.Request` nesne ve kullandığı `My.Response` ASP.NET sayfasına yazılacak nesne.</span><span class="sxs-lookup"><span data-stu-id="f7a15-109">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f7a15-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7a15-110">See also</span></span>

- <xref:System.Web.HttpResponse>
- [<span data-ttu-id="f7a15-111">My.Request Nesnesi</span><span class="sxs-lookup"><span data-stu-id="f7a15-111">My.Request Object</span></span>](../../../visual-basic/language-reference/objects/my-request-object.md)
