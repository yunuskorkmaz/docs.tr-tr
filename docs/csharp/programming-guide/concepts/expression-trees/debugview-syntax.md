---
title: DebugView özelliği tarafından kullanılan sözdizimi (C#)
description: İfade ağaçları bir dize temsilini üretmek için DebugView özelliği tarafından kullanılan özel bir sözdizimi açıklar
author: zspitz
ms.author: wiwagn
ms.date: 05/22/2019
ms.topic: reference
helpviewer_keywords:
- expression trees
- debugview
ms.openlocfilehash: ba695fc808108c49a4eee3c70a305b24c91769d8
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661722"
---
# <a name="debugview-syntax"></a>`DebugView` Söz dizimi

`DebugView` Özelliği (yalnızca hata ayıklama sırasında kullanılabilir) ifade ağaçları dize işlenmesini sağlar. Çoğu söz dizimini anlamak oldukça açıktır; özel durumlar aşağıdaki bölümlerde açıklanmıştır.

Her örneğin bir blok açıklama tarafından izlenir içeren `DebugView`.

## <a name="parameterexpression"></a>ParameterExpression

<xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> değişken adları ile görüntülenir bir `$` simge başlangıcındaki.

Parametre bir adı yoksa, otomatik olarak oluşturulmuş bir adı gibi atandıktan `$var1` veya `$var2`.

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

## <a name="constantexpression"></a>SabitDeyim'in

İçin <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> dize, tamsayı değerlerini temsil eden nesneleri ve `null`, sabit değeri görüntülenir.

C# sabit değer olarak standart sonekleri olan sayısal türleri için sonek değerine eklenir. Aşağıdaki tabloda, çeşitli sayısal türler ile ilişkili soneklerini gösterir.

| Tür | Anahtar sözcüğü | Son eki |
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

## <a name="blockexpression"></a>BlockExpression

Varsa türünü bir <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> bloğundaki son ifadenin türü nesne farklıdır, açılı ayraçlar içinde türü görüntülenir (`<` ve `>`). Aksi halde, türünü <xref:System.Linq.Expressions.BlockExpression> nesne görüntülenmez.

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

<xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> nesneler, temsilci türleri ile birlikte görüntülenir.

Bir lambda ifadesi bir adı yoksa, otomatik olarak oluşturulmuş bir adı gibi atandıktan `#Lambda1` veya `#Lambda2`.

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

İçin varsayılan bir değer belirtirseniz <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType> nesnesi, bu değer, önce görüntülenir <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType> nesne.

`.Label` Belirteci etiketi başlangıcını gösterir. `.LabelTarget` Belirteci atlamak için hedef hedefinin gösterir.

Bir etiket bir ad yoksa otomatik olarak oluşturulmuş bir adı gibi atandıktan `#Label1` veya `#Label2`.

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

## <a name="checked-operators"></a>İşaretli işleçleri

İşaretli işleçleri ile görüntülenir `#` işleci önünde simge. Örneğin, işaretli Toplama işleci olarak görüntülenir `#+`.

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
