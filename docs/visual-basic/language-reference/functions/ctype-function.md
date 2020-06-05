---
title: CType İşlevi
ms.date: 07/20/2015
f1_keywords:
- vb.CType
helpviewer_keywords:
- expression conversion results
- explicit data type conversions [Visual Basic]
- CType function
- conversions [Visual Basic], expression
ms.assetid: dd4b29e7-6fa1-428c-877e-69955420bb72
ms.openlocfilehash: 88d609146648fe1b0c3124b99a65e85293fc0707
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406436"
---
# <a name="ctype-function-visual-basic"></a>CType İşlevi (Visual Basic)

Bir ifadeyi belirtilen veri türüne, nesneye, yapıya, sınıfa veya arabirime açıkça dönüştürmenin sonucunu döndürür.

## <a name="syntax"></a>Sözdizimi

```vb
CType(expression, typename)
```

## <a name="parts"></a>Bölümler

`expression`Herhangi bir geçerli ifade. Değeri `expression` tarafından izin verilen aralığın dışındaysa `typename` Visual Basic bir özel durum oluşturur.

`typename`Deyimdeki bir yan tümce içinde geçerli olan herhangi bir ifade `As` `Dim` , diğer bir deyişle, herhangi bir veri türü, nesne, yapı, sınıf veya arabirimin adı.

## <a name="remarks"></a>Açıklamalar

> [!TIP]
> Bir tür dönüştürmesi gerçekleştirmek için aşağıdaki işlevleri de kullanabilirsiniz:
>
> - `CByte` `CDbl` `CInt` Belirli bir veri türüne dönüştürme gerçekleştiren, ve gibi tür dönüştürme işlevleri. Daha fazla bilgi için bkz. [tür dönüştürme işlevleri](type-conversion-functions.md).
> - [DirectCast İşleci](../operators/directcast-operator.md) veya [TryCast İşleci](../operators/trycast-operator.md). Bu işleçler, bir türün diğer türden devralmasını veya uygulamayı gerektirir. `CType`Veri türüne dönüştürme işleminden daha iyi bir performans sağlayabilir `Object` .

`CType`satır içi olarak derlenir, bu da dönüştürme kodunun ifadeyi değerlendiren kodun bir parçası olduğu anlamına gelir. Bazı durumlarda, dönüştürme işlemini gerçekleştirmek için hiçbir yordam çağrılmadığından kod daha hızlı çalışır.

' Den `expression` `typename` ' e (örneğin, öğesinden) hiçbir dönüştürme tanımlanmazsa `Integer` `Date` , Visual Basic bir derleme zamanı hata iletisi görüntüler.

Çalışma zamanında bir dönüştürme başarısız olursa, uygun özel durum oluşturulur. Daraltma dönüştürmesi başarısız olursa, <xref:System.OverflowException> en sık görülen sonuç olur. Dönüştürme tanımsızdır, bir <xref:System.InvalidCastException> içinde atılır. Örneğin, bu durum, `expression` türü ise `Object` ve çalışma zamanı türünün öğesine dönüştürülmesine sahip olması durumunda gerçekleşebilir `typename` .

Veri türü `expression` veya `typename` tanımladığınız bir sınıf veya yapı ise, `CType` Bu sınıf veya yapı üzerinde bir dönüştürme işleci olarak tanımlayabilirsiniz. Bu, `CType` *aşırı yüklenmiş bir operatör*olarak görev yapar. Bunu yaparsanız, oluşturulabilecek özel durumlar da dahil olmak üzere sınıfınıza veya yapınızı dönüştürme davranışını kontrol edebilirsiniz.

## <a name="overloading"></a>Aşırı Yükleme

`CType`İşleci, kodunuzun dışında tanımlanan bir sınıf veya yapı üzerinde de aşırı yüklenebilir. Kodunuz bu tür bir sınıfa veya yapıya dönüştürürse, işlecinin davranışını anladığınızdan emin olun `CType` . Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).

## <a name="converting-dynamic-objects"></a>Dinamik nesneleri dönüştürme

Dinamik nesnelerin tür dönüştürmeleri, veya yöntemlerini kullanan kullanıcı tanımlı dinamik dönüştürmeler tarafından gerçekleştirilir <xref:System.Dynamic.DynamicObject.TryConvert%2A> <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> . Dinamik nesnelerle çalışıyorsanız, <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> dinamik nesneyi dönüştürmek için yöntemini kullanın.

## <a name="example"></a>Örnek

Aşağıdaki örnek, `CType` bir ifadeyi veri türüne dönüştürmek için işlevini kullanır `Single` .

[!code-vb[VbVbalrFunctions#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#24)]

Daha fazla örnek için bkz. [örtük ve açık dönüştürmeler](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.OverflowException>
- <xref:System.InvalidCastException>
- [Tür Dönüştürme İşlevleri](type-conversion-functions.md)
- [Dönüşüm İşlevleri](conversion-functions.md)
- [Operator Deyimi](../statements/operator-statement.md)
- [Nasıl yapılır: Dönüştürme İşleci Tanımlama](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [.NET Framework'te Tür Dönüştürme](../../../standard/base-types/type-conversion.md)
