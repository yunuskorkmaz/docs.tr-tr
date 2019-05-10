---
title: MenuStrip Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- MenuStrip
helpviewer_keywords:
- MenuStrip control [Windows Forms], about MenuStrip control
- menus [Windows Forms], creating
ms.assetid: f45516e5-bf01-4468-b851-d45f4c33c055
ms.openlocfilehash: b72fcf75aeebc297d09cbaa9dbf00bb2370b1222
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625760"
---
# <a name="menustrip-control-overview-windows-forms"></a><span data-ttu-id="3cfac-102">MenuStrip Denetimine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="3cfac-102">MenuStrip Control Overview (Windows Forms)</span></span>
<span data-ttu-id="3cfac-103">Menüleri, ortak bir tema tarafından gruplandırılmış komutları tutarak kullanıcılarınıza işlevselliği kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="3cfac-103">Menus expose functionality to your users by holding commands that are grouped by a common theme.</span></span>  
  
 <span data-ttu-id="3cfac-104"><xref:System.Windows.Forms.MenuStrip> Denetimi bu Visual Studio ve .NET Framework sürümü için yenidir.</span><span class="sxs-lookup"><span data-stu-id="3cfac-104">The <xref:System.Windows.Forms.MenuStrip> control is new to this version of Visual Studio and the .NET Framework.</span></span> <span data-ttu-id="3cfac-105">Denetim ile Microsoft Office içinde bulunanlar gibi menüleri kolayca oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3cfac-105">With the control, you can easily create menus like those found in Microsoft Office.</span></span>  
  
 <span data-ttu-id="3cfac-106"><xref:System.Windows.Forms.MenuStrip> Çok Belgeli Arabirim (MDI) ve menü birleştirme, araç ipuçları ve taşma denetimini destekler.</span><span class="sxs-lookup"><span data-stu-id="3cfac-106">The <xref:System.Windows.Forms.MenuStrip> control supports the multiple-document interface (MDI) and menu merging, tool tips, and overflow.</span></span> <span data-ttu-id="3cfac-107">Erişim tuşları, kısayol tuşları, onay işaretleri, görüntüleri ve ayırıcı çubukları ekleyerek, menüler okunabilirliğini ve kullanılabilirliğini geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3cfac-107">You can enhance the usability and readability of your menus by adding access keys, shortcut keys, check marks, images, and separator bars.</span></span>  
  
 <span data-ttu-id="3cfac-108"><xref:System.Windows.Forms.MenuStrip> Denetimi değiştirir ve işlevsellik ekler <xref:System.Windows.Forms.MainMenu> denetler; ancak, <xref:System.Windows.Forms.MainMenu> denetim korunur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.</span><span class="sxs-lookup"><span data-stu-id="3cfac-108">The <xref:System.Windows.Forms.MenuStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.MainMenu> control; however, the <xref:System.Windows.Forms.MainMenu> control is retained for backward compatibility and future use if you choose.</span></span>  
  
## <a name="ways-to-use-the-menustrip-control"></a><span data-ttu-id="3cfac-109">MenuStrip denetimi kullanmanın yolları</span><span class="sxs-lookup"><span data-stu-id="3cfac-109">Ways to Use the MenuStrip Control</span></span>  
 <span data-ttu-id="3cfac-110">Kullanım <xref:System.Windows.Forms.MenuStrip> denetimi:</span><span class="sxs-lookup"><span data-stu-id="3cfac-110">Use the <xref:System.Windows.Forms.MenuStrip> control to:</span></span>  
  
- <span data-ttu-id="3cfac-111">Özelleştirilmiş kolayca oluşturun, metin ve görüntü sıralama ve hizalama, sürükle ve bırak işlemleri, MDI, taşma ve menü komutları erişmenin alternatif modları gibi arabirimi ve düzen özelliklerini destekleyen yaygın olarak çalıştırılan menüleri gelişmiş kullanıcı.</span><span class="sxs-lookup"><span data-stu-id="3cfac-111">Create easily customized, commonly employed menus that support advanced user interface and layout features, such as text and image ordering and alignment, drag-and-drop operations, MDI, overflow, and alternate modes of accessing menu commands.</span></span>  
  
- <span data-ttu-id="3cfac-112">Tipik bir görünümünü ve davranışını işletim sistemini destekler.</span><span class="sxs-lookup"><span data-stu-id="3cfac-112">Support the typical appearance and behavior of the operating system.</span></span>  
  
- <span data-ttu-id="3cfac-113">Diğer denetimlerin olaylarını işlemek aynı şekilde tüm kapsayıcılar ve içerilen öğelerin için tutarlı bir şekilde olayları işleyin.</span><span class="sxs-lookup"><span data-stu-id="3cfac-113">Handle events consistently for all containers and contained items, in the same way you handle events for other controls.</span></span>  
  
 <span data-ttu-id="3cfac-114">Aşağıdaki tablo bazı özellikle önemli özellikleri gösterir <xref:System.Windows.Forms.MenuStrip> ve ilişkilendirilmiş sınıfları.</span><span class="sxs-lookup"><span data-stu-id="3cfac-114">The following table shows some particularly important properties of <xref:System.Windows.Forms.MenuStrip> and associated classes.</span></span>  
  
|<span data-ttu-id="3cfac-115">Özellik</span><span class="sxs-lookup"><span data-stu-id="3cfac-115">Property</span></span>|<span data-ttu-id="3cfac-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3cfac-116">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>|<span data-ttu-id="3cfac-117">Alır veya ayarlar <xref:System.Windows.Forms.ToolStripMenuItem> MDI alt formlarını listesini görüntülemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3cfac-117">Gets or sets the <xref:System.Windows.Forms.ToolStripMenuItem> that is used to display a list of MDI child forms.</span></span>|  
|<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A?displayProperty=nameWithType>|<span data-ttu-id="3cfac-118">Alır veya ayarlar alt menüler üst MDI uygulamaları menülerde nasıl birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3cfac-118">Gets or sets how child menus are merged with parent menus in MDI applications.</span></span>|  
|<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A?displayProperty=nameWithType>|<span data-ttu-id="3cfac-119">Alır veya MDI uygulamaları içindeki birleştirilmiş bir öğenin konumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="3cfac-119">Gets or sets the position of a merged item within a menu in MDI applications.</span></span>|  
|<xref:System.Windows.Forms.Form.IsMdiContainer%2A?displayProperty=nameWithType>|<span data-ttu-id="3cfac-120">Alır veya form MDI alt formlarını için bir kapsayıcı olup olmadığını belirten bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="3cfac-120">Gets or sets a value indicating whether the form is a container for MDI child forms.</span></span>|  
|<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A>|<span data-ttu-id="3cfac-121">Araç ipuçları için gösterilip gösterilmeyeceğini belirten bir değeri alır veya ayarlar <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="3cfac-121">Gets or sets a value indicating whether tool tips are shown for the <xref:System.Windows.Forms.MenuStrip>.</span></span>|  
|<xref:System.Windows.Forms.MenuStrip.CanOverflow%2A>|<span data-ttu-id="3cfac-122">Belirten bir değeri alır veya ayarlar olmadığını <xref:System.Windows.Forms.MenuStrip> overflow işlevselliği destekler.</span><span class="sxs-lookup"><span data-stu-id="3cfac-122">Gets or sets a value indicating whether the <xref:System.Windows.Forms.MenuStrip> supports overflow functionality.</span></span>|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>|<span data-ttu-id="3cfac-123">Alır veya ayarlar ile ilişkili kısayol tuşlarını <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="3cfac-123">Gets or sets the shortcut keys associated with the <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>|<span data-ttu-id="3cfac-124">Alır veya ayarlar kısayol, anahtarları olup olmadığını belirten bir değer ile ilişkili <xref:System.Windows.Forms.ToolStripMenuItem> yanında görüntülenen <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="3cfac-124">Gets or sets a value indicating whether the shortcut keys that are associated with the <xref:System.Windows.Forms.ToolStripMenuItem> are displayed next to the <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>|  
  
 <span data-ttu-id="3cfac-125">Aşağıdaki tablo önemli gösterir <xref:System.Windows.Forms.MenuStrip> Yahoo! companion sınıfları.</span><span class="sxs-lookup"><span data-stu-id="3cfac-125">The following table shows the important <xref:System.Windows.Forms.MenuStrip> companion classes.</span></span>  
  
|<span data-ttu-id="3cfac-126">örneği</span><span class="sxs-lookup"><span data-stu-id="3cfac-126">Class</span></span>|<span data-ttu-id="3cfac-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3cfac-127">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|<span data-ttu-id="3cfac-128">Görüntülenen bir seçilebilir seçeneğini temsil eder bir <xref:System.Windows.Forms.MenuStrip> veya <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="3cfac-128">Represents a selectable option displayed on a <xref:System.Windows.Forms.MenuStrip> or <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>|  
|<xref:System.Windows.Forms.ContextMenuStrip>|<span data-ttu-id="3cfac-129">Bir kısayol menüsü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3cfac-129">Represents a shortcut menu.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDown>|<span data-ttu-id="3cfac-130">Kullanıcı tıkladığında görüntülenen listeden tek bir öğe kullanıcıya veren bir denetimi temsil eder bir <xref:System.Windows.Forms.ToolStripDropDownButton> ya da daha üst düzey menü öğesi.</span><span class="sxs-lookup"><span data-stu-id="3cfac-130">Represents a control that allows the user to select a single item from a list that is displayed when the user clicks a <xref:System.Windows.Forms.ToolStripDropDownButton> or a higher-level menu item.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|<span data-ttu-id="3cfac-131">Türetilen denetimler için temel işlevleri sağlar <xref:System.Windows.Forms.ToolStripItem> tıklandığında açılan öğeleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="3cfac-131">Provides basic functionality for controls derived from <xref:System.Windows.Forms.ToolStripItem> that display drop-down items when clicked.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3cfac-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3cfac-132">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripDropDown>
