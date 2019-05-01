---
title: My.Forms ve My.WebServices ile Sağlanan Varsayılan Nesne Örnekleri (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.WebServices object [Visual Basic], developing applications
- My.Forms object [Visual Basic], developing applications
- rapid application development (RAD), My.Forms
- rapid application development (RAD), My.WebServices
ms.assetid: de930027-9108-4f0c-b97c-5e7db4d6ef79
ms.openlocfilehash: ca31e1c40c77bf7f42d246019d81f4ffaed646e8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62014459"
---
# <a name="default-object-instances-provided-by-myforms-and-mywebservices-visual-basic"></a>My.Forms ve My.WebServices ile Sağlanan Varsayılan Nesne Örnekleri (Visual Basic)
[My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md) ve [My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md) nesneleri, forms, veri kaynakları ve uygulamanız tarafından kullanılan XML Web Hizmetleri erişim sağlar. Koleksiyonları sağlayarak bunu *varsayılan örnekleri* bu nesnelerin her biri.  
  
## <a name="default-instances"></a>Varsayılan örnekleri  
 Varsayılan bir örnek olması gerekmez ve çalışma zamanı tarafından sağlanan sınıfının bir örneği olduğu bildirildi ve örneği kullanarak `Dim` ve `New` deyimleri. Aşağıdaki örnek nasıl sahip olabileceğiniz bildirilmiş ve bir örneğini örneği gösterir. bir <xref:System.Windows.Forms.Form> adlı sınıf `Form1`, ve nasıl artık bu varsayılan örneğini almak <xref:System.Windows.Forms.Form> aracılığıyla sınıf `My.Forms`.  
  
 [!code-vb[VbVbcnMy#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#5)]  
  
 [!code-vb[VbVbcnMy#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#6)]  
  
 `My.Forms` Nesnesi için varsayılan örneklerinin bir koleksiyonunu döndürür her `Form` projenizde var. sınıfı. Benzer şekilde, `My.WebServices` uygulamanızda bir başvuru oluşturduğunuz her Web hizmeti proxy sınıfın varsayılan bir örnek sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [My.Forms Nesnesi](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [My.WebServices Nesnesi](../../../visual-basic/language-reference/objects/my-webservices-object.md)
- [My Özellikleri Proje Türüne Nasıl Bağımlıdır](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
