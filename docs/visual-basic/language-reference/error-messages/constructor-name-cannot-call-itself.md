---
title: Oluşturucu &#39; &lt;adı&gt; &#39; kendisini çağıramaz
ms.date: 07/20/2015
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
ms.openlocfilehash: 4a02277893147716098a3dcc327e221e0775d476
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662731"
---
# <a name="constructor-39ltnamegt39-cannot-call-itself"></a>Oluşturucu &#39; &lt;adı&gt; &#39; kendisini çağıramaz
A `Sub New` bir sınıf veya yapı yordamda kendisini çağırır.  
  
 Bir sınıfın bir örneği başlatmak için bir oluşturucu amacı olan veya ilk çalıştırıldığında yapısı oluşturulur. Sağlanan tüm farklı parametre listeleri sahip bir sınıf veya yapı birçok oluşturucuya sahip olabilir. Bir oluşturucu kendi ek işlevselliği gerçekleştirmek için başka bir oluşturucuyu çağırmak için izin verilir. Ancak bir oluşturucu kendi çağrılacak anlamsız olduğu ve hatta, sonsuz özyineleme durumuna yol izin veriyorsa, neden olur.  
  
 **Hata Kimliği:** BC30298  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Çağrılan Oluşturucusu parametre listesini kontrol edin. Bu, çağrıyı yapan Oluşturucusu farklı olmalıdır.  
  
2.  Farklı bir oluşturucuyu çağırmak düşünmüyorsanız kaldırmak `Sub New` tamamen çağırın.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Nesne ömrü: Nesnelerin nasıl oluşturulduğunu ve yok](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
