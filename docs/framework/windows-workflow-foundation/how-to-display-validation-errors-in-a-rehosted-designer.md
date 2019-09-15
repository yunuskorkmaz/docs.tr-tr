---
title: 'Nasıl yapılır: Yeniden Barındırılan Tasarımcıda Doğrulama Hatalarını Gösterme'
ms.date: 03/30/2017
ms.assetid: 5aa8fb53-8f75-433b-bc06-7c7d33583d5d
ms.openlocfilehash: 608868882f4bec23c03f0ec78f65673e76056030
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989660"
---
# <a name="how-to-display-validation-errors-in-a-rehosted-designer"></a>Nasıl yapılır: Yeniden Barındırılan Tasarımcıda Doğrulama Hatalarını Gösterme
Bu konu başlığı altında, doğrulama hatalarının yeniden barındırılan [!INCLUDE[wfd1](../../../includes/wfd1-md.md)]bir şekilde nasıl alınacağını ve yayımlanacağı açıklanmaktadır. Bu, bir yeniden barındırılan Tasarımcıda bir iş akışının geçerli olduğunu onaylamak için bize bir yordam sağlar.  
  
 Bu görevin iki bölümü vardır. Birincisi bir uygulama <xref:System.Activities.Presentation.Validation.IValidationErrorService>sağlamaktır.  Bu arabirime uygulamak için bir kritik yöntem vardır. Bu, <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> hata ayıklama günlüğüne hatalarla ilgili bilgiler içeren <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> bir nesne listesini geçecek.  Arabirimi uyguladıktan sonra, bu uygulamanın bir örneğini düzen bağlamına yayımlayarak hata bilgilerini alırsınız.  
  
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
                errors.ToList().ForEach(vei => Debug.WriteLine(string.Format("Error: {0} ", vei.Message)));  
            }  
        }  
    }  
    ```  
  
### <a name="publishing-to-the-editing-context"></a>Düzen bağlamına yayımlama  
  
1. Bu, bunu, düzen bağlamına yayımlayabilecek kod.  
  
    ```csharp  
    wd.Context.Services.Publish<IValidationErrorService>(new DebugValidationErrorService());  
    ```
