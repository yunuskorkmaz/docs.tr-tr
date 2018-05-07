---
title: Visual Basic Sınırlamaları
ms.date: 07/20/2015
helpviewer_keywords:
- limits
- limitations [Visual Basic]
- limitations
- limits, Visual Basic code
- Visual Basic code, limitations
ms.assetid: cf1646b7-5d24-48c6-9616-bda8a4849d91
ms.openlocfilehash: 57378c3aa18a5cc108c10e8654e55803f3cf9052
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="visual-basic-limitations"></a>Visual Basic Sınırlamaları
Önceki sürümleri, Visual Basic değişken adları, modüller ve modül boyutu izin verilen değişken sayısı uzunluğu gibi kodda sınırları zorunlu. Visual Basic .NET içinde bu kısıtlamalar, yazma ve düzenleme kodunuzu büyük özgürlüğünü rahat.  
  
 Fiziksel sınırları, çalışma zamanı bellek fazla derleme zamanı etmenlere bağlıdır. Akıllıca programlama uygulamalarını kullanırsanız ve büyük uygulamaların birden fazla sınıfları ve modülleri bölmek, dahili bir Visual Basic sınırlaması karşılaşmadan çok az ihtimalini yoktur.  
  
 Olağanüstü durumlarda karşılaşabileceğiniz bazı sınırlamalar şunlardır:  
  
-   **Ad uzunluğu.** Bildirilen her programlama öğe adı için karakter sayısı üst yoktur. Bu üst öğe adı tam tüm nitelik dizisi için geçerlidir. Bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
-   **Satır uzunluğu.** En fazla kaynak kodunun fiziksel bir satırda 65535 karakterden yoktur. Mantıksal kaynak kodu satır satır devamlılığı karakterleri kullanırsanız, daha uzun olabilir. Bkz: [nasıl yapılır: kodda deyimleri bölme ve birleştirme](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).  
  
-   **Dizi boyutları.** Boyutlar için bir dizi bildirebilir sayısı üst yoktur. Bu, bir dizi öğesine belirtmek için kullanabileceğiniz kaç dizinleri sınırlar. Bkz: [dizi boyutları Visual Basic'te](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).  
  
-   **Dize uzunluğu.** Tek bir dize depolayabilir Unicode karakter sayısı üst yoktur. Bkz: [dize veri türü](../../../visual-basic/language-reference/data-types/string-data-type.md).  
  
-   **Ortam dize uzunluğu.** En çok bir komut satırı bağımsız değişken olarak kullanılan herhangi bir ortam dize için 32768 karakter var. Bu tüm platformlarda kısıtlamadır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Program Yapısı ve Kod Kuralları](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [Visual Basic adlandırma kuralları](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
