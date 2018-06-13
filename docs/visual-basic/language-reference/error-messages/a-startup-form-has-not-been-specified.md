---
title: Başlangıç formu belirtilmedi
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_NoStartupForm
ms.assetid: 8e04af49-4bef-49de-a7ec-e407e9873da7
ms.openlocfilehash: 699d20e6afb2335336b3652be5907f0dd72299fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586792"
---
# <a name="a-startup-form-has-not-been-specified"></a><span data-ttu-id="d027f-102">Başlangıç formu belirtilmedi</span><span class="sxs-lookup"><span data-stu-id="d027f-102">A startup form has not been specified</span></span>
<span data-ttu-id="d027f-103">Uygulamanın kullandığı <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> sınıf ancak başlangıç formu belirtmiyor.</span><span class="sxs-lookup"><span data-stu-id="d027f-103">The application uses the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> class but does not specify the startup form.</span></span>  
  
 <span data-ttu-id="d027f-104">Bu durum ortaya çıkabilir **etkinleştir uygulama çerçevesi** Proje Tasarımcısı'nda onay kutusu seçili ancak **başlangıç formu** belirtilmedi.</span><span class="sxs-lookup"><span data-stu-id="d027f-104">This can occur if the **Enable application framework** check box is selected in the project designer but the **Startup form** is not specified.</span></span> <span data-ttu-id="d027f-105">Daha fazla bilgi için bkz: [uygulama sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="d027f-105">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d027f-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="d027f-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="d027f-107">Uygulama için bir başlangıç nesnesi belirtin.</span><span class="sxs-lookup"><span data-stu-id="d027f-107">Specify a startup object for the application.</span></span>  
  
     <span data-ttu-id="d027f-108">Daha fazla bilgi için bkz: [uygulama sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="d027f-108">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
2.  <span data-ttu-id="d027f-109">Geçersiz kılma <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> ayarlamak için yöntemin <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> başlangıç formu özelliğine.</span><span class="sxs-lookup"><span data-stu-id="d027f-109">Override the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> method to set the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> property to the startup form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d027f-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d027f-110">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A>  
 [<span data-ttu-id="d027f-111">Visual Basic Uygulama Modeline Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d027f-111">Overview of the Visual Basic Application Model</span></span>](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)
