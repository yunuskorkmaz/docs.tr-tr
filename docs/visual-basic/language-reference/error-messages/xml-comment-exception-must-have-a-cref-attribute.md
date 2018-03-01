---
title: "XML açıklama özel olmalıdır bir &#39; cref &#39; özniteliği"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c0c22c9cd9415faf17d027c3751d166662a92b50
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="xml-comment-exception-must-have-a-39cref39-attribute"></a>XML açıklama özel olmalıdır bir &#39; cref &#39; özniteliği
\<Özel durum > etiketi yöntemi tarafından oluşturulan özel durumları belge için bir yol sağlar. Gerekli `cref` özniteliği belgelerine Oluşturucu tarafından denetlenir bir üyenin adını belirtir. Üye varsa, belge dosyasındaki kurallı öğe adı için çevrilir.  
  
 **Hata Kimliği:** BC42319  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Ekleme `cref` özniteliğini aşağıdaki gibi özel durumu:  
  
    ```  
    '''<exception cref="member">description</exception>  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [\<Özel Durum >](../../../visual-basic/language-reference/xmldoc/exception.md)  
 [Nasıl yapılır: XML belgesi oluşturma](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
 [XML açıklama etiketleri](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
