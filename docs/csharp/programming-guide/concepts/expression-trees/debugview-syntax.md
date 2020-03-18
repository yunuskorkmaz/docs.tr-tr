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
# <a name="debugview-syntax"></a><span data-ttu-id="19952-103">`DebugView`Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="19952-103">`DebugView` syntax</span></span>

<span data-ttu-id="19952-104">Özellik `DebugView` (yalnızca hata ayıklama olduğunda kullanılabilir) ifade ağaçlarının dize oluşturmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="19952-104">The `DebugView` property (available only when debugging) provides a string rendering of expression trees.</span></span> <span data-ttu-id="19952-105">Sözdiziminin çoğu anlamak oldukça basittir; özel durumlar aşağıdaki bölümlerde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="19952-105">Most of the syntax is fairly straightforward to understand; the special cases are described in the following sections.</span></span>

<span data-ttu-id="19952-106">Her örnek, `DebugView`'yi içeren bir blok açıklama yla takip edilir.</span><span class="sxs-lookup"><span data-stu-id="19952-106">Each example is followed by a block comment, containing the `DebugView`.</span></span>

## <a name="parameterexpression"></a><span data-ttu-id="19952-107">Parameterexpression</span><span class="sxs-lookup"><span data-stu-id="19952-107">ParameterExpression</span></span>

<span data-ttu-id="19952-108"><xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType>değişken adları başında `$` bir sembolle görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="19952-108"><xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> variable names are displayed with a `$` symbol at the beginning.</span></span>

<span data-ttu-id="19952-109">Bir parametrenin bir adı yoksa, otomatik olarak oluşturulan bir `$var1` ad `$var2`olarak atanır veya .</span><span class="sxs-lookup"><span data-stu-id="19952-109">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>

### <a name="examples"></a><span data-ttu-id="19952-110">Örnekler</span><span class="sxs-lookup"><span data-stu-id="19952-110">Examples</span></span>

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

## <a name="constantexpression"></a><span data-ttu-id="19952-111">Constantexpression</span><span class="sxs-lookup"><span data-stu-id="19952-111">ConstantExpression</span></span>

<span data-ttu-id="19952-112">İntesayı <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> değerlerini, dizeleri ve `null`, sabitin değerini temsil eden nesneler için görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="19952-112">For <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>

<span data-ttu-id="19952-113">Standart soneklerine C# literals olarak sahip sayısal türler için, sonek değere eklenir.</span><span class="sxs-lookup"><span data-stu-id="19952-113">For numeric types that have standard suffixes as C# literals, the suffix is added to the value.</span></span> <span data-ttu-id="19952-114">Aşağıdaki tablo, çeşitli sayısal türleri ile ilişkili sonekleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="19952-114">The following table shows the suffixes associated with various numeric types.</span></span>

| <span data-ttu-id="19952-115">Tür</span><span class="sxs-lookup"><span data-stu-id="19952-115">Type</span></span> | <span data-ttu-id="19952-116">Anahtar kelime</span><span class="sxs-lookup"><span data-stu-id="19952-116">Keyword</span></span> | <span data-ttu-id="19952-117">Soneki</span><span class="sxs-lookup"><span data-stu-id="19952-117">Suffix</span></span> |
|--|--|--|
| <xref:System.UInt32?displayProperty=nameWithType> | [<span data-ttu-id="19952-118">Uint</span><span class="sxs-lookup"><span data-stu-id="19952-118">uint</span></span>](../../../language-reference/builtin-types/integral-numeric-types.md) | <span data-ttu-id="19952-119">U</span><span class="sxs-lookup"><span data-stu-id="19952-119">U</span></span> |
| <xref:System.Int64?displayProperty=nameWithType> | [<span data-ttu-id="19952-120">long</span><span class="sxs-lookup"><span data-stu-id="19952-120">long</span></span>](../../../language-reference/builtin-types/integral-numeric-types.md) | <span data-ttu-id="19952-121">L</span><span class="sxs-lookup"><span data-stu-id="19952-121">L</span></span> |
| <xref:System.UInt64?displayProperty=nameWithType> | [<span data-ttu-id="19952-122">ulong</span><span class="sxs-lookup"><span data-stu-id="19952-122">ulong</span></span>](../../../language-reference/builtin-types/integral-numeric-types.md) | <span data-ttu-id="19952-123">UL</span><span class="sxs-lookup"><span data-stu-id="19952-123">UL</span></span> |
| <xref:System.Double?displayProperty=nameWithType> | [<span data-ttu-id="19952-124">double</span><span class="sxs-lookup"><span data-stu-id="19952-124">double</span></span>](../../../language-reference/builtin-types/floating-point-numeric-types.md) | <span data-ttu-id="19952-125">D</span><span class="sxs-lookup"><span data-stu-id="19952-125">D</span></span> |
| <xref:System.Single?displayProperty=nameWithType> | [<span data-ttu-id="19952-126">float</span><span class="sxs-lookup"><span data-stu-id="19952-126">float</span></span>](../../../language-reference/builtin-types/floating-point-numeric-types.md) | <span data-ttu-id="19952-127">F</span><span class="sxs-lookup"><span data-stu-id="19952-127">F</span></span> |
| <xref:System.Decimal?displayProperty=nameWithType> | [<span data-ttu-id="19952-128">decimal</span><span class="sxs-lookup"><span data-stu-id="19952-128">decimal</span></span>](../../../language-reference/builtin-types/floating-point-numeric-types.md) | <span data-ttu-id="19952-129">M</span><span class="sxs-lookup"><span data-stu-id="19952-129">M</span></span> |

### <a name="examples"></a><span data-ttu-id="19952-130">Örnekler</span><span class="sxs-lookup"><span data-stu-id="19952-130">Examples</span></span>

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

## <a name="blockexpression"></a><span data-ttu-id="19952-131">Blockexpression</span><span class="sxs-lookup"><span data-stu-id="19952-131">BlockExpression</span></span>

<span data-ttu-id="19952-132">Bir <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> nesnenin türü bloktaki son ifadenin türünden farklıysa, tür açı ayraçları `>`(ve)`<` içinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="19952-132">If the type of a <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> object differs from the type of the last expression in the block, the type is displayed within angle brackets (`<` and `>`).</span></span> <span data-ttu-id="19952-133">Aksi takdirde, <xref:System.Linq.Expressions.BlockExpression> nesnenin türü görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="19952-133">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>

### <a name="examples"></a><span data-ttu-id="19952-134">Örnekler</span><span class="sxs-lookup"><span data-stu-id="19952-134">Examples</span></span>

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

## <a name="lambdaexpression"></a><span data-ttu-id="19952-135">Lambdaexpression</span><span class="sxs-lookup"><span data-stu-id="19952-135">LambdaExpression</span></span>

<span data-ttu-id="19952-136"><xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType>nesneler, temsilci türleri ile birlikte görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="19952-136"><xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> objects are displayed together with their delegate types.</span></span>

<span data-ttu-id="19952-137">Lambda ifadesinin bir adı yoksa, otomatik olarak oluşturulan bir ad `#Lambda1` `#Lambda2`olarak atanır veya .</span><span class="sxs-lookup"><span data-stu-id="19952-137">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>

### <a name="examples"></a><span data-ttu-id="19952-138">Örnekler</span><span class="sxs-lookup"><span data-stu-id="19952-138">Examples</span></span>

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

## <a name="labelexpression"></a><span data-ttu-id="19952-139">Labelexpression</span><span class="sxs-lookup"><span data-stu-id="19952-139">LabelExpression</span></span>

<span data-ttu-id="19952-140"><xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType> Nesne için varsayılan bir değer belirtirseniz, bu <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType> değer nesnenin önünde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="19952-140">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType> object.</span></span>

<span data-ttu-id="19952-141">Belirteç, `.Label` etiketin başlangıcını gösterir.</span><span class="sxs-lookup"><span data-stu-id="19952-141">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="19952-142">Belirteç, `.LabelTarget` atlayacak hedefin hedefini gösterir.</span><span class="sxs-lookup"><span data-stu-id="19952-142">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>

<span data-ttu-id="19952-143">Bir etiketin adı yoksa, otomatik olarak oluşturulan bir ad `#Label1` olarak `#Label2`atanır.</span><span class="sxs-lookup"><span data-stu-id="19952-143">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>

### <a name="examples"></a><span data-ttu-id="19952-144">Örnekler</span><span class="sxs-lookup"><span data-stu-id="19952-144">Examples</span></span>

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

## <a name="checked-operators"></a><span data-ttu-id="19952-145">Denetlenen Operatörler</span><span class="sxs-lookup"><span data-stu-id="19952-145">Checked Operators</span></span>

<span data-ttu-id="19952-146">Denetlenen işleçler `#` operatörün önündeki sembolle görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="19952-146">Checked operators are displayed with the `#` symbol in front of the operator.</span></span> <span data-ttu-id="19952-147">Örneğin, denetlenen ek işleç `#+`.</span><span class="sxs-lookup"><span data-stu-id="19952-147">For example, the checked addition operator is displayed as `#+`.</span></span>

### <a name="examples"></a><span data-ttu-id="19952-148">Örnekler</span><span class="sxs-lookup"><span data-stu-id="19952-148">Examples</span></span>

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
