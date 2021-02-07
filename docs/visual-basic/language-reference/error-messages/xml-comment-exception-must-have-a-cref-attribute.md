---
description: "Hakkında daha fazla bilgi edinin: BC42319: XML açıklama özel durumu ' cref ' özniteliğine sahip olmalıdır"
title: XML açıklama özel durumunda 'cref' özniteliği olmalıdır
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: e602a2973d95f70d5ab532e6be319a9575d239a7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701462"
---
# <a name="bc42319-xml-comment-exception-must-have-a-cref-attribute"></a>BC42319: XML açıklama özel durumunun ' cref ' özniteliği olmalıdır

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
