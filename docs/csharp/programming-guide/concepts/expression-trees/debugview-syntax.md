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
# <a name="debugview-syntax"></a><span data-ttu-id="a1243-103">**DebugView** sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a1243-103">**DebugView** syntax</span></span>

<span data-ttu-id="a1243-104">**DebugView** özelliği (yalnızca hata ayıklama sırasında kullanılabilir), ifade ağaçlarının dize işlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a1243-104">The **DebugView** property (available only when debugging) provides a string rendering of expression trees.</span></span> <span data-ttu-id="a1243-105">Sözdiziminin çoğu anlaşılması oldukça basittir; özel durumlar aşağıdaki bölümlerde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a1243-105">Most of the syntax is fairly straightforward to understand; the special cases are described in the following sections.</span></span>

<span data-ttu-id="a1243-106">Her örnek, **DebugView** içeren bir blok yorumu tarafından izlenir.</span><span class="sxs-lookup"><span data-stu-id="a1243-106">Each example is followed by a block comment, containing the **DebugView**.</span></span>

## <a name="parameterexpression"></a><span data-ttu-id="a1243-107">ParameterExpression</span><span class="sxs-lookup"><span data-stu-id="a1243-107">ParameterExpression</span></span>

<span data-ttu-id="a1243-108"><xref:System.Linq.Expressions.ParameterExpression> değişken adları başındaki bir simgeyle görüntülenir `$` .</span><span class="sxs-lookup"><span data-stu-id="a1243-108"><xref:System.Linq.Expressions.ParameterExpression> variable names are displayed with a `$` symbol at the beginning.</span></span>

<span data-ttu-id="a1243-109">Bir parametre bir ada sahip değilse, veya gibi otomatik olarak oluşturulan bir ad atanır `$var1` `$var2` .</span><span class="sxs-lookup"><span data-stu-id="a1243-109">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>

### <a name="examples"></a><span data-ttu-id="a1243-110">Örnekler</span><span class="sxs-lookup"><span data-stu-id="a1243-110">Examples</span></span>

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

## <a name="constantexpression"></a><span data-ttu-id="a1243-111">ConstantExpression</span><span class="sxs-lookup"><span data-stu-id="a1243-111">ConstantExpression</span></span>

<span data-ttu-id="a1243-112"><xref:System.Linq.Expressions.ConstantExpression>Tamsayı değerlerini, dizeleri ve ' ı temsil eden nesneler için `null` , sabitin değeri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a1243-112">For <xref:System.Linq.Expressions.ConstantExpression> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>

<span data-ttu-id="a1243-113">Standart son eklerini C# sabit değerleri olan sayısal türler için, sonek değerine eklenir.</span><span class="sxs-lookup"><span data-stu-id="a1243-113">For numeric types that have standard suffixes as C# literals, the suffix is added to the value.</span></span> <span data-ttu-id="a1243-114">Aşağıdaki tabloda, çeşitli sayısal türlerle ilişkili sonekler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a1243-114">The following table shows the suffixes associated with various numeric types.</span></span>

| <span data-ttu-id="a1243-115">Tür</span><span class="sxs-lookup"><span data-stu-id="a1243-115">Type</span></span> | <span data-ttu-id="a1243-116">Sözcükle</span><span class="sxs-lookup"><span data-stu-id="a1243-116">Keyword</span></span> | <span data-ttu-id="a1243-117">Önekini</span><span class="sxs-lookup"><span data-stu-id="a1243-117">Suffix</span></span> |
|--|--|--|
| <xref:System.UInt32?displayProperty=nameWithType> | [<span data-ttu-id="a1243-118">uint</span><span class="sxs-lookup"><span data-stu-id="a1243-118">uint</span></span>](../../../language-reference/builtin-types/integral-numeric-types.md) | <span data-ttu-id="a1243-119">U</span><span class="sxs-lookup"><span data-stu-id="a1243-119">U</span></span> |
| <xref:System.Int64?displayProperty=nameWithType> | [<span data-ttu-id="a1243-120">long</span><span class="sxs-lookup"><span data-stu-id="a1243-120">long</span></span>](../../../language-reference/builtin-types/integral-numeric-types.md) | <span data-ttu-id="a1243-121">L</span><span class="sxs-lookup"><span data-stu-id="a1243-121">L</span></span> |
| <xref:System.UInt64?displayProperty=nameWithType> | [<span data-ttu-id="a1243-122">ulong</span><span class="sxs-lookup"><span data-stu-id="a1243-122">ulong</span></span>](../../../language-reference/builtin-types/integral-numeric-types.md) | <span data-ttu-id="a1243-123">UL</span><span class="sxs-lookup"><span data-stu-id="a1243-123">UL</span></span> |
| <xref:System.Double?displayProperty=nameWithType> | [<span data-ttu-id="a1243-124">double</span><span class="sxs-lookup"><span data-stu-id="a1243-124">double</span></span>](../../../language-reference/builtin-types/floating-point-numeric-types.md) | <span data-ttu-id="a1243-125">D</span><span class="sxs-lookup"><span data-stu-id="a1243-125">D</span></span> |
| <xref:System.Single?displayProperty=nameWithType> | [<span data-ttu-id="a1243-126">float</span><span class="sxs-lookup"><span data-stu-id="a1243-126">float</span></span>](../../../language-reference/builtin-types/floating-point-numeric-types.md) | <span data-ttu-id="a1243-127">F</span><span class="sxs-lookup"><span data-stu-id="a1243-127">F</span></span> |
| <xref:System.Decimal?displayProperty=nameWithType> | [<span data-ttu-id="a1243-128">decimal</span><span class="sxs-lookup"><span data-stu-id="a1243-128">decimal</span></span>](../../../language-reference/builtin-types/floating-point-numeric-types.md) | <span data-ttu-id="a1243-129">M</span><span class="sxs-lookup"><span data-stu-id="a1243-129">M</span></span> |

### <a name="examples"></a><span data-ttu-id="a1243-130">Örnekler</span><span class="sxs-lookup"><span data-stu-id="a1243-130">Examples</span></span>

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

## <a name="blockexpression"></a><span data-ttu-id="a1243-131">Blok Ifadesi</span><span class="sxs-lookup"><span data-stu-id="a1243-131">BlockExpression</span></span>

<span data-ttu-id="a1243-132">Bir nesnenin türü, <xref:System.Linq.Expressions.BlockExpression> bloktaki son ifadenin türünden farklıysa, tür açılı ayraçlar ( `<` ve) içinde görüntülenir `>` .</span><span class="sxs-lookup"><span data-stu-id="a1243-132">If the type of a <xref:System.Linq.Expressions.BlockExpression> object differs from the type of the last expression in the block, the type is displayed within angle brackets (`<` and `>`).</span></span> <span data-ttu-id="a1243-133">Aksi takdirde, <xref:System.Linq.Expressions.BlockExpression> nesne türü görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="a1243-133">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>

### <a name="examples"></a><span data-ttu-id="a1243-134">Örnekler</span><span class="sxs-lookup"><span data-stu-id="a1243-134">Examples</span></span>

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

## <a name="lambdaexpression"></a><span data-ttu-id="a1243-135">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="a1243-135">LambdaExpression</span></span>

<span data-ttu-id="a1243-136"><xref:System.Linq.Expressions.LambdaExpression> nesneler, temsilci türleriyle birlikte görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a1243-136"><xref:System.Linq.Expressions.LambdaExpression> objects are displayed together with their delegate types.</span></span>

<span data-ttu-id="a1243-137">Lambda ifadesi bir ada sahip değilse, veya gibi otomatik olarak oluşturulan bir ad atanır `#Lambda1` `#Lambda2` .</span><span class="sxs-lookup"><span data-stu-id="a1243-137">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>

### <a name="examples"></a><span data-ttu-id="a1243-138">Örnekler</span><span class="sxs-lookup"><span data-stu-id="a1243-138">Examples</span></span>

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

## <a name="labelexpression"></a><span data-ttu-id="a1243-139">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="a1243-139">LabelExpression</span></span>

<span data-ttu-id="a1243-140">Nesne için varsayılan bir değer belirtirseniz <xref:System.Linq.Expressions.LabelExpression> , bu değer nesneden önce görüntülenir <xref:System.Linq.Expressions.LabelTarget> .</span><span class="sxs-lookup"><span data-stu-id="a1243-140">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget> object.</span></span>

<span data-ttu-id="a1243-141">`.Label`Belirteç, etiketin başlangıcını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a1243-141">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="a1243-142">`.LabelTarget`Belirteç, atlanacak hedefin hedefini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a1243-142">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>

<span data-ttu-id="a1243-143">Bir etiket bir ada sahip değilse, veya gibi otomatik olarak oluşturulan bir ad atanır `#Label1` `#Label2` .</span><span class="sxs-lookup"><span data-stu-id="a1243-143">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>

### <a name="examples"></a><span data-ttu-id="a1243-144">Örnekler</span><span class="sxs-lookup"><span data-stu-id="a1243-144">Examples</span></span>

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

## <a name="checked-operators"></a><span data-ttu-id="a1243-145">Denetlenen Işleçler</span><span class="sxs-lookup"><span data-stu-id="a1243-145">Checked Operators</span></span>

<span data-ttu-id="a1243-146">İşaretli işleçler, `#` işlecin önünde simgesiyle birlikte görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a1243-146">Checked operators are displayed with the `#` symbol in front of the operator.</span></span> <span data-ttu-id="a1243-147">Örneğin, denetlenen toplama işleci olarak görüntülenir `#+` .</span><span class="sxs-lookup"><span data-stu-id="a1243-147">For example, the checked addition operator is displayed as `#+`.</span></span>

### <a name="examples"></a><span data-ttu-id="a1243-148">Örnekler</span><span class="sxs-lookup"><span data-stu-id="a1243-148">Examples</span></span>

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
