---
description: 'Daha fazla bilgi edinin: kesinlik Code-Based doğrulaması'
title: Kesin Kod Temelli Doğrulama
ms.date: 03/30/2017
ms.assetid: ae12537c-455e-42b1-82f4-cea4c46c023e
ms.openlocfilehash: 36759572393be613a569c4846e3610fcbbde2a51
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792706"
---
# <a name="imperative-code-based-validation"></a><span data-ttu-id="c8804-103">Kesin Kod Temelli Doğrulama</span><span class="sxs-lookup"><span data-stu-id="c8804-103">Imperative Code-Based Validation</span></span>

<span data-ttu-id="c8804-104">Zorunlu kod tabanlı doğrulama, bir etkinliğin kendisi hakkında doğrulama sağlaması için basit bir yol sağlar ve, ve ' den türetilen etkinlikler için kullanılabilir <xref:System.Activities.CodeActivity> <xref:System.Activities.AsyncCodeActivity> <xref:System.Activities.NativeActivity> .</span><span class="sxs-lookup"><span data-stu-id="c8804-104">Imperative code-based validation provides a simple way for an activity to provide validation about itself, and is available for activities that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, and <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="c8804-105">Etkinliğe herhangi bir doğrulama hatası veya uyarı eklendiğini belirleyen doğrulama kodu.</span><span class="sxs-lookup"><span data-stu-id="c8804-105">Validation code that determines any validation errors or warnings is added to the activity.</span></span>  
  
## <a name="using-code-based-validation"></a><span data-ttu-id="c8804-106">Code-Based doğrulaması kullanma</span><span class="sxs-lookup"><span data-stu-id="c8804-106">Using Code-Based Validation</span></span>

<span data-ttu-id="c8804-107">Kod tabanlı doğrulama,, ve öğesinden türetilen etkinlikler tarafından desteklenir <xref:System.Activities.CodeActivity> <xref:System.Activities.AsyncCodeActivity> <xref:System.Activities.NativeActivity> .</span><span class="sxs-lookup"><span data-stu-id="c8804-107">Code-based validation is supported by activities that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, and <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="c8804-108">Doğrulama kodu <xref:System.Activities.CodeActivity.CacheMetadata%2A> geçersiz kılmaya yerleştirilebilecek ve meta veri bağımsız değişkenine doğrulama hataları veya uyarılar eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="c8804-108">Validation code can be placed in the <xref:System.Activities.CodeActivity.CacheMetadata%2A> override, and validation errors or warnings can be added to the metadata argument.</span></span> <span data-ttu-id="c8804-109">Aşağıdaki örnekte,, ' `Cost` den büyükse, `Price` meta verilere bir doğrulama hatası eklenir.</span><span class="sxs-lookup"><span data-stu-id="c8804-109">In the following example, if the `Cost` is greater than the `Price`, a validation error is added to the metadata.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c8804-110">`Cost`Ve `Price` etkinliğin bağımsız değişken olmadığına, ancak tasarım zamanında ayarlanan özelliklere sahip olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c8804-110">Note that `Cost` and `Price` are not arguments to the activity, but are properties that are set at design time.</span></span> <span data-ttu-id="c8804-111">Bu, değerlerinin geçersiz kılmada nasıl onaylanabileceğini de unutmayın <xref:System.Activities.CodeActivity.CacheMetadata%2A> .</span><span class="sxs-lookup"><span data-stu-id="c8804-111">That is why their values can be validated in the <xref:System.Activities.CodeActivity.CacheMetadata%2A> override.</span></span> <span data-ttu-id="c8804-112">Bir bağımsız değişken üzerinden akan verilerin değeri, çalışma zamanına kadar akış yapılmadığından, ancak etkinlik bağımsız değişkenleri `RequiredArgument` öznitelik ve aşırı yükleme grupları kullanılarak bağlandıklarından emin olmak için doğrulanabilir.</span><span class="sxs-lookup"><span data-stu-id="c8804-112">The value of the data flowing through an argument cannot be validated at design time because the data does not flow until run time, but activity arguments can be validated to ensure that they are bound by using the `RequiredArgument` attribute and overload groups.</span></span> <span data-ttu-id="c8804-113">Bu örnek kod, `RequiredArgument` bağımsız değişkeni için özniteliğini görür `Description` ve bağlanmazsa, bir doğrulama hatası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c8804-113">This example code sees the `RequiredArgument` attribute for the `Description` argument, and if it is not bound then a validation error is generated.</span></span> <span data-ttu-id="c8804-114">Gerekli bağımsız değişkenler, [gerekli bağımsız değişkenler ve aşırı yükleme gruplarında](required-arguments-and-overload-groups.md)ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="c8804-114">Required arguments are covered in [Required Arguments and Overload Groups](required-arguments-and-overload-groups.md).</span></span>  
  
```csharp  
public sealed class CreateProduct : CodeActivity  
{  
    public double Price { get; set; }  
    public double Cost { get; set; }  
  
    // [RequiredArgument] attribute will generate a validation error
    // if the Description argument is not set.  
    [RequiredArgument]  
    public InArgument<string> Description { get; set; }  
  
    protected override void CacheMetadata(CodeActivityMetadata metadata)  
    {  
        base.CacheMetadata(metadata);  
        // Determine when the activity has been configured in an invalid way.  
        if (this.Cost > this.Price)  
        {  
            // Add a validation error with a custom message.  
            metadata.AddValidationError("The Cost must be less than or equal to the Price.");  
        }  
    }  
  
    protected override void Execute(CodeActivityContext context)  
    {  
        // Not needed for the sample.  
    }  
}  
```  
  
 <span data-ttu-id="c8804-115">Varsayılan olarak, çağrıldığında meta veriye bir doğrulama hatası eklenir <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> .</span><span class="sxs-lookup"><span data-stu-id="c8804-115">By default, a validation error is added to the metadata when <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> is called.</span></span> <span data-ttu-id="c8804-116">Bir doğrulama uyarısı eklemek için, <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> <xref:System.Activities.Validation.ValidationError> ' ı alan ve <xref:System.Activities.Validation.ValidationError> özelliğini ayarlayarak bir uyarıyı temsil ettiğini belirten aşırı yüklemeyi kullanın <xref:System.Activities.Validation.ValidationError.IsWarning%2A> .</span><span class="sxs-lookup"><span data-stu-id="c8804-116">To add a validation warning, use the <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> overload that takes a <xref:System.Activities.Validation.ValidationError>, and specify that the <xref:System.Activities.Validation.ValidationError> represents a warning by setting the <xref:System.Activities.Validation.ValidationError.IsWarning%2A> property.</span></span>  
  
 <span data-ttu-id="c8804-117">Doğrulama, iş akışı tasarımcısında bir iş akışı değiştirildiğinde ve herhangi bir doğrulama hatası veya uyarı iş akışı tasarımcısında görüntülendiğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="c8804-117">Validation occurs when a workflow is modified in the workflow designer and any validation errors or warnings are displayed in the workflow designer.</span></span> <span data-ttu-id="c8804-118">Doğrulama işlemi, bir iş akışı çağrıldığında çalışma zamanında da oluşur ve herhangi bir doğrulama hatası oluşursa, <xref:System.Activities.InvalidWorkflowException> varsayılan doğrulama mantığı tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c8804-118">Validation also occurs at run time when a workflow is invoked and if any validation errors occur, an <xref:System.Activities.InvalidWorkflowException> is thrown by the default validation logic.</span></span> <span data-ttu-id="c8804-119">Doğrulamayı çağırma ve herhangi bir doğrulama uyarısına veya hataya erişme hakkında daha fazla bilgi için bkz. [etkinlik doğrulamasını çağırma](invoking-activity-validation.md).</span><span class="sxs-lookup"><span data-stu-id="c8804-119">For more information about invoking validation and accessing any validation warnings or errors, see [Invoking Activity Validation](invoking-activity-validation.md).</span></span>  
  
 <span data-ttu-id="c8804-120">Kaynağından oluşturulan tüm özel durumlar <xref:System.Activities.CodeActivity.CacheMetadata%2A> doğrulama hatası olarak değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="c8804-120">Any exceptions that are thrown from <xref:System.Activities.CodeActivity.CacheMetadata%2A> are not treated as validation errors.</span></span> <span data-ttu-id="c8804-121">Bu özel durumlar, çağrısından <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> ve çağıran tarafından işlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="c8804-121">These exceptions will escape from the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> and must be handled by the caller.</span></span>  
  
 <span data-ttu-id="c8804-122">Kod tabanlı doğrulama, kodu içeren etkinliğin doğrulanması için yararlıdır, ancak iş akışındaki diğer etkinliklere ilişkin görünürlüğe sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="c8804-122">Code-based validation is useful for validating the activity that contains the code, but it does not have visibility into the other activities in the workflow.</span></span> <span data-ttu-id="c8804-123">Bildirime dayalı kısıtlamalar doğrulaması, iş akışındaki bir etkinlik ve diğer etkinlikler arasındaki ilişkileri doğrulama olanağı sağlar ve [bildirim temelli kısıtlamalar](declarative-constraints.md) konusunda ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="c8804-123">Declarative constraints validation provides the ability to validate the relationships between an activity and other activities in the workflow, and is covered in the [Declarative Constraints](declarative-constraints.md) topic.</span></span>
