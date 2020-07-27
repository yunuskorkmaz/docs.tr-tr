---
title: UI Otomasyon Denetim Türlerine Genel Bakış
description: Bir öğenin ne tür bir denetimin temsil ettiğini göstermek için kullanılabilecek iyi bilinen tanımlayıcılar olan UI Otomasyonu Denetim türlerine genel bakış konusunu okuyun.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control types
- control types, UI Automation
ms.assetid: 75159ef8-bd43-4d13-acb7-1f1fe9253160
ms.openlocfilehash: 204e950fca74c4f7bd2c13dc8a8891152954c071
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166140"
---
# <a name="ui-automation-control-types-overview"></a><span data-ttu-id="a6896-103">UI Otomasyon Denetim Türlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a6896-103">UI Automation Control Types Overview</span></span>
> [!NOTE]
> <span data-ttu-id="a6896-104">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> .</span><span class="sxs-lookup"><span data-stu-id="a6896-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="a6896-105">Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="a6896-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]<span data-ttu-id="a6896-106">Denetim türleri, Birleşik giriş kutusu ya da düğme gibi belirli bir öğenin ne tür bir denetimin temsil ettiğini göstermek için kullanılabilen, tanınmış tanımlayıcılardır.</span><span class="sxs-lookup"><span data-stu-id="a6896-106">control types are well-known identifiers that can be used to indicate what kind of control a particular element represents, such as a combo box or a button.</span></span>  
  
 <span data-ttu-id="a6896-107">İyi bilinen bir tanımlayıcıya sahip olmak, yardımcı teknoloji cihazlarının ' de hangi tür denetimlerin kullanılabilir olduğunu [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] ve denetimlerle nasıl etkileşime gireceğini belirlemenizi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="a6896-107">Having a well-known identifier makes it easier for assistive technology devices to determine what types of controls are available in the [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] and how to interact with the controls.</span></span>  
  
<a name="UI_Automation_Control_Type_Requisites"></a>
## <a name="ui-automation-control-type-requisites"></a><span data-ttu-id="a6896-108">UI Otomasyonu Denetim türü gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="a6896-108">UI Automation Control Type Requisites</span></span>  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]<span data-ttu-id="a6896-109">Denetim türleri, sağlayıcıların karşılaması gereken koşullar kümesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a6896-109">control types provide a set of conditions that providers must meet.</span></span> <span data-ttu-id="a6896-110">Bu koşullar karşılandığında denetim, belirli denetim türü adını kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="a6896-110">When these conditions are met, the control can use the specific control type name.</span></span> <span data-ttu-id="a6896-111">Her denetim türü aşağıdakiler için koşullara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="a6896-111">Each control type has conditions for the following:</span></span>  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="a6896-112">Denetim desenleri — hangi denetim desenlerinin desteklenecek, hangi denetim desenlerinin isteğe bağlı olduğu ve hangi denetim desenlerinin denetim tarafından desteklenmemelidir gerekir.</span><span class="sxs-lookup"><span data-stu-id="a6896-112">control patterns—which control patterns must be supported, which control patterns are optional, and which control patterns must not be supported by the control.</span></span>  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="a6896-113">Özellik değerleri — hangi özellik değerlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="a6896-113">property values—which property values are supported.</span></span>  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="a6896-114">ağaç yapısı — [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Denetim için gerekli ağaç yapısı.</span><span class="sxs-lookup"><span data-stu-id="a6896-114">tree structure—the required [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree structure for the control.</span></span>  
  
 <span data-ttu-id="a6896-115">Bir denetim belirli bir denetim türünün koşullarını karşılıyorsa, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> özellik değeri bu denetim türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="a6896-115">When a control meets the conditions for a particular control type, the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> property value will indicate that control type.</span></span>  
  
<a name="Current_UI_Automation_Control_Types"></a>
## <a name="current-ui-automation-control-types"></a><span data-ttu-id="a6896-116">Geçerli UI Otomasyon Denetim türleri</span><span class="sxs-lookup"><span data-stu-id="a6896-116">Current UI Automation Control Types</span></span>  
 <span data-ttu-id="a6896-117">Aşağıdaki liste geçerli [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] Denetim türleri kümesini içerir:</span><span class="sxs-lookup"><span data-stu-id="a6896-117">The following list contains the current set of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] control types:</span></span>  
  
- [<span data-ttu-id="a6896-118">Düğme Denetim Türü İçin UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="a6896-118">UI Automation Support for the Button Control Type</span></span>](ui-automation-support-for-the-button-control-type.md)  
  
- [<span data-ttu-id="a6896-119">Takvim Denetim Türü İçin UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="a6896-119">UI Automation Support for the Calendar Control Type</span></span>](ui-automation-support-for-the-calendar-control-type.md)  
  
- [<span data-ttu-id="a6896-120">CheckBox Denetim Türü için UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="a6896-120">UI Automation Support for the CheckBox Control Type</span></span>](ui-automation-support-for-the-checkbox-control-type.md)  
  
- [<span data-ttu-id="a6896-121">ComboBox Denetim Türü için UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="a6896-121">UI Automation Support for the ComboBox Control Type</span></span>](ui-automation-support-for-the-combobox-control-type.md)  
  
- [<span data-ttu-id="a6896-122">DataGrid Denetim Türü için UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="a6896-122">UI Automation Support for the DataGrid Control Type</span></span>](ui-automation-support-for-the-datagrid-control-type.md)  
  
- [<span data-ttu-id="a6896-123">DataItem Denetim Türü için UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="a6896-123">UI Automation Support for the DataItem Control Type</span></span>](ui-automation-support-for-the-dataitem-control-type.md)  
  
- [<span data-ttu-id="a6896-124">Belge Denetim Türü İçin UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="a6896-124">UI Automation Support for the Document Control Type</span></span>](ui-automation-support-for-the-document-control-type.md)  
  
- [<span data-ttu-id="a6896-125">Düzenleme Denetim Türü İçin UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="a6896-125">UI Automation Support for the Edit Control Type</span></span>](ui-automation-support-for-the-edit-control-type.md)  
  
- [<span data-ttu-id="a6896-126">Grup Denetim Türü İçin UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="a6896-126">UI Automation Support for the Group Control Type</span></span>](ui-automation-support-for-the-group-control-type.md)  
  
- [<span data-ttu-id="a6896-127">Başlık Denetim Türü İçin UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="a6896-127">UI Automation Support for the Header Control Type</span></span>](ui-automation-support-for-the-header-control-type.md)  
  
- [<span data-ttu-id="a6896-128">HeaderItem Denetim Türü için UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="a6896-128">UI Automation Support for the HeaderItem Control Type</span></span>](ui-automation-support-for-the-headeritem-control-type.md)  
  
- [<span data-ttu-id="a6896-129">Köprü Denetim Türü İçin UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="a6896-129">UI Automation Support for the Hyperlink Control Type</span></span>](ui-automation-support-for-the-hyperlink-control-type.md)  
  
- [<span data-ttu-id="a6896-130">Görüntü Denetim Türü İçin UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="a6896-130">UI Automation Support for the Image Control Type</span></span>](ui-automation-support-for-the-image-control-type.md)  
  
- [<span data-ttu-id="a6896-131">Liste Denetim Türü İçin UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="a6896-131">UI Automation Support for the List Control Type</span></span>](ui-automation-support-for-the-list-control-type.md)  
  
- [<span data-ttu-id="a6896-132">ListItem Denetim Türü için UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="a6896-132">UI Automation Support for the ListItem Control Type</span></span>](ui-automation-support-for-the-listitem-control-type.md)  
  
- [<span data-ttu-id="a6896-133">Menü Denetim Türü İçin UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="a6896-133">UI Automation Support for the Menu Control Type</span></span>](ui-automation-support-for-the-menu-control-type.md)  
  
- [<span data-ttu-id="a6896-134">MenuBar Denetim Türü için UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="a6896-134">UI Automation Support for the MenuBar Control Type</span></span>](ui-automation-support-for-the-menubar-control-type.md)  
  
- [<span data-ttu-id="a6896-135">MenuItem Denetim Türü için UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="a6896-135">UI Automation Support for the MenuItem Control Type</span></span>](ui-automation-support-for-the-menuitem-control-type.md)  
  
- [<span data-ttu-id="a6896-136">Bölme Denetim Türü İçin UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="a6896-136">UI Automation Support for the Pane Control Type</span></span>](ui-automation-support-for-the-pane-control-type.md)  
  
- [<span data-ttu-id="a6896-137">ProgressBar Denetim Türü için UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="a6896-137">UI Automation Support for the ProgressBar Control Type</span></span>](ui-automation-support-for-the-progressbar-control-type.md)  
  
- [<span data-ttu-id="a6896-138">RadioButton Denetim Türü için UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="a6896-138">UI Automation Support for the RadioButton Control Type</span></span>](ui-automation-support-for-the-radiobutton-control-type.md)  
  
- [<span data-ttu-id="a6896-139">ScrollBar Denetim Türü için UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="a6896-139">UI Automation Support for the ScrollBar Control Type</span></span>](ui-automation-support-for-the-scrollbar-control-type.md)  
  
- [<span data-ttu-id="a6896-140">Ayırıcı Denetim Türü İçin UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="a6896-140">UI Automation Support for the Separator Control Type</span></span>](ui-automation-support-for-the-separator-control-type.md)  
  
- [<span data-ttu-id="a6896-141">Kaydırıcı Denetim Türü İçin UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="a6896-141">UI Automation Support for the Slider Control Type</span></span>](ui-automation-support-for-the-slider-control-type.md)  
  
- [<span data-ttu-id="a6896-142">Değer Değiştirici Denetim Türü İçin UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="a6896-142">UI Automation Support for the Spinner Control Type</span></span>](ui-automation-support-for-the-spinner-control-type.md)  
  
- [<span data-ttu-id="a6896-143">SplitButton Denetim Türü için UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="a6896-143">UI Automation Support for the SplitButton Control Type</span></span>](ui-automation-support-for-the-splitbutton-control-type.md)  
  
- [<span data-ttu-id="a6896-144">StatusBar Denetim Türü için UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="a6896-144">UI Automation Support for the StatusBar Control Type</span></span>](ui-automation-support-for-the-statusbar-control-type.md)  
  
- [<span data-ttu-id="a6896-145">Sekme Denetim Türü İçin UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="a6896-145">UI Automation Support for the Tab Control Type</span></span>](ui-automation-support-for-the-tab-control-type.md)  
  
- [<span data-ttu-id="a6896-146">TabItem Denetim Türü için UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="a6896-146">UI Automation Support for the TabItem Control Type</span></span>](ui-automation-support-for-the-tabitem-control-type.md)  
  
- [<span data-ttu-id="a6896-147">Tablo Denetim Türü İçin UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="a6896-147">UI Automation Support for the Table Control Type</span></span>](ui-automation-support-for-the-table-control-type.md)  
  
- [<span data-ttu-id="a6896-148">Metin Denetim Türü İçin UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="a6896-148">UI Automation Support for the Text Control Type</span></span>](ui-automation-support-for-the-text-control-type.md)  
  
- [<span data-ttu-id="a6896-149">Parmak Denetim Türü İçin UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="a6896-149">UI Automation Support for the Thumb Control Type</span></span>](ui-automation-support-for-the-thumb-control-type.md)  
  
- [<span data-ttu-id="a6896-150">TitleBar Denetim Türü için UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="a6896-150">UI Automation Support for the TitleBar Control Type</span></span>](ui-automation-support-for-the-titlebar-control-type.md)  
  
- [<span data-ttu-id="a6896-151">ToolBar Denetim Türü için UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="a6896-151">UI Automation Support for the ToolBar Control Type</span></span>](ui-automation-support-for-the-toolbar-control-type.md)  
  
- [<span data-ttu-id="a6896-152">ToolTip Denetim Türü için UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="a6896-152">UI Automation Support for the ToolTip Control Type</span></span>](ui-automation-support-for-the-tooltip-control-type.md)  
  
- [<span data-ttu-id="a6896-153">Ağaç Denetim Türü İçin UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="a6896-153">UI Automation Support for the Tree Control Type</span></span>](ui-automation-support-for-the-tree-control-type.md)  
  
- [<span data-ttu-id="a6896-154">TreeItem Denetim Türü için UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="a6896-154">UI Automation Support for the TreeItem Control Type</span></span>](ui-automation-support-for-the-treeitem-control-type.md)  
  
- [<span data-ttu-id="a6896-155">Pencere Denetim Türü İçin UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="a6896-155">UI Automation Support for the Window Control Type</span></span>](ui-automation-support-for-the-window-control-type.md)  
  
## <a name="see-also"></a><span data-ttu-id="a6896-156">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6896-156">See also</span></span>

- <xref:System.Windows.Automation.ControlType>
