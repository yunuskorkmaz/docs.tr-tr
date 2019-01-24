---
title: Visual Studio'da (Visual Basic) ifade ağaçlarında hata ayıklama
ms.date: 07/20/2015
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
ms.openlocfilehash: b060a65a38c4ab295a54f972678f273ada218d06
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54617362"
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a><span data-ttu-id="89216-102">Visual Studio'da (Visual Basic) ifade ağaçlarında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="89216-102">Debugging Expression Trees in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="89216-103">Uygulamalarınızın hata ayıklaması yaparken, yapısı ve içeriği ifade ağaçları analiz edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="89216-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="89216-104">İfade ağaç yapısı hızlı bir genel bakış edinmek için kullanabileceğiniz `DebugView` özelliği yalnızca hata ayıklama modunda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="89216-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which is available only in debug mode.</span></span> <span data-ttu-id="89216-105">Hata ayıklama hakkında daha fazla bilgi için bkz. [Visual Studio'da hata ayıklama](/visualstudio/debugger/debugging-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="89216-105">For more information about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).</span></span>  
  
 <span data-ttu-id="89216-106">Daha iyi ifade ağaçları içeriğini temsil etmek için `DebugView` özelliği, Visual Studio görselleştiriciler kullanır.</span><span class="sxs-lookup"><span data-stu-id="89216-106">To better represent the content of expression trees, the `DebugView` property uses Visual Studio visualizers.</span></span> <span data-ttu-id="89216-107">Daha fazla bilgi için [oluşturma özel Görselleştiriciler](/visualstudio/debugger/create-custom-visualizers-of-data).</span><span class="sxs-lookup"><span data-stu-id="89216-107">For more information, see [Create Custom Visualizers](/visualstudio/debugger/create-custom-visualizers-of-data).</span></span>  
  
### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="89216-108">İfade ağacı bir görselleştiriciyi açmak için</span><span class="sxs-lookup"><span data-stu-id="89216-108">To open a visualizer for an expression tree</span></span>  
  
1.  <span data-ttu-id="89216-109">Yanında görünen Büyüteç simgesine tıklayarak `DebugView` özelliğine bir ifade ağacında **DataTips**, **izleme** penceresinde **Otolar** penceresinde veya **Yereller** penceresi.</span><span class="sxs-lookup"><span data-stu-id="89216-109">Click the magnifying glass icon that appears next to the `DebugView` property of an expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
     <span data-ttu-id="89216-110">Görselleştiriciler listesi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="89216-110">A list of visualizers is displayed.</span></span>  
  
2.  <span data-ttu-id="89216-111">Kullanmak istediğiniz Görselleştirici'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="89216-111">Click the visualizer you want to use.</span></span>  
  
 <span data-ttu-id="89216-112">Aşağıdaki bölümlerde açıklandığı gibi her ifade türü görselleştiricisi içinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="89216-112">Each expression type is displayed in the visualizer as described in the following sections.</span></span>  
  
## <a name="parameterexpressions"></a><span data-ttu-id="89216-113">ParameterExpressions</span><span class="sxs-lookup"><span data-stu-id="89216-113">ParameterExpressions</span></span>  
 <span data-ttu-id="89216-114"><xref:System.Linq.Expressions.ParameterExpression> Değişken adlarının başında bir "$" simgesi ile görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="89216-114"><xref:System.Linq.Expressions.ParameterExpression> variable names are displayed with a "$" symbol at the beginning.</span></span>  
  
 <span data-ttu-id="89216-115">Parametre bir adı yoksa, otomatik olarak oluşturulmuş bir adı gibi atandıktan `$var1` veya `$var2`.</span><span class="sxs-lookup"><span data-stu-id="89216-115">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="89216-116">Örnekler</span><span class="sxs-lookup"><span data-stu-id="89216-116">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim numParam As ParameterExpression =   
    Expression.Parameter(GetType(Integer), "num")  
    ```  
  
     <span data-ttu-id="89216-117">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="89216-117">`DebugView` property</span></span>  
  
     `$num`  
  
-   `Expression`  
  
    ```vb  
    Dim numParam As ParameterExpression =   
    Expression.Parameter(GetType(Integer))  
    ```  
  
     <span data-ttu-id="89216-118">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="89216-118">`DebugView` property</span></span>  
  
     `$var1`  
  
## <a name="constantexpressions"></a><span data-ttu-id="89216-119">ConstantExpressions</span><span class="sxs-lookup"><span data-stu-id="89216-119">ConstantExpressions</span></span>  
 <span data-ttu-id="89216-120">İçin <xref:System.Linq.Expressions.ConstantExpression> dize, tamsayı değerlerini temsil eden nesneleri ve `null`, sabit değeri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="89216-120">For <xref:System.Linq.Expressions.ConstantExpression> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="89216-121">Örnekler</span><span class="sxs-lookup"><span data-stu-id="89216-121">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim num as Integer= 10  
    Dim expr As ConstantExpression = Expression.Constant(num)  
    ```  
  
     <span data-ttu-id="89216-122">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="89216-122">`DebugView` property</span></span>  
  
     <span data-ttu-id="89216-123">10</span><span class="sxs-lookup"><span data-stu-id="89216-123">10</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim num As Double = 10  
    Dim expr As ConstantExpression = Expression.Constant(num)  
    ```  
  
     <span data-ttu-id="89216-124">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="89216-124">`DebugView` property</span></span>  
  
     <span data-ttu-id="89216-125">10D</span><span class="sxs-lookup"><span data-stu-id="89216-125">10D</span></span>  
  
## <a name="blockexpression"></a><span data-ttu-id="89216-126">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="89216-126">BlockExpression</span></span>  
 <span data-ttu-id="89216-127">Varsa türünü bir <xref:System.Linq.Expressions.BlockExpression> bloğundaki son ifadenin türü nesne farklıdır, türü görüntülenen `DebugInfo` açılı ayraçlar özelliğinde (\< ve >).</span><span class="sxs-lookup"><span data-stu-id="89216-127">If the type of a <xref:System.Linq.Expressions.BlockExpression> object differs from the type of the last expression in the block, the type is displayed in the `DebugInfo` property in angle brackets (\< and >).</span></span> <span data-ttu-id="89216-128">Aksi halde, türünü <xref:System.Linq.Expressions.BlockExpression> nesne görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="89216-128">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="89216-129">Örnekler</span><span class="sxs-lookup"><span data-stu-id="89216-129">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim block As BlockExpression = Expression.Block(Expression.Constant("test"))  
    ```  
  
     <span data-ttu-id="89216-130">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="89216-130">`DebugView` property</span></span>  
  
     `.Block() {`  
  
     `"test"`  
  
     `}`  
  
-   `Expression`  
  
    ```vb  
    Dim block As BlockExpression =   
    Expression.Block(GetType(Object), Expression.Constant("test"))  
    ```  
  
     <span data-ttu-id="89216-131">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="89216-131">`DebugView` property</span></span>  
  
     `.Block<System.Object>() {`  
  
     `"test"`  
  
     `}`  
  
## <a name="lambdaexpression"></a><span data-ttu-id="89216-132">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="89216-132">LambdaExpression</span></span>  
 <span data-ttu-id="89216-133"><xref:System.Linq.Expressions.LambdaExpression> nesneler, temsilci türleri ile birlikte görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="89216-133"><xref:System.Linq.Expressions.LambdaExpression> objects are displayed together with their delegate types.</span></span>  
  
 <span data-ttu-id="89216-134">Bir lambda ifadesi bir adı yoksa, otomatik olarak oluşturulmuş bir adı gibi atandıktan `#Lambda1` veya `#Lambda2`.</span><span class="sxs-lookup"><span data-stu-id="89216-134">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="89216-135">Örnekler</span><span class="sxs-lookup"><span data-stu-id="89216-135">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim lambda As LambdaExpression =   
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1))  
    ```  
  
     <span data-ttu-id="89216-136">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="89216-136">`DebugView` property</span></span>  
  
     `.Lambda #Lambda1<System.Func'1[System.Int32]>() {`  
  
     `1`  
  
     `}`  
  
-   `Expression`  
  
    ```vb  
    Dim lambda As LambdaExpression =   
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1), "SampleLamda", Nothing)  
    ```  
  
     <span data-ttu-id="89216-137">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="89216-137">`DebugView` property</span></span>  
  
     `.Lambda SampleLambda<System.Func'1[System.Int32]>() {`  
  
     `1`  
  
     `}`  
  
## <a name="labelexpression"></a><span data-ttu-id="89216-138">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="89216-138">LabelExpression</span></span>  
 <span data-ttu-id="89216-139">İçin varsayılan bir değer belirtirseniz <xref:System.Linq.Expressions.LabelExpression> nesnesi, bu değer, önce görüntülenir <xref:System.Linq.Expressions.LabelTarget> nesne.</span><span class="sxs-lookup"><span data-stu-id="89216-139">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget> object.</span></span>  
  
 <span data-ttu-id="89216-140">`.Label` Belirteci etiketi başlangıcını gösterir.</span><span class="sxs-lookup"><span data-stu-id="89216-140">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="89216-141">`.LabelTarget` Belirteci atlamak için hedef hedefinin gösterir.</span><span class="sxs-lookup"><span data-stu-id="89216-141">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>  
  
 <span data-ttu-id="89216-142">Bir etiket bir ad yoksa otomatik olarak oluşturulmuş bir adı gibi atandıktan `#Label1` veya `#Label2`.</span><span class="sxs-lookup"><span data-stu-id="89216-142">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="89216-143">Örnekler</span><span class="sxs-lookup"><span data-stu-id="89216-143">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim target As LabelTarget = Expression.Label(GetType(Integer), "SampleLabel")  
    Dim label1 As BlockExpression = Expression.Block(  
    Expression.Goto(target, Expression.Constant(0)),  
    Expression.Label(target, Expression.Constant(-1)))  
    ```  
  
     <span data-ttu-id="89216-144">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="89216-144">`DebugView` property</span></span>  
  
     `.Block() {`  
  
     `.Goto SampleLabel { 0 };`  
  
     `.Label`  
  
     `-1`  
  
     `.LabelTarget SampleLabel:`  
  
     `}`  
  
-   `Expression`  
  
    ```vb  
    Dim target As LabelTarget = Expression.Label()  
    Dim block As BlockExpression = Expression.Block(  
    Expression.Goto(target), Expression.Label(target))  
    ```  
  
     <span data-ttu-id="89216-145">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="89216-145">`DebugView` property</span></span>  
  
     `.Block() {`  
  
     `.Goto #Label1 { };`  
  
     `.Label`  
  
     `.LabelTarget #Label1:`  
  
     `}`  
  
## <a name="checked-operators"></a><span data-ttu-id="89216-146">İşaretli işleçleri</span><span class="sxs-lookup"><span data-stu-id="89216-146">Checked Operators</span></span>  
 <span data-ttu-id="89216-147">İşaretli işleçler, işlecin önüne "#" sembolü ile görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="89216-147">Checked operators are displayed with the "#" symbol in front of the operator.</span></span> <span data-ttu-id="89216-148">Örneğin, işaretli Toplama işleci olarak görüntülenir `#+`.</span><span class="sxs-lookup"><span data-stu-id="89216-148">For example, the checked addition operator is displayed as `#+`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="89216-149">Örnekler</span><span class="sxs-lookup"><span data-stu-id="89216-149">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim expr As Expression = Expression.AddChecked(  
    Expression.Constant(1), Expression.Constant(2))  
    ```  
  
     <span data-ttu-id="89216-150">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="89216-150">`DebugView` property</span></span>  
  
     `1 #+ 2`  
  
-   `Expression`  
  
    ```vb  
    Dim expr As Expression = Expression.ConvertChecked(  
    Expression.Constant(10.0), GetType(Integer))  
    ```  
  
     <span data-ttu-id="89216-151">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="89216-151">`DebugView` property</span></span>  
  
     `#(System.Int32)10D`  
  
## <a name="see-also"></a><span data-ttu-id="89216-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89216-152">See also</span></span>
- [<span data-ttu-id="89216-153">İfade ağaçları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="89216-153">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="89216-154">Visual Studio’da hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="89216-154">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)
- [<span data-ttu-id="89216-155">Özel Görselleştirici Oluşturma</span><span class="sxs-lookup"><span data-stu-id="89216-155">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
