---
title: Başlangıç formu belirtilmedi
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_NoStartupForm
ms.assetid: 8e04af49-4bef-49de-a7ec-e407e9873da7
ms.openlocfilehash: 2bbae640ca65c95411cae24a9506fe2076b62cba
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59296478"
---
# <a name="a-startup-form-has-not-been-specified"></a><span data-ttu-id="7b692-102">Başlangıç formu belirtilmedi</span><span class="sxs-lookup"><span data-stu-id="7b692-102">A startup form has not been specified</span></span>
<span data-ttu-id="7b692-103">Uygulamanın kullandığı <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> sınıfı ancak başlangıç formu belirtmiyor.</span><span class="sxs-lookup"><span data-stu-id="7b692-103">The application uses the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> class but does not specify the startup form.</span></span>  
  
 <span data-ttu-id="7b692-104">Bu oluşabilir **etkinleştir uygulama çerçevesi** onay kutusunun seçili Proje Tasarımcısı'nda ancak **başlangıç formu** belirtilmedi.</span><span class="sxs-lookup"><span data-stu-id="7b692-104">This can occur if the **Enable application framework** check box is selected in the project designer but the **Startup form** is not specified.</span></span> <span data-ttu-id="7b692-105">Daha fazla bilgi için [uygulama sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="7b692-105">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7b692-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="7b692-106">To correct this error</span></span>  
  
1. <span data-ttu-id="7b692-107">Uygulama için bir başlangıç nesnesi belirtin.</span><span class="sxs-lookup"><span data-stu-id="7b692-107">Specify a startup object for the application.</span></span>  
  
     <span data-ttu-id="7b692-108">Daha fazla bilgi için [uygulama sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="7b692-108">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
2. <span data-ttu-id="7b692-109">Geçersiz kılma <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> ayarlanacak yöntemi <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> özelliğini başlangıç formu.</span><span class="sxs-lookup"><span data-stu-id="7b692-109">Override the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> method to set the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> property to the startup form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b692-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7b692-110">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A>
- [<span data-ttu-id="7b692-111">Visual Basic Uygulama Modeline Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7b692-111">Overview of the Visual Basic Application Model</span></span>](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)
