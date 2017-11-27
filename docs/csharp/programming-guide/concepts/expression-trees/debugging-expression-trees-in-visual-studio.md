---
title: "Visual Studio'da (C#) ifade ağaçlarında hata ayıklama"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
caps.latest.revision: "4"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d74df8ba339526e20850cd8b8f1a4b37c20e22ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a><span data-ttu-id="21553-102">Visual Studio'da (C#) ifade ağaçlarında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="21553-102">Debugging Expression Trees in Visual Studio (C#)</span></span>
<span data-ttu-id="21553-103">Uygulamalarınızda hata ayıklamak zaman ifade ağaçları içeriği ve yapısı analiz edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21553-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="21553-104">İfade ağaç yapısı hızlı bir genel bakış almak için kullanabileceğiniz `DebugView` özelliği yalnızca hata ayıklama modunda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="21553-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which is available only in debug mode.</span></span> <span data-ttu-id="21553-105">Hata ayıklama hakkında daha fazla bilgi için bkz: [Visual Studio'da hata ayıklamayı](/visualstudio/debugger/debugging-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="21553-105">For more information about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).</span></span>  
  
 <span data-ttu-id="21553-106">İfade ağaçları içeriğini daha iyi göstermek için `DebugView` özelliği Visual Studio görselleştiriciler kullanır.</span><span class="sxs-lookup"><span data-stu-id="21553-106">To better represent the content of expression trees, the `DebugView` property uses Visual Studio visualizers.</span></span> <span data-ttu-id="21553-107">Daha fazla bilgi için bkz: [oluşturma özel Görselleştiriciler](/visualstudio/debugger/create-custom-visualizers-of-data).</span><span class="sxs-lookup"><span data-stu-id="21553-107">For more information, see [Create Custom Visualizers](/visualstudio/debugger/create-custom-visualizers-of-data).</span></span>  
  
### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="21553-108">Bir ifade ağacına için Görselleştirici açmak için</span><span class="sxs-lookup"><span data-stu-id="21553-108">To open a visualizer for an expression tree</span></span>  
  
1.  <span data-ttu-id="21553-109">Yanında Büyüteç simgesini tıklatın `DebugView` bir ifade ağacına özelliğinin **DataTips**, **izleme** penceresinde **otomobiller** penceresinde veya **Yereller** penceresi.</span><span class="sxs-lookup"><span data-stu-id="21553-109">Click the magnifying glass icon that appears next to the `DebugView` property of an expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
     <span data-ttu-id="21553-110">Görselleştiriciler listesi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="21553-110">A list of visualizers is displayed.</span></span>  
  
2.  <span data-ttu-id="21553-111">Kullanmak istediğiniz Görselleştirici'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="21553-111">Click the visualizer you want to use.</span></span>  
  
 <span data-ttu-id="21553-112">Aşağıdaki bölümlerde açıklandığı gibi her bir ifade türü Görselleştirici görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="21553-112">Each expression type is displayed in the visualizer as described in the following sections.</span></span>  
  
## <a name="parameterexpressions"></a><span data-ttu-id="21553-113">ParameterExpressions</span><span class="sxs-lookup"><span data-stu-id="21553-113">ParameterExpressions</span></span>  
 <span data-ttu-id="21553-114"><xref:System.Linq.Expressions.ParameterExpression>değişken adları başında "$" simgesiyle görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="21553-114"><xref:System.Linq.Expressions.ParameterExpression> variable names are displayed with a "$" symbol at the beginning.</span></span>  
  
 <span data-ttu-id="21553-115">Bir parametre bir adı yoksa, otomatik olarak oluşturulan bir ad gibi atanmış olduğu `$var1` veya `$var2`.</span><span class="sxs-lookup"><span data-stu-id="21553-115">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="21553-116">Örnekler</span><span class="sxs-lookup"><span data-stu-id="21553-116">Examples</span></span>  
  
|<span data-ttu-id="21553-117">İfade</span><span class="sxs-lookup"><span data-stu-id="21553-117">Expression</span></span>|<span data-ttu-id="21553-118">`DebugView`özelliği</span><span class="sxs-lookup"><span data-stu-id="21553-118">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int), "num");`|`$num`|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int));`|`$var1`|  
  
## <a name="constantexpressions"></a><span data-ttu-id="21553-119">ConstantExpressions</span><span class="sxs-lookup"><span data-stu-id="21553-119">ConstantExpressions</span></span>  
 <span data-ttu-id="21553-120">İçin <xref:System.Linq.Expressions.ConstantExpression> dize, tamsayı değerleri temsil eden nesneler ve `null`, sabit değeri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="21553-120">For <xref:System.Linq.Expressions.ConstantExpression> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>  
  
 <span data-ttu-id="21553-121">C# değişmez değerler olarak standart sonekleri sayısal türleri için sonek değerine eklenir.</span><span class="sxs-lookup"><span data-stu-id="21553-121">For numeric types that have standard suffixes as C# literals, the suffix is added to the value.</span></span> <span data-ttu-id="21553-122">Aşağıdaki tabloda, çeşitli sayısal türler ile ilişkili soneklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="21553-122">The following table shows the suffixes associated with various numeric types.</span></span>  
  
|<span data-ttu-id="21553-123">Tür</span><span class="sxs-lookup"><span data-stu-id="21553-123">Type</span></span>|<span data-ttu-id="21553-124">Son eki</span><span class="sxs-lookup"><span data-stu-id="21553-124">Suffix</span></span>|  
|----------|------------|  
|<xref:System.UInt32>|<span data-ttu-id="21553-125">U</span><span class="sxs-lookup"><span data-stu-id="21553-125">U</span></span>|  
|<xref:System.Int64>|<span data-ttu-id="21553-126">L</span><span class="sxs-lookup"><span data-stu-id="21553-126">L</span></span>|  
|<xref:System.UInt64>|<span data-ttu-id="21553-127">UL</span><span class="sxs-lookup"><span data-stu-id="21553-127">UL</span></span>|  
|<xref:System.Double>|<span data-ttu-id="21553-128">D</span><span class="sxs-lookup"><span data-stu-id="21553-128">D</span></span>|  
|<xref:System.Single>|<span data-ttu-id="21553-129">F</span><span class="sxs-lookup"><span data-stu-id="21553-129">F</span></span>|  
|<xref:System.Decimal>|<span data-ttu-id="21553-130">M</span><span class="sxs-lookup"><span data-stu-id="21553-130">M</span></span>|  
  
### <a name="examples"></a><span data-ttu-id="21553-131">Örnekler</span><span class="sxs-lookup"><span data-stu-id="21553-131">Examples</span></span>  
  
|<span data-ttu-id="21553-132">İfade</span><span class="sxs-lookup"><span data-stu-id="21553-132">Expression</span></span>|<span data-ttu-id="21553-133">`DebugView`özelliği</span><span class="sxs-lookup"><span data-stu-id="21553-133">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`int num = 10; ConstantExpression expr = Expression.Constant(num);`|<span data-ttu-id="21553-134">10</span><span class="sxs-lookup"><span data-stu-id="21553-134">10</span></span>|  
|`double num = 10; ConstantExpression expr = Expression.Constant(num);`|<span data-ttu-id="21553-135">10D</span><span class="sxs-lookup"><span data-stu-id="21553-135">10D</span></span>|  
  
## <a name="blockexpression"></a><span data-ttu-id="21553-136">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="21553-136">BlockExpression</span></span>  
 <span data-ttu-id="21553-137">Varsa türü bir <xref:System.Linq.Expressions.BlockExpression> bloğundaki son ifade türü farklıdır nesne, türü görüntülenir `DebugInfo` köşeli özelliğinde (\< ve >).</span><span class="sxs-lookup"><span data-stu-id="21553-137">If the type of a <xref:System.Linq.Expressions.BlockExpression> object differs from the type of the last expression in the block, the type is displayed in the `DebugInfo` property in angle brackets (\< and >).</span></span> <span data-ttu-id="21553-138">Aksi takdirde türünü <xref:System.Linq.Expressions.BlockExpression> nesnesi görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="21553-138">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="21553-139">Örnekler</span><span class="sxs-lookup"><span data-stu-id="21553-139">Examples</span></span>  
  
|<span data-ttu-id="21553-140">İfade</span><span class="sxs-lookup"><span data-stu-id="21553-140">Expression</span></span>|<span data-ttu-id="21553-141">`DebugView`özelliği</span><span class="sxs-lookup"><span data-stu-id="21553-141">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`BlockExpression block = Expression.Block(Expression.Constant("test"));`|`.Block() {`<br /><br /> `"test"`<br /><br /> `}`|  
|`BlockExpression block =  Expression.Block(typeof(Object), Expression.Constant("test"));`|`.Block<System.Object>() {`<br /><br /> `"test"`<br /><br /> `}`|  
  
## <a name="lambdaexpression"></a><span data-ttu-id="21553-142">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="21553-142">LambdaExpression</span></span>  
 <span data-ttu-id="21553-143"><xref:System.Linq.Expressions.LambdaExpression>nesneler kendi temsilci türleri ile birlikte görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="21553-143"><xref:System.Linq.Expressions.LambdaExpression> objects are displayed together with their delegate types.</span></span>  
  
 <span data-ttu-id="21553-144">Lambda ifadesi bir adı yoksa, otomatik olarak oluşturulan bir ad gibi atanmış olduğu `#Lambda1` veya `#Lambda2`.</span><span class="sxs-lookup"><span data-stu-id="21553-144">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="21553-145">Örnekler</span><span class="sxs-lookup"><span data-stu-id="21553-145">Examples</span></span>  
  
|<span data-ttu-id="21553-146">İfade</span><span class="sxs-lookup"><span data-stu-id="21553-146">Expression</span></span>|<span data-ttu-id="21553-147">`DebugView`özelliği</span><span class="sxs-lookup"><span data-stu-id="21553-147">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1));`|`.Lambda #Lambda1<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1), "SampleLambda", null);`|`.Lambda SampleLambda<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
  
## <a name="labelexpression"></a><span data-ttu-id="21553-148">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="21553-148">LabelExpression</span></span>  
 <span data-ttu-id="21553-149">İçin varsayılan bir değer belirtirseniz, <xref:System.Linq.Expressions.LabelExpression> nesnesi, bu değer, önce görüntülenir <xref:System.Linq.Expressions.LabelTarget> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="21553-149">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget> object.</span></span>  
  
 <span data-ttu-id="21553-150">`.Label` Belirteci etiketi başlangıcını gösterir.</span><span class="sxs-lookup"><span data-stu-id="21553-150">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="21553-151">`.LabelTarget` Belirteci atlamak için hedef hedef gösterir.</span><span class="sxs-lookup"><span data-stu-id="21553-151">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>  
  
 <span data-ttu-id="21553-152">Bir etiket bir adı yoksa, otomatik olarak oluşturulan bir ad gibi atanmış olduğu `#Label1` veya `#Label2`.</span><span class="sxs-lookup"><span data-stu-id="21553-152">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="21553-153">Örnekler</span><span class="sxs-lookup"><span data-stu-id="21553-153">Examples</span></span>  
  
|<span data-ttu-id="21553-154">İfade</span><span class="sxs-lookup"><span data-stu-id="21553-154">Expression</span></span>|<span data-ttu-id="21553-155">`DebugView`özelliği</span><span class="sxs-lookup"><span data-stu-id="21553-155">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`LabelTarget target = Expression.Label(typeof(int), "SampleLabel"); BlockExpression block = Expression.Block( Expression.Goto(target, Expression.Constant(0)), Expression.Label(target, Expression.Constant(-1)));`|`.Block() {`<br /><br /> `.Goto SampleLabel { 0 };`<br /><br /> `.Label`<br /><br /> `-1`<br /><br /> `.LabelTarget SampleLabel:`<br /><br /> `}`|  
|`LabelTarget target = Expression.Label(); BlockExpression block = Expression.Block( Expression.Goto(target5), Expression.Label(target5));`|`.Block() {`<br /><br /> `.Goto #Label1 { };`<br /><br /> `.Label`<br /><br /> `.LabelTarget #Label1:`<br /><br /> `}`|  
  
## <a name="checked-operators"></a><span data-ttu-id="21553-156">Checked işleçleri</span><span class="sxs-lookup"><span data-stu-id="21553-156">Checked Operators</span></span>  
 <span data-ttu-id="21553-157">Checked işleçleri işleci önünde "#" simgesiyle gösterilir.</span><span class="sxs-lookup"><span data-stu-id="21553-157">Checked operators are displayed with the "#" symbol in front of the operator.</span></span> <span data-ttu-id="21553-158">Örneğin, denetlenen Toplama işleci olarak görüntülenir `#+`.</span><span class="sxs-lookup"><span data-stu-id="21553-158">For example, the checked addition operator is displayed as `#+`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="21553-159">Örnekler</span><span class="sxs-lookup"><span data-stu-id="21553-159">Examples</span></span>  
  
|<span data-ttu-id="21553-160">İfade</span><span class="sxs-lookup"><span data-stu-id="21553-160">Expression</span></span>|<span data-ttu-id="21553-161">`DebugView`özelliği</span><span class="sxs-lookup"><span data-stu-id="21553-161">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`Expression expr = Expression.AddChecked( Expression.Constant(1), Expression.Constant(2));`|`1 #+ 2`|  
|`Expression expr = Expression.ConvertChecked( Expression.Constant(10.0), typeof(int));`|`#(System.Int32)10D`|  
  
## <a name="see-also"></a><span data-ttu-id="21553-162">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="21553-162">See Also</span></span>  
 [<span data-ttu-id="21553-163">İfade ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="21553-163">Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
 [<span data-ttu-id="21553-164">Visual Studio'da hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="21553-164">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)  
 [<span data-ttu-id="21553-165">Özel Görselleştiriciler oluşturma</span><span class="sxs-lookup"><span data-stu-id="21553-165">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
