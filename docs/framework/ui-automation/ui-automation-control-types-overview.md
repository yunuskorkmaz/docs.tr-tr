---
title: UI Otomasyon Denetim Türlerine Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control types
- control types, UI Automation
ms.assetid: 75159ef8-bd43-4d13-acb7-1f1fe9253160
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: cf62d09c6b4cd5a135e6daf4749ecdfb56b50cd4
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43779337"
---
# <a name="ui-automation-control-types-overview"></a><span data-ttu-id="519fe-102">UI Otomasyon Denetim Türlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="519fe-102">UI Automation Control Types Overview</span></span>
> [!NOTE]
>  <span data-ttu-id="519fe-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="519fe-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="519fe-104">En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="519fe-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]<span data-ttu-id="519fe-105"> Denetim türleri ne tür bir denetim belirli bir öğenin, birleşik giriş kutusu veya bir düğme gibi temsil eden belirtmek için kullanılan bilinen tanıtıcılardır.</span><span class="sxs-lookup"><span data-stu-id="519fe-105"> control types are well-known identifiers that can be used to indicate what kind of control a particular element represents, such as a combo box or a button.</span></span>  
  
 <span data-ttu-id="519fe-106">İyi bilinen bir tanımlayıcıya sahip kolaylaştırır ne tür denetimler kullanılabilir belirlemek yardımcı teknoloji cihazları [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] ve denetimler ile etkileşim öğrenin.</span><span class="sxs-lookup"><span data-stu-id="519fe-106">Having a well-known identifier makes it easier for assistive technology devices to determine what types of controls are available in the [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] and how to interact with the controls.</span></span>  
  
<a name="UI_Automation_Control_Type_Requisites"></a>   
## <a name="ui-automation-control-type-requisites"></a><span data-ttu-id="519fe-107">UI Otomasyon denetim türü gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="519fe-107">UI Automation Control Type Requisites</span></span>  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]<span data-ttu-id="519fe-108"> Denetim türleri sağlayıcıları karşılaması gereken koşulları kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="519fe-108"> control types provide a set of conditions that providers must meet.</span></span> <span data-ttu-id="519fe-109">Bu koşullar karşılandığında, denetimin belirli denetim türü adı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="519fe-109">When these conditions are met, the control can use the specific control type name.</span></span> <span data-ttu-id="519fe-110">Her denetim türü için aşağıdaki koşullar vardır:</span><span class="sxs-lookup"><span data-stu-id="519fe-110">Each control type has conditions for the following:</span></span>  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="519fe-111"> Denetim desenleri — hangi denetim düzenleri desteklenmelidir denetleyen biçimlerinin isteğe bağlı olduğu ve hangi denetim düzenleri denetim tarafından değil desteklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="519fe-111"> control patterns—which control patterns must be supported, which control patterns are optional, and which control patterns must not be supported by the control.</span></span>  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="519fe-112"> özellik değerlerini — hangi özellik değerleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="519fe-112"> property values—which property values are supported.</span></span>  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="519fe-113"> ağaç yapısı — gerekli [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısı denetimi.</span><span class="sxs-lookup"><span data-stu-id="519fe-113"> tree structure—the required [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree structure for the control.</span></span>  
  
 <span data-ttu-id="519fe-114">Bir denetimi, belirli bir denetim türü için koşulları karşıladığında <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> özellik değeri, bu denetim gösterecektir türü.</span><span class="sxs-lookup"><span data-stu-id="519fe-114">When a control meets the conditions for a particular control type, the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> property value will indicate that control type.</span></span>  
  
<a name="Current_UI_Automation_Control_Types"></a>   
## <a name="current-ui-automation-control-types"></a><span data-ttu-id="519fe-115">Geçerli UI Otomasyon denetim türleri</span><span class="sxs-lookup"><span data-stu-id="519fe-115">Current UI Automation Control Types</span></span>  
 <span data-ttu-id="519fe-116">Aşağıdaki listede geçerli kümesini içeren [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] denetim türlerinin:</span><span class="sxs-lookup"><span data-stu-id="519fe-116">The following list contains the current set of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] control types:</span></span>  
  
-   [<span data-ttu-id="519fe-117">Button Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="519fe-117">UI Automation Support for the Button Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-button-control-type.md)  
  
-   [<span data-ttu-id="519fe-118">Calendar Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="519fe-118">UI Automation Support for the Calendar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-calendar-control-type.md)  
  
-   [<span data-ttu-id="519fe-119">CheckBox Denetim Türü için UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="519fe-119">UI Automation Support for the CheckBox Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-checkbox-control-type.md)  
  
-   [<span data-ttu-id="519fe-120">ComboBox Denetim Türü için UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="519fe-120">UI Automation Support for the ComboBox Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-combobox-control-type.md)  
  
-   [<span data-ttu-id="519fe-121">DataGrid Denetim Türü için UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="519fe-121">UI Automation Support for the DataGrid Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-datagrid-control-type.md)  
  
-   [<span data-ttu-id="519fe-122">DataItem Denetim Türü için UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="519fe-122">UI Automation Support for the DataItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-dataitem-control-type.md)  
  
-   [<span data-ttu-id="519fe-123">Document Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="519fe-123">UI Automation Support for the Document Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-document-control-type.md)  
  
-   [<span data-ttu-id="519fe-124">Edit Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="519fe-124">UI Automation Support for the Edit Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-edit-control-type.md)  
  
-   [<span data-ttu-id="519fe-125">Group Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="519fe-125">UI Automation Support for the Group Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-group-control-type.md)  
  
-   [<span data-ttu-id="519fe-126">Header Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="519fe-126">UI Automation Support for the Header Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-header-control-type.md)  
  
-   [<span data-ttu-id="519fe-127">HeaderItem Denetim Türü için UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="519fe-127">UI Automation Support for the HeaderItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-headeritem-control-type.md)  
  
-   [<span data-ttu-id="519fe-128">Hyperlink Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="519fe-128">UI Automation Support for the Hyperlink Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-hyperlink-control-type.md)  
  
-   [<span data-ttu-id="519fe-129">Image Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="519fe-129">UI Automation Support for the Image Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-image-control-type.md)  
  
-   [<span data-ttu-id="519fe-130">List Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="519fe-130">UI Automation Support for the List Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-list-control-type.md)  
  
-   [<span data-ttu-id="519fe-131">ListItem Denetim Türü için UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="519fe-131">UI Automation Support for the ListItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-listitem-control-type.md)  
  
-   [<span data-ttu-id="519fe-132">Menu Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="519fe-132">UI Automation Support for the Menu Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-menu-control-type.md)  
  
-   [<span data-ttu-id="519fe-133">MenuBar Denetim Türü için UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="519fe-133">UI Automation Support for the MenuBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md)  
  
-   [<span data-ttu-id="519fe-134">MenuItem Denetim Türü için UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="519fe-134">UI Automation Support for the MenuItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-menuitem-control-type.md)  
  
-   [<span data-ttu-id="519fe-135">Pane Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="519fe-135">UI Automation Support for the Pane Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-pane-control-type.md)  
  
-   [<span data-ttu-id="519fe-136">ProgressBar Denetim Türü için UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="519fe-136">UI Automation Support for the ProgressBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-progressbar-control-type.md)  
  
-   [<span data-ttu-id="519fe-137">RadioButton Denetim Türü için UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="519fe-137">UI Automation Support for the RadioButton Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-radiobutton-control-type.md)  
  
-   [<span data-ttu-id="519fe-138">ScrollBar Denetim Türü için UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="519fe-138">UI Automation Support for the ScrollBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-scrollbar-control-type.md)  
  
-   [<span data-ttu-id="519fe-139">Separator Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="519fe-139">UI Automation Support for the Separator Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-separator-control-type.md)  
  
-   [<span data-ttu-id="519fe-140">Slider Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="519fe-140">UI Automation Support for the Slider Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-slider-control-type.md)  
  
-   [<span data-ttu-id="519fe-141">Spinner Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="519fe-141">UI Automation Support for the Spinner Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-spinner-control-type.md)  
  
-   [<span data-ttu-id="519fe-142">SplitButton Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="519fe-142">UI Automation Support for the SplitButton Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-splitbutton-control-type.md)  
  
-   [<span data-ttu-id="519fe-143">StatusBar Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="519fe-143">UI Automation Support for the StatusBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-statusbar-control-type.md)  
  
-   [<span data-ttu-id="519fe-144">Tab Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="519fe-144">UI Automation Support for the Tab Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-tab-control-type.md)  
  
-   [<span data-ttu-id="519fe-145">TabItem Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="519fe-145">UI Automation Support for the TabItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-tabitem-control-type.md)  
  
-   [<span data-ttu-id="519fe-146">Table Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="519fe-146">UI Automation Support for the Table Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-table-control-type.md)  
  
-   [<span data-ttu-id="519fe-147">Text Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="519fe-147">UI Automation Support for the Text Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-text-control-type.md)  
  
-   [<span data-ttu-id="519fe-148">Thumb Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="519fe-148">UI Automation Support for the Thumb Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-thumb-control-type.md)  
  
-   [<span data-ttu-id="519fe-149">TitleBar Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="519fe-149">UI Automation Support for the TitleBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-titlebar-control-type.md)  
  
-   [<span data-ttu-id="519fe-150">ToolBar Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="519fe-150">UI Automation Support for the ToolBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-toolbar-control-type.md)  
  
-   [<span data-ttu-id="519fe-151">ToolTip Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="519fe-151">UI Automation Support for the ToolTip Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-tooltip-control-type.md)  
  
-   [<span data-ttu-id="519fe-152">Tree Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="519fe-152">UI Automation Support for the Tree Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-tree-control-type.md)  
  
-   [<span data-ttu-id="519fe-153">TreeItem Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="519fe-153">UI Automation Support for the TreeItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-treeitem-control-type.md)  
  
-   [<span data-ttu-id="519fe-154">Window Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="519fe-154">UI Automation Support for the Window Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-window-control-type.md)  
  
## <a name="see-also"></a><span data-ttu-id="519fe-155">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="519fe-155">See Also</span></span>  
 <xref:System.Windows.Automation.ControlType>
