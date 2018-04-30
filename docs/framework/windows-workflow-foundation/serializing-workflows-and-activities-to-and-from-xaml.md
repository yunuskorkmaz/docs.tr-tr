---
title: İş akışları ve etkinlikler XAML seri hale getirme
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 37685b32-24e3-4d72-88d8-45d5fcc49ec2
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a36b8a6bdf1a024f4ddee91bd937afac516e391f
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="serializing-workflows-and-activities-to-and-from-xaml"></a>İş akışları ve etkinlikler XAML seri hale getirme
Derlemelerde bulunan türlerine derlenmiş ek olarak, iş akışı tanımları da XAML için seri hale getirilebilir. Bu seri hale getirilmiş tanımları düzenleme için yeniden yüklenmesi veya denetleme, derleme için bir yapı sistemi geçirilen veya yüklenen ve çağrılır. Bu konu, iş akışı tanımları seri hale getirme ve XAML iş akışı tanımları ile çalışmaya genel bir bakış sağlar.  
  
## <a name="working-with-xaml-workflow-definitions"></a>XAML iş akışı tanımları ile çalışma  
 Seri hale getirme, bir iş akışı tanımı oluşturmak için <xref:System.Activities.ActivityBuilder> sınıfı kullanılır. Oluşturma bir <xref:System.Activities.ActivityBuilder> oluşturmaya çok benzer bir <xref:System.Activities.DynamicActivity>. İstenen herhangi bir bağımsız değişken belirtilir ve davranışı oluşturan etkinlikler yapılandırılır. Aşağıdaki örnekte, bir `Add` etkinlik oluşturulan iki giriş bağımsız değişkeni alır, bunları bir araya getirir ve sonucunu döndürür. Bu etkinlik bir sonuç genel döndürdüğünden <xref:System.Activities.ActivityBuilder%601> sınıfı kullanılır.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#41](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#41)]  
  
 Her biri <xref:System.Activities.DynamicActivityProperty> örnekleri temsil eden iş akışına giriş bağımsız değişkenlerinde birini ve <xref:System.Activities.ActivityBuilder.Implementation%2A> iş akışı mantığı oluşturan etkinlikler içerir. Bu örnekte r değeri ifadeleri Visual Basic ifadeleri olduğuna dikkat edin. Lambda ifadeleri için XAML serileştirilebilir olmayan sürece <xref:System.Activities.Expressions.ExpressionServices.Convert%2A> kullanılır. Serileştirilmiş iş akışları açılacak veya iş akışı Tasarımcısı'nda düzenlenebilir yönelikse Visual Basic ifadeleri kullanılmalıdır. Daha fazla bilgi için bkz: [geliştirme iş akışları, etkinlikler ve ifadeler kullanarak kesinliği kod](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).  
  
 Tarafından temsil edilen iş akışı tanımı serileştirmek için <xref:System.Activities.ActivityBuilder> XAML, kullanım örneğine <xref:System.Activities.XamlIntegration.ActivityXamlServices> oluşturmak için bir <xref:System.Xaml.XamlWriter>ve ardından <xref:System.Xaml.XamlServices> kullanarak iş akışı tanımı serileştirmek için <xref:System.Xaml.XamlWriter>. <xref:System.Activities.XamlIntegration.ActivityXamlServices> eşleme için yöntemleri vardır <xref:System.Activities.ActivityBuilder> örnekleri ve XAML ve XAML iş akışları yükleme ve döndürmek için bir <xref:System.Activities.DynamicActivity> , çağrılabilir. Aşağıdaki örnekte, <xref:System.Activities.ActivityBuilder> örneğinin önceki örnekten bir dizeye sıralanabilir ve ayrıca bir dosyaya kaydedilir.  
  
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
  
 Aşağıdaki örnek serileştirilmiş iş akışı temsil eder.  
  
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
  
 Seri hale getirilmiş bir iş akışını yüklemek için <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> yöntemi kullanılır. Bu seri hale getirilmiş iş akışı tanımı alıp döndüren bir <xref:System.Activities.DynamicActivity> , iş akışı tanımını temsil eder. XAML kadar serisi yok Not <xref:System.Activities.Activity.CacheMetadata%2A> gövdesi adlı <xref:System.Activities.DynamicActivity> doğrulama işlemi sırasında. Doğrulama açıkça çağrılmazsa iş akışı çağrıldığında sonra onu gerçekleştirilir. XAML iş akışı tanımı geçersizse, sonra bir <xref:System.ArgumentException> özel durumu oluşur. Gelen karşılaşılan özel durumlar <xref:System.Activities.Activity.CacheMetadata%2A> çağrıya kaçış <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> ve çağıran tarafından yapılması gerekir. Aşağıdaki örnekte, önceki örnekte serileştirilmiş iş akışını yüklendiğinde ve kullanılarak <xref:System.Activities.WorkflowInvoker>.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#43](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#43)]  
  
 Bu iş akışı çağrıldığında, aşağıdaki çıktıyı konsola görüntülenir.  
  
 **25 + 15**  
**40**    
> [!NOTE]
>  Giriş ve çıkış bağımsız değişkenleri iş akışlarıyla çağırma hakkında daha fazla bilgi için bkz: [kullanarak WorkflowInvoker ve WorkflowApplication](../../../docs/framework/windows-workflow-foundation/using-workflowinvoker-and-workflowapplication.md) ve <xref:System.Activities.WorkflowInvoker.Invoke%2A>.  
  
 C# ifadeler, sıralı iş akışı içeriyorsa, sonra bir <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> örneği kendi <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> özelliğini `true` bir parametre olarak geçirilmelidir <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>, aksi takdirde bir <xref:System.NotSupportedException> benzer bir ileti ile oluşturulur Aşağıdaki: `Expression Activity type 'CSharpValue`1' derleme çalıştırmak için gereklidir.  Lütfen iş akışının derlendikten olduğundan emin olun.'  
  
```csharp  
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings  
{  
    CompileExpressions = true  
};  
  
DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;  
```  
  
 Daha fazla bilgi için bkz: [C# ifadeleri](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md).  
  
 Serileştirilmiş iş akışı tanımı ayrıca içine yüklenebilir bir <xref:System.Activities.ActivityBuilder> kullanarak örnek <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.CreateBuilderReader%2A> yöntemi. Serileştirilmiş bir iş akışı içine yüklendikten sonra bir <xref:System.Activities.ActivityBuilder> Denetlenmekte ve değiştiren örneği. Bu, özel iş akışı Tasarımcısı yazarlar için yararlıdır ve kaydetme ve iş akışı tanımları tasarım işlemi sırasında yeniden yükleme için bir mekanizma sağlar. Aşağıdaki örnekte, önceki örnekten serileştirilmiş iş akışı tanımı yüklendi ve özelliklerini denetlenir.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#44](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#44)]
