---
title: Değişkenler ve Bağımsız Değişkenler
description: Bu makalede, veri depolamayı temsil eden değişkenler ve Iş akışı temeli içindeki bir etkinliğe/içinden veri akışını temsil eden bağımsız değişkenler açıklanmaktadır.
ms.date: 03/30/2017
ms.assetid: d03dbe34-5b2e-4f21-8b57-693ee49611b8
ms.openlocfilehash: 47b8a7bddc8c3a9a8427bcb3e93760a63e5fa976
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421312"
---
# <a name="variables-and-arguments"></a>Değişkenler ve Bağımsız Değişkenler
Windows Workflow Foundation (WF) içinde, değişkenler verilerin ve bağımsız değişkenlerin depolanmasını temsil eder. Etkinliğin bir dizi bağımsız değişkeni vardır ve etkinliğin imzasını yapar. Ayrıca, bir etkinlik, bir geliştiricinin iş akışının tasarımı sırasında değişkenler ekleyebileceği veya kaldırabileceği değişkenlerin bir listesini de koruyabilir. Bir bağımsız değişken, bir değer döndüren bir ifade kullanılarak bağlanır.  
  
## <a name="variables"></a>Değişkenler  
 Değişkenler, veriler için depolama konumlarıdır. Değişkenler, bir iş akışı tanımının parçası olarak belirtilir. Değişkenler çalışma zamanında değerleri alır ve bu değerler bir iş akışı örneği durumunun parçası olarak depolanır. Değişken tanımı, değişkenin türünü ve isteğe bağlı olarak adı belirtir. Aşağıdaki kod, bir değişkeni nasıl bildirecağınızı, bir etkinliği kullanarak bir değer atamayı <xref:System.Activities.Statements.Assign%601> ve sonra bir etkinliği kullanarak değerini konsola görüntülemeyi gösterir <xref:System.Activities.Statements.WriteLine> .  
  
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
  
 Varsayılan değer ifadesi, isteğe bağlı olarak bir değişken bildiriminin parçası olarak belirtilebilir. Değişkenler aynı zamanda değiştiricilere de sahip olabilir. Örneğin, bir değişken salt okunurdur, salt-okunurdur <xref:System.Activities.VariableModifiers> değiştiricisi uygulanabilir. Aşağıdaki örnekte, varsayılan değeri atanmış bir salt okunurdur.  
  
```csharp  
// Define a read-only variable with a default value.  
Variable<string> var = new Variable<string>  
{  
    Default = "Hello World.",  
    Modifiers = VariableModifiers.ReadOnly  
};  
```  
  
## <a name="variable-scoping"></a>Değişken kapsamı  
 Çalışma zamanında bir değişkenin ömrü, onu bildiren etkinliğin kullanım ömrüne eşittir. Bir etkinlik tamamlandığında, değişkenleri temizlenir ve artık başvurulamaz.  
  
## <a name="arguments"></a>Arguments  
 Etkinlik yazarları verilerin bir etkinliğin içine ve dışına nasıl akacağını tanımlamak için bağımsız değişkenler kullanır. Her bağımsız değişken belirtilen bir yöne sahiptir: <xref:System.Activities.ArgumentDirection.In> , <xref:System.Activities.ArgumentDirection.Out> , veya <xref:System.Activities.ArgumentDirection.InOut> .  
  
 İş akışı çalışma zamanı, verilerin taşınmasının ve etkinlik dışı bırakılmasının zamanlaması hakkında aşağıdaki garantisi sağlar:  
  
1. Bir etkinlik yürütülmeye başladığında, tüm giriş ve giriş/çıkış bağımsız değişkenlerinin değerleri hesaplanır. Örneğin, çağrıldığında ne olursa olsun <xref:System.Activities.Argument.Get%2A> döndürülen değer, çalışma zamanı tarafından, çağrısından önce hesaplanır `Execute` .  
  
2. <xref:System.Activities.InOutArgument%601.Set%2A>Çağrıldığında, çalışma zamanı değeri hemen ayarlanır.  
  
3. Bağımsız değişkenler, isteğe bağlı olarak belirli bir şekilde <xref:System.Activities.Argument.EvaluationOrder%2A> belirtilebilir. <xref:System.Activities.Argument.EvaluationOrder%2A>, bağımsız değişkenin değerlendirildiği sırayı belirten sıfır tabanlı bir değerdir. Varsayılan olarak, bağımsız değişkenin değerlendirme sırası belirtilmemiş ve <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> değere eşittir. <xref:System.Activities.Argument.EvaluationOrder%2A>Bu bağımsız değişken için bir değerlendirme sırası belirtmek üzere sıfıra eşit veya daha büyük bir değere ayarlayın. Windows Workflow Foundation, belirtilen değerlendirme sırasıyla bağımsız değişkenleri artan düzende değerlendirir. Belirtilmemiş bir değerlendirme siparişi olan bağımsız değişkenlerin, belirtilen değerlendirme sırasıyla hesaplanmadan önce değerlendirildiğini unutmayın.  
  
 Etkinlik yazarı bağımsız değişkenlerini göstermek için türü kesin belirlenmiş bir mekanizma kullanabilir. Bu,, ve türündeki Özellikler bildirerek yapılır <xref:System.Activities.InArgument%601> <xref:System.Activities.OutArgument%601> <xref:System.Activities.InOutArgument%601> . Bu, etkinlik yazarının bir etkinliğin içine ve dışına giden veriler hakkında belirli bir sözleşme kurmasını sağlar.  
  
### <a name="defining-the-arguments-on-an-activity"></a>Etkinlik üzerinde bağımsız değişkenleri tanımlama  
 Bağımsız değişkenler,, ve türünün özellikleri belirtilerek bir etkinlikte tanımlanabilir <xref:System.Activities.InArgument%601> <xref:System.Activities.OutArgument%601> <xref:System.Activities.InOutArgument%601> . Aşağıdaki kod, `Prompt` kullanıcıya göstermek için bir dizede geçen bir etkinliğin bağımsız değişkenlerinin nasıl tanımlanacağını gösterir ve kullanıcının yanıtını içeren bir dize döndürür.  
  
```csharp  
public class Prompt : Activity  
{  
    public InArgument<string> Text { get; set; }  
    public OutArgument<string> Response { get; set; }  
    // Rest of activity definition omitted.  
}  
```  
  
> [!NOTE]
> Tek bir değer döndüren etkinlikler <xref:System.Activities.Activity%601> , veya öğesinden türetilebilir <xref:System.Activities.NativeActivity%601> <xref:System.Activities.CodeActivity%601> . Bu etkinliklerin <xref:System.Activities.OutArgument%601> <xref:System.Activities.Activity%601.Result%2A> , etkinliğin dönüş değerini içeren iyi tanımlanmış bir adlandırılmış adı vardır.  
  
### <a name="using-variables-and-arguments-in-workflows"></a>Iş akışlarında değişkenleri ve bağımsız değişkenleri kullanma  
 Aşağıdaki örnek, bir iş akışında değişkenlerin ve bağımsız değişkenlerin nasıl kullanıldığını gösterir. İş akışı üç değişken bildiren bir dizidir: `var1` , `var2` ve `var3` . İş akışındaki ilk etkinlik, değişkenin `Assign` değerini değişkenine atayan bir etkinliktir `var1` `var2` . Bu, `WriteLine` değişkenin değerini yazdıran bir etkinlik izler `var2` . Next, değişkenin `Assign` değerini değişkenine atayan başka bir etkinliktir `var2` `var3` . Son olarak, `WriteLine` değişkenin değerini yazdıran başka bir etkinlik vardır `var3` . İlk `Assign` etkinlik kullanır `InArgument<string>` ve `OutArgument<string>` etkinliğin bağımsız değişkenlerinin bağlamalarını açıkça temsil eden nesneler. `InArgument<string>`, <xref:System.Activities.Statements.Assign.Value%2A> değeri <xref:System.Activities.Statements.Assign%601> bağımsız değişkeni aracılığıyla etkinliğe akdığı ve için kullanıldığı için kullanıldığından, değeri bağımsız değişkeni <xref:System.Activities.Statements.Assign.Value%2A> `OutArgument<string>` <xref:System.Activities.Statements.Assign.To%2A> <xref:System.Activities.Statements.Assign.To%2A> değişkenine akar. İkinci `Assign` etkinlik, daha fazla sıkıştırma ile aynı şeyi gerçekleştirir, ancak örtülü yayınları kullanan eşdeğer sözdizimi. `WriteLine`Etkinlikler Ayrıca Compact söz dizimini kullanır.  
  
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
  
### <a name="using-variables-and-arguments-in-code-based-activities"></a>Kod tabanlı etkinliklerde değişkenleri ve bağımsız değişkenleri kullanma  
 Önceki örneklerde, iş akışlarında ve bildirim temelli etkinliklerdeki bağımsız değişkenlerin ve değişkenlerin nasıl kullanılacağı gösterilmektedir. Bağımsız değişkenler ve değişkenler kod tabanlı etkinliklerde de kullanılır. Kavramsal olarak kullanım çok benzerdir. Değişkenler, etkinlik içindeki veri depolamayı temsil eder ve bağımsız değişkenler, etkinliğin veri akışını ve etkinlik akışını temsil eder ve iş akışı yazarı tarafından, verilerin nerede veya dışarı akışının bulunduğu yeri temsil eden iş akışındaki diğer değişkenlere veya bağımsız değişkenlere bağlanır. Bir etkinliğin bir değişkeninin veya bağımsız değişkeninin değerini almak veya ayarlamak için, etkinliğin geçerli yürütme ortamını temsil eden bir etkinlik bağlamı kullanılmalıdır. Bu, <xref:System.Activities.CodeActivity%601.Execute%2A> iş akışı çalışma zamanı tarafından etkinliğin yöntemine geçirilir. Bu örnekte, `Add` iki bağımsız değişkene sahip özel bir etkinlik tanımlanmıştır <xref:System.Activities.ArgumentDirection.In> . Bağımsız değişkenlerin değerine erişmek için, <xref:System.Activities.Argument.Get%2A> yöntemi kullanılır ve iş akışı çalışma zamanı tarafından geçirilen bağlam kullanılır.  
  
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
  
 Koddaki bağımsız değişkenlerle, değişkenlerle ve ifadelerde çalışma hakkında daha fazla bilgi için bkz. [using Iş akışları, etkinlikler ve deyimler Için kesinlik](authoring-workflows-activities-and-expressions-using-imperative-code.md) , zorunlu kod ve [gerekli bağımsız değişkenler ve aşırı yükleme grupları](required-arguments-and-overload-groups.md).
