---
title: İş akışı yürütme özellikleri
ms.date: 03/30/2017
ms.assetid: a50e088e-3a45-4267-bd51-1a3e6c2d246d
ms.openlocfilehash: 2b72782b4b9fef127e61bb22b7800740af1d8d2b
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48582076"
---
# <a name="workflow-execution-properties"></a>İş akışı yürütme özellikleri
İş parçacığı yerel depolama ile (TLS), her iş parçacığı için bir yürütme bağlamı CLR tutar. Bu yürütme bağlamı iş parçacığı kimliği, ortam işlem gibi bilinen iş parçacığı özellikleri yönetir ve geçerli izin ayrıca gibi kullanıcı tanımlı bir iş parçacığı özellikleri kümesine yuvaları adlı.  
  
 Doğrudan CLR'yi hedefleyen programlar farklı olarak, iş akışı hiyerarşik olarak kapsamlı bir iş parçacığı geçişte sorun yaşamaz ortamında yürütme etkinlikleri ağaçları programlardır. Bu, standart TLS mekanizmaları hangi bağlam belirli iş öğesi için kapsamda olduğunu belirlemek için doğrudan kullanılamaz anlamına gelir. Örneğin, farklı işlem yürütme iki paralel dallarından kullanabilir henüz Zamanlayıcı, aynı CLR iş parçacığı üzerinde yürütülmesi ayırma değeri.  
  
 İş akışı yürütme özellikleri etkinliğin ortama özgü özellikleri bağlam eklemek için bir mekanizma sağlar. Bu bir etkinlik bildirmek hangi özellikler, alt ağacı kapsamı içinde ve ayrıca ayarlama ve CLR nesnesi ile düzgün çalışmak için TLS aşağı bozmadan kancaları sağlar sağlar.  
  
## <a name="creating-and-using-workflow-execution-properties"></a>Oluşturma ve iş akışı yürütme özellikleri kullanma  
 İş akışı yürütme özellikleri genellikle uygulama <xref:System.Activities.IExecutionProperty> mesajlaşmayı odaklı özellikleri uygulayabilir, arabirim <xref:System.ServiceModel.Activities.ISendMessageCallback> ve <xref:System.ServiceModel.Activities.IReceiveMessageCallback> yerine. Bir iş akışı yürütme özelliği oluşturmak için uygulayan bir sınıf oluşturma <xref:System.Activities.IExecutionProperty> arabirim ve üyelerini uygulama <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> ve <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>. Bu üyeleri yürütme özelliği düzgün şekilde ayarlanır ve her pulse herhangi bir alt etkinlik dahil olmak üzere bu özelliği içeren etkinliğin çalışma sırasında iş parçacığı yerel depolama ayırma olanağı sağlar. Bu örnekte, bir `ConsoleColorProperty` bu kümeleri oluşturan `Console.ForegroundColor`.  
  
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
  
 Etkinlik yazarlar içinde kaydederek bu özelliği kullanabilir etkinliğin geçersiz kılma yürütün. Bu örnekte, bir `ConsoleColorScope` etkinliği kaydeden tanımlanır `ConsoleColorProperty` ekleyerek <xref:System.Activities.NativeActivityContext.Properties%2A> geçerli koleksiyonunu <xref:System.Activities.NativeActivityContext>.  
  
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
  
 Etkinliğin gövdesi bir pulse iş başlatıldığında <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> özelliğinin yöntemi çağrılır ve pulse iş tamamlandığında, <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> çağrılır. Bu örnekte, bir iş akışı kullanan oluşturulur bir <xref:System.Activities.Statements.Parallel> üç dallarıyla etkinlik. İlk iki dalları kullanma `ConsoleColorScope` etkinliği ve üçüncü dal desteklemez. Tüm üç iki dalları <xref:System.Activities.Statements.WriteLine> etkinlikleri ve <xref:System.Activities.Statements.Delay> etkinlik. Zaman <xref:System.Activities.Statements.Parallel> etkinliği yürütür, dalları yer alan faaliyetleri şekilde bir araya eklemeli yürütme, ancak her bir alt etkinlik yürütme sırasında doğru konsol renk tarafından uygulanır `ConsoleColorProperty`.  
  
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
  
 İş akışı çağrıldığında, konsol penceresinde aşağıdaki çıktıyı yazılır.  
  
```  
Start blue text.  
Start red text.  
Start default text.  
End blue text.  
End red text.  
End default text.  
```  
  
> [!NOTE]
>  Önceki çıktısında gösterilmese konsol penceresinde metnin her satırının belirtilen renkte görüntülenir.  
  
 İş akışı yürütme özellikleri özel etkinlik yazarları tarafından kullanılabilir ve ayrıca tanıtıcısı yönetimi etkinlikleri için bir mekanizma gibi sağlarlar <xref:System.ServiceModel.Activities.CorrelationScope> ve <xref:System.Activities.Statements.TransactionScope> etkinlikler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Activities.IExecutionProperty>  
 <xref:System.Activities.IPropertyRegistrationCallback>  
 <xref:System.Activities.RegistrationContext>
