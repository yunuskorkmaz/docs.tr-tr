---
title: "Oluşturucu &#39; &lt;adı&gt;&#39; kendisini çağıramaz"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2361d6f4d710e17a4f4e29ac03bfde523191fa83
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="constructor-39ltnamegt39-cannot-call-itself"></a>Oluşturucu &#39; &lt;adı&gt;&#39; kendisini çağıramaz
A `Sub New` bir sınıf veya yapı yordamda kendisini çağırır.  
  
 Sınıfının bir örneği başlatmak için bir oluşturucu amacı olan veya ilk çalıştırıldığında yapısı oluşturulur. Hepsi farklı parametre listeniz sağlanan birkaç Oluşturucusu bir sınıf veya yapı olabilir. Bir oluşturucu yanı sıra kendi işlevlerini gerçekleştirmek için başka bir oluşturucuyu çağırmak için izin verilir. Ancak bir oluşturucu kendisini çağırmak anlamsız ve aslında bu içinde sonsuz özyineleme izin veriyorsa, neden olur.  
  
 **Hata Kimliği:** BC30298  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Çağrılan Oluşturucusu parametre listesini kontrol edin. Çağrıyı yapan Oluşturucusu farklı olmalıdır.  
  
2.  Farklı bir oluşturucu çağırmak düşünmüyorsanız kaldırmak `Sub New` tamamen çağırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nesne ömrü: Nesneleri oluşturma ve yok etme](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
