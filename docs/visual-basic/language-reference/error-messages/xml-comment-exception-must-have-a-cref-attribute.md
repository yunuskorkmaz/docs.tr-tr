---
title: XML açıklama özel durumunda 'cref' özniteliği olmalıdır
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: c498675ab6ae616fb63d3d76ef60bcac7e247145
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406514"
---
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a>XML açıklama özel durumunda 'cref' özniteliği olmalıdır

\<exception>Etiketi, bir yöntem tarafından oluşturulan özel durumları belgelemek için bir yol sağlar. Gerekli `cref` öznitelik, belge Oluşturucu tarafından denetlenen bir üyenin adını belirtir. Üye varsa, belge dosyasında kurallı öğe adına çevrilir.

**Hata kimliği:** BC42319

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

`cref`Özel duruma şu şekilde özniteliği ekleyin:

```xml
<exception cref="member">description</exception>
```

## <a name="see-also"></a>Ayrıca bkz.

- [\<exception>](../xmldoc/exception.md)
- [Nasıl yapılır: XML Belgesi Oluşturma](../../programming-guide/program-structure/how-to-create-xml-documentation.md)
- [XML Açıklama Etiketleri](../xmldoc/index.md)
