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
ms.openlocfilehash: bc3fc579ed8031d818241f41ac728ef7e5be0b99
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690112"
---
# <a name="debugview-syntax"></a><span data-ttu-id="6d321-103">`DebugView` Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="6d321-103">`DebugView` syntax</span></span>

<span data-ttu-id="6d321-104">`DebugView` Özelliği (yalnızca hata ayıklama sırasında kullanılabilir) ifade ağaçları dize işlenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="6d321-104">The `DebugView` property (available only when debugging) provides a string rendering of expression trees.</span></span> <span data-ttu-id="6d321-105">Çoğu söz dizimini anlamak oldukça açıktır; özel durumlar aşağıdaki bölümlerde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="6d321-105">Most of the syntax is fairly straightforward to understand; the special cases are described in the following sections.</span></span>

<span data-ttu-id="6d321-106">Her örneğin bir blok açıklama tarafından izlenir içeren `DebugView`.</span><span class="sxs-lookup"><span data-stu-id="6d321-106">Each example is followed by a block comment, containing the `DebugView`.</span></span>

## <a name="parameterexpression"></a><span data-ttu-id="6d321-107">ParameterExpression</span><span class="sxs-lookup"><span data-stu-id="6d321-107">ParameterExpression</span></span>

<span data-ttu-id="6d321-108"><xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> değişken adları ile görüntülenir bir `$` simge başlangıcındaki.</span><span class="sxs-lookup"><span data-stu-id="6d321-108"><xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> variable names are displayed with a `$` symbol at the beginning.</span></span>

<span data-ttu-id="6d321-109">Parametre bir adı yoksa, otomatik olarak oluşturulmuş bir adı gibi atandıktan `$var1` veya `$var2`.</span><span class="sxs-lookup"><span data-stu-id="6d321-109">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>

### <a name="examples"></a><span data-ttu-id="6d321-110">Örnekler</span><span class="sxs-lookup"><span data-stu-id="6d321-110">Examples</span></span>

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

## <a name="constantexpression"></a><span data-ttu-id="6d321-111">SabitDeyim'in</span><span class="sxs-lookup"><span data-stu-id="6d321-111">ConstantExpression</span></span>

<span data-ttu-id="6d321-112">İçin <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> dize, tamsayı değerlerini temsil eden nesneleri ve `null`, sabit değeri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6d321-112">For <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>

<span data-ttu-id="6d321-113">C# sabit değer olarak standart sonekleri olan sayısal türleri için sonek değerine eklenir.</span><span class="sxs-lookup"><span data-stu-id="6d321-113">For numeric types that have standard suffixes as C# literals, the suffix is added to the value.</span></span> <span data-ttu-id="6d321-114">Aşağıdaki tabloda, çeşitli sayısal türler ile ilişkili soneklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6d321-114">The following table shows the suffixes associated with various numeric types.</span></span>

| <span data-ttu-id="6d321-115">Tür</span><span class="sxs-lookup"><span data-stu-id="6d321-115">Type</span></span> | <span data-ttu-id="6d321-116">Anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="6d321-116">Keyword</span></span> | <span data-ttu-id="6d321-117">Son eki</span><span class="sxs-lookup"><span data-stu-id="6d321-117">Suffix</span></span> |
|--|--|--|
| <xref:System.UInt32?displayProperty=nameWithType> | [<span data-ttu-id="6d321-118">uint</span><span class="sxs-lookup"><span data-stu-id="6d321-118">uint</span></span>](../../../language-reference/keywords/uint.md) | <span data-ttu-id="6d321-119">U</span><span class="sxs-lookup"><span data-stu-id="6d321-119">U</span></span> |
| <xref:System.Int64?displayProperty=nameWithType> | [<span data-ttu-id="6d321-120">long</span><span class="sxs-lookup"><span data-stu-id="6d321-120">long</span></span>](../../../language-reference/keywords/long.md) | <span data-ttu-id="6d321-121">L</span><span class="sxs-lookup"><span data-stu-id="6d321-121">L</span></span> |
| <xref:System.UInt64?displayProperty=nameWithType> | [<span data-ttu-id="6d321-122">ulong</span><span class="sxs-lookup"><span data-stu-id="6d321-122">ulong</span></span>](../../../language-reference/keywords/ulong.md) | <span data-ttu-id="6d321-123">UL</span><span class="sxs-lookup"><span data-stu-id="6d321-123">UL</span></span> |
| <xref:System.Double?displayProperty=nameWithType> | [<span data-ttu-id="6d321-124">double</span><span class="sxs-lookup"><span data-stu-id="6d321-124">double</span></span>](../../../language-reference/keywords/double.md) | <span data-ttu-id="6d321-125">D</span><span class="sxs-lookup"><span data-stu-id="6d321-125">D</span></span> |
| <xref:System.Single?displayProperty=nameWithType> | [<span data-ttu-id="6d321-126">float</span><span class="sxs-lookup"><span data-stu-id="6d321-126">float</span></span>](../../../language-reference/keywords/float.md) | <span data-ttu-id="6d321-127">F</span><span class="sxs-lookup"><span data-stu-id="6d321-127">F</span></span> |
| <xref:System.Decimal?displayProperty=nameWithType> | [<span data-ttu-id="6d321-128">decimal</span><span class="sxs-lookup"><span data-stu-id="6d321-128">decimal</span></span>](../../../language-reference/keywords/decimal.md) | <span data-ttu-id="6d321-129">M</span><span class="sxs-lookup"><span data-stu-id="6d321-129">M</span></span> |

### <a name="examples"></a><span data-ttu-id="6d321-130">Örnekler</span><span class="sxs-lookup"><span data-stu-id="6d321-130">Examples</span></span>

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

## <a name="blockexpression"></a><span data-ttu-id="6d321-131">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="6d321-131">BlockExpression</span></span>

<span data-ttu-id="6d321-132">Varsa türünü bir <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> bloğundaki son ifadenin türü nesne farklıdır, açılı ayraçlar içinde türü görüntülenir (`<` ve `>`).</span><span class="sxs-lookup"><span data-stu-id="6d321-132">If the type of a <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> object differs from the type of the last expression in the block, the type is displayed within angle brackets (`<` and `>`).</span></span> <span data-ttu-id="6d321-133">Aksi halde, türünü <xref:System.Linq.Expressions.BlockExpression> nesne görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="6d321-133">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>

### <a name="examples"></a><span data-ttu-id="6d321-134">Örnekler</span><span class="sxs-lookup"><span data-stu-id="6d321-134">Examples</span></span>

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

## <a name="lambdaexpression"></a><span data-ttu-id="6d321-135">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="6d321-135">LambdaExpression</span></span>

<span data-ttu-id="6d321-136"><xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> nesneler, temsilci türleri ile birlikte görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6d321-136"><xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> objects are displayed together with their delegate types.</span></span>

<span data-ttu-id="6d321-137">Bir lambda ifadesi bir adı yoksa, otomatik olarak oluşturulmuş bir adı gibi atandıktan `#Lambda1` veya `#Lambda2`.</span><span class="sxs-lookup"><span data-stu-id="6d321-137">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>

### <a name="examples"></a><span data-ttu-id="6d321-138">Örnekler</span><span class="sxs-lookup"><span data-stu-id="6d321-138">Examples</span></span>

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

## <a name="labelexpression"></a><span data-ttu-id="6d321-139">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="6d321-139">LabelExpression</span></span>

<span data-ttu-id="6d321-140">İçin varsayılan bir değer belirtirseniz <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType> nesnesi, bu değer, önce görüntülenir <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType> nesne.</span><span class="sxs-lookup"><span data-stu-id="6d321-140">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType> object.</span></span>

<span data-ttu-id="6d321-141">`.Label` Belirteci etiketi başlangıcını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6d321-141">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="6d321-142">`.LabelTarget` Belirteci atlamak için hedef hedefinin gösterir.</span><span class="sxs-lookup"><span data-stu-id="6d321-142">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>

<span data-ttu-id="6d321-143">Bir etiket bir ad yoksa otomatik olarak oluşturulmuş bir adı gibi atandıktan `#Label1` veya `#Label2`.</span><span class="sxs-lookup"><span data-stu-id="6d321-143">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>

### <a name="examples"></a><span data-ttu-id="6d321-144">Örnekler</span><span class="sxs-lookup"><span data-stu-id="6d321-144">Examples</span></span>

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

## <a name="checked-operators"></a><span data-ttu-id="6d321-145">İşaretli işleçleri</span><span class="sxs-lookup"><span data-stu-id="6d321-145">Checked Operators</span></span>

<span data-ttu-id="6d321-146">İşaretli işleçleri ile görüntülenir `#` işleci önünde simge.</span><span class="sxs-lookup"><span data-stu-id="6d321-146">Checked operators are displayed with the `#` symbol in front of the operator.</span></span> <span data-ttu-id="6d321-147">Örneğin, işaretli Toplama işleci olarak görüntülenir `#+`.</span><span class="sxs-lookup"><span data-stu-id="6d321-147">For example, the checked addition operator is displayed as `#+`.</span></span>

### <a name="examples"></a><span data-ttu-id="6d321-148">Örnekler</span><span class="sxs-lookup"><span data-stu-id="6d321-148">Examples</span></span>

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
