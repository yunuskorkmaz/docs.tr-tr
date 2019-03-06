---
title: C# Expressions
ms.date: 03/30/2017
ms.assetid: 29110be7-f4e3-407e-8dbe-78102eb21115
ms.openlocfilehash: ac123a396bd43bc7b91aff6ce928b18ef4fbe6bd
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354745"
---
# <a name="c-expressions"></a><span data-ttu-id="884be-102">C# Expressions</span><span class="sxs-lookup"><span data-stu-id="884be-102">C# Expressions</span></span>
<span data-ttu-id="884be-103">İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], C# ifadeleri, Windows Workflow Foundation (WF) desteklenir.</span><span class="sxs-lookup"><span data-stu-id="884be-103">Starting with [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], C# expressions are supported in Windows Workflow Foundation (WF).</span></span> <span data-ttu-id="884be-104">Yeni C# iş akışı projeleri hedefleyen Visual Studio 2012'de oluşturulan [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] kullanmak C# ifadeleri ve Visual Basic iş akışı projeleri Visual Basic deyimleri kullanacak.</span><span class="sxs-lookup"><span data-stu-id="884be-104">New C# workflow projects created in Visual Studio 2012 that target [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] use C# expressions, and Visual Basic workflow projects use Visual Basic expressions.</span></span> <span data-ttu-id="884be-105">Varolan [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] iş akışı projeleri, Visual Basic deyimleri kullanacak şekilde geçirilebilir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] dil ve bu projeyi bağımsız olarak desteklenir.</span><span class="sxs-lookup"><span data-stu-id="884be-105">Existing [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] workflow projects that use Visual Basic expressions can be migrated to [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] regardless of the project language and are supported.</span></span> <span data-ttu-id="884be-106">Bu konu, C# ifadeleri genel bakış sağlar. [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="884be-106">This topic provides an overview of C# expressions in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span>

## <a name="using-c-expressions-in-workflows"></a><span data-ttu-id="884be-107">C# ifadeleri iş akışlarında kullanma</span><span class="sxs-lookup"><span data-stu-id="884be-107">Using C# expressions in workflows</span></span>

-   [<span data-ttu-id="884be-108">C# ifadeleri iş akışı Tasarımcısı'nda kullanma</span><span class="sxs-lookup"><span data-stu-id="884be-108">Using C# expressions in the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#WFDesigner)

    -   [<span data-ttu-id="884be-109">Geriye dönük uyumluluk</span><span class="sxs-lookup"><span data-stu-id="884be-109">Backwards compatibility</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#BackwardCompat)

-   [<span data-ttu-id="884be-110">Kod akışlarında C# ifadeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="884be-110">Using C# expressions in code workflows</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows)

-   [<span data-ttu-id="884be-111">XAML iş akışlarında C# ifadeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="884be-111">Using C# expressions in XAML workflows</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#XamlWorkflows)

    -   [<span data-ttu-id="884be-112">Derlenmiş Xaml</span><span class="sxs-lookup"><span data-stu-id="884be-112">Compiled Xaml</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CompiledXaml)

    -   [<span data-ttu-id="884be-113">Bağımsız Xaml</span><span class="sxs-lookup"><span data-stu-id="884be-113">Loose Xaml</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#LooseXaml)

-   [<span data-ttu-id="884be-114">C# ifadelerini kullanarak XAMLX iş akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="884be-114">Using C# expressions in XAMLX workflow services</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#WFServices)

### <a name="WFDesigner"></a> <span data-ttu-id="884be-115">C# ifadeleri iş akışı Tasarımcısı'nda kullanma</span><span class="sxs-lookup"><span data-stu-id="884be-115">Using C# expressions in the Workflow Designer</span></span>
 <span data-ttu-id="884be-116">İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], C# ifadeleri, Windows Workflow Foundation (WF) desteklenir.</span><span class="sxs-lookup"><span data-stu-id="884be-116">Starting with [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], C# expressions are supported in Windows Workflow Foundation (WF).</span></span> <span data-ttu-id="884be-117">C# iş akışı projeleri hedefleyen Visual Studio 2012'de oluşturulan [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Visual Basic iş akışı projeleri Visual Basic deyimleri kullanırken, C# ifadeleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="884be-117">C# workflow projects created in Visual Studio 2012 that target [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] use C# expressions, while Visual Basic workflow projects use Visual Basic expressions.</span></span> <span data-ttu-id="884be-118">İstenen C# ifadesini belirtmek için etiketli kutuya yazın **bir C# ifadesi girin**.</span><span class="sxs-lookup"><span data-stu-id="884be-118">To specify the desired C# expression, type it into the box labeled **Enter a C# expression**.</span></span> <span data-ttu-id="884be-119">Bu etiketi, etkinlik Tasarımcısı'nda veya iş akışı tasarımcısında etkinlik seçili olduğunda Özellikler penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="884be-119">This label is displayed in the properties window when the activity is selected in the designer, or on the activity in the workflow designer.</span></span> <span data-ttu-id="884be-120">Aşağıdaki örnekte, iki `WriteLine` etkinlikleri içinde yer alır bir `Sequence` içinde bir `NoPersistScope`.</span><span class="sxs-lookup"><span data-stu-id="884be-120">In the following example, two `WriteLine` activities are contained within a `Sequence` inside a `NoPersistScope`.</span></span>

 <span data-ttu-id="884be-121">![Sıralı etkinlik otomatik olarak oluşturulan](../../../docs/framework/windows-workflow-foundation/media/autosurround2.png "AutoSurround2")</span><span class="sxs-lookup"><span data-stu-id="884be-121">![Automatically created sequence activity](../../../docs/framework/windows-workflow-foundation/media/autosurround2.png "AutoSurround2")</span></span>

> [!NOTE]
>  <span data-ttu-id="884be-122">C# ifadeleri yalnızca Visual Studio'da desteklenir ve yeniden barındırılan iş akışı Tasarımcısı'nda desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="884be-122">C# expressions are supported only in Visual Studio, and are not supported in the re-hosted workflow designer.</span></span> <span data-ttu-id="884be-123">Yeniden barındırılan tasarımcıda desteklenen yeni WF45 özellikler hakkında daha fazla bilgi için bkz. [yeniden barındırılan iş akışı tasarımcısında yeni Workflow Foundation 4.5 özellikleri desteği](../../../docs/framework/windows-workflow-foundation/wf-features-in-the-rehosted-workflow-designer.md).</span><span class="sxs-lookup"><span data-stu-id="884be-123">For more information about new WF45 features supported in the re-hosted designer, see [Support for New Workflow Foundation 4.5 Features in the Rehosted Workflow Designer](../../../docs/framework/windows-workflow-foundation/wf-features-in-the-rehosted-workflow-designer.md).</span></span>

#### <a name="BackwardCompat"></a> <span data-ttu-id="884be-124">Geriye dönük uyumluluk</span><span class="sxs-lookup"><span data-stu-id="884be-124">Backwards compatibility</span></span>
 <span data-ttu-id="884be-125">Varolan bir Visual Basic deyimleri [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] için geçirilen C# iş akışı projeleri [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] desteklenir.</span><span class="sxs-lookup"><span data-stu-id="884be-125">Visual Basic expressions in existing [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] C# workflow projects that have been migrated to [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] are supported.</span></span> <span data-ttu-id="884be-126">Visual Basic ifadeleri iş akışı Tasarımcısı'nda görüntülendiğinde, var olan Visual Basic ifadesinin metin ile değiştirilir **değer XAML ayarlandığı**, Visual Basic ifade geçerli C# sözdizimi olmadığı sürece.</span><span class="sxs-lookup"><span data-stu-id="884be-126">When the Visual Basic expressions are viewed in the workflow designer, the text of the existing Visual Basic expression is replaced with **Value was set in XAML**, unless the Visual Basic expression is valid C# syntax.</span></span> <span data-ttu-id="884be-127">Visual Basic ifade geçerli C# sözdizimi, ardından ifadesi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="884be-127">If the Visual Basic expression is valid C# syntax, then the expression is displayed.</span></span> <span data-ttu-id="884be-128">Visual Basic deyimleri C# ' tan güncelleştirmek için iş akışı Tasarımcısı'nda düzenlemek ve eşdeğer C# ifadesi belirtin.</span><span class="sxs-lookup"><span data-stu-id="884be-128">To update the Visual Basic expressions to C#, you can edit them in the workflow designer and specify the equivalent C# expression.</span></span> <span data-ttu-id="884be-129">Visual Basic deyimleri için C#, ancak ifadeler dönüştürülür C# ve Visual Basic geri değil iş akışı tasarımcısında güncelleştirildikten sonra güncelleştirmek için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="884be-129">It is not required to update the Visual Basic expressions to C#, but once the expressions are updated in the workflow designer they are converted to C# and may not be reverted to Visual Basic.</span></span>

### <a name="CodeWorkflows"></a> <span data-ttu-id="884be-130">Kod akışlarında C# ifadeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="884be-130">Using C# expressions in code workflows</span></span>
 <span data-ttu-id="884be-131">C# ifadelerini desteklenir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] kod tabanlı iş akışları, ancak iş akışı çağrılmadan önce C# ifadelerini kullanarak derlenmelidir <xref:System.Activities.XamlIntegration.TextExpressionCompiler.Compile%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="884be-131">C# expressions are supported in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] code based workflows, but before the workflow can be invoked the C# expressions must be compiled using <xref:System.Activities.XamlIntegration.TextExpressionCompiler.Compile%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="884be-132">İş akışı yazarları kullanabileceğiniz `CSharpValue` gelerek bir ifadenin temsil etmek için ve `CSharpReference` bir ifadenin lvalue temsil etmek için.</span><span class="sxs-lookup"><span data-stu-id="884be-132">Workflow authors can use `CSharpValue` to represent the r-value of an expression, and `CSharpReference` to represent the l-value of an expression.</span></span> <span data-ttu-id="884be-133">Aşağıdaki örnekte, bir iş akışı ile oluşturulan bir `Assign` etkinliği ve bir `WriteLine` etkinlik yer alan bir `Sequence` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="884be-133">In the following example, a workflow is created with an `Assign` activity and a `WriteLine` activity contained in a `Sequence` activity.</span></span> <span data-ttu-id="884be-134">A `CSharpReference` için belirtilen `To` bağımsız değişkeni `Assign`, ifadenin lvalue temsil eder.</span><span class="sxs-lookup"><span data-stu-id="884be-134">A `CSharpReference` is specified for the `To` argument of the `Assign`, and represents the l-value of the expression.</span></span> <span data-ttu-id="884be-135">A `CSharpValue` için belirtilen `Value` bağımsız değişkeni `Assign`ve `Text` bağımsız değişkeni `WriteLine`, bu iki ifade için r temsil eder.</span><span class="sxs-lookup"><span data-stu-id="884be-135">A `CSharpValue` is specified for the `Value` argument of the `Assign`, and for the `Text` argument of the `WriteLine`, and represents the r-value for those two expressions.</span></span>

```csharp
Variable<int> n = new Variable<int>
{
    Name = "n"
};

Activity wf = new Sequence
{
    Variables = { n },
    Activities =
    {
        new Assign<int>
        {
            To = new CSharpReference<int>("n"),
            Value = new CSharpValue<int>("new Random().Next(1, 101)")
        },
        new WriteLine
        {
            Text = new CSharpValue<string>("\"The number is \" + n")
        }
    }
};

CompileExpressions(wf);

WorkflowInvoker.Invoke(wf);
```

 <span data-ttu-id="884be-136">İş akışı oluşturulur, sonra C# ifadelerini çağırarak derlenir `CompileExpressions` yardımcı yöntem ve iş akışı çağrılır.</span><span class="sxs-lookup"><span data-stu-id="884be-136">After the workflow is constructed, the C# expressions are compiled by calling the `CompileExpressions` helper method and then the workflow is invoked.</span></span> <span data-ttu-id="884be-137">Aşağıdaki örnek, `CompileExpressions` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="884be-137">The following example is the `CompileExpressions` method.</span></span>

```csharp
static void CompileExpressions(Activity activity)
{
    // activityName is the Namespace.Type of the activity that contains the
    // C# expressions.
    string activityName = activity.GetType().ToString();

    // Split activityName into Namespace and Type.Append _CompiledExpressionRoot to the type name
    // to represent the new type that represents the compiled expressions.
    // Take everything after the last . for the type name.
    string activityType = activityName.Split('.').Last() + "_CompiledExpressionRoot";
    // Take everything before the last . for the namespace.
    string activityNamespace = string.Join(".", activityName.Split('.').Reverse().Skip(1).Reverse());

    // Create a TextExpressionCompilerSettings.
    TextExpressionCompilerSettings settings = new TextExpressionCompilerSettings
    {
        Activity = activity,
        Language = "C#",
        ActivityName = activityType,
        ActivityNamespace = activityNamespace,
        RootNamespace = null,
        GenerateAsPartialClass = false,
        AlwaysGenerateSource = true,
        ForImplementation = false
    };

    // Compile the C# expression.
    TextExpressionCompilerResults results =
        new TextExpressionCompiler(settings).Compile();

    // Any compilation errors are contained in the CompilerMessages.
    if (results.HasErrors)
    {
        throw new Exception("Compilation failed.");
    }

    // Create an instance of the new compiled expression type.
    ICompiledExpressionRoot compiledExpressionRoot =
        Activator.CreateInstance(results.ResultType,
            new object[] { activity }) as ICompiledExpressionRoot;

    // Attach it to the activity.
    CompiledExpressionInvoker.SetCompiledExpressionRoot(
        activity, compiledExpressionRoot);
}
```

> [!NOTE]
>  <span data-ttu-id="884be-138">Varsa C# ifadeleri derlenmemiş, bir <xref:System.NotSupportedException> aşağıdakine benzer bir ileti ile iş akışı çalıştırıldığında oluşturulur: `Expression Activity type 'CSharpValue`1' çalıştırmak için derleme gerektirir.</span><span class="sxs-lookup"><span data-stu-id="884be-138">If the C# expressions are not compiled, a <xref:System.NotSupportedException> is thrown when the workflow is invoked with a message similar to the following: `Expression Activity type 'CSharpValue`1' requires compilation in order to run.</span></span>  <span data-ttu-id="884be-139">İş akışı derlendiğinden emin olun.'</span><span class="sxs-lookup"><span data-stu-id="884be-139">Please ensure that the workflow has been compiled.\`</span></span>

 <span data-ttu-id="884be-140">İş akışı kullanan özel kodunuz tabanlıysa `DynamicActivity`, bazı değişiklikler daha sonra `CompileExpressions` yöntemi gereklidir, aşağıdaki kod örneğinde gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="884be-140">If your custom code based workflow uses `DynamicActivity`, then some changes to the `CompileExpressions` method are required, as demonstrated in the following code example.</span></span>

```csharp
static void CompileExpressions(DynamicActivity dynamicActivity)
{
    // activityName is the Namespace.Type of the activity that contains the
    // C# expressions. For Dynamic Activities this can be retrieved using the
    // name property , which must be in the form Namespace.Type.
    string activityName = dynamicActivity.Name;

    // Split activityName into Namespace and Type.Append _CompiledExpressionRoot to the type name
    // to represent the new type that represents the compiled expressions.
    // Take everything after the last . for the type name.
    string activityType = activityName.Split('.').Last() + "_CompiledExpressionRoot";
    // Take everything before the last . for the namespace.
    string activityNamespace = string.Join(".", activityName.Split('.').Reverse().Skip(1).Reverse());

    // Create a TextExpressionCompilerSettings.
    TextExpressionCompilerSettings settings = new TextExpressionCompilerSettings
    {
        Activity = dynamicActivity,
        Language = "C#",
        ActivityName = activityType,
        ActivityNamespace = activityNamespace,
        RootNamespace = null,
        GenerateAsPartialClass = false,
        AlwaysGenerateSource = true,
        ForImplementation = true
    };

    // Compile the C# expression.
    TextExpressionCompilerResults results =
        new TextExpressionCompiler(settings).Compile();

    // Any compilation errors are contained in the CompilerMessages.
    if (results.HasErrors)
    {
        throw new Exception("Compilation failed.");
    }

    // Create an instance of the new compiled expression type.
    ICompiledExpressionRoot compiledExpressionRoot =
        Activator.CreateInstance(results.ResultType,
            new object[] { dynamicActivity }) as ICompiledExpressionRoot;

    // Attach it to the activity.
    CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation(
        dynamicActivity, compiledExpressionRoot);
}
```

 <span data-ttu-id="884be-141">Çeşitli farklılıklar vardır `CompileExpressions` C# ifadelerini dinamik etkinliğinde derler aşırı yükleme.</span><span class="sxs-lookup"><span data-stu-id="884be-141">There are several differences in the `CompileExpressions` overload that compiles the C# expressions in a dynamic activity.</span></span>

-   <span data-ttu-id="884be-142">Parametre `CompileExpressions` olduğu bir `DynamicActivity`.</span><span class="sxs-lookup"><span data-stu-id="884be-142">The parameter to `CompileExpressions` is a `DynamicActivity`.</span></span>

-   <span data-ttu-id="884be-143">Ad alanı ve tür adı kullanılarak alınır `DynamicActivity.Name` özelliği.</span><span class="sxs-lookup"><span data-stu-id="884be-143">The type name and namespace are retrieved using the `DynamicActivity.Name` property.</span></span>

-   <span data-ttu-id="884be-144">`TextExpressionCompilerSettings.ForImplementation` ayarlanır `true`.</span><span class="sxs-lookup"><span data-stu-id="884be-144">`TextExpressionCompilerSettings.ForImplementation` is set to `true`.</span></span>

-   <span data-ttu-id="884be-145">`CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation` yerine adlı `CompiledExpressionInvoker.SetCompiledExpressionRoot`.</span><span class="sxs-lookup"><span data-stu-id="884be-145">`CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation` is called instead of `CompiledExpressionInvoker.SetCompiledExpressionRoot`.</span></span>

 <span data-ttu-id="884be-146">Kodda ifadeleri ile çalışma hakkında daha fazla bilgi için bkz. [yazma iş akışları, etkinlikler ve ifadeler kullanarak kesinliği kod](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).</span><span class="sxs-lookup"><span data-stu-id="884be-146">For more information about working with expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>

### <a name="XamlWorkflows"></a> <span data-ttu-id="884be-147">XAML iş akışlarında C# ifadeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="884be-147">Using C# expressions in XAML workflows</span></span>
 <span data-ttu-id="884be-148">C# ifadelerini XAML iş akışlarında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="884be-148">C# expressions are supported in XAML workflows.</span></span> <span data-ttu-id="884be-149">Derlenmiş XAML iş akışı bir tür derlenir ve gevşek XAML iş akışı çalışma zamanı tarafından yüklenir ve iş akışı yürütüldüğünde bir etkinlik ağacına derlenir.</span><span class="sxs-lookup"><span data-stu-id="884be-149">Compiled XAML workflows are compiled into a type, and loose XAML workflows are loaded by the runtime and compiled into an activity tree when the workflow is executed.</span></span>

-   [<span data-ttu-id="884be-150">Derlenmiş Xaml</span><span class="sxs-lookup"><span data-stu-id="884be-150">Compiled Xaml</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CompiledXaml)

-   [<span data-ttu-id="884be-151">Bağımsız Xaml</span><span class="sxs-lookup"><span data-stu-id="884be-151">Loose Xaml</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#LooseXaml)

#### <a name="CompiledXaml"></a> <span data-ttu-id="884be-152">Derlenmiş Xaml</span><span class="sxs-lookup"><span data-stu-id="884be-152">Compiled Xaml</span></span>
 <span data-ttu-id="884be-153">C# ifadeleri bir türe hedefleyen bir C# iş akışı projesi bir parçası olarak derlenen derlenmiş XAML iş akışlarında desteklenir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="884be-153">C# expressions are supported in compiled XAML workflows that are compiled to a type as part of a C# workflow project that targets [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)].</span></span> <span data-ttu-id="884be-154">Derlenmiş XAML iş akışı yazma Visual Studio'da varsayılan türü olduğu ve oluşturulan C# iş akışı projeleri Visual Studio hedefleyen [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] C# ifadeleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="884be-154">Compiled XAML is the default type of workflow authoring in Visual Studio, and C# workflow projects created in Visual Studio that target [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] use C# expressions.</span></span>

#### <a name="LooseXaml"></a> <span data-ttu-id="884be-155">Bağımsız Xaml</span><span class="sxs-lookup"><span data-stu-id="884be-155">Loose Xaml</span></span>
 <span data-ttu-id="884be-156">C# ifadelerini gevşek XAML iş akışlarında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="884be-156">C# expressions are supported in loose XAML workflows.</span></span> <span data-ttu-id="884be-157">İş akışı ana bilgisayar programı yükleyen ve gevşek XAML iş akışı çağırır hedeflemelidir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], ve <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> ayarlanmalıdır `true` (varsayılan değer `false`).</span><span class="sxs-lookup"><span data-stu-id="884be-157">The workflow host program that loads and invokes the loose XAML workflow must target [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], and <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> must be set to `true` (the default is `false`).</span></span> <span data-ttu-id="884be-158">Ayarlanacak <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> için `true`, oluşturun bir <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> ile örnek kendi <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> özelliğini `true`ve bunu bir parametre olarak geçiriyoruz <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="884be-158">To set <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> to `true`, create an <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> instance with its <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> property set to `true`, and pass it as a parameter to <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="884be-159">Varsa `CompileExpressions` ayarlı değil `true`, <xref:System.NotSupportedException> aşağıdakine benzer bir ileti ile oluşturulur: `Expression Activity type 'CSharpValue`1' çalıştırmak için derleme gerektirir.</span><span class="sxs-lookup"><span data-stu-id="884be-159">If `CompileExpressions` Is not set to `true`, a <xref:System.NotSupportedException> will be thrown with a message similar to the following: `Expression Activity type 'CSharpValue`1' requires compilation in order to run.</span></span>  <span data-ttu-id="884be-160">İş akışı derlendiğinden emin olun.'</span><span class="sxs-lookup"><span data-stu-id="884be-160">Please ensure that the workflow has been compiled.\`</span></span>

```csharp
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings
{
    CompileExpressions = true
};

DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;
```

 <span data-ttu-id="884be-161">XAML iş akışları ile çalışma hakkında daha fazla bilgi için bkz. [seri hale getirme iş akışları ve etkinlikler XAML gelen ve giden](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="884be-161">For more information about working with XAML workflows, see [Serializing Workflows and Activities to and from XAML](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md).</span></span>

### <a name="WFServices"></a> <span data-ttu-id="884be-162">C# ifadelerini kullanarak XAMLX iş akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="884be-162">Using C# expressions in XAMLX workflow services</span></span>
 <span data-ttu-id="884be-163">C# ifadelerini XAMLX iş akışı hizmetlerinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="884be-163">C# expressions are supported in XAMLX workflow services.</span></span> <span data-ttu-id="884be-164">Ek bir adım gerekli değildir sonra bir iş akışı hizmeti IIS ya da WAS içinde barındırıldığında, ancak XAML iş akışı hizmeti, şirket içinde barındırılan, C# ifadelerini derlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="884be-164">When a workflow service is hosted in IIS or WAS then no additional steps are required, but if the XAML workflow service is self-hosted, then the C# expressions must be compiled.</span></span> <span data-ttu-id="884be-165">C# ifadelerini şirket içinde barındırılan XAMLX iş akışı hizmeti içinde derlemek için önce XAMLX dosyasına yüklemek bir `WorkflowService`ve ardından geçirmek `Body` , `WorkflowService` için `CompileExpressions` önceki açıklanan yöntemi [kullanarak C# ifadeleri iş akışlarında kod](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) bölümü.</span><span class="sxs-lookup"><span data-stu-id="884be-165">To compile the C# expressions in a self-hosted XAMLX workflow service, first load the XAMLX file into a `WorkflowService`, and then pass the `Body` of the `WorkflowService` to the `CompileExpressions` method described in the previous [Using C# expressions in code workflows](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) section.</span></span> <span data-ttu-id="884be-166">Aşağıdaki örnekte, bir XAMLX iş akışı hizmeti yüklenir, C# ifadelerini derlenir ve sonra iş akışı hizmeti açılır ve istekleri için bekler.</span><span class="sxs-lookup"><span data-stu-id="884be-166">In the following example, a XAMLX workflow service is loaded, the C# expressions are compiled, and then the workflow service is opened and waits for requests.</span></span>

```csharp
// Load the XAMLX workflow service.
WorkflowService workflow1 =
    (WorkflowService)XamlServices.Load(xamlxPath);

// Compile the C# expressions in the workflow by passing the Body to CompileExpressions.
CompileExpressions(workflow1.Body);

// Initialize the WorkflowServiceHost.
var host = new WorkflowServiceHost(workflow1, new Uri("http://localhost:8293/Service1.xamlx"));

// Enable Metadata publishing/
ServiceMetadataBehavior smb = new ServiceMetadataBehavior();
smb.HttpGetEnabled = true;
smb.MetadataExporter.PolicyVersion = PolicyVersion.Policy15;
host.Description.Behaviors.Add(smb);

// Open the WorkflowServiceHost and wait for requests.
host.Open();
Console.WriteLine("Press enter to quit");
Console.ReadLine();
```

 <span data-ttu-id="884be-167">C# ifadelerini derlenmemiş, `Open` işlemi başarılı olur, ancak iş akışı, çağrıldığında başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="884be-167">If the C# expressions are not compiled, the `Open` operation succeeds but the workflow will fail when it is invoked.</span></span> <span data-ttu-id="884be-168">Aşağıdaki `CompileExpressions` yöntemi ile aynıdır önceki yöntem [kullanarak C# ifadeleri iş akışlarında kod](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) bölümü.</span><span class="sxs-lookup"><span data-stu-id="884be-168">The following `CompileExpressions` method is the same as the method from the previous [Using C# expressions in code workflows](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) section.</span></span>

```csharp
static void CompileExpressions(Activity activity)
{
    // activityName is the Namespace.Type of the activity that contains the
    // C# expressions.
    string activityName = activity.GetType().ToString();

    // Split activityName into Namespace and Type.Append _CompiledExpressionRoot to the type name
    // to represent the new type that represents the compiled expressions.
    // Take everything after the last . for the type name.
    string activityType = activityName.Split('.').Last() + "_CompiledExpressionRoot";
    // Take everything before the last . for the namespace.
    string activityNamespace = string.Join(".", activityName.Split('.').Reverse().Skip(1).Reverse());

    // Create a TextExpressionCompilerSettings.
    TextExpressionCompilerSettings settings = new TextExpressionCompilerSettings
    {
        Activity = activity,
        Language = "C#",
        ActivityName = activityType,
        ActivityNamespace = activityNamespace,
        RootNamespace = null,
        GenerateAsPartialClass = false,
        AlwaysGenerateSource = true,
        ForImplementation = false
    };

    // Compile the C# expression.
    TextExpressionCompilerResults results =
        new TextExpressionCompiler(settings).Compile();

    // Any compilation errors are contained in the CompilerMessages.
    if (results.HasErrors)
    {
        throw new Exception("Compilation failed.");
    }

    // Create an instance of the new compiled expression type.
    ICompiledExpressionRoot compiledExpressionRoot =
        Activator.CreateInstance(results.ResultType,
            new object[] { activity }) as ICompiledExpressionRoot;

    // Attach it to the activity.
    CompiledExpressionInvoker.SetCompiledExpressionRoot(
        activity, compiledExpressionRoot);
}
```
