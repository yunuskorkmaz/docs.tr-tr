---
description: "Hakkında daha fazla bilgi edinin: BC31183: XML ad alanı URI 'SI `http://www.w3.org/XML/1998/namespace` ; yalnızca ' xmlns 'ye bağlanabilir"
title: XML as alanı URI’si '<uri>' yalnızca 'xmlns' ile bağlanabilir
ms.date: 07/20/2015
f1_keywords:
- bc31183
- vbc31183
helpviewer_keywords:
- BC31183
ms.assetid: 0ab1dbce-8397-4959-b2cd-f58798b051a0
ms.openlocfilehash: e6a552f4754a12b8e80e5333232d0c48432f7a63
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701397"
---
# <a name="bc31183-xml-namespace-uri-httpwwww3orgxml1998namespace-can-be-bound-only-to-xmlns"></a>BC31183: XML ad alanı URI `http://www.w3.org/XML/1998/namespace` ; yalnızca ' xmlns ' öğesine bağlanabilir

URI, `http://www.w3.org/XML/1998/namespace` BIR XML ad alanı bildiriminde kullanılır. Bu URI ayrılmış bir ad alanıdır ve bir XML ad alanı bildirimine dahil edilemez.

 **Hata kimliği:** BC31183

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

XML ad alanı bildirimini kaldırın veya URI `http://www.w3.org/XML/1998/namespace` 'yi geçerli bir ad alanı URI 'si ile değiştirin.

## <a name="see-also"></a>Ayrıca bkz.

- [Imports Deyimi (XML Ad Alanı)](../statements/imports-statement-xml-namespace.md)
- [XML Değişmez Değerleri](../xml-literals/index.md)
- [XML](../../programming-guide/language-features/xml/index.md)
