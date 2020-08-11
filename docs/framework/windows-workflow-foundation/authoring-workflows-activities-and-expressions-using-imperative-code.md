---
title: Kesin Kod Kullanarak İş Akışları, Etkinlikler ve İfadeler Yazma
description: Bir Workflow Foundation iş akışı tanımı, yapılandırılmış etkinlik nesnelerinin bir ağacıdır. İş akışı tanımları, etkinlikler ve ifadeler oluşturmak için kodu kullanın.
ms.date: 03/30/2017
ms.assetid: cefc9cfc-2882-4eb9-8c94-7a6da957f2b2
ms.openlocfilehash: d169049c47c154858a2e653b5f286fa6b66ba44d
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063802"
---
# <a name="authoring-workflows-activities-and-expressions-using-imperative-code"></a>Kesin Kod Kullanarak İş Akışları, Etkinlikler ve İfadeler Yazma
İş akışı tanımı, yapılandırılmış etkinlik nesnelerinin bir ağacıdır. Bu etkinlik ağacı, el ile düzenlenen XAML veya XAML oluşturmak için İş Akışı Tasarımcısı kullanılarak dahil olmak üzere birçok şekilde tanımlanabilir. Ancak XAML kullanımı bir gereklilik değildir. Ayrıca, iş akışı tanımları programlama yoluyla da oluşturulabilir. Bu konu, kod kullanarak iş akışı tanımları, etkinlikler ve deyimler oluşturmaya genel bir bakış sağlar. Kodu kullanarak XAML iş akışlarıyla çalışma örnekleri için bkz. [xaml 'de ve xaml 'de Iş akışlarını ve etkinlikleri seri hale getirme](serializing-workflows-and-activities-to-and-from-xaml.md).  
  
## <a name="creating-workflow-definitions"></a>Iş akışı tanımları oluşturma  
 Etkinlik türünün bir örneğini oluşturarak ve etkinlik nesnesinin özellikleri yapılandırılarak bir iş akışı tanımı oluşturulabilir. Alt etkinlik içermeyen etkinlikler için, bu, birkaç satır kod kullanılarak gerçekleştirilebilir.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#47](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#47)]  
  
> [!NOTE]
> Bu konudaki örnekler <xref:System.Activities.WorkflowInvoker> örnek iş akışlarını çalıştırmak için kullanır. İş akışlarını çağırma, bağımsız değişkenleri geçirme ve kullanılabilir farklı barındırma seçeneklerini kullanma hakkında daha fazla bilgi için bkz. [Workflowwınvoker ve WorkflowApplication kullanma](using-workflowinvoker-and-workflowapplication.md).  
  
 Bu örnekte, tek bir etkinlikten oluşan bir iş akışı <xref:System.Activities.Statements.WriteLine> oluşturulur. <xref:System.Activities.Statements.WriteLine>Etkinliğin <xref:System.Activities.Statements.WriteLine.Text%2A> bağımsız değişkeni ayarlanır ve iş akışı çağrılır. Bir etkinlik alt etkinlikler içeriyorsa, oluşturma yöntemi benzerdir. Aşağıdaki örnek <xref:System.Activities.Statements.Sequence> iki etkinlik içeren bir etkinlik kullanır <xref:System.Activities.Statements.WriteLine> .  
  
 [!code-csharp[CFX_WorkflowApplicationExample#48](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#48)]  
  
### <a name="using-object-initializers"></a>Nesne başlatıcılarının kullanımı  
 Bu konudaki örnekler, nesne başlatma sözdizimini kullanır. Nesne başlatma sözdizimi, iş akışındaki etkinliklerin hiyerarşik bir görünümünü sağladığından koddaki iş akışı tanımlarını oluşturmak için kullanışlı bir yol olabilir ve etkinlikler arasındaki ilişkiyi gösterir. Program aracılığıyla iş akışları oluştururken nesne başlatma söz dizimini kullanma gereksinimi yoktur. Aşağıdaki örnek, önceki örneğe işlevsel olarak eşdeğerdir.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#49](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#49)]  
  
 Nesne başlatıcıları hakkında daha fazla bilgi için bkz. [nasıl yapılır: Oluşturucu çağırmadan nesneleri başlatma (C# Programlama Kılavuzu)](../../csharp/programming-guide/classes-and-structs/how-to-initialize-objects-by-using-an-object-initializer.md) ve [nasıl yapılır: nesne Başlatıcısı kullanarak nesne bildirme](../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md).  
  
### <a name="working-with-variables-literal-values-and-expressions"></a>Değişkenler, değişmez değerler ve Ifadelerle çalışma  
 Kodu kullanarak bir iş akışı tanımı oluştururken, iş akışı tanımı oluşturmanın bir parçası olarak hangi kodun yürütüldüğünü ve bu iş akışının bir örneğini yürütmenin bir parçası olarak hangi kodun yürütüldüğünü unutmayın. Örneğin, aşağıdaki iş akışı rastgele bir sayı oluşturmak ve konsola yazmak için tasarlanmıştır.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#50](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#50)]  
  
 Bu iş akışı Tanım kodu yürütüldüğünde, çağrısı `Random.Next` yapılır ve sonuç iş akışı tanımında değişmez değer olarak depolanır. Bu iş akışının birçok örneği çağrılabilir ve hepsi aynı numarayı görüntüler. İş akışı yürütmesi sırasında rastgele sayının oluşturulması durumunda, iş akışı her çalıştığında değerlendirilen bir ifade kullanılmalıdır. Aşağıdaki örnekte, bir Visual Basic ifadesi ile kullanılır <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> .  
  
 [!code-csharp[CFX_WorkflowApplicationExample#51](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#51)]  
  
 Önceki örnekteki ifade bir ve bir C# ifadesi kullanılarak da uygulanabilir <xref:Microsoft.CSharp.Activities.CSharpValue%601> .  
  
```csharp  
new Assign<int>  
{  
    To = n,  
    Value = new CSharpValue<int>("new Random().Next(1, 101)")  
}  
```  
  
 C# ifadeleri, kendisini içeren iş akışı çağrılmadan önce derlenmelidir. C# ifadeleri derlenmeyecekse, <xref:System.NotSupportedException> iş akışı şuna benzer bir iletiyle çağrıldığında bir oluşturulur: ``Expression Activity type 'CSharpValue`1' requires compilation in order to run.  Please ensure that the workflow has been compiled.`` Visual Studio 'da oluşturulan iş akışlarını içeren çoğu senaryoda c# ifadeleri otomatik olarak derlenir, ancak kod iş akışları gibi bazı senaryolarda c# ifadeleri el ile derlenmelidir. C# ifadelerinin nasıl derlenmeye ilişkin bir örnek için [c# ifadeleri](csharp-expressions.md) konusunun [kod Iş akışlarında c# ifadelerini kullanma](csharp-expressions.md#CodeWorkflows) bölümüne bakın.  
  
 Bir ifadede <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> r değeri olarak kullanılabilen Visual Basic sözdiziminde bir ifadeyi temsil eder ve bir ifadede <xref:Microsoft.CSharp.Activities.CSharpValue%601> r değeri olarak kullanılabilecek C# sözdiziminde bir ifadeyi temsil eder. Bu ifadeler, kapsayan etkinliğin her yürütüldüğü her seferinde değerlendirilir. İfadenin sonucu iş akışı değişkenine atanır `n` ve bu sonuçlar iş akışındaki sonraki etkinlik tarafından kullanılır. Çalışma zamanında iş akışı değişkeninin değerine erişmek için `n` <xref:System.Activities.ActivityContext> gereklidir. Bu, aşağıdaki lambda ifadesi kullanılarak erişilebilir.  
  
> [!NOTE]
> Bu kodların her ikisi de programlama dili olarak C# kullanıyor, ancak biri bir kullanır <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> ve bir kullanır <xref:Microsoft.CSharp.Activities.CSharpValue%601> . <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>ve <xref:Microsoft.CSharp.Activities.CSharpValue%601> hem Visual Basic hem de C# projelerinde kullanılabilir. Varsayılan olarak, iş akışı tasarımcısında oluşturulan ifadeler barındırma projesinin diliyle eşleşir. Kodda iş akışları oluştururken, istenen dil iş akışı yazarının kararına göre belirlenir.  
  
 Bu örneklerde, ifadenin sonucu iş akışı değişkenine atanır `n` ve bu sonuçlar iş akışındaki sonraki etkinlik tarafından kullanılır. Çalışma zamanında iş akışı değişkeninin değerine erişmek için `n` <xref:System.Activities.ActivityContext> gereklidir. Bu, aşağıdaki lambda ifadesi kullanılarak erişilebilir.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#52](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#52)]  
  
 Lambda ifadeleri hakkında daha fazla bilgi için bkz. [lambda ifadeleri (C# Başvurusu)](../../csharp/language-reference/operators/lambda-expressions.md) veya [lambda ifadeleri (Visual Basic)](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 Lambda ifadeleri XAML biçimine serileştirilebilir değildir. Lambda ifadeleriyle bir iş akışını serileştirme girişimi yapılırsa, <xref:System.Activities.Expressions.LambdaSerializationException> Şu iletiyle bir oluşturulur: "Bu iş akışı kodda belirtilen Lambda ifadelerini içerir. Bu ifadeler XAML serileştirilebilir değildir. İş akışınızı XAML-serileştirilebilir yapmak için VisualBasicValue/VisualBasicReference veya ExpressionServices. Convert (lambda) kullanın. Bu işlem lambda ifadelerinizi ifade etkinliklerine dönüştürür. " Bu ifadeyi XAML ile uyumlu hale getirmek için, <xref:System.Activities.Expressions.ExpressionServices> <xref:System.Activities.Expressions.ExpressionServices.Convert%2A> Aşağıdaki örnekte gösterildiği gibi ve kullanın.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#53](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#53)]  
  
 <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>Ayrıca kullanılabilir. Visual Basic ifadesi kullanılırken hiçbir lambda ifadesinin gerekli olmadığını unutmayın.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#54](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#54)]  
  
 Çalışma zamanında, Visual Basic ifadeleri LINQ ifadelerine derlenir. Önceki örneklerin her ikisi de XAML 'ye serileştirilebilir, ancak serileştirilmiş XAML iş akışı tasarımcısında görüntülenmek ve düzenlenilmesi amaçlanıyorsa <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> deyimleriniz için kullanın. Kullanan serileştirilmiş iş akışları `ExpressionServices.Convert` tasarımcıda açılabilir, ancak ifadenin değeri boş olur. XAML 'de iş akışlarını serileştirme hakkında daha fazla bilgi için bkz. [xaml 'de ve xaml 'de Iş akışlarını ve etkinlikleri serileştirme](serializing-workflows-and-activities-to-and-from-xaml.md).  
  
#### <a name="literal-expressions-and-reference-types"></a>Değişmez değer Ifadeleri ve başvuru türleri  
 Değişmez değerler, etkinliğin iş akışlarında temsil edilir <xref:System.Activities.Expressions.Literal%601> . Aşağıdaki <xref:System.Activities.Statements.WriteLine> Etkinlikler işlevsel olarak eşdeğerdir.  
  
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
  
 Dışında herhangi bir başvuru türüyle değişmez bir ifade başlatmak geçersizdir <xref:System.String> . Aşağıdaki örnekte, <xref:System.Activities.Statements.Assign> <xref:System.Activities.Statements.Assign.Value%2A> bir etkinliğin özelliği, kullanılarak değişmez değer ifadesiyle başlatılır `List<string>` .  
  
```csharp  
new Assign  
{  
    To = new OutArgument<List<string>>(items),  
    Value = new InArgument<List<string>>(new List<string>())  
},  
```  
  
 Bu etkinliği içeren iş akışı doğrulanırsa, aşağıdaki doğrulama hatası döndürülür: "değişmez değer yalnızca değer türlerini ve sabit tür System. String ' i destekler. System. Collections. Generic. List ' 1 [System. String] türü bir sabit değer olarak kullanılamaz. " İş akışı çağrılırsa, <xref:System.Activities.InvalidWorkflowException> doğrulama hatasının metnini içeren bir atılır. Bu bir doğrulama hatasıdır çünkü başvuru türü ile değişmez değer ifadesi oluşturma, iş akışının her bir örneği için başvuru türünün yeni bir örneğini oluşturmaz. Bu sorunu çözmek için, değişmez değer ifadesini oluşturan ve başvuru türünün yeni bir örneğini döndüren bir ifade ile değiştirin.  
  
```csharp  
new Assign  
{  
    To = new OutArgument<List<string>>(items),  
    Value = new InArgument<List<string>>(new VisualBasicValue<List<string>>("New List(Of String)"))  
},  
```  
  
 İfadeler hakkında daha fazla bilgi için bkz. [ifadeler](expressions.md).  
  
#### <a name="invoking-methods-on-objects-using-expressions-and-the-invokemethod-activity"></a>Ifadeleri ve InvokeMethod etkinliğini kullanarak nesnelerde Yöntemler çağırma  
 <xref:System.Activities.Expressions.InvokeMethod%601>Etkinlik, .NET Framework sınıfların statik ve örnek yöntemlerini çağırmak için kullanılabilir. Bu konunun önceki bir örneğinde, sınıfı kullanılarak rastgele bir sayı oluşturulmuştur <xref:System.Random> .  
  
 [!code-csharp[CFX_WorkflowApplicationExample#51](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#51)]  
  
 <xref:System.Activities.Expressions.InvokeMethod%601>Etkinlik, sınıfının yöntemini çağırmak için de kullanılmış olabilir <xref:System.Random.Next%2A> <xref:System.Random> .  
  
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
  
 <xref:System.Random.Next%2A>Bir statik yöntem olmadığından, <xref:System.Random> özelliği için sınıfının bir örneği sağlanır <xref:System.Activities.Expressions.InvokeMethod%601.TargetObject%2A> . Bu örnekte, bir Visual Basic ifadesi kullanılarak yeni bir örnek oluşturulur, ancak daha önce oluşturulmuş ve bir iş akışı değişkeninde depolanmış olabilir. Bu örnekte etkinlik yerine etkinliğin kullanılması daha basit olacaktır <xref:System.Activities.Statements.Assign%601> <xref:System.Activities.Expressions.InvokeMethod%601> . Son olarak ya da etkinlikleri tarafından çağrılan yöntem çağrısı <xref:System.Activities.Statements.Assign%601> <xref:System.Activities.Expressions.InvokeMethod%601> uzun süre çalışıyorsa, <xref:System.Activities.Expressions.InvokeMethod%601> bir özelliği olduğundan avantajı vardır <xref:System.Activities.Expressions.InvokeMethod%601.RunAsynchronously%2A> . Bu özellik olarak ayarlandığında `true` , çağrılan yöntem iş akışı ile ilgili olarak zaman uyumsuz olarak çalışır. Diğer etkinlikler paralel ise, yöntem zaman uyumsuz olarak yürütülerek bunlar engellenmeyecektir. Ayrıca, çağrılacak yöntemin dönüş değeri yoksa, <xref:System.Activities.Expressions.InvokeMethod%601> yöntemi çağırmak için uygun bir yoldur.  
  
## <a name="arguments-and-dynamic-activities"></a>Bağımsız değişkenler ve dinamik etkinlikler  
 Bir etkinlik ağacına etkinlikler bağlayarak ve tüm özellikleri ve bağımsız değişkenleri yapılandırarak kodda bir iş akışı tanımı oluşturulur. Var olan bağımsız değişkenler bağlanabilir, ancak yeni bağımsız değişkenler etkinliklere eklenemez. Bu, kök etkinliğe geçirilen iş akışı bağımsız değişkenlerini içerir. Kesinlik temelli kodda, iş akışı bağımsız değişkenleri yeni bir CLR türü üzerinde özellikler olarak belirtilir ve XAML 'de ve kullanılarak bildirilenler `x:Class` `x:Member` . Bir iş akışı tanımı, bellek içi nesneler ağacı olarak oluşturulduğunda oluşturulan yeni bir CLR türü olmadığından, bağımsız değişkenler eklenemez. Ancak, bağımsız değişkenler bir öğesine eklenebilir <xref:System.Activities.DynamicActivity> . Bu örnekte, <xref:System.Activities.DynamicActivity%601> iki tamsayı bağımsız değişkeni alan oluşturulur, bunları bir araya ekler ve sonucu döndürür. <xref:System.Activities.DynamicActivityProperty>Her bağımsız değişken için bir oluşturulur ve işlemin sonucu <xref:System.Activities.Activity%601.Result%2A> öğesinin bağımsız değişkenine atanır <xref:System.Activities.DynamicActivity%601> .  
  
 [!code-csharp[CFX_WorkflowApplicationExample#55](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#55)]  
  
 Dinamik etkinlikler hakkında daha fazla bilgi için bkz. [çalışma zamanında etkinlik oluşturma](creating-an-activity-at-runtime-with-dynamicactivity.md).  
  
## <a name="compiled-activities"></a>Derlenen etkinlikler  
 Dinamik etkinlikler, kod kullanan bağımsız değişkenler içeren bir etkinlik tanımlamanın bir yoludur, ancak etkinlikler kodda oluşturulabilir ve türlere derlenmiş olabilir. <xref:System.Activities.CodeActivity>Ve ' den türetilen zaman uyumsuz etkinliklerden türetilen basit etkinlikler oluşturulabilir <xref:System.Activities.AsyncCodeActivity> . Bu etkinlikler bağımsız değişkenlere, dönüş değerlerine sahip olabilir ve zorunlu kod kullanarak mantığını tanımlayabilir. Bu tür etkinlikleri oluşturma örnekleri için bkz. [CodeActivity temel sınıfı](workflow-activity-authoring-using-the-codeactivity-class.md) ve [zaman uyumsuz etkinlikler oluşturma](creating-asynchronous-activities-in-wf.md).  
  
 Öğesinden türetilen etkinlikler <xref:System.Activities.NativeActivity> , zorunlu kod kullanarak mantığını tanımlayabilir ve ayrıca mantığı tanımlayan alt etkinlikleri içerebilir. Ayrıca, çalışma zamanının yer işaretlerini oluşturma gibi özelliklerine tam erişimi de vardır. Tabanlı etkinlik oluşturma örnekleri için <xref:System.Activities.NativeActivity> bkz. [NativeActivity temel sınıfı](nativeactivity-base-class.md), [nasıl yapılır: etkinlik oluşturma](how-to-create-an-activity.md)ve [özel bileşik etkinlik örneği kullanımı](./samples/custom-composite-using-native-activity.md) .  
  
 Öğesinden türetilen etkinlikler <xref:System.Activities.Activity> , yalnızca alt etkinliklerin kullanımıyla mantığını tanımlar. Bu etkinlikler genellikle iş akışı Tasarımcısı kullanılarak oluşturulur, ancak kod kullanılarak da tanımlanabilir. Aşağıdaki örnekte, `Square` öğesinden türetilen bir etkinlik tanımlanmıştır `Activity<int>` . `Square`Etkinliğin tek bir adı vardır <xref:System.Activities.InArgument%601> `Value` ve özelliğini kullanarak bir etkinlik belirterek mantığını tanımlar <xref:System.Activities.Statements.Sequence> <xref:System.Activities.Activity.Implementation%2A> . <xref:System.Activities.Statements.Sequence>Etkinlik bir <xref:System.Activities.Statements.WriteLine> etkinlik ve <xref:System.Activities.Statements.Assign%601> etkinlik içerir. Birlikte, bu üç Etkinlik etkinliğin mantığını uygular `Square` .  
  
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
  
 Aşağıdaki örnekte, tek bir etkinlikten oluşan bir iş akışı tanımı `Square` kullanılarak çağrılır <xref:System.Activities.WorkflowInvoker> .  
  
```csharp  
Dictionary<string, object> inputs = new Dictionary<string, object> {{ "Value", 5}};  
int result = WorkflowInvoker.Invoke(new Square(), inputs);  
Console.WriteLine("Result: {0}", result);  
```  
  
 İş akışı çağrıldığında, konsola aşağıdaki çıktı görüntülenir:  
  
 **Karelerini alıp değeri: 5**  
**Sonuç: 25**
