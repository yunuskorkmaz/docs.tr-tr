---
title: Bu dizi sabit veya geçici olarak kilitli (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
ms.openlocfilehash: c74d9524ff64101ba6002e133b93c9b80e8f50a9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61982455"
---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a>Bu dizi sabit veya geçici olarak kilitli (Visual Basic)
Bu hata, aşağıdaki olası nedenleri vardır:  
  
- Kullanarak `ReDim` sabit boyutlu dizi öğelerinin sayısını değiştirmek için.  
  
- İçinde bir öğe bağımsız değişken olarak bir yordamına geçirildi bir modül düzeyinde dinamik dizi redimensioning. Bir öğe iletilmezse, dizi önlemek için kilitli yordamdaki başvuru parametresi bellek ayırma.  
  
- Bir değere atanmaya çalışılırken bir `Variant` içeren bir dizi değişkenini ancak `Variant` şu anda kilitli.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Özgün dizinin kendisiyle bildirerek sabit yerine dinamik hale getirmek `ReDim` (diziyi bir yordam içinde bildirilirse), ya da (diziyi Modül düzeyinde bildirilirse. öğe sayısını belirtmeden bildirme  
  
2. Modüldeki tüm yordamları içinde görünür olduğundan, öğeyi geçirilecek ihtiyacınız olup olmadığını belirler.  
  
3. Ne kilitleme belirlemek `Variant` ve çözüm.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md)
