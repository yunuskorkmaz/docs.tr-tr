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
ms.openlocfilehash: abe4acd5850aa6065bf4f6fd41bc610ede7ad13f
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097962"
---
# <a name="visual-basic-limitations"></a>Visual Basic Sınırlamaları

Kodda, değişken adlarının uzunluğu, modüllerde izin verilen değişkenlerin sayısı ve modül boyutu gibi Visual Basic Zorlanmış sınırların daha eski sürümleri. Visual Basic .NET sürümünde, bu kısıtlamalar gevşek bir şekilde, kodunuzu yazarken ve düzenleme konusunda daha fazla serbestlik sağlar.  
  
 Fiziksel sınırlar, derleme zamanı önemli noktaları ile daha fazla çalışma zamanı belleğine bağlıdır. Akıllıca programlama uygulamalarını kullanır ve büyük uygulamaları birden çok sınıfa ve modüle bölebilir, bir iç Visual Basic sınırlamasından kaçınmanın çok kısa bir olasılığı vardır.  
  
 Aşağıda, olağanüstü durumlarda karşılaşabileceğiniz bazı sınırlamalar verilmiştir:  
  
- **Ad uzunluğu.** Her bir bildirilmeyen programlama öğesinin adı için en fazla karakter sayısı vardır. Öğe adı nitelikli ise, bu en büyük bir nitelik dizesinin tamamına uygulanır. Bkz. [tanımlanmış öğe adları](../language-features/declared-elements/declared-element-names.md).  
  
- **Satır uzunluğu.** Kaynak kodunun fiziksel satırında en fazla 65535 karakter vardır. Satır devamlılık karakterleri kullanırsanız mantıksal kaynak kodu satırı daha uzun olabilir. Bkz. [nasıl yapılır: koddaki deyimleri kesme ve birleştirme](how-to-break-and-combine-statements-in-code.md).  
  
- **Dizi boyutları.** Bir dizi için bildirebilen en fazla boyut sayısı vardır. Bu, bir dizi öğesi belirtmek için kullanabileceğiniz dizin sayısını sınırlar. [Visual Basic 'de dizi boyutlarına](../language-features/arrays/array-dimensions.md)bakın.  
  
- **Dize uzunluğu.** Tek bir dizede depolayabileceğiniz en fazla Unicode karakter sayısı vardır. Bkz. [dize veri türü](../../language-reference/data-types/string-data-type.md).  
  
- **Ortam dize uzunluğu.** Komut satırı bağımsız değişkeni olarak kullanılan herhangi bir ortam dizesi için en fazla 32768 karakter vardır. Bu, Tüm platformlardaki bir kısıtlamadır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Program yapısı ve kod kuralları](program-structure-and-code-conventions.md)
- [Visual Basic Adlandırma Kuralları](naming-conventions.md)
