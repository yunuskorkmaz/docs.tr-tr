---
title: Tasarımcıyı kullanarak bir panelin arka planını ayarlama
ms.date: 03/30/2017
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: db83cf54-3c69-4b08-ac6c-25b9b5abb1b0
ms.openlocfilehash: 8bdefba433632f7ba02f549a549c52c7aa56c2d7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731926"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel-using-the-designer"></a><span data-ttu-id="aaeb9-102">Nasıl yapılır: tasarımcı kullanarak Windows Forms panelinin arka planını ayarlama</span><span class="sxs-lookup"><span data-stu-id="aaeb9-102">How to: Set the background of a Windows Forms panel using the Designer</span></span>

<span data-ttu-id="aaeb9-103">Bir Windows Forms <xref:System.Windows.Forms.Panel> denetimi hem arka plan rengini hem de arka plan görüntüsünü görüntüleyebilir.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-103">A Windows Forms <xref:System.Windows.Forms.Panel> control can display both a background color and a background image.</span></span> <span data-ttu-id="aaeb9-104"><xref:System.Windows.Forms.Control.BackColor%2A> özelliği, panelde bulunan ve Etiketler ve radyo düğmeleri gibi denetimlerin arka plan rengini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-104">The <xref:System.Windows.Forms.Control.BackColor%2A> property sets the background color for controls that are contained in the panel, such as labels and radio buttons.</span></span> <span data-ttu-id="aaeb9-105"><xref:System.Windows.Forms.Control.BackgroundImage%2A> özelliği ayarlanmamışsa, <xref:System.Windows.Forms.Control.BackColor%2A> seçimi paneli dolduracaktır.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-105">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is not set, the <xref:System.Windows.Forms.Control.BackColor%2A> selection will fill all of the panel.</span></span> <span data-ttu-id="aaeb9-106"><xref:System.Windows.Forms.Control.BackgroundImage%2A> özelliği ayarlandıysa, görüntü, panelde bulunan denetimlerin arkasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-106">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is set, the image will be displayed behind the controls that are contained in the panel.</span></span>

<span data-ttu-id="aaeb9-107">Aşağıdaki yordam, bir <xref:System.Windows.Forms.Panel> denetimi içeren bir form ile **Windows uygulama** projesi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-107">The following procedure requires a **Windows Application** project with a form that contains a <xref:System.Windows.Forms.Panel> control.</span></span> <span data-ttu-id="aaeb9-108">Visual Studio 'da böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms uygulama projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms denetim ekleme](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="aaeb9-108">For information about how to set up such a project in Visual Studio, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="set-the-background-in-the-windows-forms-designer"></a><span data-ttu-id="aaeb9-109">Windows Form Tasarımcısı arka planı ayarlama</span><span class="sxs-lookup"><span data-stu-id="aaeb9-109">Set the background in the Windows Forms Designer</span></span>

1. <span data-ttu-id="aaeb9-110">Projeyi Visual Studio 'da açın ve <xref:System.Windows.Forms.Panel> denetimini seçin.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-110">Open the project in Visual Studio and select the <xref:System.Windows.Forms.Panel> control.</span></span>

2. <span data-ttu-id="aaeb9-111">**Özellikler** penceresinde, üç sekmeye sahip bir pencere göstermek için <xref:System.Windows.Forms.Control.BackColor%2A> özelliğinin yanındaki ok düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-111">In the **Properties** window, click the arrow button next to the <xref:System.Windows.Forms.Control.BackColor%2A> property to display a window with three tabs.</span></span>

3. <span data-ttu-id="aaeb9-112">Renk paletini göstermek için **özel** sekmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-112">Select the **Custom** tab to display a palette of colors.</span></span>

4. <span data-ttu-id="aaeb9-113">Renkler için önceden tanımlanmış adların listesini göstermek üzere **Web** veya **sistem** sekmesini seçin ve ardından bir renk seçin.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-113">Select the **Web** or **System** tab to display a list of predefined names for colors, and then select a color.</span></span>

5. <span data-ttu-id="aaeb9-114">**Özellikler** penceresinde, <xref:System.Windows.Forms.Control.BackgroundImage%2A> özelliğinin yanındaki ok düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-114">In the **Properties** window, click the arrow button next to the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property.</span></span>

6. <span data-ttu-id="aaeb9-115">**Aç** iletişim kutusunda, göstermek istediğiniz dosyayı seçin.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-115">In the **Open** dialog box, select the file that you want to display.</span></span>

## <a name="see-also"></a><span data-ttu-id="aaeb9-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-116">See also</span></span>

- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [<span data-ttu-id="aaeb9-117">Panel Denetimi</span><span class="sxs-lookup"><span data-stu-id="aaeb9-117">Panel Control</span></span>](panel-control-windows-forms.md)
- [<span data-ttu-id="aaeb9-118">Panel Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="aaeb9-118">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
- [<span data-ttu-id="aaeb9-119">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms Panel Denetimi ile Denetimleri Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="aaeb9-119">How to: Group Controls with the Windows Forms Panel Control Using the Designer</span></span>](group-controls-with-wf-panel-control-using-the-designer.md)
