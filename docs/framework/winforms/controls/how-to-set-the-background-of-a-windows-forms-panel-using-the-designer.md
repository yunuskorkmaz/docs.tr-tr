---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Formları Panelinin Arka Planını Ayarlama'
ms.date: 03/30/2017
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: db83cf54-3c69-4b08-ac6c-25b9b5abb1b0
ms.openlocfilehash: 896aa61f3f0900760dffd09bcab6a08bbc01628d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33535724"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel-using-the-designer"></a><span data-ttu-id="03abe-102">Nasıl yapılır: Tasarımcı Kullanarak Windows Formları Panelinin Arka Planını Ayarlama</span><span class="sxs-lookup"><span data-stu-id="03abe-102">How to: Set the Background of a Windows Forms Panel Using the Designer</span></span>
<span data-ttu-id="03abe-103">Windows Forms <xref:System.Windows.Forms.Panel> denetim arka plan rengi ve arka plan resmini görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="03abe-103">A Windows Forms <xref:System.Windows.Forms.Panel> control can display both a background color and a background image.</span></span> <span data-ttu-id="03abe-104"><xref:System.Windows.Forms.Control.BackColor%2A> Özelliği ayarlar etiketler gibi Masası'nda bulunan ve radyo düğmeleri denetimleri için arka plan rengi.</span><span class="sxs-lookup"><span data-stu-id="03abe-104">The <xref:System.Windows.Forms.Control.BackColor%2A> property sets the background color for controls that are contained in the panel, such as labels and radio buttons.</span></span> <span data-ttu-id="03abe-105">Varsa <xref:System.Windows.Forms.Control.BackgroundImage%2A> özelliği ayarlı değil, <xref:System.Windows.Forms.Control.BackColor%2A> seçim bölmesinin tüm doldurur.</span><span class="sxs-lookup"><span data-stu-id="03abe-105">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is not set, the <xref:System.Windows.Forms.Control.BackColor%2A> selection will fill all of the panel.</span></span> <span data-ttu-id="03abe-106">Varsa <xref:System.Windows.Forms.Control.BackgroundImage%2A> özelliği ayarlanmışsa, resim panelinde bulunan denetimleri arkasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="03abe-106">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is set, the image will be displayed behind the controls that are contained in the panel.</span></span>  
  
 <span data-ttu-id="03abe-107">Aşağıdaki yordam gerektiren bir **Windows uygulaması** proje içeren bir form ile bir <xref:System.Windows.Forms.Panel> denetim.</span><span class="sxs-lookup"><span data-stu-id="03abe-107">The following procedure requires a **Windows Application** project with a form that contains a <xref:System.Windows.Forms.Panel> control.</span></span> <span data-ttu-id="03abe-108">Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) ve [nasıl yapılır: Windows Forms denetimlerine ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="03abe-108">For information about how to set up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="03abe-109">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="03abe-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="03abe-110">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="03abe-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="03abe-111">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="03abe-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-set-the-background-in-the-windows-forms-designer"></a><span data-ttu-id="03abe-112">Windows Forms Tasarımcısı'nda arka plan ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="03abe-112">To set the background in the Windows Forms Designer</span></span>  
  
1.  <span data-ttu-id="03abe-113">Seçin <xref:System.Windows.Forms.Panel> denetim.</span><span class="sxs-lookup"><span data-stu-id="03abe-113">Select the <xref:System.Windows.Forms.Panel> control.</span></span>  
  
2.  <span data-ttu-id="03abe-114">İçinde **özellikleri** penceresinde, oku için İleri düğmesini tıklatın <xref:System.Windows.Forms.Control.BackColor%2A> üç sekme penceresiyle görüntülenecek özelliği.</span><span class="sxs-lookup"><span data-stu-id="03abe-114">In the **Properties** window, click the arrow button next to the <xref:System.Windows.Forms.Control.BackColor%2A> property to display a window with three tabs.</span></span>  
  
3.  <span data-ttu-id="03abe-115">Seçin **özel** renk paletini görüntülenecek sekmesi.</span><span class="sxs-lookup"><span data-stu-id="03abe-115">Select the **Custom** tab to display a palette of colors.</span></span>  
  
4.  <span data-ttu-id="03abe-116">Seçin **Web** veya **sistem** renkler için önceden tanımlanmış adlarının bir listesini görüntülemek için sekmesini ve ardından bir rengi seçin.</span><span class="sxs-lookup"><span data-stu-id="03abe-116">Select the **Web** or **System** tab to display a list of predefined names for colors, and then select a color.</span></span>  
  
5.  <span data-ttu-id="03abe-117">İçinde **özellikleri** penceresinde, oku için İleri düğmesini tıklatın <xref:System.Windows.Forms.Control.BackgroundImage%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="03abe-117">In the **Properties** window, click the arrow button next to the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property.</span></span>  
  
6.  <span data-ttu-id="03abe-118">İçinde **açık** iletişim kutusunda, görüntülemek istediğiniz dosyayı seçin.</span><span class="sxs-lookup"><span data-stu-id="03abe-118">In the **Open** dialog box, select the file that you want to display.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03abe-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="03abe-119">See Also</span></span>  
 <xref:System.Windows.Forms.Control.BackColor%2A>  
 <xref:System.Windows.Forms.Control.BackgroundImage%2A>  
 [<span data-ttu-id="03abe-120">Panel Denetimi</span><span class="sxs-lookup"><span data-stu-id="03abe-120">Panel Control</span></span>](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)  
 [<span data-ttu-id="03abe-121">Panel Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="03abe-121">Panel Control Overview</span></span>](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)  
 [<span data-ttu-id="03abe-122">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms Panel Denetimi ile Denetimleri Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="03abe-122">How to: Group Controls with the Windows Forms Panel Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/group-controls-with-wf-panel-control-using-the-designer.md)
