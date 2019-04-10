---
title: Başlatıcı bekleniyor
ms.date: 07/20/2015
f1_keywords:
- vbc30996
- bc30996
helpviewer_keywords:
- BC30996
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
ms.openlocfilehash: 0795fdc1c4b177e13979d7555cd7588217b8cb4c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59334971"
---
# <a name="initializer-expected"></a>Başlatıcı bekleniyor
Başlatma listesi aşağıdaki örnekte gösterildiği gibi boş olduğu bir nesne Başlatıcı kullanarak bir sınıfın örneği bildirin çalıştınız.  
  
 `' Not valid.`  
  
 `' Dim aStudent As New Student With {}`  
  
 En az bir alan veya özellik Başlatıcı listesinde, aşağıdaki örnekte gösterildiği gibi başlatılmalıdır.  
  
 `Dim aStudent As New Student With {.year = "Senior"}`  
  
 **Hata Kimliği:** BC30996  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. En az bir alan veya özellik başlatıcısında başlatmak veya bir nesne Başlatıcı kullanmayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nesne Başlatıcıları: Adlandırılmış ve Anonim Türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Nasıl yapılır: Nesne Başlatıcısı Kullanarak Nesne Bildirme](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
