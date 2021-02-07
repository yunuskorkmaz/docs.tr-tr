---
description: 'Daha fazla bilgi edinin: C# ifadeleri'
title: C# İfadeleri
ms.date: 03/30/2017
ms.assetid: 29110be7-f4e3-407e-8dbe-78102eb21115
ms.openlocfilehash: ce918bb96164643f1adbc73f749d2b5f88f4eb3e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742816"
---
# <a name="c-expressions"></a>C# İfadeleri

.NET Framework 4,5 ' den başlayarak, C# ifadeleri Windows Workflow Foundation (WF) içinde desteklenir. Visual Studio 2012 ' de oluşturulan ve .NET Framework 4,5 ' i hedefleyen yeni C# iş akışı projeleri C# ifadelerini kullanır ve Visual Basic iş akışı projeleri Visual Basic ifadelerini kullanır. Visual Basic ifadelerini kullanan mevcut .NET Framework 4 iş akışı projeleri [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] Proje dilinden bağımsız olarak geçirilebilir ve desteklenir. Bu konu, içindeki C# ifadelerine genel bir bakış sağlar [!INCLUDE[wf1](../../../includes/wf1-md.md)] .

## <a name="using-c-expressions-in-workflows"></a>İş akışlarında C# ifadeleri kullanma

- [İş Akışı Tasarımcısı C# ifadeleri kullanma](csharp-expressions.md#WFDesigner)

  - [Geriye dönük uyumluluk](csharp-expressions.md#BackwardCompat)

- [Kod iş akışlarında C# ifadeleri kullanma](csharp-expressions.md#CodeWorkflows)

- [XAML iş akışlarında C# ifadeleri kullanma](csharp-expressions.md#XamlWorkflows)

  - [Derlenen xaml](csharp-expressions.md#CompiledXaml)

  - [Gevşek XAML](csharp-expressions.md#LooseXaml)

- [XAMLX iş akışı hizmetlerinde C# ifadeleri kullanma](csharp-expressions.md#WFServices)

### <a name="using-c-expressions-in-the-workflow-designer"></a><a name="WFDesigner"></a> İş Akışı Tasarımcısı C# ifadeleri kullanma

.NET Framework 4,5 ' den başlayarak, C# ifadeleri Windows Workflow Foundation (WF) içinde desteklenir. Visual Studio 2012 ' de oluşturulan ve .NET Framework 4,5 ' i hedefleyen C# ifadeleri Visual Basic iş akışı projelerinin Visual Basic ifadeleri kullandığı bir c# iş akışı projesi. İstenen C# ifadesini belirtmek için, **C# ifadesi girin** etiketli kutuya yazın. Bu etiket, tasarımcı içinde etkinlik seçildiğinde veya iş akışı tasarımcısında etkinlik olduğunda Özellikler penceresinde görüntülenir. Aşağıdaki örnekte, `WriteLine` bir içinde iki etkinlik bulunur `Sequence` `NoPersistScope` .

![Otomatik olarak oluşturulan bir sıra etkinliğini gösteren ekran görüntüsü.](./media/csharp-expressions/auto-surround-sequence-activity.png)

> [!NOTE]
> C# ifadeleri yalnızca Visual Studio 'da desteklenir ve yeniden barındırılan iş akışı tasarımcısında desteklenmez. Yeniden barındırılan tasarımcıda desteklenen yeni WF45 özellikleri hakkında daha fazla bilgi için bkz. [yeniden barındırılan iş akışı Tasarımcısı yeni Workflow Foundation 4,5 özellikleri Için destek](wf-features-in-the-rehosted-workflow-designer.md).

#### <a name="backwards-compatibility"></a><a name="BackwardCompat"></a> Geriye dönük uyumluluk

' A geçirilmiş olan mevcut .NET Framework 4 C# iş akışı projelerindeki Visual Basic ifadeler [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] desteklenir. Visual Basic ifadeleri iş akışı tasarımcısında görüntülendiğinde, Visual Basic ifadesi geçerli bir C# sözdizimi olmadığı müddetçe, varolan Visual Basic ifadesinin metni **xaml 'de ayarlanmış** olarak değiştirilmiştir. Visual Basic ifadesi geçerli C# söz dizimine göre ifadesi görüntülenir. Visual Basic ifadelerini C# olarak güncelleştirmek için, iş akışı tasarımcısında düzenleyebilir ve eşdeğer C# ifadesini belirtebilirsiniz. Visual Basic ifadelerin C# olarak güncelleştirilmesi gerekmez, ancak ifadeler iş akışı tasarımcısında güncelleştirildikten sonra C# ' a dönüştürülebilirler ve Visual Basic geri döndürülemez.

### <a name="using-c-expressions-in-code-workflows"></a><a name="CodeWorkflows"></a> Kod iş akışlarında C# ifadeleri kullanma

C# ifadeleri [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] kod tabanlı iş akışlarında desteklenir, ancak iş akışı çağrmadan önce c# ifadelerinin kullanılarak derlenmesi gerekir <xref:System.Activities.XamlIntegration.TextExpressionCompiler.Compile%2A?displayProperty=nameWithType> . İş akışı yazarları `CSharpValue` , bir ifadenin r-değerini temsil etmek ve `CSharpReference` bir ifadenin l-değerini göstermek için kullanabilir. Aşağıdaki örnekte, bir etkinlik ve etkinlik içeren bir etkinlik ile bir iş akışı oluşturulur `Assign` `WriteLine` `Sequence` . , `CSharpReference` `To` Öğesinin bağımsız değişkeni için belirtilir `Assign` ve ifadenin l-değerini temsil eder. , Öğesinin `CSharpValue` `Value` bağımsız değişkeni için ve bağımsız değişkeni için belirtilir `Assign` `Text` `WriteLine` ve bu iki ifade için r-değerini temsil eder.

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

İş akışı oluşturulduktan sonra, C# ifadeleri `CompileExpressions` yardımcı yöntemi çağırarak ve sonra iş akışı çağrıldığında derlenir. Aşağıdaki örnek `CompileExpressions` yöntemidir.

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
> C# ifadeleri derlenmeyecekse, <xref:System.NotSupportedException> iş akışı aşağıdakine benzer bir iletiyle çağrıldığında bir oluşturulur: `Expression Activity type 'CSharpValue` 1 ' çalıştırmak için derleme gerektirir.  Lütfen iş akışının derlendiğinden emin olun. '

Özel kod tabanlı iş akışınız kullanıyorsa `DynamicActivity` , `CompileExpressions` Aşağıdaki kod örneğinde gösterildiği gibi yönteminde bazı değişiklikler yapmanız gerekir.

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

`CompileExpressions`Aşırı yüklemede, C# ifadelerini dinamik bir etkinlikte derleyen birkaç fark vardır.

- Parametresi `CompileExpressions` bir `DynamicActivity` .

- Tür adı ve ad alanı özelliği kullanılarak alınır `DynamicActivity.Name` .

- `TextExpressionCompilerSettings.ForImplementation` , olarak ayarlanır `true` .

- `CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation` yerine çağrılır `CompiledExpressionInvoker.SetCompiledExpressionRoot` .

Koddaki ifadelerle çalışma hakkında daha fazla bilgi için, bkz. [using Iş akışları, etkinlikler ve ifadeleri, zorunlu kod kullanarak yazma](authoring-workflows-activities-and-expressions-using-imperative-code.md).

### <a name="using-c-expressions-in-xaml-workflows"></a><a name="XamlWorkflows"></a> XAML iş akışlarında C# ifadeleri kullanma

C# ifadeleri XAML iş akışlarında desteklenir. Derlenmiş XAML iş akışları bir türe derlenir ve gevşek XAML iş akışları çalışma zamanı tarafından yüklenir ve iş akışı yürütüldüğünde bir etkinlik ağacına derlenir.

- [Derlenen xaml](csharp-expressions.md#CompiledXaml)

- [Gevşek XAML](csharp-expressions.md#LooseXaml)

#### <a name="compiled-xaml"></a><a name="CompiledXaml"></a> Derlenen xaml

C# ifadeleri, hedefleyen bir C# iş akışı projesinin parçası olarak bir türe derlenen derlenmiş XAML iş akışlarında desteklenir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] . Derlenmiş XAML, Visual Studio 'da varsayılan iş akışı yazma türüdür ve Visual Studio 'da oluşturulan C# deyimlerini kullanan C# iş akışı projeleri [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] .

#### <a name="loose-xaml"></a><a name="LooseXaml"></a> Gevşek XAML

C# ifadeleri gevşek XAML iş akışlarında desteklenir. Gevşek XAML iş akışını yükleyen ve çağıran iş akışı konak programı hedeflemelidir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] ve <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> `true` (varsayılan) olarak ayarlanmalıdır `false` . Öğesini olarak ayarlamak için, <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> `true` özelliği olarak <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> ayarlanmış bir örnek oluşturun <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> `true` ve bunu parametresi olarak geçirin <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType> . `CompileExpressions`, Olarak ayarlanmamışsa `true` <xref:System.NotSupportedException> aşağıdakine benzer bir iletiyle birlikte oluşturulur: `Expression Activity type 'CSharpValue` 1 ' çalıştırmak için derleme gerektirir.  Lütfen iş akışının derlendiğinden emin olun. '

```csharp
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings
{
    CompileExpressions = true
};

DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;
```

XAML iş akışlarıyla çalışma hakkında daha fazla bilgi için bkz. [xaml 'de ve xaml 'de Iş akışlarını ve etkinlikleri serileştirme](serializing-workflows-and-activities-to-and-from-xaml.md).

### <a name="using-c-expressions-in-xamlx-workflow-services"></a><a name="WFServices"></a> XAMLX iş akışı hizmetlerinde C# ifadeleri kullanma

C# ifadeleri XAMLX iş akışı hizmetlerinde desteklenir. Bir iş akışı hizmeti IIS 'de barındırıldığında veya ek adımlar gerekli olmadığında, ancak XAML iş akışı hizmeti kendiliğinden barındırılıyorsa, C# ifadelerinin derlenmesi gerekir. C# deyimlerini şirket içinde barındırılan bir XAMLX iş akışı hizmetinde derlemek için, önce XAMLX dosyasını bir ' a yükleyin `WorkflowService` ve ardından öğesini `Body` `WorkflowService` `CompileExpressions` [kod iş akışlarında önceki C# ifadelerinde](csharp-expressions.md#CodeWorkflows) açıklanan yönteme geçirin. Aşağıdaki örnekte, bir XAMLX iş akışı hizmeti yüklenir, C# ifadeleri derlenir ve sonra iş akışı hizmeti açılır ve istekler için bekler.

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

C# ifadeleri derlenmeyecekse, `Open` işlem başarılı olur ancak çağrıldığında iş akışı başarısız olur. Aşağıdaki `CompileExpressions` Yöntem, [kod iş akışlarında önceki C# ifadeleriyle](csharp-expressions.md#CodeWorkflows) yöntemi ile aynıdır.

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
