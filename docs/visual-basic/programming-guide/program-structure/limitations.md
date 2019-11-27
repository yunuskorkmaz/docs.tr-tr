---
title: Sınırlamalar
ms.date: 07/20/2015
helpviewer_keywords:
- limits
- limitations [Visual Basic]
- limitations
- limits, Visual Basic code
- Visual Basic code, limitations
ms.assetid: cf1646b7-5d24-48c6-9616-bda8a4849d91
ms.openlocfilehash: f7e19977a011565bb4b1536af5cab195f8a01017
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347363"
---
# <a name="visual-basic-limitations"></a>Visual Basic Sınırlamaları
Kodda, değişken adlarının uzunluğu, modüllerde izin verilen değişkenlerin sayısı ve modül boyutu gibi Visual Basic Zorlanmış sınırların daha eski sürümleri. Visual Basic .NET sürümünde, bu kısıtlamalar gevşek bir şekilde, kodunuzu yazarken ve düzenleme konusunda daha fazla serbestlik sağlar.  
  
 Fiziksel sınırlar, derleme zamanı önemli noktaları ile daha fazla çalışma zamanı belleğine bağlıdır. Akıllıca programlama uygulamalarını kullanır ve büyük uygulamaları birden çok sınıfa ve modüle bölebilir, bir iç Visual Basic sınırlamasından kaçınmanın çok kısa bir olasılığı vardır.  
  
 Aşağıda, olağanüstü durumlarda karşılaşabileceğiniz bazı sınırlamalar verilmiştir:  
  
- **Ad uzunluğu.** Her bir bildirilmeyen programlama öğesinin adı için en fazla karakter sayısı vardır. Öğe adı nitelikli ise, bu en büyük bir nitelik dizesinin tamamına uygulanır. Bkz. [tanımlanmış öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
- **Satır uzunluğu.** Kaynak kodunun fiziksel satırında en fazla 65535 karakter vardır. Satır devamlılık karakterleri kullanırsanız mantıksal kaynak kodu satırı daha uzun olabilir. Bkz. [nasıl yapılır: koddaki deyimleri kesme ve birleştirme](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).  
  
- **Dizi boyutları.** Bir dizi için bildirebilen en fazla boyut sayısı vardır. Bu, bir dizi öğesi belirtmek için kullanabileceğiniz dizin sayısını sınırlar. [Visual Basic 'de dizi boyutlarına](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md)bakın.  
  
- **Dize uzunluğu.** Tek bir dizede depolayabileceğiniz en fazla Unicode karakter sayısı vardır. Bkz. [dize veri türü](../../../visual-basic/language-reference/data-types/string-data-type.md).  
  
- **Ortam dize uzunluğu.** Komut satırı bağımsız değişkeni olarak kullanılan herhangi bir ortam dizesi için en fazla 32768 karakter vardır. Bu, Tüm platformlardaki bir kısıtlamadır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Program Yapısı ve Kod Kuralları](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Visual Basic adlandırma kuralları](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
