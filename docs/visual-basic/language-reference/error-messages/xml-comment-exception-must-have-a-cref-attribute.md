---
title: XML açıklama özel olmalıdır bir &#39;cref&#39; özniteliği
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: abe9fe0f6216f81fa223fe83a122b580577e1c32
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43255651"
---
# <a name="xml-comment-exception-must-have-a-39cref39-attribute"></a>XML açıklama özel olmalıdır bir &#39;cref&#39; özniteliği
\<Özel durum > etiketi yöntemi tarafından oluşturulan özel durumları belge için bir yol sağlar. Gerekli `cref` öznitelik belgeleri Oluşturucu tarafından denetlenir bir üyenin adını belirtir. Üye varsa, kurallı öğe adı belgeleri dosyasına çevrilir.  
  
 **Hata Kimliği:** BC42319  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Ekleme `cref` özniteliğini aşağıdaki gibi özel durumu:  
  
    ```  
    '''<exception cref="member">description</exception>  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [\<Özel Durum >](../../../visual-basic/language-reference/xmldoc/exception.md)  
 [Nasıl yapılır: XML Belgesi Oluşturma](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
 [XML Açıklama Etiketleri](../../../visual-basic/language-reference/xmldoc/index.md)
