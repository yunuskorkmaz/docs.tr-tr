---
title: 'İzlenecek yol: Windows Forms Denetimlerindeki Akıllı Etiketleri Kullanarak Ortak Görevleri Gerçekleştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
ms.openlocfilehash: d1c69d2e9e89e0a4fed767216e8743a0ac9ac81d
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43891177"
---
# <a name="walkthrough-performing-common-tasks-using-smart-tags-on-windows-forms-controls"></a><span data-ttu-id="b01c0-102">İzlenecek yol: Windows Forms Denetimlerindeki Akıllı Etiketleri Kullanarak Ortak Görevleri Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="b01c0-102">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>
<span data-ttu-id="b01c0-103">Windows Forms uygulamanız için formlar ve denetimler oluşturmak gibi art arda gerçekleştirir çok sayıda görev vardır.</span><span class="sxs-lookup"><span data-stu-id="b01c0-103">As you construct forms and controls for your Windows Forms application, there are many tasks you will perform repeatedly.</span></span> <span data-ttu-id="b01c0-104">Karşınıza çıkacak sık gerçekleştirilen görevlerin bazıları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b01c0-104">These are some of the commonly performed tasks you will encounter:</span></span>  
  
-   <span data-ttu-id="b01c0-105">Ekleyerek veya bir sekme üzerindeki kaldırarak bir <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="b01c0-105">Adding or removing a tab on a <xref:System.Windows.Forms.TabControl>.</span></span>  
  
-   <span data-ttu-id="b01c0-106">Bir denetim için üst yerleştirme.</span><span class="sxs-lookup"><span data-stu-id="b01c0-106">Docking a control to its parent.</span></span>  
  
-   <span data-ttu-id="b01c0-107">Yönünü değiştirme bir <xref:System.Windows.Forms.SplitContainer> denetimi.</span><span class="sxs-lookup"><span data-stu-id="b01c0-107">Changing the orientation of a <xref:System.Windows.Forms.SplitContainer> control.</span></span>  
  
 <span data-ttu-id="b01c0-108">Geliştirme hızlandırmak için pek çok denetimi tasarım zamanında bu tek gibi genel görevleri gerçekleştirmenize olanak tanıyan bağlama duyarlı menüler şunlardır akıllı etiketler sunar.</span><span class="sxs-lookup"><span data-stu-id="b01c0-108">To speed development, many controls offer smart tags, which are context-sensitive menus that allow you to perform common tasks like these in a single gesture at design time.</span></span> <span data-ttu-id="b01c0-109">Bu görevleri adlı *akıllı etiket fiilleri*.</span><span class="sxs-lookup"><span data-stu-id="b01c0-109">These tasks are called *smart-tag verbs*.</span></span>  
  
 <span data-ttu-id="b01c0-110">Akıllı etiketler Tasarımcısı'nda yaşam süresi'için bir denetim örneğine bağlı kalır ve her zaman kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b01c0-110">Smart tags remain attached to a control instance for its lifetime in the designer and are always available.</span></span>  
  
 <span data-ttu-id="b01c0-111">Bu kılavuzda gösterilen görevler aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="b01c0-111">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="b01c0-112">Bir Windows Forms projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="b01c0-112">Creating a Windows Forms project</span></span>  
  
-   <span data-ttu-id="b01c0-113">Akıllı etiketleri kullanarak</span><span class="sxs-lookup"><span data-stu-id="b01c0-113">Using smart tags</span></span>  
  
-   <span data-ttu-id="b01c0-114">Akıllı etiketler devre dışı bırakma ve etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="b01c0-114">Enabling and Disabling Smart Tags</span></span>  
  
 <span data-ttu-id="b01c0-115">İşlemi tamamladığınızda, bu önemli bir düzen özellikleri tarafından oynadığı rol, bir anlayışa sahip olacaksınız.</span><span class="sxs-lookup"><span data-stu-id="b01c0-115">When you are finished, you will have an understanding of the role played by these important layout features.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b01c0-116">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="b01c0-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="b01c0-117">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="b01c0-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="b01c0-118">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="b01c0-118">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="b01c0-119">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b01c0-119">Creating the Project</span></span>  
 <span data-ttu-id="b01c0-120">İlk adım projeyi oluşturmak ve formu ayarlamaktır.</span><span class="sxs-lookup"><span data-stu-id="b01c0-120">The first step is to create the project and set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="b01c0-121">Proje oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="b01c0-121">To create the project</span></span>  
  
1.  <span data-ttu-id="b01c0-122">"SmartTagsExample" adlı bir Windows tabanlı uygulama projesi oluşturun (**dosya** > **yeni** > **proje**  >   **Visual C#** veya **Visual Basic** > **Klasik Masaüstü** > **Windows Forms uygulamalarındaki**).</span><span class="sxs-lookup"><span data-stu-id="b01c0-122">Create a Windows-based application project called "SmartTagsExample" (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>  
  
2.  <span data-ttu-id="b01c0-123">Formda seçin **Windows Form Tasarımcısı**.</span><span class="sxs-lookup"><span data-stu-id="b01c0-123">Select the form in the **Windows Forms Designer**.</span></span>  
  
## <a name="using-smart-tags"></a><span data-ttu-id="b01c0-124">Akıllı etiketleri kullanarak</span><span class="sxs-lookup"><span data-stu-id="b01c0-124">Using Smart Tags</span></span>  
 <span data-ttu-id="b01c0-125">Akıllı etiketler her zaman bunları teklif denetimleri tasarım zamanında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b01c0-125">Smart tags are always available at design time on controls that offer them.</span></span>  
  
#### <a name="to-use-smart-tags"></a><span data-ttu-id="b01c0-126">Akıllı etiketleri kullanma</span><span class="sxs-lookup"><span data-stu-id="b01c0-126">To use smart tags</span></span>  
  
1.  <span data-ttu-id="b01c0-127">Sürükleme bir <xref:System.Windows.Forms.TabControl> gelen **araç kutusu** formunuza.</span><span class="sxs-lookup"><span data-stu-id="b01c0-127">Drag a <xref:System.Windows.Forms.TabControl> from the **Toolbox** onto your form.</span></span> <span data-ttu-id="b01c0-128">Akıllı etiket karakterini unutmayın (![akıllı etiket karakterini](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) üzerinde yan, görüntülenen <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="b01c0-128">Note the smart-tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) that appears on the side of the <xref:System.Windows.Forms.TabControl>.</span></span>  
  
2.  <span data-ttu-id="b01c0-129">Akıllı etiket karakterini tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b01c0-129">Click the smart-tag glyph.</span></span> <span data-ttu-id="b01c0-130">Glif yanında görüntülenen kısayol menüsünden seçin **Sekme Ekle** öğesi.</span><span class="sxs-lookup"><span data-stu-id="b01c0-130">In the shortcut menu that appears next to the glyph, select the **Add Tab** item.</span></span> <span data-ttu-id="b01c0-131">Yeni bir sekme sayfası eklenir gözlemleyin <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="b01c0-131">Observe that a new tab page is added to the <xref:System.Windows.Forms.TabControl>.</span></span>  
  
3.  <span data-ttu-id="b01c0-132">Sürükleme bir <xref:System.Windows.Forms.TableLayoutPanel> denetimi **araç kutusu** formunuza.</span><span class="sxs-lookup"><span data-stu-id="b01c0-132">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>  
  
4.  <span data-ttu-id="b01c0-133">Akıllı etiket karakterini tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b01c0-133">Click the smart-tag glyph.</span></span> <span data-ttu-id="b01c0-134">Glif yanında görüntülenen kısayol menüsünden seçin **Sütun Ekle** öğesi.</span><span class="sxs-lookup"><span data-stu-id="b01c0-134">In the shortcut menu that appears next to the glyph, select the **Add Column** item.</span></span> <span data-ttu-id="b01c0-135">Yeni bir sütun eklenir gözlemleyin <xref:System.Windows.Forms.TableLayoutPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="b01c0-135">Observe that a new column is added to the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
5.  <span data-ttu-id="b01c0-136">Sürükleme bir <xref:System.Windows.Forms.SplitContainer> denetimi **araç kutusu** formunuza.</span><span class="sxs-lookup"><span data-stu-id="b01c0-136">Drag a <xref:System.Windows.Forms.SplitContainer> control from the **Toolbox** onto your form.</span></span>  
  
6.  <span data-ttu-id="b01c0-137">Akıllı etiket karakterini tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b01c0-137">Click the smart-tag glyph.</span></span> <span data-ttu-id="b01c0-138">Glif yanında görüntülenen kısayol menüsünden seçin **Yatay bölümlendirici yönlendirmesini** öğesi.</span><span class="sxs-lookup"><span data-stu-id="b01c0-138">In the shortcut menu that appears next to the glyph, select the **Horizontal splitter orientation** item.</span></span> <span data-ttu-id="b01c0-139">Mesajının görüntülendiğini görün <xref:System.Windows.Forms.SplitContainer> denetimin ayırıcıyı, artık yatay odaklıdır.</span><span class="sxs-lookup"><span data-stu-id="b01c0-139">Observe that the <xref:System.Windows.Forms.SplitContainer> control's splitter bar is now oriented horizontally.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b01c0-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b01c0-140">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 <xref:System.Windows.Forms.TabControl>  
 <xref:System.Windows.Forms.SplitContainer>  
 <xref:System.ComponentModel.Design.DesignerActionList>  
 [<span data-ttu-id="b01c0-141">İzlenecek yol: Bir Windows Formları bileşenine akıllı etiket ekleme</span><span class="sxs-lookup"><span data-stu-id="b01c0-141">Walkthrough: Adding Smart Tags to a Windows Forms Component</span></span>](https://msdn.microsoft.com/library/a6814169-fa7d-4527-808c-637ca5c95f63)
