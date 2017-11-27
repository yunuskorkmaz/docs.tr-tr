---
title: "Visual Basic Sınırlamaları"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- limits
- limitations [Visual Basic]
- limitations
- limits, Visual Basic code
- Visual Basic code, limitations
ms.assetid: cf1646b7-5d24-48c6-9616-bda8a4849d91
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 97a2e162b9f1a673fbe805a5d2ef1421cd423a4f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="visual-basic-limitations"></a>Visual Basic Sınırlamaları
' In önceki sürümlerini [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] zorunlu değişken adları uzunluk gibi kodda sınırları modüller ve modül boyutu, izin verilen değişkenleri sayısı. Visual Basic .NET içinde bu kısıtlamalar, yazma ve düzenleme kodunuzu büyük özgürlüğünü rahat.  
  
 Fiziksel sınırları, çalışma zamanı bellek fazla derleme zamanı etmenlere bağlıdır. Akıllıca programlama yöntemleri kullanın ve büyük uygulamaların birden fazla sınıfları ve modülleri bölmek durumunda İç karşılaşmadan, çok az olasılığı yüksektir [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] sınırlama.  
  
 Olağanüstü durumlarda karşılaşabileceğiniz bazı sınırlamalar şunlardır:  
  
-   **Ad uzunluğu.** Bildirilen her programlama öğe adı için karakter sayısı üst yoktur. Bu üst öğe adı tam tüm nitelik dizisi için geçerlidir. Bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
-   **Satır uzunluğu.** En fazla kaynak kodunun fiziksel bir satırda 65535 karakterden yoktur. Mantıksal kaynak kodu satır satır devamlılığı karakterleri kullanırsanız, daha uzun olabilir. Bkz: [nasıl yapılır: kodda deyimleri bölme ve birleştirme](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).  
  
-   **Dizi boyutları.** Boyutlar için bir dizi bildirebilir sayısı üst yoktur. Bu, bir dizi öğesine belirtmek için kullanabileceğiniz kaç dizinleri sınırlar. Bkz: [dizi boyutları Visual Basic'te](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).  
  
-   **Dize uzunluğu.** Tek bir dize depolayabilir Unicode karakter sayısı üst yoktur. Bkz: [dize veri türü](../../../visual-basic/language-reference/data-types/string-data-type.md).  
  
-   **Ortam dize uzunluğu.** En çok bir komut satırı bağımsız değişken olarak kullanılan herhangi bir ortam dize için 32768 karakter var. Bu tüm platformlarda kısıtlamadır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Program yapısı ve kod kuralları](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [Visual Basic adlandırma kuralları](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
