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
# <a name="debugview-syntax"></a><span data-ttu-id="21f5d-103">**DebugView** sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21f5d-103">**DebugView** syntax</span></span>

<span data-ttu-id="21f5d-104">**DebugView** özelliği (yalnızca hata ayıklama sırasında kullanılabilir), ifade ağaçlarının dize işlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="21f5d-104">The **DebugView** property (available only when debugging) provides a string rendering of expression trees.</span></span> <span data-ttu-id="21f5d-105">Sözdiziminin çoğu anlaşılması oldukça basittir; özel durumlar aşağıdaki bölümlerde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="21f5d-105">Most of the syntax is fairly straightforward to understand; the special cases are described in the following sections.</span></span>

<span data-ttu-id="21f5d-106">Her örnek, **DebugView** içeren bir açıklama bloğu tarafından izlenir.</span><span class="sxs-lookup"><span data-stu-id="21f5d-106">Each example is followed by a comment block containing the **DebugView**.</span></span>

## <a name="parameterexpression"></a><span data-ttu-id="21f5d-107">ParameterExpression</span><span class="sxs-lookup"><span data-stu-id="21f5d-107">ParameterExpression</span></span>

<span data-ttu-id="21f5d-108"><xref:System.Linq.Expressions.ParameterExpression> değişken adları, başlangıcında bir "$" simgesiyle görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="21f5d-108"><xref:System.Linq.Expressions.ParameterExpression> variable names are displayed with a "$" symbol at the beginning.</span></span>

<span data-ttu-id="21f5d-109">Bir parametre bir ada sahip değilse, veya gibi otomatik olarak oluşturulan bir ad atanır `$var1` `$var2` .</span><span class="sxs-lookup"><span data-stu-id="21f5d-109">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>

### <a name="examples"></a><span data-ttu-id="21f5d-110">Örnekler</span><span class="sxs-lookup"><span data-stu-id="21f5d-110">Examples</span></span>

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

## <a name="constantexpressions"></a><span data-ttu-id="21f5d-111">ConstantExpressions</span><span class="sxs-lookup"><span data-stu-id="21f5d-111">ConstantExpressions</span></span>

<span data-ttu-id="21f5d-112"><xref:System.Linq.Expressions.ConstantExpression>Tamsayı değerlerini, dizeleri ve ' ı temsil eden nesneler için `null` , sabitin değeri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="21f5d-112">For <xref:System.Linq.Expressions.ConstantExpression> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>

<span data-ttu-id="21f5d-113">Bazı sayısal türler için, değere bir sonek eklenir:</span><span class="sxs-lookup"><span data-stu-id="21f5d-113">For some numeric types, a suffix is added to the value:</span></span>

| <span data-ttu-id="21f5d-114">Tür</span><span class="sxs-lookup"><span data-stu-id="21f5d-114">Type</span></span> | <span data-ttu-id="21f5d-115">Sözcükle</span><span class="sxs-lookup"><span data-stu-id="21f5d-115">Keyword</span></span> | <span data-ttu-id="21f5d-116">Önekini</span><span class="sxs-lookup"><span data-stu-id="21f5d-116">Suffix</span></span> |
|--|--|--|
| <xref:System.UInt32?displayProperty=nameWithType> | [<span data-ttu-id="21f5d-117">UInteger</span><span class="sxs-lookup"><span data-stu-id="21f5d-117">UInteger</span></span>](../../../language-reference/data-types/uinteger-data-type.md) | <span data-ttu-id="21f5d-118">U</span><span class="sxs-lookup"><span data-stu-id="21f5d-118">U</span></span> |
| <xref:System.Int64?displayProperty=nameWithType> | [<span data-ttu-id="21f5d-119">Kalacağını</span><span class="sxs-lookup"><span data-stu-id="21f5d-119">Long</span></span>](../../../language-reference/data-types/long-data-type.md) | <span data-ttu-id="21f5d-120">L</span><span class="sxs-lookup"><span data-stu-id="21f5d-120">L</span></span> |
| <xref:System.UInt64?displayProperty=nameWithType> | [<span data-ttu-id="21f5d-121">'Tur</span><span class="sxs-lookup"><span data-stu-id="21f5d-121">ULong</span></span>](../../../language-reference/data-types/ulong-data-type.md) | <span data-ttu-id="21f5d-122">UL</span><span class="sxs-lookup"><span data-stu-id="21f5d-122">UL</span></span> |
| <xref:System.Double?displayProperty=nameWithType> | [<span data-ttu-id="21f5d-123">Çift</span><span class="sxs-lookup"><span data-stu-id="21f5d-123">Double</span></span>](../../../language-reference/data-types/double-data-type.md) | <span data-ttu-id="21f5d-124">D</span><span class="sxs-lookup"><span data-stu-id="21f5d-124">D</span></span> |
| <xref:System.Single?displayProperty=nameWithType> | [<span data-ttu-id="21f5d-125">Tek</span><span class="sxs-lookup"><span data-stu-id="21f5d-125">Single</span></span>](../../../language-reference/data-types/single-data-type.md) | <span data-ttu-id="21f5d-126">F</span><span class="sxs-lookup"><span data-stu-id="21f5d-126">F</span></span> |
| <xref:System.Decimal?displayProperty=nameWithType> | [<span data-ttu-id="21f5d-127">Kategori</span><span class="sxs-lookup"><span data-stu-id="21f5d-127">Decimal</span></span>](../../../language-reference/data-types/decimal-data-type.md) | <span data-ttu-id="21f5d-128">M</span><span class="sxs-lookup"><span data-stu-id="21f5d-128">M</span></span> |

### <a name="examples"></a><span data-ttu-id="21f5d-129">Örnekler</span><span class="sxs-lookup"><span data-stu-id="21f5d-129">Examples</span></span>

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

## <a name="blockexpression"></a><span data-ttu-id="21f5d-130">Blok Ifadesi</span><span class="sxs-lookup"><span data-stu-id="21f5d-130">BlockExpression</span></span>

<span data-ttu-id="21f5d-131">Bir nesnenin türü, <xref:System.Linq.Expressions.BlockExpression> bloktaki son ifadenin türünden farklıysa, tür açılı ayraçlar ( `<` ve) içinde görüntülenir `>` .</span><span class="sxs-lookup"><span data-stu-id="21f5d-131">If the type of a <xref:System.Linq.Expressions.BlockExpression> object differs from the type of the last expression in the block, the type is displayed within angle brackets (`<` and `>`).</span></span> <span data-ttu-id="21f5d-132">Aksi takdirde, <xref:System.Linq.Expressions.BlockExpression> nesne türü görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="21f5d-132">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>

### <a name="examples"></a><span data-ttu-id="21f5d-133">Örnekler</span><span class="sxs-lookup"><span data-stu-id="21f5d-133">Examples</span></span>

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

## <a name="lambdaexpression"></a><span data-ttu-id="21f5d-134">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="21f5d-134">LambdaExpression</span></span>

<span data-ttu-id="21f5d-135"><xref:System.Linq.Expressions.LambdaExpression> nesneler, temsilci türleriyle birlikte görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="21f5d-135"><xref:System.Linq.Expressions.LambdaExpression> objects are displayed together with their delegate types.</span></span>

<span data-ttu-id="21f5d-136">Lambda ifadesi bir ada sahip değilse, veya gibi otomatik olarak oluşturulan bir ad atanır `#Lambda1` `#Lambda2` .</span><span class="sxs-lookup"><span data-stu-id="21f5d-136">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>

### <a name="examples"></a><span data-ttu-id="21f5d-137">Örnekler</span><span class="sxs-lookup"><span data-stu-id="21f5d-137">Examples</span></span>

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

## <a name="labelexpression"></a><span data-ttu-id="21f5d-138">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="21f5d-138">LabelExpression</span></span>

<span data-ttu-id="21f5d-139">Nesne için varsayılan bir değer belirtirseniz <xref:System.Linq.Expressions.LabelExpression> , bu değer nesneden önce görüntülenir <xref:System.Linq.Expressions.LabelTarget> .</span><span class="sxs-lookup"><span data-stu-id="21f5d-139">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget> object.</span></span>

<span data-ttu-id="21f5d-140">`.Label`Belirteç, etiketin başlangıcını gösterir.</span><span class="sxs-lookup"><span data-stu-id="21f5d-140">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="21f5d-141">`.LabelTarget`Belirteç, atlanacak hedefin hedefini gösterir.</span><span class="sxs-lookup"><span data-stu-id="21f5d-141">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>

<span data-ttu-id="21f5d-142">Bir etiket bir ada sahip değilse, veya gibi otomatik olarak oluşturulan bir ad atanır `#Label1` `#Label2` .</span><span class="sxs-lookup"><span data-stu-id="21f5d-142">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>

### <a name="examples"></a><span data-ttu-id="21f5d-143">Örnekler</span><span class="sxs-lookup"><span data-stu-id="21f5d-143">Examples</span></span>

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

## <a name="checked-operators"></a><span data-ttu-id="21f5d-144">Denetlenen Işleçler</span><span class="sxs-lookup"><span data-stu-id="21f5d-144">Checked Operators</span></span>

<span data-ttu-id="21f5d-145">İşaretli işleçler, `#` işlecin önünde simgesiyle birlikte görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="21f5d-145">Checked operators are displayed with the `#` symbol in front of the operator.</span></span> <span data-ttu-id="21f5d-146">Örneğin, denetlenen toplama işleci olarak görüntülenir `#+` .</span><span class="sxs-lookup"><span data-stu-id="21f5d-146">For example, the checked addition operator is displayed as `#+`.</span></span>

### <a name="examples"></a><span data-ttu-id="21f5d-147">Örnekler</span><span class="sxs-lookup"><span data-stu-id="21f5d-147">Examples</span></span>

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
