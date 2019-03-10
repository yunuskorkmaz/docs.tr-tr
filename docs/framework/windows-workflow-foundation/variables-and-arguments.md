---
title: Değişkenler ve bağımsız değişkenler
ms.date: 03/30/2017
ms.assetid: d03dbe34-5b2e-4f21-8b57-693ee49611b8
ms.openlocfilehash: 6e534a54802228d6d001838008fc9d8f36fc0827
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57717823"
---
# <a name="variables-and-arguments"></a>Değişkenler ve bağımsız değişkenler
Windows Workflow Foundation (WF) değişkenleri temsil eden veri depolama ve küme içi ve dışı bir etkinlik bağımsız değişkenleri veri akışını temsil eder. Bağımsız değişken kümesinin bir etkinlik içerir ve bunlar etkinlik imzasını yapın. Ayrıca, bir etkinlik bir geliştirici ekleyebilir veya değişkenleri bir iş akışı tasarım sırasında kaldırma değişkenler listesini sağlayabilirsiniz. Bağımsız değişken bir değer döndüren bir ifade kullanarak bağlanır.  
  
## <a name="variables"></a>Değişkenler  
 Veri depolama konumları değişkenlerdir. Değişkenleri, bir iş akışının tanımını bir parçası olarak belirtilir. Değişken değerleri çalışma zamanında alır ve bu değerleri bir iş akışı örneği durumu bir parçası olarak depolanır. Değişken bir tanım değişkenini ve isteğe bağlı olarak ad türünü belirtir. Aşağıdaki kodu kullanarak bir değere bir değişken, Ata bildirmek gösterilmiştir bir <xref:System.Activities.Statements.Assign%601> etkinlik ve ardından Konsolu kullanarak değerinin görüntülendiğini bir <xref:System.Activities.Statements.WriteLine> etkinlik.  
  
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
  
 Varsayılan değer ifadesi bir değişken bildirimi bir parçası olarak isteğe bağlı olarak belirtilebilir. Değişkenleri de değiştiricilere sahip olabilir. Örneğin, bir değişken salt okunur ise ardından salt okunur <xref:System.Activities.VariableModifiers> değiştiricisi uygulanabilir. Aşağıdaki örnekte, atanmış bir varsayılan değere sahip bir salt okunur değişken oluşturulur.  
  
```csharp  
// Define a read-only variable with a default value.  
Variable<string> var = new Variable<string>  
{  
    Default = "Hello World.",  
    Modifiers = VariableModifiers.ReadOnly  
};  
```  
  
## <a name="variable-scoping"></a>Değişken kapsamı  
 Çalışma zamanında bir değişkenin ömrü, onu bildiren etkinlik ömrünü eşittir. Bir etkinlik tamamlandığında değişkenlerini temizlenir ve artık başvurulabilir.  
  
## <a name="arguments"></a>Arguments  
 Etkinlik yazarlar şekilde verileri tanımlamak için bağımsız değişkenler kullanın içine ve dışına Etkinlik Akışları. Belirtilen yönde her bağımsız değişkenlere sahiptir: <xref:System.Activities.ArgumentDirection.In>, <xref:System.Activities.ArgumentDirection.Out>, veya <xref:System.Activities.ArgumentDirection.InOut>.  
  
 İş akışı çalışma zamanı veri taşıma içine ve dışına etkinlikleri zamanlaması hakkında aşağıdakileri garantiler:  
  
1.  Bir etkinlik yürütme başlatıldığında, tüm giriş ve giriş/çıkış bağımsız değişkenlerinin değerlerini hesaplanır. Örneğin, ne zaman bakılmaksızın <xref:System.Activities.Argument.Get%2A> olan adlı bir hesaplanır kendi çağrılmasına önce çalışma zamanı tarafından döndürülen değer `Execute`.  
  
2.  Zaman <xref:System.Activities.InOutArgument%601.Set%2A> olan çağrılır, hemen değeri çalışma zamanı ayarlar.  
  
3.  Bağımsız değişken isteğe bağlı olarak olabilir, <xref:System.Activities.Argument.EvaluationOrder%2A> belirtilen. <xref:System.Activities.Argument.EvaluationOrder%2A> bağımsız değişken değerlendirilme sırasını belirleyen sıfır tabanlı bir değerdir. Varsayılan olarak, değerlendirme sırasında bağımsız değişken belirtilmezse ve eşittir <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> değeri. Ayarlama <xref:System.Activities.Argument.EvaluationOrder%2A> büyük veya bu bağımsız değişken için bir değerlendirme sırasını belirlemek için sıfıra eşit bir değer. Windows Workflow Foundation bir belirtilen değerlendirme sırası artan düzende bağımsız değişken değerlendirilir. Bağımsız değişkenlerle bir belirtilmeyen Değerlendirme sırasını belirtilen değerlendirme sırası olanlardan önce değerlendirildiğini unutmayın.  
  
 Bir etkinlik Yazar bağımsız değişkenlerinden açığa çıkarmak için kesin türü belirtilmiş bir mekanizma kullanabilirsiniz. Bu türün özelliklerini bildirerek gerçekleştirilir <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, ve <xref:System.Activities.InOutArgument%601>. Bu, küme içi ve dışı bir etkinlik giden verileri hakkında belirli bir sözleşme'kurmak bir etkinlik Yazar sağlar.  
  
### <a name="defining-the-arguments-on-an-activity"></a>Bir etkinlik bağımsız değişkenleri tanımlama  
 Bağımsız değişkenler tanımlanabilir bir etkinlik türünün özelliklerini belirterek <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, ve <xref:System.Activities.InOutArgument%601>. Aşağıdaki kod, bağımsız değişkenleri tanımlamak gösterilmiştir bir `Prompt` etkinliği kullanıcıya göstermek için bir dize alır ve kullanıcının yanıt içeren bir dize döndürür.  
  
```csharp  
public class Prompt : Activity  
{  
    public InArgument<string> Text { get; set; }  
    public OutArgument<string> Response { get; set; }  
    // Rest of activity definition omitted.  
}  
```  
  
> [!NOTE]
>  Tek bir değer döndürmesi etkinlikleri türeyebilir <xref:System.Activities.Activity%601>, <xref:System.Activities.NativeActivity%601>, veya <xref:System.Activities.CodeActivity%601>. Bu etkinlikler, iyi tanımlanmış olması <xref:System.Activities.OutArgument%601> adlı <xref:System.Activities.Activity%601.Result%2A> , etkinliğin dönüş değerini içerir.  
  
### <a name="using-variables-and-arguments-in-workflows"></a>İş akışlarında değişkenler ve bağımsız değişkenleri kullanma  
 Aşağıdaki örnek, değişkenler ve bağımsız değişkenleri bir iş akışında nasıl kullanılacağını gösterir. İş akışı üç değişkenler bildirilmektedir dizisidir: `var1`, `var2`, ve `var3`. İlk etkinlik iş akışında bir `Assign` değişkeninin değeri atar etkinlik `var1` değişkenine `var2`. Bu takip bir `WriteLine` değerini yazdırır etkinlik `var2` değişkeni. Başka bir sonraki olduğu `Assign` değişkeninin değeri atar etkinlik `var2` değişkenine `var3`. Son olarak yoktur başka `WriteLine` değerini yazdırır etkinlik `var3` değişkeni. İlk `Assign` etkinliği kullanan `InArgument<string>` ve `OutArgument<string>` bağlamaları etkinliğe ilişkin bağımsız değişkenler için açıkça temsil eden nesneleri. `InArgument<string>` için kullanılan <xref:System.Activities.Statements.Assign.Value%2A> değeri içine akar çünkü <xref:System.Activities.Statements.Assign%601> etkinlik aracılığıyla kendi <xref:System.Activities.Statements.Assign.Value%2A> bağımsız değişkeni, ve `OutArgument<string>` için kullanılan <xref:System.Activities.Statements.Assign.To%2A> değeri tanesi akan çünkü <xref:System.Activities.Statements.Assign.To%2A> bağımsız değişkeni olarak. İkinci `Assign` etkinlik daha aynı şeyi gerçekleştirir örtük yayınları kullanır ancak eşdeğer sözdizimi sıkıştırın. `WriteLine` Etkinlikleri de kısa sözdizimini kullanın.  
  
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
  
### <a name="using-variables-and-arguments-in-code-based-activities"></a>Değişkenler ve bağımsız değişkenler, kod tabanlı etkinlikleri kullanma  
 Önceki örneklerde, bağımsız değişkenleri ve iş akışları ve bildirim temelli etkinlikleri değişkenler nasıl kullanılacağını gösterir. Bağımsız değişkenler ve değişkenler, kod tabanlı etkinlikler de kullanılır. Kavramsal olarak kullanım çok benzer. Değişkenleri temsil eden etkinlik içinde veri depolama ve bağımsız değişkenler içine veya dışına etkinlik veri akışını temsil eden ve burada veya veri akışları temsil eden diğer değişkenleri veya iş akışı bağımsız değişkenler iş akışı yazar tarafından bağlı. GET veya değeri bir değişkene veya bağımsız bir etkinlik, bir etkinlik bağlamı içinde kullanılması gerekir kümesi, etkinliğin geçerli yürütme ortamını temsil eder. Yöntemlere geçirilen bu <xref:System.Activities.CodeActivity%601.Execute%2A> etkinlik iş akışı çalışma zamanı tarafından yöntemi. Bu örnekte, özel bir `Add` etkinlik iki içeren tanımlanır <xref:System.Activities.ArgumentDirection.In> bağımsız değişkenler. Bağımsız değişkenler değere erişmek için <xref:System.Activities.Argument.Get%2A> yöntemi kullanılır ve iş akışı çalışma zamanı tarafından geçirilen bağlamı kullanılır.  
  
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
  
 Bağımsız değişkenler, değişkenler ve ifadeleri kod ile çalışma hakkında daha fazla bilgi için bkz. [yazma iş akışları, etkinlikler ve ifadeler kullanarak kesinliği kod](authoring-workflows-activities-and-expressions-using-imperative-code.md) ve [gerekli bağımsız değişkenler ve aşırı grupları](required-arguments-and-overload-groups.md).
