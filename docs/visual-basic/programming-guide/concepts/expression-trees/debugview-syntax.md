---
title: DebugView özelliği tarafından kullanılan sözdizimi
description: İfade ağaçlarının dize gösterimini üretmek için DebugView özelliği tarafından kullanılan özel sözdizimini açıklar
author: zspitz
ms.author: wiwagn
ms.date: 02/14/2021
ms.topic: reference
helpviewer_keywords:
- expression trees
- debugview
ms.openlocfilehash: 1b6d117bb1ce0cb13344c72be3b55742c443448f
ms.sourcegitcommit: 456b3cd82a87b453fa737b4661295070d1b6d684
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2021
ms.locfileid: "100639195"
---
# <a name="debugview-syntax"></a>**DebugView** sözdizimi

**DebugView** özelliği (yalnızca hata ayıklama sırasında kullanılabilir), ifade ağaçlarının dize işlemesini sağlar. Sözdiziminin çoğu anlaşılması oldukça basittir; özel durumlar aşağıdaki bölümlerde açıklanmıştır.

Her örnek, **DebugView** içeren bir açıklama bloğu tarafından izlenir.

## <a name="parameterexpression"></a>ParameterExpression

<xref:System.Linq.Expressions.ParameterExpression> değişken adları, başlangıcında bir "$" simgesiyle görüntülenir.

Bir parametre bir ada sahip değilse, veya gibi otomatik olarak oluşturulan bir ad atanır `$var1` `$var2` .

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

<xref:System.Linq.Expressions.ConstantExpression>Tamsayı değerlerini, dizeleri ve ' ı temsil eden nesneler için `null` , sabitin değeri görüntülenir.

Bazı sayısal türler için, değere bir sonek eklenir:

| Tür | Sözcükle | Önekini |
|--|--|--|
| <xref:System.UInt32?displayProperty=nameWithType> | [UInteger](../../../language-reference/data-types/uinteger-data-type.md) | U |
| <xref:System.Int64?displayProperty=nameWithType> | [Kalacağını](../../../language-reference/data-types/long-data-type.md) | L |
| <xref:System.UInt64?displayProperty=nameWithType> | ['Tur](../../../language-reference/data-types/ulong-data-type.md) | UL |
| <xref:System.Double?displayProperty=nameWithType> | [Çift](../../../language-reference/data-types/double-data-type.md) | D |
| <xref:System.Single?displayProperty=nameWithType> | [Tek](../../../language-reference/data-types/single-data-type.md) | F |
| <xref:System.Decimal?displayProperty=nameWithType> | [Kategori](../../../language-reference/data-types/decimal-data-type.md) | M |

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

Bir nesnenin türü, <xref:System.Linq.Expressions.BlockExpression> bloktaki son ifadenin türünden farklıysa, tür açılı ayraçlar ( `<` ve) içinde görüntülenir `>` . Aksi takdirde, <xref:System.Linq.Expressions.BlockExpression> nesne türü görüntülenmez.

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

<xref:System.Linq.Expressions.LambdaExpression> nesneler, temsilci türleriyle birlikte görüntülenir.

Lambda ifadesi bir ada sahip değilse, veya gibi otomatik olarak oluşturulan bir ad atanır `#Lambda1` `#Lambda2` .

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

Nesne için varsayılan bir değer belirtirseniz <xref:System.Linq.Expressions.LabelExpression> , bu değer nesneden önce görüntülenir <xref:System.Linq.Expressions.LabelTarget> .

`.Label`Belirteç, etiketin başlangıcını gösterir. `.LabelTarget`Belirteç, atlanacak hedefin hedefini gösterir.

Bir etiket bir ada sahip değilse, veya gibi otomatik olarak oluşturulan bir ad atanır `#Label1` `#Label2` .

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

İşaretli işleçler, `#` işlecin önünde simgesiyle birlikte görüntülenir. Örneğin, denetlenen toplama işleci olarak görüntülenir `#+` .

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
