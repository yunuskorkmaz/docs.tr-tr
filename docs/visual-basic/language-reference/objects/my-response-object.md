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
# <a name="myresponse-object"></a>My.Response Nesnesi
<xref:System.Web.UI.Page>ilişkili <xref:System.Web.HttpResponse> nesnesini alır. Bu nesne bir istemciye HTTP yanıt verileri göndermenizi ve bu yanıt hakkındaki bilgileri eklemenizi sağlar.  
  
## <a name="remarks"></a>Açıklamalar  
 `My.Response` nesnesi sayfayla ilişkili geçerli <xref:System.Web.HttpResponse> nesnesini içerir.  
  
 `My.Response` nesnesi yalnızca ASP.NET uygulamalarında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `My.Request` nesnesinden üst bilgi koleksiyonunu alır ve ASP.NET sayfasına yazmak için `My.Response` nesnesini kullanır.  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Web.HttpResponse>
- [My.Request Nesnesi](../../../visual-basic/language-reference/objects/my-request-object.md)
