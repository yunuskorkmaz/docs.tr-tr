---
title: 'Nasıl yapılır: Tasarım Zamanında bir ElementHost Denetimini Kopyalayıp Yapıştırma'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: e570375d-2a68-44ba-b4f7-c781af2d20e8
ms.openlocfilehash: 0f3367deaaec04744a3f812d7f2d08047d7eb588
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211381"
---
# <a name="how-to-copy-and-paste-an-elementhost-control-at-design-time"></a><span data-ttu-id="59e24-102">Nasıl yapılır: Tasarım Zamanında bir ElementHost Denetimini Kopyalayıp Yapıştırma</span><span class="sxs-lookup"><span data-stu-id="59e24-102">How to: Copy and Paste an ElementHost Control at Design Time</span></span>

<span data-ttu-id="59e24-103">Bu yordam, Visual Studio'da bir Windows formunda bir Windows Presentation Foundation (WPF) denetimi kopyalamak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="59e24-103">This procedure shows you how to copy a Windows Presentation Foundation (WPF) control on a Windows Form in Visual Studio.</span></span>

## <a name="copy-and-paste-an-elementhost-control-at-design-time"></a><span data-ttu-id="59e24-104">Tasarım zamanında bir ElementHost denetimini yapıştırın</span><span class="sxs-lookup"><span data-stu-id="59e24-104">Copy and paste an ElementHost control at design time</span></span>

1. <span data-ttu-id="59e24-105">Yeni bir WPF ekleme <xref:System.Windows.Controls.UserControl> Windows Forms projenize.</span><span class="sxs-lookup"><span data-stu-id="59e24-105">Add a new WPF <xref:System.Windows.Controls.UserControl> to your Windows Forms project.</span></span> <span data-ttu-id="59e24-106">Denetim türü için varsayılan adı kullanacak `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="59e24-106">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="59e24-107">Daha fazla bilgi için [izlenecek yol: Yeni bir WPF içeriği Windows formlarında tasarım zamanında oluşturma](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="59e24-107">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="59e24-108">İçinde **özellikleri** penceresinde değerini ayarlayın <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerini `UserControl1` için `200`.</span><span class="sxs-lookup"><span data-stu-id="59e24-108">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties of `UserControl1` to `200`.</span></span>

3. <span data-ttu-id="59e24-109">Değerini <xref:System.Windows.Controls.Control.Background%2A> özelliğini `Blue`.</span><span class="sxs-lookup"><span data-stu-id="59e24-109">Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to `Blue`.</span></span>

4. <span data-ttu-id="59e24-110">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="59e24-110">Build the project.</span></span>

5. <span data-ttu-id="59e24-111">Açık `Form1` Windows Forms Tasarımcısı'nda.</span><span class="sxs-lookup"><span data-stu-id="59e24-111">Open `Form1` in the Windows Forms Designer.</span></span>

6. <span data-ttu-id="59e24-112">Gelen **araç kutusu**, örneği sürükleyin `UserControl1` forma.</span><span class="sxs-lookup"><span data-stu-id="59e24-112">From the **Toolbox**, drag an instance of `UserControl1` onto the form.</span></span>

   <span data-ttu-id="59e24-113">Örneği `UserControl1` yeni bir barındırılan <xref:System.Windows.Forms.Integration.ElementHost> adlı Denetim `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="59e24-113">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

7. <span data-ttu-id="59e24-114">İle `elementHost1` seçili panoya kopyalamak için CTRL + C tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="59e24-114">With `elementHost1` selected, press CTRL+C to copy it to the clipboard.</span></span>

8. <span data-ttu-id="59e24-115">Kopyalanan denetimi forma yapıştırmak için CTRL + V tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="59e24-115">Press CTRL+V to paste the copied control onto the form.</span></span>

   <span data-ttu-id="59e24-116">Yeni bir <xref:System.Windows.Forms.Integration.ElementHost> adlı Denetim `elementHost2` form üzerinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="59e24-116">A new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost2` is created on the form.</span></span>

## <a name="see-also"></a><span data-ttu-id="59e24-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="59e24-117">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="59e24-118">Geçiş ve Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="59e24-118">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="59e24-119">WPF Denetimlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="59e24-119">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="59e24-120">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="59e24-120">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
