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
# <a name="c-expressions"></a>C# İfadeleri
.NET Framework 4,5 ' den başlayarak C# , WINDOWS Workflow FOUNDATION (WF) içinde ifadeler desteklenir. Visual C# Studio 2012 ' de oluşturulan yeni iş akışı projeleri .NET Framework 4,5 kullanın C# ve Visual Basic iş akışı projeleri Visual Basic ifadelerini kullanır. Visual Basic ifadelerini kullanan mevcut .NET Framework 4 iş akışı projeleri proje dilinden bağımsız olarak [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] geçirilebilir ve desteklenir. Bu konu, [!INCLUDE[wf1](../../../includes/wf1-md.md)]C# ifadelerde bir genel bakış sağlar.

## <a name="using-c-expressions-in-workflows"></a>İş C# akışlarında ifadeleri kullanma

- [İş Akışı Tasarımcısı C# ifadeleri kullanma](csharp-expressions.md#WFDesigner)

  - [Geriye dönük uyumluluk](csharp-expressions.md#BackwardCompat)

- [Kod C# iş akışlarında ifadeleri kullanma](csharp-expressions.md#CodeWorkflows)

- [XAML C# iş akışlarında ifadeleri kullanma](csharp-expressions.md#XamlWorkflows)

  - [Derlenen xaml](csharp-expressions.md#CompiledXaml)

  - [Gevşek XAML](csharp-expressions.md#LooseXaml)

- [XAMLX C# iş akışı hizmetlerinde ifadeleri kullanma](csharp-expressions.md#WFServices)

### <a name="WFDesigner"></a>İş Akışı Tasarımcısı C# ifadeleri kullanma

.NET Framework 4,5 ' den başlayarak C# , WINDOWS Workflow FOUNDATION (WF) içinde ifadeler desteklenir. C#Visual Studio 2012 ' de oluşturulan iş akışı projeleri .NET Framework 4,5 C# ' i hedef Visual Basic iş akışı projeleri Visual Basic ifadeler kullanır. İstenen C# ifadeyi belirtmek için,  **C# ifadeyi ifade girin**etiketli kutuya yazın. Bu etiket, tasarımcı içinde etkinlik seçildiğinde veya iş akışı tasarımcısında etkinlik olduğunda Özellikler penceresinde görüntülenir. Aşağıdaki örnekte, iki `WriteLine` etkinlik `NoPersistScope`içindeki bir `Sequence` içinde yer alır.

![Otomatik olarak oluşturulan bir sıra etkinliğini gösteren ekran görüntüsü.](./media/csharp-expressions/auto-surround-sequence-activity.png)

> [!NOTE]
> C#ifadeler yalnızca Visual Studio 'da desteklenir ve yeniden barındırılan iş akışı tasarımcısında desteklenmez. Yeniden barındırılan tasarımcıda desteklenen yeni WF45 özellikleri hakkında daha fazla bilgi için bkz. [yeniden barındırılan iş akışı Tasarımcısı yeni Workflow Foundation 4,5 özellikleri Için destek](wf-features-in-the-rehosted-workflow-designer.md).

#### <a name="BackwardCompat"></a>Geriye dönük uyumluluk

[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 'e geçirilmiş mevcut .NET Framework 4 C# iş akışı projelerindeki Visual Basic ifadeler desteklenir. Visual Basic ifadeleri iş akışı tasarımcısında görüntülendiğinde, Visual Basic ifadesi geçerli C# bir sözdizimi olmadığı takdirde, varolan Visual Basic IFADESININ metni **xaml 'de ayarlanmış**olarak değiştirilmiştir. Visual Basic ifadesi geçerli C# sözdizimidir, ifade görüntülenir. Visual Basic ifadelerini ' ye C#güncelleştirmek için, onları iş akışı tasarımcısında düzenleyebilir ve denk C# ifadeyi belirtebilirsiniz. Visual Basic ifadelerin C#' a güncelleştirilmesi gerekmez, ancak ifadeler ' e dönüştürüledikleri C# iş akışı tasarımcısında güncelleştirildikten sonra Visual Basic geri döndürülemez.

### <a name="CodeWorkflows"></a>Kod C# iş akışlarında ifadeleri kullanma

C#ifadeler [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] kod tabanlı iş akışlarında desteklenir, ancak iş akışı çağrmadan önce, C# ifadelerin <xref:System.Activities.XamlIntegration.TextExpressionCompiler.Compile%2A?displayProperty=nameWithType>kullanılarak derlenmesi gerekir. Workflow yazarları, bir ifadenin r-değerini temsil etmek için `CSharpValue` kullanabilir ve bir ifadenin l-değerini temsil `CSharpReference`. Aşağıdaki örnekte, bir `Assign` etkinliği ve bir `Sequence` etkinliğinde bulunan `WriteLine` etkinliği ile bir iş akışı oluşturulur. `Assign``To` bağımsız değişkeni için `CSharpReference` belirtilir ve ifadenin l-değerini temsil eder. `Assign``Value` bağımsız değişkeni ve `WriteLine``Text` bağımsız değişkeni için `CSharpValue` belirtilir ve bu iki ifade için r-değeri temsil eder.

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

İş akışı oluşturulduktan sonra, C# ifadeler `CompileExpressions` yardımcı yöntemi çağırarak ve sonra iş akışı çağrıldığında derlenir. Aşağıdaki örnek `CompileExpressions` yöntemidir.

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
> C# İfadeler derlenmeyecekse, iş akışı aşağıdakine benzer bir iletiyle çağrıldığında bir <xref:System.NotSupportedException> oluşturulur: `Expression Activity type 'CSharpValue`1 ' çalıştırmak için derleme gerektirir.  Lütfen iş akışının derlendiğinden emin olun. '

Özel kod tabanlı iş akışınız `DynamicActivity`kullanıyorsa, aşağıdaki kod örneğinde gösterildiği gibi, `CompileExpressions` yönteminde bazı değişiklikler yapmanız gerekir.

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

Dinamik bir etkinlikte C# ifadeleri derleyen `CompileExpressions` aşırı yüklemede çeşitli farklılıklar vardır.

- `CompileExpressions` parametresi bir `DynamicActivity`.

- Tür adı ve ad alanı `DynamicActivity.Name` özelliği kullanılarak alınır.

- `TextExpressionCompilerSettings.ForImplementation` `true`olarak ayarlanır.

- `CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation` `CompiledExpressionInvoker.SetCompiledExpressionRoot`yerine çağrılır.

Koddaki ifadelerle çalışma hakkında daha fazla bilgi için, bkz. [using Iş akışları, etkinlikler ve ifadeleri, zorunlu kod kullanarak yazma](authoring-workflows-activities-and-expressions-using-imperative-code.md).

### <a name="XamlWorkflows"></a>XAML C# iş akışlarında ifadeleri kullanma

C#ifadeler XAML iş akışlarında desteklenir. Derlenmiş XAML iş akışları bir türe derlenir ve gevşek XAML iş akışları çalışma zamanı tarafından yüklenir ve iş akışı yürütüldüğünde bir etkinlik ağacına derlenir.

- [Derlenen xaml](csharp-expressions.md#CompiledXaml)

- [Gevşek XAML](csharp-expressions.md#LooseXaml)

#### <a name="CompiledXaml"></a>Derlenen xaml

C#ifadeler, [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]hedefleyen bir C# iş akışı projesinin parçası olarak bir türe derlenen derlenmiş xaml iş akışlarında desteklenir. Derlenmiş XAML, Visual Studio 'da varsayılan iş akışı yazma türüdür ve C# Visual Studio 'da oluşturulan iş akışı projeleri [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] kullanın. C#

#### <a name="LooseXaml"></a>Gevşek XAML

C#ifadeler gevşek XAML iş akışlarında desteklenir. Gevşek XAML iş akışını yükleyen ve çağıran iş akışı konak programı [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]hedeflemelidir ve <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> `true` olarak ayarlanması gerekir (varsayılan değer `false`). <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> `true`olarak ayarlamak için <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> özelliği `true`olarak ayarlanmış bir <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> örneği oluşturun ve <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>bir parametre olarak geçirin. `CompileExpressions` `true`olarak ayarlanmamışsa aşağıdakine benzer bir ileti içeren bir <xref:System.NotSupportedException> oluşturulur: `Expression Activity type 'CSharpValue`1 ' çalıştırmak için derleme gerektirir.  Lütfen iş akışının derlendiğinden emin olun. '

```csharp
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings
{
    CompileExpressions = true
};

DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;
```

XAML iş akışlarıyla çalışma hakkında daha fazla bilgi için bkz. [xaml 'de ve xaml 'de Iş akışlarını ve etkinlikleri serileştirme](serializing-workflows-and-activities-to-and-from-xaml.md).

### <a name="WFServices"></a>XAMLX C# iş akışı hizmetlerinde ifadeleri kullanma

C#ifadeler XAMLX iş akışı hizmetlerinde desteklenir. Bir iş akışı hizmeti IIS 'de barındırıldığında veya ek adımlar gerekli olmadığında, ancak XAML iş akışı hizmeti kendiliğinden barındırılıyorsa, C# ifadelerin derlenmesi gerekir. Kendi kendine barındırılan C# bir xamlx iş akışı hizmetindeki ifadeleri derlemek için, önce xamlx dosyasını bir `WorkflowService`yükleyin ve ardından `WorkflowService` `Body`, [kod iş akışlarında önceki C# ifadeleri kullanma](csharp-expressions.md#CodeWorkflows) bölümünde açıklanan `CompileExpressions` yöntemine geçirin. Aşağıdaki örnekte, bir XAMLX iş akışı hizmeti yüklenir, C# ifadeler derlenir ve sonra iş akışı hizmeti açılır ve istekler için bekler.

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

C# İfadeler derlenmediği zaman, `Open` işlemi başarılı olur ancak iş akışı çağrıldığında başarısız olur. Aşağıdaki `CompileExpressions` yöntemi, [kod iş akışlarında önceki C# using deyimleriyle](csharp-expressions.md#CodeWorkflows) aynı yöntemle aynıdır.

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
