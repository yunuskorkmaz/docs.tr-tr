---
description: 'Hakkında daha fazla bilgi edinin: bildirime dayalı kısıtlamalar'
title: Bildirim Temelli Kısıtlamalar
ms.date: 03/30/2017
ms.assetid: 67001ed1-7f4d-4ada-ae57-a31176901a53
ms.openlocfilehash: 7eeee5577e9c98db52af579749a59bc76a59b411
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742517"
---
# <a name="declarative-constraints"></a>Bildirim Temelli Kısıtlamalar

Bildirime dayalı kısıtlamalar, bir etkinlik ve diğer etkinliklerle ilişkileri için güçlü bir doğrulama yöntemi sağlar. Kısıtlamalar, yazma işlemi sırasında bir etkinlik için yapılandırılır, ancak iş akışı ana bilgisayarı tarafından ek kısıtlamalar da belirlenebilir. Bu konu, etkinlik doğrulaması sağlamak için bildirim temelli kısıtlamaları kullanmaya genel bir bakış sağlar.  
  
## <a name="using-declarative-constraints"></a>Bildirim temelli kısıtlamaları kullanma  

 Kısıtlama, doğrulama mantığını içeren bir etkinliktir. Bu kısıtlama etkinliği kodda veya XAML 'de yazılabilir. Bir kısıtlama etkinliği oluşturulduktan sonra, etkinlik yazarları bu kısıtlamayı <xref:System.Activities.Activity.Constraints%2A> doğrulanacak etkinliğin özelliğine ekler veya <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> bir örneğin özelliğini kullanarak ek doğrulama sağlamak için kısıtlamayı kullanır <xref:System.Activities.Validation.ValidationSettings> . Doğrulama mantığı, bir etkinliğin meta verilerini doğrulama gibi basit Doğrulamalardan oluşabilir, ancak aynı zamanda geçerli etkinliğin üst, alt öğeleri ve eşdüzey etkinlikleriyle ilişkilerini hesaba alan doğrulama işlemini gerçekleştirebilir. Kısıtlamalar etkinlik kullanılarak yazılır <xref:System.Activities.Validation.Constraint%601> ve doğrulama hatalarının ve uyarıların oluşturulmasına ve iş akışındaki ilgili etkinliklerle ilgili bilgiler sağlamaya yardımcı olmak için birkaç ek doğrulama etkinliği sağlanır.  
  
### <a name="assertvalidation-and-addvalidationerror"></a>AssertValidation ve AddValidationError  

 <xref:System.Activities.Validation.AssertValidation>Etkinlik, özelliği tarafından başvurulan ifadeyi değerlendirir <xref:System.Activities.Validation.AssertValidation.Assertion%2A> ve ifade olarak değerlendirilirse, `false` öğesine bir doğrulama hatası veya uyarı eklenir <xref:System.Activities.Validation.ValidationResults> . <xref:System.Activities.Validation.AssertValidation.Message%2A>Özelliği, doğrulama hatasını açıklar ve bu, <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> doğrulama hatasının bir hata mu yoksa bir uyarı mı olduğunu gösterir. İçin varsayılan değer <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> `false` .  
  
 Aşağıdaki örnekte, <xref:System.Activities.Activity.DisplayName%2A> doğrulanan etkinliğin iki karakter veya daha az uzunluğunda olması durumunda doğrulama uyarısı döndüren bir kısıtlama bildirilmiştir. İçin kullanılan genel tür parametresi, <xref:System.Activities.Validation.Constraint%601> kısıtlama tarafından doğrulanan etkinliğin türünü belirtir. Bu kısıtlama <xref:System.Activities.Activity> genel tür olarak kullanır ve tüm etkinlik türlerini doğrulamak için kullanılabilir.  
  
```csharp  
public static Constraint ActivityDisplayNameIsNotSetWarning()  
{  
    DelegateInArgument<Activity> element = new DelegateInArgument<Activity>();  
  
    return new Constraint<Activity>  
    {  
        Body = new ActivityAction<Activity, ValidationContext>  
        {  
            Argument1 = element,  
            Handler = new AssertValidation  
            {  
                IsWarning = true,  
                Assertion = new InArgument<bool>(env => (element.Get(env).DisplayName.Length > 2)),  
                Message = new InArgument<string>("It is a best practice to have a DisplayName of more than 2 characters."),  
            }  
        }  
    };  
}  
```  
  
 Bu kısıtlamayı bir etkinliğin belirlemek için, <xref:System.Activities.Activity.Constraints%2A> Aşağıdaki örnek kodda gösterildiği gibi, etkinliğin öğesine eklenir.  
  
```csharp  
public sealed class SampleActivity : CodeActivity  
{  
    public SampleActivity()  
    {  
        base.Constraints.Add(ActivityDisplayNameIsNotSetWarning());  
    }  
  
    // Activity implementation omitted.  
}  
```  
  
 Konak, bir <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> sonraki bölümde ele alınan bir iş akışındaki etkinlikler için bu kısıtlamayı da belirtebilir.  
  
 <xref:System.Activities.Validation.AddValidationError>Etkinlik, bir ifadenin değerlendirilmesi gerekmeden doğrulama hatası veya uyarı oluşturmak için kullanılır. Özellikleri öğesine benzerdir <xref:System.Activities.Validation.AssertValidation> ve etkinlik gibi bir kısıtlamanın akış denetim etkinlikleriyle birlikte kullanılabilir <xref:System.Activities.Statements.If> .
  
### <a name="workflow-relationship-activities"></a>İş akışı Ilişki etkinlikleri

Doğrulanmakta olan etkinliğe göre iş akışındaki diğer etkinlikler hakkında bilgi sağlayan çeşitli doğrulama etkinlikleri mevcuttur. <xref:System.Activities.Validation.GetParentChain> geçerli etkinlik ve kök etkinlik arasındaki tüm etkinlikleri içeren etkinliklerin bir koleksiyonunu döndürür. <xref:System.Activities.Validation.GetChildSubtree> özyinelemeli bir düzende alt etkinlikleri içeren etkinliklerin bir koleksiyonunu sağlar ve <xref:System.Activities.Validation.GetWorkflowTree> iş akışındaki tüm etkinlikleri alır.  
  
Aşağıdaki örnekte bir `CreateState` etkinlik tanımlanmıştır. `CreateState`Etkinlik bir etkinliğin içinde yer almalıdır `CreateCountry` ve `GetParent` yöntemi bu gereksinimi zorlayan bir kısıtlama döndürüyor. `GetParent` Etkinliğin <xref:System.Activities.Validation.GetParentChain> <xref:System.Activities.Statements.ForEach%601> `CreateState` karşılanıp karşılanmadığını öğrenmek için etkinliğin ana etkinliklerini incelemek üzere etkinliği bir etkinlikle birlikte kullanır.  
  
```csharp  
public sealed class CreateState : CodeActivity  
{  
    public CreateState()  
    {  
        base.Constraints.Add(CheckParent());  
        this.Cities = new List<Activity>();
    }  
  
    public List<Activity> Cities { get; set; }  
  
    public string Name { get; set; }
  
    static Constraint CheckParent()  
    {  
        DelegateInArgument<CreateState> element = new DelegateInArgument<CreateState>();  
        DelegateInArgument<ValidationContext> context = new DelegateInArgument<ValidationContext>();
        Variable<bool> result = new Variable<bool>();  
        DelegateInArgument<Activity> parent = new DelegateInArgument<Activity>();  
  
        return new Constraint<CreateState>  
        {
            Body = new ActivityAction<CreateState,ValidationContext>  
            {
                Argument1 = element,  
                Argument2 = context,  
                Handler = new Sequence  
                {  
                    Variables =  
                    {  
                        result
                    },  
                    Activities =  
                    {  
                        new ForEach<Activity>  
                        {
                            Values = new GetParentChain  
                            {  
                                ValidationContext = context
                            },  
                            Body = new ActivityAction<Activity>  
                            {
                                Argument = parent,
                                Handler = new If()  
                                {
                                    Condition = new InArgument<bool>((env) => object.Equals(parent.Get(env).GetType(),typeof(CreateCountry))),
                                    Then = new Assign<bool>  
                                    {  
                                        Value = true,  
                                        To = result  
                                    }  
                                }  
                            }
                        },  
                        new AssertValidation  
                        {  
                            Assertion = new InArgument<bool>(result),  
                            Message = new InArgument<string> ("CreateState has to be inside a CreateCountry activity"),
                        }  
                    }  
                }  
            }  
        };  
    }  
  
    protected override void Execute(CodeActivityContext context)  
    {  
        // not needed for the sample  
    }  
}  
```
  
## <a name="additional-constraints"></a>Ek kısıtlamalar  

 İş akışı konak yazarları, kısıtlamalar oluşturarak ve bunları bir örnek sözlüğüne ekleyerek bir iş akışındaki etkinlikler için ek doğrulama kısıtlamaları belirtebilir <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> <xref:System.Activities.Validation.ValidationSettings> . İçindeki her öğe <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> , kısıtlamaların uygulandığı etkinlik türünü ve bu tür bir etkinlik için ek kısıtlamaların bir listesini içerir. İş akışı için doğrulama çağrıldığında, türetilmiş sınıflar da dahil olmak üzere, belirtilen türden her etkinlik, kısıtlamaları değerlendirir. Bu örnekte, `ActivityDisplayNameIsNotSetWarning` önceki bölümdeki kısıtlama bir iş akışındaki tüm etkinliklere uygulanır.  
  
```csharp  
Activity wf = new Sequence  
{  
    // Workflow Details Omitted.  
};  
  
ValidationSettings settings = new ValidationSettings()  
{  
  
    AdditionalConstraints =  
    {  
        {typeof(Activity), new List<Constraint> {ActivityDisplayNameIsNotSetWarning()}},
    }  
};  
  
// Validate the workflow.  
ValidationResults results = ActivityValidationServices.Validate(wf, settings);  
  
// Evaluate the results.  
if (results.Errors.Count == 0 && results.Warnings.Count == 0)  
{  
    Console.WriteLine("No warnings or errors");  
}  
else  
{  
    foreach (ValidationError error in results.Errors)  
    {  
        Console.WriteLine("Error in " + error.Source.DisplayName + ": " + error.Message);  
    }  
    foreach (ValidationError warning in results.Warnings)  
    {  
        Console.WriteLine("Warning in " + warning.Source.DisplayName + ": " + warning.Message);  
    }  
}  
```  
  
 <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A>Özelliği <xref:System.Activities.Validation.ValidationSettings> ise `true` , doğrulama çağrıldığında yalnızca belirtilen ek kısıtlamalar değerlendirilir <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> . Bu, belirli doğrulama yapılandırmalarının iş akışlarını incelemek için yararlı olabilir. Ancak iş akışı çağrıldığında, iş akışında yapılandırılan doğrulama mantığının değerlendirildiğini ve iş akışının başarıyla başlaması için geçmesi gerektiğini unutmayın. Doğrulamayı çağırma hakkında daha fazla bilgi için bkz. [etkinlik doğrulamasını çağırma](invoking-activity-validation.md).
