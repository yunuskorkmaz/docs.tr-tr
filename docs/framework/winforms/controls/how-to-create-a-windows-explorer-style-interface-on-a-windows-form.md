---
title: 'Nasıl yapılır: Bir Windows Formunda Windows Gezgini Stilinde bir Arabirim Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Explorer [Windows Forms], creating with Windows Forms
- SplitContainer control [Windows Forms], Explorer-style interface
- forms [Windows Forms], Windows Explorer type
ms.assetid: 9a3d5f4f-5dda-4350-9ad5-57ce5976dc47
ms.openlocfilehash: 249210d2bcb7a9ef2c5bf1aed00bcfe138193aab
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43785384"
---
# <a name="how-to-create-a-windows-explorerstyle-interface-on-a-windows-form"></a><span data-ttu-id="87f17-102">Nasıl yapılır: Bir Windows Formunda Windows Gezgini Stilinde bir Arabirim Oluşturma</span><span class="sxs-lookup"><span data-stu-id="87f17-102">How to: Create a Windows Explorer–Style Interface on a Windows Form</span></span>
<span data-ttu-id="87f17-103">Windows Gezgini bir ortak kullanıcı arabirimi uygulamalar için kendi hazır bilgisi nedeniyle seçimdir.</span><span class="sxs-lookup"><span data-stu-id="87f17-103">Windows Explorer is a common user-interface choice for applications because of its ready familiarity.</span></span>  
  
 <span data-ttu-id="87f17-104">Esas olarak, Windows Gezgini, bir <xref:System.Windows.Forms.TreeView> denetimi ve bir <xref:System.Windows.Forms.ListView> ayrı Panel denetimi.</span><span class="sxs-lookup"><span data-stu-id="87f17-104">Windows Explorer is, essentially, a <xref:System.Windows.Forms.TreeView> control and a <xref:System.Windows.Forms.ListView> control on separate panels.</span></span> <span data-ttu-id="87f17-105">Paneller yeniden boyutlandırılabilir bir ayırıcı tarafından yapılır.</span><span class="sxs-lookup"><span data-stu-id="87f17-105">The panels are made resizable by a splitter.</span></span> <span data-ttu-id="87f17-106">Bu düzenleme denetimleri görüntüleme ve gözatma bilgilerinin oldukça etkilidir.</span><span class="sxs-lookup"><span data-stu-id="87f17-106">This arrangement of controls is very effective for displaying and browsing information.</span></span>  
  
 <span data-ttu-id="87f17-107">Aşağıdaki adımlarda, bir Windows Gezgini benzeri form denetimleri düzenlemek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="87f17-107">The following steps show how to arrange controls in a Windows Explorer-like form.</span></span> <span data-ttu-id="87f17-108">Windows Gezgini uygulama dosyasına göz atma işlevini ekleme gösterme.</span><span class="sxs-lookup"><span data-stu-id="87f17-108">They do not show how to add the file-browsing functionality of the Windows Explorer application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="87f17-109">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="87f17-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="87f17-110">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="87f17-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="87f17-111">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="87f17-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-create-a-windows-explorer-style-windows-form"></a><span data-ttu-id="87f17-112">Bir Windows Gezgini stilinde Windows Form oluşturma</span><span class="sxs-lookup"><span data-stu-id="87f17-112">To create a Windows Explorer-style Windows Form</span></span>  
  
1.  <span data-ttu-id="87f17-113">Yeni bir Windows uygulaması projesi oluşturun (**dosya** > **yeni** > **proje** > **Visual C#** veya **Visual Basic** > **Klasik Masaüstü** > **Windows Forms uygulamalarındaki**).</span><span class="sxs-lookup"><span data-stu-id="87f17-113">Create a new Windows Application project (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>  
  
2.  <span data-ttu-id="87f17-114">Gelen **araç kutusu**:</span><span class="sxs-lookup"><span data-stu-id="87f17-114">From the **Toolbox**:</span></span>  
  
    1.  <span data-ttu-id="87f17-115">Sürükleme bir <xref:System.Windows.Forms.SplitContainer> denetimi formunuza sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="87f17-115">Drag a <xref:System.Windows.Forms.SplitContainer> control onto your form.</span></span>  
  
    2.  <span data-ttu-id="87f17-116">Sürükleme bir <xref:System.Windows.Forms.TreeView> içine denetim **SplitterPanel1** (panelini <xref:System.Windows.Forms.SplitContainer> işaretlenen denetim **Panel1**).</span><span class="sxs-lookup"><span data-stu-id="87f17-116">Drag a <xref:System.Windows.Forms.TreeView> control into **SplitterPanel1** (the panel of the <xref:System.Windows.Forms.SplitContainer> control marked **Panel1**).</span></span>  
  
    3.  <span data-ttu-id="87f17-117">Sürükleme bir <xref:System.Windows.Forms.ListView> içine denetim **SplitterPanel2** (panelini <xref:System.Windows.Forms.SplitContainer> işaretlenen denetim **Panel2**).</span><span class="sxs-lookup"><span data-stu-id="87f17-117">Drag a <xref:System.Windows.Forms.ListView> control into **SplitterPanel2** (the panel of the <xref:System.Windows.Forms.SplitContainer> control marked **Panel2**).</span></span>  
  
3.  <span data-ttu-id="87f17-118">Her üç denetim CTRL tuşuna basarak ve bunları sırayla tıklayarak seçin.</span><span class="sxs-lookup"><span data-stu-id="87f17-118">Select all three controls by pressing the CTRL key and clicking them in turn.</span></span> <span data-ttu-id="87f17-119">Seçtiğinizde, <xref:System.Windows.Forms.SplitContainer> denetlemek, paneller yerine ayırıcıyı tıklayın.</span><span class="sxs-lookup"><span data-stu-id="87f17-119">When you select the <xref:System.Windows.Forms.SplitContainer> control, click the splitter bar, rather than the panels.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="87f17-120">Kullanmayın **Tümünü Seç** komutunu **Düzenle** menüsü.</span><span class="sxs-lookup"><span data-stu-id="87f17-120">Do not use the **Select All** command on the **Edit** menu.</span></span> <span data-ttu-id="87f17-121">Bunu yaparsanız, sonraki adımda gerekli özellik görüntülenmez **özellikleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="87f17-121">If you do so, the property needed in the next step will not appear in the **Properties** window.</span></span>  
  
4.  <span data-ttu-id="87f17-122">İçinde **özellikleri** penceresinde <xref:System.Windows.Forms.SplitContainer.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="87f17-122">In the **Properties** window, set the <xref:System.Windows.Forms.SplitContainer.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
5.  <span data-ttu-id="87f17-123">Uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="87f17-123">Press F5 to run the application.</span></span>  
  
     <span data-ttu-id="87f17-124">Form, Windows Gezgini için benzer bir iki bölümden kullanıcı arabirimi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="87f17-124">The form displays a two-part user interface, similar to that of the Windows Explorer.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="87f17-125">Bölümlendirici sürüklediğinizde, paneller kendilerini yeniden boyutlandırın.</span><span class="sxs-lookup"><span data-stu-id="87f17-125">When you drag the splitter, the panels resize themselves.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87f17-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="87f17-126">See Also</span></span>  
 <xref:System.Windows.Forms.SplitContainer>  
 [<span data-ttu-id="87f17-127">Nasıl yapılır: Windows Forms ile Çok Bölmeli Kullanıcı Arabirimi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="87f17-127">How to: Create a Multipane User Interface with Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)  
 [<span data-ttu-id="87f17-128">Nasıl yapılır: Bölünmüş Pencerede Yeniden Boyutlandırma ve Konumlama Davranışını Tanımlama</span><span class="sxs-lookup"><span data-stu-id="87f17-128">How to: Define Resize and Positioning Behavior in a Split Window</span></span>](../../../../docs/framework/winforms/controls/how-to-define-resize-and-positioning-behavior-in-a-split-window.md)  
 [<span data-ttu-id="87f17-129">Nasıl yapılır: Pencereyi Yatay Bölme</span><span class="sxs-lookup"><span data-stu-id="87f17-129">How to: Split a Window Horizontally</span></span>](../../../../docs/framework/winforms/controls/how-to-split-a-window-horizontally.md)  
 [<span data-ttu-id="87f17-130">SplitContainer Denetimi</span><span class="sxs-lookup"><span data-stu-id="87f17-130">SplitContainer Control</span></span>](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)
