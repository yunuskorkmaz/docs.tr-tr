---
title: Bildirim Temelli Kısıtlamalar
ms.date: 03/30/2017
ms.assetid: 67001ed1-7f4d-4ada-ae57-a31176901a53
ms.openlocfilehash: 9098a3d79337689fef6d37e4cccf3633d8128a10
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236461"
---
# <a name="declarative-constraints"></a><span data-ttu-id="cb4b1-102">Bildirim Temelli Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="cb4b1-102">Declarative Constraints</span></span>

<span data-ttu-id="cb4b1-103">Bildirime dayalı kısıtlamalar, bir etkinlik ve diğer etkinliklerle ilişkileri için güçlü bir doğrulama yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="cb4b1-103">Declarative constraints provide a powerful method of validation for an activity and its relationships with other activities.</span></span> <span data-ttu-id="cb4b1-104">Kısıtlamalar, yazma işlemi sırasında bir etkinlik için yapılandırılır, ancak iş akışı ana bilgisayarı tarafından ek kısıtlamalar da belirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="cb4b1-104">Constraints are configured for an activity during the authoring process, but additional constraints can also be specified by the workflow host.</span></span> <span data-ttu-id="cb4b1-105">Bu konu, etkinlik doğrulaması sağlamak için bildirim temelli kısıtlamaları kullanmaya genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="cb4b1-105">This topic provides an overview of using declarative constraints to provide activity validation.</span></span>  
  
## <a name="using-declarative-constraints"></a><span data-ttu-id="cb4b1-106">Bildirim temelli kısıtlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="cb4b1-106">Using Declarative Constraints</span></span>  

 <span data-ttu-id="cb4b1-107">Kısıtlama, doğrulama mantığını içeren bir etkinliktir.</span><span class="sxs-lookup"><span data-stu-id="cb4b1-107">A constraint is an activity that contains validation logic.</span></span> <span data-ttu-id="cb4b1-108">Bu kısıtlama etkinliği kodda veya XAML 'de yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="cb4b1-108">This constraint activity can be authored in code or in XAML.</span></span> <span data-ttu-id="cb4b1-109">Bir kısıtlama etkinliği oluşturulduktan sonra, etkinlik yazarları bu kısıtlamayı <xref:System.Activities.Activity.Constraints%2A> doğrulanacak etkinliğin özelliğine ekler veya <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> bir örneğin özelliğini kullanarak ek doğrulama sağlamak için kısıtlamayı kullanır <xref:System.Activities.Validation.ValidationSettings> .</span><span class="sxs-lookup"><span data-stu-id="cb4b1-109">After a constraint activity is created, activity authors add this constraint to the <xref:System.Activities.Activity.Constraints%2A> property of the activity to validate, or they use the constraint to provide additional validation by using the <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> property of a <xref:System.Activities.Validation.ValidationSettings> instance.</span></span> <span data-ttu-id="cb4b1-110">Doğrulama mantığı, bir etkinliğin meta verilerini doğrulama gibi basit Doğrulamalardan oluşabilir, ancak aynı zamanda geçerli etkinliğin üst, alt öğeleri ve eşdüzey etkinlikleriyle ilişkilerini hesaba alan doğrulama işlemini gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="cb4b1-110">The validation logic can consist of simple validations such as validating an activity’s metadata, but it can also perform validation that takes into account the relationship of the current activity to its parent, children, and sibling activities.</span></span> <span data-ttu-id="cb4b1-111">Kısıtlamalar etkinlik kullanılarak yazılır <xref:System.Activities.Validation.Constraint%601> ve doğrulama hatalarının ve uyarıların oluşturulmasına ve iş akışındaki ilgili etkinliklerle ilgili bilgiler sağlamaya yardımcı olmak için birkaç ek doğrulama etkinliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="cb4b1-111">Constraints are authored by using the <xref:System.Activities.Validation.Constraint%601> activity, and several additional validation activities are provided to assist with the creation of validation errors and warnings and to provide information about related activities in the workflow.</span></span>  
  
### <a name="assertvalidation-and-addvalidationerror"></a><span data-ttu-id="cb4b1-112">AssertValidation ve AddValidationError</span><span class="sxs-lookup"><span data-stu-id="cb4b1-112">AssertValidation and AddValidationError</span></span>  

 <span data-ttu-id="cb4b1-113"><xref:System.Activities.Validation.AssertValidation>Etkinlik, özelliği tarafından başvurulan ifadeyi değerlendirir <xref:System.Activities.Validation.AssertValidation.Assertion%2A> ve ifade olarak değerlendirilirse, `false` öğesine bir doğrulama hatası veya uyarı eklenir <xref:System.Activities.Validation.ValidationResults> .</span><span class="sxs-lookup"><span data-stu-id="cb4b1-113">The <xref:System.Activities.Validation.AssertValidation> activity evaluates the expression referenced by its <xref:System.Activities.Validation.AssertValidation.Assertion%2A> property, and if the expression evaluates to `false`, a validation error or warning is added to the <xref:System.Activities.Validation.ValidationResults>.</span></span> <span data-ttu-id="cb4b1-114"><xref:System.Activities.Validation.AssertValidation.Message%2A>Özelliği, doğrulama hatasını açıklar ve bu, <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> doğrulama hatasının bir hata mu yoksa bir uyarı mı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="cb4b1-114">The <xref:System.Activities.Validation.AssertValidation.Message%2A> property describes the validation error and the <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> property indicates whether the validation failure is an error or a warning.</span></span> <span data-ttu-id="cb4b1-115">İçin varsayılan değer <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> `false` .</span><span class="sxs-lookup"><span data-stu-id="cb4b1-115">The default value for <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> is `false`.</span></span>  
  
 <span data-ttu-id="cb4b1-116">Aşağıdaki örnekte, <xref:System.Activities.Activity.DisplayName%2A> doğrulanan etkinliğin iki karakter veya daha az uzunluğunda olması durumunda doğrulama uyarısı döndüren bir kısıtlama bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="cb4b1-116">In the following example, a constraint is declared that returns a validation warning if the <xref:System.Activities.Activity.DisplayName%2A> of the activity being validated is two characters or less in length.</span></span> <span data-ttu-id="cb4b1-117">İçin kullanılan genel tür parametresi, <xref:System.Activities.Validation.Constraint%601> kısıtlama tarafından doğrulanan etkinliğin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="cb4b1-117">The generic type parameter used for <xref:System.Activities.Validation.Constraint%601> specifies the type of activity that is validated by the constraint.</span></span> <span data-ttu-id="cb4b1-118">Bu kısıtlama <xref:System.Activities.Activity> genel tür olarak kullanır ve tüm etkinlik türlerini doğrulamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cb4b1-118">This constraint uses <xref:System.Activities.Activity> as the generic type and can be used to validate all types of activities.</span></span>  
  
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
  
 <span data-ttu-id="cb4b1-119">Bu kısıtlamayı bir etkinliğin belirlemek için, <xref:System.Activities.Activity.Constraints%2A> Aşağıdaki örnek kodda gösterildiği gibi, etkinliğin öğesine eklenir.</span><span class="sxs-lookup"><span data-stu-id="cb4b1-119">To specify this constraint for an activity, it is added to the <xref:System.Activities.Activity.Constraints%2A> of the activity, as shown in the following example code.</span></span>  
  
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
  
 <span data-ttu-id="cb4b1-120">Konak, bir <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> sonraki bölümde ele alınan bir iş akışındaki etkinlikler için bu kısıtlamayı da belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="cb4b1-120">The host could also specify this constraint for activities in a workflow by using <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>, which is covered in the next section.</span></span>  
  
 <span data-ttu-id="cb4b1-121"><xref:System.Activities.Validation.AddValidationError>Etkinlik, bir ifadenin değerlendirilmesi gerekmeden doğrulama hatası veya uyarı oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cb4b1-121">The <xref:System.Activities.Validation.AddValidationError> activity is used to generate a validation error or warning without requiring the evaluation of an expression.</span></span> <span data-ttu-id="cb4b1-122">Özellikleri öğesine benzerdir <xref:System.Activities.Validation.AssertValidation> ve etkinlik gibi bir kısıtlamanın akış denetim etkinlikleriyle birlikte kullanılabilir <xref:System.Activities.Statements.If> .</span><span class="sxs-lookup"><span data-stu-id="cb4b1-122">Its properties are similar to <xref:System.Activities.Validation.AssertValidation> and it can be used in conjunction with flow control activities of a constraint such as the <xref:System.Activities.Statements.If> activity.</span></span>
  
### <a name="workflow-relationship-activities"></a><span data-ttu-id="cb4b1-123">İş akışı Ilişki etkinlikleri</span><span class="sxs-lookup"><span data-stu-id="cb4b1-123">Workflow Relationship Activities</span></span>

<span data-ttu-id="cb4b1-124">Doğrulanmakta olan etkinliğe göre iş akışındaki diğer etkinlikler hakkında bilgi sağlayan çeşitli doğrulama etkinlikleri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="cb4b1-124">Several validation activities are available that provide information about the other activities in the workflow in relation to the activity being validated.</span></span> <span data-ttu-id="cb4b1-125"><xref:System.Activities.Validation.GetParentChain> geçerli etkinlik ve kök etkinlik arasındaki tüm etkinlikleri içeren etkinliklerin bir koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="cb4b1-125"><xref:System.Activities.Validation.GetParentChain> returns a collection of activities that contains all of the activities between the current activity and the root activity.</span></span> <span data-ttu-id="cb4b1-126"><xref:System.Activities.Validation.GetChildSubtree> özyinelemeli bir düzende alt etkinlikleri içeren etkinliklerin bir koleksiyonunu sağlar ve <xref:System.Activities.Validation.GetWorkflowTree> iş akışındaki tüm etkinlikleri alır.</span><span class="sxs-lookup"><span data-stu-id="cb4b1-126"><xref:System.Activities.Validation.GetChildSubtree> provides a collection of activities that contains the child activities in a recursive pattern, and <xref:System.Activities.Validation.GetWorkflowTree> gets all the activities in the workflow.</span></span>  
  
<span data-ttu-id="cb4b1-127">Aşağıdaki örnekte bir `CreateState` etkinlik tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="cb4b1-127">In the following example, a `CreateState` activity is defined.</span></span> <span data-ttu-id="cb4b1-128">`CreateState`Etkinlik bir etkinliğin içinde yer almalıdır `CreateCountry` ve `GetParent` yöntemi bu gereksinimi zorlayan bir kısıtlama döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="cb4b1-128">The `CreateState` activity must be contained within a `CreateCountry` activity, and the `GetParent` method returns a constraint that enforces this requirement.</span></span> <span data-ttu-id="cb4b1-129">`GetParent` Etkinliğin <xref:System.Activities.Validation.GetParentChain> <xref:System.Activities.Statements.ForEach%601> `CreateState` karşılanıp karşılanmadığını öğrenmek için etkinliğin ana etkinliklerini incelemek üzere etkinliği bir etkinlikle birlikte kullanır.</span><span class="sxs-lookup"><span data-stu-id="cb4b1-129">`GetParent` uses the <xref:System.Activities.Validation.GetParentChain> activity in conjunction with a <xref:System.Activities.Statements.ForEach%601> activity to inspect the parent activities of the `CreateState` activity to determine if the requirement is met.</span></span>  
  
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
  
## <a name="additional-constraints"></a><span data-ttu-id="cb4b1-130">Ek kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="cb4b1-130">Additional Constraints</span></span>  

 <span data-ttu-id="cb4b1-131">İş akışı konak yazarları, kısıtlamalar oluşturarak ve bunları bir örnek sözlüğüne ekleyerek bir iş akışındaki etkinlikler için ek doğrulama kısıtlamaları belirtebilir <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> <xref:System.Activities.Validation.ValidationSettings> .</span><span class="sxs-lookup"><span data-stu-id="cb4b1-131">Workflow host authors can specify additional validation constraints for activities in a workflow by creating constraints and adding them to the <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> dictionary of a <xref:System.Activities.Validation.ValidationSettings> instance.</span></span> <span data-ttu-id="cb4b1-132">İçindeki her öğe <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> , kısıtlamaların uygulandığı etkinlik türünü ve bu tür bir etkinlik için ek kısıtlamaların bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="cb4b1-132">Each item in <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> contains the type of activity for which the constraints apply and a list of the additional constraints for that type of activity.</span></span> <span data-ttu-id="cb4b1-133">İş akışı için doğrulama çağrıldığında, türetilmiş sınıflar da dahil olmak üzere, belirtilen türden her etkinlik, kısıtlamaları değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="cb4b1-133">When validation is invoked for the workflow, each activity of the specified type, including derived classes, evaluates the constraints.</span></span> <span data-ttu-id="cb4b1-134">Bu örnekte, `ActivityDisplayNameIsNotSetWarning` önceki bölümdeki kısıtlama bir iş akışındaki tüm etkinliklere uygulanır.</span><span class="sxs-lookup"><span data-stu-id="cb4b1-134">In this example, the `ActivityDisplayNameIsNotSetWarning` constraint from the previous section is applied to all activities in a workflow.</span></span>  
  
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
  
 <span data-ttu-id="cb4b1-135"><xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A>Özelliği <xref:System.Activities.Validation.ValidationSettings> ise `true` , doğrulama çağrıldığında yalnızca belirtilen ek kısıtlamalar değerlendirilir <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> .</span><span class="sxs-lookup"><span data-stu-id="cb4b1-135">If the <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> property of <xref:System.Activities.Validation.ValidationSettings> is `true`, then only the specified additional constraints are evaluated when validation is invoked by calling <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="cb4b1-136">Bu, belirli doğrulama yapılandırmalarının iş akışlarını incelemek için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="cb4b1-136">This can be useful for inspecting workflows for specific validation configurations.</span></span> <span data-ttu-id="cb4b1-137">Ancak iş akışı çağrıldığında, iş akışında yapılandırılan doğrulama mantığının değerlendirildiğini ve iş akışının başarıyla başlaması için geçmesi gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="cb4b1-137">Note however that when the workflow is invoked, the validation logic configured in the workflow is evaluated and must pass for the workflow to successfully begin.</span></span> <span data-ttu-id="cb4b1-138">Doğrulamayı çağırma hakkında daha fazla bilgi için bkz. [etkinlik doğrulamasını çağırma](invoking-activity-validation.md).</span><span class="sxs-lookup"><span data-stu-id="cb4b1-138">For more information about invoking validation, see [Invoking Activity Validation](invoking-activity-validation.md).</span></span>
