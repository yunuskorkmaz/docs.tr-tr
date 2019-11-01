---
title: 'Nasıl yapılır: Tasarım Zamanında bir ElementHost Denetimini Kopyalayıp Yapıştırma'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: e570375d-2a68-44ba-b4f7-c781af2d20e8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3d1887eb1161f714962c2c26d6fe618749b26c0f
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197483"
---
# <a name="how-to-copy-and-paste-an-elementhost-control"></a><span data-ttu-id="099f4-102">Nasıl yapılır: bir ElementHost denetimini kopyalayıp yapıştırma</span><span class="sxs-lookup"><span data-stu-id="099f4-102">How to: Copy and paste an ElementHost control</span></span>

<span data-ttu-id="099f4-103">Bu yordamda, Visual Studio 'da bir Windows formunda Windows Presentation Foundation (WPF) denetiminin nasıl kopyalanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="099f4-103">This procedure shows you how to copy a Windows Presentation Foundation (WPF) control on a Windows Form in Visual Studio.</span></span>

1. <span data-ttu-id="099f4-104">Visual Studio 'da, bir Windows Forms projesine yeni bir WPF <xref:System.Windows.Controls.UserControl> ekleyin.</span><span class="sxs-lookup"><span data-stu-id="099f4-104">In Visual Studio, add a new WPF <xref:System.Windows.Controls.UserControl> to a Windows Forms project.</span></span> <span data-ttu-id="099f4-105">Denetim türü için varsayılan adı kullanın, `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="099f4-105">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="099f4-106">Daha fazla bilgi için bkz. [Izlenecek yol: tasarım zamanında Windows Forms yenı WPF Içeriği oluşturma](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="099f4-106">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="099f4-107">**Özellikler** penceresinde `UserControl1` <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerinin değerini **200**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="099f4-107">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties of `UserControl1` to **200**.</span></span>

3. <span data-ttu-id="099f4-108"><xref:System.Windows.Controls.Control.Background%2A> özelliğinin değerini **mavi**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="099f4-108">Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to **Blue**.</span></span>

4. <span data-ttu-id="099f4-109">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="099f4-109">Build the project.</span></span>

5. <span data-ttu-id="099f4-110">Windows Form Tasarımcısı `Form1` açın.</span><span class="sxs-lookup"><span data-stu-id="099f4-110">Open `Form1` in the Windows Forms Designer.</span></span>

6. <span data-ttu-id="099f4-111">**Araç kutusundan**bir `UserControl1` örneğini form üzerine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="099f4-111">From the **Toolbox**, drag an instance of `UserControl1` onto the form.</span></span>

   <span data-ttu-id="099f4-112">`UserControl1` örneği, `elementHost1`adlı yeni bir <xref:System.Windows.Forms.Integration.ElementHost> denetiminde barındırılır.</span><span class="sxs-lookup"><span data-stu-id="099f4-112">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

7. <span data-ttu-id="099f4-113">`elementHost1` seçili olduğunda, panoya kopyalamak için **Ctrl**+**C** tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="099f4-113">With `elementHost1` selected, press **Ctrl**+**C** to copy it to the clipboard.</span></span>

8. <span data-ttu-id="099f4-114">Kopyalanmış denetimi forma yapıştırmak için **Ctrl**+**V** tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="099f4-114">Press **Ctrl**+**V** to paste the copied control onto the form.</span></span>

   <span data-ttu-id="099f4-115">Form üzerinde `elementHost2` adlı yeni bir <xref:System.Windows.Forms.Integration.ElementHost> denetimi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="099f4-115">A new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost2` is created on the form.</span></span>

## <a name="see-also"></a><span data-ttu-id="099f4-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="099f4-116">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="099f4-117">Geçiş ve Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="099f4-117">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="099f4-118">WPF Denetimlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="099f4-118">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="099f4-119">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="099f4-119">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
