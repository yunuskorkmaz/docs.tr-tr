---
title: Bileşik Veri Türleri (Visual Basic)
ms.date: 04/25/2017
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
ms.openlocfilehash: ea719b60a6bcd40494666d4923fad296a8ddae70
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61907393"
---
# <a name="composite-data-types-visual-basic"></a>Bileşik Veri Türleri (Visual Basic)
Başlangıç veri türleri Visual Basic kaynakları'na ek olarak, öğeleri oluşturmak için farklı türde de toplayabilir *bileşik veri türleri* yapılar, diziler ve sınıflar gibi. Bileşik veri türleri, temel türleri ve diğer bileşik türler oluşturabilirsiniz. Örneğin, yapı öğeleri bir dizi veya bir yapı dizi üyeleri ile tanımlayabilirsiniz.  
  
## <a name="data-types"></a>Veri Türleri  
 Bileşik tür bileşenlerinden birinin veri türünden farklıdır. Örneğin, bir dizi `Integer` öğeleri değil `Integer` veri türü.  
  
 Öğe türü, parantez ve virgül gerektiği gibi kullanarak bir dizi veri türü normal olarak temsil edilir. Örneğin, tek boyutlu bir dizi `String` öğeler olarak temsil edilir `String()`ve iki boyutlu bir dizi `Boolean` öğeler olarak temsil edilir `Boolean(,)`.  
  
## <a name="structure-types"></a>Yapı türleri  
 Tüm yapıları kapsayan tek bir veri türü yoktur. Bunun yerine, iki yapıları aynı sırada aynı öğeleri tanımlamak olsa bile her bir yapı tanımının bir benzersiz veri türünü temsil eder. Ancak, iki veya daha fazla örneğinin aynı yapısını oluşturursanız, Visual Basic bunları aynı veri türünde olmasını değerlendirir.  
  
## <a name="tuples"></a>Demetler

Bir demet eşleşen türleri önceden tanımlanmıştır iki veya daha fazla alan içeren basit bir yapıdır. Diziler, Visual Basic 2017'den itibaren desteklenir. Diziler başvuruya göre bağımsız değişkenler geçirmek zorunda ya da daha ağır sınıf veya yapı döndürülen alanları paketleme olmadan tek bir yöntem çağrısından birden çok değer döndürmek için en yaygın olarak kullanılır. Bkz: [diziler](tuples.md) konu başlıkları hakkında daha fazla bilgi için.

## <a name="array-types"></a>Dizi türleri  
 Tüm diziler kapsayan tek bir veri türü yoktur. Veri türü bir dizi belirli bir örneğini aşağıdaki tarafından belirlenir:  
  
- Bir dizi olma olgusu  
  
- Dizinin boyut (boyut sayısı)  
  
- Dizinin öğe türü  
  
 Özellikle, belirli bir boyutun uzunluğu örneğinin veri türünün bir parçası değil. Aşağıdaki örnek bunu göstermektedir.  
  
```  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 Önceki örnekte, dizi değişkenleri `arrayA` ve `arrayB` aynı veri türü olarak değerlendirilir: `Byte()` — olsa da bunlar için farklı uzunluktaki başlatılır. Değişkenleri `arrayB` ve `arrayC` kendi öğe türleri farklı olduğundan, aynı türde değildir. Değişkenleri `arrayC` ve `arrayD` kendi sıralamalara sahip farklı olduğundan, aynı türde değildir. Değişkenleri `arrayD` ve `arrayE` aynı türe sahip — `Short(,)` — kendi sıralamalara sahip ve öğe türleri aynı olsa bile olduğundan `arrayD` henüz başlatılmadı.  
  
 Diziler hakkında daha fazla bilgi için bkz. [diziler](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="class-types"></a>Sınıf Türleri  
 Tüm sınıflar kapsayan tek bir veri türü yoktur. Bir sınıf başka bir sınıftan devralabilir olsa da, her bir ayrı veri türü olan. Aynı sınıfın birden çok örneği aynı veri türü var. Başka bir sınıf örneği değişkenini atarsanız, yalnızca aynı veri türüne sahip değilsiniz, bellekte aynı sınıf örneğine işaret edecek.  
  
 Sınıflar hakkında daha fazla bilgi için bkz. [nesneler ve sınıflar](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Başlangıç Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Visual Basic'de genel türler](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Değer Türleri ve Başvuru Türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Visual Basic'de tür dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Yapılar](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Veri Türü Sorunlarını Giderme](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Nasıl yapılır: Değişkende Birden Fazla Değer Tutma](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)
