---
title: Bileşik Veri Türleri (Visual Basic)
ms.custom: ''
ms.date: 04/25/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types [Visual Basic]
- composite data types [Visual Basic]
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures [Visual Basic], composite data types
- classes [Visual Basic], composite types
- types [Visual Basic], composite
ms.assetid: 62970f2e-52c0-4369-8963-613820f1f434
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: caa832fc191ad925674e21b1237ac98328ce0bd7
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="composite-data-types-visual-basic"></a>Bileşik Veri Türleri (Visual Basic)
Başlangıç veri türleri Visual Basic kaynakları ek olarak, öğeleri oluşturmak için farklı türlerde de toplayabilir *bileşik veri türleri* yapıları, dizileri ve sınıflar gibi. Bileşik veri türleri başlangıç türleri ve diğer bileşik türler oluşturabilirsiniz. Örneğin, dizi üyeleriyle yapı öğeleri dizisi veya bir yapı tanımlayabilirsiniz.  
  
## <a name="data-types"></a>Veri Türleri  
 Bileşik tür bileşenlerinin hiçbiri veri türünden farklıdır. Örneğin, bir dizi `Integer` öğeleri değil `Integer` veri türü.  
  
 Öğe türü, parantez ve virgül gerektiği gibi kullanarak bir dizi veri türü normal olarak temsil edilir. Örneğin, tek boyutlu dizi `String` öğeler olarak temsil edilir `String()`ve iki boyutlu bir dizi `Boolean` öğeler olarak temsil edilir `Boolean(,)`.  
  
## <a name="structure-types"></a>Yapı türleri  
 Tüm yapıları kapsayan tek bir veri türü yok. Bunun yerine, iki yapıları aynı sırada aynı öğeleri tanımlamak olsa bile her bir yapı tanımının bir benzersiz veri türünü temsil eder. Ancak, aynı yapısı iki veya daha fazla örneğinin oluşturursanız, Visual Basic bunları aynı veri türünde olmasını değerlendirir.  
  
## <a name="tuples"></a>Demetler

Bir tanımlama grubu, türleri önceden tanımlanmış iki veya daha fazla alan içeren basit bir yapıdır. Diziler, Visual Basic 2017 ile başlayarak desteklenir. Diziler, en yaygın olarak başvuruya göre bağımsız değişkenler geçirmek zorunda ya da daha ağır sınıf veya yapı döndürülen alanları paketleme olmadan bir tek bir yöntem çağrısında birden çok değer döndürmek için kullanılır. Bkz: [diziler](tuples.md) konu başlıkları hakkında daha fazla bilgi için.

## <a name="array-types"></a>Dizi türleri  
 Tüm diziler kapsayan tek bir veri türü yok. Veri türü bir dizi belirli bir örneği aşağıdaki tarafından belirlenir:  
  
-   Bir dizi olma olgusu  
  
-   Dizi derecesini (dimensions sayısı)  
  
-   Dizi öğesi türü  
  
 Özellikle, belirli bir boyut uzunluğu Örneğin veri türü bir parçası değil. Aşağıdaki örnek bunu göstermektedir.  
  
```  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 Önceki örnekte değişkenleri dizi `arrayA` ve `arrayB` aynı veri türünde olduğu kabul edilir — `Byte()` — rağmen farklı uzunlukta başlatılır. Değişkenleri `arrayB` ve `arrayC` öğesi türlerini farklı olduğu için aynı türde değildir. Değişkenleri `arrayC` ve `arrayD` kendi sıralar farklı olduğu için aynı türde değildir. Değişkenleri `arrayD` ve `arrayE` aynı türe sahip — `Short(,)` —, sıralar ve öğe türleri aynı rağmen olduğundan `arrayD` henüz başlatılmadı.  
  
 Dizileri hakkında daha fazla bilgi için bkz: [diziler](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="class-types"></a>Sınıf Türleri  
 Tüm sınıflar kapsayan tek bir veri türü yok. Bir sınıf başka bir sınıfı devralabilirsiniz rağmen her bir ayrı veri türü içerir. Aynı sınıfın birden çok örneği aynı veri türünde olduğundan. Başka bir sınıf örneği değişkeni atarsanız, yalnızca aynı veri türüne sahip değillerse, aynı sınıf örneği bellekte fareyle.  
  
 Sınıfları hakkında daha fazla bilgi için bkz: [nesneler ve sınıflar](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Başlangıç Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Visual Basic'de genel türler](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Değer Türleri ve Başvuru Türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Visual Basic'de tür dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Yapılar](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Veri Türü Sorunlarını Giderme](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Nasıl yapılır: Değişkende Birden Fazla Değer Tutma](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)
