---
title: Başlatıcı bekleniyor
ms.date: 07/20/2015
f1_keywords:
- vbc30996
- bc30996
helpviewer_keywords:
- BC30996
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
ms.openlocfilehash: 2c5a65443dc16a600e25fcf6dfd11c4597b3a086
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873948"
---
# <a name="initializer-expected"></a>Başlatıcı bekleniyor

Aşağıdaki örnekte gösterildiği gibi, başlatma listesinin boş olduğu bir nesne Başlatıcısı kullanarak bir sınıfın örneğini bildirmeye çalıştınız.  
  
 `' Not valid.`  
  
 `' Dim aStudent As New Student With {}`  
  
 Aşağıdaki örnekte gösterildiği gibi, en az bir alan veya özellik Başlatıcı listesinde başlatılmalıdır.  
  
 `Dim aStudent As New Student With {.year = "Senior"}`  
  
 **Hata kimliği:** BC30996  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Başlatıcıdaki en az bir alanı veya özelliği başlatın ya da bir nesne Başlatıcısı kullanmayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nesne Başlatıcıları: Adlandırılmış ve Anonim Türler](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Nasıl yapılır: Nesne Başlatıcı Kullanarak Nesne Bildirme](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
