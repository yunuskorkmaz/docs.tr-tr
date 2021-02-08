---
description: 'Hakkında daha fazla bilgi edinin: My. Forms ve My. WebServices tarafından sunulan varsayılan nesne örnekleri (Visual Basic)'
title: My.Forms ve My.WebServices ile Sağlanan Varsayılan Nesne Örnekleri
ms.date: 07/20/2015
helpviewer_keywords:
- My.WebServices object [Visual Basic], developing applications
- My.Forms object [Visual Basic], developing applications
- rapid application development (RAD), My.Forms
- rapid application development (RAD), My.WebServices
ms.assetid: de930027-9108-4f0c-b97c-5e7db4d6ef79
ms.openlocfilehash: 34363a56577ca0fafb839e782a8066bd8a8c5a14
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775363"
---
# <a name="default-object-instances-provided-by-myforms-and-mywebservices-visual-basic"></a>My.Forms ve My.WebServices ile Sağlanan Varsayılan Nesne Örnekleri (Visual Basic)

[My. Forms](../../language-reference/objects/my-forms-object.md) ve [My. WebServices](../../language-reference/objects/my-webservices-object.md) nesneleri, uygulamanız tarafından kullanılan formlara, veri kaynaklarına ve XML Web hizmetlerine erişim sağlar. Bunlar, bu nesnelerin her birinin *varsayılan örneklerinin* koleksiyonları aracılığıyla erişim sağlar.  
  
## <a name="default-instances"></a>Varsayılan örnekler  

 Varsayılan örnek, çalışma zamanı tarafından sağlanmış bir sınıfının örneğidir ve ve deyimleri kullanılarak bildirilmesine ve örneklendirilmemelidir `Dim` `New` . Aşağıdaki örnek, adlı bir sınıfın örneğini nasıl bildirdiğini ve örnekleyeceğinizi <xref:System.Windows.Forms.Form> `Form1` ve bundan böyle bu sınıfın varsayılan bir örneğini nasıl sağlayabileceğinizi gösterir <xref:System.Windows.Forms.Form> `My.Forms` .  
  
 [!code-vb[VbVbcnMy#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#5)]  
  
 [!code-vb[VbVbcnMy#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#6)]  
  
 `My.Forms`Nesnesi, projenizde bulunan her sınıf için bir varsayılan örnekler koleksiyonu döndürür `Form` . Benzer şekilde, `My.WebServices` uygulamanızda bir başvuru oluşturduğunuz her Web hizmeti için proxy sınıfının varsayılan bir örneğini sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [My.Forms Nesnesi](../../language-reference/objects/my-forms-object.md)
- [My.WebServices Nesnesi](../../language-reference/objects/my-webservices-object.md)
- [My Özellikleri Proje Türüne Nasıl Bağımlıdır](how-my-depends-on-project-type.md)
