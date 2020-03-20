---
title: İş Akışı Yürütme Özellikleri
ms.date: 03/30/2017
ms.assetid: a50e088e-3a45-4267-bd51-1a3e6c2d246d
ms.openlocfilehash: 0f958e7e112bfddc2740c2605d446493f2d49010
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182659"
---
# <a name="workflow-execution-properties"></a>İş Akışı Yürütme Özellikleri
ClR, iş parçacığı yerel depolama (TLS) aracılığıyla her iş parçacığı için bir yürütme bağlamı tutar. Bu yürütme bağlamı, iş parçacığı kimliği, ortam hareketi ve adlandırılmış yuvalar gibi kullanıcı tanımlı iş parçacığı özelliklerine ek olarak geçerli izin kümesi gibi iyi bilinen iş parçacığı özelliklerini yönetir.  
  
 Doğrudan CLR'yi hedefleyen programların aksine, iş akışı programları hiyerarşik olarak iş parçacığı agnostik bir ortamda çalışan etkinliklerin ağaçlarıdır. Bu, standart TLS mekanizmalarının, belirli bir iş öğesi için kapsamda hangi bağlamın olduğunu belirlemek için doğrudan kullanılamayacağı anlamına gelir. Örneğin, iki paralel yürütme dalı farklı hareketler kullanabilir, ancak zamanlayıcı yürütmelerini aynı CLR iş parçacığı üzerinde bırakabilir.  
  
 İş akışı yürütme özellikleri, bir etkinliğin ortamına bağlamaya özgü özellikler eklemek için bir mekanizma sağlar. Bu, bir etkinliğin alt ağacı için hangi özelliklerin kapsamda olduğunu beyan etmesine olanak tanır ve ayrıca TLS'nin CLR nesneleri ile düzgün bir şekilde birlikte çalışması için TLS'yi kurmak ve yıkmak için kancalar sağlar.  
  
## <a name="creating-and-using-workflow-execution-properties"></a>İş Akışı Yürütme Özellikleri Oluşturma ve Kullanma  
 İş akışı yürütme özellikleri <xref:System.Activities.IExecutionProperty> genellikle arabirimi uygular, ancak <xref:System.ServiceModel.Activities.ISendMessageCallback> <xref:System.ServiceModel.Activities.IReceiveMessageCallback> iletiye odaklanmış özellikler yerine uygulanabilir. Bir iş akışı yürütme özelliği oluşturmak <xref:System.Activities.IExecutionProperty> için, arabirimi uygulayan <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> bir <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>sınıf oluşturmak ve üyeleri ve. Bu üyeler, herhangi bir alt etkinlik de dahil olmak üzere özelliği içeren etkinliğin her darbe sırasında iş parçacığı yerel depolama düzgün kurmak ve yıkmak için bir fırsat yürütme özelliği sağlar. Bu örnekte, `ConsoleColorProperty` bir . `Console.ForegroundColor`  
  
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
  
 Etkinlik yazarları bu özelliği, etkinliğin yürütülme geçersiz kılındırına kaydederek kullanabilir. Bu örnekte, `ConsoleColorScope` `ConsoleColorProperty` geçerli <xref:System.Activities.NativeActivityContext.Properties%2A> <xref:System.Activities.NativeActivityContext>.  
  
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
  
 Aktivitenin vücut çalışma bir darbe başladığında, <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> özelliğin yöntemi denir, ve işin nabzı <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> tamamlandığında, denir. Bu örnekte, üç dallı bir <xref:System.Activities.Statements.Parallel> etkinlik kullanan bir iş akışı oluşturulur. İlk iki dal `ConsoleColorScope` etkinliği kullanır ve üçüncü dal kullanmaz. Her üç dal <xref:System.Activities.Statements.WriteLine> da <xref:System.Activities.Statements.Delay> iki etkinlik ve bir etkinlik içerir. <xref:System.Activities.Statements.Parallel> Etkinlik yürütüldüğünde, dallarda bulunan etkinlikler ara sıra yürütülür, ancak her alt etkinlik yürütülürken doğru `ConsoleColorProperty`konsol rengi .  
  
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
  
 İş akışı çağrıldığızaman, aşağıdaki çıktı konsol penceresine yazılır.  
  
```console  
Start blue text.  
Start red text.  
Start default text.  
End blue text.  
End red text.  
End default text.  
```  
  
> [!NOTE]
> Önceki çıktıda gösterilmese de, konsol penceresindeki her metin satırı belirtilen renkte görüntülenir.  
  
 İş akışı yürütme özellikleri özel etkinlik yazarları tarafından kullanılabilir ve onlar da <xref:System.ServiceModel.Activities.CorrelationScope> ve <xref:System.Activities.Statements.TransactionScope> etkinlikler gibi etkinlikler için işleme yönetimi için mekanizma sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Activities.IExecutionProperty>
- <xref:System.Activities.IPropertyRegistrationCallback>
- <xref:System.Activities.RegistrationContext>
