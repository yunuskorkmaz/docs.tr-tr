---
title: "İş akışları ve etkinlikler XAML seri hale getirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37685b32-24e3-4d72-88d8-45d5fcc49ec2
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3be1c85a87896c176d5e81d2938418194d28b93b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="serializing-workflows-and-activities-to-and-from-xaml"></a><span data-ttu-id="20a1c-102">İş akışları ve etkinlikler XAML seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="20a1c-102">Serializing Workflows and Activities to and from XAML</span></span>
<span data-ttu-id="20a1c-103">Derlemelerde bulunan türlerine derlenmiş ek olarak, iş akışı tanımları da XAML için seri hale getirilebilir.</span><span class="sxs-lookup"><span data-stu-id="20a1c-103">In addition to being compiled into types that are contained in assemblies, workflow definitions can also be serialized to XAML.</span></span> <span data-ttu-id="20a1c-104">Bu seri hale getirilmiş tanımları düzenleme için yeniden yüklenmesi veya denetleme, derleme için bir yapı sistemi geçirilen veya yüklenen ve çağrılır.</span><span class="sxs-lookup"><span data-stu-id="20a1c-104">These serialized definitions can be reloaded for editing or inspection, passed to a build system for compilation, or loaded and invoked.</span></span> <span data-ttu-id="20a1c-105">Bu konu, iş akışı tanımları seri hale getirme ve XAML iş akışı tanımları ile çalışmaya genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="20a1c-105">This topic provides an overview of serializing workflow definitions and working with XAML workflow definitions.</span></span>  
  
## <a name="working-with-xaml-workflow-definitions"></a><span data-ttu-id="20a1c-106">XAML iş akışı tanımları ile çalışma</span><span class="sxs-lookup"><span data-stu-id="20a1c-106">Working with XAML Workflow Definitions</span></span>  
 <span data-ttu-id="20a1c-107">Seri hale getirme, bir iş akışı tanımı oluşturmak için <xref:System.Activities.ActivityBuilder> sınıfı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="20a1c-107">To create a workflow definition for serialization, the <xref:System.Activities.ActivityBuilder> class is used.</span></span> <span data-ttu-id="20a1c-108">Oluşturma bir <xref:System.Activities.ActivityBuilder> oluşturmaya çok benzer bir <xref:System.Activities.DynamicActivity>.</span><span class="sxs-lookup"><span data-stu-id="20a1c-108">Creating an <xref:System.Activities.ActivityBuilder> is very similar to creating a <xref:System.Activities.DynamicActivity>.</span></span> <span data-ttu-id="20a1c-109">İstenen herhangi bir bağımsız değişken belirtilir ve davranışı oluşturan etkinlikler yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="20a1c-109">Any desired arguments are specified, and the activities that constitute the behavior are configured.</span></span> <span data-ttu-id="20a1c-110">Aşağıdaki örnekte, bir `Add` etkinlik oluşturulan iki giriş bağımsız değişkeni alır, bunları bir araya getirir ve sonucunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="20a1c-110">In the following example, an `Add` activity is created that takes two input arguments, adds them together, and returns the result.</span></span> <span data-ttu-id="20a1c-111">Bu etkinlik bir sonuç genel döndürdüğünden <xref:System.Activities.ActivityBuilder%601> sınıfı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="20a1c-111">Because this activity returns a result, the generic <xref:System.Activities.ActivityBuilder%601> class is used.</span></span>  
  
 [!code-csharp[CFX_WorkflowApplicationExample#41](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#41)]  
  
 <span data-ttu-id="20a1c-112">Her biri <xref:System.Activities.DynamicActivityProperty> örnekleri temsil eden iş akışına giriş bağımsız değişkenlerinde birini ve <xref:System.Activities.ActivityBuilder.Implementation%2A> iş akışı mantığı oluşturan etkinlikler içerir.</span><span class="sxs-lookup"><span data-stu-id="20a1c-112">Each of the <xref:System.Activities.DynamicActivityProperty> instances represents one of the input arguments to the workflow, and the <xref:System.Activities.ActivityBuilder.Implementation%2A> contains the activities that make up the logic of the workflow.</span></span> <span data-ttu-id="20a1c-113">Bu örnekte r değeri ifadeleri Visual Basic ifadeleri olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="20a1c-113">Note that the r-value expressions in this example are Visual Basic expressions.</span></span> <span data-ttu-id="20a1c-114">Lambda ifadeleri için XAML serileştirilebilir olmayan sürece <xref:System.Activities.Expressions.ExpressionServices.Convert%2A> kullanılır.</span><span class="sxs-lookup"><span data-stu-id="20a1c-114">Lambda expressions are not serializable to XAML unless <xref:System.Activities.Expressions.ExpressionServices.Convert%2A> is used.</span></span> <span data-ttu-id="20a1c-115">Serileştirilmiş iş akışları açılacak veya iş akışı Tasarımcısı'nda düzenlenebilir yönelikse Visual Basic ifadeleri kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="20a1c-115">If the serialized workflows are intended to be opened or edited in the workflow designer then Visual Basic expressions should be used.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="20a1c-116">[İş akışları, etkinlikler ve ifadeler kesinlik temelli kod kullanarak geliştirme](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).</span><span class="sxs-lookup"><span data-stu-id="20a1c-116"> [Authoring Workflows, Activities, and Expressions Using Imperative Code](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>  
  
 <span data-ttu-id="20a1c-117">Tarafından temsil edilen iş akışı tanımı serileştirmek için <xref:System.Activities.ActivityBuilder> XAML, kullanım örneğine <xref:System.Activities.XamlIntegration.ActivityXamlServices> oluşturmak için bir <xref:System.Xaml.XamlWriter>ve ardından <xref:System.Xaml.XamlServices> kullanarak iş akışı tanımı serileştirmek için <xref:System.Xaml.XamlWriter>.</span><span class="sxs-lookup"><span data-stu-id="20a1c-117">To serialize the workflow definition represented by the <xref:System.Activities.ActivityBuilder> instance to XAML, use <xref:System.Activities.XamlIntegration.ActivityXamlServices> to create a <xref:System.Xaml.XamlWriter>, and then use <xref:System.Xaml.XamlServices> to serialize the workflow definition by using the <xref:System.Xaml.XamlWriter>.</span></span> <span data-ttu-id="20a1c-118"><xref:System.Activities.XamlIntegration.ActivityXamlServices>eşleme için yöntemleri vardır <xref:System.Activities.ActivityBuilder> örnekleri ve XAML ve XAML iş akışları yükleme ve döndürmek için bir <xref:System.Activities.DynamicActivity> , çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="20a1c-118"><xref:System.Activities.XamlIntegration.ActivityXamlServices> has methods to map <xref:System.Activities.ActivityBuilder> instances to and from XAML, and to load XAML workflows and return a <xref:System.Activities.DynamicActivity> that can be invoked.</span></span> <span data-ttu-id="20a1c-119">Aşağıdaki örnekte, <xref:System.Activities.ActivityBuilder> örneğinin önceki örnekten bir dizeye sıralanabilir ve ayrıca bir dosyaya kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="20a1c-119">In the following example, the <xref:System.Activities.ActivityBuilder> instance from the previous example is serialized to a string, and also saved to a file.</span></span>  
  
```csharp  
// Serialize the workflow to XAML and store it in a string.  
StringBuilder sb = new StringBuilder();  
StringWriter tw = new StringWriter(sb);  
XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(tw, new XamlSchemaContext()));  
XamlServices.Save(xw , ab);  
string serializedAB = sb.ToString();  
  
// Display the XAML to the console.  
Console.WriteLine(serializedAB);  
  
// Serialize the workflow to XAML and save it to a file.  
StreamWriter sw = File.CreateText(@"C:\Workflows\add.xaml");  
XamlWriter xw2 = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(sw, new XamlSchemaContext()));  
XamlServices.Save(xw2, ab);  
sw.Close();  
```  
  
 <span data-ttu-id="20a1c-120">Aşağıdaki örnek serileştirilmiş iş akışı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="20a1c-120">The following example represents the serialized workflow.</span></span>  
  
```xaml  
<Activity   
  x:TypeArguments="x:Int32"   
  x:Class="Add"   
  xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"   
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <x:Members>  
    <x:Property Name="Operand1" Type="InArgument(x:Int32)" />  
    <x:Property Name="Operand2" Type="InArgument(x:Int32)" />  
  </x:Members>  
  <Sequence>  
    <WriteLine Text="[Operand1.ToString() + " + " + Operand2.ToString()]" />  
    <Assign x:TypeArguments="x:Int32" Value="[Operand1 + Operand2]">  
      <Assign.To>  
        <OutArgument x:TypeArguments="x:Int32">  
          <ArgumentReference x:TypeArguments="x:Int32" ArgumentName="Result" />  
          </OutArgument>  
      </Assign.To>  
    </Assign>  
  </Sequence>  
</Activity>  
```  
  
 <span data-ttu-id="20a1c-121">Seri hale getirilmiş bir iş akışını yüklemek için <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> yöntemi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="20a1c-121">To load a serialized workflow, the <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> method is used.</span></span> <span data-ttu-id="20a1c-122">Bu seri hale getirilmiş iş akışı tanımı alıp döndüren bir <xref:System.Activities.DynamicActivity> , iş akışı tanımını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="20a1c-122">This takes the serialized workflow definition and returns a <xref:System.Activities.DynamicActivity> that represents the workflow definition.</span></span> <span data-ttu-id="20a1c-123">XAML kadar serisi yok Not <xref:System.Activities.Activity.CacheMetadata%2A> gövdesi adlı <xref:System.Activities.DynamicActivity> doğrulama işlemi sırasında.</span><span class="sxs-lookup"><span data-stu-id="20a1c-123">Note that the XAML is not deserialized until <xref:System.Activities.Activity.CacheMetadata%2A> is called on the body of the <xref:System.Activities.DynamicActivity> during the validation process.</span></span> <span data-ttu-id="20a1c-124">Doğrulama açıkça çağrılmazsa iş akışı çağrıldığında sonra onu gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="20a1c-124">If validation is not explicitly called then it is performed when the workflow is invoked.</span></span> <span data-ttu-id="20a1c-125">XAML iş akışı tanımı geçersizse, sonra bir <xref:System.Argument> özel durumu oluşur.</span><span class="sxs-lookup"><span data-stu-id="20a1c-125">If the XAML workflow definition is invalid, then an <xref:System.Argument> exception is thrown.</span></span> <span data-ttu-id="20a1c-126">Gelen karşılaşılan özel durumlar <xref:System.Activities.Activity.CacheMetadata%2A> çağrıya kaçış <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> ve çağıran tarafından yapılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="20a1c-126">Any exceptions thrown from <xref:System.Activities.Activity.CacheMetadata%2A> escape from the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> and must be handled by the caller.</span></span> <span data-ttu-id="20a1c-127">Aşağıdaki örnekte, önceki örnekte serileştirilmiş iş akışını yüklendiğinde ve kullanılarak <xref:System.Activities.WorkflowInvoker>.</span><span class="sxs-lookup"><span data-stu-id="20a1c-127">In the following example, the serialized workflow from the previous example is loaded and invoked by using <xref:System.Activities.WorkflowInvoker>.</span></span>  
  
 [!code-csharp[CFX_WorkflowApplicationExample#43](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#43)]  
  
 <span data-ttu-id="20a1c-128">Bu iş akışı çağrıldığında, aşağıdaki çıktıyı konsola görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="20a1c-128">When this workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="20a1c-129">**25 + 15**</span><span class="sxs-lookup"><span data-stu-id="20a1c-129">**25 + 15**</span></span>  
<span data-ttu-id="20a1c-130">**40**</span><span class="sxs-lookup"><span data-stu-id="20a1c-130">**40**</span></span>    
> [!NOTE]
>  [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="20a1c-131">Giriş ve çıkış bağımsız değişkenleri iş akışlarıyla çağrılırken, bkz: [kullanarak WorkflowInvoker ve WorkflowApplication](../../../docs/framework/windows-workflow-foundation/using-workflowinvoker-and-workflowapplication.md) ve <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span><span class="sxs-lookup"><span data-stu-id="20a1c-131"> invoking workflows with input and output arguments, see [Using WorkflowInvoker and WorkflowApplication](../../../docs/framework/windows-workflow-foundation/using-workflowinvoker-and-workflowapplication.md) and <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span></span>  
  
 <span data-ttu-id="20a1c-132">C# ifadeler, sıralı iş akışı içeriyorsa, sonra bir <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> örneği kendi <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> özelliğini `true` bir parametre olarak geçirilmelidir <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>, aksi takdirde bir <xref:System.NotSupportedException> benzer bir ileti ile oluşturulur Aşağıdaki: `Expression Activity type 'CSharpValue`1' derleme çalıştırmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="20a1c-132">If the serialized workflow contains C# expressions, then an <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> instance with its <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> property set to `true` must be passed as a parameter to <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>, otherwise a <xref:System.NotSupportedException> will be thrown with a message similar to the following: `Expression Activity type 'CSharpValue`1' requires compilation in order to run.</span></span>  <span data-ttu-id="20a1c-133">Lütfen iş akışının derlendikten olduğundan emin olun.'</span><span class="sxs-lookup"><span data-stu-id="20a1c-133">Please ensure that the workflow has been compiled.\`</span></span>  
  
```csharp  
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings  
{  
    CompileExpressions = true  
};  
  
DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;  
```  
  
 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="20a1c-134">[C# ifadeleri](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="20a1c-134"> [C# Expressions](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md).</span></span>  
  
 <span data-ttu-id="20a1c-135">Serileştirilmiş iş akışı tanımı ayrıca içine yüklenebilir bir <xref:System.Activities.ActivityBuilder> kullanarak örnek <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.CreateBuilderReader%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="20a1c-135">A serialized workflow definition can also be loaded into an <xref:System.Activities.ActivityBuilder> instance by using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.CreateBuilderReader%2A> method.</span></span> <span data-ttu-id="20a1c-136">Serileştirilmiş bir iş akışı içine yüklendikten sonra bir <xref:System.Activities.ActivityBuilder> Denetlenmekte ve değiştiren örneği.</span><span class="sxs-lookup"><span data-stu-id="20a1c-136">After a serialized workflow is loaded into an <xref:System.Activities.ActivityBuilder> instance it can be inspected and modified.</span></span> <span data-ttu-id="20a1c-137">Bu, özel iş akışı Tasarımcısı yazarlar için yararlıdır ve kaydetme ve iş akışı tanımları tasarım işlemi sırasında yeniden yükleme için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="20a1c-137">This is useful for custom workflow designer authors and provides a mechanism for saving and reloading workflow definitions during the design process.</span></span> <span data-ttu-id="20a1c-138">Aşağıdaki örnekte, önceki örnekten serileştirilmiş iş akışı tanımı yüklendi ve özelliklerini denetlenir.</span><span class="sxs-lookup"><span data-stu-id="20a1c-138">In the following example, the serialized workflow definition from the previous example is loaded and its properties are inspected.</span></span>  
  
 [!code-csharp[CFX_WorkflowApplicationExample#44](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#44)]
