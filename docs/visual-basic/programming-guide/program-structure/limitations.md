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
ms.openlocfilehash: 10f67c02d25ec275d1c3e98197d51c25aa250c19
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824916"
---
# <a name="visual-basic-limitations"></a>Visual Basic Sınırlamaları
Visual Basic'in önceki sürümlerindeki kodda, uzunluğu, değişkeni adları, modülleri ve modül boyutu izin verilen değişken sayısı gibi sınırlar zorunlu. Visual Basic. NET'te, bu kısıtlamalar, yazmak ve kodunuzu düzenleme büyük özgürlüğünü esnek.  
  
 Fiziksel sınırlarına derleme zamanı değerlendirmeleri hakkında daha çalışma zamanı bellek bağımlıdır. Akıllıca programlama uygulamaları kullanır ve büyük uygulamalar birden çok sınıflar ve modüller bölmek, iç bir Visual Basic sınırlaması karşılaşıldığında tutulmaları olasılığı yoktur.  
  
 Aşırı durumlarda karşılaşabileceğiniz bazı sınırlamalar aşağıda verilmiştir:  
  
-   **Ad uzunluğu.** Her bildirilmiş programlama öğesinin adı karakter sayısı yoktur. Öğe adı sağlandıysa bu maksimum tüm nitelik dizisi için geçerlidir. Bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
-   **Satır uzunluğu.** En fazla 65535 karakterden fiziksel bir kaynak kod satırı yoktur. Mantıksal kaynak kodu satır satır devamlılığı karakterleri kullanırsanız, uzun olabilir. Bkz: [nasıl yapılır: Kodda deyimleri bölme ve birleştirme](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).  
  
-   **Dizi boyutları.** Boyutları için bir dizi bildirebilirsiniz sayısı üst sınırı yoktur. Bu, bir dizi öğesine belirlemek için kullanabileceğiniz kaç dizinleri sınırlar. Bkz: [dizi boyutları Visual Basic'te](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).  
  
-   **Dize uzunluğu.** Tek bir dizede depolayabilirsiniz Unicode karakter sayısı yoktur. Bkz: [dize veri türünde](../../../visual-basic/language-reference/data-types/string-data-type.md).  
  
-   **Ortam dize uzunluğu.** En fazla bir komut satırı bağımsız değişken olarak kullanılan herhangi bir ortam dize için 32.768 karakter yoktur. Bu tüm platformlarda sınırlamasıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Program Yapısı ve Kod Kuralları](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Visual Basic adlandırma kuralları](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
