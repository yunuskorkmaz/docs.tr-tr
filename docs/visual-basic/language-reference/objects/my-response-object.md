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
