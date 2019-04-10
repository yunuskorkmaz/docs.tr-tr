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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59219765"
---
# <a name="how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol-using-the-designer"></a><span data-ttu-id="ae168-102">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms TabControl ile Sekme Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="ae168-102">How to: Add and Remove Tabs with the Windows Forms TabControl Using the Designer</span></span>
<span data-ttu-id="ae168-103">Yerleştirdiğinizde bir <xref:System.Windows.Forms.TabControl> denetim formunuzda, iki sekme varsayılan olarak içerir.</span><span class="sxs-lookup"><span data-stu-id="ae168-103">When you place a <xref:System.Windows.Forms.TabControl> control on your form, it contains two tabs by default.</span></span> <span data-ttu-id="ae168-104">Ekleyebilir veya tasarımcı kullanarak sekme kaldırın.</span><span class="sxs-lookup"><span data-stu-id="ae168-104">You can add or remove tabs using the designer.</span></span>  
  
 <span data-ttu-id="ae168-105">Aşağıdaki yordam gerektirir bir **Windows uygulama** proje içeren bir form içeren bir <xref:System.Windows.Forms.TabControl> denetimi.</span><span class="sxs-lookup"><span data-stu-id="ae168-105">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.TabControl> control.</span></span> <span data-ttu-id="ae168-106">Bu tür bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: Bir Windows Forms uygulaması projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms'a denetimler ekleme](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="ae168-106">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ae168-107">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="ae168-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="ae168-108">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="ae168-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="ae168-109">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="ae168-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-or-remove-a-tab-using-the-designer"></a><span data-ttu-id="ae168-110">Ekleme veya kaldırma Tasarımcı kullanarak sekme</span><span class="sxs-lookup"><span data-stu-id="ae168-110">To add or remove a tab using the designer</span></span>  
  
-   <span data-ttu-id="ae168-111">Denetimin akıllı etiketinde tıklayın **Sekme Ekle** veya **sekmesini Kaldır**</span><span class="sxs-lookup"><span data-stu-id="ae168-111">On the control's smart tag, click **Add Tab** or **Remove Tab**</span></span>  
  
     <span data-ttu-id="ae168-112">-veya-</span><span class="sxs-lookup"><span data-stu-id="ae168-112">-or-</span></span>  
  
     <span data-ttu-id="ae168-113">İçinde **özellikleri** penceresinde tıklayın **üç nokta** düğmesine (![VisualStudioEllipsesButton ekran](../media/vbellipsesbutton.png "vbEllipsesButton")) yanındaki <xref:System.Windows.Forms.TabControl.TabPages%2A> açmak için özellik **TabPage Koleksiyonu Düzenleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="ae168-113">In the **Properties** window, click the **Ellipsis** button (![VisualStudioEllipsesButton screenshot](../media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.TabControl.TabPages%2A> property to open the **TabPage Collection Editor**.</span></span> <span data-ttu-id="ae168-114">Tıklayın **Ekle** veya **Kaldır** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="ae168-114">Click the **Add** or **Remove** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae168-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae168-115">See also</span></span>

- [<span data-ttu-id="ae168-116">TabControl Denetimi</span><span class="sxs-lookup"><span data-stu-id="ae168-116">TabControl Control</span></span>](tabcontrol-control-windows-forms.md)
- [<span data-ttu-id="ae168-117">TabControl Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ae168-117">TabControl Control Overview</span></span>](tabcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="ae168-118">Nasıl yapılır: Sekme Sayfasına Denetim Ekleme</span><span class="sxs-lookup"><span data-stu-id="ae168-118">How to: Add a Control to a Tab Page</span></span>](how-to-add-a-control-to-a-tab-page.md)
- [<span data-ttu-id="ae168-119">Nasıl yapılır: Sekme Sayfalarını Devre Dışı Bırakma</span><span class="sxs-lookup"><span data-stu-id="ae168-119">How to: Disable Tab Pages</span></span>](how-to-disable-tab-pages.md)
- [<span data-ttu-id="ae168-120">Nasıl yapılır: Windows Forms TabControl Görünümünü Değiştirme</span><span class="sxs-lookup"><span data-stu-id="ae168-120">How to: Change the Appearance of the Windows Forms TabControl</span></span>](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
