---
title: Standart Denetimler İçin UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: cbfb640a068a2c1178d321480ee3a112db07b6ac
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43463898"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="bb197-102">Standart Denetimler İçin UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="bb197-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
>  <span data-ttu-id="bb197-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="bb197-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="bb197-104">En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="bb197-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="bb197-105">Bu konu hakkında bilgiler içerir. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] desteklemek için geliştirilen uygulamalarda standart denetimler için [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], ve [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] çerçeveleri.</span><span class="sxs-lookup"><span data-stu-id="bb197-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="bb197-106">Windows Presentation Foundation denetimleri</span><span class="sxs-lookup"><span data-stu-id="bb197-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="bb197-107">Tüm [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] bilgi veya destek için kullanıcı etkileşimi sağlayan denetim öğeleri tam yerel desteği olan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bb197-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="bb197-108">Panel gibi diğer öğeler için görünür değildir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bb197-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="bb197-109">Win32 denetimleri</span><span class="sxs-lookup"><span data-stu-id="bb197-109">Win32 Controls</span></span>  
 <span data-ttu-id="bb197-110">Çoğu [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] denetimleri için sunulur [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] UIAutomationClientsideProviders.dll istemci-tarafı sağlayıcıları aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="bb197-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="bb197-111">Bu derleme için UI otomasyon istemci uygulamaları ile kullanmak üzere otomatik olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="bb197-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="bb197-112">Yalnızca 6 sürümünden ComCtrl32.dll denetimleri için tam destek sağlanır (bulunan [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] ve üzeri).</span><span class="sxs-lookup"><span data-stu-id="bb197-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span></span>  
  
 <span data-ttu-id="bb197-113">Aşağıdaki denetimleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="bb197-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="bb197-114">Sınıf adı</span><span class="sxs-lookup"><span data-stu-id="bb197-114">Class name</span></span>|<span data-ttu-id="bb197-115">Denetim türü</span><span class="sxs-lookup"><span data-stu-id="bb197-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="bb197-116">Düğme</span><span class="sxs-lookup"><span data-stu-id="bb197-116">Button</span></span>|<span data-ttu-id="bb197-117">Düğme</span><span class="sxs-lookup"><span data-stu-id="bb197-117">Button</span></span>|  
|<span data-ttu-id="bb197-118">Düğme</span><span class="sxs-lookup"><span data-stu-id="bb197-118">Button</span></span>|<span data-ttu-id="bb197-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="bb197-119">RadioButton</span></span>|  
|<span data-ttu-id="bb197-120">Düğme</span><span class="sxs-lookup"><span data-stu-id="bb197-120">Button</span></span>|<span data-ttu-id="bb197-121">Grup</span><span class="sxs-lookup"><span data-stu-id="bb197-121">Group</span></span>|  
|<span data-ttu-id="bb197-122">Düğme</span><span class="sxs-lookup"><span data-stu-id="bb197-122">Button</span></span>|<span data-ttu-id="bb197-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="bb197-123">CheckBox</span></span>|  
|<span data-ttu-id="bb197-124">Düğme</span><span class="sxs-lookup"><span data-stu-id="bb197-124">Button</span></span>|<span data-ttu-id="bb197-125">Köprü</span><span class="sxs-lookup"><span data-stu-id="bb197-125">Hyperlink</span></span>|  
|<span data-ttu-id="bb197-126">Düğme</span><span class="sxs-lookup"><span data-stu-id="bb197-126">Button</span></span>|<span data-ttu-id="bb197-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="bb197-127">SplitButton</span></span>|  
|<span data-ttu-id="bb197-128">Düğme</span><span class="sxs-lookup"><span data-stu-id="bb197-128">Button</span></span>|<span data-ttu-id="bb197-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="bb197-129">CheckBox</span></span>|  
|<span data-ttu-id="bb197-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="bb197-130">ComboBoxEx32</span></span>|<span data-ttu-id="bb197-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="bb197-131">ComboBox</span></span>|  
|<span data-ttu-id="bb197-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="bb197-132">ComboBox</span></span>|<span data-ttu-id="bb197-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="bb197-133">ComboBox</span></span>|  
|<span data-ttu-id="bb197-134">Düzenle</span><span class="sxs-lookup"><span data-stu-id="bb197-134">Edit</span></span>|<span data-ttu-id="bb197-135">Belge</span><span class="sxs-lookup"><span data-stu-id="bb197-135">Document</span></span>|  
|<span data-ttu-id="bb197-136">Düzenle</span><span class="sxs-lookup"><span data-stu-id="bb197-136">Edit</span></span>|<span data-ttu-id="bb197-137">Düzenle</span><span class="sxs-lookup"><span data-stu-id="bb197-137">Edit</span></span>|  
|<span data-ttu-id="bb197-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="bb197-138">SysLink</span></span>|<span data-ttu-id="bb197-139">Köprü</span><span class="sxs-lookup"><span data-stu-id="bb197-139">Hyperlink</span></span>|  
|<span data-ttu-id="bb197-140">Statik</span><span class="sxs-lookup"><span data-stu-id="bb197-140">Static</span></span>|<span data-ttu-id="bb197-141">Metin</span><span class="sxs-lookup"><span data-stu-id="bb197-141">Text</span></span>|  
|<span data-ttu-id="bb197-142">Statik</span><span class="sxs-lookup"><span data-stu-id="bb197-142">Static</span></span>|<span data-ttu-id="bb197-143">Görüntü</span><span class="sxs-lookup"><span data-stu-id="bb197-143">Image</span></span>|  
|<span data-ttu-id="bb197-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="bb197-144">SysIPAddress32</span></span>|<span data-ttu-id="bb197-145">Özel</span><span class="sxs-lookup"><span data-stu-id="bb197-145">Custom</span></span>|  
|<span data-ttu-id="bb197-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="bb197-146">SysHeader32</span></span>|<span data-ttu-id="bb197-147">Üstbilgi/Headerıtem</span><span class="sxs-lookup"><span data-stu-id="bb197-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="bb197-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="bb197-148">SysListView32</span></span>|<span data-ttu-id="bb197-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="bb197-149">DataGrid</span></span>|  
|<span data-ttu-id="bb197-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="bb197-150">SysListView32</span></span>|<span data-ttu-id="bb197-151">List</span><span class="sxs-lookup"><span data-stu-id="bb197-151">List</span></span>|  
|<span data-ttu-id="bb197-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="bb197-152">ListBox</span></span>|<span data-ttu-id="bb197-153">List</span><span class="sxs-lookup"><span data-stu-id="bb197-153">List</span></span>|  
|<span data-ttu-id="bb197-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="bb197-154">ListBox</span></span>|<span data-ttu-id="bb197-155">ListItem</span><span class="sxs-lookup"><span data-stu-id="bb197-155">ListItem</span></span>|  
|<span data-ttu-id="bb197-156">#32768</span><span class="sxs-lookup"><span data-stu-id="bb197-156">#32768</span></span>|<span data-ttu-id="bb197-157">Menü</span><span class="sxs-lookup"><span data-stu-id="bb197-157">Menu</span></span>|  
|<span data-ttu-id="bb197-158">#32768</span><span class="sxs-lookup"><span data-stu-id="bb197-158">#32768</span></span>|<span data-ttu-id="bb197-159">MenuItem</span><span class="sxs-lookup"><span data-stu-id="bb197-159">MenuItem</span></span>|  
|<span data-ttu-id="bb197-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="bb197-160">msctls_progress32</span></span>|<span data-ttu-id="bb197-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="bb197-161">ProgressBar</span></span>|  
|<span data-ttu-id="bb197-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="bb197-162">RichEdit</span></span>|<span data-ttu-id="bb197-163">Belge.</span><span class="sxs-lookup"><span data-stu-id="bb197-163">Document.</span></span> <span data-ttu-id="bb197-164">Nota bakın.</span><span class="sxs-lookup"><span data-stu-id="bb197-164">See note.</span></span>|  
|<span data-ttu-id="bb197-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="bb197-165">RichEdit20A</span></span>|<span data-ttu-id="bb197-166">Belge</span><span class="sxs-lookup"><span data-stu-id="bb197-166">Document</span></span>|  
|<span data-ttu-id="bb197-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="bb197-167">RichEdit20W</span></span>|<span data-ttu-id="bb197-168">Belge</span><span class="sxs-lookup"><span data-stu-id="bb197-168">Document</span></span>|  
|<span data-ttu-id="bb197-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="bb197-169">RichEdit50W</span></span>|<span data-ttu-id="bb197-170">Belge</span><span class="sxs-lookup"><span data-stu-id="bb197-170">Document</span></span>|  
|<span data-ttu-id="bb197-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="bb197-171">ScrollBar</span></span>|<span data-ttu-id="bb197-172">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="bb197-172">Slider</span></span>|  
|<span data-ttu-id="bb197-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="bb197-173">msctls_trackbar32</span></span>|<span data-ttu-id="bb197-174">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="bb197-174">Slider</span></span>|  
|<span data-ttu-id="bb197-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="bb197-175">msctls_updown32</span></span>|<span data-ttu-id="bb197-176">Değer Değiştirici</span><span class="sxs-lookup"><span data-stu-id="bb197-176">Spinner</span></span>|  
|<span data-ttu-id="bb197-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="bb197-177">msctls_statusbar32</span></span>|<span data-ttu-id="bb197-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="bb197-178">StatusBar</span></span>|  
|<span data-ttu-id="bb197-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="bb197-179">SysTabControl32</span></span>|<span data-ttu-id="bb197-180">Tab</span><span class="sxs-lookup"><span data-stu-id="bb197-180">Tab</span></span>|  
|<span data-ttu-id="bb197-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="bb197-181">SysTabControl32</span></span>|<span data-ttu-id="bb197-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="bb197-182">TabItem</span></span>|  
|<span data-ttu-id="bb197-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="bb197-183">ToolbarWindow32</span></span>|<span data-ttu-id="bb197-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="bb197-184">ToolBar</span></span>|  
|<span data-ttu-id="bb197-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="bb197-185">ToolbarWindow32</span></span>|<span data-ttu-id="bb197-186">MenuItem</span><span class="sxs-lookup"><span data-stu-id="bb197-186">MenuItem</span></span>|  
|<span data-ttu-id="bb197-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="bb197-187">ToolbarWindow32</span></span>|<span data-ttu-id="bb197-188">Düğme</span><span class="sxs-lookup"><span data-stu-id="bb197-188">Button</span></span>|  
|<span data-ttu-id="bb197-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="bb197-189">ToolbarWindow32</span></span>|<span data-ttu-id="bb197-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="bb197-190">CheckBox</span></span>|  
|<span data-ttu-id="bb197-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="bb197-191">ToolbarWindow32</span></span>|<span data-ttu-id="bb197-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="bb197-192">RadioButton</span></span>|  
|<span data-ttu-id="bb197-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="bb197-193">ToolbarWindow32</span></span>|<span data-ttu-id="bb197-194">Ayırıcı</span><span class="sxs-lookup"><span data-stu-id="bb197-194">Separator</span></span>|  
|<span data-ttu-id="bb197-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="bb197-195">tooltips_class32</span></span>|<span data-ttu-id="bb197-196">ToolTip</span><span class="sxs-lookup"><span data-stu-id="bb197-196">ToolTip</span></span>|  
|<span data-ttu-id="bb197-197">#32774</span><span class="sxs-lookup"><span data-stu-id="bb197-197">#32774</span></span>|<span data-ttu-id="bb197-198">ToolTip</span><span class="sxs-lookup"><span data-stu-id="bb197-198">ToolTip</span></span>|  
|<span data-ttu-id="bb197-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="bb197-199">ReBarWindow32</span></span>|<span data-ttu-id="bb197-200">Araç Çubuğu</span><span class="sxs-lookup"><span data-stu-id="bb197-200">Toolbar</span></span>|  
|<span data-ttu-id="bb197-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="bb197-201">SysTreeView32</span></span>|<span data-ttu-id="bb197-202">Ağaç</span><span class="sxs-lookup"><span data-stu-id="bb197-202">Tree</span></span>|  
|<span data-ttu-id="bb197-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="bb197-203">SysTreeView32</span></span>|<span data-ttu-id="bb197-204">Treeıtem</span><span class="sxs-lookup"><span data-stu-id="bb197-204">TreeItem</span></span>|  
  
 <span data-ttu-id="bb197-205">**Not** RichEdit denetimini yalnızca sürümleri ile birlikte gelen için desteklenen [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (içinde RichEd20.dll sürüm 3.1 ve üzeri ve MsftEdit.dll sürümü 4.1 ve üzeri).</span><span class="sxs-lookup"><span data-stu-id="bb197-205">**Note** The RichEdit control is supported only for versions shipped with [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="bb197-206">Aşağıdaki denetimleri desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="bb197-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="bb197-207">Sınıf adı</span><span class="sxs-lookup"><span data-stu-id="bb197-207">Class name</span></span>|<span data-ttu-id="bb197-208">Denetim türü</span><span class="sxs-lookup"><span data-stu-id="bb197-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="bb197-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="bb197-209">SysAnimate32</span></span>|<span data-ttu-id="bb197-210">Görüntü</span><span class="sxs-lookup"><span data-stu-id="bb197-210">Image</span></span>|  
|<span data-ttu-id="bb197-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="bb197-211">SysPager</span></span>|<span data-ttu-id="bb197-212">Değer Değiştirici</span><span class="sxs-lookup"><span data-stu-id="bb197-212">Spinner</span></span>|  
|<span data-ttu-id="bb197-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="bb197-213">SysDateTimePick32</span></span>|<span data-ttu-id="bb197-214">Özel</span><span class="sxs-lookup"><span data-stu-id="bb197-214">Custom</span></span>|  
|<span data-ttu-id="bb197-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="bb197-215">SysMonthCal32</span></span>|<span data-ttu-id="bb197-216">Takvim</span><span class="sxs-lookup"><span data-stu-id="bb197-216">Calendar</span></span>|  
|<span data-ttu-id="bb197-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="bb197-217">MS_WINNOTE</span></span>|<span data-ttu-id="bb197-218">Araç İpucu</span><span class="sxs-lookup"><span data-stu-id="bb197-218">Tooltip</span></span>|  
|<span data-ttu-id="bb197-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="bb197-219">VBBubble</span></span>|<span data-ttu-id="bb197-220">Araç İpucu</span><span class="sxs-lookup"><span data-stu-id="bb197-220">Tooltip</span></span>|  
|<span data-ttu-id="bb197-221">(Tek başına denetim olarak kullanıldığında) bir kaydırma çubuğu</span><span class="sxs-lookup"><span data-stu-id="bb197-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="bb197-222">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="bb197-222">Slider</span></span>|  
|<span data-ttu-id="bb197-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="bb197-223">SuperGrid</span></span>|<span data-ttu-id="bb197-224">Özel</span><span class="sxs-lookup"><span data-stu-id="bb197-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="bb197-225">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="bb197-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="bb197-226">Windows Forms denetimleri için sunulur [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] UIAutomationClientsideProviders.dll istemci-tarafı sağlayıcıları aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="bb197-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="bb197-227">Bu derleme için UI otomasyon istemci uygulamaları ile kullanmak üzere otomatik olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="bb197-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="bb197-228">Genellikle, Windows Forms denetimleri yönetilen sarmalayıcıları için [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] tarafından desteklenen ortak denetimleri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bb197-228">Typically, Windows Forms controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="bb197-229">Aşağıdaki denetimleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="bb197-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="bb197-230">Sınıf Adı</span><span class="sxs-lookup"><span data-stu-id="bb197-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="bb197-231">Düğme</span><span class="sxs-lookup"><span data-stu-id="bb197-231">Button</span></span>|  
|<span data-ttu-id="bb197-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="bb197-232">CheckBox</span></span>|  
|<span data-ttu-id="bb197-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="bb197-233">CheckedListBox</span></span>|  
|<span data-ttu-id="bb197-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="bb197-234">ColorDialog</span></span>|  
|<span data-ttu-id="bb197-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="bb197-235">ComboBox</span></span>|  
|<span data-ttu-id="bb197-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="bb197-236">FolderBrowser</span></span>|  
|<span data-ttu-id="bb197-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="bb197-237">FontDialog</span></span>|  
|<span data-ttu-id="bb197-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="bb197-238">GroupBox</span></span>|  
|<span data-ttu-id="bb197-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="bb197-239">HscrollBar</span></span>|  
|<span data-ttu-id="bb197-240">ImageList</span><span class="sxs-lookup"><span data-stu-id="bb197-240">ImageList</span></span>|  
|<span data-ttu-id="bb197-241">Etiketle</span><span class="sxs-lookup"><span data-stu-id="bb197-241">Label</span></span>|  
|<span data-ttu-id="bb197-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="bb197-242">ListBox</span></span>|  
|<span data-ttu-id="bb197-243">ListView</span><span class="sxs-lookup"><span data-stu-id="bb197-243">ListView</span></span>|  
|<span data-ttu-id="bb197-244">MainMenu/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="bb197-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="bb197-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="bb197-245">MonthCalendar</span></span>|  
|<span data-ttu-id="bb197-246">Notifyıcon</span><span class="sxs-lookup"><span data-stu-id="bb197-246">NotifyIcon</span></span>|  
|<span data-ttu-id="bb197-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="bb197-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="bb197-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="bb197-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="bb197-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="bb197-249">PrintDialog</span></span>|  
|<span data-ttu-id="bb197-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="bb197-250">ProgressBar</span></span>|  
|<span data-ttu-id="bb197-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="bb197-251">RadioButton</span></span>|  
|<span data-ttu-id="bb197-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="bb197-252">RichTextBox</span></span>|  
|<span data-ttu-id="bb197-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="bb197-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="bb197-254">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="bb197-254">ScrollableControl</span></span>|  
|<span data-ttu-id="bb197-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="bb197-255">SoundPlayer</span></span>|  
|<span data-ttu-id="bb197-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="bb197-256">StatusBar</span></span>|  
|<span data-ttu-id="bb197-257">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="bb197-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="bb197-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="bb197-258">TextBox</span></span>|  
|<span data-ttu-id="bb197-259">Zamanlayıcı</span><span class="sxs-lookup"><span data-stu-id="bb197-259">Timer</span></span>|  
|<span data-ttu-id="bb197-260">Araç Çubuğu</span><span class="sxs-lookup"><span data-stu-id="bb197-260">Toolbar</span></span>|  
|<span data-ttu-id="bb197-261">ToolTip</span><span class="sxs-lookup"><span data-stu-id="bb197-261">ToolTip</span></span>|  
|<span data-ttu-id="bb197-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="bb197-262">TrackBar</span></span>|  
|<span data-ttu-id="bb197-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="bb197-263">TreeView</span></span>|  
|<span data-ttu-id="bb197-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="bb197-264">VscrollBar</span></span>|  
|<span data-ttu-id="bb197-265">WebBrowser</span><span class="sxs-lookup"><span data-stu-id="bb197-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="bb197-266">Aşağıdaki denetimler için sunulan [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] yalnızca kendi desteği aracılığıyla [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bb197-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span></span> <span data-ttu-id="bb197-267">Bazı işlevler kullanılamayabilir.</span><span class="sxs-lookup"><span data-stu-id="bb197-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="bb197-268">Denetim adı</span><span class="sxs-lookup"><span data-stu-id="bb197-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="bb197-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="bb197-269">BindingSource</span></span>|  
|<span data-ttu-id="bb197-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="bb197-270">DataGrid</span></span>|  
|<span data-ttu-id="bb197-271">DataGridView</span><span class="sxs-lookup"><span data-stu-id="bb197-271">DataGridView</span></span>|  
|<span data-ttu-id="bb197-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="bb197-272">DataNavigator</span></span>|  
|<span data-ttu-id="bb197-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="bb197-273">DomainUpDown</span></span>|  
|<span data-ttu-id="bb197-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="bb197-274">ErrorProvider</span></span>|  
|<span data-ttu-id="bb197-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="bb197-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="bb197-276">Form</span><span class="sxs-lookup"><span data-stu-id="bb197-276">Form</span></span>|  
|<span data-ttu-id="bb197-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="bb197-277">LinkLabel</span></span>|  
|<span data-ttu-id="bb197-278">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="bb197-278">HelpProvider</span></span>|  
|<span data-ttu-id="bb197-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="bb197-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="bb197-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="bb197-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="bb197-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="bb197-281">NumericUpDown</span></span>|  
|<span data-ttu-id="bb197-282">Panel</span><span class="sxs-lookup"><span data-stu-id="bb197-282">Panel</span></span>|  
|<span data-ttu-id="bb197-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="bb197-283">PictureBox</span></span>|  
|<span data-ttu-id="bb197-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="bb197-284">PrintDocument</span></span>|  
|<span data-ttu-id="bb197-285">PrintPreview denetimi</span><span class="sxs-lookup"><span data-stu-id="bb197-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="bb197-286">PrintPreview iletişim kutusu</span><span class="sxs-lookup"><span data-stu-id="bb197-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="bb197-287">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="bb197-287">PropertyGrid</span></span>|  
|<span data-ttu-id="bb197-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="bb197-288">UserControl</span></span>|  
|<span data-ttu-id="bb197-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="bb197-289">ToolStrip</span></span>|  
|<span data-ttu-id="bb197-290">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="bb197-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="bb197-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="bb197-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="bb197-292">Bölümlendirici</span><span class="sxs-lookup"><span data-stu-id="bb197-292">Splitter</span></span>|  
|<span data-ttu-id="bb197-293">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="bb197-293">RaftingContainer</span></span>|  
|<span data-ttu-id="bb197-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="bb197-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bb197-295">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bb197-295">See Also</span></span>  
 [<span data-ttu-id="bb197-296">UI Otomasyonu Denetim Türleri</span><span class="sxs-lookup"><span data-stu-id="bb197-296">UI Automation Control Types</span></span>](../../../docs/framework/ui-automation/ui-automation-control-types.md)
