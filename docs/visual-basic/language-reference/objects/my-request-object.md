---
title: My.Request Nesnesi
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Request
- My.Request
helpviewer_keywords:
- My.Request object
ms.assetid: 93d5f0e2-6b60-4a2c-8652-d90216f6ad10
ms.openlocfilehash: 22329bc501c9bb75b1336dd5384ab5b23a98ac21
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350686"
---
# <a name="myrequest-object"></a><span data-ttu-id="0ef3b-102">My.Request Nesnesi</span><span class="sxs-lookup"><span data-stu-id="0ef3b-102">My.Request Object</span></span>
<span data-ttu-id="0ef3b-103">İstenen sayfa için <xref:System.Web.HttpRequest> nesnesini alır.</span><span class="sxs-lookup"><span data-stu-id="0ef3b-103">Gets the <xref:System.Web.HttpRequest> object for the requested page.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ef3b-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0ef3b-104">Remarks</span></span>  
 <span data-ttu-id="0ef3b-105">`My.Request` nesnesi geçerli HTTP isteğiyle ilgili bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="0ef3b-105">The `My.Request` object contains information about the current HTTP request.</span></span>  
  
 <span data-ttu-id="0ef3b-106">`My.Request` nesnesi yalnızca ASP.NET uygulamaları için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0ef3b-106">The `My.Request` object is available only for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ef3b-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="0ef3b-107">Example</span></span>  
 <span data-ttu-id="0ef3b-108">Aşağıdaki örnek, `My.Request` nesnesinden üst bilgi koleksiyonunu alır ve ASP.NET sayfasına yazmak için `My.Response` nesnesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="0ef3b-108">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a><span data-ttu-id="0ef3b-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ef3b-109">See also</span></span>

- <xref:System.Web.HttpRequest>
- [<span data-ttu-id="0ef3b-110">My.Response Nesnesi</span><span class="sxs-lookup"><span data-stu-id="0ef3b-110">My.Response Object</span></span>](../../../visual-basic/language-reference/objects/my-response-object.md)
