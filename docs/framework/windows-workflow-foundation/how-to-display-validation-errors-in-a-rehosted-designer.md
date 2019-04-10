---
title: 'Nasıl yapılır: Yeniden Barındırılan Tasarımcıda Doğrulama Hatalarını Gösterme'
ms.date: 03/30/2017
ms.assetid: 5aa8fb53-8f75-433b-bc06-7c7d33583d5d
ms.openlocfilehash: a3d993f55bf130039905f1a6512a7ae104512432
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59310206"
---
# <a name="how-to-display-validation-errors-in-a-rehosted-designer"></a><span data-ttu-id="911dd-102">Nasıl yapılır: Yeniden Barındırılan Tasarımcıda Doğrulama Hatalarını Gösterme</span><span class="sxs-lookup"><span data-stu-id="911dd-102">How to: Display Validation Errors in a Rehosted Designer</span></span>
<span data-ttu-id="911dd-103">Bu konu, alma ve doğrulama hatalarını içinde yeniden barındırılan yayımlama açıklar [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="911dd-103">This topic describes how to retrieve and publish validation errors in a rehosted [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].</span></span> <span data-ttu-id="911dd-104">Bu bize bir iş akışı yeniden barındırılan tasarımcıda geçerli olduğundan emin olmak için ilgili bir yordam sağlar.</span><span class="sxs-lookup"><span data-stu-id="911dd-104">This provides us with a procedure to confirm that a workflow in a rehosted designer is valid.</span></span>  
  
 <span data-ttu-id="911dd-105">Bu görevi, iki bölümden oluşur.</span><span class="sxs-lookup"><span data-stu-id="911dd-105">This task has two parts.</span></span> <span data-ttu-id="911dd-106">İlk uygulama sağlamaktır <xref:System.Activities.Presentation.Validation.IValidationErrorService>.</span><span class="sxs-lookup"><span data-stu-id="911dd-106">The first is to provide an implementation <xref:System.Activities.Presentation.Validation.IValidationErrorService>.</span></span>  <span data-ttu-id="911dd-107">Bu arabirimde uygulamak için kritik bir yöntem <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> hangi geçecek, listesini <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> için hata ayıklama günlüğünü hatalara ilişkin bilgileri içeren bir nesne.</span><span class="sxs-lookup"><span data-stu-id="911dd-107">There is one critical method to implement on this interface, <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> which will pass you a list of <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> objects containing information about the errors to the debug log.</span></span>  <span data-ttu-id="911dd-108">Arabirimi uyguladıktan sonra bu uygulama örneği için düzenleme bağlamı yayımlayarak hata bilgileri alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="911dd-108">After implementing the interface, you retrieve the error information by publishing an instance of that implementation to the editing context.</span></span>  
  
### <a name="implement-the-ivalidationerrorservice-interface"></a><span data-ttu-id="911dd-109">IValidationErrorService arabirimini uygulama</span><span class="sxs-lookup"><span data-stu-id="911dd-109">Implement the IValidationErrorService Interface</span></span>  
  
1. <span data-ttu-id="911dd-110">Doğrulama hataları için hata ayıklama günlüğünü dışarı yazılacak basit bir uygulama için bir kod örneği aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="911dd-110">Here is a code sample for a simple implementation that will write out the validation errors to the debug log.</span></span>  
  
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
  
### <a name="publishing-to-the-editing-context"></a><span data-ttu-id="911dd-111">Düzenleme bağlamı yayımlama</span><span class="sxs-lookup"><span data-stu-id="911dd-111">Publishing to the Editing Context</span></span>  
  
1. <span data-ttu-id="911dd-112">Bu düzenleme bağlamı için yayımlama kod aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="911dd-112">Here is the code that will publish this to the editing context.</span></span>  
  
    ```  
    wd.Context.Services.Publish<IValidationErrorService>(new DebugValidationErrorService());  
    ```
