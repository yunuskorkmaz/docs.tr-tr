---
title: ListView Denetimi (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- lists
- checked list items [Windows Forms], Windows Forms controls
- user interface [Windows Forms], creating
- lists [Windows Forms], items with icons
- icons [Windows Forms], listing with items
- list views
- ListView control [Windows Forms]
- list controls [Windows Forms], List view
ms.assetid: 9f71cf5c-82da-488a-a04e-ef52c0817187
ms.openlocfilehash: 4472d2a46b27c75d06c5e4cd6fbab18842ed111c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54591948"
---
# <a name="listview-control-windows-forms"></a><span data-ttu-id="83ceb-102">ListView Denetimi (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="83ceb-102">ListView Control (Windows Forms)</span></span>
<span data-ttu-id="83ceb-103">Windows Forms `ListView` denetim simgeler ile öğeler bir listesini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="83ceb-103">The Windows Forms `ListView` control displays a list of items with icons.</span></span> <span data-ttu-id="83ceb-104">Bir liste görünümü sağ bölme Windows Explorer'ın gibi bir kullanıcı arabirimi oluşturmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83ceb-104">You can use a list view to create a user interface like the right pane of Windows Explorer.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="83ceb-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="83ceb-105">In This Section</span></span>  
 [<span data-ttu-id="83ceb-106">ListView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="83ceb-106">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 <span data-ttu-id="83ceb-107">Bu denetim ve önemli özellikler ve özellikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="83ceb-107">Describes this control and its key features and properties.</span></span>  
  
 [<span data-ttu-id="83ceb-108">Nasıl yapılır: Windows Forms ListView denetimi ile öğe ekleyip</span><span class="sxs-lookup"><span data-stu-id="83ceb-108">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 <span data-ttu-id="83ceb-109">Öğeleri listesi görünümünden ekleyip açıklar.</span><span class="sxs-lookup"><span data-stu-id="83ceb-109">Describes how to add or remove items from a list view.</span></span>  
  
 [<span data-ttu-id="83ceb-110">Nasıl yapılır: Windows Forms ListView denetimine sütun ekleme</span><span class="sxs-lookup"><span data-stu-id="83ceb-110">How to: Add Columns to the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)  
 <span data-ttu-id="83ceb-111">Her liste öğesi hakkında bilgi görüntülemek için sütunlar oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="83ceb-111">Describes how to create columns in order to display information about each list item.</span></span>  
  
 [<span data-ttu-id="83ceb-112">Nasıl yapılır: Windows Forms ListView denetimi için simgeler görüntüleme</span><span class="sxs-lookup"><span data-stu-id="83ceb-112">How to: Display Icons for the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 <span data-ttu-id="83ceb-113">Bir liste görünümü büyük veya küçük simgeleri görüntülemek için uygun bir görüntü listesi ilişkilendirmek nasıl açıklar.</span><span class="sxs-lookup"><span data-stu-id="83ceb-113">Describes how to associate a list view with an appropriate image list for displaying large or small icons.</span></span>  
  
 [<span data-ttu-id="83ceb-114">Nasıl yapılır: Windows Forms ListView denetimiyle sütunlardaki alt öğeleri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="83ceb-114">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)  
 <span data-ttu-id="83ceb-115">Sütunlarda her bir liste öğesi hakkında bilgi görüntülemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="83ceb-115">Describes how to display information about each list item in columns.</span></span>  
  
 [<span data-ttu-id="83ceb-116">Nasıl yapılır: Windows Forms ListView denetiminde bir öğe seçin</span><span class="sxs-lookup"><span data-stu-id="83ceb-116">How to: Select an Item in the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-an-item-in-the-windows-forms-listview-control.md)  
 <span data-ttu-id="83ceb-117">Program aracılığıyla bir öğe seçin açıklar.</span><span class="sxs-lookup"><span data-stu-id="83ceb-117">Describes how to programmatically select an item.</span></span>  
  
 [<span data-ttu-id="83ceb-118">Nasıl yapılır: Bir Windows Forms ListView denetimi içinde öğeleri gruplandırma</span><span class="sxs-lookup"><span data-stu-id="83ceb-118">How to: Group Items in a Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-group-items-in-a-windows-forms-listview-control.md)  
 <span data-ttu-id="83ceb-119">Kategorilere ayrılmış görüntü gruplarının nasıl oluşturulacağını ve öğeleri her grup için atama açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="83ceb-119">Describes how to create groups for categorized display and how to assign items to each group.</span></span>  
  
 <span data-ttu-id="83ceb-120">Bu özellik yalnızca kullanılabilir [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span><span class="sxs-lookup"><span data-stu-id="83ceb-120">This feature is available only for [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span></span>  
  
 [<span data-ttu-id="83ceb-121">Nasıl yapılır: Windows Forms ListView denetiminde döşeme görünümünü etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="83ceb-121">How to: Enable Tile View in a Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-enable-tile-view-in-a-windows-forms-listview-control.md)  
 <span data-ttu-id="83ceb-122">Her biri büyük bir simge ve birden çok metin satırı oluşur kutucuk olarak öğeleri görüntülemek nasıl açıklar.</span><span class="sxs-lookup"><span data-stu-id="83ceb-122">Describes how to display items as tiles, each of which is comprised of a large icon and multiple lines of text.</span></span>  
  
 <span data-ttu-id="83ceb-123">Bu özellik yalnızca kullanılabilir [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span><span class="sxs-lookup"><span data-stu-id="83ceb-123">This feature is available only for [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span></span>  
  
 [<span data-ttu-id="83ceb-124">Nasıl yapılır: Bir Windows Forms ListView denetiminde ekleme işareti görüntüleme</span><span class="sxs-lookup"><span data-stu-id="83ceb-124">How to: Display an Insertion Mark in a Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control.md)  
 <span data-ttu-id="83ceb-125">Kullanıcı geri bildirimi ekleme işareti her fare işaretçisi konumunun bırakma konumunu belirten bir Sürükle ve bırak işlemleri için uygulanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="83ceb-125">Describes how to implement user-feedback for drag-and-drop operations in which an insertion mark indicates the drop location for each mouse-pointer position.</span></span>  
  
 <span data-ttu-id="83ceb-126">Bu özellik yalnızca kullanılabilir [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span><span class="sxs-lookup"><span data-stu-id="83ceb-126">This feature is available only for [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span></span>  
  
 [<span data-ttu-id="83ceb-127">Nasıl yapılır: Bir ListView denetimine arama yetenekleri ekleme</span><span class="sxs-lookup"><span data-stu-id="83ceb-127">How to: Add Search Capabilities to a ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-search-capabilities-to-a-listview-control.md)  
 <span data-ttu-id="83ceb-128">Program aracılığıyla metin arama veya ekran koordinatları kullanarak bir öğeyi bulmak açıklar.</span><span class="sxs-lookup"><span data-stu-id="83ceb-128">Describes how to programmatically find an item using either text search or screen coordinates.</span></span>  
  
-   [<span data-ttu-id="83ceb-129">Nasıl yapılır: Tasarımcı kullanarak Windows Forms ListView denetimi döşeme görünümünü etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="83ceb-129">How to: Enable Tile View in a Windows Forms ListView Control Using the Designer</span></span>](enable-tile-view-in-a-wf-listview-control-using-the-designer.md)  
  
-   [<span data-ttu-id="83ceb-130">Nasıl yapılır: Tasarımcı kullanarak Windows Forms ListView denetimi ile öğe ekleyip</span><span class="sxs-lookup"><span data-stu-id="83ceb-130">How to: Add and Remove Items with the Windows Forms ListView Control Using the Designer</span></span>](add-and-remove-items-with-wf-listview-control-using-the-designer.md)  
  
-   [<span data-ttu-id="83ceb-131">Nasıl yapılır: Windows Forms ListView Tasarımcısı'nı kullanarak denetimine sütun ekleme</span><span class="sxs-lookup"><span data-stu-id="83ceb-131">How to: Add Columns to the Windows Forms ListView Control Using the Designer</span></span>](how-to-add-columns-to-the-windows-forms-listview-control-using-the-designer.md)  
  
-   [<span data-ttu-id="83ceb-132">Nasıl yapılır: Tasarımcı kullanarak Windows Forms ListView denetimi içinde öğeleri gruplandırma</span><span class="sxs-lookup"><span data-stu-id="83ceb-132">How to: Group Items in a Windows Forms ListView Control Using the Designer</span></span>](how-to-group-items-in-a-windows-forms-listview-control-using-the-designer.md)  
  
-   [<span data-ttu-id="83ceb-133">İzlenecek yol: ListView ve tasarımcı kullanarak TreeView denetimleri ile Gezgin stilinde bir arabirim oluşturma</span><span class="sxs-lookup"><span data-stu-id="83ceb-133">Walkthrough: Creating an Explorer Style Interface with the ListView and TreeView Controls Using the Designer</span></span>](creating-an-explorer-style-interface-with-the-listview-and-treeview.md)  
  
## <a name="reference"></a><span data-ttu-id="83ceb-134">Başvuru</span><span class="sxs-lookup"><span data-stu-id="83ceb-134">Reference</span></span>  
 <span data-ttu-id="83ceb-135"><xref:System.Windows.Forms.ListView> Sınıfı</span><span class="sxs-lookup"><span data-stu-id="83ceb-135"><xref:System.Windows.Forms.ListView> class</span></span>  
 <span data-ttu-id="83ceb-136">Bu sınıf açıklar ve tüm üyeleri için bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="83ceb-136">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="83ceb-137">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="83ceb-137">Related Sections</span></span>  
 [<span data-ttu-id="83ceb-138">Nasıl yapılır: Bir TreeView veya ListView denetimi (Windows Forms) özel bilgi ekleme</span><span class="sxs-lookup"><span data-stu-id="83ceb-138">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
 <span data-ttu-id="83ceb-139">Liste görünümünde bir öğe veya ağaç görünümünde bir düğüm herhangi bir alanlar, yöntemler veya gereksinim duyduğunuz oluşturucular eklemek için devralınacak açıklar.</span><span class="sxs-lookup"><span data-stu-id="83ceb-139">Describes how to inherit from an item in a list view or a node in a tree view in order to add any fields, methods, or constructors you need.</span></span>  
  
 [<span data-ttu-id="83ceb-140">ImageList Bileşeni</span><span class="sxs-lookup"><span data-stu-id="83ceb-140">ImageList Component</span></span>](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)  
 <span data-ttu-id="83ceb-141">Açıklayan bir görüntü listesi ve başlıca özellikleri ve özellikleri.</span><span class="sxs-lookup"><span data-stu-id="83ceb-141">Explains what an image list is and its key features and properties.</span></span>  
  
 [<span data-ttu-id="83ceb-142">Nasıl yapılır: Windows Forms ile çok bölmeli kullanıcı arabirimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="83ceb-142">How to: Create a Multipane User Interface with Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)  
 <span data-ttu-id="83ceb-143">Birden fazla bölme içeren bir Windows formunu yerleştirmeye ilişkin yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="83ceb-143">Gives instructions for laying out a Windows Form with multiple panes.</span></span>  
  
 [<span data-ttu-id="83ceb-144">Windows XP özellikleri ve Windows Forms denetimleri</span><span class="sxs-lookup"><span data-stu-id="83ceb-144">Windows XP Features and Windows Forms Controls</span></span>](https://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)  
 <span data-ttu-id="83ceb-145">Geçerli Windows XP özgü özelliklerinden yararlanmanıza açıklanmaktadır <xref:System.Windows.Forms.ListView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="83ceb-145">Explains how to take advantage of Windows XP-specific features that apply to the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83ceb-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="83ceb-146">See also</span></span>
- [<span data-ttu-id="83ceb-147">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="83ceb-147">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
