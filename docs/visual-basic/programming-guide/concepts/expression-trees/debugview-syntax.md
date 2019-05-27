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
ms.openlocfilehash: 1b2a1164f02208cc7578820d8f8ed3bc145fb5b8
ms.sourcegitcommit: 96543603ae29bc05cecccb8667974d058af63b4a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66196072"
---
# <a name="debugview-syntax"></a><span data-ttu-id="0d120-103">`DebugView` Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="0d120-103">`DebugView` syntax</span></span> 

<span data-ttu-id="0d120-104">`DebugView` Özelliği (yalnızca hata ayıklama sırasında kullanılabilir) ifade ağaçları dize işlenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0d120-104">The `DebugView` property (available only when debugging) provides a string rendering of expression trees.</span></span> <span data-ttu-id="0d120-105">Çoğu söz dizimini anlamak oldukça açıktır; özel durumlar aşağıdaki bölümlerde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0d120-105">Most of the syntax is fairly straightforward to understand; the special cases are described in the following sections.</span></span>

<span data-ttu-id="0d120-106">Her örneğin bir açıklama bloğu içeren ardından `DebugView`.</span><span class="sxs-lookup"><span data-stu-id="0d120-106">Each example is followed by a comment block containing the `DebugView`.</span></span> 

## <a name="parameterexpression"></a><span data-ttu-id="0d120-107">ParameterExpression</span><span class="sxs-lookup"><span data-stu-id="0d120-107">ParameterExpression</span></span>

<span data-ttu-id="0d120-108"><xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> Değişken adlarının başında bir "$" simgesi ile görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0d120-108"><xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> variable names are displayed with a "$" symbol at the beginning.</span></span>

<span data-ttu-id="0d120-109">Parametre bir adı yoksa, otomatik olarak oluşturulmuş bir adı gibi atandıktan `$var1` veya `$var2`.</span><span class="sxs-lookup"><span data-stu-id="0d120-109">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>

### <a name="examples"></a><span data-ttu-id="0d120-110">Örnekler</span><span class="sxs-lookup"><span data-stu-id="0d120-110">Examples</span></span>

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

## <a name="constantexpressions"></a><span data-ttu-id="0d120-111">ConstantExpressions</span><span class="sxs-lookup"><span data-stu-id="0d120-111">ConstantExpressions</span></span>

<span data-ttu-id="0d120-112">İçin <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> dize, tamsayı değerlerini temsil eden nesneleri ve `null`, sabit değeri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0d120-112">For <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>

<span data-ttu-id="0d120-113">Bazı sayısal türleri için bir sonek değerine eklenir:</span><span class="sxs-lookup"><span data-stu-id="0d120-113">For some numeric types, a suffix is added to the value:</span></span>

| <span data-ttu-id="0d120-114">Tür</span><span class="sxs-lookup"><span data-stu-id="0d120-114">Type</span></span> | <span data-ttu-id="0d120-115">Anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="0d120-115">Keyword</span></span> | <span data-ttu-id="0d120-116">Son eki</span><span class="sxs-lookup"><span data-stu-id="0d120-116">Suffix</span></span> |  
|--|--|--|
| <xref:System.UInt32> | [<span data-ttu-id="0d120-117">Uınteger</span><span class="sxs-lookup"><span data-stu-id="0d120-117">UInteger</span></span>](../../../language-reference/data-types/uinteger-data-type.md) | <span data-ttu-id="0d120-118">U</span><span class="sxs-lookup"><span data-stu-id="0d120-118">U</span></span> |
| <xref:System.Int64> | [<span data-ttu-id="0d120-119">uzun</span><span class="sxs-lookup"><span data-stu-id="0d120-119">Long</span></span>](../../../language-reference/data-types/long-data-type.md) | <span data-ttu-id="0d120-120">L</span><span class="sxs-lookup"><span data-stu-id="0d120-120">L</span></span> |
| <xref:System.UInt64> | [<span data-ttu-id="0d120-121">ULong</span><span class="sxs-lookup"><span data-stu-id="0d120-121">ULong</span></span>](../../../language-reference/data-types/ulong-data-type.md) | <span data-ttu-id="0d120-122">UL</span><span class="sxs-lookup"><span data-stu-id="0d120-122">UL</span></span> |
| <xref:System.Double> | [<span data-ttu-id="0d120-123">çift</span><span class="sxs-lookup"><span data-stu-id="0d120-123">Double</span></span>](../../../language-reference/data-types/double-data-type.md) | <span data-ttu-id="0d120-124">D</span><span class="sxs-lookup"><span data-stu-id="0d120-124">D</span></span> |
| <xref:System.Single> | [<span data-ttu-id="0d120-125">Tek</span><span class="sxs-lookup"><span data-stu-id="0d120-125">Single</span></span>](../../../language-reference/data-types/single-data-type.md) | <span data-ttu-id="0d120-126">F</span><span class="sxs-lookup"><span data-stu-id="0d120-126">F</span></span> | 
| <xref:System.Decimal> | [<span data-ttu-id="0d120-127">Ondalık</span><span class="sxs-lookup"><span data-stu-id="0d120-127">Decimal</span></span>](../../../language-reference/data-types/decimal-data-type.md) | <span data-ttu-id="0d120-128">M</span><span class="sxs-lookup"><span data-stu-id="0d120-128">M</span></span> |

### <a name="examples"></a><span data-ttu-id="0d120-129">Örnekler</span><span class="sxs-lookup"><span data-stu-id="0d120-129">Examples</span></span>

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

## <a name="blockexpression"></a><span data-ttu-id="0d120-130">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="0d120-130">BlockExpression</span></span>

<span data-ttu-id="0d120-131">Varsa türünü bir <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> bloğundaki son ifadenin türü nesne farklıdır, açılı ayraçlar içinde türü görüntülenir (`<` ve `>`).</span><span class="sxs-lookup"><span data-stu-id="0d120-131">If the type of a <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> object differs from the type of the last expression in the block, the type is displayed within angle brackets (`<` and `>`).</span></span> <span data-ttu-id="0d120-132">Aksi halde, türünü <xref:System.Linq.Expressions.BlockExpression> nesne görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="0d120-132">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>

### <a name="examples"></a><span data-ttu-id="0d120-133">Örnekler</span><span class="sxs-lookup"><span data-stu-id="0d120-133">Examples</span></span>

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

## <a name="lambdaexpression"></a><span data-ttu-id="0d120-134">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="0d120-134">LambdaExpression</span></span>

<span data-ttu-id="0d120-135"><xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> nesneler, temsilci türleri ile birlikte görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0d120-135"><xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> objects are displayed together with their delegate types.</span></span>

<span data-ttu-id="0d120-136">Bir lambda ifadesi bir adı yoksa, otomatik olarak oluşturulmuş bir adı gibi atandıktan `#Lambda1` veya `#Lambda2`.</span><span class="sxs-lookup"><span data-stu-id="0d120-136">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>

### <a name="examples"></a><span data-ttu-id="0d120-137">Örnekler</span><span class="sxs-lookup"><span data-stu-id="0d120-137">Examples</span></span>

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

## <a name="labelexpression"></a><span data-ttu-id="0d120-138">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="0d120-138">LabelExpression</span></span>

<span data-ttu-id="0d120-139">İçin varsayılan bir değer belirtirseniz <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType> nesnesi, bu değer, önce görüntülenir <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType> nesne.</span><span class="sxs-lookup"><span data-stu-id="0d120-139">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType> object.</span></span>

<span data-ttu-id="0d120-140">`.Label` Belirteci etiketi başlangıcını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0d120-140">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="0d120-141">`.LabelTarget` Belirteci atlamak için hedef hedefinin gösterir.</span><span class="sxs-lookup"><span data-stu-id="0d120-141">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>

<span data-ttu-id="0d120-142">Bir etiket bir ad yoksa otomatik olarak oluşturulmuş bir adı gibi atandıktan `#Label1` veya `#Label2`.</span><span class="sxs-lookup"><span data-stu-id="0d120-142">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>

### <a name="examples"></a><span data-ttu-id="0d120-143">Örnekler</span><span class="sxs-lookup"><span data-stu-id="0d120-143">Examples</span></span>

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

## <a name="checked-operators"></a><span data-ttu-id="0d120-144">İşaretli işleçleri</span><span class="sxs-lookup"><span data-stu-id="0d120-144">Checked Operators</span></span>

<span data-ttu-id="0d120-145">İşaretli işleçleri ile görüntülenir `#` işleci önünde simge.</span><span class="sxs-lookup"><span data-stu-id="0d120-145">Checked operators are displayed with the `#` symbol in front of the operator.</span></span> <span data-ttu-id="0d120-146">Örneğin, işaretli Toplama işleci olarak görüntülenir `#+`.</span><span class="sxs-lookup"><span data-stu-id="0d120-146">For example, the checked addition operator is displayed as `#+`.</span></span>

### <a name="examples"></a><span data-ttu-id="0d120-147">Örnekler</span><span class="sxs-lookup"><span data-stu-id="0d120-147">Examples</span></span>

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