---
title: Başlatıcı bekleniyor
ms.date: 07/20/2015
f1_keywords:
- vbc30996
- bc30996
helpviewer_keywords:
- BC30996
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
ms.openlocfilehash: 77cfeb57bc313ded2d2c4d5a0c59041c5c19f515
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826086"
---
# <a name="initializer-expected"></a>Başlatıcı bekleniyor
Başlatma listesi aşağıdaki örnekte gösterildiği gibi boş olduğu bir nesne Başlatıcı kullanarak bir sınıfın örneği bildirin çalıştınız.  
  
 `' Not valid.`  
  
 `' Dim aStudent As New Student With {}`  
  
 En az bir alan veya özellik Başlatıcı listesinde, aşağıdaki örnekte gösterildiği gibi başlatılmalıdır.  
  
 `Dim aStudent As New Student With {.year = "Senior"}`  
  
 **Hata Kimliği:** BC30996  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  En az bir alan veya özellik başlatıcısında başlatmak veya bir nesne Başlatıcı kullanmayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nesne başlatıcıları: Adlandırılmış ve anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Nasıl yapılır: Bir nesne Başlatıcı kullanarak nesne bildirme](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
