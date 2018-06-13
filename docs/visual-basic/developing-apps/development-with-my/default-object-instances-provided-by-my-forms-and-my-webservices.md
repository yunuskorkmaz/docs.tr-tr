---
title: My.Forms ve My.WebServices ile Sağlanan Varsayılan Nesne Örnekleri (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.WebServices object [Visual Basic], developing applications
- My.Forms object [Visual Basic], developing applications
- rapid application development (RAD), My.Forms
- rapid application development (RAD), My.WebServices
ms.assetid: de930027-9108-4f0c-b97c-5e7db4d6ef79
ms.openlocfilehash: 421995684201ec48d5e8aff9b0ed7640efd1e4b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33582668"
---
# <a name="default-object-instances-provided-by-myforms-and-mywebservices-visual-basic"></a>My.Forms ve My.WebServices ile Sağlanan Varsayılan Nesne Örnekleri (Visual Basic)
[My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md) ve [My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md) nesneleri formlar, veri kaynakları ve uygulamanız tarafından kullanılan XML Web Hizmetleri için erişim sağlar. Koleksiyonları sağlayarak bunu *varsayılan örnekleri* , bu nesnelerin her biri.  
  
## <a name="default-instances"></a>Varsayılan örnekleri  
 Varsayılan bir örnek olması gerekmez ve çalışma zamanı tarafından sağlanan sınıfının bir örneği olan bildirilir ve kullanma örneği `Dim` ve `New` deyimleri. Aşağıdaki örnek, nasıl bildirilmiş ve bir örneğini örneği gösterir bir <xref:System.Windows.Forms.Form> adlı bir sınıf `Form1`, ve nasıl şimdi bu varsayılan örneğini almak <xref:System.Windows.Forms.Form> aracılığıyla sınıf `My.Forms`.  
  
 [!code-vb[VbVbcnMy#5](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/default-object-instances-provided-by-my-forms-and-my-webservices_1.vb)]  
  
 [!code-vb[VbVbcnMy#6](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/default-object-instances-provided-by-my-forms-and-my-webservices_2.vb)]  
  
 `My.Forms` Nesne için varsayılan örneklerinin bir koleksiyonunu döndürür her `Form` projenizde var. sınıfı. Benzer şekilde, `My.WebServices` uygulamanızda oluşturulan bir başvuru için her Web hizmeti proxy sınıfı varsayılan örneği sağlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [My.Forms Nesnesi](../../../visual-basic/language-reference/objects/my-forms-object.md)  
 [My.WebServices Nesnesi](../../../visual-basic/language-reference/objects/my-webservices-object.md)  
 [My Özellikleri Proje Türüne Nasıl Bağımlıdır](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
