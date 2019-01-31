---
title: Yapıcı '<name>' kendisini çağıramaz
ms.date: 07/20/2015
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
ms.openlocfilehash: 67933e9365b1aa18063f0ccf3c2146a261e7eafc
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55276048"
---
# <a name="constructor-name-cannot-call-itself"></a>Yapıcı '\<adı >' kendisini çağıramaz
A `Sub New` bir sınıf veya yapı yordamda kendisini çağırır.  
  
 Bir sınıfın bir örneği başlatmak için bir oluşturucu amacı olan veya ilk çalıştırıldığında yapısı oluşturulur. Sağlanan tüm farklı parametre listeleri sahip bir sınıf veya yapı birçok oluşturucuya sahip olabilir. Bir oluşturucu kendi ek işlevselliği gerçekleştirmek için başka bir oluşturucuyu çağırmak için izin verilir. Ancak bir oluşturucu kendi çağrılacak anlamsız olduğu ve hatta, sonsuz özyineleme durumuna yol izin veriyorsa, neden olur.  
  
 **Hata Kimliği:** BC30298  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Çağrılan Oluşturucusu parametre listesini kontrol edin. Bu, çağrıyı yapan Oluşturucusu farklı olmalıdır.  
  
2.  Farklı bir oluşturucuyu çağırmak düşünmüyorsanız kaldırmak `Sub New` tamamen çağırın.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Nesne ömrü: Nesnelerin nasıl oluşturulduğunu ve yok](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
