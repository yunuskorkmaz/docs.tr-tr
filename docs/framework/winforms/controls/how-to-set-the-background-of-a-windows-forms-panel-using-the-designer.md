---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms Panelinin Arka Planını Ayarlama'
ms.date: 03/30/2017
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: db83cf54-3c69-4b08-ac6c-25b9b5abb1b0
ms.openlocfilehash: 888b1910902819b847d7d622f7b086fec82d669d
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59334360"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel-using-the-designer"></a><span data-ttu-id="cd8e4-102">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms Panelinin Arka Planını Ayarlama</span><span class="sxs-lookup"><span data-stu-id="cd8e4-102">How to: Set the Background of a Windows Forms Panel Using the Designer</span></span>
<span data-ttu-id="cd8e4-103">Bir Windows Forms <xref:System.Windows.Forms.Panel> denetim arka plan rengi hem de arka plan görüntüsü görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cd8e4-103">A Windows Forms <xref:System.Windows.Forms.Panel> control can display both a background color and a background image.</span></span> <span data-ttu-id="cd8e4-104"><xref:System.Windows.Forms.Control.BackColor%2A> Özelliği etiketler gibi panelinde bulunan ve radyo düğmeleri, denetimleri arka plan rengini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="cd8e4-104">The <xref:System.Windows.Forms.Control.BackColor%2A> property sets the background color for controls that are contained in the panel, such as labels and radio buttons.</span></span> <span data-ttu-id="cd8e4-105">Varsa <xref:System.Windows.Forms.Control.BackgroundImage%2A> özelliği ayarlı değil, <xref:System.Windows.Forms.Control.BackColor%2A> seçimi tüm panel doldurur.</span><span class="sxs-lookup"><span data-stu-id="cd8e4-105">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is not set, the <xref:System.Windows.Forms.Control.BackColor%2A> selection will fill all of the panel.</span></span> <span data-ttu-id="cd8e4-106">Varsa <xref:System.Windows.Forms.Control.BackgroundImage%2A> özelliği ayarlanmışsa, görüntünün arkasındaki panelde bulunan denetimleri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="cd8e4-106">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is set, the image will be displayed behind the controls that are contained in the panel.</span></span>  
  
 <span data-ttu-id="cd8e4-107">Aşağıdaki yordamı gerektiren bir **Windows uygulama** proje içeren bir form bir <xref:System.Windows.Forms.Panel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="cd8e4-107">The following procedure requires a **Windows Application** project with a form that contains a <xref:System.Windows.Forms.Panel> control.</span></span> <span data-ttu-id="cd8e4-108">Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: Bir Windows Forms uygulaması projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms'a denetimler ekleme](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="cd8e4-108">For information about how to set up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cd8e4-109">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="cd8e4-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="cd8e4-110">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="cd8e4-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="cd8e4-111">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="cd8e4-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-set-the-background-in-the-windows-forms-designer"></a><span data-ttu-id="cd8e4-112">Windows Form Tasarımcısı'nda arka planını ayarlama</span><span class="sxs-lookup"><span data-stu-id="cd8e4-112">To set the background in the Windows Forms Designer</span></span>  
  
1. <span data-ttu-id="cd8e4-113">Seçin <xref:System.Windows.Forms.Panel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="cd8e4-113">Select the <xref:System.Windows.Forms.Panel> control.</span></span>  
  
2. <span data-ttu-id="cd8e4-114">İçinde **özellikleri** penceresinde, oku, İleri düğmesine tıklayın <xref:System.Windows.Forms.Control.BackColor%2A> bir penceresi üç sekme ile görüntülenecek özelliği.</span><span class="sxs-lookup"><span data-stu-id="cd8e4-114">In the **Properties** window, click the arrow button next to the <xref:System.Windows.Forms.Control.BackColor%2A> property to display a window with three tabs.</span></span>  
  
3. <span data-ttu-id="cd8e4-115">Seçin **özel** renkler paleti görüntülemek için sekmesinde.</span><span class="sxs-lookup"><span data-stu-id="cd8e4-115">Select the **Custom** tab to display a palette of colors.</span></span>  
  
4. <span data-ttu-id="cd8e4-116">Seçin **Web** veya **sistem** renkler için önceden tanımlanmış adlarının bir listesini görüntülemek için sekmesinde ve bir renk seçin.</span><span class="sxs-lookup"><span data-stu-id="cd8e4-116">Select the **Web** or **System** tab to display a list of predefined names for colors, and then select a color.</span></span>  
  
5. <span data-ttu-id="cd8e4-117">İçinde **özellikleri** penceresinde, oku, İleri düğmesine tıklayın <xref:System.Windows.Forms.Control.BackgroundImage%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="cd8e4-117">In the **Properties** window, click the arrow button next to the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property.</span></span>  
  
6. <span data-ttu-id="cd8e4-118">İçinde **açık** iletişim kutusunda, görüntülemek istediğiniz dosyayı seçin.</span><span class="sxs-lookup"><span data-stu-id="cd8e4-118">In the **Open** dialog box, select the file that you want to display.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd8e4-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd8e4-119">See also</span></span>

- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [<span data-ttu-id="cd8e4-120">Panel Denetimi</span><span class="sxs-lookup"><span data-stu-id="cd8e4-120">Panel Control</span></span>](panel-control-windows-forms.md)
- [<span data-ttu-id="cd8e4-121">Panel Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cd8e4-121">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
- [<span data-ttu-id="cd8e4-122">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms Panel Denetimi ile Denetimleri Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="cd8e4-122">How to: Group Controls with the Windows Forms Panel Control Using the Designer</span></span>](group-controls-with-wf-panel-control-using-the-designer.md)
