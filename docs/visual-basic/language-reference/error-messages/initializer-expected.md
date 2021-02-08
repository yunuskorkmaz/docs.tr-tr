---
description: 'Şu konuda daha fazla bilgi edinin: BC30996: Başlatıcı bekleniyor'
title: Başlatıcı bekleniyor
ms.date: 07/20/2015
f1_keywords:
- vbc30996
- bc30996
helpviewer_keywords:
- BC30996
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
ms.openlocfilehash: a9859dc319ec53cb42785d71b21447a097ce30f6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796060"
---
# <a name="bc30996-initializer-expected"></a>BC30996: Başlatıcı bekleniyor

Aşağıdaki örnekte gösterildiği gibi, başlatma listesinin boş olduğu bir nesne Başlatıcısı kullanarak bir sınıfın örneğini bildirmeye çalıştınız.

 `' Not valid.`

 `' Dim aStudent As New Student With {}`

 Aşağıdaki örnekte gösterildiği gibi, en az bir alan veya özellik Başlatıcı listesinde başlatılmalıdır.

 `Dim aStudent As New Student With {.year = "Senior"}`

 **Hata kimliği:** BC30996

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Başlatıcıdaki en az bir alanı veya özelliği başlatın ya da bir nesne Başlatıcısı kullanmayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Nesne Başlatıcıları: Adlandırılmış ve Anonim Türler](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Nasıl yapılır: Nesne Başlatıcı Kullanarak Nesne Bildirme](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
