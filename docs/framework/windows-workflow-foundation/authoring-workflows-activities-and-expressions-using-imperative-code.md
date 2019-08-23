---
title: Kesin Kod Kullanarak İş Akışları, Etkinlikler ve İfadeler Yazma
ms.date: 03/30/2017
ms.assetid: cefc9cfc-2882-4eb9-8c94-7a6da957f2b2
ms.openlocfilehash: 22f5928dda55d77fde2ee518510eb2890e55b446
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940886"
---
# <a name="authoring-workflows-activities-and-expressions-using-imperative-code"></a>Kesin Kod Kullanarak İş Akışları, Etkinlikler ve İfadeler Yazma
İş akışı tanımı, yapılandırılmış etkinlik nesnelerinin bir ağacıdır. Bu etkinlik ağacı, el ile düzenlenen XAML veya XAML oluşturmak için İş Akışı Tasarımcısı kullanılarak dahil olmak üzere birçok şekilde tanımlanabilir. Ancak XAML kullanımı bir gereklilik değildir. Ayrıca, iş akışı tanımları programlama yoluyla da oluşturulabilir. Bu konu, kod kullanarak iş akışı tanımları, etkinlikler ve deyimler oluşturmaya genel bir bakış sağlar. Kodu kullanarak XAML iş akışlarıyla çalışma örnekleri için bkz. [xaml 'de ve xaml 'de Iş akışlarını ve etkinlikleri seri hale getirme](serializing-workflows-and-activities-to-and-from-xaml.md).  
  
## <a name="creating-workflow-definitions"></a>Iş akışı tanımları oluşturma  
 Etkinlik türünün bir örneğini oluşturarak ve etkinlik nesnesinin özellikleri yapılandırılarak bir iş akışı tanımı oluşturulabilir. Alt etkinlik içermeyen etkinlikler için, bu, birkaç satır kod kullanılarak gerçekleştirilebilir.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#47](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#47)]  
  
> [!NOTE]
> Bu konudaki örnekler örnek iş akışlarını <xref:System.Activities.WorkflowInvoker> çalıştırmak için kullanır. İş akışlarını çağırma, bağımsız değişkenleri geçirme ve kullanılabilir farklı barındırma seçeneklerini kullanma hakkında daha fazla bilgi için bkz. [Workflowwınvoker ve WorkflowApplication kullanma](using-workflowinvoker-and-workflowapplication.md).  
  
 Bu örnekte, tek <xref:System.Activities.Statements.WriteLine> bir etkinlikten oluşan bir iş akışı oluşturulur. <xref:System.Activities.Statements.WriteLine> Etkinliğinbağımsızdeğişkeniayarlanır<xref:System.Activities.Statements.WriteLine.Text%2A> ve iş akışı çağrılır. Bir etkinlik alt etkinlikler içeriyorsa, oluşturma yöntemi benzerdir. Aşağıdaki örnek iki <xref:System.Activities.Statements.WriteLine> etkinlik içeren <xref:System.Activities.Statements.Sequence> bir etkinlik kullanır.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#48](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#48)]  
  
### <a name="using-object-initializers"></a>Nesne başlatıcılarının kullanımı  
 Bu konudaki örnekler, nesne başlatma sözdizimini kullanır. Nesne başlatma sözdizimi, iş akışındaki etkinliklerin hiyerarşik bir görünümünü sağladığından koddaki iş akışı tanımlarını oluşturmak için kullanışlı bir yol olabilir ve etkinlikler arasındaki ilişkiyi gösterir. Program aracılığıyla iş akışları oluştururken nesne başlatma söz dizimini kullanma gereksinimi yoktur. Aşağıdaki örnek, önceki örneğe işlevsel olarak eşdeğerdir.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#49](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#49)]  
  
 Nesne başlatıcıları hakkında daha fazla bilgi için bkz [. nasıl yapılır: Bir oluşturucuyu (C# Programlama Kılavuzu)](https://go.microsoft.com/fwlink/?LinkId=161015) çağırmadan nesneleri başlatın ve [şunları yapın: Nesne Başlatıcısı](https://go.microsoft.com/fwlink/?LinkId=161016)kullanarak bir nesne bildirin.  
  
### <a name="working-with-variables-literal-values-and-expressions"></a>Değişkenler, değişmez değerler ve Ifadelerle çalışma  
 Kodu kullanarak bir iş akışı tanımı oluştururken, iş akışı tanımı oluşturmanın bir parçası olarak hangi kodun yürütüldüğünü ve bu iş akışının bir örneğini yürütmenin bir parçası olarak hangi kodun yürütüldüğünü unutmayın. Örneğin, aşağıdaki iş akışı rastgele bir sayı oluşturmak ve konsola yazmak için tasarlanmıştır.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#50](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#50)]  
  
 Bu iş akışı Tanım kodu yürütüldüğünde, çağrısı `Random.Next` yapılır ve sonuç iş akışı tanımında değişmez değer olarak depolanır. Bu iş akışının birçok örneği çağrılabilir ve hepsi aynı numarayı görüntüler. İş akışı yürütmesi sırasında rastgele sayının oluşturulması durumunda, iş akışı her çalıştığında değerlendirilen bir ifade kullanılmalıdır. Aşağıdaki örnekte, bir <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>Visual Basic ifadesi ile kullanılır.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#51](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#51)]  
  
 Önceki örnekteki ifade, <xref:Microsoft.CSharp.Activities.CSharpValue%601> ve bir C# ifadesi kullanılarak da uygulanabilir.  
  
```csharp  
new Assign<int>  
{  
    To = n,  
    Value = new CSharpValue<int>("new Random().Next(1, 101)")  
}  
```  
  
 C#ifadeleri içeren iş akışı çağrılmadan önce ifadeler derlenmelidir. C# İfadeler derlenmeyecekse, iş akışı aşağıdakine benzer <xref:System.NotSupportedException> bir iletiyle çağrıldığında bir atılır: `Expression Activity type 'CSharpValue`1 ' çalıştırmak için derleme gerekiyor.  Lütfen iş akışının derlendiğinden emin olun. ' Visual Studio 'da oluşturulan iş akışlarını içeren çoğu senaryoda C# ifadeler otomatik olarak derlenir, ancak kod iş akışları gibi bazı senaryolarda C# ifadeler el ile olmalıdır Medi. İfadelerin nasıl derlenmeye C# ilişkin bir örnek için, [ C# ifadeler](csharp-expressions.md) konusunun [kod C# iş akışlarında ifadeleri kullanma](csharp-expressions.md#CodeWorkflows) bölümüne bakın.  
  
 Bir <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> ifadede r değeri olarak kullanılabilen Visual Basic sözdiziminde bir ifadeyi temsil eder ve bir ifadede r-value olarak kullanılabilecek bir <xref:Microsoft.CSharp.Activities.CSharpValue%601> ifade C# temsil eder. Bu ifadeler, kapsayan etkinliğin her yürütüldüğü her seferinde değerlendirilir. İfadenin sonucu iş akışı değişkenine `n`atanır ve bu sonuçlar iş akışındaki sonraki etkinlik tarafından kullanılır. Çalışma zamanında `n` <xref:System.Activities.ActivityContext> iş akışı değişkeninin değerine erişmek için gereklidir. Bu, aşağıdaki lambda ifadesi kullanılarak erişilebilir.  
  
> [!NOTE]
> Bu kodların her ikisi de programlama dili olarak kullanıldığı C# , ancak biri bir <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> kullanır <xref:Microsoft.CSharp.Activities.CSharpValue%601>ve bir kullanır. <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>ve <xref:Microsoft.CSharp.Activities.CSharpValue%601> hem Visual Basic hem de C# projelerinde kullanılabilir. Varsayılan olarak, iş akışı tasarımcısında oluşturulan ifadeler barındırma projesinin diliyle eşleşir. Kodda iş akışları oluştururken, istenen dil iş akışı yazarının kararına göre belirlenir.  
  
 Bu örneklerde, ifadenin sonucu iş akışı değişkenine `n`atanır ve bu sonuçlar iş akışındaki sonraki etkinlik tarafından kullanılır. Çalışma zamanında `n` <xref:System.Activities.ActivityContext> iş akışı değişkeninin değerine erişmek için gereklidir. Bu, aşağıdaki lambda ifadesi kullanılarak erişilebilir.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#52](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#52)]  
  
 Lambda ifadeleri hakkında daha fazla bilgi için bkz. [lambda ifadeleriC# (Programlama Kılavuzu)](https://go.microsoft.com/fwlink/?LinkID=152436) veya [lambda ifadeleri (Visual Basic)](https://go.microsoft.com/fwlink/?LinkID=152437).  
  
 Lambda ifadeleri XAML biçimine serileştirilebilir değildir. Lambda ifadeleriyle bir iş akışını seri hale getirme girişimi yapılırsa, aşağıdaki iletiyle <xref:System.Activities.Expressions.LambdaSerializationException> bir oluşturulur: "Bu iş akışı kodda belirtilen Lambda ifadelerini içerir. Bu ifadeler XAML serileştirilebilir değildir. İş akışınızı XAML-serileştirilebilir yapmak için VisualBasicValue/VisualBasicReference veya ExpressionServices. Convert (lambda) kullanın. Bu işlem lambda ifadelerinizi ifade etkinliklerine dönüştürür. " Bu ifadeyi XAML ile uyumlu hale getirmek için, <xref:System.Activities.Expressions.ExpressionServices> aşağıdaki <xref:System.Activities.Expressions.ExpressionServices.Convert%2A>örnekte gösterildiği gibi ve kullanın.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#53](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#53)]  
  
 <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> Ayrıca kullanılabilir. Visual Basic ifadesi kullanılırken hiçbir lambda ifadesinin gerekli olmadığını unutmayın.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#54](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#54)]  
  
 Çalışma zamanında, Visual Basic ifadeleri LINQ ifadelerine derlenir. Önceki örneklerin her ikisi de xaml 'ye serileştirilebilir, ancak serileştirilmiş XAML iş akışı tasarımcısında görüntülenmek ve düzenlenilmesi amaçlanıyorsa deyimleriniz için kullanın <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> . Kullanan serileştirilmiş iş akışları `ExpressionServices.Convert` tasarımcıda açılabilir, ancak ifadenin değeri boş olur. XAML 'de iş akışlarını serileştirme hakkında daha fazla bilgi için bkz. [xaml 'de ve xaml 'de Iş akışlarını ve etkinlikleri serileştirme](serializing-workflows-and-activities-to-and-from-xaml.md).  
  
#### <a name="literal-expressions-and-reference-types"></a>Değişmez değer Ifadeleri ve başvuru türleri  
 Değişmez değerler, <xref:System.Activities.Expressions.Literal%601> etkinliğin iş akışlarında temsil edilir. Aşağıdaki <xref:System.Activities.Statements.WriteLine> etkinlikler işlevsel olarak eşdeğerdir.  
  
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
  
 Dışında <xref:System.String>herhangi bir başvuru türüyle değişmez bir ifade başlatmak geçersizdir. Aşağıdaki örnekte, bir <xref:System.Activities.Statements.Assign> <xref:System.Activities.Statements.Assign.Value%2A> `List<string>`etkinliğin özelliği, kullanılarak değişmez değer ifadesiyle başlatılır.  
  
```csharp  
new Assign  
{  
    To = new OutArgument<List<string>>(items),  
    Value = new InArgument<List<string>>(new List<string>())  
},  
```  
  
 Bu etkinliği içeren iş akışı doğrulandıktan sonra, aşağıdaki doğrulama hatası döndürülür: "Literal yalnızca değer türlerini ve sabit tür System. String ' i destekler. System. Collections. Generic. List ' 1 [System. String] türü bir sabit değer olarak kullanılamaz. " İş akışı çağrılırsa, doğrulama hatasının metnini <xref:System.Activities.InvalidWorkflowException> içeren bir atılır. Bu bir doğrulama hatasıdır çünkü başvuru türü ile değişmez değer ifadesi oluşturma, iş akışının her bir örneği için başvuru türünün yeni bir örneğini oluşturmaz. Bu sorunu çözmek için, değişmez değer ifadesini oluşturan ve başvuru türünün yeni bir örneğini döndüren bir ifade ile değiştirin.  
  
```csharp  
new Assign  
{  
    To = new OutArgument<List<string>>(items),  
    Value = new InArgument<List<string>>(new VisualBasicValue<List<string>>("New List(Of String)"))  
},  
```  
  
 İfadeler hakkında daha fazla bilgi için bkz. [ifadeler](expressions.md).  
  
#### <a name="invoking-methods-on-objects-using-expressions-and-the-invokemethod-activity"></a>Ifadeleri ve InvokeMethod etkinliğini kullanarak nesnelerde Yöntemler çağırma  
 <xref:System.Activities.Expressions.InvokeMethod%601> Etkinlik, .NET Framework sınıfların statik ve örnek yöntemlerini çağırmak için kullanılabilir. Bu konunun önceki bir örneğinde, <xref:System.Random> sınıfı kullanılarak rastgele bir sayı oluşturulmuştur.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#51](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#51)]  
  
 Etkinlik, <xref:System.Random> sınıfının <xref:System.Random.Next%2A> yöntemini çağırmak için de kullanılmış olabilir. <xref:System.Activities.Expressions.InvokeMethod%601>  
  
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
  
 Bir statik yöntem olmadığından, <xref:System.Activities.Expressions.InvokeMethod%601.TargetObject%2A> özelliği için <xref:System.Random> sınıfının bir örneği sağlanır. <xref:System.Random.Next%2A> Bu örnekte, bir Visual Basic ifadesi kullanılarak yeni bir örnek oluşturulur, ancak daha önce oluşturulmuş ve bir iş akışı değişkeninde depolanmış olabilir. Bu örnekte etkinlik yerine <xref:System.Activities.Statements.Assign%601> <xref:System.Activities.Expressions.InvokeMethod%601> etkinliğin kullanılması daha basit olacaktır. <xref:System.Activities.Statements.Assign%601> Son olarak ya da <xref:System.Activities.Expressions.InvokeMethod%601> etkinlikleri tarafından çağrılan yöntem çağrısı uzun süre çalışıyorsa, <xref:System.Activities.Expressions.InvokeMethod%601> bir <xref:System.Activities.Expressions.InvokeMethod%601.RunAsynchronously%2A> özelliği olduğundan avantajı vardır. Bu özellik olarak `true`ayarlandığında, çağrılan yöntem iş akışı ile ilgili olarak zaman uyumsuz olarak çalışır. Diğer etkinlikler paralel ise, yöntem zaman uyumsuz olarak yürütülerek bunlar engellenmeyecektir. Ayrıca, çağrılacak yöntemin dönüş değeri yoksa, <xref:System.Activities.Expressions.InvokeMethod%601> yöntemi çağırmak için uygun bir yoldur.  
  
## <a name="arguments-and-dynamic-activities"></a>Bağımsız değişkenler ve dinamik etkinlikler  
 Bir etkinlik ağacına etkinlikler bağlayarak ve tüm özellikleri ve bağımsız değişkenleri yapılandırarak kodda bir iş akışı tanımı oluşturulur. Var olan bağımsız değişkenler bağlanabilir, ancak yeni bağımsız değişkenler etkinliklere eklenemez. Bu, kök etkinliğe geçirilen iş akışı bağımsız değişkenlerini içerir. Kesinlik temelli kodda, iş akışı bağımsız değişkenleri yeni bir clr türü üzerinde özellikler olarak belirtilir ve xaml 'de ve `x:Class` `x:Member`kullanılarak bildirilenler. Bir iş akışı tanımı, bellek içi nesneler ağacı olarak oluşturulduğunda oluşturulan yeni bir CLR türü olmadığından, bağımsız değişkenler eklenemez. Ancak, bağımsız değişkenler bir <xref:System.Activities.DynamicActivity>öğesine eklenebilir. Bu örnekte, <xref:System.Activities.DynamicActivity%601> iki tamsayı bağımsız değişkeni alan oluşturulur, bunları bir araya ekler ve sonucu döndürür. Her <xref:System.Activities.DynamicActivityProperty> bağımsız değişken için bir oluşturulur ve işlemin sonucu öğesinin <xref:System.Activities.Activity%601.Result%2A> <xref:System.Activities.DynamicActivity%601>bağımsız değişkenine atanır.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#55](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#55)]  
  
 Dinamik etkinlikler hakkında daha fazla bilgi için bkz. [çalışma zamanında etkinlik oluşturma](creating-an-activity-at-runtime-with-dynamicactivity.md).  
  
## <a name="compiled-activities"></a>Derlenen etkinlikler  
 Dinamik etkinlikler, kod kullanan bağımsız değişkenler içeren bir etkinlik tanımlamanın bir yoludur, ancak etkinlikler kodda oluşturulabilir ve türlere derlenmiş olabilir. Ve <xref:System.Activities.CodeActivity>' den <xref:System.Activities.AsyncCodeActivity>türetilen zaman uyumsuz etkinliklerden türetilen basit etkinlikler oluşturulabilir. Bu etkinlikler bağımsız değişkenlere, dönüş değerlerine sahip olabilir ve zorunlu kod kullanarak mantığını tanımlayabilir. Bu tür etkinlikleri oluşturma örnekleri için bkz. [CodeActivity temel sınıfı](workflow-activity-authoring-using-the-codeactivity-class.md) ve [zaman uyumsuz etkinlikler oluşturma](creating-asynchronous-activities-in-wf.md).  
  
 Öğesinden <xref:System.Activities.NativeActivity> türetilen etkinlikler, zorunlu kod kullanarak mantığını tanımlayabilir ve ayrıca mantığı tanımlayan alt etkinlikleri içerebilir. Ayrıca, çalışma zamanının yer işaretlerini oluşturma gibi özelliklerine tam erişimi de vardır. Tabanlı etkinlik oluşturma <xref:System.Activities.NativeActivity>örnekleri için bkz. [NativeActivity temel sınıfı](nativeactivity-base-class.md), [nasıl yapılır: Yerel etkinlik örneğini](how-to-create-an-activity.md)kullanarak bir etkinlik ve [özel bileşik](./samples/custom-composite-using-native-activity.md) oluşturma.  
  
 Öğesinden <xref:System.Activities.Activity> türetilen etkinlikler, yalnızca alt etkinliklerin kullanımıyla mantığını tanımlar. Bu etkinlikler genellikle iş akışı Tasarımcısı kullanılarak oluşturulur, ancak kod kullanılarak da tanımlanabilir. Aşağıdaki örnekte, öğesinden `Square` `Activity<int>`türetilen bir etkinlik tanımlanmıştır. `Square` Etkinliğin <xref:System.Activities.Statements.Sequence> tek <xref:System.Activities.InArgument%601> bir adı`Value`vardır ve özelliğini<xref:System.Activities.Activity.Implementation%2A> kullanarak bir etkinlik belirterek mantığını tanımlar. Etkinlik bir <xref:System.Activities.Statements.WriteLine> etkinlik ve<xref:System.Activities.Statements.Assign%601> etkinlik içerir. <xref:System.Activities.Statements.Sequence> Birlikte, bu üç etkinlik `Square` etkinliğin mantığını uygular.  
  
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
  
 Aşağıdaki örnekte, tek `Square` bir etkinlikten oluşan bir iş akışı tanımı kullanılarak <xref:System.Activities.WorkflowInvoker>çağrılır.  
  
```csharp  
Dictionary<string, object> inputs = new Dictionary<string, object> {{ "Value", 5}};  
int result = WorkflowInvoker.Invoke(new Square(), inputs);  
Console.WriteLine("Result: {0}", result);  
```  
  
 İş akışı çağrıldığında, konsola aşağıdaki çıktı görüntülenir:  
  
 **Karelerini alıp değeri: e**  
**Kaynaklanan 250**
