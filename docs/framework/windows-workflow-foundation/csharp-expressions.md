---
title: C# İfadeleri
ms.date: 03/30/2017
ms.assetid: 29110be7-f4e3-407e-8dbe-78102eb21115
ms.openlocfilehash: d1728758a4f1af76c2d08695a83c0f9acc3dde3e
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74140088"
---
# <a name="c-expressions"></a><span data-ttu-id="cd052-102">C# İfadeleri</span><span class="sxs-lookup"><span data-stu-id="cd052-102">C# Expressions</span></span>
<span data-ttu-id="cd052-103">.NET Framework 4,5 ' den başlayarak C# , WINDOWS Workflow FOUNDATION (WF) içinde ifadeler desteklenir.</span><span class="sxs-lookup"><span data-stu-id="cd052-103">Starting with .NET Framework 4.5, C# expressions are supported in Windows Workflow Foundation (WF).</span></span> <span data-ttu-id="cd052-104">Visual C# Studio 2012 ' de oluşturulan yeni iş akışı projeleri .NET Framework 4,5 kullanın C# ve Visual Basic iş akışı projeleri Visual Basic ifadelerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="cd052-104">New C# workflow projects created in Visual Studio 2012 that target .NET Framework 4.5 use C# expressions, and Visual Basic workflow projects use Visual Basic expressions.</span></span> <span data-ttu-id="cd052-105">Visual Basic ifadelerini kullanan mevcut .NET Framework 4 iş akışı projeleri proje dilinden bağımsız olarak [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] geçirilebilir ve desteklenir.</span><span class="sxs-lookup"><span data-stu-id="cd052-105">Existing .NET Framework 4 workflow projects that use Visual Basic expressions can be migrated to [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] regardless of the project language and are supported.</span></span> <span data-ttu-id="cd052-106">Bu konu, [!INCLUDE[wf1](../../../includes/wf1-md.md)]C# ifadelerde bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="cd052-106">This topic provides an overview of C# expressions in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span>

## <a name="using-c-expressions-in-workflows"></a><span data-ttu-id="cd052-107">İş C# akışlarında ifadeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="cd052-107">Using C# expressions in workflows</span></span>

- [<span data-ttu-id="cd052-108">İş Akışı Tasarımcısı C# ifadeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="cd052-108">Using C# expressions in the Workflow Designer</span></span>](csharp-expressions.md#WFDesigner)

  - [<span data-ttu-id="cd052-109">Geriye dönük uyumluluk</span><span class="sxs-lookup"><span data-stu-id="cd052-109">Backwards compatibility</span></span>](csharp-expressions.md#BackwardCompat)

- [<span data-ttu-id="cd052-110">Kod C# iş akışlarında ifadeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="cd052-110">Using C# expressions in code workflows</span></span>](csharp-expressions.md#CodeWorkflows)

- [<span data-ttu-id="cd052-111">XAML C# iş akışlarında ifadeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="cd052-111">Using C# expressions in XAML workflows</span></span>](csharp-expressions.md#XamlWorkflows)

  - [<span data-ttu-id="cd052-112">Derlenen xaml</span><span class="sxs-lookup"><span data-stu-id="cd052-112">Compiled Xaml</span></span>](csharp-expressions.md#CompiledXaml)

  - [<span data-ttu-id="cd052-113">Gevşek XAML</span><span class="sxs-lookup"><span data-stu-id="cd052-113">Loose Xaml</span></span>](csharp-expressions.md#LooseXaml)

- [<span data-ttu-id="cd052-114">XAMLX C# iş akışı hizmetlerinde ifadeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="cd052-114">Using C# expressions in XAMLX workflow services</span></span>](csharp-expressions.md#WFServices)

### <a name="WFDesigner"></a><span data-ttu-id="cd052-115">İş Akışı Tasarımcısı C# ifadeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="cd052-115">Using C# expressions in the Workflow Designer</span></span>

<span data-ttu-id="cd052-116">.NET Framework 4,5 ' den başlayarak C# , WINDOWS Workflow FOUNDATION (WF) içinde ifadeler desteklenir.</span><span class="sxs-lookup"><span data-stu-id="cd052-116">Starting with .NET Framework 4.5, C# expressions are supported in Windows Workflow Foundation (WF).</span></span> <span data-ttu-id="cd052-117">C#Visual Studio 2012 ' de oluşturulan iş akışı projeleri .NET Framework 4,5 C# ' i hedef Visual Basic iş akışı projeleri Visual Basic ifadeler kullanır.</span><span class="sxs-lookup"><span data-stu-id="cd052-117">C# workflow projects created in Visual Studio 2012 that target .NET Framework 4.5 use C# expressions, while Visual Basic workflow projects use Visual Basic expressions.</span></span> <span data-ttu-id="cd052-118">İstenen C# ifadeyi belirtmek için,  **C# ifadeyi ifade girin**etiketli kutuya yazın.</span><span class="sxs-lookup"><span data-stu-id="cd052-118">To specify the desired C# expression, type it into the box labeled **Enter a C# expression**.</span></span> <span data-ttu-id="cd052-119">Bu etiket, tasarımcı içinde etkinlik seçildiğinde veya iş akışı tasarımcısında etkinlik olduğunda Özellikler penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="cd052-119">This label is displayed in the properties window when the activity is selected in the designer, or on the activity in the workflow designer.</span></span> <span data-ttu-id="cd052-120">Aşağıdaki örnekte, iki `WriteLine` etkinlik `NoPersistScope`içindeki bir `Sequence` içinde yer alır.</span><span class="sxs-lookup"><span data-stu-id="cd052-120">In the following example, two `WriteLine` activities are contained within a `Sequence` inside a `NoPersistScope`.</span></span>

![Otomatik olarak oluşturulan bir sıra etkinliğini gösteren ekran görüntüsü.](./media/csharp-expressions/auto-surround-sequence-activity.png)

> [!NOTE]
> <span data-ttu-id="cd052-122">C#ifadeler yalnızca Visual Studio 'da desteklenir ve yeniden barındırılan iş akışı tasarımcısında desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="cd052-122">C# expressions are supported only in Visual Studio, and are not supported in the re-hosted workflow designer.</span></span> <span data-ttu-id="cd052-123">Yeniden barındırılan tasarımcıda desteklenen yeni WF45 özellikleri hakkında daha fazla bilgi için bkz. [yeniden barındırılan iş akışı Tasarımcısı yeni Workflow Foundation 4,5 özellikleri Için destek](wf-features-in-the-rehosted-workflow-designer.md).</span><span class="sxs-lookup"><span data-stu-id="cd052-123">For more information about new WF45 features supported in the re-hosted designer, see [Support for New Workflow Foundation 4.5 Features in the Rehosted Workflow Designer](wf-features-in-the-rehosted-workflow-designer.md).</span></span>

#### <a name="BackwardCompat"></a><span data-ttu-id="cd052-124">Geriye dönük uyumluluk</span><span class="sxs-lookup"><span data-stu-id="cd052-124">Backwards compatibility</span></span>

<span data-ttu-id="cd052-125">[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 'e geçirilmiş mevcut .NET Framework 4 C# iş akışı projelerindeki Visual Basic ifadeler desteklenir.</span><span class="sxs-lookup"><span data-stu-id="cd052-125">Visual Basic expressions in existing .NET Framework 4 C# workflow projects that have been migrated to [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] are supported.</span></span> <span data-ttu-id="cd052-126">Visual Basic ifadeleri iş akışı tasarımcısında görüntülendiğinde, Visual Basic ifadesi geçerli C# bir sözdizimi olmadığı takdirde, varolan Visual Basic IFADESININ metni **xaml 'de ayarlanmış**olarak değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="cd052-126">When the Visual Basic expressions are viewed in the workflow designer, the text of the existing Visual Basic expression is replaced with **Value was set in XAML**, unless the Visual Basic expression is valid C# syntax.</span></span> <span data-ttu-id="cd052-127">Visual Basic ifadesi geçerli C# sözdizimidir, ifade görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="cd052-127">If the Visual Basic expression is valid C# syntax, then the expression is displayed.</span></span> <span data-ttu-id="cd052-128">Visual Basic ifadelerini ' ye C#güncelleştirmek için, onları iş akışı tasarımcısında düzenleyebilir ve denk C# ifadeyi belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cd052-128">To update the Visual Basic expressions to C#, you can edit them in the workflow designer and specify the equivalent C# expression.</span></span> <span data-ttu-id="cd052-129">Visual Basic ifadelerin C#' a güncelleştirilmesi gerekmez, ancak ifadeler ' e dönüştürüledikleri C# iş akışı tasarımcısında güncelleştirildikten sonra Visual Basic geri döndürülemez.</span><span class="sxs-lookup"><span data-stu-id="cd052-129">It is not required to update the Visual Basic expressions to C#, but once the expressions are updated in the workflow designer they are converted to C# and may not be reverted to Visual Basic.</span></span>

### <a name="CodeWorkflows"></a><span data-ttu-id="cd052-130">Kod C# iş akışlarında ifadeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="cd052-130">Using C# expressions in code workflows</span></span>

<span data-ttu-id="cd052-131">C#ifadeler [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] kod tabanlı iş akışlarında desteklenir, ancak iş akışı çağrmadan önce, C# ifadelerin <xref:System.Activities.XamlIntegration.TextExpressionCompiler.Compile%2A?displayProperty=nameWithType>kullanılarak derlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="cd052-131">C# expressions are supported in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] code based workflows, but before the workflow can be invoked the C# expressions must be compiled using <xref:System.Activities.XamlIntegration.TextExpressionCompiler.Compile%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="cd052-132">Workflow yazarları, bir ifadenin r-değerini temsil etmek için `CSharpValue` kullanabilir ve bir ifadenin l-değerini temsil `CSharpReference`.</span><span class="sxs-lookup"><span data-stu-id="cd052-132">Workflow authors can use `CSharpValue` to represent the r-value of an expression, and `CSharpReference` to represent the l-value of an expression.</span></span> <span data-ttu-id="cd052-133">Aşağıdaki örnekte, bir `Assign` etkinliği ve bir `Sequence` etkinliğinde bulunan `WriteLine` etkinliği ile bir iş akışı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="cd052-133">In the following example, a workflow is created with an `Assign` activity and a `WriteLine` activity contained in a `Sequence` activity.</span></span> <span data-ttu-id="cd052-134">`Assign``To` bağımsız değişkeni için `CSharpReference` belirtilir ve ifadenin l-değerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="cd052-134">A `CSharpReference` is specified for the `To` argument of the `Assign`, and represents the l-value of the expression.</span></span> <span data-ttu-id="cd052-135">`Assign``Value` bağımsız değişkeni ve `WriteLine``Text` bağımsız değişkeni için `CSharpValue` belirtilir ve bu iki ifade için r-değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="cd052-135">A `CSharpValue` is specified for the `Value` argument of the `Assign`, and for the `Text` argument of the `WriteLine`, and represents the r-value for those two expressions.</span></span>

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

<span data-ttu-id="cd052-136">İş akışı oluşturulduktan sonra, C# ifadeler `CompileExpressions` yardımcı yöntemi çağırarak ve sonra iş akışı çağrıldığında derlenir.</span><span class="sxs-lookup"><span data-stu-id="cd052-136">After the workflow is constructed, the C# expressions are compiled by calling the `CompileExpressions` helper method and then the workflow is invoked.</span></span> <span data-ttu-id="cd052-137">Aşağıdaki örnek `CompileExpressions` yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="cd052-137">The following example is the `CompileExpressions` method.</span></span>

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
> <span data-ttu-id="cd052-138">C# İfadeler derlenmeyecekse, iş akışı aşağıdakine benzer bir iletiyle çağrıldığında bir <xref:System.NotSupportedException> oluşturulur: `Expression Activity type 'CSharpValue`1 ' çalıştırmak için derleme gerektirir.</span><span class="sxs-lookup"><span data-stu-id="cd052-138">If the C# expressions are not compiled, a <xref:System.NotSupportedException> is thrown when the workflow is invoked with a message similar to the following: `Expression Activity type 'CSharpValue`1' requires compilation in order to run.</span></span>  <span data-ttu-id="cd052-139">Lütfen iş akışının derlendiğinden emin olun. '</span><span class="sxs-lookup"><span data-stu-id="cd052-139">Please ensure that the workflow has been compiled.\`</span></span>

<span data-ttu-id="cd052-140">Özel kod tabanlı iş akışınız `DynamicActivity`kullanıyorsa, aşağıdaki kod örneğinde gösterildiği gibi, `CompileExpressions` yönteminde bazı değişiklikler yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="cd052-140">If your custom code based workflow uses `DynamicActivity`, then some changes to the `CompileExpressions` method are required, as demonstrated in the following code example.</span></span>

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

<span data-ttu-id="cd052-141">Dinamik bir etkinlikte C# ifadeleri derleyen `CompileExpressions` aşırı yüklemede çeşitli farklılıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="cd052-141">There are several differences in the `CompileExpressions` overload that compiles the C# expressions in a dynamic activity.</span></span>

- <span data-ttu-id="cd052-142">`CompileExpressions` parametresi bir `DynamicActivity`.</span><span class="sxs-lookup"><span data-stu-id="cd052-142">The parameter to `CompileExpressions` is a `DynamicActivity`.</span></span>

- <span data-ttu-id="cd052-143">Tür adı ve ad alanı `DynamicActivity.Name` özelliği kullanılarak alınır.</span><span class="sxs-lookup"><span data-stu-id="cd052-143">The type name and namespace are retrieved using the `DynamicActivity.Name` property.</span></span>

- <span data-ttu-id="cd052-144">`TextExpressionCompilerSettings.ForImplementation` `true`olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="cd052-144">`TextExpressionCompilerSettings.ForImplementation` is set to `true`.</span></span>

- <span data-ttu-id="cd052-145">`CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation` `CompiledExpressionInvoker.SetCompiledExpressionRoot`yerine çağrılır.</span><span class="sxs-lookup"><span data-stu-id="cd052-145">`CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation` is called instead of `CompiledExpressionInvoker.SetCompiledExpressionRoot`.</span></span>

<span data-ttu-id="cd052-146">Koddaki ifadelerle çalışma hakkında daha fazla bilgi için, bkz. [using Iş akışları, etkinlikler ve ifadeleri, zorunlu kod kullanarak yazma](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span><span class="sxs-lookup"><span data-stu-id="cd052-146">For more information about working with expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>

### <a name="XamlWorkflows"></a><span data-ttu-id="cd052-147">XAML C# iş akışlarında ifadeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="cd052-147">Using C# expressions in XAML workflows</span></span>

<span data-ttu-id="cd052-148">C#ifadeler XAML iş akışlarında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="cd052-148">C# expressions are supported in XAML workflows.</span></span> <span data-ttu-id="cd052-149">Derlenmiş XAML iş akışları bir türe derlenir ve gevşek XAML iş akışları çalışma zamanı tarafından yüklenir ve iş akışı yürütüldüğünde bir etkinlik ağacına derlenir.</span><span class="sxs-lookup"><span data-stu-id="cd052-149">Compiled XAML workflows are compiled into a type, and loose XAML workflows are loaded by the runtime and compiled into an activity tree when the workflow is executed.</span></span>

- [<span data-ttu-id="cd052-150">Derlenen xaml</span><span class="sxs-lookup"><span data-stu-id="cd052-150">Compiled Xaml</span></span>](csharp-expressions.md#CompiledXaml)

- [<span data-ttu-id="cd052-151">Gevşek XAML</span><span class="sxs-lookup"><span data-stu-id="cd052-151">Loose Xaml</span></span>](csharp-expressions.md#LooseXaml)

#### <a name="CompiledXaml"></a><span data-ttu-id="cd052-152">Derlenen xaml</span><span class="sxs-lookup"><span data-stu-id="cd052-152">Compiled Xaml</span></span>

<span data-ttu-id="cd052-153">C#ifadeler, [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]hedefleyen bir C# iş akışı projesinin parçası olarak bir türe derlenen derlenmiş xaml iş akışlarında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="cd052-153">C# expressions are supported in compiled XAML workflows that are compiled to a type as part of a C# workflow project that targets [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)].</span></span> <span data-ttu-id="cd052-154">Derlenmiş XAML, Visual Studio 'da varsayılan iş akışı yazma türüdür ve C# Visual Studio 'da oluşturulan iş akışı projeleri [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] kullanın. C#</span><span class="sxs-lookup"><span data-stu-id="cd052-154">Compiled XAML is the default type of workflow authoring in Visual Studio, and C# workflow projects created in Visual Studio that target [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] use C# expressions.</span></span>

#### <a name="LooseXaml"></a><span data-ttu-id="cd052-155">Gevşek XAML</span><span class="sxs-lookup"><span data-stu-id="cd052-155">Loose Xaml</span></span>

<span data-ttu-id="cd052-156">C#ifadeler gevşek XAML iş akışlarında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="cd052-156">C# expressions are supported in loose XAML workflows.</span></span> <span data-ttu-id="cd052-157">Gevşek XAML iş akışını yükleyen ve çağıran iş akışı konak programı [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]hedeflemelidir ve <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> `true` olarak ayarlanması gerekir (varsayılan değer `false`).</span><span class="sxs-lookup"><span data-stu-id="cd052-157">The workflow host program that loads and invokes the loose XAML workflow must target [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], and <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> must be set to `true` (the default is `false`).</span></span> <span data-ttu-id="cd052-158"><xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> `true`olarak ayarlamak için <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> özelliği `true`olarak ayarlanmış bir <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> örneği oluşturun ve <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>bir parametre olarak geçirin.</span><span class="sxs-lookup"><span data-stu-id="cd052-158">To set <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> to `true`, create an <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> instance with its <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> property set to `true`, and pass it as a parameter to <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="cd052-159">`CompileExpressions` `true`olarak ayarlanmamışsa aşağıdakine benzer bir ileti içeren bir <xref:System.NotSupportedException> oluşturulur: `Expression Activity type 'CSharpValue`1 ' çalıştırmak için derleme gerektirir.</span><span class="sxs-lookup"><span data-stu-id="cd052-159">If `CompileExpressions` Is not set to `true`, a <xref:System.NotSupportedException> will be thrown with a message similar to the following: `Expression Activity type 'CSharpValue`1' requires compilation in order to run.</span></span>  <span data-ttu-id="cd052-160">Lütfen iş akışının derlendiğinden emin olun. '</span><span class="sxs-lookup"><span data-stu-id="cd052-160">Please ensure that the workflow has been compiled.\`</span></span>

```csharp
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings
{
    CompileExpressions = true
};

DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;
```

<span data-ttu-id="cd052-161">XAML iş akışlarıyla çalışma hakkında daha fazla bilgi için bkz. [xaml 'de ve xaml 'de Iş akışlarını ve etkinlikleri serileştirme](serializing-workflows-and-activities-to-and-from-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="cd052-161">For more information about working with XAML workflows, see [Serializing Workflows and Activities to and from XAML](serializing-workflows-and-activities-to-and-from-xaml.md).</span></span>

### <a name="WFServices"></a><span data-ttu-id="cd052-162">XAMLX C# iş akışı hizmetlerinde ifadeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="cd052-162">Using C# expressions in XAMLX workflow services</span></span>

<span data-ttu-id="cd052-163">C#ifadeler XAMLX iş akışı hizmetlerinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="cd052-163">C# expressions are supported in XAMLX workflow services.</span></span> <span data-ttu-id="cd052-164">Bir iş akışı hizmeti IIS 'de barındırıldığında veya ek adımlar gerekli olmadığında, ancak XAML iş akışı hizmeti kendiliğinden barındırılıyorsa, C# ifadelerin derlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="cd052-164">When a workflow service is hosted in IIS or WAS then no additional steps are required, but if the XAML workflow service is self-hosted, then the C# expressions must be compiled.</span></span> <span data-ttu-id="cd052-165">Kendi kendine barındırılan C# bir xamlx iş akışı hizmetindeki ifadeleri derlemek için, önce xamlx dosyasını bir `WorkflowService`yükleyin ve ardından `WorkflowService` `Body`, [kod iş akışlarında önceki C# ifadeleri kullanma](csharp-expressions.md#CodeWorkflows) bölümünde açıklanan `CompileExpressions` yöntemine geçirin.</span><span class="sxs-lookup"><span data-stu-id="cd052-165">To compile the C# expressions in a self-hosted XAMLX workflow service, first load the XAMLX file into a `WorkflowService`, and then pass the `Body` of the `WorkflowService` to the `CompileExpressions` method described in the previous [Using C# expressions in code workflows](csharp-expressions.md#CodeWorkflows) section.</span></span> <span data-ttu-id="cd052-166">Aşağıdaki örnekte, bir XAMLX iş akışı hizmeti yüklenir, C# ifadeler derlenir ve sonra iş akışı hizmeti açılır ve istekler için bekler.</span><span class="sxs-lookup"><span data-stu-id="cd052-166">In the following example, a XAMLX workflow service is loaded, the C# expressions are compiled, and then the workflow service is opened and waits for requests.</span></span>

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

<span data-ttu-id="cd052-167">C# İfadeler derlenmediği zaman, `Open` işlemi başarılı olur ancak iş akışı çağrıldığında başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="cd052-167">If the C# expressions are not compiled, the `Open` operation succeeds but the workflow will fail when it is invoked.</span></span> <span data-ttu-id="cd052-168">Aşağıdaki `CompileExpressions` yöntemi, [kod iş akışlarında önceki C# using deyimleriyle](csharp-expressions.md#CodeWorkflows) aynı yöntemle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="cd052-168">The following `CompileExpressions` method is the same as the method from the previous [Using C# expressions in code workflows](csharp-expressions.md#CodeWorkflows) section.</span></span>

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
