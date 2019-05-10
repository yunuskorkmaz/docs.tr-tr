---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms Panelinin Arka Planını Ayarlama'
ms.date: 03/30/2017
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: db83cf54-3c69-4b08-ac6c-25b9b5abb1b0
ms.openlocfilehash: 6927a7118c43ced03623a9764a3ef1e0814c95cb
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211636"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel-using-the-designer"></a><span data-ttu-id="836f3-102">Nasıl yapılır: Tasarımcı kullanarak Windows Forms panelinin arka planını ayarlama</span><span class="sxs-lookup"><span data-stu-id="836f3-102">How to: Set the background of a Windows Forms panel using the Designer</span></span>

<span data-ttu-id="836f3-103">Bir Windows Forms <xref:System.Windows.Forms.Panel> denetim arka plan rengi hem de arka plan görüntüsü görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="836f3-103">A Windows Forms <xref:System.Windows.Forms.Panel> control can display both a background color and a background image.</span></span> <span data-ttu-id="836f3-104"><xref:System.Windows.Forms.Control.BackColor%2A> Özelliği etiketler gibi panelinde bulunan ve radyo düğmeleri, denetimleri arka plan rengini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="836f3-104">The <xref:System.Windows.Forms.Control.BackColor%2A> property sets the background color for controls that are contained in the panel, such as labels and radio buttons.</span></span> <span data-ttu-id="836f3-105">Varsa <xref:System.Windows.Forms.Control.BackgroundImage%2A> özelliği ayarlı değil, <xref:System.Windows.Forms.Control.BackColor%2A> seçimi tüm panel doldurur.</span><span class="sxs-lookup"><span data-stu-id="836f3-105">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is not set, the <xref:System.Windows.Forms.Control.BackColor%2A> selection will fill all of the panel.</span></span> <span data-ttu-id="836f3-106">Varsa <xref:System.Windows.Forms.Control.BackgroundImage%2A> özelliği ayarlanmışsa, görüntünün arkasındaki panelde bulunan denetimleri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="836f3-106">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is set, the image will be displayed behind the controls that are contained in the panel.</span></span>

<span data-ttu-id="836f3-107">Aşağıdaki yordamı gerektiren bir **Windows uygulama** proje içeren bir form bir <xref:System.Windows.Forms.Panel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="836f3-107">The following procedure requires a **Windows Application** project with a form that contains a <xref:System.Windows.Forms.Panel> control.</span></span> <span data-ttu-id="836f3-108">Böyle bir projeyi Visual Studio'da ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: Bir Windows Forms uygulaması projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms'a denetimler ekleme](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="836f3-108">For information about how to set up such a project in Visual Studio, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="set-the-background-in-the-windows-forms-designer"></a><span data-ttu-id="836f3-109">Windows Form Tasarımcısı'nda arka planını ayarlama</span><span class="sxs-lookup"><span data-stu-id="836f3-109">Set the background in the Windows Forms Designer</span></span>

1. <span data-ttu-id="836f3-110">Projeyi Visual Studio'da açın ve seçin <xref:System.Windows.Forms.Panel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="836f3-110">Open the project in Visual Studio and select the <xref:System.Windows.Forms.Panel> control.</span></span>

2. <span data-ttu-id="836f3-111">İçinde **özellikleri** penceresinde, oku, İleri düğmesine tıklayın <xref:System.Windows.Forms.Control.BackColor%2A> bir penceresi üç sekme ile görüntülenecek özelliği.</span><span class="sxs-lookup"><span data-stu-id="836f3-111">In the **Properties** window, click the arrow button next to the <xref:System.Windows.Forms.Control.BackColor%2A> property to display a window with three tabs.</span></span>

3. <span data-ttu-id="836f3-112">Seçin **özel** renkler paleti görüntülemek için sekmesinde.</span><span class="sxs-lookup"><span data-stu-id="836f3-112">Select the **Custom** tab to display a palette of colors.</span></span>

4. <span data-ttu-id="836f3-113">Seçin **Web** veya **sistem** renkler için önceden tanımlanmış adlarının bir listesini görüntülemek için sekmesinde ve bir renk seçin.</span><span class="sxs-lookup"><span data-stu-id="836f3-113">Select the **Web** or **System** tab to display a list of predefined names for colors, and then select a color.</span></span>

5. <span data-ttu-id="836f3-114">İçinde **özellikleri** penceresinde, oku, İleri düğmesine tıklayın <xref:System.Windows.Forms.Control.BackgroundImage%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="836f3-114">In the **Properties** window, click the arrow button next to the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property.</span></span>

6. <span data-ttu-id="836f3-115">İçinde **açık** iletişim kutusunda, görüntülemek istediğiniz dosyayı seçin.</span><span class="sxs-lookup"><span data-stu-id="836f3-115">In the **Open** dialog box, select the file that you want to display.</span></span>

## <a name="see-also"></a><span data-ttu-id="836f3-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="836f3-116">See also</span></span>

- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [<span data-ttu-id="836f3-117">Panel Denetimi</span><span class="sxs-lookup"><span data-stu-id="836f3-117">Panel Control</span></span>](panel-control-windows-forms.md)
- [<span data-ttu-id="836f3-118">Panel Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="836f3-118">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
- [<span data-ttu-id="836f3-119">Nasıl yapılır: Tasarımcı kullanarak Windows Forms Panel denetimi ile denetimleri gruplandırma</span><span class="sxs-lookup"><span data-stu-id="836f3-119">How to: Group Controls with the Windows Forms Panel Control Using the Designer</span></span>](group-controls-with-wf-panel-control-using-the-designer.md)
