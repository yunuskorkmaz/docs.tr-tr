---
title: Başlatıcı bekleniyor
ms.date: 07/20/2015
f1_keywords:
- vbc30996
- bc30996
helpviewer_keywords:
- BC30996
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
ms.openlocfilehash: 9d786fd1e929129c420b7bec62efd0bd445d85eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="initializer-expected"></a>Başlatıcı bekleniyor
Başlatma listesi aşağıdaki örnekte gösterildiği gibi boş olduğu nesne Başlatıcı kullanarak bir sınıfın örneğini bildirme denediniz.  
  
 `' Not valid.`  
  
 `' Dim aStudent As New Student With {}`  
  
 En az bir alan veya özellik Başlatıcı listesinde, aşağıdaki örnekte gösterildiği gibi başlatılması gerekir.  
  
 `Dim aStudent As New Student With {.year = "Senior"}`  
  
 **Hata Kimliği:** BC30996  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  En az bir alan veya Başlatıcı özelliğinde başlatmak veya nesne Başlatıcı kullanmayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nesne Başlatıcıları: Adlandırılmış ve Anonim Tipler](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [Nasıl yapılır: Nesne Başlatıcısı Kullanarak Nesne Bildirme](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
