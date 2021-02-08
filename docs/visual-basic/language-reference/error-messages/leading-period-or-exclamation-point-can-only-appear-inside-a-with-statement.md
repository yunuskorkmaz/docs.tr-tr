---
description: "Hakkında daha fazla bilgi: BC30157: baştaki '. ' veya '! ' yalnızca ' with ' ifadesinin içinde bulunabilir"
title: Baştaki '.' veya '!' yalnızca 'With' deyimi içinde bulunabilir
ms.date: 07/20/2015
f1_keywords:
- vbc30157
- bc30157
helpviewer_keywords:
- BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
ms.openlocfilehash: e0325ac3c54046718d71df37edaac1edaf12f43e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795904"
---
# <a name="bc30157-leading--or--can-only-appear-inside-a-with-statement"></a>BC30157: baştaki '. ' veya '! ' yalnızca ' with ' ifadesinin içinde bulunabilir

Bir blok içinde olmayan bir nokta (.) veya ünlem işareti (!) `With` sol tarafta bir ifade olmadan meydana gelir. Üye erişimi ( `.` ) ve sözlük üye erişimi ( `!` ), üyeyi içeren öğeyi belirten bir ifade gerektirir. Bu, erişimcinin hemen solunda veya `With` üye erişimini içeren bir bloğun hedefi olarak görünmelidir.

 **Hata kimliği:** BC30157

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. `With`Bloğun doğru biçimlendirildiğinden emin olun.

2. `With`Blok yoksa, üyeyi içeren tanımlanmış bir öğe için değerlendirilen erişimcinin soluna bir ifade ekleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Koddaki Özel Karakterler](../../programming-guide/program-structure/special-characters-in-code.md)
- [With...End With Deyimi](../statements/with-end-with-statement.md)
