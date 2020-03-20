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
# <a name="declarative-constraints"></a><span data-ttu-id="c62a6-102">Bildirim Temelli Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="c62a6-102">Declarative Constraints</span></span>
<span data-ttu-id="c62a6-103">Bildirimsel kısıtlamalar, bir etkinlik ve diğer etkinliklerle ilişkileri için güçlü bir doğrulama yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c62a6-103">Declarative constraints provide a powerful method of validation for an activity and its relationships with other activities.</span></span> <span data-ttu-id="c62a6-104">Kısıtlamalar yazma işlemi sırasında bir etkinlik için yapılandırılır, ancak ek kısıtlamalar da iş akışı ana bilgisayar tarafından belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="c62a6-104">Constraints are configured for an activity during the authoring process, but additional constraints can also be specified by the workflow host.</span></span> <span data-ttu-id="c62a6-105">Bu konu, etkinlik doğrulaması sağlamak için bildirimsel kısıtlamaları kullanmaya genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="c62a6-105">This topic provides an overview of using declarative constraints to provide activity validation.</span></span>  
  
## <a name="using-declarative-constraints"></a><span data-ttu-id="c62a6-106">Bildirimsel Kısıtlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="c62a6-106">Using Declarative Constraints</span></span>  
 <span data-ttu-id="c62a6-107">Kısıtlama, doğrulama mantığı içeren bir etkinliktir.</span><span class="sxs-lookup"><span data-stu-id="c62a6-107">A constraint is an activity that contains validation logic.</span></span> <span data-ttu-id="c62a6-108">Bu kısıtlama etkinliği kod veya XAML olarak yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="c62a6-108">This constraint activity can be authored in code or in XAML.</span></span> <span data-ttu-id="c62a6-109">Bir kısıtlama etkinliği oluşturulduktan sonra, etkinlik <xref:System.Activities.Activity.Constraints%2A> yazarları bu kısıtlamayı doğrulamak için etkinliğin özelliğine ekler veya <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> bir <xref:System.Activities.Validation.ValidationSettings> örneğin özelliğini kullanarak ek doğrulama sağlamak için kısıtlamayı kullanırlar.</span><span class="sxs-lookup"><span data-stu-id="c62a6-109">After a constraint activity is created, activity authors add this constraint to the <xref:System.Activities.Activity.Constraints%2A> property of the activity to validate, or they use the constraint to provide additional validation by using the <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> property of a <xref:System.Activities.Validation.ValidationSettings> instance.</span></span> <span data-ttu-id="c62a6-110">Doğrulama mantığı, bir etkinliğin meta verilerini doğrulamak gibi basit doğrulamalardan oluşabilir, ancak geçerli etkinliğin üst, alt ve kardeş etkinlikleriyle ilişkisini de hesaba katan doğrulama gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="c62a6-110">The validation logic can consist of simple validations such as validating an activity’s metadata, but it can also perform validation that takes into account the relationship of the current activity to its parent, children, and sibling activities.</span></span> <span data-ttu-id="c62a6-111">Kısıtlamalar <xref:System.Activities.Validation.Constraint%601> etkinlik kullanılarak yazar ve doğrulama hataları ve uyarıların oluşturulmasına yardımcı olmak ve iş akışındaki ilgili etkinlikler hakkında bilgi sağlamak için birkaç ek doğrulama etkinliği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="c62a6-111">Constraints are authored by using the <xref:System.Activities.Validation.Constraint%601> activity, and several additional validation activities are provided to assist with the creation of validation errors and warnings and to provide information about related activities in the workflow.</span></span>  
  
### <a name="assertvalidation-and-addvalidationerror"></a><span data-ttu-id="c62a6-112">AssertValidation ve AddValidationError</span><span class="sxs-lookup"><span data-stu-id="c62a6-112">AssertValidation and AddValidationError</span></span>  
 <span data-ttu-id="c62a6-113">Etkinlik, <xref:System.Activities.Validation.AssertValidation> <xref:System.Activities.Validation.AssertValidation.Assertion%2A> özelliği tarafından başvurulan ifadeyi değerlendirir ve ifade `false`değerlendirirse , bir doğrulama hatası <xref:System.Activities.Validation.ValidationResults>veya uyarı .</span><span class="sxs-lookup"><span data-stu-id="c62a6-113">The <xref:System.Activities.Validation.AssertValidation> activity evaluates the expression referenced by its <xref:System.Activities.Validation.AssertValidation.Assertion%2A> property, and if the expression evaluates to `false`, a validation error or warning is added to the <xref:System.Activities.Validation.ValidationResults>.</span></span> <span data-ttu-id="c62a6-114">Özellik <xref:System.Activities.Validation.AssertValidation.Message%2A> doğrulama hatasını açıklar <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> ve özellik doğrulama hatasının bir hata mı yoksa uyarı mı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="c62a6-114">The <xref:System.Activities.Validation.AssertValidation.Message%2A> property describes the validation error and the <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> property indicates whether the validation failure is an error or a warning.</span></span> <span data-ttu-id="c62a6-115">Varsayılan `false`değer. <xref:System.Activities.Validation.AssertValidation.IsWarning%2A></span><span class="sxs-lookup"><span data-stu-id="c62a6-115">The default value for <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> is `false`.</span></span>  
  
 <span data-ttu-id="c62a6-116">Aşağıdaki örnekte, doğrulanan etkinliğin iki karakter veya <xref:System.Activities.Activity.DisplayName%2A> daha kısa uzunlukta olması durumunda bir doğrulama uyarısı döndüren bir kısıtlama bildirilir.</span><span class="sxs-lookup"><span data-stu-id="c62a6-116">In the following example, a constraint is declared that returns a validation warning if the <xref:System.Activities.Activity.DisplayName%2A> of the activity being validated is two characters or less in length.</span></span> <span data-ttu-id="c62a6-117">Genel tür parametresi <xref:System.Activities.Validation.Constraint%601> kısıtlama tarafından doğrulanır etkinlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="c62a6-117">The generic type parameter used for <xref:System.Activities.Validation.Constraint%601> specifies the type of activity that is validated by the constraint.</span></span> <span data-ttu-id="c62a6-118">Bu kısıtlama <xref:System.Activities.Activity> genel tür olarak kullanır ve tüm etkinlik türlerini doğrulamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c62a6-118">This constraint uses <xref:System.Activities.Activity> as the generic type and can be used to validate all types of activities.</span></span>  
  
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
  
 <span data-ttu-id="c62a6-119">Bir etkinlik için bu kısıtlamayı belirtmek <xref:System.Activities.Activity.Constraints%2A> için, aşağıdaki örnek kodda gösterildiği gibi etkinliğin ekine eklenir.</span><span class="sxs-lookup"><span data-stu-id="c62a6-119">To specify this constraint for an activity, it is added to the <xref:System.Activities.Activity.Constraints%2A> of the activity, as shown in the following example code.</span></span>  
  
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
  
 <span data-ttu-id="c62a6-120">Ana bilgisayar, bir sonraki bölümde kapsanan <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>bir iş akışındaki etkinlikler için bu kısıtlamayı da belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="c62a6-120">The host could also specify this constraint for activities in a workflow by using <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>, which is covered in the next section.</span></span>  
  
 <span data-ttu-id="c62a6-121">Etkinlik, <xref:System.Activities.Validation.AddValidationError> bir ifadenin değerlendirilmesi gerektirmeden bir doğrulama hatası veya uyarı oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c62a6-121">The <xref:System.Activities.Validation.AddValidationError> activity is used to generate a validation error or warning without requiring the evaluation of an expression.</span></span> <span data-ttu-id="c62a6-122">Özellikleri <xref:System.Activities.Validation.AssertValidation> benzerdir ve <xref:System.Activities.Statements.If> etkinlik gibi bir kısıtlamanın akış denetimi etkinlikleri ile birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c62a6-122">Its properties are similar to <xref:System.Activities.Validation.AssertValidation> and it can be used in conjunction with flow control activities of a constraint such as the <xref:System.Activities.Statements.If> activity.</span></span>
  
### <a name="workflow-relationship-activities"></a><span data-ttu-id="c62a6-123">İş Akışı İlişki Faaliyetleri</span><span class="sxs-lookup"><span data-stu-id="c62a6-123">Workflow Relationship Activities</span></span>

<span data-ttu-id="c62a6-124">Doğrulanan etkinlikle ilgili olarak iş akışındaki diğer etkinlikler hakkında bilgi sağlayan çeşitli doğrulama etkinlikleri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="c62a6-124">Several validation activities are available that provide information about the other activities in the workflow in relation to the activity being validated.</span></span> <span data-ttu-id="c62a6-125"><xref:System.Activities.Validation.GetParentChain>geçerli etkinlik ve kök etkinlik arasındaki tüm etkinlikleri içeren bir etkinlik koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="c62a6-125"><xref:System.Activities.Validation.GetParentChain> returns a collection of activities that contains all of the activities between the current activity and the root activity.</span></span> <span data-ttu-id="c62a6-126"><xref:System.Activities.Validation.GetChildSubtree>özyinelemeli bir desende alt etkinlikleri içeren bir etkinlik koleksiyonu <xref:System.Activities.Validation.GetWorkflowTree> sağlar ve iş akışındaki tüm etkinlikleri alır.</span><span class="sxs-lookup"><span data-stu-id="c62a6-126"><xref:System.Activities.Validation.GetChildSubtree> provides a collection of activities that contains the child activities in a recursive pattern, and <xref:System.Activities.Validation.GetWorkflowTree> gets all the activities in the workflow.</span></span>  
  
<span data-ttu-id="c62a6-127">Aşağıdaki örnekte, `CreateState` bir etkinlik tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="c62a6-127">In the following example, a `CreateState` activity is defined.</span></span> <span data-ttu-id="c62a6-128">Etkinlik `CreateState` bir `CreateCountry` etkinlik içinde içermelidir `GetParent` ve yöntem bu gereksinimi zorlayan bir kısıtlama döndürür.</span><span class="sxs-lookup"><span data-stu-id="c62a6-128">The `CreateState` activity must be contained within a `CreateCountry` activity, and the `GetParent` method returns a constraint that enforces this requirement.</span></span> <span data-ttu-id="c62a6-129">`GetParent`gereksinimin <xref:System.Activities.Validation.GetParentChain> karşılanıp <xref:System.Activities.Statements.ForEach%601> karşılanmadığını belirlemek için etkinlikçi bir etkinlikle birlikte kullanır. `CreateState`</span><span class="sxs-lookup"><span data-stu-id="c62a6-129">`GetParent` uses the <xref:System.Activities.Validation.GetParentChain> activity in conjunction with a <xref:System.Activities.Statements.ForEach%601> activity to inspect the parent activities of the `CreateState` activity to determine if the requirement is met.</span></span>  
  
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
  
## <a name="additional-constraints"></a><span data-ttu-id="c62a6-130">Ek Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="c62a6-130">Additional Constraints</span></span>  
 <span data-ttu-id="c62a6-131">İş akışı ana bilgisayarı yazarları, kısıtlamalar oluşturarak ve bunları bir <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> <xref:System.Activities.Validation.ValidationSettings> örneğin sözlüğüne ekleyerek iş akışındaki etkinlikler için ek doğrulama kısıtlamaları belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="c62a6-131">Workflow host authors can specify additional validation constraints for activities in a workflow by creating constraints and adding them to the <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> dictionary of a <xref:System.Activities.Validation.ValidationSettings> instance.</span></span> <span data-ttu-id="c62a6-132">İçindeki <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> her öğe, kısıtlamaların uygulandığı etkinlik türünü ve bu tür bir etkinlik için ek kısıtlamaların listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="c62a6-132">Each item in <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> contains the type of activity for which the constraints apply and a list of the additional constraints for that type of activity.</span></span> <span data-ttu-id="c62a6-133">İş akışı için doğrulama çağrıldığında, türemiş sınıflar da dahil olmak üzere belirtilen türdeki her etkinlik kısıtlamaları değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="c62a6-133">When validation is invoked for the workflow, each activity of the specified type, including derived classes, evaluates the constraints.</span></span> <span data-ttu-id="c62a6-134">Bu örnekte, `ActivityDisplayNameIsNotSetWarning` önceki bölümdeki kısıtlama bir iş akışındaki tüm etkinliklere uygulanır.</span><span class="sxs-lookup"><span data-stu-id="c62a6-134">In this example, the `ActivityDisplayNameIsNotSetWarning` constraint from the previous section is applied to all activities in a workflow.</span></span>  
  
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
  
 <span data-ttu-id="c62a6-135">Özelliği `true`ise, doğrulama <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>çağrıldığı zaman yalnızca belirtilen ek kısıtlamalar değerlendirilir. <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> <xref:System.Activities.Validation.ValidationSettings></span><span class="sxs-lookup"><span data-stu-id="c62a6-135">If the <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> property of <xref:System.Activities.Validation.ValidationSettings> is `true`, then only the specified additional constraints are evaluated when validation is invoked by calling <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="c62a6-136">Bu, belirli doğrulama yapılandırmaları için iş akışlarını denetlemek için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="c62a6-136">This can be useful for inspecting workflows for specific validation configurations.</span></span> <span data-ttu-id="c62a6-137">Ancak, iş akışı çağrıldığı zaman, iş akışında yapılandırılan doğrulama mantığının değerlendirildiğini ve iş akışının başarılı bir şekilde başlaması için geçmesi gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c62a6-137">Note however that when the workflow is invoked, the validation logic configured in the workflow is evaluated and must pass for the workflow to successfully begin.</span></span> <span data-ttu-id="c62a6-138">Doğrulama çağrısı hakkında daha fazla bilgi için [bkz.](invoking-activity-validation.md)</span><span class="sxs-lookup"><span data-stu-id="c62a6-138">For more information about invoking validation, see [Invoking Activity Validation](invoking-activity-validation.md).</span></span>
