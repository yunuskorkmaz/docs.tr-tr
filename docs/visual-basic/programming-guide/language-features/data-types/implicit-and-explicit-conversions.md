---
title: Örtük ve Açık Dönüştürmeler
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
ms.openlocfilehash: 2858dafd2531bd846ad89672348d103f385c4511
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393837"
---
# <a name="implicit-and-explicit-conversions-visual-basic"></a>Örtük ve Açık Dönüştürmeler (Visual Basic)

*Örtük dönüştürme* , kaynak kodunda özel bir sözdizimi gerektirmez. Aşağıdaki örnekte, Visual Basic değerini ' a atamadan önce, değeri örtük olarak `k` tek duyarlıklı kayan noktalı değere dönüştürür `q` .

```vb
Dim k As Integer
Dim q As Double
' Integer widens to Double, so you can do this with Option Strict On.
k = 432
q = k
```

*Açık dönüştürme* bir tür dönüştürme anahtar sözcüğü kullanır. Visual Basic, parantez içindeki bir ifadeyi istenen veri türüne döndüren birkaç anahtar sözcük sağlar. Bu anahtar sözcükler işlevler gibi davranır ancak derleyici, kodu satır içi olarak oluşturur, böylece yürütme bir işlev çağrısıyla biraz daha hızlıdır.

Önceki örneğin aşağıdaki uzantısında, `CInt` anahtar sözcüğü `q` öğesine atamadan önce değeri bir tamsayıya dönüştürür `k` .

```vb
' q had been assigned the value 432 from k.
q = Math.Sqrt(q)
k = CInt(q)
' k now has the value 21 (rounded square root of 432).
```

## <a name="conversion-keywords"></a>Dönüşüm Anahtar Sözcükleri

Aşağıdaki tabloda kullanılabilir dönüştürme anahtar sözcükleri gösterilmektedir.

|Tür dönüştürme anahtar sözcüğü|Bir ifadeyi veri türüne dönüştürür|Dönüştürülecek ifadenin izin verilen veri türleri|
|---|---|---|
|`CBool`|[Boolean Veri Türü](../../../language-reference/data-types/boolean-data-type.md)|Herhangi bir sayısal tür ( `Byte` , `SByte` ve numaralandırılmış türler dahil), `String` ,`Object`|
|`CByte`|[Byte Veri Türü](../../../language-reference/data-types/byte-data-type.md)|Herhangi bir sayısal tür ( `SByte` ve numaralandırılmış türler dahil),, `Boolean` `String` ,`Object`|
|`CChar`|[Char Veri Türü](../../../language-reference/data-types/char-data-type.md)|`String`, `Object`|
|`CDate`|[Date Veri Türü](../../../language-reference/data-types/date-data-type.md)|`String`, `Object`|
|`CDbl`|[Double Veri Türü](../../../language-reference/data-types/double-data-type.md)|Herhangi bir sayısal tür ( `Byte` , `SByte` ve numaralandırılmış türler dahil), `Boolean` , `String` ,`Object`|
|`CDec`|[Decimal Veri Türü](../../../language-reference/data-types/decimal-data-type.md)|Herhangi bir sayısal tür ( `Byte` , `SByte` ve numaralandırılmış türler dahil), `Boolean` , `String` ,`Object`|
|`CInt`|[Integer Veri Türü](../../../language-reference/data-types/integer-data-type.md)|Herhangi bir sayısal tür ( `Byte` , `SByte` ve numaralandırılmış türler dahil), `Boolean` , `String` ,`Object`|
|`CLng`|[Long Veri Türü](../../../language-reference/data-types/long-data-type.md)|Herhangi bir sayısal tür ( `Byte` , `SByte` ve numaralandırılmış türler dahil), `Boolean` , `String` ,`Object`|
|`CObj`|[Nesne Veri Türü](../../../language-reference/data-types/object-data-type.md)|Herhangi bir tür|
|`CSByte`|[SByte Veri Türü](../../../language-reference/data-types/sbyte-data-type.md)|Herhangi bir sayısal tür ( `Byte` ve numaralandırılmış türler dahil),, `Boolean` `String` ,`Object`|
|`CShort`|[Short Veri Türü](../../../language-reference/data-types/short-data-type.md)|Herhangi bir sayısal tür ( `Byte` , `SByte` ve numaralandırılmış türler dahil), `Boolean` , `String` ,`Object`|
|`CSng`|[Single Veri Türü](../../../language-reference/data-types/single-data-type.md)|Herhangi bir sayısal tür ( `Byte` , `SByte` ve numaralandırılmış türler dahil), `Boolean` , `String` ,`Object`|
|`CStr`|[Dize Veri Türü](../../../language-reference/data-types/string-data-type.md)|Herhangi bir sayısal tür ( `Byte` , `SByte` ve numaralandırılmış türler dahil), `Boolean` , `Char` , `Char` dizi, `Date` ,`Object`|
|`CType`|Virgül () sonrasında belirtilen tür `,`|Bir *Öğesel veri türüne* dönüştürme sırasında (bir öğesel türün dizisi dahil), karşılık gelen dönüştürme anahtar sözcüğü için izin verilen türler<br /><br /> *Bileşik veri türüne*dönüştürme yaparken, uyguladığı arabirimler ve devraldığı sınıflar<br /><br /> Daha fazla yüklü olan bir sınıfa veya yapıya dönüştürme sırasında `CType` , bu sınıf veya yapı|
|`CUInt`|[UInteger Veri Türü](../../../language-reference/data-types/uinteger-data-type.md)|Herhangi bir sayısal tür ( `Byte` , `SByte` ve numaralandırılmış türler dahil), `Boolean` , `String` ,`Object`|
|`CULng`|[ULong Veri Türü](../../../language-reference/data-types/ulong-data-type.md)|Herhangi bir sayısal tür ( `Byte` , `SByte` ve numaralandırılmış türler dahil), `Boolean` , `String` ,`Object`|
|`CUShort`|[UShort Veri Türü](../../../language-reference/data-types/ushort-data-type.md)|Herhangi bir sayısal tür ( `Byte` , `SByte` ve numaralandırılmış türler dahil), `Boolean` , `String` ,`Object`|

## <a name="the-ctype-function"></a>CType Işlevi

[CType işlevi](../../../language-reference/functions/ctype-function.md) iki bağımsız değişken üzerinde çalışır. İlki dönüştürülecek ifade, ikincisi ise hedef veri türü veya nesne sınıfıdır. İlk bağımsız değişkenin bir tür değil bir ifade olması gerektiğini unutmayın.

`CType`, bir *satır içi işlevdir*, yani derlenmiş kod, genellikle bir işlev çağrısı oluşturmadan dönüştürmeyi yapar. Bu, performansı geliştirir.

`CType`Diğer tür dönüştürme anahtar sözcükleriyle bir karşılaştırması için bkz. [DirectCast Işleci](../../../language-reference/operators/directcast-operator.md) ve [TryCast İşleci](../../../language-reference/operators/trycast-operator.md).

### <a name="elementary-types"></a>Elemensel türler

Aşağıdaki örnek öğesinin kullanımını gösterir `CType` .

```vb
k = CType(q, Integer)
' The following statement coerces w to the specific object class Label.
f = CType(w, Label)
```

### <a name="composite-types"></a>Bileşik türler

`CType`Değerleri bileşik veri türlerine ve öğesel türlere dönüştürmek için ' i kullanabilirsiniz. Ayrıca, aşağıdaki örnekte olduğu gibi, bir nesne sınıfını arabirimlerinden biri türüne zorlamak için de kullanabilirsiniz.

```vb
' Assume class cZone implements interface iZone.
Dim h As Object
' The first argument to CType must be an expression, not a type.
Dim cZ As cZone
' The following statement coerces a cZone object to its interface iZone.
h = CType(cZ, iZone)
```

### <a name="array-types"></a>Dizi türleri

`CType`, aşağıdaki örnekte olduğu gibi dizi veri türlerini de dönüştürebilir.

```vb
Dim v() As classV
Dim obArray() As Object
' Assume some object array has been assigned to obArray.
' Check for run-time type compatibility.
If TypeOf obArray Is classV()
    ' obArray can be converted to classV.
    v = CType(obArray, classV())
End If
```

Daha fazla bilgi ve bir örnek için bkz. [dizi dönüştürmeleri](array-conversions.md).

### <a name="types-defining-ctype"></a>CType tanımlayan türler

`CType`Tanımladığınız bir sınıf veya yapı üzerinde tanımlayabilirsiniz. Bu, değerleri sınıfınızın veya yapınızın türüne ve türünden dönüştürmenizi sağlar. Daha fazla bilgi ve bir örnek için bkz. [nasıl yapılır: dönüştürme Işleci tanımlama](../procedures/how-to-define-a-conversion-operator.md).

> [!NOTE]
> Bir dönüştürme anahtar sözcüğüyle kullanılan değerlerin hedef veri türü için geçerli olması gerekir veya bir hata oluşur. Örneğin, bir ' a dönüştürmeye çalışırsanız, `Long` `Integer` değeri `Long` veri türü için geçerli aralık dahilinde olmalıdır `Integer` .

> [!CAUTION]
> `CType`Kaynak türü hedef türünden türemezse, çalışma zamanında bir sınıf türünden diğerine dönüştürme yapmak için belirtme. Bu tür bir hata <xref:System.InvalidCastException> özel durum oluşturur.

Ancak, türlerden biri tanımladığınız bir yapı veya sınıf ise ve `CType` Bu yapıda veya sınıfta tanımladıysanız, bir dönüştürme işlemi, gereksinimlerinizi karşılıyorsa başarılı olabilir `CType` . Bkz. [nasıl yapılır: dönüştürme Işleci tanımlama](../procedures/how-to-define-a-conversion-operator.md).

Açık bir dönüştürme gerçekleştirmek, belirli bir veri türüne veya nesne sınıfına bir ifade *atama* olarak da bilinir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de Tür Dönüştürmeleri](type-conversions.md)
- [Dizeler ve Diğer Türler Arasında Dönüştürmeler](conversions-between-strings-and-other-types.md)
- [Nasıl yapılır: Visual Basic'te Bir Nesneyi Başka Bir Türe Dönüştürme](how-to-convert-an-object-to-another-type.md)
- [Yapılar](structures.md)
- [Veri türleri](../../../language-reference/data-types/index.md)
- [Tür Dönüştürme İşlevleri](../../../language-reference/functions/type-conversion-functions.md)
- [Veri Türü Sorunlarını Giderme](troubleshooting-data-types.md)
