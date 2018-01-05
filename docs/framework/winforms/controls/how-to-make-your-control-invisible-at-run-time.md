---
title: "Nasıl yapılır: Çalışma Zamanında Denetiminizi Görünmez Yapma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], making invisible at run time
- invisible controls
- user controls [Windows Forms], invisible
- custom controls [Windows Forms], invisible
- run time [Windows Forms], making controls invisible
ms.assetid: 69eb2e72-32f5-4f79-a157-c2c5f60c1628
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6e28a682c6f3bfc52a293daebeade960c1875bb5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-make-your-control-invisible-at-run-time"></a><span data-ttu-id="c86d9-102">Nasıl yapılır: Çalışma Zamanında Denetiminizi Görünmez Yapma</span><span class="sxs-lookup"><span data-stu-id="c86d9-102">How to: Make Your Control Invisible at Run Time</span></span>
<span data-ttu-id="c86d9-103">Ne zaman çalışma zamanında görünmez bir kullanıcı denetimi oluşturmak isteyebilirsiniz zamanlar vardır.</span><span class="sxs-lookup"><span data-stu-id="c86d9-103">There are times when you might want to create a user control that is invisible at run time.</span></span> <span data-ttu-id="c86d9-104">Örneğin, bir uyarı saati bir denetim ne zaman uyarı sizi uyarabilir dışında görünmez olabilir.</span><span class="sxs-lookup"><span data-stu-id="c86d9-104">For example, a control that is an alarm clock might be invisible except when the alarm was sounding.</span></span> <span data-ttu-id="c86d9-105">Bu ayar kolayca gerçekleştirilir <xref:System.Windows.Forms.Control.Visible%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="c86d9-105">This is easily accomplished by setting the <xref:System.Windows.Forms.Control.Visible%2A> property.</span></span> <span data-ttu-id="c86d9-106">Varsa <xref:System.Windows.Forms.Control.Visible%2A> özelliği `true`, denetiminizi normal olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="c86d9-106">If the <xref:System.Windows.Forms.Control.Visible%2A> property is `true`, your control will appear as normal.</span></span> <span data-ttu-id="c86d9-107">Varsa `false`, denetiminizi gizlenir.</span><span class="sxs-lookup"><span data-stu-id="c86d9-107">If `false`, your control will be hidden.</span></span> <span data-ttu-id="c86d9-108">Denetim kodu görünmez sırasında hala çalışabilir rağmen kullanıcı arabirimi aracılığıyla denetimi ile etkileşim mümkün olmaz.</span><span class="sxs-lookup"><span data-stu-id="c86d9-108">Although code in your control may still run while invisible, you will not be able to interact with the control through the user interface.</span></span> <span data-ttu-id="c86d9-109">Kullanıcı girişi (örneğin, fare tıklamaları) hala yanıt görünmeyen bir denetim oluşturmak istiyorsanız, saydam bir denetim oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c86d9-109">If you want to create an invisible control that still responds to user input (for example, mouse clicks), you should create a transparent control.</span></span> <span data-ttu-id="c86d9-110">Daha fazla bilgi için bkz: [denetiminize saydam arka plan vermiş](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md).</span><span class="sxs-lookup"><span data-stu-id="c86d9-110">For more information, see [Giving Your Control a Transparent Background](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md).</span></span>  
  
### <a name="to-make-your-control-invisible-at-run-time"></a><span data-ttu-id="c86d9-111">Çalışma zamanında denetiminizi görünmez yapmak için</span><span class="sxs-lookup"><span data-stu-id="c86d9-111">To make your control invisible at run time</span></span>  
  
1.  <span data-ttu-id="c86d9-112">Ayarlama <xref:System.Windows.Forms.Control.Visible%2A> özelliğine `false`.</span><span class="sxs-lookup"><span data-stu-id="c86d9-112">Set the <xref:System.Windows.Forms.Control.Visible%2A> property to `false`.</span></span>  
  
    ```vb  
    ' To set the Visible property from within your object's own code.  
    Me.Visible = False  
    ' To set the Visible property from another object.  
    myControl1.Visible = False  
    ```  
  
    ```csharp  
    // To set the Visible property from within your object's own code.  
    this.Visible = false;  
    // To set the Visible property from another object.  
    myControl1.Visible = false;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c86d9-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c86d9-113">See Also</span></span>  
 <xref:System.Windows.Forms.Control.Visible%2A>  
 [<span data-ttu-id="c86d9-114">.NET Framework ile Özel Windows Forms Denetimleri Geliştirme</span><span class="sxs-lookup"><span data-stu-id="c86d9-114">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [<span data-ttu-id="c86d9-115">Nasıl yapılır: Denetiminize Saydam Arka Plan Verme</span><span class="sxs-lookup"><span data-stu-id="c86d9-115">How to: Give Your Control a Transparent Background</span></span>](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)
