---
title: Yapıcı '<name>' kendisini çağıramaz
ms.date: 07/20/2015
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
ms.openlocfilehash: 8459ee7fec6d761161a721c88ccdc88e513fc95f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59324389"
---
# <a name="constructor-name-cannot-call-itself"></a>Yapıcı '\<adı >' kendisini çağıramaz
A `Sub New` bir sınıf veya yapı yordamda kendisini çağırır.  
  
 Bir sınıfın bir örneği başlatmak için bir oluşturucu amacı olan veya ilk çalıştırıldığında yapısı oluşturulur. Sağlanan tüm farklı parametre listeleri sahip bir sınıf veya yapı birçok oluşturucuya sahip olabilir. Bir oluşturucu kendi ek işlevselliği gerçekleştirmek için başka bir oluşturucuyu çağırmak için izin verilir. Ancak bir oluşturucu kendi çağrılacak anlamsız olduğu ve hatta, sonsuz özyineleme durumuna yol izin veriyorsa, neden olur.  
  
 **Hata Kimliği:** BC30298  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Çağrılan Oluşturucusu parametre listesini kontrol edin. Bu, çağrıyı yapan Oluşturucusu farklı olmalıdır.  
  
2. Farklı bir oluşturucuyu çağırmak düşünmüyorsanız kaldırmak `Sub New` tamamen çağırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nesne ömrü: Nesnelerin nasıl oluşturulduğunu ve yok](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
