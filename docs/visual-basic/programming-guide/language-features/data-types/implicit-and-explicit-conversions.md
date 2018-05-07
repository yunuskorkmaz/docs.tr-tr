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
ms.openlocfilehash: 8a0909641b653a1800bdf3f50ec1dfe993411824
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="implicit-and-explicit-conversions-visual-basic"></a>Örtük ve Açık Dönüştürmeler (Visual Basic)
Bir *örtük dönüşüm* kaynak kodda özel bir sözdizimi gerektirmez. Aşağıdaki örnekte, Visual Basic örtük olarak değerini dönüştürür `k` atanarak önce bir tek duyarlıklı kayan noktalı değeri `q`.  
  
```  
Dim k As Integer  
Dim q As Double  
' Integer widens to Double, so you can do this with Option Strict On.  
k = 432  
q = k  
```  
  
 Bir *açık dönüşüm* bir tür dönüştürme anahtar kullanır. Visual Basic istenen veri türüne parantez içindeki ifadenin coerce birkaç gibi anahtar sözcükler sağlar. Bu anahtar sözcükler işlevleri gibi davranır ancak yürütme bir işlev çağrısı ile biraz daha hızlı olacak şekilde kodu satır içi derleyici üretir.  
  
 Önceki örnekte, aşağıdaki uzantısına `CInt` anahtar sözcüğü değerine dönüştürür `q` atanarak önce geri tamsayıya `k`.  
  
```  
' q had been assigned the value 432 from k.  
q = Math.Sqrt(q)  
k = CInt(q)  
' k now has the value 21 (rounded square root of 432).  
```  
  
## <a name="conversion-keywords"></a>Dönüşüm Anahtar Sözcükleri  
 Aşağıdaki tabloda kullanılabilir dönüşüm anahtar sözcükleri gösterir.  
  
|Tür dönüştürme anahtar sözcüğü|Bir ifade veri türüne dönüştürür|Dönüştürülecek ifade izin verilen veri türleri|  
|---|---|---|  
|`CBool`|[Boolean Veri Türü](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)|Herhangi bir sayısal tür (de dahil olmak üzere `Byte`, `SByte`ve türleri numaralandırılan), `String`, `Object`|  
|`CByte`|[Byte Veri Türü](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|Herhangi bir sayısal tür (de dahil olmak üzere `SByte` ve türleri numaralandırılan), `Boolean`, `String`, `Object`|  
|`CChar`|[Char Veri Türü](../../../../visual-basic/language-reference/data-types/char-data-type.md)|`String`, `Object`|  
|`CDate`|[Date Veri Türü](../../../../visual-basic/language-reference/data-types/date-data-type.md)|`String`, `Object`|  
|`CDbl`|[Double Veri Türü](../../../../visual-basic/language-reference/data-types/double-data-type.md)|Herhangi bir sayısal tür (de dahil olmak üzere `Byte`, `SByte`ve türleri numaralandırılan), `Boolean`, `String`, `Object`|  
|`CDec`|[Decimal Veri Türü](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|Herhangi bir sayısal tür (de dahil olmak üzere `Byte`, `SByte`ve türleri numaralandırılan), `Boolean`, `String`, `Object`|  
|`CInt`|[Integer Veri Türü](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|Herhangi bir sayısal tür (de dahil olmak üzere `Byte`, `SByte`ve türleri numaralandırılan), `Boolean`, `String`, `Object`|  
|`CLng`|[Long Veri Türü](../../../../visual-basic/language-reference/data-types/long-data-type.md)|Herhangi bir sayısal tür (de dahil olmak üzere `Byte`, `SByte`ve türleri numaralandırılan), `Boolean`, `String`, `Object`|  
|`CObj`|[Object Veri Türü](../../../../visual-basic/language-reference/data-types/object-data-type.md)|Herhangi bir türü|  
|`CSByte`|[SByte Veri Türü](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|Herhangi bir sayısal tür (de dahil olmak üzere `Byte` ve türleri numaralandırılan), `Boolean`, `String`, `Object`|  
|`CShort`|[Short Veri Türü](../../../../visual-basic/language-reference/data-types/short-data-type.md)|Herhangi bir sayısal tür (de dahil olmak üzere `Byte`, `SByte`ve türleri numaralandırılan), `Boolean`, `String`, `Object`|  
|`CSng`|[Single Veri Türü](../../../../visual-basic/language-reference/data-types/single-data-type.md)|Herhangi bir sayısal tür (de dahil olmak üzere `Byte`, `SByte`ve türleri numaralandırılan), `Boolean`, `String`, `Object`|  
|`CStr`|[String Veri Türü](../../../../visual-basic/language-reference/data-types/string-data-type.md)|Herhangi bir sayısal tür (de dahil olmak üzere `Byte`, `SByte`ve türleri numaralandırılan), `Boolean`, `Char`, `Char` diziye `Date`, `Object`|  
|`CType`|Belirtilen tür virgül aşağıdaki (`,`)|Dönüştürülürken bir *başlangıç veri türü* (bir başlangıç türünde bir dizi dahil), aynı karşılık gelen dönüştürme anahtar sözcüğü için izin verilen olarak türleri<br /><br /> Dönüştürülürken bir *bileşik veri türü*, bunu uygulayan arabirimleri ve devraldığı sınıfları<br /><br /> Üzerinde aşırı sınıf veya yapı için dönüştürülürken `CType`, bu sınıf veya yapı|  
|`CUInt`|[UInteger Veri Türü](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|Herhangi bir sayısal tür (de dahil olmak üzere `Byte`, `SByte`ve türleri numaralandırılan), `Boolean`, `String`, `Object`|  
|`CULng`|[ULong Veri Türü](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|Herhangi bir sayısal tür (de dahil olmak üzere `Byte`, `SByte`ve türleri numaralandırılan), `Boolean`, `String`, `Object`|  
|`CUShort`|[UShort Veri Türü](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|Herhangi bir sayısal tür (de dahil olmak üzere `Byte`, `SByte`ve türleri numaralandırılan), `Boolean`, `String`, `Object`|  
  
## <a name="the-ctype-function"></a>CType işlevi  
 [CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md) iki bağımsız değişkenler üzerinde çalışır. İlk dönüştürülecek ifadesidir ve hedef veri türü veya nesne sınıfı saniyedir. İlk bağımsız değişkeni bir türde bir ifade olması gerektiğini unutmayın.  
  
 `CType` olan bir *satır içi işlev*derlenmiş kod anlamı dönüştürme yapar, genellikle bir işlev oluşturmadan çağırın. Bu performansı artırır.  
  
 Bir karşılaştırması `CType` diğer tür dönüşüm anahtar sözcükleri ile bkz: [DirectCast işleci](../../../../visual-basic/language-reference/operators/directcast-operator.md) ve [TryCast işleci](../../../../visual-basic/language-reference/operators/trycast-operator.md).  
  
### <a name="elementary-types"></a>Başlangıç türleri  
 Aşağıdaki örnek kullanımını gösteren `CType`.  
  
```  
k = CType(q, Integer)  
' The following statement coerces w to the specific object class Label.  
f = CType(w, Label)  
```  
  
### <a name="composite-types"></a>Bileşik türler  
 Kullanabileceğiniz `CType` bileşik veri türleri de başlangıç türleri için farklı değerler dönüştürmek için. Aşağıdaki örnekte olduğu gibi arabirimlerinden birini türde bir nesne sınıfının coerce için de kullanabilirsiniz.  
  
```  
' Assume class cZone implements interface iZone.  
Dim h As Object  
' The first argument to CType must be an expression, not a type.  
Dim cZ As cZone  
' The following statement coerces a cZone object to its interface iZone.  
h = CType(cZ, iZone)  
```  
  
### <a name="array-types"></a>Dizi türleri  
 `CType` Ayrıca aşağıdaki örnekte olduğu gibi dizi veri türleri dönüştürebilirsiniz.  
  
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
  
 Daha fazla bilgi ve bir örnek için bkz: [dizi dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md).  
  
### <a name="types-defining-ctype"></a>CType tanımlama türleri  
 Tanımlayabileceğiniz `CType` bir sınıf veya yapı tanımladığınız. Bu sınıf veya yapı türü gelen ve giden değerleri dönüştürmenize olanak sağlar. Daha fazla bilgi ve bir örnek için bkz: [nasıl yapılır: bir dönüşüm işleci tanımlama](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
> [!NOTE]
>  Dönüşüm anahtar sözcüğü ile kullanılan değerleri hedef veri türü için geçerli olmalıdır veya bir hata oluşur. Dönüştürme çalışırsanız, örneğin, bir `Long` için bir `Integer`, değeri `Long` için geçerli aralıkta olmalıdır `Integer` veri türü.  
  
> [!CAUTION]
>  Belirtme `CType` kaynak türü hedef türünden türetilmemiş varsa bir sınıf türünden çalışma zamanında başka bir başarısız dönüştürmek için. Bu tür bir hata oluşturduğunda bir <xref:System.InvalidCastException> özel durum.  
  
 Ancak, türlerinden birini bir yapı veya tanımladığınız sınıfı ise ve tanımladığınız `CType` gereksinimlerini karşılayıp karşılamadığını bu yapısı veya sınıfı, bir dönüştürme başarılı olabilmesi için `CType`. Bkz: [nasıl yapılır: bir dönüşüm işleci tanımlama](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
 Açık bir dönüştürme gerçekleştirmek olduğu olarak da bilinen *atama* verilen veri türü veya nesne sınıfı için bir ifade.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de tür dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Dizeler ve Diğer Türler Arasında Dönüştürmeler](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [Nasıl yapılır: Visual Basic'de başka bir tür nesneyi Dönüştür](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [Yapılar](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Veri Türleri](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Tür Dönüştürme İşlevleri](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Veri Türü Sorunlarını Giderme](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
