---
title: UI Otomasyon Denetim Türlerine Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control types
- control types, UI Automation
ms.assetid: 75159ef8-bd43-4d13-acb7-1f1fe9253160
ms.openlocfilehash: ec2dd3635f09144985df278be1d53ead675d3080
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442632"
---
# <a name="ui-automation-control-types-overview"></a><span data-ttu-id="ac7f0-102">UI Otomasyon Denetim Türlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ac7f0-102">UI Automation Control Types Overview</span></span>
> [!NOTE]
> <span data-ttu-id="ac7f0-103">Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="ac7f0-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="ac7f0-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="ac7f0-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] <span data-ttu-id="ac7f0-105">denetim türleri, Birleşik giriş kutusu ya da düğme gibi belirli bir öğenin ne tür bir denetimin temsil ettiğini göstermek için kullanılabilecek iyi bilinen tanımlayıcılardır.</span><span class="sxs-lookup"><span data-stu-id="ac7f0-105">control types are well-known identifiers that can be used to indicate what kind of control a particular element represents, such as a combo box or a button.</span></span>  
  
 <span data-ttu-id="ac7f0-106">İyi bilinen bir tanımlayıcıya sahip olmak, yardımcı teknoloji cihazlarının [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] hangi tür denetimlerin kullanılabilir olduğunu ve denetimlerle nasıl etkileşime gireceğini belirlemenizi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="ac7f0-106">Having a well-known identifier makes it easier for assistive technology devices to determine what types of controls are available in the [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] and how to interact with the controls.</span></span>  
  
<a name="UI_Automation_Control_Type_Requisites"></a>   
## <a name="ui-automation-control-type-requisites"></a><span data-ttu-id="ac7f0-107">UI Otomasyonu Denetim türü gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="ac7f0-107">UI Automation Control Type Requisites</span></span>  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] <span data-ttu-id="ac7f0-108">denetim türleri, sağlayıcıların karşılaması gereken koşullar kümesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac7f0-108">control types provide a set of conditions that providers must meet.</span></span> <span data-ttu-id="ac7f0-109">Bu koşullar karşılandığında denetim, belirli denetim türü adını kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="ac7f0-109">When these conditions are met, the control can use the specific control type name.</span></span> <span data-ttu-id="ac7f0-110">Her denetim türü aşağıdakiler için koşullara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="ac7f0-110">Each control type has conditions for the following:</span></span>  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <span data-ttu-id="ac7f0-111">Denetim desenleri — hangi denetim desenlerinin desteklenmelidir, hangi Denetim desenleri isteğe bağlıdır ve hangi denetim desenlerinin denetim tarafından desteklenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="ac7f0-111">control patterns—which control patterns must be supported, which control patterns are optional, and which control patterns must not be supported by the control.</span></span>  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <span data-ttu-id="ac7f0-112">özellik değerleri — hangi özellik değerlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="ac7f0-112">property values—which property values are supported.</span></span>  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <span data-ttu-id="ac7f0-113">ağaç yapısı — denetim için gereken [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısı.</span><span class="sxs-lookup"><span data-stu-id="ac7f0-113">tree structure—the required [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree structure for the control.</span></span>  
  
 <span data-ttu-id="ac7f0-114">Bir denetim belirli bir denetim türünün koşullarını karşılıyorsa, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> Özellik değeri bu denetim türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="ac7f0-114">When a control meets the conditions for a particular control type, the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> property value will indicate that control type.</span></span>  
  
<a name="Current_UI_Automation_Control_Types"></a>   
## <a name="current-ui-automation-control-types"></a><span data-ttu-id="ac7f0-115">Geçerli UI Otomasyon Denetim türleri</span><span class="sxs-lookup"><span data-stu-id="ac7f0-115">Current UI Automation Control Types</span></span>  
 <span data-ttu-id="ac7f0-116">Aşağıdaki liste, geçerli [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] denetim türleri kümesini içerir:</span><span class="sxs-lookup"><span data-stu-id="ac7f0-116">The following list contains the current set of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] control types:</span></span>  
  
- [<span data-ttu-id="ac7f0-117">Button Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="ac7f0-117">UI Automation Support for the Button Control Type</span></span>](ui-automation-support-for-the-button-control-type.md)  
  
- [<span data-ttu-id="ac7f0-118">Calendar Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="ac7f0-118">UI Automation Support for the Calendar Control Type</span></span>](ui-automation-support-for-the-calendar-control-type.md)  
  
- [<span data-ttu-id="ac7f0-119">CheckBox Denetim Türü için UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="ac7f0-119">UI Automation Support for the CheckBox Control Type</span></span>](ui-automation-support-for-the-checkbox-control-type.md)  
  
- [<span data-ttu-id="ac7f0-120">ComboBox Denetim Türü için UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="ac7f0-120">UI Automation Support for the ComboBox Control Type</span></span>](ui-automation-support-for-the-combobox-control-type.md)  
  
- [<span data-ttu-id="ac7f0-121">DataGrid Denetim Türü için UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="ac7f0-121">UI Automation Support for the DataGrid Control Type</span></span>](ui-automation-support-for-the-datagrid-control-type.md)  
  
- [<span data-ttu-id="ac7f0-122">DataItem Denetim Türü için UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="ac7f0-122">UI Automation Support for the DataItem Control Type</span></span>](ui-automation-support-for-the-dataitem-control-type.md)  
  
- [<span data-ttu-id="ac7f0-123">Document Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="ac7f0-123">UI Automation Support for the Document Control Type</span></span>](ui-automation-support-for-the-document-control-type.md)  
  
- [<span data-ttu-id="ac7f0-124">Edit Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="ac7f0-124">UI Automation Support for the Edit Control Type</span></span>](ui-automation-support-for-the-edit-control-type.md)  
  
- [<span data-ttu-id="ac7f0-125">Group Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="ac7f0-125">UI Automation Support for the Group Control Type</span></span>](ui-automation-support-for-the-group-control-type.md)  
  
- [<span data-ttu-id="ac7f0-126">Header Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="ac7f0-126">UI Automation Support for the Header Control Type</span></span>](ui-automation-support-for-the-header-control-type.md)  
  
- [<span data-ttu-id="ac7f0-127">HeaderItem Denetim Türü için UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="ac7f0-127">UI Automation Support for the HeaderItem Control Type</span></span>](ui-automation-support-for-the-headeritem-control-type.md)  
  
- [<span data-ttu-id="ac7f0-128">Hyperlink Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="ac7f0-128">UI Automation Support for the Hyperlink Control Type</span></span>](ui-automation-support-for-the-hyperlink-control-type.md)  
  
- [<span data-ttu-id="ac7f0-129">Image Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="ac7f0-129">UI Automation Support for the Image Control Type</span></span>](ui-automation-support-for-the-image-control-type.md)  
  
- [<span data-ttu-id="ac7f0-130">List Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="ac7f0-130">UI Automation Support for the List Control Type</span></span>](ui-automation-support-for-the-list-control-type.md)  
  
- [<span data-ttu-id="ac7f0-131">ListItem Denetim Türü için UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="ac7f0-131">UI Automation Support for the ListItem Control Type</span></span>](ui-automation-support-for-the-listitem-control-type.md)  
  
- [<span data-ttu-id="ac7f0-132">Menu Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="ac7f0-132">UI Automation Support for the Menu Control Type</span></span>](ui-automation-support-for-the-menu-control-type.md)  
  
- [<span data-ttu-id="ac7f0-133">MenuBar Denetim Türü için UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="ac7f0-133">UI Automation Support for the MenuBar Control Type</span></span>](ui-automation-support-for-the-menubar-control-type.md)  
  
- [<span data-ttu-id="ac7f0-134">MenuItem Denetim Türü için UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="ac7f0-134">UI Automation Support for the MenuItem Control Type</span></span>](ui-automation-support-for-the-menuitem-control-type.md)  
  
- [<span data-ttu-id="ac7f0-135">Pane Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="ac7f0-135">UI Automation Support for the Pane Control Type</span></span>](ui-automation-support-for-the-pane-control-type.md)  
  
- [<span data-ttu-id="ac7f0-136">ProgressBar Denetim Türü için UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="ac7f0-136">UI Automation Support for the ProgressBar Control Type</span></span>](ui-automation-support-for-the-progressbar-control-type.md)  
  
- [<span data-ttu-id="ac7f0-137">RadioButton Denetim Türü için UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="ac7f0-137">UI Automation Support for the RadioButton Control Type</span></span>](ui-automation-support-for-the-radiobutton-control-type.md)  
  
- [<span data-ttu-id="ac7f0-138">ScrollBar Denetim Türü için UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="ac7f0-138">UI Automation Support for the ScrollBar Control Type</span></span>](ui-automation-support-for-the-scrollbar-control-type.md)  
  
- [<span data-ttu-id="ac7f0-139">Separator Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="ac7f0-139">UI Automation Support for the Separator Control Type</span></span>](ui-automation-support-for-the-separator-control-type.md)  
  
- [<span data-ttu-id="ac7f0-140">Slider Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="ac7f0-140">UI Automation Support for the Slider Control Type</span></span>](ui-automation-support-for-the-slider-control-type.md)  
  
- [<span data-ttu-id="ac7f0-141">Spinner Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="ac7f0-141">UI Automation Support for the Spinner Control Type</span></span>](ui-automation-support-for-the-spinner-control-type.md)  
  
- [<span data-ttu-id="ac7f0-142">SplitButton Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="ac7f0-142">UI Automation Support for the SplitButton Control Type</span></span>](ui-automation-support-for-the-splitbutton-control-type.md)  
  
- [<span data-ttu-id="ac7f0-143">StatusBar Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="ac7f0-143">UI Automation Support for the StatusBar Control Type</span></span>](ui-automation-support-for-the-statusbar-control-type.md)  
  
- [<span data-ttu-id="ac7f0-144">Tab Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="ac7f0-144">UI Automation Support for the Tab Control Type</span></span>](ui-automation-support-for-the-tab-control-type.md)  
  
- [<span data-ttu-id="ac7f0-145">TabItem Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="ac7f0-145">UI Automation Support for the TabItem Control Type</span></span>](ui-automation-support-for-the-tabitem-control-type.md)  
  
- [<span data-ttu-id="ac7f0-146">Table Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="ac7f0-146">UI Automation Support for the Table Control Type</span></span>](ui-automation-support-for-the-table-control-type.md)  
  
- [<span data-ttu-id="ac7f0-147">Text Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="ac7f0-147">UI Automation Support for the Text Control Type</span></span>](ui-automation-support-for-the-text-control-type.md)  
  
- [<span data-ttu-id="ac7f0-148">Thumb Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="ac7f0-148">UI Automation Support for the Thumb Control Type</span></span>](ui-automation-support-for-the-thumb-control-type.md)  
  
- [<span data-ttu-id="ac7f0-149">TitleBar Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="ac7f0-149">UI Automation Support for the TitleBar Control Type</span></span>](ui-automation-support-for-the-titlebar-control-type.md)  
  
- [<span data-ttu-id="ac7f0-150">ToolBar Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="ac7f0-150">UI Automation Support for the ToolBar Control Type</span></span>](ui-automation-support-for-the-toolbar-control-type.md)  
  
- [<span data-ttu-id="ac7f0-151">ToolTip Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="ac7f0-151">UI Automation Support for the ToolTip Control Type</span></span>](ui-automation-support-for-the-tooltip-control-type.md)  
  
- [<span data-ttu-id="ac7f0-152">Tree Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="ac7f0-152">UI Automation Support for the Tree Control Type</span></span>](ui-automation-support-for-the-tree-control-type.md)  
  
- [<span data-ttu-id="ac7f0-153">TreeItem Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="ac7f0-153">UI Automation Support for the TreeItem Control Type</span></span>](ui-automation-support-for-the-treeitem-control-type.md)  
  
- [<span data-ttu-id="ac7f0-154">Window Denetim Türü İçin UI Otomasyonu Desteği</span><span class="sxs-lookup"><span data-stu-id="ac7f0-154">UI Automation Support for the Window Control Type</span></span>](ui-automation-support-for-the-window-control-type.md)  
  
## <a name="see-also"></a><span data-ttu-id="ac7f0-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac7f0-155">See also</span></span>

- <xref:System.Windows.Automation.ControlType>
