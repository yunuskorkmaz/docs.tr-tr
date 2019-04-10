---
title: 'Nasıl yapılır: Çalışma Zamanında Denetiminizi Görünmez Yapma'
ms.date: 03/30/2017
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
ms.openlocfilehash: e9af529541a40a951d6defea180dbbef04c8f3be
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59345904"
---
# <a name="how-to-make-your-control-invisible-at-run-time"></a><span data-ttu-id="f25f2-102">Nasıl yapılır: Çalışma Zamanında Denetiminizi Görünmez Yapma</span><span class="sxs-lookup"><span data-stu-id="f25f2-102">How to: Make Your Control Invisible at Run Time</span></span>
<span data-ttu-id="f25f2-103">Çalışma zamanında görünmez olan bir kullanıcı denetimi oluşturmak isteyebilirsiniz zamanlar vardır.</span><span class="sxs-lookup"><span data-stu-id="f25f2-103">There are times when you might want to create a user control that is invisible at run time.</span></span> <span data-ttu-id="f25f2-104">Örneğin, bir uyarı saati bir denetim ne zaman uyarı sizi uyarabilir dışında görünmez olabilir.</span><span class="sxs-lookup"><span data-stu-id="f25f2-104">For example, a control that is an alarm clock might be invisible except when the alarm was sounding.</span></span> <span data-ttu-id="f25f2-105">Bu ayarlayarak kolayca gerçekleştirilir <xref:System.Windows.Forms.Control.Visible%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="f25f2-105">This is easily accomplished by setting the <xref:System.Windows.Forms.Control.Visible%2A> property.</span></span> <span data-ttu-id="f25f2-106">Varsa <xref:System.Windows.Forms.Control.Visible%2A> özelliği `true`, Denetim normal olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="f25f2-106">If the <xref:System.Windows.Forms.Control.Visible%2A> property is `true`, your control will appear as normal.</span></span> <span data-ttu-id="f25f2-107">Varsa `false`, denetiminizin gizlenir.</span><span class="sxs-lookup"><span data-stu-id="f25f2-107">If `false`, your control will be hidden.</span></span> <span data-ttu-id="f25f2-108">Denetiminiz kodunda görünmez hala çalışabilir ancak kullanıcı arabirimi aracılığıyla denetimi ile etkileşim kurmak mümkün olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="f25f2-108">Although code in your control may still run while invisible, you will not be able to interact with the control through the user interface.</span></span> <span data-ttu-id="f25f2-109">Kullanıcı girişi (örneğin, fare tıklamaları) hala yanıt veren görünmeyen bir denetim oluşturmak istiyorsanız, saydam bir denetimi oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f25f2-109">If you want to create an invisible control that still responds to user input (for example, mouse clicks), you should create a transparent control.</span></span> <span data-ttu-id="f25f2-110">Daha fazla bilgi için [denetiminiz saydam bir arka plan verme](how-to-give-your-control-a-transparent-background.md).</span><span class="sxs-lookup"><span data-stu-id="f25f2-110">For more information, see [Giving Your Control a Transparent Background](how-to-give-your-control-a-transparent-background.md).</span></span>  
  
### <a name="to-make-your-control-invisible-at-run-time"></a><span data-ttu-id="f25f2-111">İçin çalışma zamanında denetiminizi görünmez yapma</span><span class="sxs-lookup"><span data-stu-id="f25f2-111">To make your control invisible at run time</span></span>  
  
1. <span data-ttu-id="f25f2-112">Ayarlama <xref:System.Windows.Forms.Control.Visible%2A> özelliğini `false`.</span><span class="sxs-lookup"><span data-stu-id="f25f2-112">Set the <xref:System.Windows.Forms.Control.Visible%2A> property to `false`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f25f2-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f25f2-113">See also</span></span>

- <xref:System.Windows.Forms.Control.Visible%2A>
- [<span data-ttu-id="f25f2-114">.NET Framework ile Özel Windows Forms Denetimleri Geliştirme</span><span class="sxs-lookup"><span data-stu-id="f25f2-114">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="f25f2-115">Nasıl yapılır: Denetiminize Saydam Arka Plan Verme</span><span class="sxs-lookup"><span data-stu-id="f25f2-115">How to: Give Your Control a Transparent Background</span></span>](how-to-give-your-control-a-transparent-background.md)
