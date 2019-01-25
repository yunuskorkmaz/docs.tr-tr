---
title: Visual Studio'da (C#) ifade ağaçlarında hata ayıklama
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: 308b377af00a3d12523f8f8d469c50808f216030
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632159"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a><span data-ttu-id="d8709-102">Visual Studio'da (C#) ifade ağaçlarında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="d8709-102">Debugging Expression Trees in Visual Studio (C#)</span></span>
<span data-ttu-id="d8709-103">Uygulamalarınızın hata ayıklaması yaparken, yapısı ve içeriği ifade ağaçları analiz edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8709-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="d8709-104">İfade ağaç yapısı hızlı bir genel bakış edinmek için kullanabileceğiniz `DebugView` özelliği yalnızca hata ayıklama modunda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d8709-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which is available only in debug mode.</span></span> <span data-ttu-id="d8709-105">Hata ayıklama hakkında daha fazla bilgi için bkz. [Visual Studio'da hata ayıklama](/visualstudio/debugger/debugging-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="d8709-105">For more information about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).</span></span>  
  
 <span data-ttu-id="d8709-106">Daha iyi ifade ağaçları içeriğini temsil etmek için `DebugView` özelliği, Visual Studio görselleştiriciler kullanır.</span><span class="sxs-lookup"><span data-stu-id="d8709-106">To better represent the content of expression trees, the `DebugView` property uses Visual Studio visualizers.</span></span> <span data-ttu-id="d8709-107">Daha fazla bilgi için [oluşturma özel Görselleştiriciler](/visualstudio/debugger/create-custom-visualizers-of-data).</span><span class="sxs-lookup"><span data-stu-id="d8709-107">For more information, see [Create Custom Visualizers](/visualstudio/debugger/create-custom-visualizers-of-data).</span></span>  
  
### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="d8709-108">İfade ağacı bir görselleştiriciyi açmak için</span><span class="sxs-lookup"><span data-stu-id="d8709-108">To open a visualizer for an expression tree</span></span>  
  
1.  <span data-ttu-id="d8709-109">Yanında görünen Büyüteç simgesine tıklayarak `DebugView` özelliğine bir ifade ağacında **DataTips**, **izleme** penceresinde **Otolar** penceresinde veya **Yereller** penceresi.</span><span class="sxs-lookup"><span data-stu-id="d8709-109">Click the magnifying glass icon that appears next to the `DebugView` property of an expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
     <span data-ttu-id="d8709-110">Görselleştiriciler listesi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d8709-110">A list of visualizers is displayed.</span></span>  
  
2.  <span data-ttu-id="d8709-111">Kullanmak istediğiniz Görselleştirici'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d8709-111">Click the visualizer you want to use.</span></span>  
  
 <span data-ttu-id="d8709-112">Aşağıdaki bölümlerde açıklandığı gibi her ifade türü görselleştiricisi içinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d8709-112">Each expression type is displayed in the visualizer as described in the following sections.</span></span>  
  
## <a name="parameterexpressions"></a><span data-ttu-id="d8709-113">ParameterExpressions</span><span class="sxs-lookup"><span data-stu-id="d8709-113">ParameterExpressions</span></span>  
 <span data-ttu-id="d8709-114"><xref:System.Linq.Expressions.ParameterExpression> Değişken adlarının başında bir "$" simgesi ile görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d8709-114"><xref:System.Linq.Expressions.ParameterExpression> variable names are displayed with a "$" symbol at the beginning.</span></span>  
  
 <span data-ttu-id="d8709-115">Parametre bir adı yoksa, otomatik olarak oluşturulmuş bir adı gibi atandıktan `$var1` veya `$var2`.</span><span class="sxs-lookup"><span data-stu-id="d8709-115">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="d8709-116">Örnekler</span><span class="sxs-lookup"><span data-stu-id="d8709-116">Examples</span></span>  
  
|<span data-ttu-id="d8709-117">İfade</span><span class="sxs-lookup"><span data-stu-id="d8709-117">Expression</span></span>|<span data-ttu-id="d8709-118">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="d8709-118">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int), "num");`|`$num`|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int));`|`$var1`|  
  
## <a name="constantexpressions"></a><span data-ttu-id="d8709-119">ConstantExpressions</span><span class="sxs-lookup"><span data-stu-id="d8709-119">ConstantExpressions</span></span>  
 <span data-ttu-id="d8709-120">İçin <xref:System.Linq.Expressions.ConstantExpression> dize, tamsayı değerlerini temsil eden nesneleri ve `null`, sabit değeri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d8709-120">For <xref:System.Linq.Expressions.ConstantExpression> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>  
  
 <span data-ttu-id="d8709-121">C# sabit değer olarak standart sonekleri olan sayısal türleri için sonek değerine eklenir.</span><span class="sxs-lookup"><span data-stu-id="d8709-121">For numeric types that have standard suffixes as C# literals, the suffix is added to the value.</span></span> <span data-ttu-id="d8709-122">Aşağıdaki tabloda, çeşitli sayısal türler ile ilişkili soneklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d8709-122">The following table shows the suffixes associated with various numeric types.</span></span>  
  
|<span data-ttu-id="d8709-123">Tür</span><span class="sxs-lookup"><span data-stu-id="d8709-123">Type</span></span>|<span data-ttu-id="d8709-124">Son eki</span><span class="sxs-lookup"><span data-stu-id="d8709-124">Suffix</span></span>|  
|----------|------------|  
|<xref:System.UInt32>|<span data-ttu-id="d8709-125">U</span><span class="sxs-lookup"><span data-stu-id="d8709-125">U</span></span>|  
|<xref:System.Int64>|<span data-ttu-id="d8709-126">L</span><span class="sxs-lookup"><span data-stu-id="d8709-126">L</span></span>|  
|<xref:System.UInt64>|<span data-ttu-id="d8709-127">UL</span><span class="sxs-lookup"><span data-stu-id="d8709-127">UL</span></span>|  
|<xref:System.Double>|<span data-ttu-id="d8709-128">D</span><span class="sxs-lookup"><span data-stu-id="d8709-128">D</span></span>|  
|<xref:System.Single>|<span data-ttu-id="d8709-129">F</span><span class="sxs-lookup"><span data-stu-id="d8709-129">F</span></span>|  
|<xref:System.Decimal>|<span data-ttu-id="d8709-130">M</span><span class="sxs-lookup"><span data-stu-id="d8709-130">M</span></span>|  
  
### <a name="examples"></a><span data-ttu-id="d8709-131">Örnekler</span><span class="sxs-lookup"><span data-stu-id="d8709-131">Examples</span></span>  
  
|<span data-ttu-id="d8709-132">İfade</span><span class="sxs-lookup"><span data-stu-id="d8709-132">Expression</span></span>|<span data-ttu-id="d8709-133">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="d8709-133">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`int num = 10; ConstantExpression expr = Expression.Constant(num);`|<span data-ttu-id="d8709-134">10</span><span class="sxs-lookup"><span data-stu-id="d8709-134">10</span></span>|  
|`double num = 10; ConstantExpression expr = Expression.Constant(num);`|<span data-ttu-id="d8709-135">10D</span><span class="sxs-lookup"><span data-stu-id="d8709-135">10D</span></span>|  
  
## <a name="blockexpression"></a><span data-ttu-id="d8709-136">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="d8709-136">BlockExpression</span></span>  
 <span data-ttu-id="d8709-137">Varsa türünü bir <xref:System.Linq.Expressions.BlockExpression> bloğundaki son ifadenin türü nesne farklıdır, türü görüntülenen `DebugInfo` açılı ayraçlar özelliğinde (\< ve >).</span><span class="sxs-lookup"><span data-stu-id="d8709-137">If the type of a <xref:System.Linq.Expressions.BlockExpression> object differs from the type of the last expression in the block, the type is displayed in the `DebugInfo` property in angle brackets (\< and >).</span></span> <span data-ttu-id="d8709-138">Aksi halde, türünü <xref:System.Linq.Expressions.BlockExpression> nesne görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="d8709-138">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="d8709-139">Örnekler</span><span class="sxs-lookup"><span data-stu-id="d8709-139">Examples</span></span>  
  
|<span data-ttu-id="d8709-140">İfade</span><span class="sxs-lookup"><span data-stu-id="d8709-140">Expression</span></span>|<span data-ttu-id="d8709-141">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="d8709-141">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`BlockExpression block = Expression.Block(Expression.Constant("test"));`|`.Block() {`<br /><br /> `"test"`<br /><br /> `}`|  
|`BlockExpression block =  Expression.Block(typeof(Object), Expression.Constant("test"));`|`.Block<System.Object>() {`<br /><br /> `"test"`<br /><br /> `}`|  
  
## <a name="lambdaexpression"></a><span data-ttu-id="d8709-142">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="d8709-142">LambdaExpression</span></span>  
 <span data-ttu-id="d8709-143"><xref:System.Linq.Expressions.LambdaExpression> nesneler, temsilci türleri ile birlikte görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d8709-143"><xref:System.Linq.Expressions.LambdaExpression> objects are displayed together with their delegate types.</span></span>  
  
 <span data-ttu-id="d8709-144">Bir lambda ifadesi bir adı yoksa, otomatik olarak oluşturulmuş bir adı gibi atandıktan `#Lambda1` veya `#Lambda2`.</span><span class="sxs-lookup"><span data-stu-id="d8709-144">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="d8709-145">Örnekler</span><span class="sxs-lookup"><span data-stu-id="d8709-145">Examples</span></span>  
  
|<span data-ttu-id="d8709-146">İfade</span><span class="sxs-lookup"><span data-stu-id="d8709-146">Expression</span></span>|<span data-ttu-id="d8709-147">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="d8709-147">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1));`|`.Lambda #Lambda1<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1), "SampleLambda", null);`|`.Lambda SampleLambda<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
  
## <a name="labelexpression"></a><span data-ttu-id="d8709-148">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="d8709-148">LabelExpression</span></span>  
 <span data-ttu-id="d8709-149">İçin varsayılan bir değer belirtirseniz <xref:System.Linq.Expressions.LabelExpression> nesnesi, bu değer, önce görüntülenir <xref:System.Linq.Expressions.LabelTarget> nesne.</span><span class="sxs-lookup"><span data-stu-id="d8709-149">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget> object.</span></span>  
  
 <span data-ttu-id="d8709-150">`.Label` Belirteci etiketi başlangıcını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d8709-150">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="d8709-151">`.LabelTarget` Belirteci atlamak için hedef hedefinin gösterir.</span><span class="sxs-lookup"><span data-stu-id="d8709-151">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>  
  
 <span data-ttu-id="d8709-152">Bir etiket bir ad yoksa otomatik olarak oluşturulmuş bir adı gibi atandıktan `#Label1` veya `#Label2`.</span><span class="sxs-lookup"><span data-stu-id="d8709-152">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="d8709-153">Örnekler</span><span class="sxs-lookup"><span data-stu-id="d8709-153">Examples</span></span>  
  
|<span data-ttu-id="d8709-154">İfade</span><span class="sxs-lookup"><span data-stu-id="d8709-154">Expression</span></span>|<span data-ttu-id="d8709-155">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="d8709-155">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`LabelTarget target = Expression.Label(typeof(int), "SampleLabel"); BlockExpression block = Expression.Block( Expression.Goto(target, Expression.Constant(0)), Expression.Label(target, Expression.Constant(-1)));`|`.Block() {`<br /><br /> `.Goto SampleLabel { 0 };`<br /><br /> `.Label`<br /><br /> `-1`<br /><br /> `.LabelTarget SampleLabel:`<br /><br /> `}`|  
|`LabelTarget target = Expression.Label(); BlockExpression block = Expression.Block( Expression.Goto(target5), Expression.Label(target5));`|`.Block() {`<br /><br /> `.Goto #Label1 { };`<br /><br /> `.Label`<br /><br /> `.LabelTarget #Label1:`<br /><br /> `}`|  
  
## <a name="checked-operators"></a><span data-ttu-id="d8709-156">İşaretli işleçleri</span><span class="sxs-lookup"><span data-stu-id="d8709-156">Checked Operators</span></span>  
 <span data-ttu-id="d8709-157">İşaretli işleçler, işlecin önüne "#" sembolü ile görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d8709-157">Checked operators are displayed with the "#" symbol in front of the operator.</span></span> <span data-ttu-id="d8709-158">Örneğin, işaretli Toplama işleci olarak görüntülenir `#+`.</span><span class="sxs-lookup"><span data-stu-id="d8709-158">For example, the checked addition operator is displayed as `#+`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="d8709-159">Örnekler</span><span class="sxs-lookup"><span data-stu-id="d8709-159">Examples</span></span>  
  
|<span data-ttu-id="d8709-160">İfade</span><span class="sxs-lookup"><span data-stu-id="d8709-160">Expression</span></span>|<span data-ttu-id="d8709-161">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="d8709-161">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`Expression expr = Expression.AddChecked( Expression.Constant(1), Expression.Constant(2));`|`1 #+ 2`|  
|`Expression expr = Expression.ConvertChecked( Expression.Constant(10.0), typeof(int));`|`#(System.Int32)10D`|  
  
## <a name="see-also"></a><span data-ttu-id="d8709-162">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8709-162">See also</span></span>

- [<span data-ttu-id="d8709-163">İfade ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="d8709-163">Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="d8709-164">Visual Studio’da hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="d8709-164">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)
- [<span data-ttu-id="d8709-165">Özel Görselleştirici Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d8709-165">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
