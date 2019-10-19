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
ms.openlocfilehash: 768559c7a6caf064f7529786675e51ce19667d6b
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581709"
---
# <a name="composite-data-types-visual-basic"></a>Bileşik Veri Türleri (Visual Basic)
Visual Basic tedariklerini temel veri türlerine ek olarak, yapılar, diziler ve sınıflar gibi *bileşik veri türleri* oluşturmak için farklı türlerdeki öğeleri de birleştirebilirsiniz. Birleşik veri türlerini temel türler ve diğer bileşik türlerden oluşturabilirsiniz. Örneğin, bir yapı öğeleri dizisi veya dizi üyeleri olan bir yapı tanımlayabilirsiniz.  
  
## <a name="data-types"></a>Veri Türleri  
 Bileşik tür, bileşenlerinden herhangi birinin veri türünden farklıdır. Örneğin, bir dizi `Integer` öğesi `Integer` veri türünde değildir.  
  
 Dizi veri türü, normalde öğe türü, parantezler ve gereken virgüller kullanılarak temsil edilir. Örneğin, tek boyutlu bir `String` öğeleri `String()` olarak temsil edilir ve iki boyutlu bir dizi `Boolean` öğesi `Boolean(,)` olarak temsil edilir.  
  
## <a name="structure-types"></a>Yapı türleri  
 Tüm yapıları kapsayan tek bir veri türü yoktur. Bunun yerine, bir yapının her tanımı, iki yapı aynı sırada aynı öğeleri tanımlasa bile benzersiz bir veri türünü temsil eder. Ancak, aynı yapının iki veya daha fazla örneğini oluşturursanız Visual Basic, bunları aynı veri türünde olacak şekilde değerlendirir.  
  
## <a name="tuples"></a>Demetler

Kayıt düzeni, türleri önceden tanımlanmış iki veya daha fazla alan içeren hafif bir yapıdır. Tanımlama grupları Visual Basic 2017 ' den başlayarak desteklenir. Tanımlama alanları, bağımsız değişkenleri başvuruya göre geçirmek veya döndürülen alanları daha ağır bir sınıfta veya yapıda paketlemek zorunda kalmadan, tek bir yöntem çağrısından birden çok değer döndürmek için en yaygın olarak kullanılır. Tanımlama grupları hakkında daha fazla bilgi için [Tanımlama grupları](tuples.md) konusuna bakın.

## <a name="array-types"></a>Dizi türleri  
 Tüm dizileri kapsayan tek veri türü yok. Bir dizinin belirli bir örneğinin veri türü aşağıdaki şekilde belirlenir:  
  
- Bir dizi olması  
  
- Dizinin derecesi (boyut sayısı)  
  
- Dizinin öğe türü  
  
 Özellikle, belirli bir boyutun uzunluğu örneğin veri türünün bir parçası değildir. Aşağıdaki örnek bunu göstermektedir.  
  
```vb  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 Yukarıdaki örnekte, `arrayA` ve `arrayB` dizi değişkenleri, farklı uzunluklara başlatılmalarına rağmen aynı veri türünde (`Byte()`) olarak değerlendirilir. @No__t_0 ve `arrayC` değişkenleri, öğe türleri farklı olduğundan aynı türde değil. @No__t_0 ve `arrayD` değişkenleri, dereceleri farklı olduğundan aynı türde değil. @No__t_0 ve `arrayE` değişkenleri aynı türde olmalıdır — `Short(,)` — `arrayD` henüz başlatılmamış olsa da, dereceleri ve öğe türleri aynı olduğundan.  
  
 Diziler hakkında daha fazla bilgi için bkz. [diziler](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="class-types"></a>Sınıf Türleri  
 Tüm sınıflardan oluşan tek bir veri türü yoktur. Bir sınıf başka bir sınıftan devralınabilir olsa da, her biri ayrı bir veri türüdür. Aynı sınıfın birden çok örneği aynı veri türündedir. Bir sınıf örneği değişkenini diğerine atarsanız, yalnızca aynı veri türüne sahip olmaları gerekmez, bellekte aynı sınıf örneğine işaret ederler.  
  
 Sınıflar hakkında daha fazla bilgi için bkz. [nesneler ve sınıflar](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Başlangıç Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Visual Basic genel türler](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Değer Türleri ve Başvuru Türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Visual Basic dönüşümler yazın](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Yapılar](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Veri Türü Sorunlarını Giderme](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Nasıl yapılır: Değişkende Birden Fazla Değer Tutma](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)
