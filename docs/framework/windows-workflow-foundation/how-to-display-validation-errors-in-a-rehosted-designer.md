---
description: 'Daha fazla bilgi edinin: nasıl yapılır: doğrulama hatalarını yeniden barındırılan bir tasarımcıda görüntüleme'
title: 'Nasıl yapılır: Yeniden Barındırılan Tasarımcıda Doğrulama Hatalarını Gösterme'
ms.date: 03/30/2017
ms.assetid: 5aa8fb53-8f75-433b-bc06-7c7d33583d5d
ms.openlocfilehash: 75ff45e6e9a81df96a9940ce21d1b160cab1000e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99777742"
---
# <a name="how-to-display-validation-errors-in-a-rehosted-designer"></a>Nasıl yapılır: Yeniden Barındırılan Tasarımcıda Doğrulama Hatalarını Gösterme

Bu konuda, yeniden barındırılan bir Windows İş Akışı Tasarımcısı doğrulama hatalarının nasıl alınacağını ve yayımlanacağı açıklanmaktadır. Bu, bir yeniden barındırılan Tasarımcıda bir iş akışının geçerli olduğunu onaylamak için bize bir yordam sağlar.  
  
 Bu görevin iki bölümü vardır. Birincisi bir uygulama sağlamaktır <xref:System.Activities.Presentation.Validation.IValidationErrorService> .  Bu arabirime uygulamak için bir kritik yöntem vardır. Bu, <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> hata ayıklama günlüğüne hatalarla ilgili bilgiler içeren bir nesne listesini geçecek.  Arabirimi uyguladıktan sonra, bu uygulamanın bir örneğini düzen bağlamına yayımlayarak hata bilgilerini alırsınız.  
  
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
