---
title: İş akışı yürütme özellikleri
ms.date: 03/30/2017
ms.assetid: a50e088e-3a45-4267-bd51-1a3e6c2d246d
ms.openlocfilehash: 2681152ba89baa2f65d5402a8c8c9d872cadb65b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33518650"
---
# <a name="workflow-execution-properties"></a>İş akışı yürütme özellikleri
İş parçacığı yerel depolaması (TLS), her iş parçacığı için yürütme bağlamı CLR tutar. Bu yürütme bağlamı ortam işlem iş parçacığı kimliği gibi bilinen iş parçacığı özellikleri yönetir ve ayrıca gibi kullanıcı tanımlı iş parçacığı özellikleri için geçerli izni yuvaları adlı.  
  
 Doğrudan CLR hedefleme programlar, iş akışını bir iş parçacığı belirsiz ortamında yürütme etkinliklerin hiyerarşik olarak kapsamlı ağaçları programlardır. Bu, standart TLS mekanizmaları hangi bağlam belirli iş öğesi kapsamında olduğunu belirlemek için doğrudan kullanılamaz olduğu anlamına gelir. Örneğin, iki paralel yürütme dallarını farklı işlemler kullanabilir henüz Zamanlayıcı aynı CLR iş parçacığı üzerinde kendi yürütme Interleave.  
  
 İş akışı yürütme özellikleri bir etkinliğin ortama bağlam belirli özellikleri eklemek için bir mekanizma sağlar. Bu bir etkinlik bildirmek hangi özellikler kendi alt ağaç kapsamında ve ayrıca ayarlama ve CLR nesneleriyle birlikte düzgün çalışmak için TLS aşağı hattının kaldırılması kancaları sağlar sağlar.  
  
## <a name="creating-and-using-workflow-execution-properties"></a>Oluşturma ve iş akışı yürütme özellikleri kullanma  
 İş akışı yürütme özellikleri genellikle uygulama <xref:System.Activities.IExecutionProperty> mesajlaşmayı odaklı özellikleri uygulayabilir, arabirim <xref:System.ServiceModel.Activities.ISendMessageCallback> ve <xref:System.ServiceModel.Activities.IReceiveMessageCallback> yerine. Bir iş akışı yürütme özelliği oluşturmak için uygulayan bir sınıf oluşturun <xref:System.Activities.IExecutionProperty> arabirim ve üyeleri uygulayan <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> ve <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>. Bu üyeler yürütme özelliği düzgün şekilde ayarlayabilir ve her alt etkinlikler dahil olmak üzere bu özelliği içerir etkinliğin çalışma pulse sırasında iş parçacığı yerel depolaması ayırma olanağı sağlar. Bu örnekte, bir `ConsoleColorProperty` bu kümeleri oluşturulan `Console.ForegroundColor`.  
  
> [!NOTE]
>  Bu konudaki aşağıdaki kod örneği, dayanır [yürütme özellikleri](../../../docs/framework/windows-workflow-foundation/samples/execution-properties.md) örnek.  
  
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
  
 Etkinlik yazarlar, bu özellik içinde kaydederek kullanabilir etkinliğe ilişkin geçersiz kılma yürütün. Bu örnekte, bir `ConsoleColorScope` etkinliği kaydeden tanımlanır `ConsoleColorProperty` ekleyerek <xref:System.Activities.NativeActivityContext.Properties%2A> geçerli koleksiyonunu <xref:System.Activities.NativeActivityContext>.  
  
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
  
 Etkinliğin gövdesi, çalışmanın pulse başladığında <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> özelliğinin yöntemi çağrılır ve pulse iş tamamlandığında, <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> olarak adlandırılır. Bu örnekte, bir iş akışı kullanan oluşturulur bir <xref:System.Activities.Statements.Parallel> üç dalları etkinlikle. İlk iki dalları kullanma `ConsoleColorScope` etkinliği ve üçüncü dalı desteklemez. Tüm üç iki dalları <xref:System.Activities.Statements.WriteLine> etkinlikleri ve <xref:System.Activities.Statements.Delay> etkinlik. Zaman <xref:System.Activities.Statements.Parallel> etkinlik yürütür, bir araya eklemeli şekilde dallarda içerdiği etkinlikleri yürütmek, ancak her alt etkinlik yürütür gibi doğru konsol renk tarafından uygulanan `ConsoleColorProperty`.  
  
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
  
 İş akışı çağrıldığında, aşağıdaki çıkış konsol penceresine yazılır.  
  
```  
Start blue text.  
Start red text.  
Start default text.  
End blue text.  
End red text.  
End default text.  
```  
  
> [!NOTE]
>  Önceki çıktısında gösterilmese de, her konsol penceresinde metin satırının belirtilen renkte görüntülenir.  
  
 İş akışı yürütme özellikleri özel etkinlik yazarlar tarafından kullanılabilir ve ayrıca tanıtıcısı yönetimi etkinlikleri için mekanizması gibi sağlarlar <xref:System.ServiceModel.Activities.CorrelationScope> ve <xref:System.Activities.Statements.TransactionScope> etkinlikler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Activities.IExecutionProperty>  
 <xref:System.Activities.IPropertyRegistrationCallback>  
 <xref:System.Activities.RegistrationContext>
