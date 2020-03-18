---
title: DebugView özelliği tarafından kullanılan sözdizimi (C#)
description: İfade ağaçlarının dize gösterimini oluşturmak için DebugView özelliği tarafından kullanılan özel sözdizimini açıklar
author: zspitz
ms.author: wiwagn
ms.date: 05/22/2019
ms.topic: reference
helpviewer_keywords:
- expression trees
- debugview
ms.openlocfilehash: ba695fc808108c49a4eee3c70a305b24c91769d8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "67661722"
---
# <a name="debugview-syntax"></a>`DebugView`Sözdizimi

Özellik `DebugView` (yalnızca hata ayıklama olduğunda kullanılabilir) ifade ağaçlarının dize oluşturmasını sağlar. Sözdiziminin çoğu anlamak oldukça basittir; özel durumlar aşağıdaki bölümlerde açıklanmıştır.

Her örnek, `DebugView`'yi içeren bir blok açıklama yla takip edilir.

## <a name="parameterexpression"></a>Parameterexpression

<xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType>değişken adları başında `$` bir sembolle görüntülenir.

Bir parametrenin bir adı yoksa, otomatik olarak oluşturulan bir `$var1` ad `$var2`olarak atanır veya .

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

## <a name="constantexpression"></a>Constantexpression

İntesayı <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> değerlerini, dizeleri ve `null`, sabitin değerini temsil eden nesneler için görüntülenir.

Standart soneklerine C# literals olarak sahip sayısal türler için, sonek değere eklenir. Aşağıdaki tablo, çeşitli sayısal türleri ile ilişkili sonekleri gösterir.

| Tür | Anahtar kelime | Soneki |
|--|--|--|
| <xref:System.UInt32?displayProperty=nameWithType> | [Uint](../../../language-reference/builtin-types/integral-numeric-types.md) | U |
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

## <a name="blockexpression"></a>Blockexpression

Bir <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> nesnenin türü bloktaki son ifadenin türünden farklıysa, tür açı ayraçları `>`(ve)`<` içinde görüntülenir. Aksi takdirde, <xref:System.Linq.Expressions.BlockExpression> nesnenin türü görüntülenmez.

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

## <a name="lambdaexpression"></a>Lambdaexpression

<xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType>nesneler, temsilci türleri ile birlikte görüntülenir.

Lambda ifadesinin bir adı yoksa, otomatik olarak oluşturulan bir ad `#Lambda1` `#Lambda2`olarak atanır veya .

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

## <a name="labelexpression"></a>Labelexpression

<xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType> Nesne için varsayılan bir değer belirtirseniz, bu <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType> değer nesnenin önünde görüntülenir.

Belirteç, `.Label` etiketin başlangıcını gösterir. Belirteç, `.LabelTarget` atlayacak hedefin hedefini gösterir.

Bir etiketin adı yoksa, otomatik olarak oluşturulan bir ad `#Label1` olarak `#Label2`atanır.

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

## <a name="checked-operators"></a>Denetlenen Operatörler

Denetlenen işleçler `#` operatörün önündeki sembolle görüntülenir. Örneğin, denetlenen ek işleç `#+`.

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
