---
title: DebugView özelliği tarafından kullanılan sözdizimi
description: İfade ağaçlarının dize gösterimini üretmek için DebugView özelliği tarafından kullanılan özel sözdizimini açıklar
author: zspitz
ms.author: wiwagn
ms.date: 05/22/2019
ms.topic: reference
helpviewer_keywords:
- expression trees
- debugview
ms.openlocfilehash: 98ceba37aa226fab68ae1c1028e2a1139b3b8e7e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346877"
---
# <a name="debugview-syntax"></a>`DebugView` sözdizimi

`DebugView` özelliği (yalnızca hata ayıklama sırasında kullanılabilir), ifade ağaçlarının dize işlemesini sağlar. Sözdiziminin çoğu anlaşılması oldukça basittir; özel durumlar aşağıdaki bölümlerde açıklanmıştır.

Her örnek, `DebugView`içeren bir açıklama bloğu tarafından izlenir.

## <a name="parameterexpression"></a>ParameterExpression

<xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> değişken adları, başındaki bir "$" simgesiyle görüntülenir.

Bir parametre bir ada sahip değilse, `$var1` veya `$var2`gibi otomatik olarak oluşturulan bir ad atanır.

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

Tamsayı değerlerini, dizeleri ve `null`temsil eden <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> nesneleri için, sabitin değeri görüntülenir.

Bazı sayısal türler için, değere bir sonek eklenir:

| Type | Anahtar sözcüğü | Önekini |
|--|--|--|
| <xref:System.UInt32> | [UInteger](../../../language-reference/data-types/uinteger-data-type.md) | U |
| <xref:System.Int64> | [Kalacağını](../../../language-reference/data-types/long-data-type.md) | L |
| <xref:System.UInt64> | ['Tur](../../../language-reference/data-types/ulong-data-type.md) | UL |
| <xref:System.Double> | [Çift](../../../language-reference/data-types/double-data-type.md) | D |
| <xref:System.Single> | [Sunuculu](../../../language-reference/data-types/single-data-type.md) | F |
| <xref:System.Decimal> | [Kategori](../../../language-reference/data-types/decimal-data-type.md) | M |

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

## <a name="blockexpression"></a>Blok Ifadesi

Bir <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> nesnesinin türü bloktaki son ifadenin türünden farklıysa, tür açılı ayraç içinde görüntülenir (`<` ve `>`). Aksi takdirde, <xref:System.Linq.Expressions.BlockExpression> nesnenin türü gösterilmez.

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

<xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> nesneler, temsilci türleriyle birlikte görüntülenir.

Lambda ifadesinin adı yoksa, `#Lambda1` veya `#Lambda2`gibi otomatik olarak oluşturulan bir ad atanır.

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

<xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType> nesnesi için varsayılan bir değer belirtirseniz, bu değer <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType> nesnesinden önce görüntülenir.

`.Label` belirteci etiketin başlangıcını gösterir. `.LabelTarget` belirteci, atlanacak hedefin hedefini gösterir.

Bir etiketin adı yoksa, `#Label1` veya `#Label2`gibi otomatik olarak oluşturulan bir ad atanır.

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

## <a name="checked-operators"></a>Denetlenen Işleçler

İşaretli işleçler, işlecin önünde `#` simgesiyle birlikte görüntülenir. Örneğin, denetlenen toplama işleci `#+`olarak görüntülenir.

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
