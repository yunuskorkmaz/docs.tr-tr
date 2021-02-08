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
# <a name="imperative-code-based-validation"></a>Kesin Kod Temelli Doğrulama

Zorunlu kod tabanlı doğrulama, bir etkinliğin kendisi hakkında doğrulama sağlaması için basit bir yol sağlar ve, ve ' den türetilen etkinlikler için kullanılabilir <xref:System.Activities.CodeActivity> <xref:System.Activities.AsyncCodeActivity> <xref:System.Activities.NativeActivity> . Etkinliğe herhangi bir doğrulama hatası veya uyarı eklendiğini belirleyen doğrulama kodu.  
  
## <a name="using-code-based-validation"></a>Code-Based doğrulaması kullanma

Kod tabanlı doğrulama,, ve öğesinden türetilen etkinlikler tarafından desteklenir <xref:System.Activities.CodeActivity> <xref:System.Activities.AsyncCodeActivity> <xref:System.Activities.NativeActivity> . Doğrulama kodu <xref:System.Activities.CodeActivity.CacheMetadata%2A> geçersiz kılmaya yerleştirilebilecek ve meta veri bağımsız değişkenine doğrulama hataları veya uyarılar eklenebilir. Aşağıdaki örnekte,, ' `Cost` den büyükse, `Price` meta verilere bir doğrulama hatası eklenir.  
  
> [!NOTE]
> `Cost`Ve `Price` etkinliğin bağımsız değişken olmadığına, ancak tasarım zamanında ayarlanan özelliklere sahip olduğunu unutmayın. Bu, değerlerinin geçersiz kılmada nasıl onaylanabileceğini de unutmayın <xref:System.Activities.CodeActivity.CacheMetadata%2A> . Bir bağımsız değişken üzerinden akan verilerin değeri, çalışma zamanına kadar akış yapılmadığından, ancak etkinlik bağımsız değişkenleri `RequiredArgument` öznitelik ve aşırı yükleme grupları kullanılarak bağlandıklarından emin olmak için doğrulanabilir. Bu örnek kod, `RequiredArgument` bağımsız değişkeni için özniteliğini görür `Description` ve bağlanmazsa, bir doğrulama hatası oluşturulur. Gerekli bağımsız değişkenler, [gerekli bağımsız değişkenler ve aşırı yükleme gruplarında](required-arguments-and-overload-groups.md)ele alınmıştır.  
  
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
  
 Varsayılan olarak, çağrıldığında meta veriye bir doğrulama hatası eklenir <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> . Bir doğrulama uyarısı eklemek için, <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> <xref:System.Activities.Validation.ValidationError> ' ı alan ve <xref:System.Activities.Validation.ValidationError> özelliğini ayarlayarak bir uyarıyı temsil ettiğini belirten aşırı yüklemeyi kullanın <xref:System.Activities.Validation.ValidationError.IsWarning%2A> .  
  
 Doğrulama, iş akışı tasarımcısında bir iş akışı değiştirildiğinde ve herhangi bir doğrulama hatası veya uyarı iş akışı tasarımcısında görüntülendiğinde oluşur. Doğrulama işlemi, bir iş akışı çağrıldığında çalışma zamanında da oluşur ve herhangi bir doğrulama hatası oluşursa, <xref:System.Activities.InvalidWorkflowException> varsayılan doğrulama mantığı tarafından oluşturulur. Doğrulamayı çağırma ve herhangi bir doğrulama uyarısına veya hataya erişme hakkında daha fazla bilgi için bkz. [etkinlik doğrulamasını çağırma](invoking-activity-validation.md).  
  
 Kaynağından oluşturulan tüm özel durumlar <xref:System.Activities.CodeActivity.CacheMetadata%2A> doğrulama hatası olarak değerlendirilmez. Bu özel durumlar, çağrısından <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> ve çağıran tarafından işlenmelidir.  
  
 Kod tabanlı doğrulama, kodu içeren etkinliğin doğrulanması için yararlıdır, ancak iş akışındaki diğer etkinliklere ilişkin görünürlüğe sahip değildir. Bildirime dayalı kısıtlamalar doğrulaması, iş akışındaki bir etkinlik ve diğer etkinlikler arasındaki ilişkileri doğrulama olanağı sağlar ve [bildirim temelli kısıtlamalar](declarative-constraints.md) konusunda ele alınmıştır.
