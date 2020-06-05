---
title: Bileşik Veri Türleri
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
ms.openlocfilehash: 3e8df5ccfeca4bc0a19237ba6d59e9d0747080ea
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84394304"
---
# <a name="composite-data-types-visual-basic"></a>Bileşik Veri Türleri (Visual Basic)
Visual Basic tedariklerini temel veri türlerine ek olarak, yapılar, diziler ve sınıflar gibi *bileşik veri türleri* oluşturmak için farklı türlerdeki öğeleri de birleştirebilirsiniz. Birleşik veri türlerini temel türler ve diğer bileşik türlerden oluşturabilirsiniz. Örneğin, bir yapı öğeleri dizisi veya dizi üyeleri olan bir yapı tanımlayabilirsiniz.  
  
## <a name="data-types"></a>Veri Türleri  
 Bileşik tür, bileşenlerinden herhangi birinin veri türünden farklıdır. Örneğin, bir dizi `Integer` öğe `Integer` veri türünde değil.  
  
 Dizi veri türü, normalde öğe türü, parantezler ve gereken virgüller kullanılarak temsil edilir. Örneğin, tek boyutlu bir `String` öğe dizisi olarak temsil edilir `String()` ve iki boyutlu bir `Boolean` öğe dizisi olarak temsil edilir `Boolean(,)` .  
  
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
  
 Önceki örnekte, dizi değişkenleri `arrayA` ve `arrayB` aynı veri türünde olduğu kabul edilir — `Byte()` ancak farklı uzunluklara başlatılsalar bile. Değişkenlerini `arrayB` ve `arrayC` öğe türleri farklı olduğundan aynı türde değil. `arrayC`Ve `arrayD` dereceleri farklı olduğundan, değişkenler aynı türde değil. Değişkenleri `arrayD` ve `arrayE` `Short(,)` öğe türleri aynı olmalıdır, ancak henüz başlatılmamış olsa da, kendi dereceleri ve öğe türleri aynı türde `arrayD` .  
  
 Diziler hakkında daha fazla bilgi için bkz. [diziler](../arrays/index.md).  
  
## <a name="class-types"></a>Sınıf Türleri  
 Tüm sınıflardan oluşan tek bir veri türü yoktur. Bir sınıf başka bir sınıftan devralınabilir olsa da, her biri ayrı bir veri türüdür. Aynı sınıfın birden çok örneği aynı veri türündedir. Bir sınıf örneği değişkenini diğerine atarsanız, yalnızca aynı veri türüne sahip olmaları gerekmez, bellekte aynı sınıf örneğine işaret ederler.  
  
 Sınıflar hakkında daha fazla bilgi için bkz. [nesneler ve sınıflar](../objects-and-classes/index.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri türleri](index.md)
- [Başlangıç Veri Türleri](elementary-data-types.md)
- [Visual Basic genel türler](generic-types.md)
- [Değer Türleri ve Başvuru Türleri](value-types-and-reference-types.md)
- [Visual Basic'de Tür Dönüştürmeleri](type-conversions.md)
- [Yapılar](structures.md)
- [Veri Türü Sorunlarını Giderme](troubleshooting-data-types.md)
- [Nasıl yapılır: Değişkende Birden Fazla Değer Tutma](how-to-hold-more-than-one-value-in-a-variable.md)
