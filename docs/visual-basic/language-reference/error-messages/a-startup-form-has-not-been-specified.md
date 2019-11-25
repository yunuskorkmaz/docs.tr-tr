---
title: Başlangıç formu belirtilmedi
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_NoStartupForm
ms.assetid: 8e04af49-4bef-49de-a7ec-e407e9873da7
ms.openlocfilehash: 301f249e6222c929d2c513964ecbb21df5fbc47f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976188"
---
# <a name="a-startup-form-has-not-been-specified"></a><span data-ttu-id="fbb5a-102">Başlangıç formu belirtilmedi</span><span class="sxs-lookup"><span data-stu-id="fbb5a-102">A startup form has not been specified</span></span>

<span data-ttu-id="fbb5a-103">Uygulama <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> sınıfını kullanır, ancak başlangıç formunu belirtmez.</span><span class="sxs-lookup"><span data-stu-id="fbb5a-103">The application uses the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> class but does not specify the startup form.</span></span>  
  
 <span data-ttu-id="fbb5a-104">Bu durum proje tasarımcısında **uygulama çerçevesini etkinleştir** onay kutusu işaretliyse, ancak **başlangıç formu** belirtilmediğinde ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="fbb5a-104">This can occur if the **Enable application framework** check box is selected in the project designer but the **Startup form** is not specified.</span></span> <span data-ttu-id="fbb5a-105">Daha fazla bilgi için bkz. [uygulama sayfası, proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="fbb5a-105">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fbb5a-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="fbb5a-106">To correct this error</span></span>  
  
1. <span data-ttu-id="fbb5a-107">Uygulama için bir başlangıç nesnesi belirtin.</span><span class="sxs-lookup"><span data-stu-id="fbb5a-107">Specify a startup object for the application.</span></span>  
  
     <span data-ttu-id="fbb5a-108">Daha fazla bilgi için bkz. [uygulama sayfası, proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="fbb5a-108">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
2. <span data-ttu-id="fbb5a-109"><xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> özelliğini başlangıç formu olarak ayarlamak için <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> yöntemini geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="fbb5a-109">Override the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> method to set the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> property to the startup form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbb5a-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fbb5a-110">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A>
- [<span data-ttu-id="fbb5a-111">Visual Basic Uygulama Modeline Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="fbb5a-111">Overview of the Visual Basic Application Model</span></span>](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)
