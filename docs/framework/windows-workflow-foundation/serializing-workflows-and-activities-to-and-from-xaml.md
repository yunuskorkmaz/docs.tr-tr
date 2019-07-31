---
title: XAML’de İş Akışı ve Etkinlikleri Serileştirme
ms.date: 03/30/2017
ms.assetid: 37685b32-24e3-4d72-88d8-45d5fcc49ec2
ms.openlocfilehash: c18afa7232adabc4f1c4e17fde993064b9189e39
ms.sourcegitcommit: 3eeea78f52ca771087a6736c23f74600cc662658
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68671904"
---
# <a name="serialize-workflows-and-activities-to-and-from-xaml"></a>XAML 'ye ve XAML 'ye Iş akışlarını ve etkinlikleri seri hale getirme

Derlemeler içinde yer alan türlere derlenmenin yanı sıra, iş akışı tanımları da XAML 'ye seri hale getirilebilir. Bu serileştirilmiş tanımlar, derleme veya inceleme için yeniden yüklenebilir, derleme için bir derleme sistemine geçirilebilir veya yüklenip çağrılabilir. Bu konu, iş akışı tanımlarının serileştirilmesi ve XAML iş akışı tanımlarıyla çalışma hakkında genel bakış sağlar.

## <a name="work-with-xaml-workflow-definitions"></a>XAML Iş akışı tanımlarıyla çalışma

Serileştirme için bir iş akışı tanımı oluşturmak üzere <xref:System.Activities.ActivityBuilder> sınıfı kullanılır. Oluşturma, oluşturmak için çok benzerdir <xref:System.Activities.DynamicActivity>. <xref:System.Activities.ActivityBuilder> İstenen bağımsız değişkenler belirtilir ve davranışı oluşturan etkinlikler yapılandırılır. Aşağıdaki örnekte, iki giriş bağımsız `Add` değişkeni alan bir etkinlik oluşturulur, bunları bir araya ekler ve sonucu döndürür. Bu etkinlik bir sonuç döndürdüğünden, genel <xref:System.Activities.ActivityBuilder%601> sınıf kullanılır.

[!code-csharp[CFX_WorkflowApplicationExample#41](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#41)]

Örneklerin her biri, iş akışına ait giriş bağımsız değişkenlerinden birini temsil eder <xref:System.Activities.ActivityBuilder.Implementation%2A> ve iş akışının mantığını oluşturan etkinlikleri içerir. <xref:System.Activities.DynamicActivityProperty> Bu örnekteki r-value ifadelerinin Visual Basic ifadeler olduğunu unutmayın. Lambda ifadeleri, kullanılmamışsa <xref:System.Activities.Expressions.ExpressionServices.Convert%2A> xaml 'ye serileştirilebilir değildir. Seri hale getirilmiş iş akışlarının iş akışı tasarımcısında açılması veya düzenlenmesi amaçlanıyorsa, Visual Basic ifadelerin kullanılması gerekir. Daha fazla bilgi için bkz. zorunlu [kod kullanarak Iş akışları, etkinlikler ve Ifadeler yazma](authoring-workflows-activities-and-expressions-using-imperative-code.md).

<xref:System.Activities.ActivityBuilder> Örnek tarafından temsil edilen iş akışı tanımını xaml 'e seri hale getirmek için <xref:System.Activities.XamlIntegration.ActivityXamlServices> , bir <xref:System.Xaml.XamlWriter>oluşturmak için öğesini kullanın ve <xref:System.Xaml.XamlServices> kullanarak <xref:System.Xaml.XamlWriter>iş akışı tanımını seri hale getirmek için kullanın. <xref:System.Activities.XamlIntegration.ActivityXamlServices>, XAML 'ye ve <xref:System.Activities.ActivityBuilder> xaml 'ye ve XAML iş akışlarını yüklemeye ve çağrılabilir bir <xref:System.Activities.DynamicActivity> öğesine döndürme yöntemlerine sahiptir. Aşağıdaki örnekte, <xref:System.Activities.ActivityBuilder> önceki örnekteki örnek bir dizeye serileştirilir ve bir dosyaya kaydedilir.

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

Aşağıdaki örnek, serileştirilmiş iş akışını temsil eder.

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

Seri hale getirilmiş bir iş akışını yüklemek için <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> yöntemini kullanın. Bu, serileştirilmiş iş akışı tanımını alır ve iş <xref:System.Activities.DynamicActivity> akışı tanımını temsil eden bir döndürür. XAML, doğrulama işlemi <xref:System.Activities.Activity.CacheMetadata%2A> <xref:System.Activities.DynamicActivity> sırasında gövdesinde çağrılana kadar seri durumdan çıkarılmadığını unutmayın. Doğrulama açıkça çağrılmadıysanız, iş akışı çağrıldığında yapılır. XAML iş akışı tanımı geçersizse, bir <xref:System.ArgumentException> özel durum oluşturulur. Çağrılarından <xref:System.Activities.Activity.CacheMetadata%2A> ve çağrısından oluşan tüm özel durumlar, çağıran tarafından işlenmelidir. <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> Aşağıdaki örnekte, önceki örnekteki serileştirilmiş iş akışı kullanılarak <xref:System.Activities.WorkflowInvoker>yüklenir ve çağrılır.

[!code-csharp[CFX_WorkflowApplicationExample#43](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#43)]

Bu iş akışı çağrıldığında, konsola aşağıdaki çıktı görüntülenir.

**25 + 15**\
**40**

> [!NOTE]
> Giriş ve çıkış bağımsız değişkenleriyle iş akışlarını çağırma hakkında daha fazla bilgi için bkz <xref:System.Activities.WorkflowInvoker.Invoke%2A>. [Workflowwınvoker ve WorkflowApplication kullanma](using-workflowinvoker-and-workflowapplication.md) .

Serileştirilmiş iş akışı ifadeler içeriyorsa C# , <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> özelliği olarak ayarlanmış `true` bir örnek öğesine <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>parametresi olarak geçirilmesi <xref:System.NotSupportedException> gerekir, aksi halde, benzer bir iletiyle birlikte şunları yapın: **' CSharpValue ' 1 ' ifade etkinlik türü, çalıştırmak için derleme gerektiriyor.  Lütfen iş akışının derlendiğinden emin olun.**

```csharp
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings
{
    CompileExpressions = true
};

DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;
```

Daha fazla bilgi için bkz [ C# . ifadeler](csharp-expressions.md).

Seri hale getirilmiş bir iş akışı tanımı, <xref:System.Activities.ActivityBuilder> <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.CreateBuilderReader%2A> yöntemi kullanılarak bir örneğe de yüklenebilir. Serileştirilmiş bir iş akışı bir <xref:System.Activities.ActivityBuilder> örneğe yüklendikten sonra, bu, incelenebilir ve değiştirilebilir. Bu, özel iş akışı Tasarımcısı yazarları için yararlıdır ve tasarım sürecinde iş akışı tanımlarının kaydedilmesi ve yeniden yüklenmesi için bir mekanizma sağlar. Aşağıdaki örnekte, önceki örnekteki serileştirilmiş iş akışı tanımı yüklenir ve özellikleri denetlenir.

[!code-csharp[CFX_WorkflowApplicationExample#44](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#44)]
