---
title: 'Nasıl yapılır: Tasarım Zamanında Windows Formundaki Denetimler için ToolTips Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
ms.openlocfilehash: 7f698a517fbf72ceafde4a117b4d92dd9d352834
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44360261"
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a><span data-ttu-id="38ec1-102">Nasıl yapılır: Tasarım Zamanında Windows Formundaki Denetimler için ToolTips Ayarlama</span><span class="sxs-lookup"><span data-stu-id="38ec1-102">How to: Set ToolTips for Controls on a Windows Form at Design Time</span></span>
<span data-ttu-id="38ec1-103">Ayarlayabileceğiniz bir <xref:System.Windows.Forms.ToolTip> kodda veya Windows Forms Tasarımcısı'nda bir dize.</span><span class="sxs-lookup"><span data-stu-id="38ec1-103">You can set a <xref:System.Windows.Forms.ToolTip> string in code or in the Windows Forms Designer.</span></span> <span data-ttu-id="38ec1-104">Hakkında daha fazla bilgi için <xref:System.Windows.Forms.ToolTip> bileşeni Bkz [ToolTip bileşenine genel bakış](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="38ec1-104">For more information about the <xref:System.Windows.Forms.ToolTip> component, see [ToolTip Component Overview](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="38ec1-105">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="38ec1-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="38ec1-106">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="38ec1-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="38ec1-107">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="38ec1-107">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-set-a-tooltip-programmatically"></a><span data-ttu-id="38ec1-108">Bir araç ipucu program üzerinden ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="38ec1-108">To set a ToolTip programmatically</span></span>  
  
1.  <span data-ttu-id="38ec1-109">Araç İpucu görüntüleyen denetimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="38ec1-109">Add the control that will display the ToolTip.</span></span>  
  
2.  <span data-ttu-id="38ec1-110">Kullanım <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> yöntemi <xref:System.Windows.Forms.ToolTip> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="38ec1-110">Use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method of the <xref:System.Windows.Forms.ToolTip> component.</span></span>  
  
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
  
### <a name="to-set-a-tooltip-in-the-designer"></a><span data-ttu-id="38ec1-111">Tasarımcıda bir araç ipucu ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="38ec1-111">To set a ToolTip in the designer</span></span>  
  
1.  <span data-ttu-id="38ec1-112">Ekleme bir <xref:System.Windows.Forms.ToolTip> forma bileşen.</span><span class="sxs-lookup"><span data-stu-id="38ec1-112">Add a <xref:System.Windows.Forms.ToolTip> component to the form.</span></span>  
  
2.  <span data-ttu-id="38ec1-113">Araç ipucunu görüntülemek veya forma ekler denetimi seçin.</span><span class="sxs-lookup"><span data-stu-id="38ec1-113">Select the control that will display the ToolTip, or add it to the form.</span></span>  
  
3.  <span data-ttu-id="38ec1-114">İçinde **özellikleri** penceresinde **ToolTip1 araç ipucu** uygun bir metin dizesi değeri.</span><span class="sxs-lookup"><span data-stu-id="38ec1-114">In the **Properties** window, set the **ToolTip on ToolTip1** value to an appropriate string of text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38ec1-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="38ec1-115">See Also</span></span>  
 [<span data-ttu-id="38ec1-116">ToolTip Bileşenine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="38ec1-116">ToolTip Component Overview</span></span>](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md)  
 [<span data-ttu-id="38ec1-117">Nasıl yapılır: Windows Forms ToolTip Bileşeninin Gecikmesini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="38ec1-117">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)  
 [<span data-ttu-id="38ec1-118">ToolTip Bileşeni</span><span class="sxs-lookup"><span data-stu-id="38ec1-118">ToolTip Component</span></span>](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)
