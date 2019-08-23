---
title: 'Nasıl yapılır: Bir Windows Formunda Windows Gezgini Stilinde bir Arabirim Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Explorer [Windows Forms], creating with Windows Forms
- SplitContainer control [Windows Forms], Explorer-style interface
- forms [Windows Forms], Windows Explorer type
ms.assetid: 9a3d5f4f-5dda-4350-9ad5-57ce5976dc47
ms.openlocfilehash: 34a5cd735c350688d9e83003806668e213932c85
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960618"
---
# <a name="how-to-create-a-windows-explorerstyle-interface-on-a-windows-form"></a><span data-ttu-id="5ceff-102">Nasıl yapılır: Bir Windows Formunda Windows Gezgini Stilinde bir Arabirim Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5ceff-102">How to: Create a Windows Explorer–Style Interface on a Windows Form</span></span>
<span data-ttu-id="5ceff-103">Windows Gezgini, uygulama için önceden kullanılan bir kullanıcı arabirimi seçiminden kaynaklanır.</span><span class="sxs-lookup"><span data-stu-id="5ceff-103">Windows Explorer is a common user-interface choice for applications because of its ready familiarity.</span></span>

 <span data-ttu-id="5ceff-104">Windows Gezgini, temelde bir <xref:System.Windows.Forms.TreeView> denetim <xref:System.Windows.Forms.ListView> ve ayrı panellerde bir denetimdir.</span><span class="sxs-lookup"><span data-stu-id="5ceff-104">Windows Explorer is, essentially, a <xref:System.Windows.Forms.TreeView> control and a <xref:System.Windows.Forms.ListView> control on separate panels.</span></span> <span data-ttu-id="5ceff-105">Panolar bir Splitter tarafından yeniden boyutlandırılabilir hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="5ceff-105">The panels are made resizable by a splitter.</span></span> <span data-ttu-id="5ceff-106">Denetimlerin bu düzenlemesi, bilgileri görüntülemek ve göz atmak için çok etkilidir.</span><span class="sxs-lookup"><span data-stu-id="5ceff-106">This arrangement of controls is very effective for displaying and browsing information.</span></span>

 <span data-ttu-id="5ceff-107">Aşağıdaki adımlarda, Windows Gezgini benzeri bir biçimde denetimlerin nasıl düzenlendiğini gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5ceff-107">The following steps show how to arrange controls in a Windows Explorer-like form.</span></span> <span data-ttu-id="5ceff-108">Windows Gezgini uygulamasının dosya tarama işlevinin nasıl ekleneceğini göstermez.</span><span class="sxs-lookup"><span data-stu-id="5ceff-108">They do not show how to add the file-browsing functionality of the Windows Explorer application.</span></span>

## <a name="to-create-a-windows-explorer-style-windows-form"></a><span data-ttu-id="5ceff-109">Windows Gezgini stili bir Windows formu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="5ceff-109">To create a Windows Explorer-style Windows Form</span></span>

1. <span data-ttu-id="5ceff-110">Yeni bir Windows uygulaması projesi oluşturma (**Dosya** > **Yeni** > **Proje** > **görseli C#**  veya **Visual Basic** > **Klasik** Masaüstü >  **Windows Forms uygulama**).</span><span class="sxs-lookup"><span data-stu-id="5ceff-110">Create a new Windows Application project (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

2. <span data-ttu-id="5ceff-111">**Araç kutusundan**:</span><span class="sxs-lookup"><span data-stu-id="5ceff-111">From the **Toolbox**:</span></span>

    1. <span data-ttu-id="5ceff-112">Formunuza bir <xref:System.Windows.Forms.SplitContainer> denetim sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="5ceff-112">Drag a <xref:System.Windows.Forms.SplitContainer> control onto your form.</span></span>

    2. <span data-ttu-id="5ceff-113">Bir <xref:System.Windows.Forms.TreeView> denetimi **SplitterPanel1** öğesine sürükleyin ( <xref:System.Windows.Forms.SplitContainer> **Panel1**olarak işaretlenen denetimin bölmesi).</span><span class="sxs-lookup"><span data-stu-id="5ceff-113">Drag a <xref:System.Windows.Forms.TreeView> control into **SplitterPanel1** (the panel of the <xref:System.Windows.Forms.SplitContainer> control marked **Panel1**).</span></span>

    3. <span data-ttu-id="5ceff-114">Bir <xref:System.Windows.Forms.ListView> denetimi **SplitterPanel2** öğesine sürükleyin ( <xref:System.Windows.Forms.SplitContainer> **Panel2**olarak işaretlenen denetimin bölmesi).</span><span class="sxs-lookup"><span data-stu-id="5ceff-114">Drag a <xref:System.Windows.Forms.ListView> control into **SplitterPanel2** (the panel of the <xref:System.Windows.Forms.SplitContainer> control marked **Panel2**).</span></span>

3. <span data-ttu-id="5ceff-115">CTRL tuşuna basarak ve sırasıyla tıklayarak tüm üç denetimi seçin.</span><span class="sxs-lookup"><span data-stu-id="5ceff-115">Select all three controls by pressing the CTRL key and clicking them in turn.</span></span> <span data-ttu-id="5ceff-116"><xref:System.Windows.Forms.SplitContainer> Denetimi seçtiğinizde, panolar yerine Bölümlendirici çubuğuna tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5ceff-116">When you select the <xref:System.Windows.Forms.SplitContainer> control, click the splitter bar, rather than the panels.</span></span>

    > [!NOTE]
    > <span data-ttu-id="5ceff-117">**Düzenleme** menüsünde **Tümünü Seç** komutunu kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="5ceff-117">Do not use the **Select All** command on the **Edit** menu.</span></span> <span data-ttu-id="5ceff-118">Bunu yaparsanız, sonraki adımda gerekli olan özellik **Özellikler** penceresinde görünmez.</span><span class="sxs-lookup"><span data-stu-id="5ceff-118">If you do so, the property needed in the next step will not appear in the **Properties** window.</span></span>

4. <span data-ttu-id="5ceff-119">**Özellikler** penceresinde, <xref:System.Windows.Forms.SplitContainer.Dock%2A> özelliğini olarak <xref:System.Windows.Forms.DockStyle.Fill>ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="5ceff-119">In the **Properties** window, set the <xref:System.Windows.Forms.SplitContainer.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

5. <span data-ttu-id="5ceff-120">Uygulamayı çalıştırmak için F5'e basın.</span><span class="sxs-lookup"><span data-stu-id="5ceff-120">Press F5 to run the application.</span></span>

     <span data-ttu-id="5ceff-121">Form, Windows Gezgini ' ne benzer şekilde iki bölümden oluşan bir kullanıcı arabirimi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5ceff-121">The form displays a two-part user interface, similar to that of the Windows Explorer.</span></span>

    > [!NOTE]
    > <span data-ttu-id="5ceff-122">Bölümlendirici sürüklediğiniz zaman, panolar kendilerini yeniden boyutlandırır.</span><span class="sxs-lookup"><span data-stu-id="5ceff-122">When you drag the splitter, the panels resize themselves.</span></span>

## <a name="see-also"></a><span data-ttu-id="5ceff-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ceff-123">See also</span></span>

- <xref:System.Windows.Forms.SplitContainer>
- [<span data-ttu-id="5ceff-124">Nasıl yapılır: Windows Forms ile çok Bölbir Kullanıcı arabirimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="5ceff-124">How to: Create a Multipane User Interface with Windows Forms</span></span>](how-to-create-a-multipane-user-interface-with-windows-forms.md)
- [<span data-ttu-id="5ceff-125">Nasıl yapılır: Bölünmüş pencerede yeniden boyutlandırma ve konumlandırma davranışını tanımlama</span><span class="sxs-lookup"><span data-stu-id="5ceff-125">How to: Define Resize and Positioning Behavior in a Split Window</span></span>](how-to-define-resize-and-positioning-behavior-in-a-split-window.md)
- [<span data-ttu-id="5ceff-126">Nasıl yapılır: Pencereyi yatay bölme</span><span class="sxs-lookup"><span data-stu-id="5ceff-126">How to: Split a Window Horizontally</span></span>](how-to-split-a-window-horizontally.md)
- [<span data-ttu-id="5ceff-127">SplitContainer Denetimi</span><span class="sxs-lookup"><span data-stu-id="5ceff-127">SplitContainer Control</span></span>](splitcontainer-control-windows-forms.md)
