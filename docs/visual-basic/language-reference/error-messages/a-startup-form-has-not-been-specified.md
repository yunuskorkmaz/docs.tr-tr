---
title: Başlangıç formu belirtilmedi
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_NoStartupForm
ms.assetid: 8e04af49-4bef-49de-a7ec-e407e9873da7
ms.openlocfilehash: 9af95b397bef4a19654510619cf0864c8ab7b76f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833574"
---
# <a name="a-startup-form-has-not-been-specified"></a><span data-ttu-id="a0f89-102">Başlangıç formu belirtilmedi</span><span class="sxs-lookup"><span data-stu-id="a0f89-102">A startup form has not been specified</span></span>
<span data-ttu-id="a0f89-103">Uygulamanın kullandığı <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> sınıfı ancak başlangıç formu belirtmiyor.</span><span class="sxs-lookup"><span data-stu-id="a0f89-103">The application uses the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> class but does not specify the startup form.</span></span>  
  
 <span data-ttu-id="a0f89-104">Bu oluşabilir **etkinleştir uygulama çerçevesi** onay kutusunun seçili Proje Tasarımcısı'nda ancak **başlangıç formu** belirtilmedi.</span><span class="sxs-lookup"><span data-stu-id="a0f89-104">This can occur if the **Enable application framework** check box is selected in the project designer but the **Startup form** is not specified.</span></span> <span data-ttu-id="a0f89-105">Daha fazla bilgi için [uygulama sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="a0f89-105">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a0f89-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="a0f89-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="a0f89-107">Uygulama için bir başlangıç nesnesi belirtin.</span><span class="sxs-lookup"><span data-stu-id="a0f89-107">Specify a startup object for the application.</span></span>  
  
     <span data-ttu-id="a0f89-108">Daha fazla bilgi için [uygulama sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="a0f89-108">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
2.  <span data-ttu-id="a0f89-109">Geçersiz kılma <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> ayarlanacak yöntemi <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> özelliğini başlangıç formu.</span><span class="sxs-lookup"><span data-stu-id="a0f89-109">Override the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> method to set the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> property to the startup form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0f89-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0f89-110">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A>
- [<span data-ttu-id="a0f89-111">Visual Basic Uygulama Modeline Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a0f89-111">Overview of the Visual Basic Application Model</span></span>](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)
