---
title: C# ifadeleri
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 29110be7-f4e3-407e-8dbe-78102eb21115
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 32fb7be6f8c465994b40814a94efd95d42a481da
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="c-expressions"></a>C# ifadeleri
İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], C# ifadeleri, Windows Workflow Foundation (WF) desteklenir. Yeni C# iş akışı projeleri oluşturulan [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] hedefleyen [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] kullanım C# ifadeleri ve Visual Basic iş akışı projeleri Visual Basic ifadeler kullanın. Varolan [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] Visual Basic ifadeleri kullanma iş akışı projeleri geçiş yapabilir için [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] dil ve bu projenin bağımsız olarak desteklenir. Bu konu, C# ifadelerinde genel bir bakış sağlar. [!INCLUDE[wf1](../../../includes/wf1-md.md)].  
  
## <a name="using-c-expressions-in-workflows"></a>C# ifadeleri iş akışlarında kullanma  
  
-   [İş Akışı Tasarımcısı'nda C# ifadeler kullanma](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#WFDesigner)  
  
    -   [Geriye dönük uyumluluk](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#BackwardCompat)  
  
-   [Kod iş akışlarında C# ifadeler kullanma](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows)  
  
-   [XAML iş akışlarında C# ifadeler kullanma](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#XamlWorkflows)  
  
    -   [Derlenmiş Xaml](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CompiledXaml)  
  
    -   [Gevşek Xaml](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#LooseXaml)  
  
-   [C# ifadeler XAMLX iş akışı hizmetleri kullanma](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#WFServices)  
  
###  <a name="WFDesigner"></a> İş Akışı Tasarımcısı'nda C# ifadeler kullanma  
 İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], C# ifadeleri, Windows Workflow Foundation (WF) desteklenir. C# iş akışı projeleri oluşturulan [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] hedefleyen [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] C# ifadeler, Visual Basic iş akışı projeleri Visual Basic ifadeleri kullanırken kullanın. İstenen C# ifade belirtmek için bunu etiketli kutusuna **bir C# ifadesi girin**. Etkinlik Tasarımcısı'nda veya iş akışı Tasarımcısı'nda faaliyete seçildiğinde bu etiket Özellikler penceresinde görüntülenir. Aşağıdaki örnekte, iki `WriteLine` etkinlikleri içinde bulunan bir `Sequence` içinde bir `NoPersistScope`.  
  
 ![Sıralı etkinlik otomatik olarak oluşturulan](../../../docs/framework/windows-workflow-foundation/media/autosurround2.png "AutoSurround2")  
  
> [!NOTE]
>  C# ifadeleri yalnızca Visual Studio'da desteklenir ve yeniden barındırılan iş akışı Tasarımcısı'nda desteklenmez. Yeniden barındırılan Tasarımcısı'nda desteklenen yeni WF45 özellikler hakkında daha fazla bilgi için bkz: [Rehosted iş akışı Tasarımcısı'nda yeni iş akışı Foundation 4.5 özellikleri için destek](../../../docs/framework/windows-workflow-foundation/wf-features-in-the-rehosted-workflow-designer.md).  
  
####  <a name="BackwardCompat"></a> Geriye dönük uyumluluk  
 Visual Basic ifadeleri varolan [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] için geçirilen C# iş akışı projeleri [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] desteklenir. Visual Basic ifadeleri iş akışı Tasarımcısı'nda görüntülendiğinde mevcut Visual Basic ifade metin ile değiştirilir **değeri XAML'de ayarlandığı**, Visual Basic ifade geçerli C# sözdizimi değilse. Visual Basic ifade geçerli C# sözdizimi ise, ifadesi görüntülenir. Visual Basic ifadeleri C# güncelleştirmek için iş akışı Tasarımcısı'nda düzenleyebilir ve eşdeğer C# ifadeyi belirtin. Visual Basic ifadeler için C#, ancak ifadeleri dönüştürülür C# ve Visual Basic geri olmayan iş akışı Tasarımcısı'nda güncelleştirilmiş bir kez güncelleştirmek için gerekli değildir.  
  
###  <a name="CodeWorkflows"></a> Kod iş akışlarında C# ifadeler kullanma  
 C# ifadeler de desteklenmektedir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] kod tabanlı iş akışları, ancak iş akışı çağrılabilir önce C# ifadeler kullanarak derlenmelidir <xref:System.Activities.XamlIntegration.TextExpressionCompiler.Compile%2A?displayProperty=nameWithType>. İş akışı yazarları kullanabileceğiniz `CSharpValue` bir ifade r temsil etmek için ve `CSharpReference` l-değeri ifade temsil etmek için. Aşağıdaki örnekte, bir iş akışı ile oluşturulan bir `Assign` etkinliği ve bir `WriteLine` etkinlik içinde yer alan bir `Sequence` etkinlik. A `CSharpReference` için belirtilen `To` bağımsız değişkeni `Assign`ve ifade l-değeri temsil eder. A `CSharpValue` için belirtilen `Value` bağımsız değişkeni `Assign`ve `Text` bağımsız değişkeni `WriteLine`, bu iki ifadeye r temsil eder.  
  
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
  
 İş akışı oluşturulan sonra C# ifadeleri çağırarak derlenen `CompileExpressions` yardımcı yöntem ve iş akışı çağrılır. Aşağıdaki örnek `CompileExpressions` yöntemi.  
  
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
>  C# ifadeleri derlenmemiş, bir <xref:System.NotSupportedException> aşağıdakine benzer bir ileti ile iş akışı çağrıldığında oluşturulur: `Expression Activity type 'CSharpValue`1' derleme çalıştırmak için gereklidir.  Lütfen iş akışının derlendikten olduğundan emin olun.'  
  
 İş akışı kullanan özel kodunuzu dayalı olarak, `DynamicActivity`, bazı değişiklikler sonra `CompileExpressions` yöntemi gereklidir, aşağıdaki kod örneğinde gösterildiği gibi.  
  
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
  
 Bazı farklılıklar vardır `CompileExpressions` C# ifadeleri dinamik bir aktivite içinde derler aşırı.  
  
-   Parametre `CompileExpressions` olan bir `DynamicActivity`.  
  
-   Ad alanı ve türü adını kullanarak alınır `DynamicActivity.Name` özelliği.  
  
-   `TextExpressionCompilerSettings.ForImplementation` ayarlanmış `true`.  
  
-   `CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation` yerine adlı `CompiledExpressionInvoker.SetCompiledExpressionRoot`.  
  
 Kodda ifadeleri ile çalışma hakkında daha fazla bilgi için bkz: [geliştirme iş akışları, etkinlikler ve ifadeler kullanarak kesinliği kod](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).  
  
###  <a name="XamlWorkflows"></a> XAML iş akışlarında C# ifadeler kullanma  
 C# ifadeleri XAML iş akışlarında desteklenir. Derlenmiş XAML iş akışı bir türe derlenir ve gevşek XAML iş akışı çalışma zamanı tarafından yüklenen ve iş akışı çalıştırıldığında bir etkinlik ağacına derlenir.  
  
-   [Derlenmiş Xaml](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CompiledXaml)  
  
-   [Gevşek Xaml](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#LooseXaml)  
  
####  <a name="CompiledXaml"></a> Derlenmiş Xaml  
 C# ifadeleri türüne hedefleyen bir C# iş akışı projesinde bir parçası olarak derlenmiş derlenmiş XAML iş akışlarında desteklenir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]. Derlenmiş XAML Visual Studio iş akışı yazma varsayılan tür ve C# iş akışı projeleri oluşturulan Visual Studio hedefleyen [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] C# ifadeler kullanın.  
  
####  <a name="LooseXaml"></a> Gevşek Xaml  
 C# ifadeleri gevşek XAML iş akışlarında desteklenir. Yükleyen ve gevşek XAML iş akışı çağıran iş akışı ana bilgisayar programı hedeflemelidir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], ve <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> ayarlanmalıdır `true` (varsayılan `false`). Ayarlamak için <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> için `true`, oluşturma bir <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> örneği kendi <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> özelliğini `true`ve bir parametre olarak geçirmek <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>. Varsa `CompileExpressions` ayarlanmazsa `true`, <xref:System.NotSupportedException> aşağıdakine benzer bir ileti ile oluşturulur: `Expression Activity type 'CSharpValue`1' derleme çalıştırmak için gereklidir.  Lütfen iş akışının derlendikten olduğundan emin olun.'  
  
```csharp  
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings  
{  
    CompileExpressions = true  
};  
  
DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;  
```  
  
 XAML iş akışları ile çalışma hakkında daha fazla bilgi için bkz: [seri hale getirme iş akışları ve etkinlikler XAML gelen ve giden](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md).  
  
###  <a name="WFServices"></a> C# ifadeler XAMLX iş akışı hizmetleri kullanma  
 C# ifadeleri XAMLX iş akışı hizmetleri desteklenir. Başka adım gerekli değildir sonra bir iş akışı hizmeti IIS ya da WAS içinde barındırıldığında, ancak XAML iş akışı hizmeti Self barındırılıyorsa, C# ifadeleri derlenmiş gerekir. C# ifadelerinde kendini barındıran XAMLX iş akışı hizmeti derlemek için önce XAMLX dosyasına yüklemek bir `WorkflowService`ve ardından geçirmek `Body` , `WorkflowService` için `CompileExpressions` önceki açıklanan yöntemi [kullanarak C# kod iş akışları ifadelerinde](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) bölümü. Aşağıdaki örnekte, XAMLX iş akışı hizmeti yüklenmiş, C# ifadeleri derlenir ve iş akışı hizmeti açıldıktan sonra istekleri için bekler.  
  
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
  
 C# ifadeleri derlenmemiş, `Open` işlemi başarılı olur, ancak çalıştırıldığında iş akışının başarısız olur. Aşağıdaki `CompileExpressions` yöntemi aynıdır önceki yöntemi [kullanarak C# kod iş akışları ifadelerinde](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) bölümü.  
  
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
