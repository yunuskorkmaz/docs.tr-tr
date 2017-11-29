---
title: "Bu dizi sabit veya geçici olarak kilitli (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: adff10d4ae61e45402df64ebaa3baf146371ff9e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
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
