---
title: Visual Studio'da (C#) ifade ağaçlarında hata ayıklama
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: 4017e2c2592dc1d6067b428fc1d47f37775abf85
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877117"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a><span data-ttu-id="b5e1c-102">Visual Studio'da (C#) ifade ağaçlarında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="b5e1c-102">Debugging Expression Trees in Visual Studio (C#)</span></span>
<span data-ttu-id="b5e1c-103">Uygulamalarınızın hata ayıklaması yaparken, yapısı ve içeriği ifade ağaçları analiz edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5e1c-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="b5e1c-104">İfade ağaç yapısı hızlı bir genel bakış edinmek için kullanabileceğiniz `DebugView` açıklanan özel bir söz dizimi kullanılarak ifade ağaçları temsil eden özellik [aşağıda](#debugview-syntax).</span><span class="sxs-lookup"><span data-stu-id="b5e1c-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which represents expression trees using a special syntax described [below](#debugview-syntax).</span></span> <span data-ttu-id="b5e1c-105">(Unutmayın `DebugView` yalnızca hata ayıklama modunda kullanılabilir.)</span><span class="sxs-lookup"><span data-stu-id="b5e1c-105">(Note that `DebugView` is available only in debug mode.)</span></span>  

![DebugView Visual Studio hata ayıklayıcısı içinde ifade ağacı](media/debugging-expression-trees-in-visual-studio/debugview.png)

<span data-ttu-id="b5e1c-107">Bu yana `DebugView` bir dize ise kullanabilirsiniz [yerleşik metin Görselleştiriciye](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) seçerek birden çok satırda, görüntülemek için **metin görselleştiricisi** Büyüteç simgesinin yanındaki gelen `DebugView` Etiket.</span><span class="sxs-lookup"><span data-stu-id="b5e1c-107">Since `DebugView` is a string, you can use the [built-in Text Visualizer](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) to view it across multiple lines, by selecting **Text Visualizer** from the magnifying glass icon next to the `DebugView` label.</span></span>

 ![Metin Görselleştirici 'DebugView' sonuçlarına uygulandı](media/debugging-expression-trees-in-visual-studio/string_visualizer.png)

<span data-ttu-id="b5e1c-109">Alternatif olarak, yükleyip kullanabilir [özel Görselleştirici](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) için ifade ağaçları:</span><span class="sxs-lookup"><span data-stu-id="b5e1c-109">Alternatively, you can install and use [a custom visualizer](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) for expression trees:</span></span>

* <span data-ttu-id="b5e1c-110">[Okunabilir ifadeleri](https://github.com/agileobjects/ReadableExpressions) ([MIT lisansı](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), kullanılabilir [Visual Studio Market](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), işler ifade ağacı C# kod:</span><span class="sxs-lookup"><span data-stu-id="b5e1c-110">[Readable Expressions](https://github.com/agileobjects/ReadableExpressions) ([MIT license](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), available at the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renders the expression tree as C# code:</span></span>

  ![Okunabilir ifadeleri görselleştiricisi](media/debugging-expression-trees-in-visual-studio/readable_expressions_visualizer.png)

* <span data-ttu-id="b5e1c-112">[İfade ağacı Görselleştiricisini](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([MIT lisansı](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), ifade ağacı, özelliklerini, grafik bir görünümünü sağlar ve ilgili nesneleri:</span><span class="sxs-lookup"><span data-stu-id="b5e1c-112">[Expression Tree Visualizer](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([MIT license](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), provides a graphical view of the expression tree, its properties, and related objects:</span></span>

  ![ExpressionToString Görselleştirici](media/debugging-expression-trees-in-visual-studio/expression_to_string_visualizer.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="b5e1c-114">İfade ağacı bir görselleştiriciyi açmak için</span><span class="sxs-lookup"><span data-stu-id="b5e1c-114">To open a visualizer for an expression tree</span></span>  
  
1. <span data-ttu-id="b5e1c-115">İfade ağacında yanında Büyüteç simgesine tıklayarak **DataTips**, **Watch** penceresinde **Otolar** penceresinde veya **Yereller** penceresi.</span><span class="sxs-lookup"><span data-stu-id="b5e1c-115">Click the magnifying glass icon that appears next to the expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
     <span data-ttu-id="b5e1c-116">Kullanılabilir görselleştiriciler listesi görüntülenir.:</span><span class="sxs-lookup"><span data-stu-id="b5e1c-116">A list of available visualizers is displayed.:</span></span> 

      ![Visual Studio'dan açılış görselleştiriciler](media/debugging-expression-trees-in-visual-studio/expression_tree_visualizers.png)

2. <span data-ttu-id="b5e1c-118">Kullanmak istediğiniz Görselleştirici'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b5e1c-118">Click the visualizer you want to use.</span></span>  

## <a name="debugview-syntax"></a><span data-ttu-id="b5e1c-119">`DebugView` Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b5e1c-119">`DebugView` syntax</span></span> 

<span data-ttu-id="b5e1c-120">Her deyim türü tarafından görüntülenen `DebugView` aşağıdaki bölümlerde açıklandığı gibi özellik.</span><span class="sxs-lookup"><span data-stu-id="b5e1c-120">Each expression type is displayed by the `DebugView` property as described in the following sections.</span></span>  
  
## <a name="parameterexpressions"></a><span data-ttu-id="b5e1c-121">ParameterExpressions</span><span class="sxs-lookup"><span data-stu-id="b5e1c-121">ParameterExpressions</span></span>  
 <span data-ttu-id="b5e1c-122"><xref:System.Linq.Expressions.ParameterExpression> Değişken adlarının başında bir "$" simgesi ile görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b5e1c-122"><xref:System.Linq.Expressions.ParameterExpression> variable names are displayed with a "$" symbol at the beginning.</span></span>  
  
 <span data-ttu-id="b5e1c-123">Parametre bir adı yoksa, otomatik olarak oluşturulmuş bir adı gibi atandıktan `$var1` veya `$var2`.</span><span class="sxs-lookup"><span data-stu-id="b5e1c-123">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="b5e1c-124">Örnekler</span><span class="sxs-lookup"><span data-stu-id="b5e1c-124">Examples</span></span>  
  
|<span data-ttu-id="b5e1c-125">İfade</span><span class="sxs-lookup"><span data-stu-id="b5e1c-125">Expression</span></span>|<span data-ttu-id="b5e1c-126">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="b5e1c-126">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int), "num");`|`$num`|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int));`|`$var1`|  
  
## <a name="constantexpressions"></a><span data-ttu-id="b5e1c-127">ConstantExpressions</span><span class="sxs-lookup"><span data-stu-id="b5e1c-127">ConstantExpressions</span></span>  
 <span data-ttu-id="b5e1c-128">İçin <xref:System.Linq.Expressions.ConstantExpression> dize, tamsayı değerlerini temsil eden nesneleri ve `null`, sabit değeri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b5e1c-128">For <xref:System.Linq.Expressions.ConstantExpression> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>  
  
 <span data-ttu-id="b5e1c-129">C# sabit değer olarak standart sonekleri olan sayısal türleri için sonek değerine eklenir.</span><span class="sxs-lookup"><span data-stu-id="b5e1c-129">For numeric types that have standard suffixes as C# literals, the suffix is added to the value.</span></span> <span data-ttu-id="b5e1c-130">Aşağıdaki tabloda, çeşitli sayısal türler ile ilişkili soneklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b5e1c-130">The following table shows the suffixes associated with various numeric types.</span></span>  
  
|<span data-ttu-id="b5e1c-131">Tür</span><span class="sxs-lookup"><span data-stu-id="b5e1c-131">Type</span></span>|<span data-ttu-id="b5e1c-132">Son eki</span><span class="sxs-lookup"><span data-stu-id="b5e1c-132">Suffix</span></span>|  
|----------|------------|  
|<xref:System.UInt32>|<span data-ttu-id="b5e1c-133">U</span><span class="sxs-lookup"><span data-stu-id="b5e1c-133">U</span></span>|  
|<xref:System.Int64>|<span data-ttu-id="b5e1c-134">L</span><span class="sxs-lookup"><span data-stu-id="b5e1c-134">L</span></span>|  
|<xref:System.UInt64>|<span data-ttu-id="b5e1c-135">UL</span><span class="sxs-lookup"><span data-stu-id="b5e1c-135">UL</span></span>|  
|<xref:System.Double>|<span data-ttu-id="b5e1c-136">D</span><span class="sxs-lookup"><span data-stu-id="b5e1c-136">D</span></span>|  
|<xref:System.Single>|<span data-ttu-id="b5e1c-137">F</span><span class="sxs-lookup"><span data-stu-id="b5e1c-137">F</span></span>|  
|<xref:System.Decimal>|<span data-ttu-id="b5e1c-138">M</span><span class="sxs-lookup"><span data-stu-id="b5e1c-138">M</span></span>|  
  
### <a name="examples"></a><span data-ttu-id="b5e1c-139">Örnekler</span><span class="sxs-lookup"><span data-stu-id="b5e1c-139">Examples</span></span>  
  
|<span data-ttu-id="b5e1c-140">İfade</span><span class="sxs-lookup"><span data-stu-id="b5e1c-140">Expression</span></span>|<span data-ttu-id="b5e1c-141">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="b5e1c-141">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`int num = 10; ConstantExpression expr = Expression.Constant(num);`|<span data-ttu-id="b5e1c-142">10</span><span class="sxs-lookup"><span data-stu-id="b5e1c-142">10</span></span>|  
|`double num = 10; ConstantExpression expr = Expression.Constant(num);`|<span data-ttu-id="b5e1c-143">10D</span><span class="sxs-lookup"><span data-stu-id="b5e1c-143">10D</span></span>|  
  
## <a name="blockexpression"></a><span data-ttu-id="b5e1c-144">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="b5e1c-144">BlockExpression</span></span>  
 <span data-ttu-id="b5e1c-145">Varsa türünü bir <xref:System.Linq.Expressions.BlockExpression> bloğundaki son ifadenin türü nesne farklıdır, türü görüntülenen `DebugInfo` açılı ayraçlar özelliğinde (\< ve >).</span><span class="sxs-lookup"><span data-stu-id="b5e1c-145">If the type of a <xref:System.Linq.Expressions.BlockExpression> object differs from the type of the last expression in the block, the type is displayed in the `DebugInfo` property in angle brackets (\< and >).</span></span> <span data-ttu-id="b5e1c-146">Aksi halde, türünü <xref:System.Linq.Expressions.BlockExpression> nesne görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="b5e1c-146">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="b5e1c-147">Örnekler</span><span class="sxs-lookup"><span data-stu-id="b5e1c-147">Examples</span></span>  
  
|<span data-ttu-id="b5e1c-148">İfade</span><span class="sxs-lookup"><span data-stu-id="b5e1c-148">Expression</span></span>|<span data-ttu-id="b5e1c-149">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="b5e1c-149">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`BlockExpression block = Expression.Block(Expression.Constant("test"));`|`.Block() {`<br /><br /> `"test"`<br /><br /> `}`|  
|`BlockExpression block =  Expression.Block(typeof(Object), Expression.Constant("test"));`|`.Block<System.Object>() {`<br /><br /> `"test"`<br /><br /> `}`|  
  
## <a name="lambdaexpression"></a><span data-ttu-id="b5e1c-150">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="b5e1c-150">LambdaExpression</span></span>  
 <span data-ttu-id="b5e1c-151"><xref:System.Linq.Expressions.LambdaExpression> nesneler, temsilci türleri ile birlikte görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b5e1c-151"><xref:System.Linq.Expressions.LambdaExpression> objects are displayed together with their delegate types.</span></span>  
  
 <span data-ttu-id="b5e1c-152">Bir lambda ifadesi bir adı yoksa, otomatik olarak oluşturulmuş bir adı gibi atandıktan `#Lambda1` veya `#Lambda2`.</span><span class="sxs-lookup"><span data-stu-id="b5e1c-152">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="b5e1c-153">Örnekler</span><span class="sxs-lookup"><span data-stu-id="b5e1c-153">Examples</span></span>  
  
|<span data-ttu-id="b5e1c-154">İfade</span><span class="sxs-lookup"><span data-stu-id="b5e1c-154">Expression</span></span>|<span data-ttu-id="b5e1c-155">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="b5e1c-155">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1));`|`.Lambda #Lambda1<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1), "SampleLambda", null);`|`.Lambda SampleLambda<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
  
## <a name="labelexpression"></a><span data-ttu-id="b5e1c-156">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="b5e1c-156">LabelExpression</span></span>  
 <span data-ttu-id="b5e1c-157">İçin varsayılan bir değer belirtirseniz <xref:System.Linq.Expressions.LabelExpression> nesnesi, bu değer, önce görüntülenir <xref:System.Linq.Expressions.LabelTarget> nesne.</span><span class="sxs-lookup"><span data-stu-id="b5e1c-157">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget> object.</span></span>  
  
 <span data-ttu-id="b5e1c-158">`.Label` Belirteci etiketi başlangıcını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b5e1c-158">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="b5e1c-159">`.LabelTarget` Belirteci atlamak için hedef hedefinin gösterir.</span><span class="sxs-lookup"><span data-stu-id="b5e1c-159">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>  
  
 <span data-ttu-id="b5e1c-160">Bir etiket bir ad yoksa otomatik olarak oluşturulmuş bir adı gibi atandıktan `#Label1` veya `#Label2`.</span><span class="sxs-lookup"><span data-stu-id="b5e1c-160">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="b5e1c-161">Örnekler</span><span class="sxs-lookup"><span data-stu-id="b5e1c-161">Examples</span></span>  
  
|<span data-ttu-id="b5e1c-162">İfade</span><span class="sxs-lookup"><span data-stu-id="b5e1c-162">Expression</span></span>|<span data-ttu-id="b5e1c-163">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="b5e1c-163">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`LabelTarget target = Expression.Label(typeof(int), "SampleLabel"); BlockExpression block = Expression.Block( Expression.Goto(target, Expression.Constant(0)), Expression.Label(target, Expression.Constant(-1)));`|`.Block() {`<br /><br /> `.Goto SampleLabel { 0 };`<br /><br /> `.Label`<br /><br /> `-1`<br /><br /> `.LabelTarget SampleLabel:`<br /><br /> `}`|  
|`LabelTarget target = Expression.Label(); BlockExpression block = Expression.Block( Expression.Goto(target5), Expression.Label(target5));`|`.Block() {`<br /><br /> `.Goto #Label1 { };`<br /><br /> `.Label`<br /><br /> `.LabelTarget #Label1:`<br /><br /> `}`|  
  
## <a name="checked-operators"></a><span data-ttu-id="b5e1c-164">İşaretli işleçleri</span><span class="sxs-lookup"><span data-stu-id="b5e1c-164">Checked Operators</span></span>  
 <span data-ttu-id="b5e1c-165">İşaretli işleçler, işlecin önüne "#" sembolü ile görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b5e1c-165">Checked operators are displayed with the "#" symbol in front of the operator.</span></span> <span data-ttu-id="b5e1c-166">Örneğin, işaretli Toplama işleci olarak görüntülenir `#+`.</span><span class="sxs-lookup"><span data-stu-id="b5e1c-166">For example, the checked addition operator is displayed as `#+`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="b5e1c-167">Örnekler</span><span class="sxs-lookup"><span data-stu-id="b5e1c-167">Examples</span></span>  
  
|<span data-ttu-id="b5e1c-168">İfade</span><span class="sxs-lookup"><span data-stu-id="b5e1c-168">Expression</span></span>|<span data-ttu-id="b5e1c-169">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="b5e1c-169">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`Expression expr = Expression.AddChecked( Expression.Constant(1), Expression.Constant(2));`|`1 #+ 2`|  
|`Expression expr = Expression.ConvertChecked( Expression.Constant(10.0), typeof(int));`|`#(System.Int32)10D`|  
  
## <a name="see-also"></a><span data-ttu-id="b5e1c-170">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5e1c-170">See also</span></span>

- [<span data-ttu-id="b5e1c-171">İfade ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="b5e1c-171">Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="b5e1c-172">Visual Studio’da hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="b5e1c-172">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)
- [<span data-ttu-id="b5e1c-173">Özel Görselleştirici Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b5e1c-173">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
