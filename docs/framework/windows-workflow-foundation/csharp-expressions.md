---
title: C# ifadeleri
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 29110be7-f4e3-407e-8dbe-78102eb21115
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f220ffdf04102a110124e7331a53ae5ee70316a3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="c-expressions"></a><span data-ttu-id="569de-102">C# ifadeleri</span><span class="sxs-lookup"><span data-stu-id="569de-102">C# Expressions</span></span>
<span data-ttu-id="569de-103">İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], C# ifadeler de desteklenmektedir [!INCLUDE[wf](../../../includes/wf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="569de-103">Starting with [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], C# expressions are supported in [!INCLUDE[wf](../../../includes/wf-md.md)].</span></span> <span data-ttu-id="569de-104">Yeni C# iş akışı projeleri oluşturulan [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] hedefleyen [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] kullanım C# ifadeleri ve Visual Basic iş akışı projeleri Visual Basic ifadeler kullanın.</span><span class="sxs-lookup"><span data-stu-id="569de-104">New C# workflow projects created in [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] that target [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] use C# expressions, and Visual Basic workflow projects use Visual Basic expressions.</span></span> <span data-ttu-id="569de-105">Varolan [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] Visual Basic ifadeleri kullanma iş akışı projeleri geçiş yapabilir için [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] dil ve bu projenin bağımsız olarak desteklenir.</span><span class="sxs-lookup"><span data-stu-id="569de-105">Existing [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] workflow projects that use Visual Basic expressions can be migrated to [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] regardless of the project language and are supported.</span></span> <span data-ttu-id="569de-106">Bu konu, C# ifadelerinde genel bir bakış sağlar. [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="569de-106">This topic provides an overview of C# expressions in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span>  
  
## <a name="using-c-expressions-in-workflows"></a><span data-ttu-id="569de-107">C# ifadeleri iş akışlarında kullanma</span><span class="sxs-lookup"><span data-stu-id="569de-107">Using C# expressions in workflows</span></span>  
  
-   [<span data-ttu-id="569de-108">İş Akışı Tasarımcısı'nda C# ifadeler kullanma</span><span class="sxs-lookup"><span data-stu-id="569de-108">Using C# expressions in the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#WFDesigner)  
  
    -   [<span data-ttu-id="569de-109">Geriye dönük uyumluluk</span><span class="sxs-lookup"><span data-stu-id="569de-109">Backwards compatibility</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#BackwardCompat)  
  
-   [<span data-ttu-id="569de-110">Kod iş akışlarında C# ifadeler kullanma</span><span class="sxs-lookup"><span data-stu-id="569de-110">Using C# expressions in code workflows</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows)  
  
-   [<span data-ttu-id="569de-111">XAML iş akışlarında C# ifadeler kullanma</span><span class="sxs-lookup"><span data-stu-id="569de-111">Using C# expressions in XAML workflows</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#XamlWorkflows)  
  
    -   [<span data-ttu-id="569de-112">Derlenmiş Xaml</span><span class="sxs-lookup"><span data-stu-id="569de-112">Compiled Xaml</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CompiledXaml)  
  
    -   [<span data-ttu-id="569de-113">Gevşek Xaml</span><span class="sxs-lookup"><span data-stu-id="569de-113">Loose Xaml</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#LooseXaml)  
  
-   [<span data-ttu-id="569de-114">C# ifadeler XAMLX iş akışı hizmetleri kullanma</span><span class="sxs-lookup"><span data-stu-id="569de-114">Using C# expressions in XAMLX workflow services</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#WFServices)  
  
###  <span data-ttu-id="569de-115"><a name="WFDesigner"></a>İş Akışı Tasarımcısı'nda C# ifadeler kullanma</span><span class="sxs-lookup"><span data-stu-id="569de-115"><a name="WFDesigner"></a> Using C# expressions in the Workflow Designer</span></span>  
 <span data-ttu-id="569de-116">İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], C# ifadeler de desteklenmektedir [!INCLUDE[wf](../../../includes/wf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="569de-116">Starting with [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], C# expressions are supported in [!INCLUDE[wf](../../../includes/wf-md.md)].</span></span> <span data-ttu-id="569de-117">C# iş akışı projeleri oluşturulan [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] hedefleyen [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] C# ifadeler, Visual Basic iş akışı projeleri Visual Basic ifadeleri kullanırken kullanın.</span><span class="sxs-lookup"><span data-stu-id="569de-117">C# workflow projects created in [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] that target [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] use C# expressions, while Visual Basic workflow projects use Visual Basic expressions.</span></span> <span data-ttu-id="569de-118">İstenen C# ifade belirtmek için bunu etiketli kutusuna **bir C# ifadesi girin**.</span><span class="sxs-lookup"><span data-stu-id="569de-118">To specify the desired C# expression, type it into the box labeled **Enter a C# expression**.</span></span> <span data-ttu-id="569de-119">Etkinlik Tasarımcısı'nda veya iş akışı Tasarımcısı'nda faaliyete seçildiğinde bu etiket Özellikler penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="569de-119">This label is displayed in the properties window when the activity is selected in the designer, or on the activity in the workflow designer.</span></span> <span data-ttu-id="569de-120">Aşağıdaki örnekte, iki `WriteLine` etkinlikleri içinde bulunan bir `Sequence` içinde bir `NoPersistScope`.</span><span class="sxs-lookup"><span data-stu-id="569de-120">In the following example, two `WriteLine` activities are contained within a `Sequence` inside a `NoPersistScope`.</span></span>  
  
 <span data-ttu-id="569de-121">![Sıralı etkinlik otomatik olarak oluşturulan](../../../docs/framework/windows-workflow-foundation/media/autosurround2.png "AutoSurround2")</span><span class="sxs-lookup"><span data-stu-id="569de-121">![Automatically created sequence activity](../../../docs/framework/windows-workflow-foundation/media/autosurround2.png "AutoSurround2")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="569de-122">C# ifadeleri yalnızca desteklenen [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)]ve yeniden barındırılan iş akışı Tasarımcısı'nda desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="569de-122">C# expressions are supported only in [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)], and are not supported in the re-hosted workflow designer.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="569de-123">bkz: yeniden barındırılan Tasarımcısı'nda desteklenen yeni WF45 özellikleri [Rehosted iş akışı Tasarımcısı'nda yeni iş akışı Foundation 4.5 özellikleri için destek](../../../docs/framework/windows-workflow-foundation/wf-features-in-the-rehosted-workflow-designer.md).</span><span class="sxs-lookup"><span data-stu-id="569de-123"> new WF45 features supported in the re-hosted designer, see [Support for New Workflow Foundation 4.5 Features in the Rehosted Workflow Designer](../../../docs/framework/windows-workflow-foundation/wf-features-in-the-rehosted-workflow-designer.md).</span></span>  
  
####  <span data-ttu-id="569de-124"><a name="BackwardCompat"></a>Geriye dönük uyumluluk</span><span class="sxs-lookup"><span data-stu-id="569de-124"><a name="BackwardCompat"></a> Backwards compatibility</span></span>  
 <span data-ttu-id="569de-125">Visual Basic ifadeleri varolan [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] için geçirilen C# iş akışı projeleri [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] desteklenir.</span><span class="sxs-lookup"><span data-stu-id="569de-125">Visual Basic expressions in existing [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] C# workflow projects that have been migrated to [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] are supported.</span></span> <span data-ttu-id="569de-126">Visual Basic ifadeleri iş akışı Tasarımcısı'nda görüntülendiğinde mevcut Visual Basic ifade metin ile değiştirilir **değeri XAML'de ayarlandığı**, Visual Basic ifade geçerli C# sözdizimi değilse.</span><span class="sxs-lookup"><span data-stu-id="569de-126">When the Visual Basic expressions are viewed in the workflow designer, the text of the existing Visual Basic expression is replaced with **Value was set in XAML**, unless the Visual Basic expression is valid C# syntax.</span></span> <span data-ttu-id="569de-127">Visual Basic ifade geçerli C# sözdizimi ise, ifadesi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="569de-127">If the Visual Basic expression is valid C# syntax, then the expression is displayed.</span></span> <span data-ttu-id="569de-128">Visual Basic ifadeleri C# güncelleştirmek için iş akışı Tasarımcısı'nda düzenleyebilir ve eşdeğer C# ifadeyi belirtin.</span><span class="sxs-lookup"><span data-stu-id="569de-128">To update the Visual Basic expressions to C#, you can edit them in the workflow designer and specify the equivalent C# expression.</span></span> <span data-ttu-id="569de-129">Visual Basic ifadeler için C#, ancak ifadeleri dönüştürülür C# ve Visual Basic geri olmayan iş akışı Tasarımcısı'nda güncelleştirilmiş bir kez güncelleştirmek için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="569de-129">It is not required to update the Visual Basic expressions to C#, but once the expressions are updated in the workflow designer they are converted to C# and may not be reverted to Visual Basic.</span></span>  
  
###  <span data-ttu-id="569de-130"><a name="CodeWorkflows"></a>Kod iş akışlarında C# ifadeler kullanma</span><span class="sxs-lookup"><span data-stu-id="569de-130"><a name="CodeWorkflows"></a> Using C# expressions in code workflows</span></span>  
 <span data-ttu-id="569de-131">C# ifadeler de desteklenmektedir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] kod tabanlı iş akışları, ancak iş akışı çağrılabilir önce C# ifadeler kullanarak derlenmelidir <xref:System.Activities.XamlIntegration.TextExpressionCompiler.Compile%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="569de-131">C# expressions are supported in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] code based workflows, but before the workflow can be invoked the C# expressions must be compiled using <xref:System.Activities.XamlIntegration.TextExpressionCompiler.Compile%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="569de-132">İş akışı yazarları kullanabileceğiniz `CSharpValue` bir ifade r temsil etmek için ve `CSharpReference` l-değeri ifade temsil etmek için.</span><span class="sxs-lookup"><span data-stu-id="569de-132">Workflow authors can use `CSharpValue` to represent the r-value of an expression, and `CSharpReference` to represent the l-value of an expression.</span></span> <span data-ttu-id="569de-133">Aşağıdaki örnekte, bir iş akışı ile oluşturulan bir `Assign` etkinliği ve bir `WriteLine` etkinlik içinde yer alan bir `Sequence` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="569de-133">In the following example, a workflow is created with an `Assign` activity and a `WriteLine` activity contained in a `Sequence` activity.</span></span> <span data-ttu-id="569de-134">A `CSharpReference` için belirtilen `To` bağımsız değişkeni `Assign`ve ifade l-değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="569de-134">A `CSharpReference` is specified for the `To` argument of the `Assign`, and represents the l-value of the expression.</span></span> <span data-ttu-id="569de-135">A `CSharpValue` için belirtilen `Value` bağımsız değişkeni `Assign`ve `Text` bağımsız değişkeni `WriteLine`, bu iki ifadeye r temsil eder.</span><span class="sxs-lookup"><span data-stu-id="569de-135">A `CSharpValue` is specified for the `Value` argument of the `Assign`, and for the `Text` argument of the `WriteLine`, and represents the r-value for those two expressions.</span></span>  
  
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
  
 <span data-ttu-id="569de-136">İş akışı oluşturulan sonra C# ifadeleri çağırarak derlenen `CompileExpressions` yardımcı yöntem ve iş akışı çağrılır.</span><span class="sxs-lookup"><span data-stu-id="569de-136">After the workflow is constructed, the C# expressions are compiled by calling the `CompileExpressions` helper method and then the workflow is invoked.</span></span> <span data-ttu-id="569de-137">Aşağıdaki örnek `CompileExpressions` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="569de-137">The following example is the `CompileExpressions` method.</span></span>  
  
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
>  <span data-ttu-id="569de-138">C# ifadeleri derlenmemiş, bir <xref:System.NotSupportedException> aşağıdakine benzer bir ileti ile iş akışı çağrıldığında oluşturulur: `Expression Activity type 'CSharpValue`1' derleme çalıştırmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="569de-138">If the C# expressions are not compiled, a <xref:System.NotSupportedException> is thrown when the workflow is invoked with a message similar to the following: `Expression Activity type 'CSharpValue`1' requires compilation in order to run.</span></span>  <span data-ttu-id="569de-139">Lütfen iş akışının derlendikten olduğundan emin olun.'</span><span class="sxs-lookup"><span data-stu-id="569de-139">Please ensure that the workflow has been compiled.\`</span></span>  
  
 <span data-ttu-id="569de-140">İş akışı kullanan özel kodunuzu dayalı olarak, `DynamicActivity`, bazı değişiklikler sonra `CompileExpressions` yöntemi gereklidir, aşağıdaki kod örneğinde gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="569de-140">If your custom code based workflow uses `DynamicActivity`, then some changes to the `CompileExpressions` method are required, as demonstrated in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="569de-141">Bazı farklılıklar vardır `CompileExpressions` C# ifadeleri dinamik bir aktivite içinde derler aşırı.</span><span class="sxs-lookup"><span data-stu-id="569de-141">There are several differences in the `CompileExpressions` overload that compiles the C# expressions in a dynamic activity.</span></span>  
  
-   <span data-ttu-id="569de-142">Parametre `CompileExpressions` olan bir `DynamicActivity`.</span><span class="sxs-lookup"><span data-stu-id="569de-142">The parameter to `CompileExpressions` is a `DynamicActivity`.</span></span>  
  
-   <span data-ttu-id="569de-143">Ad alanı ve türü adını kullanarak alınır `DynamicActivity.Name` özelliği.</span><span class="sxs-lookup"><span data-stu-id="569de-143">The type name and namespace are retrieved using the `DynamicActivity.Name` property.</span></span>  
  
-   <span data-ttu-id="569de-144">`TextExpressionCompilerSettings.ForImplementation`ayarlanmış `true`.</span><span class="sxs-lookup"><span data-stu-id="569de-144">`TextExpressionCompilerSettings.ForImplementation` is set to `true`.</span></span>  
  
-   <span data-ttu-id="569de-145">`CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation`yerine adlı `CompiledExpressionInvoker.SetCompiledExpressionRoot`.</span><span class="sxs-lookup"><span data-stu-id="569de-145">`CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation` is called instead of `CompiledExpressionInvoker.SetCompiledExpressionRoot`.</span></span>  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="569de-146">kodda ifadeleri ile çalışma, bkz: [geliştirme iş akışları, etkinlikler ve ifadeler kullanarak kesinliği kod](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).</span><span class="sxs-lookup"><span data-stu-id="569de-146"> working with expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>  
  
###  <span data-ttu-id="569de-147"><a name="XamlWorkflows"></a>XAML iş akışlarında C# ifadeler kullanma</span><span class="sxs-lookup"><span data-stu-id="569de-147"><a name="XamlWorkflows"></a> Using C# expressions in XAML workflows</span></span>  
 <span data-ttu-id="569de-148">C# ifadeleri XAML iş akışlarında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="569de-148">C# expressions are supported in XAML workflows.</span></span> <span data-ttu-id="569de-149">Derlenmiş XAML iş akışı bir türe derlenir ve gevşek XAML iş akışı çalışma zamanı tarafından yüklenen ve iş akışı çalıştırıldığında bir etkinlik ağacına derlenir.</span><span class="sxs-lookup"><span data-stu-id="569de-149">Compiled XAML workflows are compiled into a type, and loose XAML workflows are loaded by the runtime and compiled into an activity tree when the workflow is executed.</span></span>  
  
-   [<span data-ttu-id="569de-150">Derlenmiş Xaml</span><span class="sxs-lookup"><span data-stu-id="569de-150">Compiled Xaml</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CompiledXaml)  
  
-   [<span data-ttu-id="569de-151">Gevşek Xaml</span><span class="sxs-lookup"><span data-stu-id="569de-151">Loose Xaml</span></span>](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#LooseXaml)  
  
####  <span data-ttu-id="569de-152"><a name="CompiledXaml"></a>Derlenmiş Xaml</span><span class="sxs-lookup"><span data-stu-id="569de-152"><a name="CompiledXaml"></a> Compiled Xaml</span></span>  
 <span data-ttu-id="569de-153">C# ifadeleri türüne hedefleyen bir C# iş akışı projesinde bir parçası olarak derlenmiş derlenmiş XAML iş akışlarında desteklenir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="569de-153">C# expressions are supported in compiled XAML workflows that are compiled to a type as part of a C# workflow project that targets [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)].</span></span> <span data-ttu-id="569de-154">Derlenmiş XAML iş akışı içinde yazma varsayılan türü olan [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)], ve C# iş akışı projeleri oluşturulan [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] hedefleyen [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] C# ifadeler kullanın.</span><span class="sxs-lookup"><span data-stu-id="569de-154">Compiled XAML is the default type of workflow authoring in [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)], and C# workflow projects created in [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] that target [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] use C# expressions.</span></span>  
  
####  <span data-ttu-id="569de-155"><a name="LooseXaml"></a>Gevşek Xaml</span><span class="sxs-lookup"><span data-stu-id="569de-155"><a name="LooseXaml"></a> Loose Xaml</span></span>  
 <span data-ttu-id="569de-156">C# ifadeleri gevşek XAML iş akışlarında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="569de-156">C# expressions are supported in loose XAML workflows.</span></span> <span data-ttu-id="569de-157">Yükleyen ve gevşek XAML iş akışı çağıran iş akışı ana bilgisayar programı hedeflemelidir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], ve <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> ayarlanmalıdır `true` (varsayılan `false`).</span><span class="sxs-lookup"><span data-stu-id="569de-157">The workflow host program that loads and invokes the loose XAML workflow must target [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], and <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> must be set to `true` (the default is `false`).</span></span> <span data-ttu-id="569de-158">Ayarlamak için <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> için `true`, oluşturma bir <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> örneği kendi <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> özelliğini `true`ve bir parametre olarak geçirmek <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="569de-158">To set <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> to `true`, create an <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> instance with its <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> property set to `true`, and pass it as a parameter to <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="569de-159">Varsa `CompileExpressions` ayarlanmazsa `true`, <xref:System.NotSupportedException> aşağıdakine benzer bir ileti ile oluşturulur: `Expression Activity type 'CSharpValue`1' derleme çalıştırmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="569de-159">If `CompileExpressions` Is not set to `true`, a <xref:System.NotSupportedException> will be thrown with a message similar to the following: `Expression Activity type 'CSharpValue`1' requires compilation in order to run.</span></span>  <span data-ttu-id="569de-160">Lütfen iş akışının derlendikten olduğundan emin olun.'</span><span class="sxs-lookup"><span data-stu-id="569de-160">Please ensure that the workflow has been compiled.\`</span></span>  
  
```csharp  
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings  
{  
    CompileExpressions = true  
};  
  
DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;  
```  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="569de-161">XAML iş akışlarıyla çalışma, bkz: [seri hale getirme iş akışları ve etkinlikler XAML gelen ve giden](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="569de-161"> working with XAML workflows, see [Serializing Workflows and Activities to and from XAML](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md).</span></span>  
  
###  <span data-ttu-id="569de-162"><a name="WFServices"></a>C# ifadeler XAMLX iş akışı hizmetleri kullanma</span><span class="sxs-lookup"><span data-stu-id="569de-162"><a name="WFServices"></a> Using C# expressions in XAMLX workflow services</span></span>  
 <span data-ttu-id="569de-163">C# ifadeleri XAMLX iş akışı hizmetleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="569de-163">C# expressions are supported in XAMLX workflow services.</span></span> <span data-ttu-id="569de-164">Başka adım gerekli değildir sonra bir iş akışı hizmeti IIS ya da WAS içinde barındırıldığında, ancak XAML iş akışı hizmeti Self barındırılıyorsa, C# ifadeleri derlenmiş gerekir.</span><span class="sxs-lookup"><span data-stu-id="569de-164">When a workflow service is hosted in IIS or WAS then no additional steps are required, but if the XAML workflow service is self-hosted, then the C# expressions must be compiled.</span></span> <span data-ttu-id="569de-165">C# ifadelerinde kendini barındıran XAMLX iş akışı hizmeti derlemek için önce XAMLX dosyasına yüklemek bir `WorkflowService`ve ardından geçirmek `Body` , `WorkflowService` için `CompileExpressions` önceki açıklanan yöntemi [kullanarak C# kod iş akışları ifadelerinde](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) bölümü.</span><span class="sxs-lookup"><span data-stu-id="569de-165">To compile the C# expressions in a self-hosted XAMLX workflow service, first load the XAMLX file into a `WorkflowService`, and then pass the `Body` of the `WorkflowService` to the `CompileExpressions` method described in the previous [Using C# expressions in code workflows](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) section.</span></span> <span data-ttu-id="569de-166">Aşağıdaki örnekte, XAMLX iş akışı hizmeti yüklenmiş, C# ifadeleri derlenir ve iş akışı hizmeti açıldıktan sonra istekleri için bekler.</span><span class="sxs-lookup"><span data-stu-id="569de-166">In the following example, a XAMLX workflow service is loaded, the C# expressions are compiled, and then the workflow service is opened and waits for requests.</span></span>  
  
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
  
 <span data-ttu-id="569de-167">C# ifadeleri derlenmemiş, `Open` işlemi başarılı olur, ancak çalıştırıldığında iş akışının başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="569de-167">If the C# expressions are not compiled, the `Open` operation succeeds but the workflow will fail when it is invoked.</span></span> <span data-ttu-id="569de-168">Aşağıdaki `CompileExpressions` yöntemi aynıdır önceki yöntemi [kullanarak C# kod iş akışları ifadelerinde](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) bölümü.</span><span class="sxs-lookup"><span data-stu-id="569de-168">The following `CompileExpressions` method is the same as the method from the previous [Using C# expressions in code workflows](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) section.</span></span>  
  
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
