---
title: Bildirim Temelli Kısıtlamalar
ms.date: 03/30/2017
ms.assetid: 67001ed1-7f4d-4ada-ae57-a31176901a53
ms.openlocfilehash: 321021e3d73daecae07268f33807c992414a7b4c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182957"
---
# <a name="declarative-constraints"></a>Bildirim Temelli Kısıtlamalar
Bildirimsel kısıtlamalar, bir etkinlik ve diğer etkinliklerle ilişkileri için güçlü bir doğrulama yöntemi sağlar. Kısıtlamalar yazma işlemi sırasında bir etkinlik için yapılandırılır, ancak ek kısıtlamalar da iş akışı ana bilgisayar tarafından belirtilebilir. Bu konu, etkinlik doğrulaması sağlamak için bildirimsel kısıtlamaları kullanmaya genel bir bakış sağlar.  
  
## <a name="using-declarative-constraints"></a>Bildirimsel Kısıtlamaları Kullanma  
 Kısıtlama, doğrulama mantığı içeren bir etkinliktir. Bu kısıtlama etkinliği kod veya XAML olarak yazılabilir. Bir kısıtlama etkinliği oluşturulduktan sonra, etkinlik <xref:System.Activities.Activity.Constraints%2A> yazarları bu kısıtlamayı doğrulamak için etkinliğin özelliğine ekler veya <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> bir <xref:System.Activities.Validation.ValidationSettings> örneğin özelliğini kullanarak ek doğrulama sağlamak için kısıtlamayı kullanırlar. Doğrulama mantığı, bir etkinliğin meta verilerini doğrulamak gibi basit doğrulamalardan oluşabilir, ancak geçerli etkinliğin üst, alt ve kardeş etkinlikleriyle ilişkisini de hesaba katan doğrulama gerçekleştirebilir. Kısıtlamalar <xref:System.Activities.Validation.Constraint%601> etkinlik kullanılarak yazar ve doğrulama hataları ve uyarıların oluşturulmasına yardımcı olmak ve iş akışındaki ilgili etkinlikler hakkında bilgi sağlamak için birkaç ek doğrulama etkinliği sağlanır.  
  
### <a name="assertvalidation-and-addvalidationerror"></a>AssertValidation ve AddValidationError  
 Etkinlik, <xref:System.Activities.Validation.AssertValidation> <xref:System.Activities.Validation.AssertValidation.Assertion%2A> özelliği tarafından başvurulan ifadeyi değerlendirir ve ifade `false`değerlendirirse , bir doğrulama hatası <xref:System.Activities.Validation.ValidationResults>veya uyarı . Özellik <xref:System.Activities.Validation.AssertValidation.Message%2A> doğrulama hatasını açıklar <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> ve özellik doğrulama hatasının bir hata mı yoksa uyarı mı olduğunu gösterir. Varsayılan `false`değer. <xref:System.Activities.Validation.AssertValidation.IsWarning%2A>  
  
 Aşağıdaki örnekte, doğrulanan etkinliğin iki karakter veya <xref:System.Activities.Activity.DisplayName%2A> daha kısa uzunlukta olması durumunda bir doğrulama uyarısı döndüren bir kısıtlama bildirilir. Genel tür parametresi <xref:System.Activities.Validation.Constraint%601> kısıtlama tarafından doğrulanır etkinlik türünü belirtir. Bu kısıtlama <xref:System.Activities.Activity> genel tür olarak kullanır ve tüm etkinlik türlerini doğrulamak için kullanılabilir.  
  
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
  
 Bir etkinlik için bu kısıtlamayı belirtmek <xref:System.Activities.Activity.Constraints%2A> için, aşağıdaki örnek kodda gösterildiği gibi etkinliğin ekine eklenir.  
  
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
  
 Ana bilgisayar, bir sonraki bölümde kapsanan <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>bir iş akışındaki etkinlikler için bu kısıtlamayı da belirtebilir.  
  
 Etkinlik, <xref:System.Activities.Validation.AddValidationError> bir ifadenin değerlendirilmesi gerektirmeden bir doğrulama hatası veya uyarı oluşturmak için kullanılır. Özellikleri <xref:System.Activities.Validation.AssertValidation> benzerdir ve <xref:System.Activities.Statements.If> etkinlik gibi bir kısıtlamanın akış denetimi etkinlikleri ile birlikte kullanılabilir.
  
### <a name="workflow-relationship-activities"></a>İş Akışı İlişki Faaliyetleri

Doğrulanan etkinlikle ilgili olarak iş akışındaki diğer etkinlikler hakkında bilgi sağlayan çeşitli doğrulama etkinlikleri mevcuttur. <xref:System.Activities.Validation.GetParentChain>geçerli etkinlik ve kök etkinlik arasındaki tüm etkinlikleri içeren bir etkinlik koleksiyonunu döndürür. <xref:System.Activities.Validation.GetChildSubtree>özyinelemeli bir desende alt etkinlikleri içeren bir etkinlik koleksiyonu <xref:System.Activities.Validation.GetWorkflowTree> sağlar ve iş akışındaki tüm etkinlikleri alır.  
  
Aşağıdaki örnekte, `CreateState` bir etkinlik tanımlanır. Etkinlik `CreateState` bir `CreateCountry` etkinlik içinde içermelidir `GetParent` ve yöntem bu gereksinimi zorlayan bir kısıtlama döndürür. `GetParent`gereksinimin <xref:System.Activities.Validation.GetParentChain> karşılanıp <xref:System.Activities.Statements.ForEach%601> karşılanmadığını belirlemek için etkinlikçi bir etkinlikle birlikte kullanır. `CreateState`  
  
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
  
## <a name="additional-constraints"></a>Ek Kısıtlamalar  
 İş akışı ana bilgisayarı yazarları, kısıtlamalar oluşturarak ve bunları bir <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> <xref:System.Activities.Validation.ValidationSettings> örneğin sözlüğüne ekleyerek iş akışındaki etkinlikler için ek doğrulama kısıtlamaları belirtebilir. İçindeki <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> her öğe, kısıtlamaların uygulandığı etkinlik türünü ve bu tür bir etkinlik için ek kısıtlamaların listesini içerir. İş akışı için doğrulama çağrıldığında, türemiş sınıflar da dahil olmak üzere belirtilen türdeki her etkinlik kısıtlamaları değerlendirir. Bu örnekte, `ActivityDisplayNameIsNotSetWarning` önceki bölümdeki kısıtlama bir iş akışındaki tüm etkinliklere uygulanır.  
  
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
  
 Özelliği `true`ise, doğrulama <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>çağrıldığı zaman yalnızca belirtilen ek kısıtlamalar değerlendirilir. <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> <xref:System.Activities.Validation.ValidationSettings> Bu, belirli doğrulama yapılandırmaları için iş akışlarını denetlemek için yararlı olabilir. Ancak, iş akışı çağrıldığı zaman, iş akışında yapılandırılan doğrulama mantığının değerlendirildiğini ve iş akışının başarılı bir şekilde başlaması için geçmesi gerektiğini unutmayın. Doğrulama çağrısı hakkında daha fazla bilgi için [bkz.](invoking-activity-validation.md)
