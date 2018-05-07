---
title: Oluşturucu &#39; &lt;adı&gt; &#39; kendisini çağıramaz
ms.date: 07/20/2015
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
ms.openlocfilehash: 069de813a0426230e19cddf14c3b83d40a602a41
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="constructor-39ltnamegt39-cannot-call-itself"></a>Oluşturucu &#39; &lt;adı&gt; &#39; kendisini çağıramaz
A `Sub New` bir sınıf veya yapı yordamda kendisini çağırır.  
  
 Sınıfının bir örneği başlatmak için bir oluşturucu amacı olan veya ilk çalıştırıldığında yapısı oluşturulur. Hepsi farklı parametre listeniz sağlanan birkaç Oluşturucusu bir sınıf veya yapı olabilir. Bir oluşturucu yanı sıra kendi işlevlerini gerçekleştirmek için başka bir oluşturucuyu çağırmak için izin verilir. Ancak bir oluşturucu kendisini çağırmak anlamsız ve aslında bu içinde sonsuz özyineleme izin veriyorsa, neden olur.  
  
 **Hata Kimliği:** BC30298  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Çağrılan Oluşturucusu parametre listesini kontrol edin. Çağrıyı yapan Oluşturucusu farklı olmalıdır.  
  
2.  Farklı bir oluşturucu çağırmak düşünmüyorsanız kaldırmak `Sub New` tamamen çağırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nesne Ömrü: Nesneleri Oluşturma ve Yok Etme](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
