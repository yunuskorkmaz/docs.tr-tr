---
title: "Nasıl yapılır: Rehosted Tasarımcısı'nda doğrulama hataları görüntüleme"
ms.date: 03/30/2017
ms.assetid: 5aa8fb53-8f75-433b-bc06-7c7d33583d5d
ms.openlocfilehash: 8f70b190042d167741bbadc4e1645756fe5b830d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512573"
---
# <a name="how-to-display-validation-errors-in-a-rehosted-designer"></a>Nasıl yapılır: Rehosted Tasarımcısı'nda doğrulama hataları görüntüleme
Bu konu, almak ve doğrulama hatalarını bir rehosted yayımlamak açıklar [!INCLUDE[wfd1](../../../includes/wfd1-md.md)]. Bu bize rehosted Tasarımcısı bir iş akışında geçerli olduğunu onaylamak için bir yordam sağlar.  
  
 Bu görev iki bölümden oluşur. Bir uygulama sunmak amacıyla ilk olduğu <xref:System.Activities.Presentation.Validation.IValidationErrorService>.  Bu arabirimde uygulamak için bir kritik yöntemi yoktur <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> hangi geçecek, listesini <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> hata ayıklama günlüğüne hatalar hakkında bilgi içeren nesne.  Arabirimi uyguladıktan sonra bu uygulama örneğini düzenleme bağlamına yayımlayarak hata bilgilerini alır.  
  
### <a name="implement-the-ivalidationerrorservice-interface"></a>IValidationErrorService arabirimini uygulama  
  
1.  Hata ayıklama günlüğüne doğrulama hataları ortaya yazacak basit bir uygulama için bir kod örneği aşağıda verilmiştir.  
  
    ```  
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
                errors.ToList().ForEach(vei => Debug.WriteLine(string.Format("Error: {0} ", vei.Message)));  
            }  
        }  
    }  
    ```  
  
### <a name="publishing-to-the-editing-context"></a>Düzenlediğiniz içerik yayımlama  
  
1.  Aşağıda, bu düzenleme bağlamına yayımlayacak kodu verilmiştir.  
  
    ```  
    wd.Context.Services.Publish<IValidationErrorService>(new DebugValidationErrorService());  
    ```
