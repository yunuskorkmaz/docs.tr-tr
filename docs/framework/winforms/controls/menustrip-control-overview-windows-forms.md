---
title: MenuStrip Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- MenuStrip
helpviewer_keywords:
- MenuStrip control [Windows Forms], about MenuStrip control
- menus [Windows Forms], creating
ms.assetid: f45516e5-bf01-4468-b851-d45f4c33c055
ms.openlocfilehash: 46a3a25415db77ee261f5fb1c3bf114b2275a2d4
ms.sourcegitcommit: 8c6426a3d2adff5fbcbe1fed0f28eda718c15351
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/02/2019
ms.locfileid: "68733452"
---
# <a name="menustrip-control-overview-windows-forms"></a><span data-ttu-id="338d6-102">MenuStrip Denetimine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="338d6-102">MenuStrip Control Overview (Windows Forms)</span></span>
<span data-ttu-id="338d6-103">Menüler, ortak bir temaya göre gruplanmış komutları tutarak kullanıcılarınıza işlevselliği sunar.</span><span class="sxs-lookup"><span data-stu-id="338d6-103">Menus expose functionality to your users by holding commands that are grouped by a common theme.</span></span>  
  
 <span data-ttu-id="338d6-104"><xref:System.Windows.Forms.MenuStrip> Denetim, .NET Framework sürüm 2,0 ' de tanıtılmıştı.</span><span class="sxs-lookup"><span data-stu-id="338d6-104">The <xref:System.Windows.Forms.MenuStrip> control was introduced in version 2.0 of the .NET Framework.</span></span> <span data-ttu-id="338d6-105"><xref:System.Windows.Forms.MenuStrip> Denetimiyle, Microsoft Office bulunan gibi kolayca menüler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="338d6-105">With the <xref:System.Windows.Forms.MenuStrip> control, you can easily create menus like those found in Microsoft Office.</span></span>  
  
 <span data-ttu-id="338d6-106"><xref:System.Windows.Forms.MenuStrip> Denetim, çoklu belge arabirimi (MDI) ve menü birleştirme, araç ipuçları ve taşmayı destekler.</span><span class="sxs-lookup"><span data-stu-id="338d6-106">The <xref:System.Windows.Forms.MenuStrip> control supports the multiple-document interface (MDI) and menu merging, tool tips, and overflow.</span></span> <span data-ttu-id="338d6-107">Erişim tuşları, kısayol tuşları, onay işaretleri, görüntüler ve ayırıcı çubuklar ekleyerek menülerinizi kullanılabilirliğini ve okunabilirliğini geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="338d6-107">You can enhance the usability and readability of your menus by adding access keys, shortcut keys, check marks, images, and separator bars.</span></span>  
  
 <span data-ttu-id="338d6-108">Denetim yerini alır ve <xref:System.Windows.Forms.MainMenu> <xref:System.Windows.Forms.MainMenu> denetime işlevsellik ekler; ancak, denetim geriye dönük uyumluluk için ve isterseniz daha sonra kullanılmak üzere tutulur. <xref:System.Windows.Forms.MenuStrip></span><span class="sxs-lookup"><span data-stu-id="338d6-108">The <xref:System.Windows.Forms.MenuStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.MainMenu> control; however, the <xref:System.Windows.Forms.MainMenu> control is retained for backward compatibility and future use if you choose.</span></span>  
  
## <a name="ways-to-use-the-menustrip-control"></a><span data-ttu-id="338d6-109">MenuStrip denetimini kullanmanın yolları</span><span class="sxs-lookup"><span data-stu-id="338d6-109">Ways to Use the MenuStrip Control</span></span>  
 <span data-ttu-id="338d6-110">Şunları yapmak için denetimi kullanın: <xref:System.Windows.Forms.MenuStrip></span><span class="sxs-lookup"><span data-stu-id="338d6-110">Use the <xref:System.Windows.Forms.MenuStrip> control to:</span></span>  
  
- <span data-ttu-id="338d6-111">Metin ve görüntü sıralama ve hizalama, sürükle ve bırak işlemleri, MDI, taşma ve menü komutlarının diğer modları gibi gelişmiş kullanıcı arabirimi ve düzen özelliklerini destekleyen kolayca özelleştirilmiş, yaygın olarak kullanılan menüler oluşturun.</span><span class="sxs-lookup"><span data-stu-id="338d6-111">Create easily customized, commonly employed menus that support advanced user interface and layout features, such as text and image ordering and alignment, drag-and-drop operations, MDI, overflow, and alternate modes of accessing menu commands.</span></span>  
  
- <span data-ttu-id="338d6-112">İşletim sisteminin tipik görünümünü ve davranışını destekler.</span><span class="sxs-lookup"><span data-stu-id="338d6-112">Support the typical appearance and behavior of the operating system.</span></span>  
  
- <span data-ttu-id="338d6-113">Olayları tüm kapsayıcılar ve içerilen öğeler için, diğer denetimler için de olayları idare ettiğiniz şekilde işleyin.</span><span class="sxs-lookup"><span data-stu-id="338d6-113">Handle events consistently for all containers and contained items, in the same way you handle events for other controls.</span></span>  
  
 <span data-ttu-id="338d6-114">Aşağıdaki tabloda, <xref:System.Windows.Forms.MenuStrip> ve ilişkili sınıfların bazı özellikle önemli özellikleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="338d6-114">The following table shows some particularly important properties of <xref:System.Windows.Forms.MenuStrip> and associated classes.</span></span>  
  
|<span data-ttu-id="338d6-115">Özellik</span><span class="sxs-lookup"><span data-stu-id="338d6-115">Property</span></span>|<span data-ttu-id="338d6-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="338d6-116">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>|<span data-ttu-id="338d6-117">MDI alt formlarının listesini <xref:System.Windows.Forms.ToolStripMenuItem> göstermek için kullanılan öğesini alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="338d6-117">Gets or sets the <xref:System.Windows.Forms.ToolStripMenuItem> that is used to display a list of MDI child forms.</span></span>|  
|<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A?displayProperty=nameWithType>|<span data-ttu-id="338d6-118">Alt menülerin MDI uygulamalarında üst menülerle nasıl birleştirildiğini alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="338d6-118">Gets or sets how child menus are merged with parent menus in MDI applications.</span></span>|  
|<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A?displayProperty=nameWithType>|<span data-ttu-id="338d6-119">MDI uygulamalarında bir menü içindeki birleştirilmiş öğenin konumunu alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="338d6-119">Gets or sets the position of a merged item within a menu in MDI applications.</span></span>|  
|<xref:System.Windows.Forms.Form.IsMdiContainer%2A?displayProperty=nameWithType>|<span data-ttu-id="338d6-120">Formun MDI alt formları için bir kapsayıcı olup olmadığını gösteren bir değer alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="338d6-120">Gets or sets a value indicating whether the form is a container for MDI child forms.</span></span>|  
|<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A>|<span data-ttu-id="338d6-121">İçin araç ipuçlarının gösterilip gösterilmeyeceğini gösteren bir değer alır veya ayarlar <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="338d6-121">Gets or sets a value indicating whether tool tips are shown for the <xref:System.Windows.Forms.MenuStrip>.</span></span>|  
|<xref:System.Windows.Forms.MenuStrip.CanOverflow%2A>|<span data-ttu-id="338d6-122">' Nin taşma işlevini <xref:System.Windows.Forms.MenuStrip> destekleyip desteklemediğini gösteren bir değer alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="338d6-122">Gets or sets a value indicating whether the <xref:System.Windows.Forms.MenuStrip> supports overflow functionality.</span></span>|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>|<span data-ttu-id="338d6-123">İle ilişkili kısayol tuşlarını alır veya ayarlar <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="338d6-123">Gets or sets the shortcut keys associated with the <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>|<span data-ttu-id="338d6-124">İle <xref:System.Windows.Forms.ToolStripMenuItem> ilişkili kısayol tuşlarının ' nin yanında <xref:System.Windows.Forms.ToolStripMenuItem>görüntülenip görüntülenmediğini gösteren bir değer alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="338d6-124">Gets or sets a value indicating whether the shortcut keys that are associated with the <xref:System.Windows.Forms.ToolStripMenuItem> are displayed next to the <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>|  
  
 <span data-ttu-id="338d6-125">Aşağıdaki tabloda, önemli <xref:System.Windows.Forms.MenuStrip> yardımcı sınıflar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="338d6-125">The following table shows the important <xref:System.Windows.Forms.MenuStrip> companion classes.</span></span>  
  
|<span data-ttu-id="338d6-126">örneği</span><span class="sxs-lookup"><span data-stu-id="338d6-126">Class</span></span>|<span data-ttu-id="338d6-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="338d6-127">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|<span data-ttu-id="338d6-128"><xref:System.Windows.Forms.MenuStrip> Veya<xref:System.Windows.Forms.ContextMenuStrip>üzerinde görünen seçilebilir bir seçeneği temsil eder.</span><span class="sxs-lookup"><span data-stu-id="338d6-128">Represents a selectable option displayed on a <xref:System.Windows.Forms.MenuStrip> or <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>|  
|<xref:System.Windows.Forms.ContextMenuStrip>|<span data-ttu-id="338d6-129">Bir kısayol menüsünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="338d6-129">Represents a shortcut menu.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDown>|<span data-ttu-id="338d6-130">Kullanıcının bir <xref:System.Windows.Forms.ToolStripDropDownButton> veya daha yüksek düzey menü öğesine tıkladığı zaman görüntülenen listeden tek bir öğe seçmesini sağlayan bir denetimi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="338d6-130">Represents a control that allows the user to select a single item from a list that is displayed when the user clicks a <xref:System.Windows.Forms.ToolStripDropDownButton> or a higher-level menu item.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|<span data-ttu-id="338d6-131">Tıklandığında <xref:System.Windows.Forms.ToolStripItem> , açılan öğeden türetilmiş denetimler için temel işlevleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="338d6-131">Provides basic functionality for controls derived from <xref:System.Windows.Forms.ToolStripItem> that display drop-down items when clicked.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="338d6-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="338d6-132">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripDropDown>
