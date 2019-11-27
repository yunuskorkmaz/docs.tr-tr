---
title: My.Forms ve My.WebServices ile Sağlanan Varsayılan Nesne Örnekleri
ms.date: 07/20/2015
helpviewer_keywords:
- My.WebServices object [Visual Basic], developing applications
- My.Forms object [Visual Basic], developing applications
- rapid application development (RAD), My.Forms
- rapid application development (RAD), My.WebServices
ms.assetid: de930027-9108-4f0c-b97c-5e7db4d6ef79
ms.openlocfilehash: d06df4bd023892429b2aaefdd624398a6546d06d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330212"
---
# <a name="default-object-instances-provided-by-myforms-and-mywebservices-visual-basic"></a>My.Forms ve My.WebServices ile Sağlanan Varsayılan Nesne Örnekleri (Visual Basic)

[My. Forms](../../../visual-basic/language-reference/objects/my-forms-object.md) ve [My. WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md) nesneleri, uygulamanız tarafından kullanılan formlara, veri kaynaklarına ve XML Web hizmetlerine erişim sağlar. Bu nesneleri, bu nesnelerin her birinin *varsayılan örnek* koleksiyonlarını sunarak yapabilirler.  
  
## <a name="default-instances"></a>Varsayılan örnekler  

 Varsayılan örnek, çalışma zamanı tarafından sağlanmış bir sınıfının örneğidir ve `Dim` ve `New` deyimleri kullanılarak bildirilmesine ve örneklendirilmemelidir. Aşağıdaki örnek, `Form1`adlı bir <xref:System.Windows.Forms.Form> sınıfın örneğini nasıl bildirdiğini ve örnekleyeceğinizi ve `My.Forms`aracılığıyla bu <xref:System.Windows.Forms.Form> sınıfının varsayılan bir örneğini nasıl sağlayabileceğinizi gösterir.  
  
 [!code-vb[VbVbcnMy#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#5)]  
  
 [!code-vb[VbVbcnMy#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#6)]  
  
 `My.Forms` nesnesi, projenizde bulunan her `Form` sınıfının varsayılan örneklerinin bir koleksiyonunu döndürür. Benzer şekilde, `My.WebServices` uygulamanızda bir başvuru oluşturduğunuz her Web hizmeti için proxy sınıfının varsayılan bir örneğini sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [My.Forms Nesnesi](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [My.WebServices Nesnesi](../../../visual-basic/language-reference/objects/my-webservices-object.md)
- [My Özellikleri Proje Türüne Nasıl Bağımlıdır](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
