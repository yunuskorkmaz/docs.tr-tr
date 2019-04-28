---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms TabControl ile Sekme Ekleme ve Kaldırma'
ms.date: 03/30/2017
helpviewer_keywords:
- tabs [Windows Forms], removing from pages
- TabPage control
- TabPage control [Windows Forms], adding and removing tabs
- tabs [Windows Forms], adding to pages
- tab pages
ms.assetid: 480633db-413a-45d2-9c8f-0427cc13adbe
ms.openlocfilehash: 23fe9fa2b8405a6ebe66e8f0cee1d81d45f2395b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61640380"
---
# <a name="how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol-using-the-designer"></a><span data-ttu-id="429b4-102">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms TabControl ile Sekme Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="429b4-102">How to: Add and Remove Tabs with the Windows Forms TabControl Using the Designer</span></span>
<span data-ttu-id="429b4-103">Yerleştirdiğinizde bir <xref:System.Windows.Forms.TabControl> denetim formunuzda, iki sekme varsayılan olarak içerir.</span><span class="sxs-lookup"><span data-stu-id="429b4-103">When you place a <xref:System.Windows.Forms.TabControl> control on your form, it contains two tabs by default.</span></span> <span data-ttu-id="429b4-104">Ekleyebilir veya tasarımcı kullanarak sekme kaldırın.</span><span class="sxs-lookup"><span data-stu-id="429b4-104">You can add or remove tabs using the designer.</span></span>  
  
 <span data-ttu-id="429b4-105">Aşağıdaki yordam gerektirir bir **Windows uygulama** proje içeren bir form içeren bir <xref:System.Windows.Forms.TabControl> denetimi.</span><span class="sxs-lookup"><span data-stu-id="429b4-105">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.TabControl> control.</span></span> <span data-ttu-id="429b4-106">Bu tür bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: Bir Windows Forms uygulaması projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms'a denetimler ekleme](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="429b4-106">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="429b4-107">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="429b4-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="429b4-108">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="429b4-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="429b4-109">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="429b4-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-or-remove-a-tab-using-the-designer"></a><span data-ttu-id="429b4-110">Ekleme veya kaldırma Tasarımcı kullanarak sekme</span><span class="sxs-lookup"><span data-stu-id="429b4-110">To add or remove a tab using the designer</span></span>  
  
- <span data-ttu-id="429b4-111">Denetimin akıllı etiketinde tıklayın **Sekme Ekle** veya **sekmesini Kaldır**</span><span class="sxs-lookup"><span data-stu-id="429b4-111">On the control's smart tag, click **Add Tab** or **Remove Tab**</span></span>  
  
     <span data-ttu-id="429b4-112">-veya-</span><span class="sxs-lookup"><span data-stu-id="429b4-112">-or-</span></span>  
  
     <span data-ttu-id="429b4-113">İçinde **özellikleri** penceresinde tıklayın **üç nokta** düğmesine (![VisualStudioEllipsesButton ekran](../media/vbellipsesbutton.png "vbEllipsesButton")) yanındaki <xref:System.Windows.Forms.TabControl.TabPages%2A> açmak için özellik **TabPage Koleksiyonu Düzenleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="429b4-113">In the **Properties** window, click the **Ellipsis** button (![VisualStudioEllipsesButton screenshot](../media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.TabControl.TabPages%2A> property to open the **TabPage Collection Editor**.</span></span> <span data-ttu-id="429b4-114">Tıklayın **Ekle** veya **Kaldır** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="429b4-114">Click the **Add** or **Remove** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="429b4-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="429b4-115">See also</span></span>

- [<span data-ttu-id="429b4-116">TabControl Denetimi</span><span class="sxs-lookup"><span data-stu-id="429b4-116">TabControl Control</span></span>](tabcontrol-control-windows-forms.md)
- [<span data-ttu-id="429b4-117">TabControl Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="429b4-117">TabControl Control Overview</span></span>](tabcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="429b4-118">Nasıl yapılır: Sekme sayfasına denetim ekleme</span><span class="sxs-lookup"><span data-stu-id="429b4-118">How to: Add a Control to a Tab Page</span></span>](how-to-add-a-control-to-a-tab-page.md)
- [<span data-ttu-id="429b4-119">Nasıl yapılır: Sekme sayfalarını devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="429b4-119">How to: Disable Tab Pages</span></span>](how-to-disable-tab-pages.md)
- [<span data-ttu-id="429b4-120">Nasıl yapılır: Windows Forms Tabcontrol'un görünüşünü değiştirme</span><span class="sxs-lookup"><span data-stu-id="429b4-120">How to: Change the Appearance of the Windows Forms TabControl</span></span>](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
