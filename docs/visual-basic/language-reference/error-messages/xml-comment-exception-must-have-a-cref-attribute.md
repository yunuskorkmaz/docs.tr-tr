---
title: XML açıklama özel durumunda 'cref' özniteliği olmalıdır
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: 2e57dc63cb7ad8b2e061296a082d6fa79b464f08
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592036"
---
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a>XML açıklama özel durumunda 'cref' özniteliği olmalıdır
@No__t-0exception > etiketi, bir yöntem tarafından oluşturulan özel durumları belgelemek için bir yol sağlar. Gerekli `cref` özniteliği, belge Oluşturucu tarafından denetlenen bir üyenin adını belirtir. Üye varsa, belge dosyasında kurallı öğe adına çevrilir.  
  
 **Hata KIMLIĞI:** BC42319  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- @No__t-0 özniteliğini özel duruma aşağıdaki şekilde ekleyin:  
  
    xml  
    ' ' '<exception cref="member">açıklaması</exception>  
    ```  
  
## See also

- [\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md)
- [How to: Create XML Documentation](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/index.md)
