---
title: XAML’de İş Akışı ve Etkinlikleri Serileştirme
description: Bu makale, iş akışı tanımlarının serileştirilmesi ve Workflow Foundation 'da XAML iş akışı tanımlarıyla çalışma hakkında genel bakıştır.
ms.date: 03/30/2017
ms.assetid: 37685b32-24e3-4d72-88d8-45d5fcc49ec2
ms.openlocfilehash: 168dbc9a36cfa80c15fddc7481e986d1ce383adb
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421351"
---
# <a name="serialize-workflows-and-activities-to-and-from-xaml"></a><span data-ttu-id="3a745-103">XAML 'ye ve XAML 'ye Iş akışlarını ve etkinlikleri seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="3a745-103">Serialize Workflows and Activities to and from XAML</span></span>

<span data-ttu-id="3a745-104">Derlemeler içinde yer alan türlere derlenmenin yanı sıra, iş akışı tanımları da XAML 'ye seri hale getirilebilir.</span><span class="sxs-lookup"><span data-stu-id="3a745-104">In addition to being compiled into types that are contained in assemblies, workflow definitions can also be serialized to XAML.</span></span> <span data-ttu-id="3a745-105">Bu serileştirilmiş tanımlar, derleme veya inceleme için yeniden yüklenebilir, derleme için bir derleme sistemine geçirilebilir veya yüklenip çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="3a745-105">These serialized definitions can be reloaded for editing or inspection, passed to a build system for compilation, or loaded and invoked.</span></span> <span data-ttu-id="3a745-106">Bu konu, iş akışı tanımlarının serileştirilmesi ve XAML iş akışı tanımlarıyla çalışma hakkında genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a745-106">This topic provides an overview of serializing workflow definitions and working with XAML workflow definitions.</span></span>

## <a name="work-with-xaml-workflow-definitions"></a><span data-ttu-id="3a745-107">XAML Iş akışı tanımlarıyla çalışma</span><span class="sxs-lookup"><span data-stu-id="3a745-107">Work with XAML Workflow definitions</span></span>

<span data-ttu-id="3a745-108">Serileştirme için bir iş akışı tanımı oluşturmak üzere <xref:System.Activities.ActivityBuilder> sınıfı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3a745-108">To create a workflow definition for serialization, the <xref:System.Activities.ActivityBuilder> class is used.</span></span> <span data-ttu-id="3a745-109">Oluşturma <xref:System.Activities.ActivityBuilder> , oluşturmak için çok benzerdir <xref:System.Activities.DynamicActivity> .</span><span class="sxs-lookup"><span data-stu-id="3a745-109">Creating an <xref:System.Activities.ActivityBuilder> is very similar to creating a <xref:System.Activities.DynamicActivity>.</span></span> <span data-ttu-id="3a745-110">İstenen bağımsız değişkenler belirtilir ve davranışı oluşturan etkinlikler yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="3a745-110">Any desired arguments are specified, and the activities that constitute the behavior are configured.</span></span> <span data-ttu-id="3a745-111">Aşağıdaki örnekte, `Add` iki giriş bağımsız değişkeni alan bir etkinlik oluşturulur, bunları bir araya ekler ve sonucu döndürür.</span><span class="sxs-lookup"><span data-stu-id="3a745-111">In the following example, an `Add` activity is created that takes two input arguments, adds them together, and returns the result.</span></span> <span data-ttu-id="3a745-112">Bu etkinlik bir sonuç döndürdüğünden, genel <xref:System.Activities.ActivityBuilder%601> sınıf kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3a745-112">Because this activity returns a result, the generic <xref:System.Activities.ActivityBuilder%601> class is used.</span></span>

[!code-csharp[CFX_WorkflowApplicationExample#41](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#41)]

<span data-ttu-id="3a745-113">Örneklerin her biri, <xref:System.Activities.DynamicActivityProperty> iş akışına ait giriş bağımsız değişkenlerinden birini temsil eder ve <xref:System.Activities.ActivityBuilder.Implementation%2A> iş akışının mantığını oluşturan etkinlikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="3a745-113">Each of the <xref:System.Activities.DynamicActivityProperty> instances represents one of the input arguments to the workflow, and the <xref:System.Activities.ActivityBuilder.Implementation%2A> contains the activities that make up the logic of the workflow.</span></span> <span data-ttu-id="3a745-114">Bu örnekteki r-value ifadelerinin Visual Basic ifadeler olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3a745-114">Note that the r-value expressions in this example are Visual Basic expressions.</span></span> <span data-ttu-id="3a745-115">Lambda ifadeleri, kullanılmamışsa XAML 'ye serileştirilebilir değildir <xref:System.Activities.Expressions.ExpressionServices.Convert%2A> .</span><span class="sxs-lookup"><span data-stu-id="3a745-115">Lambda expressions are not serializable to XAML unless <xref:System.Activities.Expressions.ExpressionServices.Convert%2A> is used.</span></span> <span data-ttu-id="3a745-116">Seri hale getirilmiş iş akışlarının iş akışı tasarımcısında açılması veya düzenlenmesi amaçlanıyorsa, Visual Basic ifadelerin kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3a745-116">If the serialized workflows are intended to be opened or edited in the workflow designer, then Visual Basic expressions should be used.</span></span> <span data-ttu-id="3a745-117">Daha fazla bilgi için bkz. zorunlu [kod kullanarak Iş akışları, etkinlikler ve Ifadeler yazma](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span><span class="sxs-lookup"><span data-stu-id="3a745-117">For more information, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>

<span data-ttu-id="3a745-118">Örnek tarafından temsil edilen iş akışı tanımını XAML 'e seri hale getirmek için, <xref:System.Activities.ActivityBuilder> <xref:System.Activities.XamlIntegration.ActivityXamlServices> bir oluşturmak için <xref:System.Xaml.XamlWriter> öğesini kullanın ve <xref:System.Xaml.XamlServices> kullanarak iş akışı tanımını seri hale getirmek için kullanın <xref:System.Xaml.XamlWriter> .</span><span class="sxs-lookup"><span data-stu-id="3a745-118">To serialize the workflow definition represented by the <xref:System.Activities.ActivityBuilder> instance to XAML, use <xref:System.Activities.XamlIntegration.ActivityXamlServices> to create a <xref:System.Xaml.XamlWriter>, and then use <xref:System.Xaml.XamlServices> to serialize the workflow definition by using the <xref:System.Xaml.XamlWriter>.</span></span> <span data-ttu-id="3a745-119"><xref:System.Activities.XamlIntegration.ActivityXamlServices>, <xref:System.Activities.ActivityBuilder> xaml 'ye ve xaml 'ye ve XAML iş akışlarını yüklemeye ve çağrılabilir bir öğesine <xref:System.Activities.DynamicActivity> döndürme yöntemlerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="3a745-119"><xref:System.Activities.XamlIntegration.ActivityXamlServices> has methods to map <xref:System.Activities.ActivityBuilder> instances to and from XAML and to load XAML workflows and return a <xref:System.Activities.DynamicActivity> that can be invoked.</span></span> <span data-ttu-id="3a745-120">Aşağıdaki örnekte, <xref:System.Activities.ActivityBuilder> önceki örnekteki örnek bir dizeye serileştirilir ve bir dosyaya kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="3a745-120">In the following example, the <xref:System.Activities.ActivityBuilder> instance from the previous example is serialized to a string and saved to a file.</span></span>

```csharp
// Serialize the workflow to XAML and store it in a string.
StringBuilder sb = new StringBuilder();
StringWriter tw = new StringWriter(sb);
XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(tw, new XamlSchemaContext()));
XamlServices.Save(xw, ab);
string serializedAB = sb.ToString();

// Display the XAML to the console.
Console.WriteLine(serializedAB);

// Serialize the workflow to XAML and save it to a file.
StreamWriter sw = File.CreateText(@"C:\Workflows\add.xaml");
XamlWriter xw2 = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(sw, new XamlSchemaContext()));
XamlServices.Save(xw2, ab);
sw.Close();
```

<span data-ttu-id="3a745-121">Aşağıdaki örnek, serileştirilmiş iş akışını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3a745-121">The following example represents the serialized workflow.</span></span>

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

<span data-ttu-id="3a745-122">Seri hale getirilmiş bir iş akışını yüklemek için <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="3a745-122">To load a serialized workflow, use the <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> method.</span></span> <span data-ttu-id="3a745-123">Bu, serileştirilmiş iş akışı tanımını alır ve <xref:System.Activities.DynamicActivity> iş akışı tanımını temsil eden bir döndürür.</span><span class="sxs-lookup"><span data-stu-id="3a745-123">This takes the serialized workflow definition and returns a <xref:System.Activities.DynamicActivity> that represents the workflow definition.</span></span> <span data-ttu-id="3a745-124">XAML, <xref:System.Activities.Activity.CacheMetadata%2A> doğrulama işlemi sırasında gövdesinde çağrılana kadar seri durumdan çıkarılmadığını unutmayın <xref:System.Activities.DynamicActivity> .</span><span class="sxs-lookup"><span data-stu-id="3a745-124">Note that the XAML is not deserialized until <xref:System.Activities.Activity.CacheMetadata%2A> is called on the body of the <xref:System.Activities.DynamicActivity> during the validation process.</span></span> <span data-ttu-id="3a745-125">Doğrulama açıkça çağrılmadıysanız, iş akışı çağrıldığında yapılır.</span><span class="sxs-lookup"><span data-stu-id="3a745-125">If validation is not explicitly called, then it is performed when the workflow is invoked.</span></span> <span data-ttu-id="3a745-126">XAML iş akışı tanımı geçersizse, bir <xref:System.ArgumentException> özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3a745-126">If the XAML workflow definition is invalid, then an <xref:System.ArgumentException> exception is thrown.</span></span> <span data-ttu-id="3a745-127"><xref:System.Activities.Activity.CacheMetadata%2A>Çağrılarından ve çağrısından oluşan tüm özel durumlar <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> , çağıran tarafından işlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="3a745-127">Any exceptions thrown from <xref:System.Activities.Activity.CacheMetadata%2A> escape from the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> and must be handled by the caller.</span></span> <span data-ttu-id="3a745-128">Aşağıdaki örnekte, önceki örnekteki serileştirilmiş iş akışı kullanılarak yüklenir ve çağrılır <xref:System.Activities.WorkflowInvoker> .</span><span class="sxs-lookup"><span data-stu-id="3a745-128">In the following example, the serialized workflow from the previous example is loaded and invoked by using <xref:System.Activities.WorkflowInvoker>.</span></span>

[!code-csharp[CFX_WorkflowApplicationExample#43](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#43)]

<span data-ttu-id="3a745-129">Bu iş akışı çağrıldığında, konsola aşağıdaki çıktı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="3a745-129">When this workflow is invoked, the following output is displayed to the console.</span></span>

<span data-ttu-id="3a745-130">**25 + 15**</span><span class="sxs-lookup"><span data-stu-id="3a745-130">**25 + 15**</span></span>\
<span data-ttu-id="3a745-131">**40**</span><span class="sxs-lookup"><span data-stu-id="3a745-131">**40**</span></span>

> [!NOTE]
> <span data-ttu-id="3a745-132">Giriş ve çıkış bağımsız değişkenleriyle iş akışlarını çağırma hakkında daha fazla bilgi için bkz. [Workflowwınvoker ve WorkflowApplication kullanma](using-workflowinvoker-and-workflowapplication.md) <xref:System.Activities.WorkflowInvoker.Invoke%2A> .</span><span class="sxs-lookup"><span data-stu-id="3a745-132">For more information about invoking workflows with input and output arguments, see [Using WorkflowInvoker and WorkflowApplication](using-workflowinvoker-and-workflowapplication.md) and <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span></span>

<span data-ttu-id="3a745-133">Serileştirilmiş iş akışı C# ifadeleri içeriyorsa, <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> özelliği olarak ayarlanmış bir örnek `true` öğesine parametresi olarak geçirilmesi gerekir <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType> , aksi halde <xref:System.NotSupportedException> aşağıdakine benzer bir Iletiyle birlikte oluşturulur: **' CSharpValue ' 1 ' ifade etkinlik türü, çalıştırmak için derleme gerektirir.  Lütfen iş akışının derlendiğinden emin olun.**</span><span class="sxs-lookup"><span data-stu-id="3a745-133">If the serialized workflow contains C# expressions, then an <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> instance with its <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> property set to `true` must be passed as a parameter to <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>, otherwise a <xref:System.NotSupportedException> will be thrown with a message similar to the following: **Expression Activity type 'CSharpValue\`1' requires compilation in order to run.  Please ensure that the workflow has been compiled.**</span></span>

```csharp
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings
{
    CompileExpressions = true
};

DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;
```

<span data-ttu-id="3a745-134">Daha fazla bilgi için bkz. [C# ifadeleri](csharp-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="3a745-134">For more information, see [C# Expressions](csharp-expressions.md).</span></span>

<span data-ttu-id="3a745-135">Seri hale getirilmiş bir iş akışı tanımı <xref:System.Activities.ActivityBuilder> , yöntemi kullanılarak bir örneğe de yüklenebilir <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.CreateBuilderReader%2A> .</span><span class="sxs-lookup"><span data-stu-id="3a745-135">A serialized workflow definition can also be loaded into an <xref:System.Activities.ActivityBuilder> instance by using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.CreateBuilderReader%2A> method.</span></span> <span data-ttu-id="3a745-136">Serileştirilmiş bir iş akışı bir örneğe yüklendikten sonra <xref:System.Activities.ActivityBuilder> , bu, incelenebilir ve değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="3a745-136">After a serialized workflow is loaded into an <xref:System.Activities.ActivityBuilder> instance, it can be inspected and modified.</span></span> <span data-ttu-id="3a745-137">Bu, özel iş akışı Tasarımcısı yazarları için yararlıdır ve tasarım sürecinde iş akışı tanımlarının kaydedilmesi ve yeniden yüklenmesi için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a745-137">This is useful for custom workflow designer authors and provides a mechanism for saving and reloading workflow definitions during the design process.</span></span> <span data-ttu-id="3a745-138">Aşağıdaki örnekte, önceki örnekteki serileştirilmiş iş akışı tanımı yüklenir ve özellikleri denetlenir.</span><span class="sxs-lookup"><span data-stu-id="3a745-138">In the following example, the serialized workflow definition from the previous example is loaded and its properties are inspected.</span></span>

[!code-csharp[CFX_WorkflowApplicationExample#44](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#44)]
