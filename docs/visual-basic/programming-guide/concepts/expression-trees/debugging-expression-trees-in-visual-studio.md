---
title: Visual Studio (Visual Basic) ifade ağaçlarında hata ayıklama
ms.date: 07/20/2015
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
ms.openlocfilehash: 2addba2654067eaaf6c621c927e0992308879ae4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644244"
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a><span data-ttu-id="99a66-102">Visual Studio (Visual Basic) ifade ağaçlarında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="99a66-102">Debugging Expression Trees in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="99a66-103">Uygulamalarınızda hata ayıklamak zaman ifade ağaçları içeriği ve yapısı analiz edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99a66-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="99a66-104">İfade ağaç yapısı hızlı bir genel bakış almak için kullanabileceğiniz `DebugView` özelliği yalnızca hata ayıklama modunda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="99a66-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which is available only in debug mode.</span></span> <span data-ttu-id="99a66-105">Hata ayıklama hakkında daha fazla bilgi için bkz: [Visual Studio'da hata ayıklamayı](/visualstudio/debugger/debugging-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="99a66-105">For more information about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).</span></span>  
  
 <span data-ttu-id="99a66-106">İfade ağaçları içeriğini daha iyi göstermek için `DebugView` özelliği Visual Studio görselleştiriciler kullanır.</span><span class="sxs-lookup"><span data-stu-id="99a66-106">To better represent the content of expression trees, the `DebugView` property uses Visual Studio visualizers.</span></span> <span data-ttu-id="99a66-107">Daha fazla bilgi için bkz: [oluşturma özel Görselleştiriciler](/visualstudio/debugger/create-custom-visualizers-of-data).</span><span class="sxs-lookup"><span data-stu-id="99a66-107">For more information, see [Create Custom Visualizers](/visualstudio/debugger/create-custom-visualizers-of-data).</span></span>  
  
### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="99a66-108">Bir ifade ağacına için Görselleştirici açmak için</span><span class="sxs-lookup"><span data-stu-id="99a66-108">To open a visualizer for an expression tree</span></span>  
  
1.  <span data-ttu-id="99a66-109">Yanında Büyüteç simgesini tıklatın `DebugView` bir ifade ağacına özelliğinin **DataTips**, **izleme** penceresinde **otomobiller** penceresinde veya **Yereller** penceresi.</span><span class="sxs-lookup"><span data-stu-id="99a66-109">Click the magnifying glass icon that appears next to the `DebugView` property of an expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
     <span data-ttu-id="99a66-110">Görselleştiriciler listesi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="99a66-110">A list of visualizers is displayed.</span></span>  
  
2.  <span data-ttu-id="99a66-111">Kullanmak istediğiniz Görselleştirici'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="99a66-111">Click the visualizer you want to use.</span></span>  
  
 <span data-ttu-id="99a66-112">Aşağıdaki bölümlerde açıklandığı gibi her bir ifade türü Görselleştirici görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="99a66-112">Each expression type is displayed in the visualizer as described in the following sections.</span></span>  
  
## <a name="parameterexpressions"></a><span data-ttu-id="99a66-113">ParameterExpressions</span><span class="sxs-lookup"><span data-stu-id="99a66-113">ParameterExpressions</span></span>  
 <span data-ttu-id="99a66-114"><xref:System.Linq.Expressions.ParameterExpression> değişken adları başında "$" simgesiyle görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="99a66-114"><xref:System.Linq.Expressions.ParameterExpression> variable names are displayed with a "$" symbol at the beginning.</span></span>  
  
 <span data-ttu-id="99a66-115">Bir parametre bir adı yoksa, otomatik olarak oluşturulan bir ad gibi atanmış olduğu `$var1` veya `$var2`.</span><span class="sxs-lookup"><span data-stu-id="99a66-115">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="99a66-116">Örnekler</span><span class="sxs-lookup"><span data-stu-id="99a66-116">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim numParam As ParameterExpression =   
    Expression.Parameter(GetType(Integer), "num")  
    ```  
  
     <span data-ttu-id="99a66-117">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="99a66-117">`DebugView` property</span></span>  
  
     `$num`  
  
-   `Expression`  
  
    ```vb  
    Dim numParam As ParameterExpression =   
    Expression.Parameter(GetType(Integer))  
    ```  
  
     <span data-ttu-id="99a66-118">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="99a66-118">`DebugView` property</span></span>  
  
     `$var1`  
  
## <a name="constantexpressions"></a><span data-ttu-id="99a66-119">ConstantExpressions</span><span class="sxs-lookup"><span data-stu-id="99a66-119">ConstantExpressions</span></span>  
 <span data-ttu-id="99a66-120">İçin <xref:System.Linq.Expressions.ConstantExpression> dize, tamsayı değerleri temsil eden nesneler ve `null`, sabit değeri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="99a66-120">For <xref:System.Linq.Expressions.ConstantExpression> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="99a66-121">Örnekler</span><span class="sxs-lookup"><span data-stu-id="99a66-121">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim num as Integer= 10  
    Dim expr As ConstantExpression = Expression.Constant(num)  
    ```  
  
     <span data-ttu-id="99a66-122">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="99a66-122">`DebugView` property</span></span>  
  
     <span data-ttu-id="99a66-123">10</span><span class="sxs-lookup"><span data-stu-id="99a66-123">10</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim num As Double = 10  
    Dim expr As ConstantExpression = Expression.Constant(num)  
    ```  
  
     <span data-ttu-id="99a66-124">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="99a66-124">`DebugView` property</span></span>  
  
     <span data-ttu-id="99a66-125">10D</span><span class="sxs-lookup"><span data-stu-id="99a66-125">10D</span></span>  
  
## <a name="blockexpression"></a><span data-ttu-id="99a66-126">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="99a66-126">BlockExpression</span></span>  
 <span data-ttu-id="99a66-127">Varsa türü bir <xref:System.Linq.Expressions.BlockExpression> bloğundaki son ifade türü farklıdır nesne, türü görüntülenir `DebugInfo` köşeli özelliğinde (\< ve >).</span><span class="sxs-lookup"><span data-stu-id="99a66-127">If the type of a <xref:System.Linq.Expressions.BlockExpression> object differs from the type of the last expression in the block, the type is displayed in the `DebugInfo` property in angle brackets (\< and >).</span></span> <span data-ttu-id="99a66-128">Aksi takdirde türünü <xref:System.Linq.Expressions.BlockExpression> nesnesi görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="99a66-128">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="99a66-129">Örnekler</span><span class="sxs-lookup"><span data-stu-id="99a66-129">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim block As BlockExpression = Expression.Block(Expression.Constant("test"))  
    ```  
  
     <span data-ttu-id="99a66-130">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="99a66-130">`DebugView` property</span></span>  
  
     `.Block() {`  
  
     `"test"`  
  
     `}`  
  
-   `Expression`  
  
    ```vb  
    Dim block As BlockExpression =   
    Expression.Block(GetType(Object), Expression.Constant("test"))  
    ```  
  
     <span data-ttu-id="99a66-131">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="99a66-131">`DebugView` property</span></span>  
  
     `.Block<System.Object>() {`  
  
     `"test"`  
  
     `}`  
  
## <a name="lambdaexpression"></a><span data-ttu-id="99a66-132">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="99a66-132">LambdaExpression</span></span>  
 <span data-ttu-id="99a66-133"><xref:System.Linq.Expressions.LambdaExpression> nesneler kendi temsilci türleri ile birlikte görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="99a66-133"><xref:System.Linq.Expressions.LambdaExpression> objects are displayed together with their delegate types.</span></span>  
  
 <span data-ttu-id="99a66-134">Lambda ifadesi bir adı yoksa, otomatik olarak oluşturulan bir ad gibi atanmış olduğu `#Lambda1` veya `#Lambda2`.</span><span class="sxs-lookup"><span data-stu-id="99a66-134">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="99a66-135">Örnekler</span><span class="sxs-lookup"><span data-stu-id="99a66-135">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim lambda As LambdaExpression =   
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1))  
    ```  
  
     <span data-ttu-id="99a66-136">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="99a66-136">`DebugView` property</span></span>  
  
     `.Lambda #Lambda1<System.Func'1[System.Int32]>() {`  
  
     `1`  
  
     `}`  
  
-   `Expression`  
  
    ```vb  
    Dim lambda As LambdaExpression =   
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1), "SampleLamda", Nothing)  
    ```  
  
     <span data-ttu-id="99a66-137">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="99a66-137">`DebugView` property</span></span>  
  
     `.Lambda SampleLambda<System.Func'1[System.Int32]>() {`  
  
     `1`  
  
     `}`  
  
## <a name="labelexpression"></a><span data-ttu-id="99a66-138">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="99a66-138">LabelExpression</span></span>  
 <span data-ttu-id="99a66-139">İçin varsayılan bir değer belirtirseniz, <xref:System.Linq.Expressions.LabelExpression> nesnesi, bu değer, önce görüntülenir <xref:System.Linq.Expressions.LabelTarget> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="99a66-139">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget> object.</span></span>  
  
 <span data-ttu-id="99a66-140">`.Label` Belirteci etiketi başlangıcını gösterir.</span><span class="sxs-lookup"><span data-stu-id="99a66-140">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="99a66-141">`.LabelTarget` Belirteci atlamak için hedef hedef gösterir.</span><span class="sxs-lookup"><span data-stu-id="99a66-141">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>  
  
 <span data-ttu-id="99a66-142">Bir etiket bir adı yoksa, otomatik olarak oluşturulan bir ad gibi atanmış olduğu `#Label1` veya `#Label2`.</span><span class="sxs-lookup"><span data-stu-id="99a66-142">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="99a66-143">Örnekler</span><span class="sxs-lookup"><span data-stu-id="99a66-143">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim target As LabelTarget = Expression.Label(GetType(Integer), "SampleLabel")  
    Dim label1 As BlockExpression = Expression.Block(  
    Expression.Goto(target, Expression.Constant(0)),  
    Expression.Label(target, Expression.Constant(-1)))  
    ```  
  
     <span data-ttu-id="99a66-144">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="99a66-144">`DebugView` property</span></span>  
  
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
  
     <span data-ttu-id="99a66-145">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="99a66-145">`DebugView` property</span></span>  
  
     `.Block() {`  
  
     `.Goto #Label1 { };`  
  
     `.Label`  
  
     `.LabelTarget #Label1:`  
  
     `}`  
  
## <a name="checked-operators"></a><span data-ttu-id="99a66-146">Checked işleçleri</span><span class="sxs-lookup"><span data-stu-id="99a66-146">Checked Operators</span></span>  
 <span data-ttu-id="99a66-147">Checked işleçleri işleci önünde "#" simgesiyle gösterilir.</span><span class="sxs-lookup"><span data-stu-id="99a66-147">Checked operators are displayed with the "#" symbol in front of the operator.</span></span> <span data-ttu-id="99a66-148">Örneğin, denetlenen Toplama işleci olarak görüntülenir `#+`.</span><span class="sxs-lookup"><span data-stu-id="99a66-148">For example, the checked addition operator is displayed as `#+`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="99a66-149">Örnekler</span><span class="sxs-lookup"><span data-stu-id="99a66-149">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim expr As Expression = Expression.AddChecked(  
    Expression.Constant(1), Expression.Constant(2))  
    ```  
  
     <span data-ttu-id="99a66-150">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="99a66-150">`DebugView` property</span></span>  
  
     `1 #+ 2`  
  
-   `Expression`  
  
    ```vb  
    Dim expr As Expression = Expression.ConvertChecked(  
    Expression.Constant(10.0), GetType(Integer))  
    ```  
  
     <span data-ttu-id="99a66-151">`DebugView` Özelliği</span><span class="sxs-lookup"><span data-stu-id="99a66-151">`DebugView` property</span></span>  
  
     `#(System.Int32)10D`  
  
## <a name="see-also"></a><span data-ttu-id="99a66-152">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="99a66-152">See Also</span></span>  
 [<span data-ttu-id="99a66-153">İfade ağaçları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="99a66-153">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)  
 [<span data-ttu-id="99a66-154">Visual Studio’da hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="99a66-154">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)  
 [<span data-ttu-id="99a66-155">Özel Görselleştiriciler oluşturma</span><span class="sxs-lookup"><span data-stu-id="99a66-155">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
