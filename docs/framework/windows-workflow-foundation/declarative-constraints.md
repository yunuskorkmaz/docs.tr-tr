---
title: Bildirim temelli kısıtlamaları
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67001ed1-7f4d-4ada-ae57-a31176901a53
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4406bbbe7780fabc8872718ca21e8d755ea85c59
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="declarative-constraints"></a><span data-ttu-id="214c6-102">Bildirim temelli kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="214c6-102">Declarative Constraints</span></span>
<span data-ttu-id="214c6-103">Bildirim temelli kısıtlamaları bir etkinlik ve diğer etkinlikler ilişkilerini için güçlü bir yöntem doğrulama sağlayın.</span><span class="sxs-lookup"><span data-stu-id="214c6-103">Declarative constraints provide a powerful method of validation for an activity and its relationships with other activities.</span></span> <span data-ttu-id="214c6-104">Kısıtlamaları yazma işlemi sırasında bir etkinlik için yapılandırılmış, ancak ek kısıtlamalar iş akışı ana bilgisayar tarafından da belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="214c6-104">Constraints are configured for an activity during the authoring process, but additional constraints can also be specified by the workflow host.</span></span> <span data-ttu-id="214c6-105">Bu konu, etkinlik doğrulama sağlamak için bildirim temelli kısıtlamaları kullanarak genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="214c6-105">This topic provides an overview of using declarative constraints to provide activity validation.</span></span>  
  
## <a name="using-declarative-constraints"></a><span data-ttu-id="214c6-106">Bildirim temelli kısıtlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="214c6-106">Using Declarative Constraints</span></span>  
 <span data-ttu-id="214c6-107">Kısıtlama Doğrulama mantığı içeren bir etkinliktir.</span><span class="sxs-lookup"><span data-stu-id="214c6-107">A constraint is an activity that contains validation logic.</span></span> <span data-ttu-id="214c6-108">Bu kısıtlama etkinlik, kod veya XAML yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="214c6-108">This constraint activity can be authored in code or in XAML.</span></span> <span data-ttu-id="214c6-109">Kısıtlama etkinlik oluşturulduktan sonra bu kısıtlamayı etkinlik yazarlar eklemek <xref:System.Activities.Activity.Constraints%2A> doğrulamak için etkinlik özellik veya kısıtlama kullanarak ek doğrulama sağlamak için kullandıkları <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> özelliği bir <xref:System.Activities.Validation.ValidationSettings> örneği .</span><span class="sxs-lookup"><span data-stu-id="214c6-109">After a constraint activity is created, activity authors add this constraint to the <xref:System.Activities.Activity.Constraints%2A> property of the activity to validate, or they use the constraint to provide additional validation by using the <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> property of a <xref:System.Activities.Validation.ValidationSettings> instance.</span></span> <span data-ttu-id="214c6-110">Doğrulama mantığını bir etkinliğin meta veri doğrulama gibi basit doğrulamaları oluşabilir, ancak kendi üst, alt ve eşdüzey etkinliklere geçerli etkinlik arasındaki ilişki dikkate alır doğrulama de gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="214c6-110">The validation logic can consist of simple validations such as validating an activity’s metadata, but it can also perform validation that takes into account the relationship of the current activity to its parent, children, and sibling activities.</span></span> <span data-ttu-id="214c6-111">Kısıtlamaları kullanarak varsayılan <xref:System.Activities.Validation.Constraint%601> etkinliği ve birkaç ek doğrulama etkinliği oluşturulmasını doğrulama hataları ve Uyarıları ile yardımcı olmak ve iş akışı ilgili etkinlikleri hakkında bilgi sağlamak için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="214c6-111">Constraints are authored by using the <xref:System.Activities.Validation.Constraint%601> activity, and several additional validation activities are provided to assist with the creation of validation errors and warnings and to provide information about related activities in the workflow.</span></span>  
  
### <a name="assertvalidation-and-addvalidationerror"></a><span data-ttu-id="214c6-112">AssertValidation ve AddValidationError</span><span class="sxs-lookup"><span data-stu-id="214c6-112">AssertValidation and AddValidationError</span></span>  
 <span data-ttu-id="214c6-113"><xref:System.Activities.Validation.AssertValidation> Etkinlik tarafından başvurulan ifadeyi değerlendirir kendi <xref:System.Activities.Validation.AssertValidation.Assertion%2A> özelliği ve ifade değerlendirilirse `false`, bir doğrulama hata veya uyarı eklenir <xref:System.Activities.Validation.ValidationResults>.</span><span class="sxs-lookup"><span data-stu-id="214c6-113">The <xref:System.Activities.Validation.AssertValidation> activity evaluates the expression referenced by its <xref:System.Activities.Validation.AssertValidation.Assertion%2A> property, and if the expression evaluates to `false`, a validation error or warning is added to the <xref:System.Activities.Validation.ValidationResults>.</span></span> <span data-ttu-id="214c6-114"><xref:System.Activities.Validation.AssertValidation.Message%2A> Özelliği doğrulama hatası açıklar ve <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> özelliği, doğrulama hatası bir hata veya uyarı olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="214c6-114">The <xref:System.Activities.Validation.AssertValidation.Message%2A> property describes the validation error and the <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> property indicates whether the validation failure is an error or a warning.</span></span> <span data-ttu-id="214c6-115">İçin varsayılan değer <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> olan `false`.</span><span class="sxs-lookup"><span data-stu-id="214c6-115">The default value for <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> is `false`.</span></span>  
  
 <span data-ttu-id="214c6-116">Aşağıdaki örnekte, bir doğrulama uyarısı döndüren bir kısıtlama bildirilmiş <xref:System.Activities.Activity.DisplayName%2A> etkinliğini Doğrulanmakta olan iki karakter veya daha az olduğu.</span><span class="sxs-lookup"><span data-stu-id="214c6-116">In the following example, a constraint is declared that returns a validation warning if the <xref:System.Activities.Activity.DisplayName%2A> of the activity being validated is two characters or less in length.</span></span> <span data-ttu-id="214c6-117">Genel tür parametresi için kullanılan <xref:System.Activities.Validation.Constraint%601> kısıtlaması tarafından doğrulandığından etkinlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="214c6-117">The generic type parameter used for <xref:System.Activities.Validation.Constraint%601> specifies the type of activity that is validated by the constraint.</span></span> <span data-ttu-id="214c6-118">Bu kısıtlamayı kullanan <xref:System.Activities.Activity> genel olarak yazın ve tüm etkinlik türlerini doğrulamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="214c6-118">This constraint uses <xref:System.Activities.Activity> as the generic type and can be used to validate all types of activities.</span></span>  
  
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
  
 <span data-ttu-id="214c6-119">Bir etkinliğin bu kısıtlamasını belirtmek amacıyla eklendiğinden <xref:System.Activities.Activity.Constraints%2A> etkinliğin aşağıdaki örnek kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="214c6-119">To specify this constraint for an activity, it is added to the <xref:System.Activities.Activity.Constraints%2A> of the activity, as shown in the following example code.</span></span>  
  
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
  
 <span data-ttu-id="214c6-120">Konak da bu kısıtlamanın etkinlikler için bir iş akışında kullanarak belirtebilirsiniz <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>, sonraki bölümde ele.</span><span class="sxs-lookup"><span data-stu-id="214c6-120">The host could also specify this constraint for activities in a workflow by using <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>, which is covered in the next section.</span></span>  
  
 <span data-ttu-id="214c6-121"><xref:System.Activities.Validation.AddValidationError> Etkinlik, bir ifadenin değerlendirmesine gerek kalmadan bir doğrulama hata veya uyarı oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="214c6-121">The <xref:System.Activities.Validation.AddValidationError> activity is used to generate a validation error or warning without requiring the evaluation of an expression.</span></span> <span data-ttu-id="214c6-122">Özelliklerini benzer <xref:System.Activities.Validation.AssertValidation> ve onu bir kısıtlamanın akış denetimi etkinlikleriyle birlikte gibi kullanılabilir <xref:System.Activities.Statements.If> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="214c6-122">Its properties are similar to <xref:System.Activities.Validation.AssertValidation> and it can be used in conjunction with flow control activities of a constraint such as the <xref:System.Activities.Statements.If> activity.</span></span>  
  
### <a name="workflow-relationship-activities"></a><span data-ttu-id="214c6-123">İş akışı ilişki etkinlikleri</span><span class="sxs-lookup"><span data-stu-id="214c6-123">Workflow Relationship Activities</span></span>  
 <span data-ttu-id="214c6-124">Birkaç doğrulama etkinliği kullanılabilir Doğrulanmakta olan etkinliği bağlantılı olarak iş akışındaki diğer etkinlikleri hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="214c6-124">Several validation activities are available that provide information about the other activities in the workflow in relation to the activity being validated.</span></span> <span data-ttu-id="214c6-125"><xref:System.Activities.Validation.GetParentChain> geçerli etkinliği Kök etkinlik arasındaki etkinliklerin tümünü içeren bir koleksiyon etkinliklerin döndürür.</span><span class="sxs-lookup"><span data-stu-id="214c6-125"><xref:System.Activities.Validation.GetParentChain> returns a collection of activities that contains all of the activities between the current activity and the root activity.</span></span> <span data-ttu-id="214c6-126"><xref:System.Activities.Validation.GetChildSubtree> bir özyinelemeli düzeninde alt etkinlikler içeren bir koleksiyon etkinliklerin sağlar ve <xref:System.Activities.Validation.GetWorkflowTree> tüm etkinlikler iş akışında alır.</span><span class="sxs-lookup"><span data-stu-id="214c6-126"><xref:System.Activities.Validation.GetChildSubtree> provides a collection of activities that contains the child activities in a recursive pattern, and <xref:System.Activities.Validation.GetWorkflowTree> gets all the activities in the workflow.</span></span>  
  
 <span data-ttu-id="214c6-127">Aşağıdaki örnekte [etkinlik ilişkileri doğrulama](../../../docs/framework/windows-workflow-foundation/samples/activity-relationships-validation.md) örnek, bir `CreateState` etkinlik tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="214c6-127">In the following example from the [Activity Relationships Validation](../../../docs/framework/windows-workflow-foundation/samples/activity-relationships-validation.md) sample, a `CreateState` activity is defined.</span></span> <span data-ttu-id="214c6-128">`CreateState` Etkinlik bulunan, içinde bir `CreateCountry` etkinliği ve `GetParent` yöntemi bu gereksinimini zorlar bir kısıtlama döndürür.</span><span class="sxs-lookup"><span data-stu-id="214c6-128">The `CreateState` activity must be contained within a `CreateCountry` activity, and the `GetParent` method returns a constraint that enforces this requirement.</span></span> <span data-ttu-id="214c6-129">`GetParent` kullanan <xref:System.Activities.Validation.GetParentChain> etkinlik ile birlikte bir <xref:System.Activities.Statements.ForEach%601> üst etkinliklerini incelemek için etkinlik `CreateState` gereksinim karşılanır belirlemek için etkinlik.</span><span class="sxs-lookup"><span data-stu-id="214c6-129">`GetParent` uses the <xref:System.Activities.Validation.GetParentChain> activity in conjunction with a <xref:System.Activities.Statements.ForEach%601> activity to inspect the parent activities of the `CreateState` activity to determine if the requirement is met.</span></span>  
  
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
  
 <span data-ttu-id="214c6-130">Daha fazla bilgi için bkz: Windows Workflow Foundation [doğrulama](../../../docs/framework/windows-workflow-foundation/samples/validation.md) örnekleri.</span><span class="sxs-lookup"><span data-stu-id="214c6-130">For more information, see the Windows Workflow Foundation [Validation](../../../docs/framework/windows-workflow-foundation/samples/validation.md) samples.</span></span>  
  
## <a name="additional-constraints"></a><span data-ttu-id="214c6-131">Ek sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="214c6-131">Additional Constraints</span></span>  
 <span data-ttu-id="214c6-132">İş akışı ana yazarları belirtebilirsiniz ek doğrulama kısıtlamaları etkinlikler için bir iş akışında kısıtlamaları oluşturarak ve bunları ekleme <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> sözlüğü bir <xref:System.Activities.Validation.ValidationSettings> örneği.</span><span class="sxs-lookup"><span data-stu-id="214c6-132">Workflow host authors can specify additional validation constraints for activities in a workflow by creating constraints and adding them to the <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> dictionary of a <xref:System.Activities.Validation.ValidationSettings> instance.</span></span> <span data-ttu-id="214c6-133">Her öğe <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> için etkinlik türünü içerir kısıtlamaları uygulanacak ve bu tür bir etkinlik için ek kısıtlamalar listesi.</span><span class="sxs-lookup"><span data-stu-id="214c6-133">Each item in <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> contains the type of activity for which the constraints apply and a list of the additional constraints for that type of activity.</span></span> <span data-ttu-id="214c6-134">Doğrulama için iş akışını çağrıldığında, her etkinlik türetilen sınıflar dahil olmak üzere belirtilen türde kısıtlamalar değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="214c6-134">When validation is invoked for the workflow, each activity of the specified type, including derived classes, evaluates the constraints.</span></span> <span data-ttu-id="214c6-135">Bu örnekte, `ActivityDisplayNameIsNotSetWarning` önceki bölümdeki kısıtlaması, bir iş akışındaki tüm etkinlikler için uygulanır.</span><span class="sxs-lookup"><span data-stu-id="214c6-135">In this example, the `ActivityDisplayNameIsNotSetWarning` constraint from the previous section is applied to all activities in a workflow.</span></span>  
  
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
  
 <span data-ttu-id="214c6-136">Varsa <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> özelliği <xref:System.Activities.Validation.ValidationSettings> olan `true`, yalnızca belirtilen ek kısıtlamalar doğrulama çağırarak çağrıldığında değerlendirilir sonra <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="214c6-136">If the <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> property of <xref:System.Activities.Validation.ValidationSettings> is `true`, then only the specified additional constraints are evaluated when validation is invoked by calling <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="214c6-137">Bu, belirli doğrulama yapılandırmaları için iş akışlarını incelemek için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="214c6-137">This can be useful for inspecting workflows for specific validation configurations.</span></span> <span data-ttu-id="214c6-138">Ancak iş akışı çağrıldığında iş akışı içinde yapılandırılmış doğrulama mantığını değerlendirilir ve başarılı bir şekilde başlamak iş akışı için geçmesi gereken unutmayın.</span><span class="sxs-lookup"><span data-stu-id="214c6-138">Note however that when the workflow is invoked, the validation logic configured in the workflow is evaluated and must pass for the workflow to successfully begin.</span></span> <span data-ttu-id="214c6-139">Doğrulama çağırma hakkında daha fazla bilgi için bkz: [çağırma etkinlik doğrulama](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md).</span><span class="sxs-lookup"><span data-stu-id="214c6-139">For more information about invoking validation, see [Invoking Activity Validation](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md).</span></span>
