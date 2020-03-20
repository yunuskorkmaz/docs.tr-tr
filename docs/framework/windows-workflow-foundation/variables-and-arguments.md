---
title: Değişkenler ve Bağımsız Değişkenler
ms.date: 03/30/2017
ms.assetid: d03dbe34-5b2e-4f21-8b57-693ee49611b8
ms.openlocfilehash: f975f46a1858d204d12588f7570b7ea5a365e650
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182690"
---
# <a name="variables-and-arguments"></a>Değişkenler ve Bağımsız Değişkenler
Windows İş Akışı Temeli'nde (WF) değişkenler, verilerin ve bağımsız değişkenlerin depolanmasını temsil eder ve bir etkinliğin içine ve dışına veri akışını temsil eder. Bir etkinliğin bir dizi bağımsız değişkeni vardır ve bunlar etkinliğin imzasını yapar. Ayrıca, bir etkinlik, bir geliştiricinin iş akışının tasarımı sırasında değişkenler ekleyebileceği veya kaldırabileceği değişkenlerin listesini saklayabilir. Bir değer döndüren bir ifade kullanılarak bir bağımsız değişken bağlanır.  
  
## <a name="variables"></a>Değişkenler  
 Değişkenler veri depolama konumlarıdır. Değişkenler iş akışının tanımının bir parçası olarak bildirilir. Değişkenler çalışma zamanında değerleri alır ve bu değerler iş akışı örneğinin durumunun bir parçası olarak depolanır. Değişken tanımı değişkenin türünü ve isteğe bağlı olarak adı belirtir. Aşağıdaki kod, bir değişkenin nasıl bildirilen, bir <xref:System.Activities.Statements.Assign%601> etkinlik kullanarak bir değer atanın <xref:System.Activities.Statements.WriteLine> ve sonra bir etkinlik kullanarak konsola değerini nasıl gösterin.  
  
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
  
 Varsayılan değer ifadesi isteğe bağlı olarak değişken bildiriminin bir parçası olarak belirtilebilir. Değişkenler de değiştiriciler olabilir. Örneğin, bir değişken salt okunursa, salt <xref:System.Activities.VariableModifiers> okunur değiştirici uygulanabilir. Aşağıdaki örnekte, varsayılan değeri atanmış salt okunur değişken oluşturulur.  
  
```csharp  
// Define a read-only variable with a default value.  
Variable<string> var = new Variable<string>  
{  
    Default = "Hello World.",  
    Modifiers = VariableModifiers.ReadOnly  
};  
```  
  
## <a name="variable-scoping"></a>Değişken Kapsam  
 Bir değişkenin çalışma zamanındaki ömrü, onu bildiren etkinliğin ömrüne eşittir. Bir etkinlik tamamlandığında, değişkenleri temizlenir ve artık başvurulamaz.  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 Etkinlik yazarları, verilerin bir faaliyete giriş ve çıkış biçimini tanımlamak için bağımsız değişkenler kullanır. Her bağımsız değişkenin <xref:System.Activities.ArgumentDirection.In>belirli <xref:System.Activities.ArgumentDirection.Out>bir <xref:System.Activities.ArgumentDirection.InOut>yönü vardır: , , veya .  
  
 İş akışı çalışma süresi, veri hareketinin etkinliklere giriş ve çıkış zamanlaması hakkında aşağıdaki garantileri sağlar:  
  
1. Bir etkinlik yürütmeye başladığında, tüm giriş ve girdi/çıktı bağımsız değişkenlerinin değerleri hesaplanır. Örneğin, ne zaman <xref:System.Activities.Argument.Get%2A> çağrıldığına bakılmaksızın, döndürülen değer, `Execute`'' ' ' ' ' '  
  
2. Çağrıldığında, <xref:System.Activities.InOutArgument%601.Set%2A> çalışma zamanı değeri hemen ayarlar.  
  
3. Bağımsız değişkenler isteğe bağlı olarak belirtilebilir. <xref:System.Activities.Argument.EvaluationOrder%2A> <xref:System.Activities.Argument.EvaluationOrder%2A>bağımsız değişkenin değerlendirilme sırasını belirten sıfır tabanlı bir değerdir. Varsayılan olarak, bağımsız değişkenin değerlendirme sırası belirtilmemiş <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> tir ve değere eşittir. <xref:System.Activities.Argument.EvaluationOrder%2A> Bu bağımsız değişken için bir değerlendirme sırası belirtmek için sıfırdan büyük veya eşit bir değer ayarlayın. Windows İş Akışı Temeli, artan sırada belirli bir değerlendirme sırası ile bağımsız değişkenleri değerlendirir. Belirtilmemiş bir değerlendirme sırasına sahip bağımsız değişkenlerin, belirli bir değerlendirme sırasına sahip olanlardan önce değerlendirildiğini unutmayın.  
  
 Bir etkinlik yazarı, bağımsız değişkenlerini ortaya çıkarmak için güçlü bir şekilde yazılmış bir mekanizma kullanabilir. Bu, türü <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>ve <xref:System.Activities.InOutArgument%601>. Bu, bir etkinlik yazarının bir faaliyete giren ve çıkan verilerle ilgili belirli bir sözleşme oluşturmasına olanak tanır.  
  
### <a name="defining-the-arguments-on-an-activity"></a>Bir Etkinlikle Ilgili Bağımsız Değişkenleri Tanımlama  
 Bağımsız değişkenler, bir etkinlik üzerinde, <xref:System.Activities.InArgument%601>ve <xref:System.Activities.OutArgument%601> <xref:System.Activities.InOutArgument%601>. Aşağıdaki kod, kullanıcıya görüntülenmesi `Prompt` için bir dize alan ve kullanıcının yanıtını içeren bir dize döndüren bir etkinliğin bağımsız değişkenlerinin nasıl tanımlandığını gösterir.  
  
```csharp  
public class Prompt : Activity  
{  
    public InArgument<string> Text { get; set; }  
    public OutArgument<string> Response { get; set; }  
    // Rest of activity definition omitted.  
}  
```  
  
> [!NOTE]
> Tek bir değer döndüren etkinlikler <xref:System.Activities.Activity%601> <xref:System.Activities.NativeActivity%601>, <xref:System.Activities.CodeActivity%601>, veya . Bu etkinlikler, etkinliğin <xref:System.Activities.OutArgument%601> geri <xref:System.Activities.Activity%601.Result%2A> dönüş değerini içeren iyi tanımlanmış bir adlandırılmış.  
  
### <a name="using-variables-and-arguments-in-workflows"></a>İş Akışlarında Değişkenleri ve Bağımsızları Kullanma  
 Aşağıdaki örnek, değişkenlerin ve bağımsız değişkenlerin bir iş akışında nasıl kullanıldığını gösterir. İş akışı üç değişkeni bildiren bir `var1`dizidir: , `var2`ve `var3`. İş akışındaki ilk etkinlik, `Assign` değişkenin `var1` değerini değişkene `var2`atayan bir etkinliktir. Bunu, `var2` değişkenin `WriteLine` değerini yazdıran bir etkinlik izler. Sonraki değişkenin `Assign` `var2` değerini değişkene `var3`atayan başka bir etkinliktir. Son olarak `WriteLine` `var3` değişkenin değerini yazdıran başka bir etkinlik vardır. İlk `Assign` etkinlik, `InArgument<string>` `OutArgument<string>` etkinliğin bağımsız değişkenlerinin bağlaştırışlarını açıkça temsil eden nesneleri kullanır ve nesneler. `InArgument<string>`değer <xref:System.Activities.Statements.Assign.Value%2A> <xref:System.Activities.Statements.Assign%601> <xref:System.Activities.Statements.Assign.Value%2A> bağımsız değişkeni üzerinden aktiviteye aktığı için `OutArgument<string>` kullanılır ve <xref:System.Activities.Statements.Assign.To%2A> değer <xref:System.Activities.Statements.Assign.To%2A> bağımsız değişkenden değişkene aktığı için kullanılır. İkinci `Assign` etkinlik, örtük dökümleri kullanan daha kompakt ancak eşdeğer sözdizimi ile aynı şeyi gerçekleştirir. Etkinlikler `WriteLine` de kompakt sözdizimini kullanır.  
  
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
  
### <a name="using-variables-and-arguments-in-code-based-activities"></a>Kod Tabanlı Etkinliklerde Değişkenleri ve Bağımsız değişkenleri kullanma  
 Önceki örnekler, iş akışlarında ve bildirimsel etkinliklerde bağımsız değişkenlerin ve değişkenlerin nasıl kullanılacağını gösterir. Bağımsız değişkenler ve değişkenler de kod tabanlı etkinliklerde kullanılır. Kavramsal olarak kullanımı çok benzer. Değişkenler etkinlik içinde veri depolamayı temsil eder ve bağımsız değişkenler veri akışını etkinlik içine veya dışına temsil eder ve iş akışı yazarı tarafından iş akışı yazarı tarafından verilerin nereye veya nereden aktığını temsil eden diğer değişkenlere veya bağımsız değişkenlere bağlıdır. Bir etkinlikteki değişken veya bağımsız değişkenin değerini almak veya ayarlamak için, etkinliğin geçerli yürütme ortamını temsil eden bir etkinlik bağlamının kullanılması gerekir. Bu, iş <xref:System.Activities.CodeActivity%601.Execute%2A> akışı çalışma süresi tarafından etkinlik yöntemine aktarılır. Bu örnekte, `Add` iki <xref:System.Activities.ArgumentDirection.In> bağımsız değişkeni olan özel bir etkinlik tanımlanır. Bağımsız değişkenlerin değerine erişmek <xref:System.Activities.Argument.Get%2A> için yöntem kullanılır ve iş akışı çalışma zamanı tarafından geçirilen bağlam kullanılır.  
  
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
  
 Bağımsız değişkenler, değişkenler ve koddaki ifadelerle çalışma hakkında daha fazla bilgi için [bkz.](authoring-workflows-activities-and-expressions-using-imperative-code.md) [Required Arguments and Overload Groups](required-arguments-and-overload-groups.md)
