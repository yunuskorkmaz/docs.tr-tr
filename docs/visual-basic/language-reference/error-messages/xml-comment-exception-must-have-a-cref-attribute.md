---
title: XML açıklama özel durumunda 'cref' özniteliği olmalıdır
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: 54965f3796b6c5ef0e387cd354abcb5740476257
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321168"
---
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a>XML açıklama özel durumunda 'cref' özniteliği olmalıdır

@No__t-0exception > etiketi, bir yöntem tarafından oluşturulan özel durumları belgelemek için bir yol sağlar. Gerekli `cref` özniteliği, belge Oluşturucu tarafından denetlenen bir üyenin adını belirtir. Üye varsa, belge dosyasında kurallı öğe adına çevrilir.

**Hata kimliği:** BC42319

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

@No__t-0 özniteliğini özel duruma aşağıdaki şekilde ekleyin:

```xml
<exception cref="member">description</exception>
```

## <a name="see-also"></a>Ayrıca bkz.

- [\< özel durum >](../../../visual-basic/language-reference/xmldoc/exception.md)
- [Nasıl yapılır: XML Belgesi Oluşturma](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [XML Açıklama Etiketleri](../../../visual-basic/language-reference/xmldoc/index.md)
