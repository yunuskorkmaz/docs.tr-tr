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
# <a name="how-to-display-validation-errors-in-a-rehosted-designer"></a><span data-ttu-id="8dd13-102">Nasıl yapılır: Rehosted Tasarımcısı'nda doğrulama hataları görüntüleme</span><span class="sxs-lookup"><span data-stu-id="8dd13-102">How to: Display Validation Errors in a Rehosted Designer</span></span>
<span data-ttu-id="8dd13-103">Bu konu, almak ve doğrulama hatalarını bir rehosted yayımlamak açıklar [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8dd13-103">This topic describes how to retrieve and publish validation errors in a rehosted [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].</span></span> <span data-ttu-id="8dd13-104">Bu bize rehosted Tasarımcısı bir iş akışında geçerli olduğunu onaylamak için bir yordam sağlar.</span><span class="sxs-lookup"><span data-stu-id="8dd13-104">This provides us with a procedure to confirm that a workflow in a rehosted designer is valid.</span></span>  
  
 <span data-ttu-id="8dd13-105">Bu görev iki bölümden oluşur.</span><span class="sxs-lookup"><span data-stu-id="8dd13-105">This task has two parts.</span></span> <span data-ttu-id="8dd13-106">Bir uygulama sunmak amacıyla ilk olduğu <xref:System.Activities.Presentation.Validation.IValidationErrorService>.</span><span class="sxs-lookup"><span data-stu-id="8dd13-106">The first is to provide an implementation <xref:System.Activities.Presentation.Validation.IValidationErrorService>.</span></span>  <span data-ttu-id="8dd13-107">Bu arabirimde uygulamak için bir kritik yöntemi yoktur <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> hangi geçecek, listesini <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> hata ayıklama günlüğüne hatalar hakkında bilgi içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="8dd13-107">There is one critical method to implement on this interface, <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> which will pass you a list of <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> objects containing information about the errors to the debug log.</span></span>  <span data-ttu-id="8dd13-108">Arabirimi uyguladıktan sonra bu uygulama örneğini düzenleme bağlamına yayımlayarak hata bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="8dd13-108">After implementing the interface, you retrieve the error information by publishing an instance of that implementation to the editing context.</span></span>  
  
### <a name="implement-the-ivalidationerrorservice-interface"></a><span data-ttu-id="8dd13-109">IValidationErrorService arabirimini uygulama</span><span class="sxs-lookup"><span data-stu-id="8dd13-109">Implement the IValidationErrorService Interface</span></span>  
  
1.  <span data-ttu-id="8dd13-110">Hata ayıklama günlüğüne doğrulama hataları ortaya yazacak basit bir uygulama için bir kod örneği aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8dd13-110">Here is a code sample for a simple implementation that will write out the validation errors to the debug log.</span></span>  
  
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
  
### <a name="publishing-to-the-editing-context"></a><span data-ttu-id="8dd13-111">Düzenlediğiniz içerik yayımlama</span><span class="sxs-lookup"><span data-stu-id="8dd13-111">Publishing to the Editing Context</span></span>  
  
1.  <span data-ttu-id="8dd13-112">Aşağıda, bu düzenleme bağlamına yayımlayacak kodu verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8dd13-112">Here is the code that will publish this to the editing context.</span></span>  
  
    ```  
    wd.Context.Services.Publish<IValidationErrorService>(new DebugValidationErrorService());  
    ```
