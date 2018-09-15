---
title: 'Nasıl yapılır: Tasarım Zamanında bir ElementHost Denetimini Kopyalayıp Yapıştırma'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: e570375d-2a68-44ba-b4f7-c781af2d20e8
ms.openlocfilehash: 43ebe50497df97511925bd2e413ab5b5988b7f57
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45624794"
---
# <a name="how-to-copy-and-paste-an-elementhost-control-at-design-time"></a><span data-ttu-id="36e9b-102">Nasıl yapılır: Tasarım Zamanında bir ElementHost Denetimini Kopyalayıp Yapıştırma</span><span class="sxs-lookup"><span data-stu-id="36e9b-102">How to: Copy and Paste an ElementHost Control at Design Time</span></span>
<span data-ttu-id="36e9b-103">Bu yordam Windows formunda bir Windows Presentation Foundation (WPF) denetimi kopyalamak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="36e9b-103">This procedure shows you how to copy a Windows Presentation Foundation (WPF) control on a Windows Form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="36e9b-104">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="36e9b-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="36e9b-105">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="36e9b-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="36e9b-106">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="36e9b-106">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-copy-and-paste-an-elementhost-control-at-design-time"></a><span data-ttu-id="36e9b-107">Kopyalayıp tasarım zamanında bir ElementHost denetimini yapıştırmak için</span><span class="sxs-lookup"><span data-stu-id="36e9b-107">To copy and paste an ElementHost control at design time</span></span>  
  
1.  <span data-ttu-id="36e9b-108">Yeni bir WPF ekleme <xref:System.Windows.Controls.UserControl> Windows Forms projenize.</span><span class="sxs-lookup"><span data-stu-id="36e9b-108">Add a new WPF <xref:System.Windows.Controls.UserControl> to your Windows Forms project.</span></span> <span data-ttu-id="36e9b-109">Denetim türü için varsayılan adı kullanacak `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="36e9b-109">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="36e9b-110">Daha fazla bilgi için [izlenecek yol: oluşturma yeni WPF içeriği Windows Forms'ta tasarım zamanında](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="36e9b-110">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="36e9b-111">İçinde **özellikleri** penceresinde değerini ayarlayın <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerini `UserControl1` için `200`.</span><span class="sxs-lookup"><span data-stu-id="36e9b-111">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties of `UserControl1` to `200`.</span></span>  
  
3.  <span data-ttu-id="36e9b-112">Değerini <xref:System.Windows.Controls.Control.Background%2A> özelliğini `Blue`.</span><span class="sxs-lookup"><span data-stu-id="36e9b-112">Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to `Blue`.</span></span>  
  
4.  <span data-ttu-id="36e9b-113">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="36e9b-113">Build the project.</span></span>  
  
5.  <span data-ttu-id="36e9b-114">Açık `Form1` Windows Forms Tasarımcısı'nda.</span><span class="sxs-lookup"><span data-stu-id="36e9b-114">Open `Form1` in the Windows Forms Designer.</span></span>  
  
6.  <span data-ttu-id="36e9b-115">Gelen **araç kutusu**, örneği sürükleyin `UserControl1` forma.</span><span class="sxs-lookup"><span data-stu-id="36e9b-115">From the **Toolbox**, drag an instance of `UserControl1` onto the form.</span></span>  
  
     <span data-ttu-id="36e9b-116">Örneği `UserControl1` yeni bir barındırılan <xref:System.Windows.Forms.Integration.ElementHost> adlı Denetim `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="36e9b-116">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
7.  <span data-ttu-id="36e9b-117">İle `elementHost1` seçili panoya kopyalamak için CTRL + C tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="36e9b-117">With `elementHost1` selected, press CTRL+C to copy it to the clipboard.</span></span>  
  
8.  <span data-ttu-id="36e9b-118">Kopyalanan denetimi forma yapıştırmak için CTRL + V tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="36e9b-118">Press CTRL+V to paste the copied control onto the form.</span></span>  
  
     <span data-ttu-id="36e9b-119">Yeni bir <xref:System.Windows.Forms.Integration.ElementHost> adlı Denetim `elementHost2` form üzerinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="36e9b-119">A new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost2` is created on the form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36e9b-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="36e9b-120">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="36e9b-121">İzlenecek yol: Bir ElementHost Denetimini Ayrı Windows Forms’a Kopyalama ve Yapıştırma</span><span class="sxs-lookup"><span data-stu-id="36e9b-121">Walkthrough: Copying and Pasting an ElementHost Control into Separate Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/copy--paste-an-elementhost-control-into-forms.md)  
 [<span data-ttu-id="36e9b-122">Geçiş ve Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="36e9b-122">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="36e9b-123">WPF Denetimlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="36e9b-123">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="36e9b-124">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="36e9b-124">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
