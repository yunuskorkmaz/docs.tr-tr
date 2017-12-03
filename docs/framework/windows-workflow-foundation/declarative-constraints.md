---
title: "Bildirim temelli kısıtlamaları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 67001ed1-7f4d-4ada-ae57-a31176901a53
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a07b5d3b3451a9e5e29680fb74ea8411db6d11f7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="declarative-constraints"></a>Bildirim temelli kısıtlamaları
Bildirim temelli kısıtlamaları bir etkinlik ve diğer etkinlikler ilişkilerini için güçlü bir yöntem doğrulama sağlayın. Kısıtlamaları yazma işlemi sırasında bir etkinlik için yapılandırılmış, ancak ek kısıtlamalar iş akışı ana bilgisayar tarafından da belirtilebilir. Bu konu, etkinlik doğrulama sağlamak için bildirim temelli kısıtlamaları kullanarak genel bir bakış sağlar.  
  
## <a name="using-declarative-constraints"></a>Bildirim temelli kısıtlamaları kullanma  
 Kısıtlama Doğrulama mantığı içeren bir etkinliktir. Bu kısıtlama etkinlik, kod veya XAML yazılabilir. Kısıtlama etkinlik oluşturulduktan sonra bu kısıtlamayı etkinlik yazarlar eklemek <xref:System.Activities.Activity.Constraints%2A> doğrulamak için etkinlik özellik veya kısıtlama kullanarak ek doğrulama sağlamak için kullandıkları <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> özelliği bir <xref:System.Activities.Validation.ValidationSettings> örneği . Doğrulama mantığını bir etkinliğin meta veri doğrulama gibi basit doğrulamaları oluşabilir, ancak kendi üst, alt ve eşdüzey etkinliklere geçerli etkinlik arasındaki ilişki dikkate alır doğrulama de gerçekleştirebilirsiniz. Kısıtlamaları kullanarak varsayılan <xref:System.Activities.Validation.Constraint%601> etkinliği ve birkaç ek doğrulama etkinliği oluşturulmasını doğrulama hataları ve Uyarıları ile yardımcı olmak ve iş akışı ilgili etkinlikleri hakkında bilgi sağlamak için sağlanır.  
  
### <a name="assertvalidation-and-addvalidationerror"></a>AssertValidation ve AddValidationError  
 <xref:System.Activities.Validation.AssertValidation> Etkinlik tarafından başvurulan ifadeyi değerlendirir kendi <xref:System.Activities.Validation.AssertValidation.Assertion%2A> özelliği ve ifade değerlendirilirse `false`, bir doğrulama hata veya uyarı eklenir <xref:System.Activities.Validation.ValidationResults>. <xref:System.Activities.Validation.AssertValidation.Message%2A> Özelliği doğrulama hatası açıklar ve <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> özelliği, doğrulama hatası bir hata veya uyarı olup olmadığını belirtir. İçin varsayılan değer <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> olan `false`.  
  
 Aşağıdaki örnekte, bir doğrulama uyarısı döndüren bir kısıtlama bildirilmiş <xref:System.Activities.Activity.DisplayName%2A> etkinliğini Doğrulanmakta olan iki karakter veya daha az olduğu. Genel tür parametresi için kullanılan <xref:System.Activities.Validation.Constraint%601> kısıtlaması tarafından doğrulandığından etkinlik türünü belirtir. Bu kısıtlamayı kullanan <xref:System.Activities.Activity> genel olarak yazın ve tüm etkinlik türlerini doğrulamak için kullanılabilir.  
  
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
  
 Bir etkinliğin bu kısıtlamasını belirtmek amacıyla eklendiğinden <xref:System.Activities.Activity.Constraints%2A> etkinliğin aşağıdaki örnek kodda gösterildiği gibi.  
  
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
  
 Konak da bu kısıtlamanın etkinlikler için bir iş akışında kullanarak belirtebilirsiniz <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>, sonraki bölümde ele.  
  
 <xref:System.Activities.Validation.AddValidationError> Etkinlik, bir ifadenin değerlendirmesine gerek kalmadan bir doğrulama hata veya uyarı oluşturmak için kullanılır. Özelliklerini benzer <xref:System.Activities.Validation.AssertValidation> ve onu bir kısıtlamanın akış denetimi etkinlikleriyle birlikte gibi kullanılabilir <xref:System.Activities.Statements.If> etkinlik.  
  
### <a name="workflow-relationship-activities"></a>İş akışı ilişki etkinlikleri  
 Birkaç doğrulama etkinliği kullanılabilir Doğrulanmakta olan etkinliği bağlantılı olarak iş akışındaki diğer etkinlikleri hakkında bilgi sağlar. <xref:System.Activities.Validation.GetParentChain>geçerli etkinliği Kök etkinlik arasındaki etkinliklerin tümünü içeren bir koleksiyon etkinliklerin döndürür. <xref:System.Activities.Validation.GetChildSubtree>bir özyinelemeli düzeninde alt etkinlikler içeren bir koleksiyon etkinliklerin sağlar ve <xref:System.Activities.Validation.GetWorkflowTree> tüm etkinlikler iş akışında alır.  
  
 Aşağıdaki örnekte [etkinlik ilişkileri doğrulama](../../../docs/framework/windows-workflow-foundation/samples/activity-relationships-validation.md) örnek, bir `CreateState` etkinlik tanımlanır. `CreateState` Etkinlik bulunan, içinde bir `CreateCountry` etkinliği ve `GetParent` yöntemi bu gereksinimini zorlar bir kısıtlama döndürür. `GetParent`kullanan <xref:System.Activities.Validation.GetParentChain> etkinlik ile birlikte bir <xref:System.Activities.Statements.ForEach%601> üst etkinliklerini incelemek için etkinlik `CreateState` gereksinim karşılanır belirlemek için etkinlik.  
  
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
  
 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]Windows Workflow Foundation [doğrulama](../../../docs/framework/windows-workflow-foundation/samples/validation.md) örnekleri.  
  
## <a name="additional-constraints"></a>Ek sınırlamalar  
 İş akışı ana yazarları belirtebilirsiniz ek doğrulama kısıtlamaları etkinlikler için bir iş akışında kısıtlamaları oluşturarak ve bunları ekleme <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> sözlüğü bir <xref:System.Activities.Validation.ValidationSettings> örneği. Her öğe <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> için etkinlik türünü içerir kısıtlamaları uygulanacak ve bu tür bir etkinlik için ek kısıtlamalar listesi. Doğrulama için iş akışını çağrıldığında, her etkinlik türetilen sınıflar dahil olmak üzere belirtilen türde kısıtlamalar değerlendirir. Bu örnekte, `ActivityDisplayNameIsNotSetWarning` önceki bölümdeki kısıtlaması, bir iş akışındaki tüm etkinlikler için uygulanır.  
  
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
  
 Varsa <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> özelliği <xref:System.Activities.Validation.ValidationSettings> olan `true`, yalnızca belirtilen ek kısıtlamalar doğrulama çağırarak çağrıldığında değerlendirilir sonra <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>. Bu, belirli doğrulama yapılandırmaları için iş akışlarını incelemek için yararlı olabilir. Ancak iş akışı çağrıldığında iş akışı içinde yapılandırılmış doğrulama mantığını değerlendirilir ve başarılı bir şekilde başlamak iş akışı için geçmesi gereken unutmayın. [!INCLUDE[crabout](../../../includes/crabout-md.md)]doğrulama, çağırma bkz [çağırma etkinlik doğrulama](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md).
