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
# <a name="myresponse-object"></a>My.Response Nesnesi

<xref:System.Web.HttpResponse>İle ilişkili nesneyi alır <xref:System.Web.UI.Page> . Bu nesne bir istemciye HTTP yanıt verileri göndermenizi ve bu yanıt hakkındaki bilgileri eklemenizi sağlar.  
  
## <a name="remarks"></a>Açıklamalar  

 `My.Response`Nesne, <xref:System.Web.HttpResponse> sayfayla ilişkili geçerli nesneyi içerir.  
  
 `My.Response`Nesne yalnızca ASP.NET uygulamalarında kullanılabilir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, nesnesinden üstbilgi koleksiyonunu alır `My.Request` ve `My.Response` nesneyi ASP.NET sayfasına yazmak için kullanır.  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Web.HttpResponse>
- [My.Request Nesnesi](my-request-object.md)
