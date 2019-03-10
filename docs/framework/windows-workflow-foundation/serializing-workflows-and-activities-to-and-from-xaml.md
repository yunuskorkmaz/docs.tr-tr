---
title: İş akışları ve etkinlikler XAML seri hale getirme
ms.date: 03/30/2017
ms.assetid: 37685b32-24e3-4d72-88d8-45d5fcc49ec2
ms.openlocfilehash: 70ee2e8e0c457e9db2853935ef95b86c7f903fc3
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57715847"
---
# <a name="serializing-workflows-and-activities-to-and-from-xaml"></a>İş akışları ve etkinlikler XAML seri hale getirme
Derlemede bulunan türleri içine derlenmiş yanı sıra, iş akışı tanımları ayrıca XAML için seri hale getirilebilir. Bu seri hale getirilmiş tanımlarını düzenlemek için yeniden yüklenmesi veya İnceleme için bir derleme sistemi derleme için geçirilen veya yüklendi ve çağrılır. Bu konu, iş akışı tanımları seri hale getirme ve XAML iş akışı tanımları ile çalışmaya genel bir bakış sağlar.  
  
## <a name="working-with-xaml-workflow-definitions"></a>XAML iş akışı tanımları ile çalışma  
 Seri hale getirme, bir iş akışı tanımı oluşturma <xref:System.Activities.ActivityBuilder> sınıfı kullanılır. Oluşturma bir <xref:System.Activities.ActivityBuilder> oluşturmaya çok benzer bir <xref:System.Activities.DynamicActivity>. İstenen herhangi bir bağımsız değişken belirtilir ve davranışı oluşturan etkinlikler yapılandırılır. Aşağıdaki örnekte, bir `Add` etkinlik oluşturulan iki giriş bağımsız değişkeni alır, bunları bir araya getirir ve sonucu döndürür. Bu etkinlik, genel bir sonuç döndürdüğünden <xref:System.Activities.ActivityBuilder%601> sınıfı kullanılır.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#41](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#41)]  
  
 Her biri <xref:System.Activities.DynamicActivityProperty> örnekleri temsil eden iş akışına giriş bağımsız değişkenlerden biri ve <xref:System.Activities.ActivityBuilder.Implementation%2A> iş akışı mantığı oluşturma etkinliklerinin içerir. Bu örnekte r değeri ifadeleri Visual Basic deyimleri olduğunu unutmayın. Lambda ifadeleri için XAML serileştirilebilir olmayan sürece <xref:System.Activities.Expressions.ExpressionServices.Convert%2A> kullanılır. Seri hale getirilmiş iş akışları açılamıyor veya iş akışı Tasarımcısı'nda düzenlenebilir istiyorsanız Visual Basic deyimleri kullanılmalıdır. Daha fazla bilgi için [yazma iş akışları, etkinlikler ve ifadeler kullanarak kesinliği kod](authoring-workflows-activities-and-expressions-using-imperative-code.md).  
  
 İş akışı tanımı tarafından temsil edilen seri hale getirmek için <xref:System.Activities.ActivityBuilder> XAML, kullanım örneğine <xref:System.Activities.XamlIntegration.ActivityXamlServices> oluşturmak için bir <xref:System.Xaml.XamlWriter>ve ardından <xref:System.Xaml.XamlServices> kullanarak iş akışı tanımı seri hale getirmek için <xref:System.Xaml.XamlWriter>. <xref:System.Activities.XamlIntegration.ActivityXamlServices> eşleme yöntemlerine sahiptir <xref:System.Activities.ActivityBuilder> örnekleri ve XAML ve XAML iş akışları yükleme ve döndürmek için bir <xref:System.Activities.DynamicActivity> , çağrılabilir. Aşağıdaki örnekte, <xref:System.Activities.ActivityBuilder> örneği önceki örnekte bir dizeye serileştirilmiş ve ayrıca bir dosyaya kaydedilebilir.  
  
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
  
 Aşağıdaki örnek, seri hale getirilmiş iş akışını temsil eder.  
  
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
  
 Seri hale getirilmiş bir iş akışı yüklenecek <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> yöntemi kullanılır. Bu seri hale getirilmiş iş akışı tanımı alan ve döndüren bir <xref:System.Activities.DynamicActivity> , iş akışı tanımını temsil eder. XAML kadar serisi değil Not <xref:System.Activities.Activity.CacheMetadata%2A> gövdesinin adlı <xref:System.Activities.DynamicActivity> doğrulama işlemi sırasında. Doğrulama açıkça çağrılmaz iş akışı çağrıldığında daha sonra bu yapılmaz. XAML iş akışı tanımı geçersizse, bir <xref:System.ArgumentException> özel durumu oluşturulur. Şuradan oluşturulduğu özel durumların <xref:System.Activities.Activity.CacheMetadata%2A> kaçış çağrısından <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> ve çağıran tarafından ele alınması gerekir. Aşağıdaki örnekte, önceki örnekte seri hale getirilmiş iş akışı yüklenen ve kullanarak çağrılan <xref:System.Activities.WorkflowInvoker>.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#43](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#43)]  
  
 Bu iş akışı çağrıldığında, aşağıdaki çıktıyı konsola görüntülenir.  
  
 **25 + 15**  
**40**    
> [!NOTE]
>  Giriş ve çıkış bağımsız değişkenleri ile iş akışlarını çağırma hakkında daha fazla bilgi için bkz. [kullanarak Workflowınvoker ve WorkflowApplication](using-workflowinvoker-and-workflowapplication.md) ve <xref:System.Activities.WorkflowInvoker.Invoke%2A>.  
  
 Seri hale getirilmiş iş akışı içeriyorsa C# ifadeleri, ardından bir <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> ile örnek kendi <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> özelliğini `true` bir parametre olarak geçirilmelidir <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>, aksi halde bir <xref:System.NotSupportedException> ile benzer bir ileti oluşturulur şu şekilde: `Expression Activity type 'CSharpValue`1' çalıştırmak için derleme gerektirir.  İş akışı derlendiğinden emin olun.'  
  
```csharp  
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings  
{  
    CompileExpressions = true  
};  
  
DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;  
```  
  
 Daha fazla bilgi için [ C# ifadeleri](csharp-expressions.md).  
  
 Bir seri hale getirilmiş iş akışı tanımı da içine yüklenemez bir <xref:System.Activities.ActivityBuilder> kullanarak örneği <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.CreateBuilderReader%2A> yöntemi. Seri hale getirilmiş bir iş akışı uygulamasına yüklendikten sonra bir <xref:System.Activities.ActivityBuilder> inceledi ve değiştiren örneği. Bu özel iş akışı Tasarımcısı yazarları için kullanışlıdır ve kaydetme ve iş akışı tanımları tasarım işlemi sırasında yeniden yüklenmesi için bir mekanizma sağlar. Aşağıdaki örnekte, önceki örnekte seri hale getirilmiş iş akışı tanımı yüklendi ve özelliklerini olup olmadığı denetlenir.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#44](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#44)]
