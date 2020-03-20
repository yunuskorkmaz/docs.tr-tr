---
title: Kesin Kod Temelli Doğrulama
ms.date: 03/30/2017
ms.assetid: ae12537c-455e-42b1-82f4-cea4c46c023e
ms.openlocfilehash: f3b07d0ab06b3753286c929b90e713a6941684ad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143102"
---
# <a name="imperative-code-based-validation"></a><span data-ttu-id="fec02-102">Kesin Kod Temelli Doğrulama</span><span class="sxs-lookup"><span data-stu-id="fec02-102">Imperative Code-Based Validation</span></span>

<span data-ttu-id="fec02-103">Zorunlu kod tabanlı doğrulama, bir etkinliğin kendisi hakkında doğrulama sağlaması için basit bir yol <xref:System.Activities.CodeActivity>sağlar <xref:System.Activities.AsyncCodeActivity>ve <xref:System.Activities.NativeActivity>, ve .</span><span class="sxs-lookup"><span data-stu-id="fec02-103">Imperative code-based validation provides a simple way for an activity to provide validation about itself, and is available for activities that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, and <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="fec02-104">Etkinlikte herhangi bir doğrulama hatası veya uyarıyı belirleyen doğrulama kodu eklenir.</span><span class="sxs-lookup"><span data-stu-id="fec02-104">Validation code that determines any validation errors or warnings is added to the activity.</span></span>  
  
## <a name="using-code-based-validation"></a><span data-ttu-id="fec02-105">Kod Tabanlı Doğrulamayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="fec02-105">Using Code-Based Validation</span></span>

<span data-ttu-id="fec02-106">Kod tabanlı <xref:System.Activities.CodeActivity>doğrulama, , ve <xref:System.Activities.AsyncCodeActivity>. <xref:System.Activities.NativeActivity></span><span class="sxs-lookup"><span data-stu-id="fec02-106">Code-based validation is supported by activities that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, and <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="fec02-107">Geçersiz kılmaya <xref:System.Activities.CodeActivity.CacheMetadata%2A> doğrulama kodu yerleştirilebilir ve doğrulama hataları veya uyarıları meta veri bağımsız değişkenine eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="fec02-107">Validation code can be placed in the <xref:System.Activities.CodeActivity.CacheMetadata%2A> override, and validation errors or warnings can be added to the metadata argument.</span></span> <span data-ttu-id="fec02-108">Aşağıdaki örnekte, `Cost` meta verilere `Price`bir doğrulama hatası eklenir.</span><span class="sxs-lookup"><span data-stu-id="fec02-108">In the following example, if the `Cost` is greater than the `Price`, a validation error is added to the metadata.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fec02-109">Bu `Cost` ve `Price` etkinlik için bağımsız değişkenler değildir, ancak tasarım zamanında ayarlanmış özellikleri olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="fec02-109">Note that `Cost` and `Price` are not arguments to the activity, but are properties that are set at design time.</span></span> <span data-ttu-id="fec02-110">Bu nedenle, değerleri geçersiz kılmada <xref:System.Activities.CodeActivity.CacheMetadata%2A> doğrulanabilir.</span><span class="sxs-lookup"><span data-stu-id="fec02-110">That is why their values can be validated in the <xref:System.Activities.CodeActivity.CacheMetadata%2A> override.</span></span> <span data-ttu-id="fec02-111">Bir bağımsız değişken den akan verilerin değeri, veriler çalışma süresine kadar akmaz, ancak öznitelik ve aşırı yük grupları kullanılarak `RequiredArgument` bağlı olduğundan emin olmak için etkinlik bağımsız değişkenleri doğrulanabilir, çünkü tasarım zamanında doğrulanamaz.</span><span class="sxs-lookup"><span data-stu-id="fec02-111">The value of the data flowing through an argument cannot be validated at design time because the data does not flow until run time, but activity arguments can be validated to ensure that they are bound by using the `RequiredArgument` attribute and overload groups.</span></span> <span data-ttu-id="fec02-112">Bu örnek kod `RequiredArgument` `Description` bağımsız değişken için özniteliği görür ve bağlı değilse bir doğrulama hatası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="fec02-112">This example code sees the `RequiredArgument` attribute for the `Description` argument, and if it is not bound then a validation error is generated.</span></span> <span data-ttu-id="fec02-113">Gerekli bağımsız değişkenler Gerekli Bağımsız Değişkenler ve Aşırı Yük Grupları'nda ele [alınmıştır.](required-arguments-and-overload-groups.md)</span><span class="sxs-lookup"><span data-stu-id="fec02-113">Required arguments are covered in [Required Arguments and Overload Groups](required-arguments-and-overload-groups.md).</span></span>  
  
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
  
 <span data-ttu-id="fec02-114">Varsayılan olarak, çağrıldığında <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> meta verilere bir doğrulama hatası eklenir.</span><span class="sxs-lookup"><span data-stu-id="fec02-114">By default, a validation error is added to the metadata when <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> is called.</span></span> <span data-ttu-id="fec02-115">Doğrulama uyarısı eklemek için, <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> bir <xref:System.Activities.Validation.ValidationError>, alan aşırı yükü <xref:System.Activities.Validation.ValidationError> kullanın ve <xref:System.Activities.Validation.ValidationError.IsWarning%2A> özelliği ayarlayarak bir uyarı temsil ettiğini belirtin.</span><span class="sxs-lookup"><span data-stu-id="fec02-115">To add a validation warning, use the <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> overload that takes a <xref:System.Activities.Validation.ValidationError>, and specify that the <xref:System.Activities.Validation.ValidationError> represents a warning by setting the <xref:System.Activities.Validation.ValidationError.IsWarning%2A> property.</span></span>  
  
 <span data-ttu-id="fec02-116">Doğrulama, iş akışı tasarımcısında bir iş akışı değiştirildiğinde ve iş akışı tasarımcısında doğrulama hataları veya uyarıları görüntülendiğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="fec02-116">Validation occurs when a workflow is modified in the workflow designer and any validation errors or warnings are displayed in the workflow designer.</span></span> <span data-ttu-id="fec02-117">Doğrulama, bir iş akışı çağrıldığı ve herhangi bir doğrulama hatası oluştuğunda, <xref:System.Activities.InvalidWorkflowException> varsayılan doğrulama mantığı tarafından atılan çalışma zamanında da oluşur.</span><span class="sxs-lookup"><span data-stu-id="fec02-117">Validation also occurs at run time when a workflow is invoked and if any validation errors occur, an <xref:System.Activities.InvalidWorkflowException> is thrown by the default validation logic.</span></span> <span data-ttu-id="fec02-118">Doğrulama çağırmak ve doğrulama uyarılarına veya hatalarına erişim hakkında daha fazla bilgi için [bkz.](invoking-activity-validation.md)</span><span class="sxs-lookup"><span data-stu-id="fec02-118">For more information about invoking validation and accessing any validation warnings or errors, see [Invoking Activity Validation](invoking-activity-validation.md).</span></span>  
  
 <span data-ttu-id="fec02-119">Atılan <xref:System.Activities.CodeActivity.CacheMetadata%2A> tüm özel durumlar doğrulama hatası olarak kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="fec02-119">Any exceptions that are thrown from <xref:System.Activities.CodeActivity.CacheMetadata%2A> are not treated as validation errors.</span></span> <span data-ttu-id="fec02-120">Bu özel durumlar aramadan <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> kaçar ve arayan tarafından ele alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fec02-120">These exceptions will escape from the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> and must be handled by the caller.</span></span>  
  
 <span data-ttu-id="fec02-121">Kod tabanlı doğrulama, kodu içeren etkinliği doğrulamak için yararlıdır, ancak iş akışındaki diğer etkinliklere görünürlüğü yoktur.</span><span class="sxs-lookup"><span data-stu-id="fec02-121">Code-based validation is useful for validating the activity that contains the code, but it does not have visibility into the other activities in the workflow.</span></span> <span data-ttu-id="fec02-122">Bildirimsel kısıtlamalar doğrulaması, bir etkinlik le iş akışındaki diğer etkinlikler arasındaki ilişkileri doğrulama olanağı sağlar ve [Bildirimsel Kısıtlamalar](declarative-constraints.md) konusunda ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="fec02-122">Declarative constraints validation provides the ability to validate the relationships between an activity and other activities in the workflow, and is covered in the [Declarative Constraints](declarative-constraints.md) topic.</span></span>
