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
ms.openlocfilehash: dfe5244e0c5b61fdf6d940dd16d8c280f013b12c
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666176"
---
# <a name="how-to-copy-and-paste-an-elementhost-control"></a><span data-ttu-id="00726-102">Nasıl yapılır: ElementHost denetimini kopyalayıp yapıştırma</span><span class="sxs-lookup"><span data-stu-id="00726-102">How to: Copy and paste an ElementHost control</span></span>

<span data-ttu-id="00726-103">Bu yordamda, Visual Studio 'da bir Windows formunda Windows Presentation Foundation (WPF) denetiminin nasıl kopyalanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="00726-103">This procedure shows you how to copy a Windows Presentation Foundation (WPF) control on a Windows Form in Visual Studio.</span></span>

1. <span data-ttu-id="00726-104">Visual Studio 'da Windows Forms projesine yeni bir WPF <xref:System.Windows.Controls.UserControl> ekleyin.</span><span class="sxs-lookup"><span data-stu-id="00726-104">In Visual Studio, add a new WPF <xref:System.Windows.Controls.UserControl> to a Windows Forms project.</span></span> <span data-ttu-id="00726-105">Denetim türü için varsayılan adı kullanın, `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="00726-105">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="00726-106">Daha fazla bilgi için bkz [. İzlenecek yol: Tasarım zamanında](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)Windows Forms yeni WPF içeriği oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="00726-106">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="00726-107">**Özellikler** penceresinde <xref:System.Windows.FrameworkElement.Width%2A> , ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerinin `UserControl1` değerini **200**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="00726-107">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties of `UserControl1` to **200**.</span></span>

3. <span data-ttu-id="00726-108"><xref:System.Windows.Controls.Control.Background%2A> Özelliğin değerini **mavi**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="00726-108">Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to **Blue**.</span></span>

4. <span data-ttu-id="00726-109">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="00726-109">Build the project.</span></span>

5. <span data-ttu-id="00726-110">Windows Form Tasarımcısı `Form1` açın.</span><span class="sxs-lookup"><span data-stu-id="00726-110">Open `Form1` in the Windows Forms Designer.</span></span>

6. <span data-ttu-id="00726-111">**Araç kutusundan**form `UserControl1` üzerine bir örneğini sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="00726-111">From the **Toolbox**, drag an instance of `UserControl1` onto the form.</span></span>

   <span data-ttu-id="00726-112">Bir örneği `UserControl1` adlı <xref:System.Windows.Forms.Integration.ElementHost> Yeni`elementHost1`bir denetimde barındırılır.</span><span class="sxs-lookup"><span data-stu-id="00726-112">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

7. <span data-ttu-id="00726-113">Seçili olarak, panoya kopyalamak için **CTRL**+C tuşlarına basın. `elementHost1`</span><span class="sxs-lookup"><span data-stu-id="00726-113">With `elementHost1` selected, press **Ctrl**+**C** to copy it to the clipboard.</span></span>

8. <span data-ttu-id="00726-114">Form üzerine kopyalanmış denetimi yapıştırmak için **CTRL**+**V** tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="00726-114">Press **Ctrl**+**V** to paste the copied control onto the form.</span></span>

   <span data-ttu-id="00726-115">Formunda adlı <xref:System.Windows.Forms.Integration.ElementHost> `elementHost2` yeni bir denetim oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="00726-115">A new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost2` is created on the form.</span></span>

## <a name="see-also"></a><span data-ttu-id="00726-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00726-116">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="00726-117">Geçiş ve Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="00726-117">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="00726-118">WPF Denetimlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="00726-118">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="00726-119">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="00726-119">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
