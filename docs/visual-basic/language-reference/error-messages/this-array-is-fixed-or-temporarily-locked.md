---
title: Bu dizi sabit veya geçici olarak kilitli (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
ms.openlocfilehash: e912bd202603d9a0f427418708ad584c7d6203e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a>Bu dizi sabit veya geçici olarak kilitli (Visual Basic)
Bu hata, aşağıdaki olası nedenleri vardır:  
  
-   Kullanarak `ReDim` bir sabit boyutlu dizi öğelerinin sayısını değiştirmek için.  
  
-   İçinde bir öğe bağımsız değişken olarak bir yordama geçirildi bir modül düzeyi dinamik dizi redimensioning. Bir öğenin aktarılırsa, dizi önlemek için kilitlenir yordamdaki başvuru parametre bellek ayırma.  
  
-   Bir değer atamaya deneyen bir `Variant` içeren bir dizi değişken ancak `Variant` şu anda kilitli.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Özgün dizi yerine ile bildirerek sabit dinamik olun `ReDim` (dizinin bir yordam içinde bildirilen varsa), ya da (array modülü düzeyinde bildirilirse. öğe sayısı belirtmeden bildirme  
  
2.  Sizin gerçekten modülündeki tüm yordamları içinde görünür olduğundan öğesi geçirmek gerekip gerekmeyeceğini belirleyin.  
  
3.  Ne kilitleme belirlemek `Variant` ve çözüm.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md)
