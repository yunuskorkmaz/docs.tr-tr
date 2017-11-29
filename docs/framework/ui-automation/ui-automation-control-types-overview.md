---
title: "UI Otomasyon Denetim Türlerine Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, control types
- control types, UI Automation
ms.assetid: 75159ef8-bd43-4d13-acb7-1f1fe9253160
caps.latest.revision: "22"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: c1a424f05f2d57f773e8367e102f553d69b7dc22
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ui-automation-control-types-overview"></a><span data-ttu-id="1a8b2-102">UI Otomasyon Denetim Türlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1a8b2-102">UI Automation Control Types Overview</span></span>
> [!NOTE]
>  <span data-ttu-id="1a8b2-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="1a8b2-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="1a8b2-104">Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="1a8b2-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]<span data-ttu-id="1a8b2-105">Denetim türleri ne tür bir denetim belirli bir öğe, bir birleşik giriş kutusu veya düğmesi gibi temsil eden belirtmek için kullanılan iyi bilinen tanımlayıcılardır.</span><span class="sxs-lookup"><span data-stu-id="1a8b2-105"> control types are well-known identifiers that can be used to indicate what kind of control a particular element represents, such as a combo box or a button.</span></span>  
  
 <span data-ttu-id="1a8b2-106">İyi bilinen bir tanımlayıcı sahip kolaylaştırır hangi tür denetimlerin kullanılabilir olduğunu belirlemek yardımcı teknoloji aygıtlarını [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] ve denetimleri ile etkileşime geçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1a8b2-106">Having a well-known identifier makes it easier for assistive technology devices to determine what types of controls are available in the [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] and how to interact with the controls.</span></span>  
  
<a name="UI_Automation_Control_Type_Requisites"></a>   
## <a name="ui-automation-control-type-requisites"></a><span data-ttu-id="1a8b2-107">UI Otomasyon denetim türü gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="1a8b2-107">UI Automation Control Type Requisites</span></span>  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]<span data-ttu-id="1a8b2-108">Denetim türleri sağlayıcıları karşılaması gereken koşulları belirtin.</span><span class="sxs-lookup"><span data-stu-id="1a8b2-108"> control types provide a set of conditions that providers must meet.</span></span> <span data-ttu-id="1a8b2-109">Bu koşullar karşılandığında denetimi belirli denetim türü adı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1a8b2-109">When these conditions are met, the control can use the specific control type name.</span></span> <span data-ttu-id="1a8b2-110">Her denetim türü için aşağıdaki koşullar vardır:</span><span class="sxs-lookup"><span data-stu-id="1a8b2-110">Each control type has conditions for the following:</span></span>  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="1a8b2-111">Denetim desenleri — hangi denetim düzenleri desteklenen, hangi denetimi desenleri isteğe bağlı ve hangi denetim düzenleri gerekir desteklenmiyor denetim tarafından.</span><span class="sxs-lookup"><span data-stu-id="1a8b2-111"> control patterns—which control patterns must be supported, which control patterns are optional, and which control patterns must not be supported by the control.</span></span>  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="1a8b2-112">özellik değerlerini — hangi özellik değerleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="1a8b2-112"> property values—which property values are supported.</span></span>  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="1a8b2-113">ağaç yapısı — gerekli [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısı denetimi için.</span><span class="sxs-lookup"><span data-stu-id="1a8b2-113"> tree structure—the required [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree structure for the control.</span></span>  
  
 <span data-ttu-id="1a8b2-114">Bir denetim belirli denetim türü için koşulları karşıladığında <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> özellik değerini denetleyen göstermek türü.</span><span class="sxs-lookup"><span data-stu-id="1a8b2-114">When a control meets the conditions for a particular control type, the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> property value will indicate that control type.</span></span>  
  
<a name="Current_UI_Automation_Control_Types"></a>   
## <a name="current-ui-automation-control-types"></a><span data-ttu-id="1a8b2-115">Geçerli UI Otomasyon denetim türleri</span><span class="sxs-lookup"><span data-stu-id="1a8b2-115">Current UI Automation Control Types</span></span>  
 <span data-ttu-id="1a8b2-116">Aşağıdaki listede, geçerli kümesi içeriyor. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] kontrol türleri:</span><span class="sxs-lookup"><span data-stu-id="1a8b2-116">The following list contains the current set of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] control types:</span></span>  
  
-   [<span data-ttu-id="1a8b2-117">Düğme denetim türü için UI Otomasyon desteği</span><span class="sxs-lookup"><span data-stu-id="1a8b2-117">UI Automation Support for the Button Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-button-control-type.md)  
  
-   [<span data-ttu-id="1a8b2-118">Takvim denetim türü için UI Otomasyon desteği</span><span class="sxs-lookup"><span data-stu-id="1a8b2-118">UI Automation Support for the Calendar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-calendar-control-type.md)  
  
-   [<span data-ttu-id="1a8b2-119">CheckBox denetim türü için UI Otomasyon desteği</span><span class="sxs-lookup"><span data-stu-id="1a8b2-119">UI Automation Support for the CheckBox Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-checkbox-control-type.md)  
  
-   [<span data-ttu-id="1a8b2-120">ComboBox denetim türü için UI Otomasyon desteği</span><span class="sxs-lookup"><span data-stu-id="1a8b2-120">UI Automation Support for the ComboBox Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-combobox-control-type.md)  
  
-   [<span data-ttu-id="1a8b2-121">DataGrid denetim türü için UI Otomasyon desteği</span><span class="sxs-lookup"><span data-stu-id="1a8b2-121">UI Automation Support for the DataGrid Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-datagrid-control-type.md)  
  
-   [<span data-ttu-id="1a8b2-122">DataItem denetim türü için UI Otomasyon desteği</span><span class="sxs-lookup"><span data-stu-id="1a8b2-122">UI Automation Support for the DataItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-dataitem-control-type.md)  
  
-   [<span data-ttu-id="1a8b2-123">Belge Denetim türü için UI Otomasyon desteği</span><span class="sxs-lookup"><span data-stu-id="1a8b2-123">UI Automation Support for the Document Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-document-control-type.md)  
  
-   [<span data-ttu-id="1a8b2-124">Düzenleme denetim türü için UI Otomasyon desteği</span><span class="sxs-lookup"><span data-stu-id="1a8b2-124">UI Automation Support for the Edit Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-edit-control-type.md)  
  
-   [<span data-ttu-id="1a8b2-125">Grup denetim türü için UI Otomasyon desteği</span><span class="sxs-lookup"><span data-stu-id="1a8b2-125">UI Automation Support for the Group Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-group-control-type.md)  
  
-   [<span data-ttu-id="1a8b2-126">Başlık denetim türü için UI Otomasyon desteği</span><span class="sxs-lookup"><span data-stu-id="1a8b2-126">UI Automation Support for the Header Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-header-control-type.md)  
  
-   [<span data-ttu-id="1a8b2-127">Headerıtem denetim türü için UI Otomasyon desteği</span><span class="sxs-lookup"><span data-stu-id="1a8b2-127">UI Automation Support for the HeaderItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-headeritem-control-type.md)  
  
-   [<span data-ttu-id="1a8b2-128">Köprü denetim türü için UI Otomasyon desteği</span><span class="sxs-lookup"><span data-stu-id="1a8b2-128">UI Automation Support for the Hyperlink Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-hyperlink-control-type.md)  
  
-   [<span data-ttu-id="1a8b2-129">Görüntü Denetim türü için UI Otomasyon desteği</span><span class="sxs-lookup"><span data-stu-id="1a8b2-129">UI Automation Support for the Image Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-image-control-type.md)  
  
-   [<span data-ttu-id="1a8b2-130">Liste Denetim türü için UI Otomasyon desteği</span><span class="sxs-lookup"><span data-stu-id="1a8b2-130">UI Automation Support for the List Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-list-control-type.md)  
  
-   [<span data-ttu-id="1a8b2-131">ListItem denetim türü için UI Otomasyon desteği</span><span class="sxs-lookup"><span data-stu-id="1a8b2-131">UI Automation Support for the ListItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-listitem-control-type.md)  
  
-   [<span data-ttu-id="1a8b2-132">Menü denetim türü için UI Otomasyon desteği</span><span class="sxs-lookup"><span data-stu-id="1a8b2-132">UI Automation Support for the Menu Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-menu-control-type.md)  
  
-   [<span data-ttu-id="1a8b2-133">MenuBar denetim türü için UI Otomasyon desteği</span><span class="sxs-lookup"><span data-stu-id="1a8b2-133">UI Automation Support for the MenuBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md)  
  
-   [<span data-ttu-id="1a8b2-134">MenuItem denetim türü için UI Otomasyon desteği</span><span class="sxs-lookup"><span data-stu-id="1a8b2-134">UI Automation Support for the MenuItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-menuitem-control-type.md)  
  
-   [<span data-ttu-id="1a8b2-135">Bölme denetim türü için UI Otomasyon desteği</span><span class="sxs-lookup"><span data-stu-id="1a8b2-135">UI Automation Support for the Pane Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-pane-control-type.md)  
  
-   [<span data-ttu-id="1a8b2-136">ProgressBar denetim türü için UI Otomasyon desteği</span><span class="sxs-lookup"><span data-stu-id="1a8b2-136">UI Automation Support for the ProgressBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-progressbar-control-type.md)  
  
-   [<span data-ttu-id="1a8b2-137">RadioButton denetim türü için UI Otomasyon desteği</span><span class="sxs-lookup"><span data-stu-id="1a8b2-137">UI Automation Support for the RadioButton Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-radiobutton-control-type.md)  
  
-   [<span data-ttu-id="1a8b2-138">ScrollBar denetim türü için UI Otomasyon desteği</span><span class="sxs-lookup"><span data-stu-id="1a8b2-138">UI Automation Support for the ScrollBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-scrollbar-control-type.md)  
  
-   [<span data-ttu-id="1a8b2-139">Ayırıcı denetim türü için UI Otomasyon desteği</span><span class="sxs-lookup"><span data-stu-id="1a8b2-139">UI Automation Support for the Separator Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-separator-control-type.md)  
  
-   [<span data-ttu-id="1a8b2-140">Kaydırıcı denetim türü için UI Otomasyon desteği</span><span class="sxs-lookup"><span data-stu-id="1a8b2-140">UI Automation Support for the Slider Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-slider-control-type.md)  
  
-   [<span data-ttu-id="1a8b2-141">Değer değiştirici denetim türü için UI Otomasyon desteği</span><span class="sxs-lookup"><span data-stu-id="1a8b2-141">UI Automation Support for the Spinner Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-spinner-control-type.md)  
  
-   [<span data-ttu-id="1a8b2-142">Bölünmüş düğme denetim türü için UI Otomasyon desteği</span><span class="sxs-lookup"><span data-stu-id="1a8b2-142">UI Automation Support for the SplitButton Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-splitbutton-control-type.md)  
  
-   [<span data-ttu-id="1a8b2-143">StatusBar denetim türü için UI Otomasyon desteği</span><span class="sxs-lookup"><span data-stu-id="1a8b2-143">UI Automation Support for the StatusBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-statusbar-control-type.md)  
  
-   [<span data-ttu-id="1a8b2-144">Sekme denetim türü için UI Otomasyon desteği</span><span class="sxs-lookup"><span data-stu-id="1a8b2-144">UI Automation Support for the Tab Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-tab-control-type.md)  
  
-   [<span data-ttu-id="1a8b2-145">TabItem denetim türü için UI Otomasyon desteği</span><span class="sxs-lookup"><span data-stu-id="1a8b2-145">UI Automation Support for the TabItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-tabitem-control-type.md)  
  
-   [<span data-ttu-id="1a8b2-146">Tablo denetim türü için UI Otomasyon desteği</span><span class="sxs-lookup"><span data-stu-id="1a8b2-146">UI Automation Support for the Table Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-table-control-type.md)  
  
-   [<span data-ttu-id="1a8b2-147">Metin denetim türü için UI Otomasyon desteği</span><span class="sxs-lookup"><span data-stu-id="1a8b2-147">UI Automation Support for the Text Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-text-control-type.md)  
  
-   [<span data-ttu-id="1a8b2-148">Parmak denetim türü için UI Otomasyon desteği</span><span class="sxs-lookup"><span data-stu-id="1a8b2-148">UI Automation Support for the Thumb Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-thumb-control-type.md)  
  
-   [<span data-ttu-id="1a8b2-149">TitleBar denetim türü için UI Otomasyon desteği</span><span class="sxs-lookup"><span data-stu-id="1a8b2-149">UI Automation Support for the TitleBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-titlebar-control-type.md)  
  
-   [<span data-ttu-id="1a8b2-150">Araç çubuğu denetim türü için UI Otomasyon desteği</span><span class="sxs-lookup"><span data-stu-id="1a8b2-150">UI Automation Support for the ToolBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-toolbar-control-type.md)  
  
-   [<span data-ttu-id="1a8b2-151">ToolTip denetim türü için UI Otomasyon desteği</span><span class="sxs-lookup"><span data-stu-id="1a8b2-151">UI Automation Support for the ToolTip Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-tooltip-control-type.md)  
  
-   [<span data-ttu-id="1a8b2-152">Ağaç denetim türü için UI Otomasyon desteği</span><span class="sxs-lookup"><span data-stu-id="1a8b2-152">UI Automation Support for the Tree Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-tree-control-type.md)  
  
-   [<span data-ttu-id="1a8b2-153">Treeıtem denetim türü için UI Otomasyon desteği</span><span class="sxs-lookup"><span data-stu-id="1a8b2-153">UI Automation Support for the TreeItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-treeitem-control-type.md)  
  
-   [<span data-ttu-id="1a8b2-154">Pencere denetim türü için UI Otomasyon desteği</span><span class="sxs-lookup"><span data-stu-id="1a8b2-154">UI Automation Support for the Window Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-window-control-type.md)  
  
## <a name="see-also"></a><span data-ttu-id="1a8b2-155">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1a8b2-155">See Also</span></span>  
 <xref:System.Windows.Automation.ControlType>
