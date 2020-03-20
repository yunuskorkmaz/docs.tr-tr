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
# <a name="imperative-code-based-validation"></a>Kesin Kod Temelli Doğrulama

Zorunlu kod tabanlı doğrulama, bir etkinliğin kendisi hakkında doğrulama sağlaması için basit bir yol <xref:System.Activities.CodeActivity>sağlar <xref:System.Activities.AsyncCodeActivity>ve <xref:System.Activities.NativeActivity>, ve . Etkinlikte herhangi bir doğrulama hatası veya uyarıyı belirleyen doğrulama kodu eklenir.  
  
## <a name="using-code-based-validation"></a>Kod Tabanlı Doğrulamayı Kullanma

Kod tabanlı <xref:System.Activities.CodeActivity>doğrulama, , ve <xref:System.Activities.AsyncCodeActivity>. <xref:System.Activities.NativeActivity> Geçersiz kılmaya <xref:System.Activities.CodeActivity.CacheMetadata%2A> doğrulama kodu yerleştirilebilir ve doğrulama hataları veya uyarıları meta veri bağımsız değişkenine eklenebilir. Aşağıdaki örnekte, `Cost` meta verilere `Price`bir doğrulama hatası eklenir.  
  
> [!NOTE]
> Bu `Cost` ve `Price` etkinlik için bağımsız değişkenler değildir, ancak tasarım zamanında ayarlanmış özellikleri olduğunu unutmayın. Bu nedenle, değerleri geçersiz kılmada <xref:System.Activities.CodeActivity.CacheMetadata%2A> doğrulanabilir. Bir bağımsız değişken den akan verilerin değeri, veriler çalışma süresine kadar akmaz, ancak öznitelik ve aşırı yük grupları kullanılarak `RequiredArgument` bağlı olduğundan emin olmak için etkinlik bağımsız değişkenleri doğrulanabilir, çünkü tasarım zamanında doğrulanamaz. Bu örnek kod `RequiredArgument` `Description` bağımsız değişken için özniteliği görür ve bağlı değilse bir doğrulama hatası oluşturulur. Gerekli bağımsız değişkenler Gerekli Bağımsız Değişkenler ve Aşırı Yük Grupları'nda ele [alınmıştır.](required-arguments-and-overload-groups.md)  
  
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
  
 Varsayılan olarak, çağrıldığında <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> meta verilere bir doğrulama hatası eklenir. Doğrulama uyarısı eklemek için, <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> bir <xref:System.Activities.Validation.ValidationError>, alan aşırı yükü <xref:System.Activities.Validation.ValidationError> kullanın ve <xref:System.Activities.Validation.ValidationError.IsWarning%2A> özelliği ayarlayarak bir uyarı temsil ettiğini belirtin.  
  
 Doğrulama, iş akışı tasarımcısında bir iş akışı değiştirildiğinde ve iş akışı tasarımcısında doğrulama hataları veya uyarıları görüntülendiğinde oluşur. Doğrulama, bir iş akışı çağrıldığı ve herhangi bir doğrulama hatası oluştuğunda, <xref:System.Activities.InvalidWorkflowException> varsayılan doğrulama mantığı tarafından atılan çalışma zamanında da oluşur. Doğrulama çağırmak ve doğrulama uyarılarına veya hatalarına erişim hakkında daha fazla bilgi için [bkz.](invoking-activity-validation.md)  
  
 Atılan <xref:System.Activities.CodeActivity.CacheMetadata%2A> tüm özel durumlar doğrulama hatası olarak kabul edilmez. Bu özel durumlar aramadan <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> kaçar ve arayan tarafından ele alınmalıdır.  
  
 Kod tabanlı doğrulama, kodu içeren etkinliği doğrulamak için yararlıdır, ancak iş akışındaki diğer etkinliklere görünürlüğü yoktur. Bildirimsel kısıtlamalar doğrulaması, bir etkinlik le iş akışındaki diğer etkinlikler arasındaki ilişkileri doğrulama olanağı sağlar ve [Bildirimsel Kısıtlamalar](declarative-constraints.md) konusunda ele alınmıştır.
