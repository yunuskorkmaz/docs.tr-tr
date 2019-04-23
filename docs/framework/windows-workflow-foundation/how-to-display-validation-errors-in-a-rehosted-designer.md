---
title: 'Nasıl yapılır: Yeniden Barındırılan Tasarımcıda Doğrulama Hatalarını Gösterme'
ms.date: 03/30/2017
ms.assetid: 5aa8fb53-8f75-433b-bc06-7c7d33583d5d
ms.openlocfilehash: a3d993f55bf130039905f1a6512a7ae104512432
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59770912"
---
# <a name="how-to-display-validation-errors-in-a-rehosted-designer"></a>Nasıl yapılır: Yeniden Barındırılan Tasarımcıda Doğrulama Hatalarını Gösterme
Bu konu, alma ve doğrulama hatalarını içinde yeniden barındırılan yayımlama açıklar [!INCLUDE[wfd1](../../../includes/wfd1-md.md)]. Bu bize bir iş akışı yeniden barındırılan tasarımcıda geçerli olduğundan emin olmak için ilgili bir yordam sağlar.  
  
 Bu görevi, iki bölümden oluşur. İlk uygulama sağlamaktır <xref:System.Activities.Presentation.Validation.IValidationErrorService>.  Bu arabirimde uygulamak için kritik bir yöntem <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> hangi geçecek, listesini <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> için hata ayıklama günlüğünü hatalara ilişkin bilgileri içeren bir nesne.  Arabirimi uyguladıktan sonra bu uygulama örneği için düzenleme bağlamı yayımlayarak hata bilgileri alabilirsiniz.  
  
### <a name="implement-the-ivalidationerrorservice-interface"></a>IValidationErrorService arabirimini uygulama  
  
1. Doğrulama hataları için hata ayıklama günlüğünü dışarı yazılacak basit bir uygulama için bir kod örneği aşağıda verilmiştir.  
  
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
  
### <a name="publishing-to-the-editing-context"></a>Düzenleme bağlamı yayımlama  
  
1. Bu düzenleme bağlamı için yayımlama kod aşağıdaki gibidir.  
  
    ```  
    wd.Context.Services.Publish<IValidationErrorService>(new DebugValidationErrorService());  
    ```
