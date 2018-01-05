---
title: "İş akışları, etkinlikler ve ifadeler kesinlik temelli kod kullanarak geliştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cefc9cfc-2882-4eb9-8c94-7a6da957f2b2
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ee7c5320caa3b7704813b94d4ddfbf1ce0fecf96
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="authoring-workflows-activities-and-expressions-using-imperative-code"></a>İş akışları, etkinlikler ve ifadeler kesinlik temelli kod kullanarak geliştirme
Bir iş akışı tanımı yapılandırılmış etkinlik nesne ağacının ' dir. Bu ağaç etkinlikler XAML elle düzenlemeye veya XAML üretmek için iş akışı Tasarımcısı kullanarak da dahil olmak üzere birçok şekilde tanımlanabilir. XAML kullanın, ancak, bir gereksinim değildir. İş akışı tanımları de bir program aracılığıyla oluşturulabilir. Bu konu, kod kullanarak iş akışı tanımları, etkinlikler ve ifadeler oluşturmaya genel bir bakış sağlar. Kod kullanarak XAML iş akışlarıyla çalışma örnekleri için bkz: [seri hale getirme iş akışları ve etkinlikler XAML gelen ve giden](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md).  
  
## <a name="creating-workflow-definitions"></a>İş akışı tanımları oluşturma  
 Bir iş akışı tanımı, bir etkinlik türünün bir örneği başlatmasını ve etkinlik nesnenin özelliklerini yapılandırma oluşturulabilir. Alt etkinlikler içermeyen etkinlikler için bu kodu birkaç satırlık kullanılarak gerçekleştirilebilir.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#47](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#47)]  
  
> [!NOTE]
>  Bu konuda kullanım örnekleri <xref:System.Activities.WorkflowInvoker> örnek iş akışlarını çalıştırmak için. [!INCLUDE[crabout](../../../includes/crabout-md.md)]İş akışları, bağımsız değişkenleri geçirme ve kullanılabilir farklı barındırma seçenekleri çağrılırken, bkz: [kullanarak WorkflowInvoker ve WorkflowApplication](../../../docs/framework/windows-workflow-foundation/using-workflowinvoker-and-workflowapplication.md).  
  
 Bu örnekte, bir tek oluşan bir iş akışı <xref:System.Activities.Statements.WriteLine> etkinlik oluşturulur. <xref:System.Activities.Statements.WriteLine> Etkinliğin <xref:System.Activities.Statements.WriteLine.Text%2A> bağımsız değişkeni olarak ayarlanmış ve iş akışı çağrılır. Oluşturma yöntemi, bir etkinlik alt etkinlikleri içeriyorsa, benzer. Aşağıdaki örnek kullanan bir <xref:System.Activities.Statements.Sequence> iki etkinlik <xref:System.Activities.Statements.WriteLine> etkinlikler.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#48](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#48)]  
  
### <a name="using-object-initializers"></a>Nesne başlatıcıları kullanma  
 Bu konudaki örnekler nesne başlatma sözdizimini kullanın. Nesne başlatma sözdizimi etkinlikleri arasındaki ilişkiyi gösterir ve iş akışındaki etkinliklerin hiyerarşik bir görünümü sağlar kodda iş akışı tanımları oluşturmak için kullanışlı bir yol olabilir. Program aracılığıyla iş akışları oluşturduğunuzda, nesne başlatma sözdizimi kullanma zorunluluğu yoktur. Aşağıdaki örnek önceki örneğe işlevsel olarak eşdeğerdir.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#49](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#49)]  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]Nesne başlatıcılar, bkz: [nasıl yapılır: nesneler Oluşturucusu (C# programlama Kılavuzu) çağırma olmadan başlatmak](http://go.microsoft.com/fwlink/?LinkId=161015) ve [nasıl yapılır: nesne Başlatıcı kullanarak nesne bildirme](http://go.microsoft.com/fwlink/?LinkId=161016).  
  
### <a name="working-with-variables-literal-values-and-expressions"></a>Değişkenleri, değişmez değerler ve ifadeler ile çalışma  
 Kod kullanarak bir iş akışı tanımı oluşturma sırasında hangi kod oluşturma iş akışı tanımının bir parçası olarak çalıştırır ve bu iş akışı örneği yürütülmesini bir parçası olarak hangi kodu yürütür unutmayın. Örneğin, aşağıdaki iş akışı, rastgele bir sayı üretmek ve konsola yazma için tasarlanmıştır.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#50](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#50)]  
  
 Bu iş akışı tanımı kod zaman yürütülür, çağrısı `Random.Next` yapılır ve sonucu iş akışı tanımı bir hazır değer olarak depolanır. Bu iş akışının çok sayıda örnekleri çağrılabilir ve tüm aynı numarasını görüntüler. Diğer bir deyişle bir ifade kullanılan iş akışı yürütme sırasında ortaya rastgele sayı oluşturma için iş akışı her çalıştığında değerlendirilir. Aşağıdaki örnekte, bir Visual Basic ifade ile kullanılan bir <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#51](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#51)]  
  
 Önceki örnekte ifade kullanarak da uygulanabilir bir <xref:Microsoft.CSharp.Activities.CSharpValue%601> ve C# ifade.  
  
```csharp  
new Assign<int>  
{  
    To = n,  
    Value = new CSharpValue<int>("new Random().Next(1, 101)")  
}  
```  
  
 Bunları içeren iş akışı çağrılmadan önce C# ifadeleri derlenmiş olmalıdır. C# ifadeleri derlenmemiş, bir <xref:System.NotSupportedException> aşağıdakine benzer bir ileti ile iş akışı çağrıldığında oluşturulur: `Expression Activity type 'CSharpValue`1' derleme çalıştırmak için gereklidir.  Lütfen iş akışının derlendikten olduğundan emin olun.' Visual Studio'da C# oluşturulan iş akışı içeren çoğu senaryoda ifadeleri otomatik olarak derlenen ancak kodu iş akışları gibi bazı senaryolarda C# ifadeleri el ile derlenmiş olmalıdır. C# ifadeleri derlemek nasıl bir örnek için bkz: [kullanarak C# kod iş akışları ifadelerinde](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) bölümünü [C# ifadeleri](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md) konu.  
  
 A <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> bir ifadede bir r olarak kullanılan Visual Basic söz dizimine bir ifadeyi temsil eder ve bir <xref:Microsoft.CSharp.Activities.CSharpValue%601> bir ifadede bir r olarak kullanılan C# sözdizimi bir ifadeyi temsil eder. Bu ifadeler içeren etkinlik her yürütüldüğünde değerlendirilir. İfadenin sonucu iş akışı değişkenine atanan `n`, ve bu sonuçların sonraki etkinliği iş akışı tarafından kullanılır. İş akışı değişkeninin değerini erişmek için `n` çalışma zamanında <xref:System.Activities.ActivityContext> gereklidir. Bu, aşağıdaki lambda ifadesi kullanılarak erişilebilir.  
  
> [!NOTE]
>  Hem de bu kodu örnekleri olduğunu unutmayın kullandığınız C# programlama dili olarak, ancak bir kullanan bir <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> ve bir kullanan bir <xref:Microsoft.CSharp.Activities.CSharpValue%601>. <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>ve <xref:Microsoft.CSharp.Activities.CSharpValue%601> hem Visual Basic ve Visual C# projeleri içinde kullanılabilir. Varsayılan olarak, iş akışı Tasarımcısı'nda oluşturulan ifadeler barındırma projenin dili eşleşmesi. İş akışları kodda oluştururken, istenen iş akışı yazarı kümeleri dilidir.  
  
 Bu örneklerde ifadenin sonucu iş akışı değişkenine atanan `n`, ve bu sonuçların sonraki etkinliği iş akışı tarafından kullanılır. İş akışı değişkeninin değerini erişmek için `n` çalışma zamanında <xref:System.Activities.ActivityContext> gereklidir. Bu, aşağıdaki lambda ifadesi kullanılarak erişilebilir.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#52](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#52)]  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]Lambda ifadeleri bkz [Lambda ifadeleri (C# programlama Kılavuzu)](http://go.microsoft.com/fwlink/?LinkID=152436) veya [Lambda ifadeleri (Visual Basic)](http://go.microsoft.com/fwlink/?LinkID=152437).  
  
 Lambda ifadeleri XAML biçimine seri hale getirilebilir değildir. Lambda ifadeleri bir iş akışıyla seri denemesi yapılırsa, bir <xref:System.Activities.Expressions.LambdaSerializationException> aşağıdaki iletiyle oluşturulur: "Bu iş akışı kodunda belirtilen lambda ifadeleri içerir. Bu deyimler XAML seri hale getirilebilir değildir. İş akışınızı XAML serileştirilebilir yapmak için ya da VisualBasicValue/VisualBasicReference veya ExpressionServices.Convert(lambda) kullanın. Bu, lambda ifadeleri ifade etkinliklerine dönüştürür." Bu ifade XAML ile uyumlu hale getirmek için kullanmak <xref:System.Activities.Expressions.ExpressionServices> ve <xref:System.Activities.Expressions.ExpressionServices.Convert%2A>, aşağıdaki örnekte gösterildiği gibi.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#53](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#53)]  
  
 A <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> de kullanılabilir. Lambda ifadesi bir Visual Basic ifade kullanırken gerekli olduğunu unutmayın.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#54](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#54)]  
  
 Çalışma zamanında, Visual Basic ifadeleri LINQ ifadelere derlenir. Önceki örneklerde her ikisi de serileştirilmiş XAML görüntülenmesine ve iş akışı Tasarımcısı'nda düzenlenemiyor kullanmak için tasarlanmıştır, ancak XAML serileştirilebilir <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> , ifadeler için. Serileştirilmiş kullanan iş akışları `ExpressionServices.Convert` tasarımcıda açılır, ancak ifadesinin değerini boş olacaktır. [!INCLUDE[crabout](../../../includes/crabout-md.md)]XAML iş akışlarına seri hale getirme, bkz: [seri hale getirme iş akışları ve etkinlikler XAML gelen ve giden](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md).  
  
#### <a name="literal-expressions-and-reference-types"></a>Sabit ifadeleri ve başvuru türleri  
 Sabit ifadeleri iş akışlarında tarafından gösterilen <xref:System.Activities.Expressions.Literal%601> etkinlik. Aşağıdaki <xref:System.Activities.Statements.WriteLine> etkinlikleri işlevsel olarak eşdeğerdir.  
  
```csharp  
new WriteLine  
{  
    Text = "Hello World."  
},  
new WriteLine  
{  
    Text = new Literal<string>("Hello World.")  
}  
```  
  
 Değişmez değer ifadesi dışında herhangi bir başvuru türü ile başlatmak için geçersiz <xref:System.String>. Aşağıdaki örnekte, bir <xref:System.Activities.Statements.Assign> etkinliğin <xref:System.Activities.Statements.Assign.Value%2A> özelliğinin başlatıldığı değişmez değer ifadesi kullanarak bir `List<string>`.  
  
```csharp  
new Assign  
{  
    To = new OutArgument<List<string>>(items),  
    Value = new InArgument<List<string>>(new List<string>())  
},  
```  
  
 Bu etkinliğini içeren iş akışı doğrulandığında, aşağıdaki doğrulama hatasını döndürdü: "değişmez değeri yalnızca değer türleri ve destekler System.String sabit türü. Tür System.Collections.Generic.List'1[System.String] sabit değer olarak kullanılamaz." İş akışı çağrılırsa, bir <xref:System.Activities.InvalidWorkflowException> atılır doğrulama hatasının metni içerir. Bir başvuru türü ile bir değişmez değer ifadesi oluşturma iş akışı her örneği için başvuru türü yeni bir örneğini oluşturmaz bir doğrulama hatası olmasıdır. Bu sorunu çözmek için değişmez değer ifadesi oluşturur ve başvuru türü yeni bir örneğini döndüren bir ile değiştirin.  
  
```csharp  
new Assign  
{  
    To = new OutArgument<List<string>>(items),  
    Value = new InArgument<List<string>>(new VisualBasicValue<List<string>>("New List(Of String)"))  
},  
```  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]ifadeler, bkz: [ifadeleri](../../../docs/framework/windows-workflow-foundation/expressions.md).  
  
#### <a name="invoking-methods-on-objects-using-expressions-and-the-invokemethod-activity"></a>İfadeler ve InvokeMethod etkinliğini kullanarak nesneleri yöntemleri çağırma  
 <xref:System.Activities.Expressions.InvokeMethod%601> Etkinlik, statik çağırma ve .NET Framework sınıfları, yöntemleri örneği için kullanılabilir. Bu konuda önceki örnekte rastgele bir sayı kullanılarak oluşturulan <xref:System.Random> sınıfı.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#51](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#51)]  
  
 <xref:System.Activities.Expressions.InvokeMethod%601> Etkinlik da kullanılabilirdi çağırmak için <xref:System.Random.Next%2A> yöntemi <xref:System.Random> sınıfı.  
  
```csharp  
new InvokeMethod<int>  
{  
    TargetObject = new InArgument<Random>(new VisualBasicValue<Random>("New Random()")),  
    MethodName = "Next",  
    Parameters =   
    {  
        new InArgument<int>(1),  
        new InArgument<int>(101)  
    },  
    Result = n  
}  
```  
  
 Bu yana <xref:System.Random.Next%2A> örneği bir statik yöntem değildir <xref:System.Random> sınıfı için sağlanmaktadır <xref:System.Activities.Expressions.InvokeMethod%601.TargetObject%2A> özelliği. Bu örnekte, bir Visual Basic ifade kullanılarak yeni bir örneği oluşturulur, ancak bunu de daha önce oluşturulmuş ve bir iş akışı değişkeninde depolanan. Bu örnekte, kullanmayı daha kolay olacaktır <xref:System.Activities.Statements.Assign%601> yerine etkinlik <xref:System.Activities.Expressions.InvokeMethod%601> etkinlik. Yöntem çağrısının sonuçta ya da başlatılırsa <xref:System.Activities.Statements.Assign%601> veya <xref:System.Activities.Expressions.InvokeMethod%601> etkinlikleri uzun çalışan, <xref:System.Activities.Expressions.InvokeMethod%601> içerdiğinden bir avantajı vardır, bir <xref:System.Activities.Expressions.InvokeMethod%601.RunAsynchronously%2A> özelliği. Bu özellik ayarlandığında `true`, çağrılan yöntem iş akışı göre zaman uyumsuz olarak çalışır. Paralel olarak diğer etkinlikler varsa yöntemi zaman uyumsuz olarak yürütülürken bunlar engellenmez. Ayrıca, çağrılacak yöntemin dönüş değeri, ardından yoksa <xref:System.Activities.Expressions.InvokeMethod%601> yöntemini çağırmak için uygun bir yoludur.  
  
## <a name="arguments-and-dynamic-activities"></a>Bağımsız değişkenler ve dinamik etkinlikleri  
 Bir iş akışı tanımı kod içinde bir etkinlik ağacına etkinlikleri birleştirme ve tüm özellikleri ve bağımsız değişkenler yapılandırma oluşturulur. Var olan bağımsız değişkenler bağlanabilir ancak yeni bağımsız değişkenleri etkinlikler için eklenemiyor. Bu kök etkinlik geçirilen iş akışı değişkenleri içerir. Yeni bir CLR türü özellikleri olarak belirtilen kesinlik temelli kodda iş akışı değişkenleri ve XAML'de bunlar kullanarak bildirilir `x:Class` ve `x:Member`. Bağımsız değişkenler, bir iş akışı tanımı bellek içi nesnelerin ağaç oluşturulduğunda yeni bir CLR türü olduğundan eklenemez. Bağımsız değişkenler ancak, eklenebilir bir <xref:System.Activities.DynamicActivity>. Bu örnekte, bir <xref:System.Activities.DynamicActivity%601> bu alır iki tamsayı bağımsız değişkeni oluşturulur, birlikte ekler ve sonucu döndürür. A <xref:System.Activities.DynamicActivityProperty> her bağımsız değişkeni için oluşturulan ve işleminin sonucu atandığı <xref:System.Activities.Activity%601.Result%2A> bağımsız değişkeni <xref:System.Activities.DynamicActivity%601>.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#55](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#55)]  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]dinamik etkinlikleri bkz [çalışma zamanında bir etkinlik oluşturma](../../../docs/framework/windows-workflow-foundation/creating-an-activity-at-runtime-with-dynamicactivity.md).  
  
## <a name="compiled-activities"></a>Derlenmiş etkinlikleri  
 Dinamik etkinlikleri kod kullanarak bağımsız değişkenleri içeren bir etkinlik tanımlamak için bir yol sunar, ancak etkinlikler ayrıca kod oluşturulabilir ve türleriyle derlenmiş. Öğesinden türetilen basit etkinlikleri oluşturulabilir <xref:System.Activities.CodeActivity>ve türetilen zaman uyumsuz etkinlikleri <xref:System.Activities.AsyncCodeActivity>. Bu etkinlikler dönüş değerleri ve kesinlik temelli kod kullanarak kendi mantığını tanımlamak bağımsız değişkenler, olabilir. Bu tür etkinlikler oluşturma örnekler için bkz: [CodeActivity temel sınıf](../../../docs/framework/windows-workflow-foundation/workflow-activity-authoring-using-the-codeactivity-class.md) ve [oluşturma zaman uyumsuz etkinlikleri](../../../docs/framework/windows-workflow-foundation/creating-asynchronous-activities-in-wf.md).  
  
 Öğesinden türetilen etkinlikleri <xref:System.Activities.NativeActivity> kesinlik temelli kod kullanarak kendi mantığı tanımlayabilir ve mantığını tanımlayan alt etkinlikler de içerebilir. Ayrıca tam yer işaretleri oluşturma gibi çalışma zamanı özelliklerine erişimi. Oluşturma örnekler bir <xref:System.Activities.NativeActivity>-etkinlik, temel bkz [NativeActivity temel sınıf](../../../docs/framework/windows-workflow-foundation/nativeactivity-base-class.md), [nasıl yapılır: bir etkinlik oluşturmak](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)ve [özel kullanarak yerel etkinliğiniBileşik](../../../docs/framework/windows-workflow-foundation/samples/custom-composite-using-native-activity.md)örnek.  
  
 Öğesinden türetilen etkinlikleri <xref:System.Activities.Activity> yalnızca alt etkinlikleri ile bunların mantığı tanımlayın. Bu etkinlikler iş akışı Tasarımcısı kullanarak genellikle oluşturulur, ancak kod kullanılarak da tanımlanabilir. Aşağıdaki örnekte, bir `Square` etkinlik tanımlanmış türeyen `Activity<int>`. `Square` Etkinlik sahip tek bir <xref:System.Activities.InArgument%601> adlı `Value`ve belirterek, mantığını tanımlayan bir <xref:System.Activities.Statements.Sequence> kullanarak etkinliğini <xref:System.Activities.Activity.Implementation%2A> özelliği. <xref:System.Activities.Statements.Sequence> Etkinlik içeren bir <xref:System.Activities.Statements.WriteLine> etkinliği ve bir <xref:System.Activities.Statements.Assign%601> etkinlik. Birlikte, bu üç etkinlikler mantığını uygulamak `Square` etkinlik.  
  
```csharp  
class Square : Activity<int>  
{  
    [RequiredArgument]  
    public InArgument<int> Value { get; set; }  
  
    public Square()  
    {  
        this.Implementation = () => new Sequence  
        {  
            Activities =  
            {  
                new WriteLine  
                {  
                    Text = new InArgument<string>((env) => "Squaring the value: " + this.Value.Get(env))  
                },  
                new Assign<int>  
                {  
                    To = new OutArgument<int>((env) => this.Result.Get(env)),  
                    Value = new InArgument<int>((env) => this.Value.Get(env) * this.Value.Get(env))  
                }  
            }  
        };  
    }  
}  
```  
  
 Aşağıdaki örnekte, bir tek oluşan bir iş akışı tanımı `Square` etkinliğini kullanarak çağrıldığında <xref:System.Activities.WorkflowInvoker>.  
  
```csharp  
Dictionary<string, object> inputs = new Dictionary<string, object> {{ "Value", 5}};  
int result = WorkflowInvoker.Invoke(new Square(), inputs);  
Console.WriteLine("Result: {0}", result);  
```  
  
 İş akışı çağrıldığında, aşağıdaki çıktıyı konsola görüntülenir:  
  
 **Değer karesini: 5**  
**Sonuç: 25**
