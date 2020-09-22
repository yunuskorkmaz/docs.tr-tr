---
title: Bu dizi sabit veya geçici olarak kilitli
ms.date: 07/20/2015
f1_keywords:
- vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
ms.openlocfilehash: 05fb8e2ef788920fd200d79a75eec3d7c252b123
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873584"
---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a>Bu dizi sabit veya geçici olarak kilitli (Visual Basic)

Bu hatanın olası nedenleri şunlardır:  
  
- `ReDim`Sabit boyutlu bir dizinin öğelerinin sayısını değiştirmek için kullanma.  
  
- Bir öğe için bağımsız değişken olarak geçirilen bir modül düzeyinde dinamik dizi yeniden boyutlama. Bir öğe geçirilirse, işlem içindeki başvuru parametresi için bellek ayırmayı engellemek üzere dizi kilitlenir.  
  
- Bir dizi içeren bir değişkene değer atamaya çalışılıyor `Variant` , ancak `Variant` Şu anda kilitli.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Özgün diziyi, ile bildirerek sabit yerine dinamik yapın `ReDim` (dizi bir yordam içinde bildirilirse) veya öğe sayısını belirtmeden (dizi modül düzeyinde bildirilirse).  
  
2. Modüldeki tüm yordamlarda görünür olduğundan, gerçekten öğeyi iletmeniz gerekip gerekmediğini belirleme.  
  
3. Neyi kilitleyeceğini `Variant` ve bu öğeyi nasıl yaptığını saptayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Diziler](../../programming-guide/language-features/arrays/index.md)
