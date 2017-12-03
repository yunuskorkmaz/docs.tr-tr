---
title: "Değişkenleri ve bağımsız değişkenler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d03dbe34-5b2e-4f21-8b57-693ee49611b8
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5f231a4e43723ce3ea73831086ed54e9ee08c1a0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="variables-and-arguments"></a>Değişkenleri ve bağımsız değişkenler
İçinde [!INCLUDE[wf](../../../includes/wf-md.md)]değişkenlerini temsil eden veri depolama ve bağımsız değişkenleri içine ve dışına aktivite veri akışını temsil eder. Bir etkinlik bir bağımsız değişkenler kümesine sahip ve etkinlik imza yapın. Ayrıca, aktivite Geliştirici ekleyebilir veya değişkenleri bir iş akışı tasarım sırasında kaldırma değişkenlerin listesini sağlayabilirsiniz. Bağımsız değişken bir değer döndüren bir ifadeye kullanarak bağlanır.  
  
## <a name="variables"></a>Değişkenler  
 Veri depolama konumları değişkenlerdir. Değişkenleri bir iş akışı tanımının bir parçası olarak bildirilir. Değerleri çalışma zamanında değişkenleri alın ve bu değerleri bir iş akışı örneğinin durumunu bir parçası olarak depolanır. Bir değişken tanımını değişkeni ve isteğe bağlı olarak, ad türünü belirtir. Aşağıdaki kod kullanarak bir değere bir değişken, Ata bildirmeyi gösterir bir <xref:System.Activities.Statements.Assign%601> etkinlik ve ardından konsol kullanmaya değerini görüntülemek bir <xref:System.Activities.Statements.WriteLine> etkinlik.  
  
```csharp  
// Define a variable named "str" of type string.  
Variable<string> var = new Variable<string>  
{  
    Name = "str"  
};  
  
// Declare the variable within a Sequence, assign  
// a value to it, and then display it.  
Activity wf = new Sequence()  
{  
    Variables = { var },  
    Activities =  
    {  
        new Assign<string>  
        {  
            To = var,  
            Value = "Hello World."  
        },  
        new WriteLine  
        {  
            Text = var  
        }  
    }  
};  
  
WorkflowInvoker.Invoke(wf);  
```  
  
 Varsayılan değer ifadesi bir değişken bildirimi bir parçası olarak isteğe bağlı olarak belirtilebilir. Değişkenleri değiştiricileri da sahip olabilirsiniz. Örneğin, bir değişken salt okunur ise sonra salt okunur için <xref:System.Activities.VariableModifiers> değiştiricisi uygulanabilir. Aşağıdaki örnekte, bir salt okunur değişken atanan varsayılan değer olan oluşturulur.  
  
```csharp  
// Define a read-only variable with a default value.  
Variable<string> var = new Variable<string>  
{  
    Default = "Hello World.",  
    Modifiers = VariableModifiers.ReadOnly  
};  
```  
  
## <a name="variable-scoping"></a>Değişken kapsamı  
 Çalışma zamanında bir değişken ömrü onu tanımlandığı etkinlik için kullanım ömrü eşittir. Bir etkinlik tamamlandığında değişkenlerini temizlenmesini ve artık başvurulabilir.  
  
## <a name="arguments"></a>Arguments  
 Etkinlik yazarlar şekilde verileri tanımlamak için bağımsız değişkenleri kullanma içine ve dışına bir etkinlik akışı. Belirtilen yöne her bağımsız değişkenlere sahiptir: <xref:System.Activities.ArgumentDirection.In>, <xref:System.Activities.ArgumentDirection.Out>, veya <xref:System.Activities.ArgumentDirection.InOut>.  
  
 İş akışı çalışma zamanı veri taşıma içine ve dışına etkinlikleri zamanlama hakkında aşağıdaki garantisi yapar:  
  
1.  Bir etkinlik yürütme başladığında, tüm giriş ve giriş/çıkış değişkenlerinin değerlerini hesaplanır. Örneğin, bağımsız olarak ne zaman <xref:System.Activities.Argument.Get%2A> olan adlı bir hesaplanan kendi çağrılması önce çalışma zamanı tarafından döndürülen değer `Execute`.  
  
2.  Zaman <xref:System.Activities.InOutArgument%601.Set%2A> olan çağrılmadan hemen değeri çalışma zamanı ayarlar.  
  
3.  Bağımsız değişkenler isteğe bağlı olarak olabilir kendi <xref:System.Activities.Argument.EvaluationOrder%2A> belirtilen. <xref:System.Activities.Argument.EvaluationOrder%2A>bağımsız değişken değerlendirildiği sırayı belirtir sıfır tabanlı bir değerdir. Varsayılan olarak bağımsız değişkenin değerlendirme sırası belirtilmezse, eşittir <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> değeri. Ayarlama <xref:System.Activities.Argument.EvaluationOrder%2A> bu bağımsız değişken için bir değerlendirme sıra belirtmek sıfıra eşit veya daha büyük bir değer. [!INCLUDE[wf2](../../../includes/wf2-md.md)]artan düzende belirtilen değerlendirme sırası değişkenleriyle değerlendirir. Belirtilmeyen değerlendirme sırası değişkenleriyle belirtilen değerlendirme sırası olanlar önce değerlendirildiğini unutmayın.  
  
 Bir etkinlik Yazar kesin türü belirtilmiş bir mekanizma değişkenlerinin gösterme için kullanabilirsiniz. Bu tür özelliklerini bildirerek gerçekleştirilir <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, ve <xref:System.Activities.InOutArgument%601>. Bu, belirli bir sözleşme içine ve dışına bir etkinlik giderek verilerle ilgili kurmak bir etkinlik Yazar sağlar.  
  
### <a name="defining-the-arguments-on-an-activity"></a>Bir etkinliği bağımsız değişkenleri tanımlama  
 Bağımsız değişkenler tanımlanabilir üzerinde bir etkinlik türünün özelliklerini belirterek <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, ve <xref:System.Activities.InOutArgument%601>. Aşağıdaki kod, bağımsız değişkenleri tanımlamak gösterilmiştir bir `Prompt` etkinliği kullanıcıya görüntülenecek bir dize alır ve kullanıcının yanıtı içeren bir dize döndürür.  
  
```csharp  
public class Prompt : Activity  
{  
    public InArgument<string> Text { get; set; }  
    public OutArgument<string> Response { get; set; }  
    // Rest of activity definition omitted.  
}  
```  
  
> [!NOTE]
>  Tek bir değer döndürmesi etkinlikler türetilen <xref:System.Activities.Activity%601>, <xref:System.Activities.NativeActivity%601>, veya <xref:System.Activities.CodeActivity%601>. Bu etkinlikler iyi tanımlanmış olması <xref:System.Activities.OutArgument%601> adlı <xref:System.Activities.Activity%601.Result%2A> etkinliğin dönüş değeri içerir.  
  
### <a name="using-variables-and-arguments-in-workflows"></a>İş akışlarında değişkenler ve bağımsız değişkenleri kullanma  
 Aşağıdaki örnek, değişkenler ve bağımsız değişkenleri bir iş akışında nasıl kullanıldığını gösterir. İş akışı üç değişkenleri bildiren bir dizidir: `var1`, `var2`, ve `var3`. İş akışındaki ilk etkinliği bir `Assign` değişkeninin değeri atar etkinlik `var1` değişkenine `var2`. Bu tarafından izlenir bir `WriteLine` değerini yazdırır etkinlik `var2` değişkeni. Sonraki başka olduğu `Assign` değişkeninin değeri atar etkinlik `var2` değişkenine `var3`. Son olarak olduğundan başka `WriteLine` değerini yazdırır etkinlik `var3` değişkeni. İlk `Assign` aktivitesi kullanır `InArgument<string>` ve `OutArgument<string>` açıkça etkinliğin bağımsız değişkenler için olan bağlamaları temsil eden nesne. `InArgument<string>`için kullanılan <xref:System.Activities.Statements.Assign.Value%2A> değeri içine akan çünkü <xref:System.Activities.Statements.Assign%601> etkinliği aracılığıyla kendi <xref:System.Activities.Statements.Assign.Value%2A> bağımsız değişkeni, ve `OutArgument<string>` için kullanılan <xref:System.Activities.Statements.Assign.To%2A> değeri dışı akan olduğundan <xref:System.Activities.Statements.Assign.To%2A> bağımsız değişkeni olarak. İkinci `Assign` etkinlik daha fazla ile aynı işlevi gerçekleştirir örtük atamaları kullanır ancak eşdeğer sözdizimi sıkıştırın. `WriteLine` Etkinlikleri de compact sözdizimini kullanın.  
  
```csharp  
// Declare three variables; the first one is given an initial value.  
Variable<string> var1 = new Variable<string>()  
{  
    Default = "one"  
};  
Variable<string> var2 = new Variable<string>();  
Variable<string> var3 = new Variable<string>();  
  
// Define the workflow  
Activity wf = new Sequence  
{  
    Variables = { var1, var2, var3 },  
    Activities =   
    {  
        new Assign<string>()  
        {  
            Value = new InArgument<string>(var1),  
            To = new OutArgument<string>(var2)  
        },  
        new WriteLine() { Text = var2 },  
        new Assign<string>()  
        {  
            Value = var2,  
            To = var3  
        },  
        new WriteLine() { Text = var3 }  
    }  
};  
  
WorkflowInvoker.Invoke(wf);  
```  
  
### <a name="using-variables-and-arguments-in-code-based-activities"></a>Değişken ve bağımsız değişkenler kod tabanlı etkinlikleri kullanma  
 Önceki örneklerde bağımsız ve iş akışları ve bildirim temelli etkinlikleri değişkenler nasıl kullanılacağını gösterir. Bağımsız değişkenler ve değişkenleri kod tabanlı etkinlikleri de kullanılır. Kavramsal kullanım çok benzer. Değişkenleri veri depolama etkinlik temsil eder ve bağımsız değişkenleri içine veya etkinlik dışı veri akışını temsil eder ve burada veriler veya akar temsil eden diğer değişkenleri veya bağımsız değişkenler iş akışı iş akışı yazarı tarafından bağlı. GET veya etkinliğin geçerli yürütme ortamı temsil eden bir değişken veya bir etkinlik, bir etkinlik bağlamı değişkeninde değerini kullanılmalıdır kümesi. Bu içine geçirilir <xref:System.Activities.CodeActivity%601.Execute%2A> etkinlik iş akışı çalışma zamanı tarafından yöntemi. Bu örnekte, özel bir `Add` etkinlik tanımlanmış iki sahip <xref:System.Activities.ArgumentDirection.In> bağımsız değişkenler. Bağımsız değişken değeri erişmek için <xref:System.Activities.Argument.Get%2A> yöntemi kullanılır ve iş akışı çalışma zamanı tarafından geçirilen bağlamı kullanılır.  
  
```csharp  
public sealed class Add : CodeActivity<int>  
{  
    [RequiredArgument]  
    public InArgument<int> Operand1 { get; set; }  
  
    [RequiredArgument]  
    public InArgument<int> Operand2 { get; set; }  
  
    protected override int Execute(CodeActivityContext context)  
    {  
        return Operand1.Get(context) + Operand2.Get(context);  
    }  
}  
```  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]bağımsız değişkenler, değişkenleri ve kodda ifadeleri ile çalışma, bkz: [geliştirme iş akışları, etkinlikler ve ifadeler kullanarak kesinliği kod](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md) ve [gerekli bağımsız değişkenleri ve aşırı grupları](../../../docs/framework/windows-workflow-foundation/required-arguments-and-overload-groups.md).
