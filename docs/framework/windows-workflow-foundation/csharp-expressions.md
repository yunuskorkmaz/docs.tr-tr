---
title: C# İfadeleri
ms.date: 03/30/2017
ms.assetid: 29110be7-f4e3-407e-8dbe-78102eb21115
ms.openlocfilehash: c50f6a2a8dfb69b914fb4fa84c028f9d65c00cfa
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65882102"
---
# <a name="c-expressions"></a>C# İfadeleri
İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], C# ifadeleri, Windows Workflow Foundation (WF) desteklenir. Yeni C# iş akışı projeleri hedefleyen Visual Studio 2012'de oluşturulan [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] kullanmak C# ifadeleri ve Visual Basic iş akışı projeleri Visual Basic deyimleri kullanacak. Varolan [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] iş akışı projeleri, Visual Basic deyimleri kullanacak şekilde geçirilebilir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] dil ve bu projeyi bağımsız olarak desteklenir. Bu konu, C# ifadeleri genel bakış sağlar. [!INCLUDE[wf1](../../../includes/wf1-md.md)].

## <a name="using-c-expressions-in-workflows"></a>C# ifadeleri iş akışlarında kullanma

- [C# ifadeleri iş akışı Tasarımcısı'nda kullanma](csharp-expressions.md#WFDesigner)

    - [Geriye dönük uyumluluk](csharp-expressions.md#BackwardCompat)

- [Kod akışlarında C# ifadeleri kullanma](csharp-expressions.md#CodeWorkflows)

- [XAML iş akışlarında C# ifadeleri kullanma](csharp-expressions.md#XamlWorkflows)

    - [Derlenmiş Xaml](csharp-expressions.md#CompiledXaml)

    - [Bağımsız Xaml](csharp-expressions.md#LooseXaml)

- [C# ifadelerini kullanarak XAMLX iş akışı Hizmetleri](csharp-expressions.md#WFServices)

### <a name="WFDesigner"></a> C# ifadeleri iş akışı Tasarımcısı'nda kullanma
 İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], C# ifadeleri, Windows Workflow Foundation (WF) desteklenir. C# iş akışı projeleri hedefleyen Visual Studio 2012'de oluşturulan [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Visual Basic iş akışı projeleri Visual Basic deyimleri kullanırken, C# ifadeleri kullanın. İstenen C# ifadesini belirtmek için etiketli kutuya yazın **bir C# ifadesi girin**. Bu etiketi, etkinlik Tasarımcısı'nda veya iş akışı tasarımcısında etkinlik seçili olduğunda Özellikler penceresinde görüntülenir. Aşağıdaki örnekte, iki `WriteLine` etkinlikleri içinde yer alır bir `Sequence` içinde bir `NoPersistScope`.

 ![Otomatik olarak oluşturulan sıralı etkinlik gösteren ekran görüntüsü.](./media/csharp-expressions/auto-surround-sequence-activity.png)

> [!NOTE]
>  C# ifadeleri yalnızca Visual Studio'da desteklenir ve yeniden barındırılan iş akışı Tasarımcısı'nda desteklenmez. Yeniden barındırılan tasarımcıda desteklenen yeni WF45 özellikler hakkında daha fazla bilgi için bkz. [yeniden barındırılan iş akışı tasarımcısında yeni Workflow Foundation 4.5 özellikleri desteği](wf-features-in-the-rehosted-workflow-designer.md).

#### <a name="BackwardCompat"></a> Geriye dönük uyumluluk
 Varolan bir Visual Basic deyimleri [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] için geçirilen C# iş akışı projeleri [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] desteklenir. Visual Basic ifadeleri iş akışı Tasarımcısı'nda görüntülendiğinde, var olan Visual Basic ifadesinin metin ile değiştirilir **değer XAML ayarlandığı**, Visual Basic ifade geçerli C# sözdizimi olmadığı sürece. Visual Basic ifade geçerli C# sözdizimi, ardından ifadesi görüntülenir. Visual Basic deyimleri C# ' tan güncelleştirmek için iş akışı Tasarımcısı'nda düzenlemek ve eşdeğer C# ifadesi belirtin. Visual Basic deyimleri için C#, ancak ifadeler dönüştürülür C# ve Visual Basic geri değil iş akışı tasarımcısında güncelleştirildikten sonra güncelleştirmek için gerekli değildir.

### <a name="CodeWorkflows"></a> Kod akışlarında C# ifadeleri kullanma
 C# ifadelerini desteklenir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] kod tabanlı iş akışları, ancak iş akışı çağrılmadan önce C# ifadelerini kullanarak derlenmelidir <xref:System.Activities.XamlIntegration.TextExpressionCompiler.Compile%2A?displayProperty=nameWithType>. İş akışı yazarları kullanabileceğiniz `CSharpValue` gelerek bir ifadenin temsil etmek için ve `CSharpReference` bir ifadenin lvalue temsil etmek için. Aşağıdaki örnekte, bir iş akışı ile oluşturulan bir `Assign` etkinliği ve bir `WriteLine` etkinlik yer alan bir `Sequence` etkinlik. A `CSharpReference` için belirtilen `To` bağımsız değişkeni `Assign`, ifadenin lvalue temsil eder. A `CSharpValue` için belirtilen `Value` bağımsız değişkeni `Assign`ve `Text` bağımsız değişkeni `WriteLine`, bu iki ifade için r temsil eder.

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

 İş akışı oluşturulur, sonra C# ifadelerini çağırarak derlenir `CompileExpressions` yardımcı yöntem ve iş akışı çağrılır. Aşağıdaki örnek, `CompileExpressions` yöntemi.

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
>  Varsa C# ifadeleri derlenmemiş, bir <xref:System.NotSupportedException> aşağıdakine benzer bir ileti ile iş akışı çalıştırıldığında oluşturulur: `Expression Activity type 'CSharpValue`1' çalıştırmak için derleme gerektirir.  İş akışı derlendiğinden emin olun.'

 İş akışı kullanan özel kodunuz tabanlıysa `DynamicActivity`, bazı değişiklikler daha sonra `CompileExpressions` yöntemi gereklidir, aşağıdaki kod örneğinde gösterildiği gibi.

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

 Çeşitli farklılıklar vardır `CompileExpressions` C# ifadelerini dinamik etkinliğinde derler aşırı yükleme.

- Parametre `CompileExpressions` olduğu bir `DynamicActivity`.

- Ad alanı ve tür adı kullanılarak alınır `DynamicActivity.Name` özelliği.

- `TextExpressionCompilerSettings.ForImplementation` ayarlanır `true`.

- `CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation` yerine adlı `CompiledExpressionInvoker.SetCompiledExpressionRoot`.

 Kodda ifadeleri ile çalışma hakkında daha fazla bilgi için bkz. [yazma iş akışları, etkinlikler ve ifadeler kullanarak kesinliği kod](authoring-workflows-activities-and-expressions-using-imperative-code.md).

### <a name="XamlWorkflows"></a> XAML iş akışlarında C# ifadeleri kullanma
 C# ifadelerini XAML iş akışlarında desteklenir. Derlenmiş XAML iş akışı bir tür derlenir ve gevşek XAML iş akışı çalışma zamanı tarafından yüklenir ve iş akışı yürütüldüğünde bir etkinlik ağacına derlenir.

- [Derlenmiş Xaml](csharp-expressions.md#CompiledXaml)

- [Bağımsız Xaml](csharp-expressions.md#LooseXaml)

#### <a name="CompiledXaml"></a> Derlenmiş Xaml
 C# ifadeleri bir türe hedefleyen bir C# iş akışı projesi bir parçası olarak derlenen derlenmiş XAML iş akışlarında desteklenir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]. Derlenmiş XAML iş akışı yazma Visual Studio'da varsayılan türü olduğu ve oluşturulan C# iş akışı projeleri Visual Studio hedefleyen [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] C# ifadeleri kullanın.

#### <a name="LooseXaml"></a> Bağımsız Xaml
 C# ifadelerini gevşek XAML iş akışlarında desteklenir. İş akışı ana bilgisayar programı yükleyen ve gevşek XAML iş akışı çağırır hedeflemelidir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], ve <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> ayarlanmalıdır `true` (varsayılan değer `false`). Ayarlanacak <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> için `true`, oluşturun bir <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> ile örnek kendi <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> özelliğini `true`ve bunu bir parametre olarak geçiriyoruz <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>. Varsa `CompileExpressions` ayarlı değil `true`, <xref:System.NotSupportedException> aşağıdakine benzer bir ileti ile oluşturulur: `Expression Activity type 'CSharpValue`1' çalıştırmak için derleme gerektirir.  İş akışı derlendiğinden emin olun.'

```csharp
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings
{
    CompileExpressions = true
};

DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;
```

 XAML iş akışları ile çalışma hakkında daha fazla bilgi için bkz. [seri hale getirme iş akışları ve etkinlikler XAML gelen ve giden](serializing-workflows-and-activities-to-and-from-xaml.md).

### <a name="WFServices"></a> C# ifadelerini kullanarak XAMLX iş akışı Hizmetleri
 C# ifadelerini XAMLX iş akışı hizmetlerinde desteklenir. Ek bir adım gerekli değildir sonra bir iş akışı hizmeti IIS ya da WAS içinde barındırıldığında, ancak XAML iş akışı hizmeti, şirket içinde barındırılan, C# ifadelerini derlenmelidir. C# ifadelerini şirket içinde barındırılan XAMLX iş akışı hizmeti içinde derlemek için önce XAMLX dosyasına yüklemek bir `WorkflowService`ve ardından geçirmek `Body` , `WorkflowService` için `CompileExpressions` önceki açıklanan yöntemi [kullanarak C# ifadeleri iş akışlarında kod](csharp-expressions.md#CodeWorkflows) bölümü. Aşağıdaki örnekte, bir XAMLX iş akışı hizmeti yüklenir, C# ifadelerini derlenir ve sonra iş akışı hizmeti açılır ve istekleri için bekler.

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

 C# ifadelerini derlenmemiş, `Open` işlemi başarılı olur, ancak iş akışı, çağrıldığında başarısız olur. Aşağıdaki `CompileExpressions` yöntemi ile aynıdır önceki yöntem [kullanarak C# ifadeleri iş akışlarında kod](csharp-expressions.md#CodeWorkflows) bölümü.

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
