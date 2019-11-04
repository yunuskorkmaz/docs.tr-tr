---
title: 'Nasıl yapılır: yeniden barındırılan bir tasarımcıda doğrulama hatalarını görüntüleme'
ms.date: 03/30/2017
ms.assetid: 5aa8fb53-8f75-433b-bc06-7c7d33583d5d
ms.openlocfilehash: d36883eb77864ccc16cb5882d0de216e1aaaa589
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73420606"
---
# <a name="how-to-display-validation-errors-in-a-rehosted-designer"></a>Nasıl yapılır: yeniden barındırılan bir tasarımcıda doğrulama hatalarını görüntüleme
Bu konu başlığı altında, yeniden barındırılan bir [!INCLUDE[wfd1](../../../includes/wfd1-md.md)]doğrulama hatalarının nasıl alınacağını ve yayımlanacağı açıklanmaktadır. Bu, bir yeniden barındırılan Tasarımcıda bir iş akışının geçerli olduğunu onaylamak için bize bir yordam sağlar.  
  
 Bu görevin iki bölümü vardır. Birincisi bir uygulama <xref:System.Activities.Presentation.Validation.IValidationErrorService>sağlamaktır.  Bu arabirimde uygulanması için bir kritik yöntem vardır <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>, hata ayıklama günlüğüne hatalar hakkında bilgi içeren <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> nesnelerinin bir listesini geçilecektir.  Arabirimi uyguladıktan sonra, bu uygulamanın bir örneğini düzen bağlamına yayımlayarak hata bilgilerini alırsınız.  
  
### <a name="implement-the-ivalidationerrorservice-interface"></a>IValidationErrorService arabirimini uygulama  
  
1. Hata ayıklama günlüğüne doğrulama hatalarını yazacak basit bir uygulama için kod örneği aşağıda verilmiştir.  
  
    ```csharp  
    using System.Activities.Presentation.Validation;  
    using System.Collections.Generic;  
    using System.Diagnostics;  
    using System.Linq;  
  
    namespace VariableFinderShell  
    {  
        class DebugValidationErrorService : IValidationErrorService  
        {  
            public void ShowValidationErrors(IList<ValidationErrorInfo> errors)  
            {  
                errors.ToList().ForEach(vei => Debug.WriteLine($"Error: {vei.Message}"));  
            }  
        }  
    }  
    ```  
  
### <a name="publishing-to-the-editing-context"></a>Düzen bağlamına yayımlama  
  
1. Bu, bunu, düzen bağlamına yayımlayabilecek kod.  
  
    ```csharp  
    wd.Context.Services.Publish<IValidationErrorService>(new DebugValidationErrorService());  
    ```
