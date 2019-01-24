---
title: 'Nasıl yapılır: Tasarım zamanında bir ElementHost denetimini yapıştırın'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: e570375d-2a68-44ba-b4f7-c781af2d20e8
ms.openlocfilehash: 6ff1ccc5e8f188bdec2e09048974fdc20a785920
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572637"
---
# <a name="how-to-copy-and-paste-an-elementhost-control-at-design-time"></a><span data-ttu-id="8346d-102">Nasıl yapılır: Tasarım zamanında bir ElementHost denetimini yapıştırın</span><span class="sxs-lookup"><span data-stu-id="8346d-102">How to: Copy and Paste an ElementHost Control at Design Time</span></span>
<span data-ttu-id="8346d-103">Bu yordam Windows formunda bir Windows Presentation Foundation (WPF) denetimi kopyalamak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="8346d-103">This procedure shows you how to copy a Windows Presentation Foundation (WPF) control on a Windows Form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8346d-104">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="8346d-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="8346d-105">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="8346d-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="8346d-106">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="8346d-106">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-copy-and-paste-an-elementhost-control-at-design-time"></a><span data-ttu-id="8346d-107">Kopyalayıp tasarım zamanında bir ElementHost denetimini yapıştırmak için</span><span class="sxs-lookup"><span data-stu-id="8346d-107">To copy and paste an ElementHost control at design time</span></span>  
  
1.  <span data-ttu-id="8346d-108">Yeni bir WPF ekleme <xref:System.Windows.Controls.UserControl> Windows Forms projenize.</span><span class="sxs-lookup"><span data-stu-id="8346d-108">Add a new WPF <xref:System.Windows.Controls.UserControl> to your Windows Forms project.</span></span> <span data-ttu-id="8346d-109">Denetim türü için varsayılan adı kullanacak `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="8346d-109">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="8346d-110">Daha fazla bilgi için [izlenecek yol: Yeni bir WPF içeriği Windows formlarında tasarım zamanında oluşturma](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="8346d-110">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="8346d-111">İçinde **özellikleri** penceresinde değerini ayarlayın <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerini `UserControl1` için `200`.</span><span class="sxs-lookup"><span data-stu-id="8346d-111">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties of `UserControl1` to `200`.</span></span>  
  
3.  <span data-ttu-id="8346d-112">Değerini <xref:System.Windows.Controls.Control.Background%2A> özelliğini `Blue`.</span><span class="sxs-lookup"><span data-stu-id="8346d-112">Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to `Blue`.</span></span>  
  
4.  <span data-ttu-id="8346d-113">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8346d-113">Build the project.</span></span>  
  
5.  <span data-ttu-id="8346d-114">Açık `Form1` Windows Forms Tasarımcısı'nda.</span><span class="sxs-lookup"><span data-stu-id="8346d-114">Open `Form1` in the Windows Forms Designer.</span></span>  
  
6.  <span data-ttu-id="8346d-115">Gelen **araç kutusu**, örneği sürükleyin `UserControl1` forma.</span><span class="sxs-lookup"><span data-stu-id="8346d-115">From the **Toolbox**, drag an instance of `UserControl1` onto the form.</span></span>  
  
     <span data-ttu-id="8346d-116">Örneği `UserControl1` yeni bir barındırılan <xref:System.Windows.Forms.Integration.ElementHost> adlı Denetim `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="8346d-116">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
7.  <span data-ttu-id="8346d-117">İle `elementHost1` seçili panoya kopyalamak için CTRL + C tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="8346d-117">With `elementHost1` selected, press CTRL+C to copy it to the clipboard.</span></span>  
  
8.  <span data-ttu-id="8346d-118">Kopyalanan denetimi forma yapıştırmak için CTRL + V tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="8346d-118">Press CTRL+V to paste the copied control onto the form.</span></span>  
  
     <span data-ttu-id="8346d-119">Yeni bir <xref:System.Windows.Forms.Integration.ElementHost> adlı Denetim `elementHost2` form üzerinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8346d-119">A new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost2` is created on the form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8346d-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8346d-120">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="8346d-121">Geçiş ve Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="8346d-121">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="8346d-122">WPF Denetimlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="8346d-122">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)
- [<span data-ttu-id="8346d-123">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="8346d-123">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
