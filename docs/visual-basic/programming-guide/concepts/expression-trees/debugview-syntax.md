---
title: DebugView özelliği (Visual Basic) tarafından kullanılan söz dizimi
description: İfade ağaçları bir dize temsilini üretmek için DebugView özelliği tarafından kullanılan özel bir sözdizimi açıklar
author: zspitz
ms.author: wiwagn
ms.date: 05/22/2019
ms.topic: reference
helpviewer_keywords:
- expression trees
- debugview
ms.openlocfilehash: ae2c75607f7b9cdc40fc5c163ce533f0472ab454
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66689546"
---
# <a name="debugview-syntax"></a>`DebugView` Söz dizimi

`DebugView` Özelliği (yalnızca hata ayıklama sırasında kullanılabilir) ifade ağaçları dize işlenmesini sağlar. Çoğu söz dizimini anlamak oldukça açıktır; özel durumlar aşağıdaki bölümlerde açıklanmıştır.

Her örneğin bir açıklama bloğu içeren ardından `DebugView`.

## <a name="parameterexpression"></a>ParameterExpression

<xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> Değişken adlarının başında bir "$" simgesi ile görüntülenir.

Parametre bir adı yoksa, otomatik olarak oluşturulmuş bir adı gibi atandıktan `$var1` veya `$var2`.

### <a name="examples"></a>Örnekler

```vb
Dim numParam As ParameterExpression = Expression.Parameter(GetType(Integer), "num")
'
'    $num
'

Dim numParam As ParameterExpression = Expression.Parameter(GetType(Integer))
'
'    $var1
'
```

## <a name="constantexpressions"></a>ConstantExpressions

İçin <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> dize, tamsayı değerlerini temsil eden nesneleri ve `null`, sabit değeri görüntülenir.

Bazı sayısal türleri için bir sonek değerine eklenir:

| Tür | Anahtar sözcüğü | Son eki |
|--|--|--|
| <xref:System.UInt32> | [Uınteger](../../../language-reference/data-types/uinteger-data-type.md) | U |
| <xref:System.Int64> | [uzun](../../../language-reference/data-types/long-data-type.md) | L |
| <xref:System.UInt64> | [ULong](../../../language-reference/data-types/ulong-data-type.md) | UL |
| <xref:System.Double> | [çift](../../../language-reference/data-types/double-data-type.md) | D |
| <xref:System.Single> | [Tek](../../../language-reference/data-types/single-data-type.md) | F |
| <xref:System.Decimal> | [Ondalık](../../../language-reference/data-types/decimal-data-type.md) | M |

### <a name="examples"></a>Örnekler

```vb
Dim num as Integer = 10
Dim expr As ConstantExpression = Expression.Constant(num)
'
'    10
'

Dim num As Double = 10
Dim expr As ConstantExpression = Expression.Constant(num)
'
'    10D
'
```

## <a name="blockexpression"></a>BlockExpression

Varsa türünü bir <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> bloğundaki son ifadenin türü nesne farklıdır, açılı ayraçlar içinde türü görüntülenir (`<` ve `>`). Aksi halde, türünü <xref:System.Linq.Expressions.BlockExpression> nesne görüntülenmez.

### <a name="examples"></a>Örnekler

```vb
Dim block As BlockExpression = Expression.Block(Expression.Constant("test"))
'
'    .Block() {
'        "test"
'    }
'

Dim block As BlockExpression = Expression.Block(
    GetType(Object),
    Expression.Constant("test")
)
'
'    .Block<System.Object>() {
'        "test"
'    }
'
```

## <a name="lambdaexpression"></a>LambdaExpression

<xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> nesneler, temsilci türleri ile birlikte görüntülenir.

Bir lambda ifadesi bir adı yoksa, otomatik olarak oluşturulmuş bir adı gibi atandıktan `#Lambda1` veya `#Lambda2`.

### <a name="examples"></a>Örnekler

```vb
Dim lambda As LambdaExpression = Expression.Lambda(Of Func(Of Integer))(
    Expression.Constant(1)
)
'
'    .Lambda #Lambda1<System.Func'1[System.Int32]>() {
'        1
'    }
'

Dim lambda As LambdaExpression = Expression.Lambda(Of Func(Of Integer))(
    Expression.Constant(1),
    "SampleLambda",
    Nothing
)
'
'    .Lambda #SampleLambda<System.Func'1[System.Int32]>() {
'        1
'    }
'
```

## <a name="labelexpression"></a>LabelExpression

İçin varsayılan bir değer belirtirseniz <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType> nesnesi, bu değer, önce görüntülenir <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType> nesne.

`.Label` Belirteci etiketi başlangıcını gösterir. `.LabelTarget` Belirteci atlamak için hedef hedefinin gösterir.

Bir etiket bir ad yoksa otomatik olarak oluşturulmuş bir adı gibi atandıktan `#Label1` veya `#Label2`.

### <a name="examples"></a>Örnekler

```vb
Dim target As LabelTarget = Expression.Label(GetType(Integer), "SampleLabel")
Dim label1 As BlockExpression = Expression.Block(
    Expression.Goto(target, Expression.Constant(0)),
    Expression.Label(target, Expression.Constant(-1))
)
'
'    .Block() {
'        .Goto SampleLabel { 0 };
'        .Label
'            -1
'        .LabelTarget SampleLabel:
'    }
'

Dim target As LabelTarget = Expression.Label()
Dim block As BlockExpression = Expression.Block(
    Expression.Goto(target),
    Expression.Label(target)
)
'
'    .Block() {
'        .Goto #Label1 { };
'        .Label
'        .LabelTarget #Label1:
'    }
'
```

## <a name="checked-operators"></a>İşaretli işleçleri

İşaretli işleçleri ile görüntülenir `#` işleci önünde simge. Örneğin, işaretli Toplama işleci olarak görüntülenir `#+`.

### <a name="examples"></a>Örnekler

```vb
Dim expr As Expression = Expression.AddChecked(
    Expression.Constant(1),
    Expression.Constant(2)
)
'
'     1 #+ 2
'

Dim expr As Expression = Expression.ConvertChecked(
    Expression.Constant(10.0),
    GetType(Integer)
)
'
'    #(System.Int32)10D
'
```
