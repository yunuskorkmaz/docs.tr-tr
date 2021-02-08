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
# <a name="how-to-display-validation-errors-in-a-rehosted-designer"></a><span data-ttu-id="e0a3d-103">Nasıl yapılır: Yeniden Barındırılan Tasarımcıda Doğrulama Hatalarını Gösterme</span><span class="sxs-lookup"><span data-stu-id="e0a3d-103">How to: Display Validation Errors in a Rehosted Designer</span></span>

<span data-ttu-id="e0a3d-104">Bu konuda, yeniden barındırılan bir Windows İş Akışı Tasarımcısı doğrulama hatalarının nasıl alınacağını ve yayımlanacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e0a3d-104">This topic describes how to retrieve and publish validation errors in a rehosted Windows Workflow Designer.</span></span> <span data-ttu-id="e0a3d-105">Bu, bir yeniden barındırılan Tasarımcıda bir iş akışının geçerli olduğunu onaylamak için bize bir yordam sağlar.</span><span class="sxs-lookup"><span data-stu-id="e0a3d-105">This provides us with a procedure to confirm that a workflow in a rehosted designer is valid.</span></span>  
  
 <span data-ttu-id="e0a3d-106">Bu görevin iki bölümü vardır.</span><span class="sxs-lookup"><span data-stu-id="e0a3d-106">This task has two parts.</span></span> <span data-ttu-id="e0a3d-107">Birincisi bir uygulama sağlamaktır <xref:System.Activities.Presentation.Validation.IValidationErrorService> .</span><span class="sxs-lookup"><span data-stu-id="e0a3d-107">The first is to provide an implementation <xref:System.Activities.Presentation.Validation.IValidationErrorService>.</span></span>  <span data-ttu-id="e0a3d-108">Bu arabirime uygulamak için bir kritik yöntem vardır. Bu, <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> hata ayıklama günlüğüne hatalarla ilgili bilgiler içeren bir nesne listesini geçecek.</span><span class="sxs-lookup"><span data-stu-id="e0a3d-108">There is one critical method to implement on this interface, <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> which will pass you a list of <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> objects containing information about the errors to the debug log.</span></span>  <span data-ttu-id="e0a3d-109">Arabirimi uyguladıktan sonra, bu uygulamanın bir örneğini düzen bağlamına yayımlayarak hata bilgilerini alırsınız.</span><span class="sxs-lookup"><span data-stu-id="e0a3d-109">After implementing the interface, you retrieve the error information by publishing an instance of that implementation to the editing context.</span></span>  
  
### <a name="implement-the-ivalidationerrorservice-interface"></a><span data-ttu-id="e0a3d-110">IValidationErrorService arabirimini uygulama</span><span class="sxs-lookup"><span data-stu-id="e0a3d-110">Implement the IValidationErrorService Interface</span></span>  
  
1. <span data-ttu-id="e0a3d-111">Hata ayıklama günlüğüne doğrulama hatalarını yazacak basit bir uygulama için kod örneği aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e0a3d-111">Here is a code sample for a simple implementation that will write out the validation errors to the debug log.</span></span>  
  
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
  
### <a name="publishing-to-the-editing-context"></a><span data-ttu-id="e0a3d-112">Düzen bağlamına yayımlama</span><span class="sxs-lookup"><span data-stu-id="e0a3d-112">Publishing to the Editing Context</span></span>  
  
1. <span data-ttu-id="e0a3d-113">Bu, bunu, düzen bağlamına yayımlayabilecek kod.</span><span class="sxs-lookup"><span data-stu-id="e0a3d-113">Here is the code that will publish this to the editing context.</span></span>  
  
    ```csharp  
    wd.Context.Services.Publish<IValidationErrorService>(new DebugValidationErrorService());  
    ```
