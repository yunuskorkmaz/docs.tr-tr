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
ms.openlocfilehash: e30f4b21d8b8f1a4c5a168402ce5cc386d932f86
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43510617"
---
# <a name="listview-control-windows-forms"></a><span data-ttu-id="e4677-102">ListView Denetimi (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="e4677-102">ListView Control (Windows Forms)</span></span>
<span data-ttu-id="e4677-103">Windows Forms `ListView` denetim simgeler ile öğeler bir listesini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e4677-103">The Windows Forms `ListView` control displays a list of items with icons.</span></span> <span data-ttu-id="e4677-104">Bir liste görünümü sağ bölme Windows Explorer'ın gibi bir kullanıcı arabirimi oluşturmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4677-104">You can use a list view to create a user interface like the right pane of Windows Explorer.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e4677-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="e4677-105">In This Section</span></span>  
 [<span data-ttu-id="e4677-106">ListView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e4677-106">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 <span data-ttu-id="e4677-107">Bu denetim ve önemli özellikler ve özellikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="e4677-107">Describes this control and its key features and properties.</span></span>  
  
 [<span data-ttu-id="e4677-108">Nasıl yapılır: Windows Forms ListView Denetimi ile Öğe Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="e4677-108">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 <span data-ttu-id="e4677-109">Öğeleri listesi görünümünden ekleyip açıklar.</span><span class="sxs-lookup"><span data-stu-id="e4677-109">Describes how to add or remove items from a list view.</span></span>  
  
 [<span data-ttu-id="e4677-110">Nasıl yapılır: Windows Forms ListView Denetimine Sütun Ekleme</span><span class="sxs-lookup"><span data-stu-id="e4677-110">How to: Add Columns to the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)  
 <span data-ttu-id="e4677-111">Her liste öğesi hakkında bilgi görüntülemek için sütunlar oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="e4677-111">Describes how to create columns in order to display information about each list item.</span></span>  
  
 [<span data-ttu-id="e4677-112">Nasıl yapılır: Windows Forms ListView Denetimi için Simgeler Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="e4677-112">How to: Display Icons for the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 <span data-ttu-id="e4677-113">Bir liste görünümü büyük veya küçük simgeleri görüntülemek için uygun bir görüntü listesi ilişkilendirmek nasıl açıklar.</span><span class="sxs-lookup"><span data-stu-id="e4677-113">Describes how to associate a list view with an appropriate image list for displaying large or small icons.</span></span>  
  
 [<span data-ttu-id="e4677-114">Nasıl yapılır: Windows Forms ListView Denetimiyle Sütunlardaki Alt Öğeleri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="e4677-114">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)  
 <span data-ttu-id="e4677-115">Sütunlarda her bir liste öğesi hakkında bilgi görüntülemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="e4677-115">Describes how to display information about each list item in columns.</span></span>  
  
 [<span data-ttu-id="e4677-116">Nasıl yapılır: Windows Forms ListView Denetiminde Öğe Seçme</span><span class="sxs-lookup"><span data-stu-id="e4677-116">How to: Select an Item in the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-an-item-in-the-windows-forms-listview-control.md)  
 <span data-ttu-id="e4677-117">Program aracılığıyla bir öğe seçin açıklar.</span><span class="sxs-lookup"><span data-stu-id="e4677-117">Describes how to programmatically select an item.</span></span>  
  
 [<span data-ttu-id="e4677-118">Nasıl yapılır: Windows Forms ListView Denetimindeki Öğeleri Gruplama</span><span class="sxs-lookup"><span data-stu-id="e4677-118">How to: Group Items in a Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-group-items-in-a-windows-forms-listview-control.md)  
 <span data-ttu-id="e4677-119">Kategorilere ayrılmış görüntü gruplarının nasıl oluşturulacağını ve öğeleri her grup için atama açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e4677-119">Describes how to create groups for categorized display and how to assign items to each group.</span></span>  
  
 <span data-ttu-id="e4677-120">Bu özellik yalnızca kullanılabilir [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e4677-120">This feature is available only for [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span></span>  
  
 [<span data-ttu-id="e4677-121">Nasıl yapılır: Windows Forms ListView Denetiminde Döşeme Görünümünü Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="e4677-121">How to: Enable Tile View in a Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-enable-tile-view-in-a-windows-forms-listview-control.md)  
 <span data-ttu-id="e4677-122">Her biri büyük bir simge ve birden çok metin satırı oluşur kutucuk olarak öğeleri görüntülemek nasıl açıklar.</span><span class="sxs-lookup"><span data-stu-id="e4677-122">Describes how to display items as tiles, each of which is comprised of a large icon and multiple lines of text.</span></span>  
  
 <span data-ttu-id="e4677-123">Bu özellik yalnızca kullanılabilir [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e4677-123">This feature is available only for [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span></span>  
  
 [<span data-ttu-id="e4677-124">Nasıl yapılır: Windows Forms ListView Denetiminde Ekleme İşareti Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="e4677-124">How to: Display an Insertion Mark in a Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control.md)  
 <span data-ttu-id="e4677-125">Kullanıcı geri bildirimi ekleme işareti her fare işaretçisi konumunun bırakma konumunu belirten bir Sürükle ve bırak işlemleri için uygulanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e4677-125">Describes how to implement user-feedback for drag-and-drop operations in which an insertion mark indicates the drop location for each mouse-pointer position.</span></span>  
  
 <span data-ttu-id="e4677-126">Bu özellik yalnızca kullanılabilir [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e4677-126">This feature is available only for [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span></span>  
  
 [<span data-ttu-id="e4677-127">Nasıl yapılır: ListView Denetimine Arama Yetenekleri Ekleme</span><span class="sxs-lookup"><span data-stu-id="e4677-127">How to: Add Search Capabilities to a ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-search-capabilities-to-a-listview-control.md)  
 <span data-ttu-id="e4677-128">Program aracılığıyla metin arama veya ekran koordinatları kullanarak bir öğeyi bulmak açıklar.</span><span class="sxs-lookup"><span data-stu-id="e4677-128">Describes how to programmatically find an item using either text search or screen coordinates.</span></span>  
  
-   [<span data-ttu-id="e4677-129">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms ListView Denetiminde Döşeme Görünümünü Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="e4677-129">How to: Enable Tile View in a Windows Forms ListView Control Using the Designer</span></span>](enable-tile-view-in-a-wf-listview-control-using-the-designer.md)  
  
-   [<span data-ttu-id="e4677-130">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms ListView Denetimi ile Öğe Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="e4677-130">How to: Add and Remove Items with the Windows Forms ListView Control Using the Designer</span></span>](add-and-remove-items-with-wf-listview-control-using-the-designer.md)  
  
-   [<span data-ttu-id="e4677-131">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms ListView Denetimine Sütunlar Ekleme</span><span class="sxs-lookup"><span data-stu-id="e4677-131">How to: Add Columns to the Windows Forms ListView Control Using the Designer</span></span>](how-to-add-columns-to-the-windows-forms-listview-control-using-the-designer.md)  
  
-   [<span data-ttu-id="e4677-132">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms ListView Denetimindeki Öğeleri Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="e4677-132">How to: Group Items in a Windows Forms ListView Control Using the Designer</span></span>](how-to-group-items-in-a-windows-forms-listview-control-using-the-designer.md)  
  
-   [<span data-ttu-id="e4677-133">İzlenecek yol: Tasarımcıyı Kullanarak ListView ve TreeView Denetimleri ile Gezgin Stilinde bir Arabirim Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e4677-133">Walkthrough: Creating an Explorer Style Interface with the ListView and TreeView Controls Using the Designer</span></span>](creating-an-explorer-style-interface-with-the-listview-and-treeview.md)  
  
## <a name="reference"></a><span data-ttu-id="e4677-134">Başvuru</span><span class="sxs-lookup"><span data-stu-id="e4677-134">Reference</span></span>  
 <span data-ttu-id="e4677-135"><xref:System.Windows.Forms.ListView> Sınıfı</span><span class="sxs-lookup"><span data-stu-id="e4677-135"><xref:System.Windows.Forms.ListView> class</span></span>  
 <span data-ttu-id="e4677-136">Bu sınıf açıklar ve tüm üyeleri için bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="e4677-136">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e4677-137">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="e4677-137">Related Sections</span></span>  
 [<span data-ttu-id="e4677-138">Nasıl yapılır: Bir TreeView veya ListView Denetimine Özel Bilgi Ekleme (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="e4677-138">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
 <span data-ttu-id="e4677-139">Liste görünümünde bir öğe veya ağaç görünümünde bir düğüm herhangi bir alanlar, yöntemler veya gereksinim duyduğunuz oluşturucular eklemek için devralınacak açıklar.</span><span class="sxs-lookup"><span data-stu-id="e4677-139">Describes how to inherit from an item in a list view or a node in a tree view in order to add any fields, methods, or constructors you need.</span></span>  
  
 [<span data-ttu-id="e4677-140">ImageList Bileşeni</span><span class="sxs-lookup"><span data-stu-id="e4677-140">ImageList Component</span></span>](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)  
 <span data-ttu-id="e4677-141">Açıklayan bir görüntü listesi ve başlıca özellikleri ve özellikleri.</span><span class="sxs-lookup"><span data-stu-id="e4677-141">Explains what an image list is and its key features and properties.</span></span>  
  
 [<span data-ttu-id="e4677-142">Nasıl yapılır: Windows Forms ile Çok Bölmeli Kullanıcı Arabirimi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e4677-142">How to: Create a Multipane User Interface with Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)  
 <span data-ttu-id="e4677-143">Birden fazla bölme içeren bir Windows formunu yerleştirmeye ilişkin yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e4677-143">Gives instructions for laying out a Windows Form with multiple panes.</span></span>  
  
 [<span data-ttu-id="e4677-144">Windows XP özellikleri ve Windows Forms denetimleri</span><span class="sxs-lookup"><span data-stu-id="e4677-144">Windows XP Features and Windows Forms Controls</span></span>](https://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)  
 <span data-ttu-id="e4677-145">Geçerli Windows XP özgü özelliklerinden yararlanmanıza açıklanmaktadır <xref:System.Windows.Forms.ListView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="e4677-145">Explains how to take advantage of Windows XP-specific features that apply to the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4677-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e4677-146">See Also</span></span>  
 [<span data-ttu-id="e4677-147">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="e4677-147">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
