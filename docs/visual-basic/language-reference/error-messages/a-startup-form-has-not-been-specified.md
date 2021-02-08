---
description: 'Hakkında daha fazla bilgi edinin: bir başlangıç formu belirtilmedi'
title: Başlangıç formu belirtilmedi
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_NoStartupForm
ms.assetid: 8e04af49-4bef-49de-a7ec-e407e9873da7
ms.openlocfilehash: 4b00890f07121ef55ce49978842010cc54aba29b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797191"
---
# <a name="a-startup-form-has-not-been-specified"></a><span data-ttu-id="5847d-103">Başlangıç formu belirtilmedi</span><span class="sxs-lookup"><span data-stu-id="5847d-103">A startup form has not been specified</span></span>

<span data-ttu-id="5847d-104">Uygulama sınıfı kullanır, <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> ancak başlangıç formunu belirtmez.</span><span class="sxs-lookup"><span data-stu-id="5847d-104">The application uses the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> class but does not specify the startup form.</span></span>  
  
 <span data-ttu-id="5847d-105">Bu durum proje tasarımcısında **uygulama çerçevesini etkinleştir** onay kutusu işaretliyse, ancak **başlangıç formu** belirtilmediğinde ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="5847d-105">This can occur if the **Enable application framework** check box is selected in the project designer but the **Startup form** is not specified.</span></span> <span data-ttu-id="5847d-106">Daha fazla bilgi için bkz. [uygulama sayfası, proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="5847d-106">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5847d-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="5847d-107">To correct this error</span></span>  
  
1. <span data-ttu-id="5847d-108">Uygulama için bir başlangıç nesnesi belirtin.</span><span class="sxs-lookup"><span data-stu-id="5847d-108">Specify a startup object for the application.</span></span>  
  
     <span data-ttu-id="5847d-109">Daha fazla bilgi için bkz. [uygulama sayfası, proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="5847d-109">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
2. <span data-ttu-id="5847d-110"><xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>Özelliği başlangıç formu olarak ayarlamak için yöntemini geçersiz kılın <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> .</span><span class="sxs-lookup"><span data-stu-id="5847d-110">Override the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> method to set the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> property to the startup form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5847d-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5847d-111">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A>
- [<span data-ttu-id="5847d-112">Visual Basic Uygulama Modeline Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5847d-112">Overview of the Visual Basic Application Model</span></span>](../../developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)
