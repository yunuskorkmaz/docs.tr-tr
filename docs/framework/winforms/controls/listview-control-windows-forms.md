---
title: ListView Denetimi (Windows Forms)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9bc771b81e1db87f3d881dc2a0ab84f7aad93247
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="listview-control-windows-forms"></a><span data-ttu-id="a6b9f-102">ListView Denetimi (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="a6b9f-102">ListView Control (Windows Forms)</span></span>
<span data-ttu-id="a6b9f-103">Windows Forms `ListView` denetim simgeler ile öğeler listesini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a6b9f-103">The Windows Forms `ListView` control displays a list of items with icons.</span></span> <span data-ttu-id="a6b9f-104">Sağ bölmede Windows Explorer gibi bir kullanıcı arabirimi oluşturmak için bir liste görünümü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a6b9f-104">You can use a list view to create a user interface like the right pane of Windows Explorer.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a6b9f-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="a6b9f-105">In This Section</span></span>  
 [<span data-ttu-id="a6b9f-106">ListView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a6b9f-106">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 <span data-ttu-id="a6b9f-107">Bu denetim ve anahtar özellikleri ve özelliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="a6b9f-107">Describes this control and its key features and properties.</span></span>  
  
 [<span data-ttu-id="a6b9f-108">Nasıl yapılır: Windows Forms ListView Denetimi ile Öğe Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="a6b9f-108">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 <span data-ttu-id="a6b9f-109">Öğeleri listesi görünümünden ekleyip açıklar.</span><span class="sxs-lookup"><span data-stu-id="a6b9f-109">Describes how to add or remove items from a list view.</span></span>  
  
 [<span data-ttu-id="a6b9f-110">Nasıl yapılır: Windows Forms ListView Denetimine Sütun Ekleme</span><span class="sxs-lookup"><span data-stu-id="a6b9f-110">How to: Add Columns to the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)  
 <span data-ttu-id="a6b9f-111">Her liste öğesi hakkındaki bilgileri görüntülemek için sütunları oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="a6b9f-111">Describes how to create columns in order to display information about each list item.</span></span>  
  
 [<span data-ttu-id="a6b9f-112">Nasıl yapılır: Windows Forms ListView Denetimi için Simgeler Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="a6b9f-112">How to: Display Icons for the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 <span data-ttu-id="a6b9f-113">Büyük veya küçük simgeleri görüntüleme için uygun görüntü listesi bir liste görünümü ilişkilendirmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="a6b9f-113">Describes how to associate a list view with an appropriate image list for displaying large or small icons.</span></span>  
  
 [<span data-ttu-id="a6b9f-114">Nasıl yapılır: Windows Forms ListView Denetimiyle Sütunlardaki Alt Öğeleri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="a6b9f-114">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)  
 <span data-ttu-id="a6b9f-115">Her liste öğesi hakkında bilgi görüntülemek sütunlar açıklar.</span><span class="sxs-lookup"><span data-stu-id="a6b9f-115">Describes how to display information about each list item in columns.</span></span>  
  
 [<span data-ttu-id="a6b9f-116">Nasıl yapılır: Windows Forms ListView Denetiminde Öğe Seçme</span><span class="sxs-lookup"><span data-stu-id="a6b9f-116">How to: Select an Item in the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-an-item-in-the-windows-forms-listview-control.md)  
 <span data-ttu-id="a6b9f-117">Program aracılığıyla bir öğe seçin açıklar.</span><span class="sxs-lookup"><span data-stu-id="a6b9f-117">Describes how to programmatically select an item.</span></span>  
  
 [<span data-ttu-id="a6b9f-118">Nasıl yapılır: Windows Forms ListView Denetimindeki Öğeleri Gruplama</span><span class="sxs-lookup"><span data-stu-id="a6b9f-118">How to: Group Items in a Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-group-items-in-a-windows-forms-listview-control.md)  
 <span data-ttu-id="a6b9f-119">Kategorilere ayrılmış görüntülemek için gruplar oluşturun ve her gruba öğeleri Ata açıklar.</span><span class="sxs-lookup"><span data-stu-id="a6b9f-119">Describes how to create groups for categorized display and how to assign items to each group.</span></span>  
  
 <span data-ttu-id="a6b9f-120">Bu özellik yalnızca kullanılabilir [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a6b9f-120">This feature is available only for [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span></span>  
  
 [<span data-ttu-id="a6b9f-121">Nasıl yapılır: Windows Forms ListView Denetiminde Döşeme Görünümünü Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="a6b9f-121">How to: Enable Tile View in a Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-enable-tile-view-in-a-windows-forms-listview-control.md)  
 <span data-ttu-id="a6b9f-122">Her biri büyük bir simge ve birkaç satırlık metin oluşur kutucukları olarak öğeleri görüntüleme açıklar.</span><span class="sxs-lookup"><span data-stu-id="a6b9f-122">Describes how to display items as tiles, each of which is comprised of a large icon and multiple lines of text.</span></span>  
  
 <span data-ttu-id="a6b9f-123">Bu özellik yalnızca kullanılabilir [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a6b9f-123">This feature is available only for [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span></span>  
  
 [<span data-ttu-id="a6b9f-124">Nasıl yapılır: Windows Forms ListView Denetiminde Ekleme İşareti Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="a6b9f-124">How to: Display an Insertion Mark in a Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control.md)  
 <span data-ttu-id="a6b9f-125">Kullanıcı geri bildirim ekleme işareti her fare işaretçisini konumunun bırakma konumu gösterir sürükle ve bırak işlemleri için uygulanacak açıklar.</span><span class="sxs-lookup"><span data-stu-id="a6b9f-125">Describes how to implement user-feedback for drag-and-drop operations in which an insertion mark indicates the drop location for each mouse-pointer position.</span></span>  
  
 <span data-ttu-id="a6b9f-126">Bu özellik yalnızca kullanılabilir [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a6b9f-126">This feature is available only for [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span></span>  
  
 [<span data-ttu-id="a6b9f-127">Nasıl yapılır: ListView Denetimine Arama Yetenekleri Ekleme</span><span class="sxs-lookup"><span data-stu-id="a6b9f-127">How to: Add Search Capabilities to a ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-search-capabilities-to-a-listview-control.md)  
 <span data-ttu-id="a6b9f-128">Program aracılığıyla metin arama veya ekran koordinatları kullanarak bir öğeyi bulmak açıklar.</span><span class="sxs-lookup"><span data-stu-id="a6b9f-128">Describes how to programmatically find an item using either text search or screen coordinates.</span></span>  
  
-   <span data-ttu-id="a6b9f-129">[Nasıl yapılır: Tasarımcı Kullanarak Windows Forms ListView Denetiminde Döşeme Görünümünü Etkinleştirme](http://msdn.microsoft.com/library/ms233655\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="a6b9f-129">[How to: Enable Tile View in a Windows Forms ListView Control Using the Designer](http://msdn.microsoft.com/library/ms233655\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="a6b9f-130">[Nasıl yapılır: Tasarımcı Kullanarak Windows Forms ListView Denetimi ile Öğe Ekleme ve Kaldırma](http://msdn.microsoft.com/library/ms233671\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="a6b9f-130">[How to: Add and Remove Items with the Windows Forms ListView Control Using the Designer](http://msdn.microsoft.com/library/ms233671\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="a6b9f-131">[Nasıl yapılır: Tasarımcı Kullanarak Windows Forms ListView Denetimine Sütunlar Ekleme](http://msdn.microsoft.com/library/ms233652\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="a6b9f-131">[How to: Add Columns to the Windows Forms ListView Control Using the Designer](http://msdn.microsoft.com/library/ms233652\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="a6b9f-132">[Nasıl yapılır: Tasarımcı Kullanarak Windows Forms ListView Denetimindeki Öğeleri Gruplandırma](http://msdn.microsoft.com/library/ms233663\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="a6b9f-132">[How to: Group Items in a Windows Forms ListView Control Using the Designer](http://msdn.microsoft.com/library/ms233663\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="a6b9f-133">[İzlenecek yol: Tasarımcıyı Kullanarak ListView ve TreeView Denetimleri ile Gezgin Stilinde bir Arabirim Oluşturma](http://msdn.microsoft.com/library/ms171645\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="a6b9f-133">[Walkthrough: Creating an Explorer Style Interface with the ListView and TreeView Controls Using the Designer](http://msdn.microsoft.com/library/ms171645\(v=vs.110\))</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a6b9f-134">Başvuru</span><span class="sxs-lookup"><span data-stu-id="a6b9f-134">Reference</span></span>  
 <span data-ttu-id="a6b9f-135"><xref:System.Windows.Forms.ListView>sınıfı</span><span class="sxs-lookup"><span data-stu-id="a6b9f-135"><xref:System.Windows.Forms.ListView> class</span></span>  
 <span data-ttu-id="a6b9f-136">Bu sınıf tanımlar ve tüm üyeleri bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="a6b9f-136">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a6b9f-137">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="a6b9f-137">Related Sections</span></span>  
 [<span data-ttu-id="a6b9f-138">Nasıl yapılır: Bir TreeView veya ListView Denetimine Özel Bilgi Ekleme (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="a6b9f-138">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
 <span data-ttu-id="a6b9f-139">Herhangi bir alanlar, yöntemi veya gereksinim duyduğunuz oluşturucular eklemek için liste görünümünde bir öğe veya ağaç görünümünde bir düğüm devral açıklar.</span><span class="sxs-lookup"><span data-stu-id="a6b9f-139">Describes how to inherit from an item in a list view or a node in a tree view in order to add any fields, methods, or constructors you need.</span></span>  
  
 [<span data-ttu-id="a6b9f-140">ImageList Bileşeni</span><span class="sxs-lookup"><span data-stu-id="a6b9f-140">ImageList Component</span></span>](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)  
 <span data-ttu-id="a6b9f-141">Açıklayan bir görüntü listesi ve anahtar özellikleri ve özellikleri.</span><span class="sxs-lookup"><span data-stu-id="a6b9f-141">Explains what an image list is and its key features and properties.</span></span>  
  
 [<span data-ttu-id="a6b9f-142">Nasıl yapılır: Windows Forms ile Çok Bölmeli Kullanıcı Arabirimi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a6b9f-142">How to: Create a Multipane User Interface with Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)  
 <span data-ttu-id="a6b9f-143">Birden çok bölmeleri içeren bir Windows formunu yerleştirmeye ilişkin talimatlar sunar.</span><span class="sxs-lookup"><span data-stu-id="a6b9f-143">Gives instructions for laying out a Windows Form with multiple panes.</span></span>  
  
 [<span data-ttu-id="a6b9f-144">Windows XP özellikleri ve Windows Forms denetimleri</span><span class="sxs-lookup"><span data-stu-id="a6b9f-144">Windows XP Features and Windows Forms Controls</span></span>](http://msdn.microsoft.com/en-us/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)  
 <span data-ttu-id="a6b9f-145">Geçerli Windows XP özgü özelliklerden yararlanmak nasıl açıklanmaktadır <xref:System.Windows.Forms.ListView> denetim.</span><span class="sxs-lookup"><span data-stu-id="a6b9f-145">Explains how to take advantage of Windows XP-specific features that apply to the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6b9f-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a6b9f-146">See Also</span></span>  
 [<span data-ttu-id="a6b9f-147">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="a6b9f-147">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
