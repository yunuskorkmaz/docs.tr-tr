---
title: İş akışları, etkinlikler ve ifadeler kesin kod kullanarak geliştirme
ms.date: 03/30/2017
ms.assetid: cefc9cfc-2882-4eb9-8c94-7a6da957f2b2
ms.openlocfilehash: a0566e01d5786c955562ef97d6d083d886278293
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45518054"
---
# <a name="authoring-workflows-activities-and-expressions-using-imperative-code"></a>İş akışları, etkinlikler ve ifadeler kesin kod kullanarak geliştirme
Bir iş akışı tanımı, yapılandırılan etkinlik nesneleri ağacıdır. Bu ağaç etkinliklerin elle düzenlemeye XAML veya XAML üretmek için iş akışı Tasarımcısı kullanarak da dahil olmak üzere birçok şekilde tanımlanabilir. XAML, kullanımı, ancak bir gereksinim değildir. İş akışı tanımları da bir program aracılığıyla oluşturulabilir. Bu konuda, kod kullanarak iş akışı tanımları, etkinlikler ve ifadeler oluşturmaya genel bir bakış sağlar. Kod kullanarak XAML iş akışları ile çalışma örnekleri için bkz. [seri hale getirme iş akışları ve etkinlikler XAML gelen ve giden](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md).  
  
## <a name="creating-workflow-definitions"></a>İş akışı tanımları oluşturma  
 Bir iş akışı tanımı, bir etkinlik türünün bir örneği örnekleme ve etkinlik nesnesinin özelliklerini yapılandırma oluşturulabilir. Çocuk etkinliklerinin içermeyen etkinlikler için bu birkaç satır kod kullanarak gerçekleştirilebilir.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#47](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#47)]  
  
> [!NOTE]
>  Bu konuda kullanım örnekleri <xref:System.Activities.WorkflowInvoker> örnek iş akışlarını çalıştırmak için. İş akışları, bağımsız değişkenleri geçirme ve mevcut olan farklı barındırma seçenekleri çağırma hakkında daha fazla bilgi için bkz. [kullanarak Workflowınvoker ve WorkflowApplication](../../../docs/framework/windows-workflow-foundation/using-workflowinvoker-and-workflowapplication.md).  
  
 Bu örnekte, bir tek oluşan bir iş akışı <xref:System.Activities.Statements.WriteLine> etkinlik oluşturulur. <xref:System.Activities.Statements.WriteLine> Etkinliğin <xref:System.Activities.Statements.WriteLine.Text%2A> bağımsız değişkeni ayarlanır ve bu iş akışı çağrılır. Oluşturma yöntemi, çocuk etkinliklerinin bir etkinlik içeriyorsa, benzer. Aşağıdaki örnekte bir <xref:System.Activities.Statements.Sequence> iki etkinlik <xref:System.Activities.Statements.WriteLine> etkinlikler.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#48](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#48)]  
  
### <a name="using-object-initializers"></a>Nesne Başlatıcı kullanma  
 Bu konudaki örnekleri nesne başlatma söz dizimi kullanın. Nesne başlatma söz dizimi etkinlikleri arasındaki ilişkiyi gösterir ve iş akışındaki etkinliklerin hiyerarşik bir görünümü sağlar çünkü kod içinde iş akışı tanımları oluşturma için kullanışlı bir yol olabilir. Nesne başlatma söz dizimi programlı olarak iş akışları oluşturduğunuzda kullanılacak gereksinimi yoktur. Aşağıdaki örnek önceki örneğe işlevsel olarak eşdeğerdir.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#49](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#49)]  
  
 Nesne başlatıcıları hakkında daha fazla bilgi için bkz: [nasıl yapılır: nesneleri başlatma (C# programlama Kılavuzu) Yapılandırıcının olmadan](https://go.microsoft.com/fwlink/?LinkId=161015) ve [nasıl yapılır: nesne Başlatıcı kullanarak nesne bildirme](https://go.microsoft.com/fwlink/?LinkId=161016).  
  
### <a name="working-with-variables-literal-values-and-expressions"></a>Değişkenler, değişmez değerler ve ifadeleri ile çalışma  
 Kod kullanarak bir iş akışı tanımı oluştururken, hangi kod oluşturma iş akışı tanımının bir parçası olarak çalışır ve bu iş akışı örneği yürütme işleminin bir parçası olarak hangi kodu yürütür unutmayın. Örneğin, aşağıdaki iş akışı, rastgele bir sayı oluşturur ve konsola yazma için tasarlanmıştır.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#50](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#50)]  
  
 Bu iş akışı tanımı kod olduğunda yürütülür, çağrı `Random.Next` yapılır ve sonuç iş akışı tanımında değişmez değer olarak depolanır. Bu iş akışı birçok örneği çağrılabilir ve tümü aynı numarasını görüntüler. İş akışı yürütme sırasında oluşan bir ifade başka bir deyişle kullanılmalıdır rastgele sayı üretimi için iş akışı her çalıştığında değerlendirilir. Aşağıdaki örnekte, bir Visual Basic ifade ile kullanılan bir <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#51](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#51)]  
  
 Önceki örnekte ifade kullanarak da uygulanabilir bir <xref:Microsoft.CSharp.Activities.CSharpValue%601> ve bir C# ifadesi.  
  
```csharp  
new Assign<int>  
{  
    To = n,  
    Value = new CSharpValue<int>("new Random().Next(1, 101)")  
}  
```  
  
 C# ifadelerini bunları içeren iş akışı çağrılmadan önce derlenmesi gerekir. C# ifadelerini derlenmemiş, bir <xref:System.NotSupportedException> aşağıdakine benzer bir ileti ile iş akışı çalıştırıldığında oluşturulur: `Expression Activity type 'CSharpValue`1' derlemesi çalıştırmak için gerekiyor.  İş akışı derlendiğinden emin olun.' Visual Studio'da C# oluşturulan iş akışları içeren çoğu senaryoda ifadeleri otomatik olarak derlenir, ancak kodu iş akışları gibi bazı senaryolarda C# ifadelerini el ile derlenmiş olmalıdır. C# ifadelerini derlemeye ilişkin bir örnek için bkz. [kullanarak C# ifadeleri iş akışlarında kod](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) bölümünü [C# ifadelerini](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md) konu.  
  
 A <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> bir ifadede bir r olarak kullanılan Visual Basic sözdiziminde ifadeyi temsil eden ve <xref:Microsoft.CSharp.Activities.CSharpValue%601> bir ifadede bir ifadede bir r olarak kullanılabilen C# sözdizimi temsil eder. Bu ifadeler içeren etkinlik yürütülen her zaman değerlendirilir. İfadenin sonucu iş akışı değişkenine atanan `n`, ve bu sonuçları, iş akışındaki sonraki etkinliği tarafından kullanılır. İş akışı değişkeninin değerini erişmeye `n` zamanında <xref:System.Activities.ActivityContext> gereklidir. Bu, aşağıdaki lambda ifadesi kullanılarak erişilebilir.  
  
> [!NOTE]
>  Hem bu kod örnekleri olduğunu not kullandığınız C# programlama dili olarak, ancak kullanan tek bir <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> ve kullanan tek bir <xref:Microsoft.CSharp.Activities.CSharpValue%601>. <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> ve <xref:Microsoft.CSharp.Activities.CSharpValue%601> Visual Basic ve C# projelerinde kullanılabilir. Varsayılan olarak, iş akışı Tasarımcısı'nda oluşturulan ifadeler barındırma projenin diliyle eşleşiyor. İş akışlarının kodda oluştururken istediğiniz dil için iş akışı yazarın takdirinizdedir.  
  
 Bu örneklerde, ifadenin sonucu iş akışı değişkenine atanır `n`, ve bu sonuçları, iş akışındaki sonraki etkinliği tarafından kullanılır. İş akışı değişkeninin değerini erişmeye `n` zamanında <xref:System.Activities.ActivityContext> gereklidir. Bu, aşağıdaki lambda ifadesi kullanılarak erişilebilir.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#52](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#52)]  
  
 Lambda ifadeleri hakkında daha fazla bilgi için bkz. [Lambda ifadeleri (C# programlama Kılavuzu)](https://go.microsoft.com/fwlink/?LinkID=152436) veya [Lambda ifadeleri (Visual Basic)](https://go.microsoft.com/fwlink/?LinkID=152437).  
  
 Lambda ifadeleri, XAML biçimine seri hale getirilebilir değildir. Lambda ifadeleri bir iş akışıyla seri hale getirme denemesi yapılırsa bir <xref:System.Activities.Expressions.LambdaSerializationException> şu ileti ile oluşturulur: "Bu iş akışı kodda belirtilen lambda ifadeleri içerir. Bu ifadeler, XAML serileştirilebilir değil. Akışınızı XAML serileştirilebilir yapmak için VisualBasicValue/VisualBasicReference veya ExpressionServices.Convert(lambda) kullanın. Bu, lambda ifadeleri ifade etkinliklerine dönüştürür." Bu ifade XAML ile uyumlu hale getirmek için kullanın <xref:System.Activities.Expressions.ExpressionServices> ve <xref:System.Activities.Expressions.ExpressionServices.Convert%2A>, aşağıdaki örnekte gösterildiği gibi.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#53](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#53)]  
  
 A <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> de kullanılabilir. Hiçbir lambda ifadesi bir Visual Basic ifadesinin kullanırken gerekli olduğunu unutmayın.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#54](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#54)]  
  
 Çalışma zamanında, Visual Basic deyimleri LINQ ifadelere derlenir. Önceki örneklerin her ikisi de seri hale getirilmiş XAML görüntülenmesine ve iş akışı Tasarımcısı'nda düzenlenebilir yöneliktir, ancak XAML, seri hale getirilebilir <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> , ifadeler için. Serileştirilmiş kullanan iş akışları `ExpressionServices.Convert` tasarımcıda açık, ancak ifadenin değerini boş olarak görüntülenir. XAML iş akışlarına serileştirmek hakkında daha fazla bilgi için bkz. [seri hale getirme iş akışları ve etkinlikler XAML gelen ve giden](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md).  
  
#### <a name="literal-expressions-and-reference-types"></a>Değişmez ifadeleri ve başvuru türleri  
 Değişmez ifadeleri iş akışlarında tarafından temsil edilir <xref:System.Activities.Expressions.Literal%601> etkinlik. Aşağıdaki <xref:System.Activities.Statements.WriteLine> etkinlikleri işlevsel olarak eşdeğerdir.  
  
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
  
 Hazır ifadeyi herhangi bir başvuru türü ile başlatmak için geçersiz <xref:System.String>. Aşağıdaki örnekte, bir <xref:System.Activities.Statements.Assign> etkinliğin <xref:System.Activities.Statements.Assign.Value%2A> özelliğinin kullanarak bir değişmez değer ifadesinin başlatıldığı bir `List<string>`.  
  
```csharp  
new Assign  
{  
    To = new OutArgument<List<string>>(items),  
    Value = new InArgument<List<string>>(new List<string>())  
},  
```  
  
 Bu etkinliğini içeren iş akışı doğrulandığında, aşağıdaki doğrulama hatası döndürülür: "değişmez değeri yalnızca değer türleri ve destekler System.String sabit türü. Türü System.Collections.Generic.List'1[System.String] bir değişmez değer olarak kullanılamaz." İş akışı çağrılırsa bir <xref:System.Activities.InvalidWorkflowException> atılır doğrulama hatası metnini içeren. Değişmez değer ifadesinin bir başvuru türü ile oluşturma başvuru türü her iş akışı örneği için yeni bir örneğini oluşturmaz bir doğrulama hatası olmasıdır. Bu sorunu çözmek için oluşturur ve yeni bir başvuru türünün örneğini döndüren bir değişmez değer ifadesinin değiştirin.  
  
```csharp  
new Assign  
{  
    To = new OutArgument<List<string>>(items),  
    Value = new InArgument<List<string>>(new VisualBasicValue<List<string>>("New List(Of String)"))  
},  
```  
  
 İfadeler hakkında daha fazla bilgi için bkz. [ifadeleri](../../../docs/framework/windows-workflow-foundation/expressions.md).  
  
#### <a name="invoking-methods-on-objects-using-expressions-and-the-invokemethod-activity"></a>Nesne ifadeleri ve InvokeMethod etkinliği kullanma yöntemleri çağırma  
 <xref:System.Activities.Expressions.InvokeMethod%601> Etkinlik, statik çağırmak ve .NET Framework sınıfların yöntemlerinde örneği için kullanılabilir. Bu konuda bir önceki örnekte, rastgele bir sayı kullanılarak oluşturulan <xref:System.Random> sınıfı.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#51](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#51)]  
  
 <xref:System.Activities.Expressions.InvokeMethod%601> Etkinliği de kullanılabilirdi çağrılacak <xref:System.Random.Next%2A> yöntemi <xref:System.Random> sınıfı.  
  
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
  
 Bu yana <xref:System.Random.Next%2A> statik bir yöntemi, bir örneği değil <xref:System.Random> sınıfı için sağlanmaktadır <xref:System.Activities.Expressions.InvokeMethod%601.TargetObject%2A> özelliği. Bu örnekte, bir Visual Basic ifadesinin kullanarak yeni bir örneği oluşturulur, ancak bunu ayrıca daha önce oluşturulmuş ve bir iş akışı değişkeninde depolanan. Bu örnekte, kullanmayı daha kolay olacaktır <xref:System.Activities.Statements.Assign%601> yerine etkinlik <xref:System.Activities.Expressions.InvokeMethod%601> etkinlik. Yöntem çağrısının ya da sonunda çağrılır, <xref:System.Activities.Statements.Assign%601> veya <xref:System.Activities.Expressions.InvokeMethod%601> etkinlikler, uzun çalışan, <xref:System.Activities.Expressions.InvokeMethod%601> , sahip olduğu bir avantajı vardır bir <xref:System.Activities.Expressions.InvokeMethod%601.RunAsynchronously%2A> özelliği. Bu özelliği ayarlandığında `true`, çağrılan yöntemi bir iş akışı ile ilgili zaman uyumsuz olarak çalışır. Diğer etkinlikler paralel olarak ise, yöntem zaman uyumsuz olarak yürütülürken bunlar engellenmez. Ayrıca, çağrılacak yöntemin dönüş değeri, ardından yoksa <xref:System.Activities.Expressions.InvokeMethod%601> yöntemini çağırmak için en uygun yolu.  
  
## <a name="arguments-and-dynamic-activities"></a>Bağımsız değişkenler ve dinamik etkinlikleri  
 Bir iş akışı tanımı kod içinde bir etkinlik ağacına etkinlikleri derleyerek ve tüm özellikleri ve bağımsız değişkenler yapılandırma oluşturulur. Mevcut bağımsız değişkenleri bağlanabilir ancak yeni bağımsız değişkenler için etkinlikleri eklenemez. Bu kök etkinlik için geçirilen iş akışı bağımsız değişkenler içerir. Kesinlik temelli kod içinde yeni bir CLR türündeki özellikleri olarak iş akışı bağımsız değişkenleri belirtilir ve XAML içinde kullanılarak bildirilirler `x:Class` ve `x:Member`. Bağımsız değişkenleri bir iş akışı tanımı bellekteki nesnelerin ağaç olarak oluşturulduğunda CLR türünün belirtilmemesi yeni olduğundan eklenemez. Bununla birlikte, bağımsız değişkenleri eklenebilen bir <xref:System.Activities.DynamicActivity>. Bu örnekte, bir <xref:System.Activities.DynamicActivity%601> alır, iki tamsayı bağımsız oluşturulur, bunları bir araya getirir ve sonucu döndürür. A <xref:System.Activities.DynamicActivityProperty> her bağımsız değişkeni için oluşturulan ve işlemin sonucu atandığı <xref:System.Activities.Activity%601.Result%2A> bağımsız değişkeni <xref:System.Activities.DynamicActivity%601>.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#55](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#55)]  
  
 Dinamik etkinlikleri hakkında daha fazla bilgi için bkz: [çalışma zamanında bir etkinlik oluşturma](../../../docs/framework/windows-workflow-foundation/creating-an-activity-at-runtime-with-dynamicactivity.md).  
  
## <a name="compiled-activities"></a>Derlenmiş etkinlikleri  
 Dinamik etkinlikleri kod kullanarak bağımsız değişkenleri içeren bir etkinlik tanımlamak için bir yoludur, ancak etkinlikleri de kodda oluşturulabilir ve tür olarak derlenir. Öğesinden türetilen basit etkinlikleri oluşturulabilir <xref:System.Activities.CodeActivity>ve türetilen zaman uyumsuz etkinlikler <xref:System.Activities.AsyncCodeActivity>. Bu etkinlik bağımsız değişkenleri, dönüş değerleri ve kesin kod kullanarak kendi mantığını tanımlamak olabilir. Bu tür etkinlikler oluşturmayı örnekler için bkz. [CodeActivity temel sınıfı](../../../docs/framework/windows-workflow-foundation/workflow-activity-authoring-using-the-codeactivity-class.md) ve [zaman uyumsuz etkinlikler oluşturma](../../../docs/framework/windows-workflow-foundation/creating-asynchronous-activities-in-wf.md).  
  
 Öğesinden türetilen etkinlikleri <xref:System.Activities.NativeActivity> mantığını kesin kod kullanarak tanımlayabilirsiniz ve mantığı tanımlayan alt etkinlikleri de içerebilir. Ayrıca yer işaretlerini oluşturma gibi çalışma zamanı özelliklerine tam erişim sahiptirler. Oluşturmaya yönelik örnek için bir <xref:System.Activities.NativeActivity>-etkinlik, temel bkz [NativeActivity temel sınıfı](../../../docs/framework/windows-workflow-foundation/nativeactivity-base-class.md), [nasıl yapılır: bir etkinliği oluşturma](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)ve [Nativeetkinliğikullananözelbileşik](../../../docs/framework/windows-workflow-foundation/samples/custom-composite-using-native-activity.md)örnek.  
  
 Öğesinden türetilen etkinlikleri <xref:System.Activities.Activity> yalnızca alt etkinlikleri kullanarak bunların mantığına tanımlayın. Bu etkinlikler, genellikle iş akışı Tasarımcısı kullanarak oluşturulur, ancak kod kullanılarak da tanımlanabilir. Aşağıdaki örnekte, bir `Square` etkinlik öğesinden türetilen tanımlanır `Activity<int>`. `Square` Etkinliğinde, tek bir <xref:System.Activities.InArgument%601> adlı `Value`ve belirterek mantığını tanımlayan bir <xref:System.Activities.Statements.Sequence> etkinliğini kullanarak <xref:System.Activities.Activity.Implementation%2A> özelliği. <xref:System.Activities.Statements.Sequence> Etkinliği içeren bir <xref:System.Activities.Statements.WriteLine> etkinliği ve bir <xref:System.Activities.Statements.Assign%601> etkinlik. Birlikte, bu üç etkinlikleri mantığını uygulayan `Square` etkinlik.  
  
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
  
 Aşağıdaki örnekte, bir tek oluşan bir iş akışı tanımı `Square` etkinliği kullanarak çağrıldığında <xref:System.Activities.WorkflowInvoker>.  
  
```csharp  
Dictionary<string, object> inputs = new Dictionary<string, object> {{ "Value", 5}};  
int result = WorkflowInvoker.Invoke(new Square(), inputs);  
Console.WriteLine("Result: {0}", result);  
```  
  
 İş akışı çağrıldığında, aşağıdaki çıktıyı konsola görüntülenir:  
  
 **Değer karesini: 5**  
**Sonuç: 25**
