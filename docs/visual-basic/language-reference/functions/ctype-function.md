---
title: CType İşlevi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.CType
helpviewer_keywords:
- expression conversion results
- explicit data type conversions [Visual Basic]
- CType function
- conversions [Visual Basic], expression
ms.assetid: dd4b29e7-6fa1-428c-877e-69955420bb72
ms.openlocfilehash: 4a0391b0a5d76f36803b433369d4832c02b05e09
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592106"
---
# <a name="ctype-function-visual-basic"></a>CType İşlevi (Visual Basic)

Bir ifadeyi belirtilen veri türüne, nesneye, yapıya, sınıfa veya arabirime açıkça dönüştürmenin sonucunu döndürür.

## <a name="syntax"></a>Sözdizimi

```vb
CType(expression, typename)
```

## <a name="parts"></a>Bölümler

`expression` geçerli bir ifade. @No__t-0 değeri `typename` tarafından izin verilen aralığın dışındaysa Visual Basic bir özel durum oluşturur.

`typename` bir `Dim` deyimindeki bir `As` yan tümcesi içinde geçerli olan herhangi bir ifade, diğer bir deyişle, herhangi bir veri türü, nesne, yapı, sınıf veya arabirimin adı.

## <a name="remarks"></a>Açıklamalar

> [!TIP]
> Bir tür dönüştürmesi gerçekleştirmek için aşağıdaki işlevleri de kullanabilirsiniz:
>
> - Belirli bir veri türüne dönüştürme gerçekleştiren `CByte`, `CDbl` ve `CInt` gibi tür dönüştürme işlevleri. Daha fazla bilgi için bkz. [tür dönüştürme işlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md).
> - [DirectCast İşleci](../../../visual-basic/language-reference/operators/directcast-operator.md) veya [TryCast İşleci](../../../visual-basic/language-reference/operators/trycast-operator.md). Bu işleçler, bir türün diğer türden devralmasını veya uygulamayı gerektirir. @No__t-1 veri türüne dönüştürülürken `CType` ' dan daha iyi bir performans sağlayabilir.

`CType`, satır içi olarak derlenir, bu da dönüştürme kodunun ifadeyi değerlendiren kodun bir parçası olduğu anlamına gelir. Bazı durumlarda, dönüştürme işlemini gerçekleştirmek için hiçbir yordam çağrılmadığından kod daha hızlı çalışır.

@No__t-0 ' dan `typename` ' e (örneğin, `Integer` ' ye `Date`) bir dönüştürme tanımlanmazsa, Visual Basic bir derleme zamanı hata iletisi görüntüler.

Çalışma zamanında bir dönüştürme başarısız olursa, uygun özel durum oluşturulur. Daraltma dönüştürmesi başarısız olursa, en sık kullanılan sonuç <xref:System.OverflowException> ' dır. Dönüştürme tanımlanmamışsa, <xref:System.InvalidCastException> oluşturulur. Örneğin, `expression` `Object` türünde ise ve çalışma zamanı türünün `typename` ' ye dönüştürülmesine sahip olması durumunda bu durum oluşabilir.

@No__t-0 veya `typename` ' in veri türü tanımladığınız bir sınıf veya yapı ise, bu sınıf veya yapıda `CType` ' i dönüştürme işleci olarak tanımlayabilirsiniz. Bu, `CType` ' ın *aşırı yüklenmiş bir operatör*olarak çalışmasını sağlar. Bunu yaparsanız, oluşturulabilecek özel durumlar da dahil olmak üzere sınıfınıza veya yapınızı dönüştürme davranışını kontrol edebilirsiniz.

## <a name="overloading"></a>Aşırı Yükleme

@No__t-0 işleci, kodunuzun dışında tanımlanan bir sınıf veya yapı üzerinde de aşırı yüklenebilir. Kodunuz bu tür bir sınıfa veya yapıya dönüştürürse, `CType` işlecinin davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).

## <a name="converting-dynamic-objects"></a>Dinamik nesneleri dönüştürme

Dinamik nesnelerin tür dönüştürmeleri, <xref:System.Dynamic.DynamicObject.TryConvert%2A> veya <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> yöntemlerini kullanan kullanıcı tanımlı dinamik dönüştürmeler tarafından gerçekleştirilir. Dinamik nesnelerle çalışıyorsanız, dinamik nesneyi dönüştürmek için <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> yöntemini kullanın.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir ifadeyi `Single` veri türüne dönüştürmek için `CType` işlevini kullanır.

[!code-vb[VbVbalrFunctions#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#24)]

Daha fazla örnek için bkz. [örtük ve açık dönüştürmeler](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.OverflowException>
- <xref:System.InvalidCastException>
- [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/conversion-functions.md)
- [Operator Deyimi](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Nasıl yapılır: Dönüştürme Işleci tanımlama @ no__t-0
- [.NET Framework dönüştürme türü](../../../standard/base-types/type-conversion.md)
