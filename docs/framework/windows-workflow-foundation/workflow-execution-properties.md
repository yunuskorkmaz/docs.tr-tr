---
title: İş Akışı Yürütme Özellikleri
ms.date: 03/30/2017
ms.assetid: a50e088e-3a45-4267-bd51-1a3e6c2d246d
ms.openlocfilehash: 87775ba6efb9ec26ed2445e1f9d0944c379ba04f
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988595"
---
# <a name="workflow-execution-properties"></a>İş Akışı Yürütme Özellikleri
İş parçacığı yerel depolaması (TLS) aracılığıyla CLR her iş parçacığı için bir yürütme bağlamı tutar. Bu yürütme bağlamı iş parçacığı kimliği, ortam işlemi ve geçerli izin kümesi gibi bilinen iş parçacığı özelliklerinin yanı sıra adlandırılmış yuvalar gibi Kullanıcı tanımlı iş parçacığı özelliklerine ek olarak yönetir.  
  
 Programların CLR 'yi doğrudan hedeflemesini, iş akışı programlarının aksine, iş parçacığı belirsiz bir ortamda yürütülen etkinliklerin hiyerarşik olarak kapsamlı ağaçları vardır. Bu, belirli bir iş öğesi için kapsamda hangi bağlamın olduğunu belirlemek üzere Standart TLS mekanizmalarının doğrudan kullanılamayacağını gösterir. Örneğin, yürütmenin iki paralel dalı farklı işlemler kullanabilir, ancak Zamanlayıcı, yürütmelerini aynı CLR iş parçacığı üzerinde ayırmada sağlayabilir.  
  
 İş akışı yürütme özellikleri, bir etkinliğin ortamına bağlama özgü özellikler eklemek için bir mekanizma sağlar. Bu, bir etkinliğin alt ağacı için kapsamda hangi özelliklerin olduğunu bildirme ve ayrıca CLR nesneleriyle düzgün şekilde birlikte çalışmak üzere TLS ayarlama ve test etme için kancalar sağladığını sağlar.  
  
## <a name="creating-and-using-workflow-execution-properties"></a>Iş akışı yürütme özellikleri oluşturma ve kullanma  
 İş akışı yürütme özellikleri genellikle <xref:System.Activities.IExecutionProperty> arabirimini uygular, ancak mesajlaşmaya odaklanan özellikler de uygulayabilir <xref:System.ServiceModel.Activities.IReceiveMessageCallback> <xref:System.ServiceModel.Activities.ISendMessageCallback> ve bunun yerine kullanılabilir. Bir iş akışı yürütme özelliği oluşturmak için, <xref:System.Activities.IExecutionProperty> arabirimini uygulayan ve üyeleri <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> ve <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>uygulayan bir sınıf oluşturun. Bu Üyeler, tüm alt etkinlikler dahil olmak üzere, özelliği içeren etkinliğin her bir aşamasında iş parçacığı yerel depolama alanını düzgün bir şekilde ayarlama ve ayırma fırsatı ile yürütme özelliğini sağlar. Bu örnekte, ' ı `ConsoleColorProperty` `Console.ForegroundColor`ayarlayan oluşturulur.  
  
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
  
 Etkinlik yazarları bu özelliği etkinliğin yürütme geçersiz kılması ile kaydederek kullanabilir. Bu örnekte, öğesini geçerli `ConsoleColorScope` `ConsoleColorProperty` <xref:System.Activities.NativeActivityContext.Properties%2A> birkoleksiyonunaekleyerekkaydeden<xref:System.Activities.NativeActivityContext>bir etkinlik tanımlanmıştır.  
  
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
  
 Etkinliğin gövdesi bir iş <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> darbesi başlattığında, özelliğin yöntemi çağrılır ve iş darbesi tamamlandığında <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> , çağırılır. Bu örnekte, üç dalla bir <xref:System.Activities.Statements.Parallel> etkinlik kullanan bir iş akışı oluşturulur. İlk iki dal `ConsoleColorScope` etkinliği kullanır ve üçüncü dal değildir. Üç dal de iki <xref:System.Activities.Statements.WriteLine> etkinlik ve bir <xref:System.Activities.Statements.Delay> etkinlik içerir. Etkinlik yürütüldüğünde, dallardaki etkinlikler araya eklemeli bir şekilde yürütülür, ancak her alt etkinlik her bir alt etkinlik `ConsoleColorProperty`tarafından çalıştırıldığında doğru konsol rengi tarafından uygulanır. <xref:System.Activities.Statements.Parallel>  
  
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
  
 İş akışı yürütme özellikleri özel etkinlik yazarları tarafından kullanılabilir ve ayrıca, <xref:System.ServiceModel.Activities.CorrelationScope> ve <xref:System.Activities.Statements.TransactionScope> etkinlikleri gibi etkinlikler için tanıtıcı yönetimi mekanizmasını sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Activities.IExecutionProperty>
- <xref:System.Activities.IPropertyRegistrationCallback>
- <xref:System.Activities.RegistrationContext>
