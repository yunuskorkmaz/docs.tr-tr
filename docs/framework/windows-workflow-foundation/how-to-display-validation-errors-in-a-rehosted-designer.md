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
# <a name="how-to-display-validation-errors-in-a-rehosted-designer"></a><span data-ttu-id="577ad-102">Nasıl yapılır: Yeniden Barındırılan Tasarımcıda Doğrulama Hatalarını Gösterme</span><span class="sxs-lookup"><span data-stu-id="577ad-102">How to: Display Validation Errors in a Rehosted Designer</span></span>
<span data-ttu-id="577ad-103">Bu konu başlığı altında, doğrulama hatalarının yeniden barındırılan [!INCLUDE[wfd1](../../../includes/wfd1-md.md)]bir şekilde nasıl alınacağını ve yayımlanacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="577ad-103">This topic describes how to retrieve and publish validation errors in a rehosted [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].</span></span> <span data-ttu-id="577ad-104">Bu, bir yeniden barındırılan Tasarımcıda bir iş akışının geçerli olduğunu onaylamak için bize bir yordam sağlar.</span><span class="sxs-lookup"><span data-stu-id="577ad-104">This provides us with a procedure to confirm that a workflow in a rehosted designer is valid.</span></span>  
  
 <span data-ttu-id="577ad-105">Bu görevin iki bölümü vardır.</span><span class="sxs-lookup"><span data-stu-id="577ad-105">This task has two parts.</span></span> <span data-ttu-id="577ad-106">Birincisi bir uygulama <xref:System.Activities.Presentation.Validation.IValidationErrorService>sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="577ad-106">The first is to provide an implementation <xref:System.Activities.Presentation.Validation.IValidationErrorService>.</span></span>  <span data-ttu-id="577ad-107">Bu arabirime uygulamak için bir kritik yöntem vardır. Bu, <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> hata ayıklama günlüğüne hatalarla ilgili bilgiler içeren <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> bir nesne listesini geçecek.</span><span class="sxs-lookup"><span data-stu-id="577ad-107">There is one critical method to implement on this interface, <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> which will pass you a list of <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> objects containing information about the errors to the debug log.</span></span>  <span data-ttu-id="577ad-108">Arabirimi uyguladıktan sonra, bu uygulamanın bir örneğini düzen bağlamına yayımlayarak hata bilgilerini alırsınız.</span><span class="sxs-lookup"><span data-stu-id="577ad-108">After implementing the interface, you retrieve the error information by publishing an instance of that implementation to the editing context.</span></span>  
  
### <a name="implement-the-ivalidationerrorservice-interface"></a><span data-ttu-id="577ad-109">IValidationErrorService arabirimini uygulama</span><span class="sxs-lookup"><span data-stu-id="577ad-109">Implement the IValidationErrorService Interface</span></span>  
  
1. <span data-ttu-id="577ad-110">Hata ayıklama günlüğüne doğrulama hatalarını yazacak basit bir uygulama için kod örneği aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="577ad-110">Here is a code sample for a simple implementation that will write out the validation errors to the debug log.</span></span>  
  
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
  
### <a name="publishing-to-the-editing-context"></a><span data-ttu-id="577ad-111">Düzen bağlamına yayımlama</span><span class="sxs-lookup"><span data-stu-id="577ad-111">Publishing to the Editing Context</span></span>  
  
1. <span data-ttu-id="577ad-112">Bu, bunu, düzen bağlamına yayımlayabilecek kod.</span><span class="sxs-lookup"><span data-stu-id="577ad-112">Here is the code that will publish this to the editing context.</span></span>  
  
    ```csharp  
    wd.Context.Services.Publish<IValidationErrorService>(new DebugValidationErrorService());  
    ```
