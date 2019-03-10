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
# <a name="declarative-constraints"></a><span data-ttu-id="8ca43-102">Bildirim temelli kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="8ca43-102">Declarative Constraints</span></span>
<span data-ttu-id="8ca43-103">Bildirim temelli kısıtlamalar, güçlü bir doğrulama yöntemi için bir etkinlik ve ilişkilerini diğer etkinliklerle sunar.</span><span class="sxs-lookup"><span data-stu-id="8ca43-103">Declarative constraints provide a powerful method of validation for an activity and its relationships with other activities.</span></span> <span data-ttu-id="8ca43-104">Kısıtlamalar için bir etkinlik yazma işlemi sırasında yapılandırılır, ancak ek kısıtlamaları, iş akışı ana bilgisayarı tarafından belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="8ca43-104">Constraints are configured for an activity during the authoring process, but additional constraints can also be specified by the workflow host.</span></span> <span data-ttu-id="8ca43-105">Bu konuda, etkinlik doğrulama sağlamak için bildirim temelli kısıtlamalar kullanarak genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="8ca43-105">This topic provides an overview of using declarative constraints to provide activity validation.</span></span>  
  
## <a name="using-declarative-constraints"></a><span data-ttu-id="8ca43-106">Bildirim temelli kısıtlamalar kullanma</span><span class="sxs-lookup"><span data-stu-id="8ca43-106">Using Declarative Constraints</span></span>  
 <span data-ttu-id="8ca43-107">Kısıtlama Doğrulama mantığı içeren bir etkinliktir.</span><span class="sxs-lookup"><span data-stu-id="8ca43-107">A constraint is an activity that contains validation logic.</span></span> <span data-ttu-id="8ca43-108">Bu kısıtlama etkinlik, kod veya XAML yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="8ca43-108">This constraint activity can be authored in code or in XAML.</span></span> <span data-ttu-id="8ca43-109">Kısıtlama etkinlik oluşturulduktan sonra bu kısıtlama için etkinlik yazarları ekleme <xref:System.Activities.Activity.Constraints%2A> doğrulamak için etkinliğin özelliği veya kısıtlama kullanarak ek doğrulama sağlamak için kullandıkları <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> özelliği bir <xref:System.Activities.Validation.ValidationSettings> örneği .</span><span class="sxs-lookup"><span data-stu-id="8ca43-109">After a constraint activity is created, activity authors add this constraint to the <xref:System.Activities.Activity.Constraints%2A> property of the activity to validate, or they use the constraint to provide additional validation by using the <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> property of a <xref:System.Activities.Validation.ValidationSettings> instance.</span></span> <span data-ttu-id="8ca43-110">Doğrulama mantığını etkinlik meta veri doğrulama gibi basit doğrulamaları oluşabilir, ancak üst, alt ve eşdüzey etkinlikleriyle için geçerli etkinlik arasındaki ilişkiyi dikkate doğrulama gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ca43-110">The validation logic can consist of simple validations such as validating an activity’s metadata, but it can also perform validation that takes into account the relationship of the current activity to its parent, children, and sibling activities.</span></span> <span data-ttu-id="8ca43-111">Kısıtlamaları kullanılarak yazılır <xref:System.Activities.Validation.Constraint%601> etkinliği ve birkaç ek doğrulama etkinliği oluşturulmasını doğrulama hataları ve Uyarıları ile yardımcı ve iş akışındaki ilgili etkinlikler hakkında bilgi sağlamak için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="8ca43-111">Constraints are authored by using the <xref:System.Activities.Validation.Constraint%601> activity, and several additional validation activities are provided to assist with the creation of validation errors and warnings and to provide information about related activities in the workflow.</span></span>  
  
### <a name="assertvalidation-and-addvalidationerror"></a><span data-ttu-id="8ca43-112">AssertValidation ve AddValidationError</span><span class="sxs-lookup"><span data-stu-id="8ca43-112">AssertValidation and AddValidationError</span></span>  
 <span data-ttu-id="8ca43-113"><xref:System.Activities.Validation.AssertValidation> Etkinliği tarafından başvurulan ifade değerlendirir, <xref:System.Activities.Validation.AssertValidation.Assertion%2A> özelliği ve ifade değerlendirme sonucu `false`, bir doğrulama hata veya uyarı eklenir <xref:System.Activities.Validation.ValidationResults>.</span><span class="sxs-lookup"><span data-stu-id="8ca43-113">The <xref:System.Activities.Validation.AssertValidation> activity evaluates the expression referenced by its <xref:System.Activities.Validation.AssertValidation.Assertion%2A> property, and if the expression evaluates to `false`, a validation error or warning is added to the <xref:System.Activities.Validation.ValidationResults>.</span></span> <span data-ttu-id="8ca43-114"><xref:System.Activities.Validation.AssertValidation.Message%2A> Özelliği doğrulama hatası açıklar ve <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> özelliği doğrulama hatası bir hata veya uyarı olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8ca43-114">The <xref:System.Activities.Validation.AssertValidation.Message%2A> property describes the validation error and the <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> property indicates whether the validation failure is an error or a warning.</span></span> <span data-ttu-id="8ca43-115">İçin varsayılan değer <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> olduğu `false`.</span><span class="sxs-lookup"><span data-stu-id="8ca43-115">The default value for <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> is `false`.</span></span>  
  
 <span data-ttu-id="8ca43-116">Aşağıdaki örnekte, bir kısıtlama döndüren bir doğrulama uyarısı, bildirilen <xref:System.Activities.Activity.DisplayName%2A> etkinliğini doğrulanması gereken iki karakter veya daha az olduğundan.</span><span class="sxs-lookup"><span data-stu-id="8ca43-116">In the following example, a constraint is declared that returns a validation warning if the <xref:System.Activities.Activity.DisplayName%2A> of the activity being validated is two characters or less in length.</span></span> <span data-ttu-id="8ca43-117">Genel tür parametresi için kullanılan <xref:System.Activities.Validation.Constraint%601> kısıtlaması tarafından doğrulanır etkinlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="8ca43-117">The generic type parameter used for <xref:System.Activities.Validation.Constraint%601> specifies the type of activity that is validated by the constraint.</span></span> <span data-ttu-id="8ca43-118">Bu kısıtlama kullanan <xref:System.Activities.Activity> genel olarak yazın ve tüm etkinlik türleri doğrulamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8ca43-118">This constraint uses <xref:System.Activities.Activity> as the generic type and can be used to validate all types of activities.</span></span>  
  
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
  
 <span data-ttu-id="8ca43-119">Bir etkinlik için bu kısıtlamayı belirtmek için bu eklenir <xref:System.Activities.Activity.Constraints%2A> aşağıdaki örnekte gösterildiği gibi etkinliğin.</span><span class="sxs-lookup"><span data-stu-id="8ca43-119">To specify this constraint for an activity, it is added to the <xref:System.Activities.Activity.Constraints%2A> of the activity, as shown in the following example code.</span></span>  
  
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
  
 <span data-ttu-id="8ca43-120">Konak da bu kısıtlamanın etkinlikleri için bir iş akışında kullanarak belirtebilirsiniz <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>, sonraki bölümde ele.</span><span class="sxs-lookup"><span data-stu-id="8ca43-120">The host could also specify this constraint for activities in a workflow by using <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>, which is covered in the next section.</span></span>  
  
 <span data-ttu-id="8ca43-121"><xref:System.Activities.Validation.AddValidationError> Etkinliği, bir ifadenin değerlendirmesine gerek kalmadan bir doğrulama hata veya uyarı oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8ca43-121">The <xref:System.Activities.Validation.AddValidationError> activity is used to generate a validation error or warning without requiring the evaluation of an expression.</span></span> <span data-ttu-id="8ca43-122">Özellikleri benzer <xref:System.Activities.Validation.AssertValidation> ve birlikte bir kısıtlamaya akış denetimi etkinlikleri gibi kullanılmadan <xref:System.Activities.Statements.If> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="8ca43-122">Its properties are similar to <xref:System.Activities.Validation.AssertValidation> and it can be used in conjunction with flow control activities of a constraint such as the <xref:System.Activities.Statements.If> activity.</span></span>
  
### <a name="workflow-relationship-activities"></a><span data-ttu-id="8ca43-123">İş akışı ilişki etkinlikleri</span><span class="sxs-lookup"><span data-stu-id="8ca43-123">Workflow Relationship Activities</span></span>

<span data-ttu-id="8ca43-124">Birkaç doğrulama etkinliği kullanılabilir iş akışı içinde Doğrulanmakta olan etkinliği ile ilgili diğer etkinlikler hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="8ca43-124">Several validation activities are available that provide information about the other activities in the workflow in relation to the activity being validated.</span></span> <span data-ttu-id="8ca43-125"><xref:System.Activities.Validation.GetParentChain> Geçerli etkinlik arasındaki Kök etkinlik etkinliklerin tümünü içeren etkinlikler koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="8ca43-125"><xref:System.Activities.Validation.GetParentChain> returns a collection of activities that contains all of the activities between the current activity and the root activity.</span></span> <span data-ttu-id="8ca43-126"><xref:System.Activities.Validation.GetChildSubtree> bir özyinelemeli deseninde, çocuk etkinliklerinin içeren bir koleksiyon etkinliklerin sağlar ve <xref:System.Activities.Validation.GetWorkflowTree> tüm etkinlikler iş akışında alır.</span><span class="sxs-lookup"><span data-stu-id="8ca43-126"><xref:System.Activities.Validation.GetChildSubtree> provides a collection of activities that contains the child activities in a recursive pattern, and <xref:System.Activities.Validation.GetWorkflowTree> gets all the activities in the workflow.</span></span>  
  
<span data-ttu-id="8ca43-127">Aşağıdaki örnekte, bir `CreateState` etkinlik tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="8ca43-127">In the following example, a `CreateState` activity is defined.</span></span> <span data-ttu-id="8ca43-128">`CreateState` Etkinlik bulunan, içinde bir `CreateCountry` etkinliği ve `GetParent` bu gereksinimini zorlar bir kısıtlama döner.</span><span class="sxs-lookup"><span data-stu-id="8ca43-128">The `CreateState` activity must be contained within a `CreateCountry` activity, and the `GetParent` method returns a constraint that enforces this requirement.</span></span> <span data-ttu-id="8ca43-129">`GetParent` kullanan <xref:System.Activities.Validation.GetParentChain> etkinlik ile birlikte bir <xref:System.Activities.Statements.ForEach%601> üst etkinliklerini İnceleme etkinliği `CreateState` bu gereksinimi karşılarsınız belirlemek için etkinlik.</span><span class="sxs-lookup"><span data-stu-id="8ca43-129">`GetParent` uses the <xref:System.Activities.Validation.GetParentChain> activity in conjunction with a <xref:System.Activities.Statements.ForEach%601> activity to inspect the parent activities of the `CreateState` activity to determine if the requirement is met.</span></span>  
  
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
  
## <a name="additional-constraints"></a><span data-ttu-id="8ca43-130">Ek kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="8ca43-130">Additional Constraints</span></span>  
 <span data-ttu-id="8ca43-131">İş akışı konak yazarları belirtebilirsiniz ek doğrulama kısıtlamalarını etkinlikler için bir iş akışında kısıtlamalar oluşturarak ve ekleyerek bunları <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> sözlüğü bir <xref:System.Activities.Validation.ValidationSettings> örneği.</span><span class="sxs-lookup"><span data-stu-id="8ca43-131">Workflow host authors can specify additional validation constraints for activities in a workflow by creating constraints and adding them to the <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> dictionary of a <xref:System.Activities.Validation.ValidationSettings> instance.</span></span> <span data-ttu-id="8ca43-132">Her öğe <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> için etkinlik türünü içerir, kısıtlamalar uygulanır ve bu tür bir etkinlik için ek kısıtlamalar listesi.</span><span class="sxs-lookup"><span data-stu-id="8ca43-132">Each item in <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> contains the type of activity for which the constraints apply and a list of the additional constraints for that type of activity.</span></span> <span data-ttu-id="8ca43-133">İş akışı için Doğrulama çağrıldığında belirtilen türün türetilen sınıflar da dahil olmak üzere her bir etkinlik kısıtlamaları değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="8ca43-133">When validation is invoked for the workflow, each activity of the specified type, including derived classes, evaluates the constraints.</span></span> <span data-ttu-id="8ca43-134">Bu örnekte, `ActivityDisplayNameIsNotSetWarning` kısıtlama önceki bölümde, iş akışındaki tüm etkinlikler için uygulanır.</span><span class="sxs-lookup"><span data-stu-id="8ca43-134">In this example, the `ActivityDisplayNameIsNotSetWarning` constraint from the previous section is applied to all activities in a workflow.</span></span>  
  
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
  
 <span data-ttu-id="8ca43-135">Varsa <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> özelliği <xref:System.Activities.Validation.ValidationSettings> olduğu `true`, yalnızca belirtilen ek kısıtlamaları çağırarak Doğrulama çağrıldığında değerlendirilir sonra <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="8ca43-135">If the <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> property of <xref:System.Activities.Validation.ValidationSettings> is `true`, then only the specified additional constraints are evaluated when validation is invoked by calling <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="8ca43-136">Bu, belirli bir doğrulama yapılandırmalar için iş akışları incelemek için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="8ca43-136">This can be useful for inspecting workflows for specific validation configurations.</span></span> <span data-ttu-id="8ca43-137">Ancak iş akışı çağrıldığında iş akışı içinde yapılandırılmış doğrulama mantığı değerlendirilir ve başarılı bir şekilde başlamak iş akışı için geçmesi gereken unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8ca43-137">Note however that when the workflow is invoked, the validation logic configured in the workflow is evaluated and must pass for the workflow to successfully begin.</span></span> <span data-ttu-id="8ca43-138">Doğrulamayı çağırma hakkında daha fazla bilgi için bkz. [etkinlik doğrulamayı çağırma](invoking-activity-validation.md).</span><span class="sxs-lookup"><span data-stu-id="8ca43-138">For more information about invoking validation, see [Invoking Activity Validation](invoking-activity-validation.md).</span></span>
