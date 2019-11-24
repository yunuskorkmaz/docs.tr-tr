---
title: Standart Denetimler İçin UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: c59352f908c5f4a1fd2ca6dd631d26bb5d69f09a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441216"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="7bc58-102">Standart Denetimler İçin UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="7bc58-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
> <span data-ttu-id="7bc58-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span><span class="sxs-lookup"><span data-stu-id="7bc58-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="7bc58-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="7bc58-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="7bc58-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span><span class="sxs-lookup"><span data-stu-id="7bc58-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="7bc58-106">Windows Presentation Foundation Controls</span><span class="sxs-lookup"><span data-stu-id="7bc58-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="7bc58-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7bc58-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="7bc58-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7bc58-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="7bc58-109">Win32 Controls</span><span class="sxs-lookup"><span data-stu-id="7bc58-109">Win32 Controls</span></span>  
 <span data-ttu-id="7bc58-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="7bc58-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="7bc58-111">This assembly is automatically registered for use with UI Automation client applications.</span><span class="sxs-lookup"><span data-stu-id="7bc58-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="7bc58-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span><span class="sxs-lookup"><span data-stu-id="7bc58-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span></span>  
  
 <span data-ttu-id="7bc58-113">The following controls are supported.</span><span class="sxs-lookup"><span data-stu-id="7bc58-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="7bc58-114">Sınıf adı</span><span class="sxs-lookup"><span data-stu-id="7bc58-114">Class name</span></span>|<span data-ttu-id="7bc58-115">Control Type</span><span class="sxs-lookup"><span data-stu-id="7bc58-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="7bc58-116">Düğme</span><span class="sxs-lookup"><span data-stu-id="7bc58-116">Button</span></span>|<span data-ttu-id="7bc58-117">Düğme</span><span class="sxs-lookup"><span data-stu-id="7bc58-117">Button</span></span>|  
|<span data-ttu-id="7bc58-118">Düğme</span><span class="sxs-lookup"><span data-stu-id="7bc58-118">Button</span></span>|<span data-ttu-id="7bc58-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="7bc58-119">RadioButton</span></span>|  
|<span data-ttu-id="7bc58-120">Düğme</span><span class="sxs-lookup"><span data-stu-id="7bc58-120">Button</span></span>|<span data-ttu-id="7bc58-121">Grup</span><span class="sxs-lookup"><span data-stu-id="7bc58-121">Group</span></span>|  
|<span data-ttu-id="7bc58-122">Düğme</span><span class="sxs-lookup"><span data-stu-id="7bc58-122">Button</span></span>|<span data-ttu-id="7bc58-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="7bc58-123">CheckBox</span></span>|  
|<span data-ttu-id="7bc58-124">Düğme</span><span class="sxs-lookup"><span data-stu-id="7bc58-124">Button</span></span>|<span data-ttu-id="7bc58-125">Köprü</span><span class="sxs-lookup"><span data-stu-id="7bc58-125">Hyperlink</span></span>|  
|<span data-ttu-id="7bc58-126">Düğme</span><span class="sxs-lookup"><span data-stu-id="7bc58-126">Button</span></span>|<span data-ttu-id="7bc58-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="7bc58-127">SplitButton</span></span>|  
|<span data-ttu-id="7bc58-128">Düğme</span><span class="sxs-lookup"><span data-stu-id="7bc58-128">Button</span></span>|<span data-ttu-id="7bc58-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="7bc58-129">CheckBox</span></span>|  
|<span data-ttu-id="7bc58-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="7bc58-130">ComboBoxEx32</span></span>|<span data-ttu-id="7bc58-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="7bc58-131">ComboBox</span></span>|  
|<span data-ttu-id="7bc58-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="7bc58-132">ComboBox</span></span>|<span data-ttu-id="7bc58-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="7bc58-133">ComboBox</span></span>|  
|<span data-ttu-id="7bc58-134">Düzenle</span><span class="sxs-lookup"><span data-stu-id="7bc58-134">Edit</span></span>|<span data-ttu-id="7bc58-135">Belge</span><span class="sxs-lookup"><span data-stu-id="7bc58-135">Document</span></span>|  
|<span data-ttu-id="7bc58-136">Düzenle</span><span class="sxs-lookup"><span data-stu-id="7bc58-136">Edit</span></span>|<span data-ttu-id="7bc58-137">Düzenle</span><span class="sxs-lookup"><span data-stu-id="7bc58-137">Edit</span></span>|  
|<span data-ttu-id="7bc58-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="7bc58-138">SysLink</span></span>|<span data-ttu-id="7bc58-139">Köprü</span><span class="sxs-lookup"><span data-stu-id="7bc58-139">Hyperlink</span></span>|  
|<span data-ttu-id="7bc58-140">Statik</span><span class="sxs-lookup"><span data-stu-id="7bc58-140">Static</span></span>|<span data-ttu-id="7bc58-141">Metin</span><span class="sxs-lookup"><span data-stu-id="7bc58-141">Text</span></span>|  
|<span data-ttu-id="7bc58-142">Statik</span><span class="sxs-lookup"><span data-stu-id="7bc58-142">Static</span></span>|<span data-ttu-id="7bc58-143">Görüntü</span><span class="sxs-lookup"><span data-stu-id="7bc58-143">Image</span></span>|  
|<span data-ttu-id="7bc58-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="7bc58-144">SysIPAddress32</span></span>|<span data-ttu-id="7bc58-145">Özel</span><span class="sxs-lookup"><span data-stu-id="7bc58-145">Custom</span></span>|  
|<span data-ttu-id="7bc58-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="7bc58-146">SysHeader32</span></span>|<span data-ttu-id="7bc58-147">Header/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="7bc58-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="7bc58-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="7bc58-148">SysListView32</span></span>|<span data-ttu-id="7bc58-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="7bc58-149">DataGrid</span></span>|  
|<span data-ttu-id="7bc58-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="7bc58-150">SysListView32</span></span>|<span data-ttu-id="7bc58-151">List</span><span class="sxs-lookup"><span data-stu-id="7bc58-151">List</span></span>|  
|<span data-ttu-id="7bc58-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="7bc58-152">ListBox</span></span>|<span data-ttu-id="7bc58-153">List</span><span class="sxs-lookup"><span data-stu-id="7bc58-153">List</span></span>|  
|<span data-ttu-id="7bc58-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="7bc58-154">ListBox</span></span>|<span data-ttu-id="7bc58-155">ListItem</span><span class="sxs-lookup"><span data-stu-id="7bc58-155">ListItem</span></span>|  
|<span data-ttu-id="7bc58-156">#32768</span><span class="sxs-lookup"><span data-stu-id="7bc58-156">#32768</span></span>|<span data-ttu-id="7bc58-157">Menü</span><span class="sxs-lookup"><span data-stu-id="7bc58-157">Menu</span></span>|  
|<span data-ttu-id="7bc58-158">#32768</span><span class="sxs-lookup"><span data-stu-id="7bc58-158">#32768</span></span>|<span data-ttu-id="7bc58-159">MenuItem</span><span class="sxs-lookup"><span data-stu-id="7bc58-159">MenuItem</span></span>|  
|<span data-ttu-id="7bc58-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="7bc58-160">msctls_progress32</span></span>|<span data-ttu-id="7bc58-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="7bc58-161">ProgressBar</span></span>|  
|<span data-ttu-id="7bc58-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="7bc58-162">RichEdit</span></span>|<span data-ttu-id="7bc58-163">Document.</span><span class="sxs-lookup"><span data-stu-id="7bc58-163">Document.</span></span> <span data-ttu-id="7bc58-164">See note.</span><span class="sxs-lookup"><span data-stu-id="7bc58-164">See note.</span></span>|  
|<span data-ttu-id="7bc58-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="7bc58-165">RichEdit20A</span></span>|<span data-ttu-id="7bc58-166">Belge</span><span class="sxs-lookup"><span data-stu-id="7bc58-166">Document</span></span>|  
|<span data-ttu-id="7bc58-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="7bc58-167">RichEdit20W</span></span>|<span data-ttu-id="7bc58-168">Belge</span><span class="sxs-lookup"><span data-stu-id="7bc58-168">Document</span></span>|  
|<span data-ttu-id="7bc58-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="7bc58-169">RichEdit50W</span></span>|<span data-ttu-id="7bc58-170">Belge</span><span class="sxs-lookup"><span data-stu-id="7bc58-170">Document</span></span>|  
|<span data-ttu-id="7bc58-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="7bc58-171">ScrollBar</span></span>|<span data-ttu-id="7bc58-172">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="7bc58-172">Slider</span></span>|  
|<span data-ttu-id="7bc58-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="7bc58-173">msctls_trackbar32</span></span>|<span data-ttu-id="7bc58-174">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="7bc58-174">Slider</span></span>|  
|<span data-ttu-id="7bc58-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="7bc58-175">msctls_updown32</span></span>|<span data-ttu-id="7bc58-176">Değer Değiştirici</span><span class="sxs-lookup"><span data-stu-id="7bc58-176">Spinner</span></span>|  
|<span data-ttu-id="7bc58-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="7bc58-177">msctls_statusbar32</span></span>|<span data-ttu-id="7bc58-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="7bc58-178">StatusBar</span></span>|  
|<span data-ttu-id="7bc58-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="7bc58-179">SysTabControl32</span></span>|<span data-ttu-id="7bc58-180">Tab</span><span class="sxs-lookup"><span data-stu-id="7bc58-180">Tab</span></span>|  
|<span data-ttu-id="7bc58-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="7bc58-181">SysTabControl32</span></span>|<span data-ttu-id="7bc58-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="7bc58-182">TabItem</span></span>|  
|<span data-ttu-id="7bc58-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="7bc58-183">ToolbarWindow32</span></span>|<span data-ttu-id="7bc58-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="7bc58-184">ToolBar</span></span>|  
|<span data-ttu-id="7bc58-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="7bc58-185">ToolbarWindow32</span></span>|<span data-ttu-id="7bc58-186">MenuItem</span><span class="sxs-lookup"><span data-stu-id="7bc58-186">MenuItem</span></span>|  
|<span data-ttu-id="7bc58-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="7bc58-187">ToolbarWindow32</span></span>|<span data-ttu-id="7bc58-188">Düğme</span><span class="sxs-lookup"><span data-stu-id="7bc58-188">Button</span></span>|  
|<span data-ttu-id="7bc58-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="7bc58-189">ToolbarWindow32</span></span>|<span data-ttu-id="7bc58-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="7bc58-190">CheckBox</span></span>|  
|<span data-ttu-id="7bc58-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="7bc58-191">ToolbarWindow32</span></span>|<span data-ttu-id="7bc58-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="7bc58-192">RadioButton</span></span>|  
|<span data-ttu-id="7bc58-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="7bc58-193">ToolbarWindow32</span></span>|<span data-ttu-id="7bc58-194">Ayırıcı</span><span class="sxs-lookup"><span data-stu-id="7bc58-194">Separator</span></span>|  
|<span data-ttu-id="7bc58-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="7bc58-195">tooltips_class32</span></span>|<span data-ttu-id="7bc58-196">ToolTip</span><span class="sxs-lookup"><span data-stu-id="7bc58-196">ToolTip</span></span>|  
|<span data-ttu-id="7bc58-197">#32774</span><span class="sxs-lookup"><span data-stu-id="7bc58-197">#32774</span></span>|<span data-ttu-id="7bc58-198">ToolTip</span><span class="sxs-lookup"><span data-stu-id="7bc58-198">ToolTip</span></span>|  
|<span data-ttu-id="7bc58-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="7bc58-199">ReBarWindow32</span></span>|<span data-ttu-id="7bc58-200">Araç Çubuğu</span><span class="sxs-lookup"><span data-stu-id="7bc58-200">Toolbar</span></span>|  
|<span data-ttu-id="7bc58-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="7bc58-201">SysTreeView32</span></span>|<span data-ttu-id="7bc58-202">Ağaç</span><span class="sxs-lookup"><span data-stu-id="7bc58-202">Tree</span></span>|  
|<span data-ttu-id="7bc58-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="7bc58-203">SysTreeView32</span></span>|<span data-ttu-id="7bc58-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="7bc58-204">TreeItem</span></span>|  
  
 <span data-ttu-id="7bc58-205">**Note** The RichEdit control is supported only for versions shipped with Windows Vista (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span><span class="sxs-lookup"><span data-stu-id="7bc58-205">**Note** The RichEdit control is supported only for versions shipped with Windows Vista (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="7bc58-206">The following controls are not supported.</span><span class="sxs-lookup"><span data-stu-id="7bc58-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="7bc58-207">Sınıf adı</span><span class="sxs-lookup"><span data-stu-id="7bc58-207">Class name</span></span>|<span data-ttu-id="7bc58-208">Control type</span><span class="sxs-lookup"><span data-stu-id="7bc58-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="7bc58-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="7bc58-209">SysAnimate32</span></span>|<span data-ttu-id="7bc58-210">Görüntü</span><span class="sxs-lookup"><span data-stu-id="7bc58-210">Image</span></span>|  
|<span data-ttu-id="7bc58-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="7bc58-211">SysPager</span></span>|<span data-ttu-id="7bc58-212">Değer Değiştirici</span><span class="sxs-lookup"><span data-stu-id="7bc58-212">Spinner</span></span>|  
|<span data-ttu-id="7bc58-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="7bc58-213">SysDateTimePick32</span></span>|<span data-ttu-id="7bc58-214">Özel</span><span class="sxs-lookup"><span data-stu-id="7bc58-214">Custom</span></span>|  
|<span data-ttu-id="7bc58-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="7bc58-215">SysMonthCal32</span></span>|<span data-ttu-id="7bc58-216">Takvim</span><span class="sxs-lookup"><span data-stu-id="7bc58-216">Calendar</span></span>|  
|<span data-ttu-id="7bc58-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="7bc58-217">MS_WINNOTE</span></span>|<span data-ttu-id="7bc58-218">Tooltip</span><span class="sxs-lookup"><span data-stu-id="7bc58-218">Tooltip</span></span>|  
|<span data-ttu-id="7bc58-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="7bc58-219">VBBubble</span></span>|<span data-ttu-id="7bc58-220">Tooltip</span><span class="sxs-lookup"><span data-stu-id="7bc58-220">Tooltip</span></span>|  
|<span data-ttu-id="7bc58-221">ScrollBar (when used as a standalone control)</span><span class="sxs-lookup"><span data-stu-id="7bc58-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="7bc58-222">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="7bc58-222">Slider</span></span>|  
|<span data-ttu-id="7bc58-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="7bc58-223">SuperGrid</span></span>|<span data-ttu-id="7bc58-224">Özel</span><span class="sxs-lookup"><span data-stu-id="7bc58-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="7bc58-225">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="7bc58-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="7bc58-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span><span class="sxs-lookup"><span data-stu-id="7bc58-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="7bc58-227">This assembly is automatically registered for use with UI Automation client applications.</span><span class="sxs-lookup"><span data-stu-id="7bc58-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="7bc58-228">Typically, Windows Forms controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7bc58-228">Typically, Windows Forms controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="7bc58-229">The following controls are supported.</span><span class="sxs-lookup"><span data-stu-id="7bc58-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="7bc58-230">Sınıf Adı</span><span class="sxs-lookup"><span data-stu-id="7bc58-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="7bc58-231">Düğme</span><span class="sxs-lookup"><span data-stu-id="7bc58-231">Button</span></span>|  
|<span data-ttu-id="7bc58-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="7bc58-232">CheckBox</span></span>|  
|<span data-ttu-id="7bc58-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="7bc58-233">CheckedListBox</span></span>|  
|<span data-ttu-id="7bc58-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="7bc58-234">ColorDialog</span></span>|  
|<span data-ttu-id="7bc58-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="7bc58-235">ComboBox</span></span>|  
|<span data-ttu-id="7bc58-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="7bc58-236">FolderBrowser</span></span>|  
|<span data-ttu-id="7bc58-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="7bc58-237">FontDialog</span></span>|  
|<span data-ttu-id="7bc58-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="7bc58-238">GroupBox</span></span>|  
|<span data-ttu-id="7bc58-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="7bc58-239">HscrollBar</span></span>|  
|<span data-ttu-id="7bc58-240">ImageList</span><span class="sxs-lookup"><span data-stu-id="7bc58-240">ImageList</span></span>|  
|<span data-ttu-id="7bc58-241">Etiketle</span><span class="sxs-lookup"><span data-stu-id="7bc58-241">Label</span></span>|  
|<span data-ttu-id="7bc58-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="7bc58-242">ListBox</span></span>|  
|<span data-ttu-id="7bc58-243">ListView</span><span class="sxs-lookup"><span data-stu-id="7bc58-243">ListView</span></span>|  
|<span data-ttu-id="7bc58-244">MainMenu/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="7bc58-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="7bc58-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="7bc58-245">MonthCalendar</span></span>|  
|<span data-ttu-id="7bc58-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="7bc58-246">NotifyIcon</span></span>|  
|<span data-ttu-id="7bc58-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="7bc58-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="7bc58-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="7bc58-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="7bc58-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="7bc58-249">PrintDialog</span></span>|  
|<span data-ttu-id="7bc58-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="7bc58-250">ProgressBar</span></span>|  
|<span data-ttu-id="7bc58-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="7bc58-251">RadioButton</span></span>|  
|<span data-ttu-id="7bc58-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="7bc58-252">RichTextBox</span></span>|  
|<span data-ttu-id="7bc58-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="7bc58-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="7bc58-254">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="7bc58-254">ScrollableControl</span></span>|  
|<span data-ttu-id="7bc58-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="7bc58-255">SoundPlayer</span></span>|  
|<span data-ttu-id="7bc58-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="7bc58-256">StatusBar</span></span>|  
|<span data-ttu-id="7bc58-257">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="7bc58-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="7bc58-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="7bc58-258">TextBox</span></span>|  
|<span data-ttu-id="7bc58-259">Zamanlayıcı</span><span class="sxs-lookup"><span data-stu-id="7bc58-259">Timer</span></span>|  
|<span data-ttu-id="7bc58-260">Araç Çubuğu</span><span class="sxs-lookup"><span data-stu-id="7bc58-260">Toolbar</span></span>|  
|<span data-ttu-id="7bc58-261">ToolTip</span><span class="sxs-lookup"><span data-stu-id="7bc58-261">ToolTip</span></span>|  
|<span data-ttu-id="7bc58-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="7bc58-262">TrackBar</span></span>|  
|<span data-ttu-id="7bc58-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="7bc58-263">TreeView</span></span>|  
|<span data-ttu-id="7bc58-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="7bc58-264">VscrollBar</span></span>|  
|<span data-ttu-id="7bc58-265">WebBrowser</span><span class="sxs-lookup"><span data-stu-id="7bc58-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="7bc58-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for Microsoft Active Accessibility.</span><span class="sxs-lookup"><span data-stu-id="7bc58-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for Microsoft Active Accessibility.</span></span> <span data-ttu-id="7bc58-267">Some functionality may not be available.</span><span class="sxs-lookup"><span data-stu-id="7bc58-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="7bc58-268">Control Name</span><span class="sxs-lookup"><span data-stu-id="7bc58-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="7bc58-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="7bc58-269">BindingSource</span></span>|  
|<span data-ttu-id="7bc58-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="7bc58-270">DataGrid</span></span>|  
|<span data-ttu-id="7bc58-271">DataGridView</span><span class="sxs-lookup"><span data-stu-id="7bc58-271">DataGridView</span></span>|  
|<span data-ttu-id="7bc58-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="7bc58-272">DataNavigator</span></span>|  
|<span data-ttu-id="7bc58-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="7bc58-273">DomainUpDown</span></span>|  
|<span data-ttu-id="7bc58-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="7bc58-274">ErrorProvider</span></span>|  
|<span data-ttu-id="7bc58-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="7bc58-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="7bc58-276">Form</span><span class="sxs-lookup"><span data-stu-id="7bc58-276">Form</span></span>|  
|<span data-ttu-id="7bc58-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="7bc58-277">LinkLabel</span></span>|  
|<span data-ttu-id="7bc58-278">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="7bc58-278">HelpProvider</span></span>|  
|<span data-ttu-id="7bc58-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="7bc58-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="7bc58-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="7bc58-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="7bc58-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="7bc58-281">NumericUpDown</span></span>|  
|<span data-ttu-id="7bc58-282">Panel</span><span class="sxs-lookup"><span data-stu-id="7bc58-282">Panel</span></span>|  
|<span data-ttu-id="7bc58-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="7bc58-283">PictureBox</span></span>|  
|<span data-ttu-id="7bc58-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="7bc58-284">PrintDocument</span></span>|  
|<span data-ttu-id="7bc58-285">PrintPreview-Control</span><span class="sxs-lookup"><span data-stu-id="7bc58-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="7bc58-286">PrintPreview-Dialog</span><span class="sxs-lookup"><span data-stu-id="7bc58-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="7bc58-287">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="7bc58-287">PropertyGrid</span></span>|  
|<span data-ttu-id="7bc58-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="7bc58-288">UserControl</span></span>|  
|<span data-ttu-id="7bc58-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="7bc58-289">ToolStrip</span></span>|  
|<span data-ttu-id="7bc58-290">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="7bc58-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="7bc58-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="7bc58-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="7bc58-292">Splitter</span><span class="sxs-lookup"><span data-stu-id="7bc58-292">Splitter</span></span>|  
|<span data-ttu-id="7bc58-293">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="7bc58-293">RaftingContainer</span></span>|  
|<span data-ttu-id="7bc58-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="7bc58-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7bc58-295">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7bc58-295">See also</span></span>

- [<span data-ttu-id="7bc58-296">UI Otomasyonu Denetim Türleri</span><span class="sxs-lookup"><span data-stu-id="7bc58-296">UI Automation Control Types</span></span>](ui-automation-control-types.md)
