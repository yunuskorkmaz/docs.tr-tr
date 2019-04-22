---
title: Örtük ve Açık Dönüştürmeler (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [Visual Basic], type
- variables [Visual Basic], changing data type
- casting
- conversions [Visual Basic], data type
- type conversion [Visual Basic], implicit conversions
- CType function [Visual Basic], conversions
- casting, data types
- data type conversion [Visual Basic], explicit
- type conversion [Visual Basic], explicit conversions
- data types [Visual Basic], casting
- conversions [Visual Basic], implicit
- explicit data type conversions [Visual Basic]
- conversions [Visual Basic]
- changing data types [Visual Basic]
- conversions [Visual Basic], explicit
- data type conversion [Visual Basic], implicit
- implicit data type conversions [Visual Basic]
ms.assetid: 77de1659-af8a-492c-967e-e7ef60ccce66
ms.openlocfilehash: 82ff710629089cd14c7e982b4afa4301d0790811
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834003"
---
# <a name="implicit-and-explicit-conversions-visual-basic"></a>Örtük ve Açık Dönüştürmeler (Visual Basic)
Bir *örtük dönüştürme* kaynak kodunda özel bir sözdizimi gerektirmez. Aşağıdaki örnekte, Visual Basic değeri örtük olarak dönüştürür `k` giderek önce bir tek duyarlıklı kayan nokta değerine `q`.  
  
```  
Dim k As Integer  
Dim q As Double  
' Integer widens to Double, so you can do this with Option Strict On.  
k = 432  
q = k  
```  
  
 Bir *açık dönüştürme* bir tür dönüştürme anahtar sözcüğünü kullanır. Visual Basic, istenen veri türüne parantez içinde bir ifade coerce birkaç tür anahtar sözcükler sağlar. Bu anahtar sözcükler işlevleri gibi davranır, ancak yürütme bir işlev çağrısıyla biraz daha hızlıdır, bu nedenle, derleyici satır içi kod oluşturur.  
  
 Önceki örnekte, aşağıdaki uzantısına `CInt` anahtar sözcüğü değerini dönüştürür `q` geri giderek önce tamsayı `k`.  
  
```  
' q had been assigned the value 432 from k.  
q = Math.Sqrt(q)  
k = CInt(q)  
' k now has the value 21 (rounded square root of 432).  
```  
  
## <a name="conversion-keywords"></a>Dönüşüm Anahtar Sözcükleri  
 Aşağıdaki tabloda kullanılabilir dönüşüm anahtar sözcükleri gösterilmektedir.  
  
|Tür dönüştürme anahtar sözcüğü|Bir ifadenin veri türüne dönüştürür.|Dönüştürülecek ifade izin verilen veri türleri|  
|---|---|---|  
|`CBool`|[Boolean Veri Türü](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)|Herhangi bir sayısal tür (dahil olmak üzere `Byte`, `SByte`ve numaralandırılan türleri), `String`, `Object`|  
|`CByte`|[Byte Veri Türü](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|Herhangi bir sayısal tür (dahil olmak üzere `SByte` ve numaralandırılan türleri), `Boolean`, `String`, `Object`|  
|`CChar`|[Char Veri Türü](../../../../visual-basic/language-reference/data-types/char-data-type.md)|`String`, `Object`|  
|`CDate`|[Date Veri Türü](../../../../visual-basic/language-reference/data-types/date-data-type.md)|`String`, `Object`|  
|`CDbl`|[Double Veri Türü](../../../../visual-basic/language-reference/data-types/double-data-type.md)|Herhangi bir sayısal tür (dahil olmak üzere `Byte`, `SByte`ve numaralandırılan türleri), `Boolean`, `String`, `Object`|  
|`CDec`|[Decimal Veri Türü](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|Herhangi bir sayısal tür (dahil olmak üzere `Byte`, `SByte`ve numaralandırılan türleri), `Boolean`, `String`, `Object`|  
|`CInt`|[Integer Veri Türü](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|Herhangi bir sayısal tür (dahil olmak üzere `Byte`, `SByte`ve numaralandırılan türleri), `Boolean`, `String`, `Object`|  
|`CLng`|[Long Veri Türü](../../../../visual-basic/language-reference/data-types/long-data-type.md)|Herhangi bir sayısal tür (dahil olmak üzere `Byte`, `SByte`ve numaralandırılan türleri), `Boolean`, `String`, `Object`|  
|`CObj`|[Object Veri Türü](../../../../visual-basic/language-reference/data-types/object-data-type.md)|Herhangi bir türü|  
|`CSByte`|[SByte Veri Türü](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|Herhangi bir sayısal tür (dahil olmak üzere `Byte` ve numaralandırılan türleri), `Boolean`, `String`, `Object`|  
|`CShort`|[Short Veri Türü](../../../../visual-basic/language-reference/data-types/short-data-type.md)|Herhangi bir sayısal tür (dahil olmak üzere `Byte`, `SByte`ve numaralandırılan türleri), `Boolean`, `String`, `Object`|  
|`CSng`|[Single Veri Türü](../../../../visual-basic/language-reference/data-types/single-data-type.md)|Herhangi bir sayısal tür (dahil olmak üzere `Byte`, `SByte`ve numaralandırılan türleri), `Boolean`, `String`, `Object`|  
|`CStr`|[String Veri Türü](../../../../visual-basic/language-reference/data-types/string-data-type.md)|Herhangi bir sayısal tür (dahil olmak üzere `Byte`, `SByte`ve numaralandırılan türleri), `Boolean`, `Char`, `Char` dizi `Date`, `Object`|  
|`CType`|Belirtilen tür virgülün (`,`)|Dönüştürülürken bir *başlangıç veri türü* (bir basit türü bir dizi dahil), aynı karşılık gelen dönüştürme anahtar sözcüğü için izin verilen türleri<br /><br /> Dönüştürülürken bir *bileşik veri türü*, bunu uyguladığı arayüzlerin ve devraldığı sınıfları<br /><br /> Bir sınıf veya yapı için üzerinde aşırı dönüştürülürken `CType`, bu sınıf ya da yapı|  
|`CUInt`|[UInteger Veri Türü](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|Herhangi bir sayısal tür (dahil olmak üzere `Byte`, `SByte`ve numaralandırılan türleri), `Boolean`, `String`, `Object`|  
|`CULng`|[ULong Veri Türü](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|Herhangi bir sayısal tür (dahil olmak üzere `Byte`, `SByte`ve numaralandırılan türleri), `Boolean`, `String`, `Object`|  
|`CUShort`|[UShort Veri Türü](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|Herhangi bir sayısal tür (dahil olmak üzere `Byte`, `SByte`ve numaralandırılan türleri), `Boolean`, `String`, `Object`|  
  
## <a name="the-ctype-function"></a>CType işlevi  
 [CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md) iki bağımsız değişken üzerinde çalışır. Birincisi dönüştürülecek ifade ve hedef veri türü veya nesne sınıfı saniyedir. İlk bağımsız değişkeni bir tür değil bir ifade olması gerektiğini unutmayın.  
  
 `CType` olan bir *satır içi işlev*derlenmiş kodunu anlamı yapar dönüştürme, genellikle bir işlev oluşturmadan çağırın. Bu, performansı geliştirir.  
  
 Bir karşılaştırması `CType` diğer tür dönüşüm anahtar sözcükleri ile bkz: [DirectCast işleci](../../../../visual-basic/language-reference/operators/directcast-operator.md) ve [TryCast işleci](../../../../visual-basic/language-reference/operators/trycast-operator.md).  
  
### <a name="elementary-types"></a>Basit türler  
 Aşağıdaki örnek, kullanımını gösterir `CType`.  
  
```  
k = CType(q, Integer)  
' The following statement coerces w to the specific object class Label.  
f = CType(w, Label)  
```  
  
### <a name="composite-types"></a>Bileşik türler  
 Kullanabileceğiniz `CType` bileşik veri türleri de basit türler için farklı değerler dönüştürmek için. Coerce aşağıdaki örnekteki gibi arabirimlerinden birini türde bir nesne sınıfı için de kullanabilirsiniz.  
  
```  
' Assume class cZone implements interface iZone.  
Dim h As Object  
' The first argument to CType must be an expression, not a type.  
Dim cZ As cZone  
' The following statement coerces a cZone object to its interface iZone.  
h = CType(cZ, iZone)  
```  
  
### <a name="array-types"></a>Dizi türleri  
 `CType` Aşağıdaki örnekte gösterildiği gibi dizi veri türleri de dönüştürebilirsiniz.  
  
```  
Dim v() As classV  
Dim obArray() As Object  
' Assume some object array has been assigned to obArray.  
' Check for run-time type compatibility.  
If TypeOf obArray Is classV()  
    ' obArray can be converted to classV.  
    v = CType(obArray, classV())  
End If  
```  
  
 Daha fazla bilgi ve örnek için bkz. [dizi dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md).  
  
### <a name="types-defining-ctype"></a>CType tanımlama türleri  
 Tanımlayabileceğiniz `CType` bir sınıf veya yapı tanımladığınız üzerinde. Bu sınıf veya yapı türünü gelen ve değerleri dönüştürmenize olanak sağlar. Daha fazla bilgi ve örnek için bkz. [nasıl yapılır: Bir dönüşüm işleci tanımlama](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
> [!NOTE]
>  Bir hata meydana gelir veya bir dönüştürme anahtar sözcüğü ile kullanılan değerleri hedef veri türü için geçerli olmalıdır. Örneğin, dönüştürmeyi denediğinizde bir `Long` için bir `Integer`, değerini `Long` geçerli aralığında olmalıdır `Integer` veri türü.  
  
> [!CAUTION]
>  Belirtme `CType` kaynak türü hedef türünden türetilmemiş bir sınıf türünden başka bir başarısız çalışma zamanında için dönüştürülecek. Böyle bir hata oluşturur bir <xref:System.InvalidCastException> özel durum.  
  
 Ancak, türlerinden bir yapı ya da tanımladığınız sınıf varsa ve tanımladığınız `CType` gereksinimlerini karşılıyorsa, yapı veya sınıf üzerinde bir dönüştürme başarılı olabilmesi için `CType`. Bkz: [nasıl yapılır: Bir dönüşüm işleci tanımlama](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
 Açık bir dönüştürme gerçekleştirmek olan olarak da bilinen *atama* belirtilen veri türü veya nesne sınıfı için bir ifade.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de tür dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Dizeler ve Diğer Türler Arasında Dönüştürmeler](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [Nasıl yapılır: Bir nesneyi Visual Basic'de başka bir türe dönüştürme](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [Yapılar](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Veri Türleri](../../../../visual-basic/language-reference/data-types/index.md)
- [Tür Dönüştürme İşlevleri](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Veri Türü Sorunlarını Giderme](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
