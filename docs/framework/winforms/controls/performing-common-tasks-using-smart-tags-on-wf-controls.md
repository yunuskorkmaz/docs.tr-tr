---
title: 'İzlenecek yol: Windows Forms Denetimlerindeki Akıllı Etiketleri Kullanarak Ortak Görevleri Gerçekleştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
ms.openlocfilehash: a558f6d274f260fc91fd140e9dae2c740b1ae00d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537950"
---
# <a name="walkthrough-performing-common-tasks-using-smart-tags-on-windows-forms-controls"></a><span data-ttu-id="77a90-102">İzlenecek yol: Windows Forms Denetimlerindeki Akıllı Etiketleri Kullanarak Ortak Görevleri Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="77a90-102">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>
<span data-ttu-id="77a90-103">Windows Forms uygulamanız için formlar ve denetimler oluşturmak gibi art arda gerçekleştirecek pek çok görev vardır.</span><span class="sxs-lookup"><span data-stu-id="77a90-103">As you construct forms and controls for your Windows Forms application, there are many tasks you will perform repeatedly.</span></span> <span data-ttu-id="77a90-104">Bunlar, karşınıza çıkacak sık gerçekleştirilen görevlerden bazıları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="77a90-104">These are some of the commonly performed tasks you will encounter:</span></span>  
  
-   <span data-ttu-id="77a90-105">Ekleyerek veya üzerinde bir sekme kaldırarak bir <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="77a90-105">Adding or removing a tab on a <xref:System.Windows.Forms.TabControl>.</span></span>  
  
-   <span data-ttu-id="77a90-106">Bir denetim kendi üst yerleştirme.</span><span class="sxs-lookup"><span data-stu-id="77a90-106">Docking a control to its parent.</span></span>  
  
-   <span data-ttu-id="77a90-107">Yönünü değiştirme bir <xref:System.Windows.Forms.SplitContainer> denetim.</span><span class="sxs-lookup"><span data-stu-id="77a90-107">Changing the orientation of a <xref:System.Windows.Forms.SplitContainer> control.</span></span>  
  
 <span data-ttu-id="77a90-108">Geliştirme hızlandırmak için tasarım zamanında bunları tek bir hareketi gibi genel görevleri gerçekleştirmenize olanak sağlayan bağlama duyarlı menüler olan akıllı etiketler birçok denetim sunar.</span><span class="sxs-lookup"><span data-stu-id="77a90-108">To speed development, many controls offer smart tags, which are context-sensitive menus that allow you to perform common tasks like these in a single gesture at design time.</span></span> <span data-ttu-id="77a90-109">Bu görevleri adlı *akıllı etiket fiiller*.</span><span class="sxs-lookup"><span data-stu-id="77a90-109">These tasks are called *smart-tag verbs*.</span></span>  
  
 <span data-ttu-id="77a90-110">Akıllı etiketler Tasarımcısı'nda ömrü için bir denetim örneğine eklenen kalır ve her zaman kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="77a90-110">Smart tags remain attached to a control instance for its lifetime in the designer and are always available.</span></span>  
  
 <span data-ttu-id="77a90-111">Bu örneklerde gösterilen görevler aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="77a90-111">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="77a90-112">Windows Forms projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="77a90-112">Creating a Windows Forms project</span></span>  
  
-   <span data-ttu-id="77a90-113">Akıllı etiketleri kullanarak</span><span class="sxs-lookup"><span data-stu-id="77a90-113">Using smart tags</span></span>  
  
-   <span data-ttu-id="77a90-114">Akıllı etiketler devre dışı bırakma ve etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="77a90-114">Enabling and Disabling Smart Tags</span></span>  
  
 <span data-ttu-id="77a90-115">İşiniz bittiğinde, bu önemli yerleşim özellikleri tarafından oynadığı rol anlaşılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="77a90-115">When you are finished, you will have an understanding of the role played by these important layout features.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="77a90-116">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="77a90-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="77a90-117">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="77a90-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="77a90-118">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="77a90-118">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="77a90-119">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="77a90-119">Creating the Project</span></span>  
 <span data-ttu-id="77a90-120">Projeyi oluşturmak ve formu ayarlamak için ilk adımdır bakın.</span><span class="sxs-lookup"><span data-stu-id="77a90-120">The first step is to create the project and set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="77a90-121">Proje oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="77a90-121">To create the project</span></span>  
  
1.  <span data-ttu-id="77a90-122">"SmartTagsExample" adlı bir Windows tabanlı bir uygulama projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="77a90-122">Create a Windows-based application project called "SmartTagsExample".</span></span> <span data-ttu-id="77a90-123">Ayrıntılar için bkz [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span><span class="sxs-lookup"><span data-stu-id="77a90-123">For details, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="77a90-124">Formda seçin **Windows Form Tasarımcısı**.</span><span class="sxs-lookup"><span data-stu-id="77a90-124">Select the form in the **Windows Forms Designer**.</span></span>  
  
## <a name="using-smart-tags"></a><span data-ttu-id="77a90-125">Akıllı etiketleri kullanarak</span><span class="sxs-lookup"><span data-stu-id="77a90-125">Using Smart Tags</span></span>  
 <span data-ttu-id="77a90-126">Akıllı etiketler her zaman bunları teklif denetimlerinde tasarım zamanında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="77a90-126">Smart tags are always available at design time on controls that offer them.</span></span>  
  
#### <a name="to-use-smart-tags"></a><span data-ttu-id="77a90-127">Akıllı etiketleri kullanma</span><span class="sxs-lookup"><span data-stu-id="77a90-127">To use smart tags</span></span>  
  
1.  <span data-ttu-id="77a90-128">Sürükleme bir <xref:System.Windows.Forms.TabControl> gelen **araç** formunuza.</span><span class="sxs-lookup"><span data-stu-id="77a90-128">Drag a <xref:System.Windows.Forms.TabControl> from the **Toolbox** onto your form.</span></span> <span data-ttu-id="77a90-129">Akıllı etiket karakteri unutmayın (![akıllı etiket karakteri](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) görünen üzerinde yan, <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="77a90-129">Note the smart-tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) that appears on the side of the <xref:System.Windows.Forms.TabControl>.</span></span>  
  
2.  <span data-ttu-id="77a90-130">Akıllı etiket karakteri'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="77a90-130">Click the smart-tag glyph.</span></span> <span data-ttu-id="77a90-131">Karakter yanında görüntülenen kısayol menüsünden seçin **sekmesi Ekle** öğesi.</span><span class="sxs-lookup"><span data-stu-id="77a90-131">In the shortcut menu that appears next to the glyph, select the **Add Tab** item.</span></span> <span data-ttu-id="77a90-132">Yeni bir sekme sayfası eklenir gözlemlemek <xref:System.Windows.Forms.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="77a90-132">Observe that a new tab page is added to the <xref:System.Windows.Forms.TabControl>.</span></span>  
  
3.  <span data-ttu-id="77a90-133">Sürükleme bir <xref:System.Windows.Forms.TableLayoutPanel> gelen denetim **araç** formunuza.</span><span class="sxs-lookup"><span data-stu-id="77a90-133">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>  
  
4.  <span data-ttu-id="77a90-134">Akıllı etiket karakteri'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="77a90-134">Click the smart-tag glyph.</span></span> <span data-ttu-id="77a90-135">Karakter yanında görüntülenen kısayol menüsünden seçin **Sütun Ekle** öğesi.</span><span class="sxs-lookup"><span data-stu-id="77a90-135">In the shortcut menu that appears next to the glyph, select the **Add Column** item.</span></span> <span data-ttu-id="77a90-136">Yeni bir sütun eklenir gözlemlemek <xref:System.Windows.Forms.TableLayoutPanel> denetim.</span><span class="sxs-lookup"><span data-stu-id="77a90-136">Observe that a new column is added to the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
5.  <span data-ttu-id="77a90-137">Sürükleme bir <xref:System.Windows.Forms.SplitContainer> gelen denetim **araç** formunuza.</span><span class="sxs-lookup"><span data-stu-id="77a90-137">Drag a <xref:System.Windows.Forms.SplitContainer> control from the **Toolbox** onto your form.</span></span>  
  
6.  <span data-ttu-id="77a90-138">Akıllı etiket karakteri'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="77a90-138">Click the smart-tag glyph.</span></span> <span data-ttu-id="77a90-139">Karakter yanında görüntülenen kısayol menüsünden seçin **Yatay bölümlendirici yönlendirmesini** öğesi.</span><span class="sxs-lookup"><span data-stu-id="77a90-139">In the shortcut menu that appears next to the glyph, select the **Horizontal splitter orientation** item.</span></span> <span data-ttu-id="77a90-140">Görüntülendiğini <xref:System.Windows.Forms.SplitContainer> denetimin ayırıcıyı olduğu şimdi yatay yönelimli.</span><span class="sxs-lookup"><span data-stu-id="77a90-140">Observe that the <xref:System.Windows.Forms.SplitContainer> control's splitter bar is now oriented horizontally.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77a90-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="77a90-141">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 <xref:System.Windows.Forms.TabControl>  
 <xref:System.Windows.Forms.SplitContainer>  
 <xref:System.ComponentModel.Design.DesignerActionList>  
 [<span data-ttu-id="77a90-142">İzlenecek yol: Bir Windows Forms bileşenine akıllı etiketler ekleme</span><span class="sxs-lookup"><span data-stu-id="77a90-142">Walkthrough: Adding Smart Tags to a Windows Forms Component</span></span>](http://msdn.microsoft.com/library/a6814169-fa7d-4527-808c-637ca5c95f63)
