---
title: "Nasıl yapılır: Rehosted Tasarımcısı'nda doğrulama hataları görüntüleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5aa8fb53-8f75-433b-bc06-7c7d33583d5d
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b9f76f1ad5282ecf10a3ce58db0f6e1bd8df1b4d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
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
