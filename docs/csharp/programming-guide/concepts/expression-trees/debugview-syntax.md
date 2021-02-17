---
title: DebugView özelliği tarafından kullanılan sözdizimi (C#)
description: İfade ağaçlarının dize gösterimini üretmek için DebugView özelliği tarafından kullanılan özel sözdizimini açıklar
author: zspitz
ms.author: wiwagn
ms.date: 14/02/2021
ms.topic: reference
helpviewer_keywords:
- expression trees
- debugview
ms.openlocfilehash: 387f3369d4b7543c3cfbc35c919818a932b822eb
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2021
ms.locfileid: "100583644"
---
# <a name="debugview-syntax"></a>**DebugView** sözdizimi

**DebugView** özelliği (yalnızca hata ayıklama sırasında kullanılabilir), ifade ağaçlarının dize işlemesini sağlar. Sözdiziminin çoğu anlaşılması oldukça basittir; özel durumlar aşağıdaki bölümlerde açıklanmıştır.

Her örnek, **DebugView** içeren bir blok yorumu tarafından izlenir.

## <a name="parameterexpression"></a>ParameterExpression

<xref:System.Linq.Expressions.ParameterExpression> değişken adları başındaki bir simgeyle görüntülenir `$` .

Bir parametre bir ada sahip değilse, veya gibi otomatik olarak oluşturulan bir ad atanır `$var1` `$var2` .

### <a name="examples"></a>Örnekler

```csharp
ParameterExpression numParam =  Expression.Parameter(typeof(int), "num");
/*
    $num
*/

ParameterExpression numParam =  Expression.Parameter(typeof(int));
/*
    $var1
*/
```

## <a name="constantexpression"></a>ConstantExpression

<xref:System.Linq.Expressions.ConstantExpression>Tamsayı değerlerini, dizeleri ve ' ı temsil eden nesneler için `null` , sabitin değeri görüntülenir.

Standart son eklerini C# sabit değerleri olan sayısal türler için, sonek değerine eklenir. Aşağıdaki tabloda, çeşitli sayısal türlerle ilişkili sonekler gösterilmektedir.

| Tür | Sözcükle | Önekini |
|--|--|--|
| <xref:System.UInt32?displayProperty=nameWithType> | [uint](../../../language-reference/builtin-types/integral-numeric-types.md) | U |
| <xref:System.Int64?displayProperty=nameWithType> | [long](../../../language-reference/builtin-types/integral-numeric-types.md) | L |
| <xref:System.UInt64?displayProperty=nameWithType> | [ulong](../../../language-reference/builtin-types/integral-numeric-types.md) | UL |
| <xref:System.Double?displayProperty=nameWithType> | [double](../../../language-reference/builtin-types/floating-point-numeric-types.md) | D |
| <xref:System.Single?displayProperty=nameWithType> | [float](../../../language-reference/builtin-types/floating-point-numeric-types.md) | F |
| <xref:System.Decimal?displayProperty=nameWithType> | [decimal](../../../language-reference/builtin-types/floating-point-numeric-types.md) | M |

### <a name="examples"></a>Örnekler

```csharp
int num = 10;
ConstantExpression expr = Expression.Constant(num);
/*
    10
*/

double num = 10;
ConstantExpression expr = Expression.Constant(num);
/*
    10D
*/
```

## <a name="blockexpression"></a>Blok Ifadesi

Bir nesnenin türü, <xref:System.Linq.Expressions.BlockExpression> bloktaki son ifadenin türünden farklıysa, tür açılı ayraçlar ( `<` ve) içinde görüntülenir `>` . Aksi takdirde, <xref:System.Linq.Expressions.BlockExpression> nesne türü görüntülenmez.

### <a name="examples"></a>Örnekler

```csharp
BlockExpression block = Expression.Block(Expression.Constant("test"));
/*
    .Block() {
        "test"
    }
*/

BlockExpression block =  Expression.Block(typeof(Object), Expression.Constant("test"));
/*
    .Block<System.Object>() {
        "test"
    }
*/
```

## <a name="lambdaexpression"></a>LambdaExpression

<xref:System.Linq.Expressions.LambdaExpression> nesneler, temsilci türleriyle birlikte görüntülenir.

Lambda ifadesi bir ada sahip değilse, veya gibi otomatik olarak oluşturulan bir ad atanır `#Lambda1` `#Lambda2` .

### <a name="examples"></a>Örnekler

```csharp
LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1));
/*
    .Lambda #Lambda1<System.Func'1[System.Int32]>() {
        1
    }
*/

LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1), "SampleLambda", null);
/*
    .Lambda #SampleLambda<System.Func'1[System.Int32]>() {
        1
    }
*/
```

## <a name="labelexpression"></a>LabelExpression

Nesne için varsayılan bir değer belirtirseniz <xref:System.Linq.Expressions.LabelExpression> , bu değer nesneden önce görüntülenir <xref:System.Linq.Expressions.LabelTarget> .

`.Label`Belirteç, etiketin başlangıcını gösterir. `.LabelTarget`Belirteç, atlanacak hedefin hedefini gösterir.

Bir etiket bir ada sahip değilse, veya gibi otomatik olarak oluşturulan bir ad atanır `#Label1` `#Label2` .

### <a name="examples"></a>Örnekler

```csharp
LabelTarget target = Expression.Label(typeof(int), "SampleLabel");
BlockExpression block = Expression.Block(
    Expression.Goto(target, Expression.Constant(0)),
    Expression.Label(target, Expression.Constant(-1))
);
/*
    .Block() {
        .Goto SampleLabel { 0 };
        .Label
            -1
        .LabelTarget SampleLabel:
    }
*/

LabelTarget target = Expression.Label();
BlockExpression block = Expression.Block(
    Expression.Goto(target),
    Expression.Label(target)
);
/*
    .Block() {
        .Goto #Label1 { };
        .Label
        .LabelTarget #Label1:
    }
*/
```

## <a name="checked-operators"></a>Denetlenen Işleçler

İşaretli işleçler, `#` işlecin önünde simgesiyle birlikte görüntülenir. Örneğin, denetlenen toplama işleci olarak görüntülenir `#+` .

### <a name="examples"></a>Örnekler

```csharp
Expression expr = Expression.AddChecked( Expression.Constant(1), Expression.Constant(2));
/*
    1 #+ 2
*/

Expression expr = Expression.ConvertChecked( Expression.Constant(10.0), typeof(int));
/*
    #(System.Int32)10D
*/
```
