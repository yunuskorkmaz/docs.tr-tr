---
title: İş Akışı Yürütme Özellikleri
ms.date: 03/30/2017
ms.assetid: a50e088e-3a45-4267-bd51-1a3e6c2d246d
ms.openlocfilehash: be9ae5924786ea1e23cc649034d927789c64e405
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293799"
---
# <a name="workflow-execution-properties"></a>İş Akışı Yürütme Özellikleri

İş parçacığı yerel depolaması (TLS) aracılığıyla CLR her iş parçacığı için bir yürütme bağlamı tutar. Bu yürütme bağlamı iş parçacığı kimliği, ortam işlemi ve geçerli izin kümesi gibi bilinen iş parçacığı özelliklerinin yanı sıra adlandırılmış yuvalar gibi Kullanıcı tanımlı iş parçacığı özelliklerine ek olarak yönetir.  
  
 Programların CLR 'yi doğrudan hedeflemesini, iş akışı programlarının aksine, iş parçacığı belirsiz bir ortamda yürütülen etkinliklerin hiyerarşik olarak kapsamlı ağaçları vardır. Bu, belirli bir iş öğesi için kapsamda hangi bağlamın olduğunu belirlemek üzere Standart TLS mekanizmalarının doğrudan kullanılamayacağını gösterir. Örneğin, yürütmenin iki paralel dalı farklı işlemler kullanabilir, ancak Zamanlayıcı, yürütmelerini aynı CLR iş parçacığı üzerinde ayırmada sağlayabilir.  
  
 İş akışı yürütme özellikleri, bir etkinliğin ortamına bağlama özgü özellikler eklemek için bir mekanizma sağlar. Bu, bir etkinliğin alt ağacı için kapsamda hangi özelliklerin olduğunu bildirme ve ayrıca CLR nesneleriyle düzgün şekilde birlikte çalışmak üzere TLS ayarlama ve test etme için kancalar sağladığını sağlar.  
  
## <a name="creating-and-using-workflow-execution-properties"></a>Iş akışı yürütme özellikleri oluşturma ve kullanma  

 İş akışı yürütme özellikleri genellikle <xref:System.Activities.IExecutionProperty> arabirimini uygular, ancak mesajlaşmaya odaklanan özellikler de uygulayabilir <xref:System.ServiceModel.Activities.ISendMessageCallback> ve <xref:System.ServiceModel.Activities.IReceiveMessageCallback> bunun yerine kullanılabilir. Bir iş akışı yürütme özelliği oluşturmak için, <xref:System.Activities.IExecutionProperty> arabirimini uygulayan ve üyeleri ve uygulayan bir sınıf oluşturun <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> . Bu Üyeler, tüm alt etkinlikler dahil olmak üzere, özelliği içeren etkinliğin her bir aşamasında iş parçacığı yerel depolama alanını düzgün bir şekilde ayarlama ve ayırma fırsatı ile yürütme özelliğini sağlar. Bu örnekte, ' ı `ConsoleColorProperty` ayarlayan oluşturulur `Console.ForegroundColor` .  
  
```csharp  
class ConsoleColorProperty : IExecutionProperty  
{  
    public const string Name = "ConsoleColorProperty";  
  
    ConsoleColor original;  
    ConsoleColor color;  
  
    public ConsoleColorProperty(ConsoleColor color)  
    {  
        this.color = color;  
    }  
  
    void IExecutionProperty.SetupWorkflowThread()  
    {  
        original = Console.ForegroundColor;  
        Console.ForegroundColor = color;  
    }  
  
    void IExecutionProperty.CleanupWorkflowThread()  
    {  
        Console.ForegroundColor = original;  
    }  
}  
```  
  
 Etkinlik yazarları bu özelliği etkinliğin yürütme geçersiz kılması ile kaydederek kullanabilir. Bu örnekte, öğesini `ConsoleColorScope` geçerli bir koleksiyonuna ekleyerek kaydeden bir etkinlik tanımlanmıştır `ConsoleColorProperty` <xref:System.Activities.NativeActivityContext.Properties%2A> <xref:System.Activities.NativeActivityContext> .  
  
```csharp  
public sealed class ConsoleColorScope : NativeActivity  
{  
    public ConsoleColorScope()  
        : base()  
    {  
    }  
  
    public ConsoleColor Color { get; set; }  
    public Activity Body { get; set; }  
  
    protected override void Execute(NativeActivityContext context)  
    {  
        context.Properties.Add(ConsoleColorProperty.Name, new ConsoleColorProperty(this.Color));  
  
        if (this.Body != null)  
        {  
            context.ScheduleActivity(this.Body);  
        }  
    }  
}  
```  
  
 Etkinliğin gövdesi bir iş darbesi başlattığında, <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> özelliğin yöntemi çağrılır ve iş darbesi tamamlandığında, <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> çağırılır. Bu örnekte, üç dalla bir etkinlik kullanan bir iş akışı oluşturulur <xref:System.Activities.Statements.Parallel> . İlk iki dal `ConsoleColorScope` etkinliği kullanır ve üçüncü dal değildir. Üç dal de iki etkinlik <xref:System.Activities.Statements.WriteLine> ve bir <xref:System.Activities.Statements.Delay> etkinlik içerir. <xref:System.Activities.Statements.Parallel>Etkinlik yürütüldüğünde, dallardaki etkinlikler araya eklemeli bir şekilde yürütülür, ancak her alt etkinlik her bir alt etkinlik tarafından çalıştırıldığında doğru konsol rengi tarafından uygulanır `ConsoleColorProperty` .  
  
```csharp  
Activity wf = new Parallel  
{  
    Branches =
    {  
        new ConsoleColorScope  
        {  
            Color = ConsoleColor.Blue,  
            Body = new Sequence  
            {  
                Activities =
                {  
                    new WriteLine  
                    {  
                        Text = "Start blue text."  
                    },  
                    new Delay  
                    {  
                        Duration = TimeSpan.FromSeconds(1)  
                    },  
                    new WriteLine  
                    {  
                        Text = "End blue text."  
                    }  
                }  
            }  
        },  
        new ConsoleColorScope  
        {  
            Color = ConsoleColor.Red,  
            Body = new Sequence  
            {  
                Activities =
                {  
                    new WriteLine  
                    {  
                        Text = "Start red text."  
                    },  
                    new Delay  
                    {  
                        Duration = TimeSpan.FromSeconds(1)  
                    },  
                    new WriteLine  
                    {  
                        Text = "End red text."  
                    }  
                }  
            }  
        },  
        new Sequence  
        {  
            Activities =
            {  
                new WriteLine  
                {  
                    Text = "Start default text."  
                },  
                new Delay  
                {  
                    Duration = TimeSpan.FromSeconds(1)  
                },  
                new WriteLine  
                {  
                    Text = "End default text."  
                }  
            }  
        }  
    }  
};  
  
WorkflowInvoker.Invoke(wf);  
```  
  
 İş akışı çağrıldığında, aşağıdaki çıktı konsol penceresine yazılır.  
  
```console  
Start blue text.  
Start red text.  
Start default text.  
End blue text.  
End red text.  
End default text.  
```  
  
> [!NOTE]
> Önceki çıktıda gösterilmese de, konsol penceresindeki her metin satırı, belirtilen renkte görüntülenir.  
  
 İş akışı yürütme özellikleri özel etkinlik yazarları tarafından kullanılabilir ve ayrıca, ve etkinlikleri gibi etkinlikler için tanıtıcı yönetimi mekanizmasını sağlar <xref:System.ServiceModel.Activities.CorrelationScope> <xref:System.Activities.Statements.TransactionScope> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Activities.IExecutionProperty>
- <xref:System.Activities.IPropertyRegistrationCallback>
- <xref:System.Activities.RegistrationContext>
