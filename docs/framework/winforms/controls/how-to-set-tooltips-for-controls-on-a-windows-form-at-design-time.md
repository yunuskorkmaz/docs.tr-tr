---
title: "Nasıl yapılır: Tasarım Zamanında Windows Formundaki Denetimler için ToolTips Ayarlama"
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
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 28a83a623329a7bf0162bb9feb0dc21bb73611cf
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a><span data-ttu-id="cdd90-102">Nasıl yapılır: Tasarım Zamanında Windows Formundaki Denetimler için ToolTips Ayarlama</span><span class="sxs-lookup"><span data-stu-id="cdd90-102">How to: Set ToolTips for Controls on a Windows Form at Design Time</span></span>
<span data-ttu-id="cdd90-103">Ayarlayabileceğiniz bir <xref:System.Windows.Forms.ToolTip> kodunda ya da Windows Form Tasarımcısı dize.</span><span class="sxs-lookup"><span data-stu-id="cdd90-103">You can set a <xref:System.Windows.Forms.ToolTip> string in code or in the Windows Forms Designer.</span></span> <span data-ttu-id="cdd90-104">Hakkında daha fazla bilgi için <xref:System.Windows.Forms.ToolTip> bileşeni Bkz [ToolTip bileşenine genel bakış](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="cdd90-104">For more information about the <xref:System.Windows.Forms.ToolTip> component, see [ToolTip Component Overview](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cdd90-105">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="cdd90-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="cdd90-106">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="cdd90-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="cdd90-107">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="cdd90-107">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-set-a-tooltip-programmatically"></a><span data-ttu-id="cdd90-108">Bir araç ipucu programlı olarak ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="cdd90-108">To set a ToolTip programmatically</span></span>  
  
1.  <span data-ttu-id="cdd90-109">Araç İpucu görüntüler denetimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cdd90-109">Add the control that will display the ToolTip.</span></span>  
  
2.  <span data-ttu-id="cdd90-110">Kullanım <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> yöntemi <xref:System.Windows.Forms.ToolTip> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="cdd90-110">Use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method of the <xref:System.Windows.Forms.ToolTip> component.</span></span>  
  
    ```vb  
    ' In this example, Button1 is the control to display the ToolTip.  
    ToolTip1.SetToolTip(Button1, "Save changes")  
    ```  
  
    ```csharp  
    // In this example, button1 is the control to display the ToolTip.  
    toolTip1.SetToolTip(button1, "Save changes");  
    ```  
  
    ```cpp  
    // In this example, button1 is the control to display the ToolTip.  
    toolTip1->SetToolTip(button1, "Save changes");  
    ```  
  
### <a name="to-set-a-tooltip-in-the-designer"></a><span data-ttu-id="cdd90-111">Bir araç ipucu Designer'da ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="cdd90-111">To set a ToolTip in the designer</span></span>  
  
1.  <span data-ttu-id="cdd90-112">Ekleme bir <xref:System.Windows.Forms.ToolTip> forma bileşen.</span><span class="sxs-lookup"><span data-stu-id="cdd90-112">Add a <xref:System.Windows.Forms.ToolTip> component to the form.</span></span>  
  
2.  <span data-ttu-id="cdd90-113">Araç ipucu görüntülemek veya forma ekler denetimi seçin.</span><span class="sxs-lookup"><span data-stu-id="cdd90-113">Select the control that will display the ToolTip, or add it to the form.</span></span>  
  
3.  <span data-ttu-id="cdd90-114">İçinde **özellikleri** penceresindeki ayarlayın **araç ipucu ToolTip1 üzerinde** uygun bir metin dizesini değerine.</span><span class="sxs-lookup"><span data-stu-id="cdd90-114">In the **Properties** window, set the **ToolTip on ToolTip1** value to an appropriate string of text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdd90-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cdd90-115">See Also</span></span>  
 [<span data-ttu-id="cdd90-116">ToolTip Bileşenine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cdd90-116">ToolTip Component Overview</span></span>](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md)  
 [<span data-ttu-id="cdd90-117">Nasıl yapılır: Windows Forms ToolTip Bileşeninin Gecikmesini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="cdd90-117">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)  
 [<span data-ttu-id="cdd90-118">ToolTip Bileşeni</span><span class="sxs-lookup"><span data-stu-id="cdd90-118">ToolTip Component</span></span>](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)
