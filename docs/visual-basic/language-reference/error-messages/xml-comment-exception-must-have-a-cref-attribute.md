---
title: XML açıklama özel olmalıdır bir &#39;cref&#39; özniteliği
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: 0f276781165e80b2d869da2518dbe34b33085d5c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54649953"
---
# <a name="xml-comment-exception-must-have-a-39cref39-attribute"></a>XML açıklama özel olmalıdır bir &#39;cref&#39; özniteliği
\<Özel durum > etiketi yöntemi tarafından oluşturulan özel durumları belge için bir yol sağlar. Gerekli `cref` öznitelik belgeleri Oluşturucu tarafından denetlenir bir üyenin adını belirtir. Üye varsa, kurallı öğe adı belgeleri dosyasına çevrilir.  
  
 **Hata Kimliği:** BC42319  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Ekleme `cref` özniteliğini aşağıdaki gibi özel durumu:  
  
    ```  
    '''<exception cref="member">description</exception>  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [\<Özel Durum >](../../../visual-basic/language-reference/xmldoc/exception.md)
- [Nasıl yapılır: XML belgesi oluşturma](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [XML Açıklama Etiketleri](../../../visual-basic/language-reference/xmldoc/index.md)
