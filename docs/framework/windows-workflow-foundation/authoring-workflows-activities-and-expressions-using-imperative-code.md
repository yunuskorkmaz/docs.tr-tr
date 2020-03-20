---
title: Kesin Kod Kullanarak İş Akışları, Etkinlikler ve İfadeler Yazma
ms.date: 03/30/2017
ms.assetid: cefc9cfc-2882-4eb9-8c94-7a6da957f2b2
ms.openlocfilehash: 7f22880a965274961006f999b1170634377fcf1c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183022"
---
# <a name="authoring-workflows-activities-and-expressions-using-imperative-code"></a>Kesin Kod Kullanarak İş Akışları, Etkinlikler ve İfadeler Yazma
İş akışı tanımı, yapılandırılan etkinlik nesnelerinden oluşan bir ağaçtır. Bu etkinlik ağacı, XAML'yi elle düzenleme veya XAML üretmek için İş Akışı Tasarımcısı'nı kullanmak da dahil olmak üzere birçok şekilde tanımlanabilir. Ancak XAML kullanımı bir gereklilik değildir. İş akışı tanımları da programlı olarak oluşturulabilir. Bu konu, kod kullanarak iş akışı tanımları, etkinlikler ve ifadeler oluşturmaya genel bir bakış sağlar. Kod kullanarak XAML iş akışlarıyla çalışma örnekleri için, [XAML'ye ve Etkinliklere Seri Hale Getirme İş Akışları'na](serializing-workflows-and-activities-to-and-from-xaml.md)bakın.  
  
## <a name="creating-workflow-definitions"></a>İş Akışı Tanımları Oluşturma  
 İş akışı tanımı, etkinlik türünün bir örneğinin anlık olarak ayarlanması ve etkinlik nesnesinin özelliklerinin yapılandırılmasıyla oluşturulabilir. Alt etkinlikler içermeyen etkinlikler için bu, birkaç kod satırı kullanılarak gerçekleştirilebilir.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#47](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#47)]  
  
> [!NOTE]
> Bu konudaki örnekler, örnek iş akışlarını çalıştırmak için kullanılır. <xref:System.Activities.WorkflowInvoker> İş akışlarının çağrılması, bağımsız değişkenlerin geçirilmesi ve kullanılabilen farklı barındırma seçenekleri hakkında daha fazla bilgi [için](using-workflowinvoker-and-workflowapplication.md)bkz.  
  
 Bu örnekte, tek <xref:System.Activities.Statements.WriteLine> bir etkinlikten oluşan bir iş akışı oluşturulur. <xref:System.Activities.Statements.WriteLine> Etkinliğin <xref:System.Activities.Statements.WriteLine.Text%2A> bağımsız değişkeni ayarlanır ve iş akışı çağrılır. Bir etkinlik alt etkinlikleri içeriyorsa, inşaat yöntemi benzerdir. Aşağıdaki örnekte <xref:System.Activities.Statements.Sequence> iki <xref:System.Activities.Statements.WriteLine> etkinlik içeren bir etkinlik kullanır.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#48](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#48)]  
  
### <a name="using-object-initializers"></a>Nesne Baş harflerini kullanma  
 Bu konudaki örnekler nesne başlatma sözdizimini kullanır. Nesne başlatma sözdizimi, iş akışındaki etkinliklerin hiyerarşik bir görünümünü sağladığından ve etkinlikler arasındaki ilişkiyi gösterdiğinden, kodda iş akışı tanımları oluşturmak için yararlı bir yol olabilir. İş akışlarını programlı bir şekilde oluştururken nesne başlatma sözdizimini kullanma zorunluluğu yoktur. Aşağıdaki örnek işlevsel olarak önceki örneğe eşdeğerdir.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#49](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#49)]  
  
 Nesne baş harfleri hakkında daha fazla bilgi için bkz: Kurucu [Çağırmadan Nesneleri Başlatma (C# Programlama Kılavuzu)](../../csharp/programming-guide/classes-and-structs/how-to-initialize-objects-by-using-an-object-initializer.md) ve [Nesne Başadımlaştırıcıkullanarak NesneYi Nasıl Bildirin.](../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)  
  
### <a name="working-with-variables-literal-values-and-expressions"></a>Değişkenler, Gerçek Değerler ve İfadelerle Çalışma  
 Kodu kullanarak bir iş akışı tanımı oluştururken, iş akışı tanımının oluşturulmasının bir parçası olarak hangi kodun yürütüldettiğini ve bu iş akışının bir örneğinin yürütülmesinin bir parçası olarak hangi kodun yürütüldettiğini unutmayın. Örneğin, aşağıdaki iş akışı rasgele bir sayı oluşturmak ve konsola yazmak için tasarlanmıştır.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#50](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#50)]  
  
 Bu iş akışı tanımı kodu yürütüldüğünde, çağrı `Random.Next` yapılır ve sonuç iş akışı tanımında gerçek bir değer olarak depolanır. Bu iş akışının birçok örneği çağrılabilir ve tümü aynı sayıyı görüntüler. Rasgele sayı oluşturmanın iş akışı yürütmesırasında oluşması için, iş akışı her çalıştığında değerlendirilen bir ifade kullanılmalıdır. Aşağıdaki örnekte, Visual Basic ifadesi . <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>  
  
 [!code-csharp[CFX_WorkflowApplicationExample#51](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#51)]  
  
 Önceki örnekteki ifade a <xref:Microsoft.CSharp.Activities.CSharpValue%601> ve C# ifadesi kullanılarak da uygulanabilir.  
  
```csharp  
new Assign<int>  
{  
    To = n,  
    Value = new CSharpValue<int>("new Random().Next(1, 101)")  
}  
```  
  
 C# ifadeleri, bunları içeren iş akışı çağrılmadan önce derlenmelidir. C# ifadeleri derlenmezse, iş <xref:System.NotSupportedException> akışı aşağıdakine benzer bir iletiyle çağrıldığında a ``Expression Activity type 'CSharpValue`1' requires compilation in order to run.  Please ensure that the workflow has been compiled.`` atılır: Visual Studio'da oluşturulan iş akışlarını içeren çoğu senaryoda C# ifadeleri otomatik olarak derlenir, ancak kod iş akışları gibi bazı senaryolarda C# ifadeleri el ile derlenmelidir. C# ifadelerinin nasıl derlenebildiğini öğrenmek için [C# İfadeleri](csharp-expressions.md) konusunun kod iş akışları bölümünde [C# ifadelerini kullanma](csharp-expressions.md#CodeWorkflows) bölümüne bakın.  
  
 A, <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> Visual Basic sözdiziminde bir ifadede r değeri olarak kullanılabilecek <xref:Microsoft.CSharp.Activities.CSharpValue%601> bir ifadeyi ve C# sözdiziminde bir ifadede r değeri olarak kullanılabilecek bir ifadeyi temsil eder. Bu ifadeler, içeren etkinlik her yürütüldünde değerlendirilir. İfadenin sonucu iş akışı değişkenine `n`atanır ve bu sonuçlar iş akışındaki bir sonraki etkinlik tarafından kullanılır. Çalışma zamanında `n` <xref:System.Activities.ActivityContext> iş akışı değişkeninin değerine erişmek için gereklidir. Bu aşağıdaki lambda ifadesi kullanılarak erişilebilir.  
  
> [!NOTE]
> Bu kodların her ikisinin de programlama dili olarak C# kullanan <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> örnekler olduğunu, ancak bir tanenin a ve bir'in bir <xref:Microsoft.CSharp.Activities.CSharpValue%601>. <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>ve <xref:Microsoft.CSharp.Activities.CSharpValue%601> Visual Basic ve C# projelerinde kullanılabilir. Varsayılan olarak, iş akışı tasarımcısında oluşturulan ifadeler barındırma projesinin diliyle eşleşir. Kodda iş akışları oluştururken, istenen dil iş akışı yazarının takdirine bağlıdır.  
  
 Bu örneklerde ifadenin sonucu iş akışı değişkenine `n`atanır ve bu sonuçlar iş akışındaki bir sonraki etkinlik tarafından kullanılır. Çalışma zamanında `n` <xref:System.Activities.ActivityContext> iş akışı değişkeninin değerine erişmek için gereklidir. Bu aşağıdaki lambda ifadesi kullanılarak erişilebilir.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#52](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#52)]  
  
 Lambda ifadeleri hakkında daha fazla bilgi için [lambda İfadeleri (C# Programlama Kılavuzu)](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) veya [Lambda İfadeleri (Visual Basic)](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)'ye bakın.  
  
 Lambda ifadeleri XAML biçimine serileştirilebilir değildir. Lambda ifadeleri ile bir iş akışını serihale etme <xref:System.Activities.Expressions.LambdaSerializationException> girişimi yapılırsa, aşağıdaki mesajla bir iş akışı yapılır: "Bu iş akışı kodda belirtilen lambda ifadelerini içerir. Bu ifadeler XAML serializable değildir. İş akışınızı XAML serializable yapmak için VisualBasicValue/VisualBasicReference veya ExpressionServices.Convert(lambda) kullanın. Bu da lambda ifadelerinizi ifade etkinliklerine dönüştürecektir." Bu ifadeyi XAML ile <xref:System.Activities.Expressions.ExpressionServices> uyumlu <xref:System.Activities.Expressions.ExpressionServices.Convert%2A>hale getirmek için aşağıdaki örnekte gösterildiği gibi kullanın ve kullanın.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#53](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#53)]  
  
 A <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> da kullanılabilir. Visual Basic ifadesini kullanırken lambda ifadesinin gerekli olmadığını unutmayın.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#54](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#54)]  
  
 Çalışma zamanında Visual Basic ifadeleri LINQ ifadeleri halinde derlenir. Önceki örneklerin her ikisi de XAML'ye serileştirilebilir, ancak serileştirilmiş XAML iş akışı tasarımcısında <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> görüntülenecek ve düzenlenmek üzere tasarlandıysa, ifadeleriniz için kullanın. Kullanılan `ExpressionServices.Convert` serileştirilmiş iş akışları tasarımcıda açılabilir, ancak ifadenin değeri boş olacaktır. XAML'ye iş akışlarını serileştirme hakkında daha fazla bilgi için Bkz. [XAML'ye seri hale getirme İş Akışları ve Etkinlikleri.](serializing-workflows-and-activities-to-and-from-xaml.md)  
  
#### <a name="literal-expressions-and-reference-types"></a>Gerçek İfadeler ve Başvuru Türleri  
 Gerçek ifadeler <xref:System.Activities.Expressions.Literal%601> iş akışlarında etkinlik tarafından temsil edilir. Aşağıdaki <xref:System.Activities.Statements.WriteLine> etkinlikler işlevsel olarak eşdeğerdir.  
  
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
  
 Dışında herhangi bir başvuru türü ile bir edebi <xref:System.String>ifade yi başlatmak geçersizdir. Aşağıdaki örnekte, <xref:System.Activities.Statements.Assign> bir etkinliğin <xref:System.Activities.Statements.Assign.Value%2A> özelliği bir `List<string>`. kullanılarak gerçek bir ifadeyle başharfe  
  
```csharp  
new Assign  
{  
    To = new OutArgument<List<string>>(items),  
    Value = new InArgument<List<string>>(new List<string>())  
},  
```  
  
 Bu etkinliği içeren iş akışı doğrulandığında, aşağıdaki doğrulama hatası döndürülür: "Literal yalnızca değer türlerini ve değişmez sistem türünü destekler. System.Collections.Generic.List'1[System.String] türü gerçek bir kelime olarak kullanılamaz." İş akışı çağrılması durumunda, doğrulama hatası metnini içeren bir <xref:System.Activities.InvalidWorkflowException> atılmıştır. Başvuru türüne sahip gerçek bir ifade oluşturmak, iş akışının her örneği için başvuru türünün yeni bir örneğini oluşturmadığından, bu bir doğrulama hatasıdır. Bunu çözmek için, gerçek ifadeyi başvuru türünün yeni bir örneğini oluşturan ve döndüren bir ifadeyle değiştirin.  
  
```csharp  
new Assign  
{  
    To = new OutArgument<List<string>>(items),  
    Value = new InArgument<List<string>>(new VisualBasicValue<List<string>>("New List(Of String)"))  
},  
```  
  
 İfadeler hakkında daha fazla bilgi için [Bkz. İfadeler](expressions.md).  
  
#### <a name="invoking-methods-on-objects-using-expressions-and-the-invokemethod-activity"></a>İfadeleri Kullanan Nesnelere Çağrı Yöntemleri ve InvokeMethod Etkinliği  
 Etkinlik, <xref:System.Activities.Expressions.InvokeMethod%601> .NET Framework'deki sınıfların statik ve örnek yöntemlerini çağırmak için kullanılabilir. Bu konudaönceki bir örnekte, <xref:System.Random> sınıf kullanılarak rasgele bir sayı oluşturuldu.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#51](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#51)]  
  
 Etkinlik, <xref:System.Activities.Expressions.InvokeMethod%601> <xref:System.Random.Next%2A> <xref:System.Random> sınıfın yöntemini çağırmak için de kullanılmış olabilir.  
  
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
  
 <xref:System.Random.Next%2A> Statik bir yöntem olmadığından, <xref:System.Activities.Expressions.InvokeMethod%601.TargetObject%2A> özellik için <xref:System.Random> sınıfın bir örneği sağlanır. Bu örnekte Visual Basic ifadesi kullanılarak yeni bir örnek oluşturulur, ancak daha önce oluşturulmuş ve iş akışı değişkeninde depolanmış olabilir. Bu örnekte, <xref:System.Activities.Statements.Assign%601> <xref:System.Activities.Expressions.InvokeMethod%601> etkinlik yerine etkinliği kullanmak daha kolay olacaktır. Yöntem arama <xref:System.Activities.Statements.Assign%601> sonuçta ya veya <xref:System.Activities.Expressions.InvokeMethod%601> faaliyetleri tarafından çağrılan uzun <xref:System.Activities.Expressions.InvokeMethod%601> çalışıyorsa, bir <xref:System.Activities.Expressions.InvokeMethod%601.RunAsynchronously%2A> özelliği olduğundan bir avantaja sahiptir. Bu özellik `true`ayarlandığında, çağrılan yöntem iş akışı yla ilgili olarak eşzamanlı olarak çalışacaktır. Diğer etkinlikler paralelse, yöntem eşkenardırıcı bir şekilde yürütülerken engellenmez. Ayrıca, çağrılacak yöntemin geri dönüş değeri <xref:System.Activities.Expressions.InvokeMethod%601> yoksa, yöntemi çağırmak için uygun yoldur.  
  
## <a name="arguments-and-dynamic-activities"></a>Argümanlar ve Dinamik Faaliyetler  
 İş akışı tanımı, etkinlikleri bir etkinlik ağacında birleştirerek ve herhangi bir özelliği ve bağımsız değişkeni yapılandırarak kod halinde oluşturulur. Varolan bağımsız değişkenler bağlanabilir, ancak etkinliklere yeni bağımsız değişkenler eklenemez. Bu, kök aktiviteye geçirilen iş akışı bağımsız değişkenlerini içerir. Zorunlu kodda, iş akışı bağımsız değişkenleri yeni bir CLR türünde özellik olarak `x:Class` `x:Member`belirtilir ve XAML'de kullanılarak ve . Bir iş akışı tanımı bellek nesneleri ağacı olarak oluşturulduğunda yeni CLR türü oluşturulmadığından, bağımsız değişkenler eklenemez. Ancak, bağımsız değişkenler <xref:System.Activities.DynamicActivity>bir . Bu örnekte, <xref:System.Activities.DynamicActivity%601> iki tamsayı bağımsız değişkeni alan, bunları bir araya getiren ve sonucu döndüren bir oluşturulur. A <xref:System.Activities.DynamicActivityProperty> her bağımsız değişken için oluşturulur ve işlemin sonucu <xref:System.Activities.Activity%601.Result%2A> bağımsız <xref:System.Activities.DynamicActivity%601>değişkenine atanır.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#55](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#55)]  
  
 Dinamik etkinlikler hakkında daha fazla bilgi için [Runtime'da Etkinlik Oluşturma'ya](creating-an-activity-at-runtime-with-dynamicactivity.md)bakın.  
  
## <a name="compiled-activities"></a>Derlenmiş Etkinlikler  
 Dinamik etkinlikler, kodu kullanarak bağımsız değişkenler içeren bir etkinliği tanımlamanın bir yoludur, ancak etkinlikler kod halinde oluşturulabilir ve türler halinde derlenebilir. Basit etkinlikler, 'den ve <xref:System.Activities.CodeActivity>' den <xref:System.Activities.AsyncCodeActivity>türeyen eşzamanlı etkinliklerden türeyen basit etkinlikler oluşturulabilir. Bu etkinlikler, bağımsız değişkenler olabilir, değerleri döndürebilir ve zorunlu kodu kullanarak mantıklarını tanımlayabilir. Bu tür etkinlikler oluşturma örnekleri için Bkz. [KodEtkinliği Taban Sınıfı](workflow-activity-authoring-using-the-codeactivity-class.md) ve [Eşzamanlı Etkinlikler Oluşturma.](creating-asynchronous-activities-in-wf.md)  
  
 Bu tür <xref:System.Activities.NativeActivity> etkinlikler zorunlu kodu kullanarak kendi mantığını tanımlayabilir ve mantığı tanımlayan alt etkinlikleri de içerebilir. Ayrıca, yer imleri oluşturma gibi çalışma zamanının özelliklerine de tam erişim sağlarlar. Tabanlı <xref:System.Activities.NativeActivity>etkinlik oluşturma örnekleri için bkz: [NativeActivity Base Class](nativeactivity-base-class.md), How [to: Create a Activity](how-to-create-an-activity.md)ve Yerel Etkinlik örneğini kullanarak Özel [Bileşik.](./samples/custom-composite-using-native-activity.md)  
  
 Mantıklarından türeyen etkinlikler sadece çocuk etkinliklerini kullanarak <xref:System.Activities.Activity> tanımlar. Bu etkinlikler genellikle iş akışı tasarımcısı kullanılarak oluşturulur, ancak kod kullanılarak da tanımlanabilir. Aşağıdaki örnekte, `Square` 'den `Activity<int>`türeyen bir etkinlik tanımlanır. Etkinlik `Square` <xref:System.Activities.InArgument%601> adlı `Value`tek bir vardır ve <xref:System.Activities.Statements.Sequence> <xref:System.Activities.Activity.Implementation%2A> özelliği kullanarak bir etkinlik belirterek onun mantığını tanımlar. Etkinlik <xref:System.Activities.Statements.Sequence> bir <xref:System.Activities.Statements.WriteLine> etkinlik ve <xref:System.Activities.Statements.Assign%601> bir etkinlik içerir. Birlikte, bu üç etkinlik `Square` etkinliğin mantığını uygular.  
  
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
  
 Aşağıdaki örnekte, tek `Square` bir etkinlikten oluşan bir iş <xref:System.Activities.WorkflowInvoker>akışı tanımı kullanılarak çağrılır.  
  
```csharp  
Dictionary<string, object> inputs = new Dictionary<string, object> {{ "Value", 5}};  
int result = WorkflowInvoker.Invoke(new Square(), inputs);  
Console.WriteLine("Result: {0}", result);  
```  
  
 İş akışı çağrıldığında, aşağıdaki çıktı konsola görüntülenir:  
  
 **Değeri squaring: 5**  
**Sonuç: 25**
