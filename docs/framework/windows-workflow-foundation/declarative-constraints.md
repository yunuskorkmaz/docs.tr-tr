---
title: Bildirim temelli kısıtlamalar
ms.date: 03/30/2017
ms.assetid: 67001ed1-7f4d-4ada-ae57-a31176901a53
ms.openlocfilehash: e3ced8f6f88d698273ace5c8b74fe90b94fa9720
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708160"
---
# <a name="declarative-constraints"></a>Bildirim temelli kısıtlamalar
Bildirim temelli kısıtlamalar, güçlü bir doğrulama yöntemi için bir etkinlik ve ilişkilerini diğer etkinliklerle sunar. Kısıtlamalar için bir etkinlik yazma işlemi sırasında yapılandırılır, ancak ek kısıtlamaları, iş akışı ana bilgisayarı tarafından belirtilebilir. Bu konuda, etkinlik doğrulama sağlamak için bildirim temelli kısıtlamalar kullanarak genel bir bakış sağlar.  
  
## <a name="using-declarative-constraints"></a>Bildirim temelli kısıtlamalar kullanma  
 Kısıtlama Doğrulama mantığı içeren bir etkinliktir. Bu kısıtlama etkinlik, kod veya XAML yazılabilir. Kısıtlama etkinlik oluşturulduktan sonra bu kısıtlama için etkinlik yazarları ekleme <xref:System.Activities.Activity.Constraints%2A> doğrulamak için etkinliğin özelliği veya kısıtlama kullanarak ek doğrulama sağlamak için kullandıkları <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> özelliği bir <xref:System.Activities.Validation.ValidationSettings> örneği . Doğrulama mantığını etkinlik meta veri doğrulama gibi basit doğrulamaları oluşabilir, ancak üst, alt ve eşdüzey etkinlikleriyle için geçerli etkinlik arasındaki ilişkiyi dikkate doğrulama gerçekleştirebilirsiniz. Kısıtlamaları kullanılarak yazılır <xref:System.Activities.Validation.Constraint%601> etkinliği ve birkaç ek doğrulama etkinliği oluşturulmasını doğrulama hataları ve Uyarıları ile yardımcı ve iş akışındaki ilgili etkinlikler hakkında bilgi sağlamak için sağlanır.  
  
### <a name="assertvalidation-and-addvalidationerror"></a>AssertValidation ve AddValidationError  
 <xref:System.Activities.Validation.AssertValidation> Etkinliği tarafından başvurulan ifade değerlendirir, <xref:System.Activities.Validation.AssertValidation.Assertion%2A> özelliği ve ifade değerlendirme sonucu `false`, bir doğrulama hata veya uyarı eklenir <xref:System.Activities.Validation.ValidationResults>. <xref:System.Activities.Validation.AssertValidation.Message%2A> Özelliği doğrulama hatası açıklar ve <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> özelliği doğrulama hatası bir hata veya uyarı olup olmadığını gösterir. İçin varsayılan değer <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> olduğu `false`.  
  
 Aşağıdaki örnekte, bir kısıtlama döndüren bir doğrulama uyarısı, bildirilen <xref:System.Activities.Activity.DisplayName%2A> etkinliğini doğrulanması gereken iki karakter veya daha az olduğundan. Genel tür parametresi için kullanılan <xref:System.Activities.Validation.Constraint%601> kısıtlaması tarafından doğrulanır etkinlik türünü belirtir. Bu kısıtlama kullanan <xref:System.Activities.Activity> genel olarak yazın ve tüm etkinlik türleri doğrulamak için kullanılabilir.  
  
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
  
 Bir etkinlik için bu kısıtlamayı belirtmek için bu eklenir <xref:System.Activities.Activity.Constraints%2A> aşağıdaki örnekte gösterildiği gibi etkinliğin.  
  
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
  
 Konak da bu kısıtlamanın etkinlikleri için bir iş akışında kullanarak belirtebilirsiniz <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>, sonraki bölümde ele.  
  
 <xref:System.Activities.Validation.AddValidationError> Etkinliği, bir ifadenin değerlendirmesine gerek kalmadan bir doğrulama hata veya uyarı oluşturmak için kullanılır. Özellikleri benzer <xref:System.Activities.Validation.AssertValidation> ve birlikte bir kısıtlamaya akış denetimi etkinlikleri gibi kullanılmadan <xref:System.Activities.Statements.If> etkinlik.
  
### <a name="workflow-relationship-activities"></a>İş akışı ilişki etkinlikleri

Birkaç doğrulama etkinliği kullanılabilir iş akışı içinde Doğrulanmakta olan etkinliği ile ilgili diğer etkinlikler hakkında bilgi sağlar. <xref:System.Activities.Validation.GetParentChain> Geçerli etkinlik arasındaki Kök etkinlik etkinliklerin tümünü içeren etkinlikler koleksiyonunu döndürür. <xref:System.Activities.Validation.GetChildSubtree> bir özyinelemeli deseninde, çocuk etkinliklerinin içeren bir koleksiyon etkinliklerin sağlar ve <xref:System.Activities.Validation.GetWorkflowTree> tüm etkinlikler iş akışında alır.  
  
Aşağıdaki örnekte, bir `CreateState` etkinlik tanımlanır. `CreateState` Etkinlik bulunan, içinde bir `CreateCountry` etkinliği ve `GetParent` bu gereksinimini zorlar bir kısıtlama döner. `GetParent` kullanan <xref:System.Activities.Validation.GetParentChain> etkinlik ile birlikte bir <xref:System.Activities.Statements.ForEach%601> üst etkinliklerini İnceleme etkinliği `CreateState` bu gereksinimi karşılarsınız belirlemek için etkinlik.  
  
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
 İş akışı konak yazarları belirtebilirsiniz ek doğrulama kısıtlamalarını etkinlikler için bir iş akışında kısıtlamalar oluşturarak ve ekleyerek bunları <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> sözlüğü bir <xref:System.Activities.Validation.ValidationSettings> örneği. Her öğe <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> için etkinlik türünü içerir, kısıtlamalar uygulanır ve bu tür bir etkinlik için ek kısıtlamalar listesi. İş akışı için Doğrulama çağrıldığında belirtilen türün türetilen sınıflar da dahil olmak üzere her bir etkinlik kısıtlamaları değerlendirir. Bu örnekte, `ActivityDisplayNameIsNotSetWarning` kısıtlama önceki bölümde, iş akışındaki tüm etkinlikler için uygulanır.  
  
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
  
 Varsa <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> özelliği <xref:System.Activities.Validation.ValidationSettings> olduğu `true`, yalnızca belirtilen ek kısıtlamaları çağırarak Doğrulama çağrıldığında değerlendirilir sonra <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>. Bu, belirli bir doğrulama yapılandırmalar için iş akışları incelemek için yararlı olabilir. Ancak iş akışı çağrıldığında iş akışı içinde yapılandırılmış doğrulama mantığı değerlendirilir ve başarılı bir şekilde başlamak iş akışı için geçmesi gereken unutmayın. Doğrulamayı çağırma hakkında daha fazla bilgi için bkz. [etkinlik doğrulamayı çağırma](invoking-activity-validation.md).
