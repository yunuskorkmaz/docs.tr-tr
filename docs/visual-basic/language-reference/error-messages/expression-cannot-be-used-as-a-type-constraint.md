---
title: "&#39; &lt;ifade&gt;&#39; tür sınırlaması kullanılamaz"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32061
- vbc32061
helpviewer_keywords: BC32061
ms.assetid: b17821b7-fa14-4397-a211-6e2a14079f09
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c7271018a93c97ed90dc272f7f5404c0f0a22d42
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="39ltexpressiongt39-cannot-be-used-as-a-type-constraint"></a>&#39; &lt;ifade&gt;&#39; tür sınırlaması kullanılamaz
Bir kısıtlama listesi bir tür parametresi geçerli bir kısıtlaması göstermiyor bir ifade içerir.  
  
 Kısıtlama listesini türü parametresine geçirilen tür bağımsız değişkeni gereksinimlerine uygular. Aşağıdaki gereksinimleri herhangi bir bileşimini belirtebilirsiniz:  
  
-   Tür bağımsız değişkeni bir veya daha fazla arabirim uygulamalıdır  
  
-   Tür bağımsız değişkeni en fazla bir sınıftan gerekir  
  
-   Tür bağımsız değişkeni oluşturma kodu erişebilirsiniz parametresiz bir kurucusu kullanıma gerekir (dahil `New` kısıtlaması)  
  
 Kısıtlama listesinde herhangi bir belirli bir sınıf veya arabirim içermiyorsa, aşağıdakilerden birini belirterek daha genel bir gereksinim uygulayabilirsiniz:  
  
-   Tür bağımsız değişkeni bir değer türü olması gerekir (dahil `Structure` kısıtlaması)  
  
-   Tür bağımsız değişkeni bir başvuru türü olmalıdır (dahil `Class` kısıtlaması)  
  
 Her ikisini birden belirtemezsiniz `Structure` ve `Class` aynı tür için parametre ve bunlardan birini birden çok kez belirtilemez.  
  
 **Hata Kimliği:** BC32061  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   İfade ve öğeleri doğru yazdığınızdan emin olun.  
  
-   İfade önceki gereksinimlerinin listesi için uygun değilse, kısıtlama listesinden kaldırın.  
  
-   İfade bir arabirim ya da sınıf başvuruyorsa, derleyici bu arabirimi veya sınıf erişimi olduğunu doğrulayın. Projeniz için bir başvuru eklemeniz gerekebilir ve adını nitelemek gerekebilir. Daha fazla bilgi için bkz: "Projeleri başvuruları" [bildirilmiş öğelere başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Değer Türleri ve Başvuru Türleri](../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Bildirilmiş Öğelere Başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 
