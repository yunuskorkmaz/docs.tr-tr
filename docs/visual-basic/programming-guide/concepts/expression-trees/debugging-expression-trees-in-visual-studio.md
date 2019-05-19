---
title: Visual Studio'da (Visual Basic) ifade ağaçlarında hata ayıklama
ms.date: 07/20/2015
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
ms.openlocfilehash: 7fc97d898c5956b5a569036e6e0fe1174714576d
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65879817"
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a><span data-ttu-id="5fa25-102">Visual Studio'da (Visual Basic) ifade ağaçlarında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="5fa25-102">Debugging Expression Trees in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="5fa25-103">Uygulamalarınızın hata ayıklaması yaparken, yapısı ve içeriği ifade ağaçları analiz edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5fa25-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="5fa25-104">İfade ağaç yapısı hızlı bir genel bakış edinmek için kullanabileceğiniz `DebugView` açıklanan özel bir söz dizimi kullanılarak ifade ağaçları temsil eden özellik [aşağıda](#debugview-syntax).</span><span class="sxs-lookup"><span data-stu-id="5fa25-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which represents expression trees using a special syntax described [below](#debugview-syntax).</span></span> <span data-ttu-id="5fa25-105">(Unutmayın `DebugView` yalnızca hata ayıklama modunda kullanılabilir.)</span><span class="sxs-lookup"><span data-stu-id="5fa25-105">(Note that `DebugView` is available only in debug mode.)</span></span>  

![DebugView Visual Studio hata ayıklayıcısı içinde ifade ağacı](media/debugging-expression-trees-in-visual-studio/debugview_vb.png)

<span data-ttu-id="5fa25-107">Bu yana `DebugView` bir dize ise kullanabilirsiniz [yerleşik metin Görselleştiriciye](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) seçerek birden çok satırda, görüntülemek için **metin görselleştiricisi** Büyüteç simgesinin yanındaki gelen `DebugView` Etiket.</span><span class="sxs-lookup"><span data-stu-id="5fa25-107">Since `DebugView` is a string, you can use the [built-in Text Visualizer](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) to view it across multiple lines, by selecting **Text Visualizer** from the magnifying glass icon next to the `DebugView` label.</span></span>

 ![Metin Görselleştirici 'DebugView' sonuçlarına uygulandı](media/debugging-expression-trees-in-visual-studio/string_visualizer_vb.png)

<span data-ttu-id="5fa25-109">Alternatif olarak, yükleyip kullanabilir [özel Görselleştirici](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) için ifade ağaçları:</span><span class="sxs-lookup"><span data-stu-id="5fa25-109">Alternatively, you can install and use [a custom visualizer](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) for expression trees:</span></span>

* <span data-ttu-id="5fa25-110">[Okunabilir ifadeleri](https://github.com/agileobjects/ReadableExpressions) ([MIT lisansı](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), kullanılabilir [Visual Studio Market](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), işler ifade ağacı C# kod:</span><span class="sxs-lookup"><span data-stu-id="5fa25-110">[Readable Expressions](https://github.com/agileobjects/ReadableExpressions) ([MIT license](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), available at the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renders the expression tree as C# code:</span></span>

  ![Okunabilir ifadeleri görselleştiricisi](media/debugging-expression-trees-in-visual-studio/readable_expressions_visualizer.png)

* <span data-ttu-id="5fa25-112">[İfade ağacı Görselleştiricisini](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([MIT lisansı](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), ifade ağacı, özellikler ve ilgili nesneleri; grafik bir görünümünü sunar ve Visual Basic kodunu kullanarak ifade ağacı işleyebilir:</span><span class="sxs-lookup"><span data-stu-id="5fa25-112">[Expression Tree Visualizer](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([MIT license](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), provides a graphical view of the expression tree, its properties, and related objects; and can render the expression tree using Visual Basic code:</span></span>

  ![ExpressionToString Görselleştirici](media/debugging-expression-trees-in-visual-studio/expression_to_string_visualizer_vb.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="5fa25-114">İfade ağacı bir görselleştiriciyi açmak için</span><span class="sxs-lookup"><span data-stu-id="5fa25-114">To open a visualizer for an expression tree</span></span>  
  
1. <span data-ttu-id="5fa25-115">İfade ağacında yanında Büyüteç simgesine tıklayarak **DataTips**, **Watch** penceresinde **Otolar** penceresinde veya **Yereller** penceresi.</span><span class="sxs-lookup"><span data-stu-id="5fa25-115">Click the magnifying glass icon that appears next to the expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
     <span data-ttu-id="5fa25-116">Kullanılabilir görselleştiriciler listesi görüntülenir.:</span><span class="sxs-lookup"><span data-stu-id="5fa25-116">A list of available visualizers is displayed.:</span></span> 

      ![Visual Studio'dan açılış görselleştiriciler](media/debugging-expression-trees-in-visual-studio/expression_tree_visualizers_vb.png)

2. <span data-ttu-id="5fa25-118">Kullanmak istediğiniz Görselleştirici'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5fa25-118">Click the visualizer you want to use.</span></span>  

## <a name="debugview-syntax"></a><span data-ttu-id="5fa25-119">`DebugView` Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="5fa25-119">`DebugView` syntax</span></span> 

<span data-ttu-id="5fa25-120">Aşağıdaki bölümlerde açıklandığı gibi her ifade türü görselleştiricisi içinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5fa25-120">Each expression type is displayed in the visualizer as described in the following sections.</span></span>

## <a name="parameterexpressions"></a><span data-ttu-id="5fa25-121">ParameterExpressions</span><span class="sxs-lookup"><span data-stu-id="5fa25-121">ParameterExpressions</span></span>

<span data-ttu-id="5fa25-122"><xref:System.Linq.Expressions.ParameterExpression> Değişken adlarının başında bir "$" simgesi ile görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5fa25-122"><xref:System.Linq.Expressions.ParameterExpression> variable names are displayed with a "$" symbol at the beginning.</span></span>

<span data-ttu-id="5fa25-123">Parametre bir adı yoksa, otomatik olarak oluşturulmuş bir adı gibi atandıktan `$var1` veya `$var2`.</span><span class="sxs-lookup"><span data-stu-id="5fa25-123">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>

### <a name="examples"></a><span data-ttu-id="5fa25-124">Örnekler</span><span class="sxs-lookup"><span data-stu-id="5fa25-124">Examples</span></span>

- `Expression`

    ```vb
    Dim numParam As ParameterExpression =
    Expression.Parameter(GetType(Integer), "num")
    ```

    <span data-ttu-id="5fa25-125">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="5fa25-125">`DebugView` property</span></span>

    `$num`

- `Expression`

    ```vb
    Dim numParam As ParameterExpression =
    Expression.Parameter(GetType(Integer))
    ```

    <span data-ttu-id="5fa25-126">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="5fa25-126">`DebugView` property</span></span>

    `$var1`

## <a name="constantexpressions"></a><span data-ttu-id="5fa25-127">ConstantExpressions</span><span class="sxs-lookup"><span data-stu-id="5fa25-127">ConstantExpressions</span></span>
 <span data-ttu-id="5fa25-128">İçin <xref:System.Linq.Expressions.ConstantExpression> dize, tamsayı değerlerini temsil eden nesneleri ve `null`, sabit değeri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5fa25-128">For <xref:System.Linq.Expressions.ConstantExpression> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>

### <a name="examples"></a><span data-ttu-id="5fa25-129">Örnekler</span><span class="sxs-lookup"><span data-stu-id="5fa25-129">Examples</span></span>

- `Expression`

    ```vb
    Dim num as Integer= 10
    Dim expr As ConstantExpression = Expression.Constant(num)
    ```

    <span data-ttu-id="5fa25-130">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="5fa25-130">`DebugView` property</span></span>

    <span data-ttu-id="5fa25-131">10</span><span class="sxs-lookup"><span data-stu-id="5fa25-131">10</span></span>

- `Expression`

    ```vb
    Dim num As Double = 10
    Dim expr As ConstantExpression = Expression.Constant(num)
    ```

    <span data-ttu-id="5fa25-132">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="5fa25-132">`DebugView` property</span></span>

    <span data-ttu-id="5fa25-133">10D</span><span class="sxs-lookup"><span data-stu-id="5fa25-133">10D</span></span>

## <a name="blockexpression"></a><span data-ttu-id="5fa25-134">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="5fa25-134">BlockExpression</span></span>

<span data-ttu-id="5fa25-135">Varsa türünü bir <xref:System.Linq.Expressions.BlockExpression> bloğundaki son ifadenin türü nesne farklıdır, türü görüntülenen `DebugInfo` açılı ayraçlar özelliğinde (\< ve >).</span><span class="sxs-lookup"><span data-stu-id="5fa25-135">If the type of a <xref:System.Linq.Expressions.BlockExpression> object differs from the type of the last expression in the block, the type is displayed in the `DebugInfo` property in angle brackets (\< and >).</span></span> <span data-ttu-id="5fa25-136">Aksi halde, türünü <xref:System.Linq.Expressions.BlockExpression> nesne görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="5fa25-136">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>

### <a name="examples"></a><span data-ttu-id="5fa25-137">Örnekler</span><span class="sxs-lookup"><span data-stu-id="5fa25-137">Examples</span></span>

- `Expression`

    ```vb
    Dim block As BlockExpression = Expression.Block(Expression.Constant("test"))
    ```

    <span data-ttu-id="5fa25-138">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="5fa25-138">`DebugView` property</span></span>

    `.Block() {`

    `"test"`

    `}`

- `Expression`

    ```vb
    Dim block As BlockExpression =
    Expression.Block(GetType(Object), Expression.Constant("test"))
    ```

    <span data-ttu-id="5fa25-139">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="5fa25-139">`DebugView` property</span></span>

    `.Block<System.Object>() {`

    `"test"`

    `}`

## <a name="lambdaexpression"></a><span data-ttu-id="5fa25-140">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="5fa25-140">LambdaExpression</span></span>

<span data-ttu-id="5fa25-141"><xref:System.Linq.Expressions.LambdaExpression> nesneler, temsilci türleri ile birlikte görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5fa25-141"><xref:System.Linq.Expressions.LambdaExpression> objects are displayed together with their delegate types.</span></span>

<span data-ttu-id="5fa25-142">Bir lambda ifadesi bir adı yoksa, otomatik olarak oluşturulmuş bir adı gibi atandıktan `#Lambda1` veya `#Lambda2`.</span><span class="sxs-lookup"><span data-stu-id="5fa25-142">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>

### <a name="examples"></a><span data-ttu-id="5fa25-143">Örnekler</span><span class="sxs-lookup"><span data-stu-id="5fa25-143">Examples</span></span>

- `Expression`

    ```vb
    Dim lambda As LambdaExpression =
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1))
    ```

    <span data-ttu-id="5fa25-144">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="5fa25-144">`DebugView` property</span></span>

    `.Lambda #Lambda1<System.Func'1[System.Int32]>() {`

    `1`

    `}`

- `Expression`

    ```vb
    Dim lambda As LambdaExpression =
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1), "SampleLambda", Nothing)
    ```

    <span data-ttu-id="5fa25-145">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="5fa25-145">`DebugView` property</span></span>

    `.Lambda SampleLambda<System.Func'1[System.Int32]>() {`

    `1`

    `}`

## <a name="labelexpression"></a><span data-ttu-id="5fa25-146">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="5fa25-146">LabelExpression</span></span>

<span data-ttu-id="5fa25-147">İçin varsayılan bir değer belirtirseniz <xref:System.Linq.Expressions.LabelExpression> nesnesi, bu değer, önce görüntülenir <xref:System.Linq.Expressions.LabelTarget> nesne.</span><span class="sxs-lookup"><span data-stu-id="5fa25-147">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget> object.</span></span>

<span data-ttu-id="5fa25-148">`.Label` Belirteci etiketi başlangıcını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5fa25-148">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="5fa25-149">`.LabelTarget` Belirteci atlamak için hedef hedefinin gösterir.</span><span class="sxs-lookup"><span data-stu-id="5fa25-149">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>

<span data-ttu-id="5fa25-150">Bir etiket bir ad yoksa otomatik olarak oluşturulmuş bir adı gibi atandıktan `#Label1` veya `#Label2`.</span><span class="sxs-lookup"><span data-stu-id="5fa25-150">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>

### <a name="examples"></a><span data-ttu-id="5fa25-151">Örnekler</span><span class="sxs-lookup"><span data-stu-id="5fa25-151">Examples</span></span>

- `Expression`

    ```vb
    Dim target As LabelTarget = Expression.Label(GetType(Integer), "SampleLabel")
    Dim label1 As BlockExpression = Expression.Block(
    Expression.Goto(target, Expression.Constant(0)),
    Expression.Label(target, Expression.Constant(-1)))
    ```

    <span data-ttu-id="5fa25-152">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="5fa25-152">`DebugView` property</span></span>

    `.Block() {`

    `.Goto SampleLabel { 0 };`

    `.Label`

    `-1`

    `.LabelTarget SampleLabel:`

    `}`

- `Expression`

    ```vb
    Dim target As LabelTarget = Expression.Label()
    Dim block As BlockExpression = Expression.Block(
    Expression.Goto(target), Expression.Label(target))
    ```

    <span data-ttu-id="5fa25-153">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="5fa25-153">`DebugView` property</span></span>

    `.Block() {`

    `.Goto #Label1 { };`

    `.Label`

    `.LabelTarget #Label1:`

    `}`

## <a name="checked-operators"></a><span data-ttu-id="5fa25-154">İşaretli işleçleri</span><span class="sxs-lookup"><span data-stu-id="5fa25-154">Checked Operators</span></span>

<span data-ttu-id="5fa25-155">İşaretli işleçler, işlecin önüne "#" sembolü ile görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5fa25-155">Checked operators are displayed with the "#" symbol in front of the operator.</span></span> <span data-ttu-id="5fa25-156">Örneğin, işaretli Toplama işleci olarak görüntülenir `#+`.</span><span class="sxs-lookup"><span data-stu-id="5fa25-156">For example, the checked addition operator is displayed as `#+`.</span></span>

### <a name="examples"></a><span data-ttu-id="5fa25-157">Örnekler</span><span class="sxs-lookup"><span data-stu-id="5fa25-157">Examples</span></span>

- `Expression`

    ```vb
    Dim expr As Expression = Expression.AddChecked(
    Expression.Constant(1), Expression.Constant(2))
    ```

    <span data-ttu-id="5fa25-158">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="5fa25-158">`DebugView` property</span></span>

    `1 #+ 2`

- `Expression`

    ```vb
    Dim expr As Expression = Expression.ConvertChecked(
    Expression.Constant(10.0), GetType(Integer))
    ```

    <span data-ttu-id="5fa25-159">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="5fa25-159">`DebugView` property</span></span>

    `#(System.Int32)10D`

## <a name="see-also"></a><span data-ttu-id="5fa25-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5fa25-160">See also</span></span>

- [<span data-ttu-id="5fa25-161">İfade ağaçları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5fa25-161">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="5fa25-162">Visual Studio’da hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="5fa25-162">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)
- [<span data-ttu-id="5fa25-163">Özel Görselleştirici Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5fa25-163">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
