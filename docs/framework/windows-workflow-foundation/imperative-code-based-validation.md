---
title: Kesinlik temelli kod tabanlı doğrulama
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ae12537c-455e-42b1-82f4-cea4c46c023e
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5dde4c75d2cf9432c750a8988c2495cd72eb2770
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="imperative-code-based-validation"></a>Kesinlik temelli kod tabanlı doğrulama
Kesinlik temelli kod tabanlı doğrulama kendisi hakkında doğrulama sağlamak bir etkinlik için basit bir yol sağlar ve türetilen etkinlikler için kullanılabilir <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, ve <xref:System.Activities.NativeActivity>. Herhangi bir doğrulama hata veya uyarı belirler doğrulama kodunu aktivite eklenir.  
  
## <a name="using-code-based-validation"></a>Kod tabanlı doğrulama kullanma  
 Kod tabanlı doğrulama öğesinden türetilen etkinlikleri tarafından desteklenen <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, ve <xref:System.Activities.NativeActivity>. Doğrulama kodu yerleştirilebilen <xref:System.Activities.CodeActivity.CacheMetadata%2A> geçersiz kıl ve doğrulama hatalar veya uyarılar meta verileri bağımsız değişkeni olarak eklenebilir. Aşağıdaki örnekte, geçen [temel doğrulama](../../../docs/framework/windows-workflow-foundation/samples/basic-validation.md) , örnek `Cost` değerinden daha büyük `Price`, meta veriler için bir doğrulama hatası eklenir.  
  
> [!NOTE]
>  Unutmayın `Cost` ve `Price` etkinlik bağımsız değişkenleri değildir, ancak tasarım zamanında ayarlama özelliklerdir. Diğer bir deyişle neden değerlerine içinde doğrulanabilir <xref:System.Activities.CodeActivity.CacheMetadata%2A> geçersiz kılar. Veri çalışma zamanına kadar akış değil, ancak etkinlik bağımsız değişkenler doğrulanmış bunlar kullanarak bağlı emin olmak için tasarım zamanında bir bağımsız değişken akan verilere değeri doğrulanamıyor `RequiredArgument` özniteliği ve grupları aşırı yükleme. Bu kod örneği görür `RequiredArgument` için öznitelik `Description` bağımsız değişkeni ve bağlı değilse sonra bir doğrulama hatası oluşturulur. Gerekli bağımsız ele alınmıştır [gerekli bağımsız değişkenleri ve aşırı grupları](../../../docs/framework/windows-workflow-foundation/required-arguments-and-overload-groups.md).  
  
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
  
 Varsayılan olarak, meta veriler için bir doğrulama hatası eklenir, <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> olarak adlandırılır. Doğrulama uyarısı eklemek için kullanın <xref:System.Activities.CodeActivityMetadata.AddValidationError%2A> alan aşırı bir <xref:System.Activities.Validation.ValidationError>, belirleyen <xref:System.Activities.Validation.ValidationError> ayarlayarak bir uyarı temsil eden <xref:System.Activities.Validation.ValidationError.IsWarning%2A> özelliği.  
  
 Bir iş akışı iş akışı Tasarımcısı'nda değiştirilir ve herhangi bir doğrulama hata veya uyarı iş akışı Tasarımcısı'nda görüntülenen doğrulama oluşur. Doğrulama da ortaya çıkar çalışma zamanında bir iş akışı çalıştırıldığında ve herhangi bir doğrulama hatası oluşursa, bir <xref:System.Activities.InvalidWorkflowException> varsayılan Doğrulama mantığı tarafından oluşturulur. Doğrulama çağırma ve doğrulama uyarı veya hata erişme hakkında daha fazla bilgi için bkz: [çağırma etkinlik doğrulama](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md).  
  
 Öğesinden oluşturulan özel durumlar <xref:System.Activities.CodeActivity.CacheMetadata%2A> doğrulama hata olarak kabul edilmediği. Bu özel durumlar için çağrısından kaçış <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> ve çağıran tarafından yapılması gerekir.  
  
 Kod tabanlı doğrulama kodunu içeren aktiviteyi doğrulamak için yararlıdır, ancak diğer etkinlikler görünürlük iş akışı içinde yok. Bildirim temelli kısıtlamaları doğrulama aktivite ve iş akışındaki diğer etkinlikleri arasındaki ilişkileri doğrulama olanağı sağlar ve içinde ele [bildirim temelli kısıtlamaları](../../../docs/framework/windows-workflow-foundation/declarative-constraints.md) konu.
