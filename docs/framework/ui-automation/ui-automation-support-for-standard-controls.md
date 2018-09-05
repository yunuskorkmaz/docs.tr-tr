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
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43519999"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="dceac-102">Standart Denetimler İçin UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="dceac-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
>  <span data-ttu-id="dceac-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="dceac-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="dceac-104">En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="dceac-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="dceac-105">Bu konu hakkında bilgiler içerir. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] desteklemek için geliştirilen uygulamalarda standart denetimler için [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], ve [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] çerçeveleri.</span><span class="sxs-lookup"><span data-stu-id="dceac-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="dceac-106">Windows Presentation Foundation denetimleri</span><span class="sxs-lookup"><span data-stu-id="dceac-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="dceac-107">Tüm [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] bilgi veya destek için kullanıcı etkileşimi sağlayan denetim öğeleri tam yerel desteği olan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dceac-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="dceac-108">Panel gibi diğer öğeler için görünür değildir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dceac-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="dceac-109">Win32 denetimleri</span><span class="sxs-lookup"><span data-stu-id="dceac-109">Win32 Controls</span></span>  
 <span data-ttu-id="dceac-110">Çoğu [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] denetimleri için sunulur [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] UIAutomationClientsideProviders.dll istemci-tarafı sağlayıcıları aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="dceac-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="dceac-111">Bu derleme için UI otomasyon istemci uygulamaları ile kullanmak üzere otomatik olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="dceac-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="dceac-112">Yalnızca 6 sürümünden ComCtrl32.dll denetimleri için tam destek sağlanır (bulunan [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] ve üzeri).</span><span class="sxs-lookup"><span data-stu-id="dceac-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span></span>  
  
 <span data-ttu-id="dceac-113">Aşağıdaki denetimleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="dceac-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="dceac-114">Sınıf adı</span><span class="sxs-lookup"><span data-stu-id="dceac-114">Class name</span></span>|<span data-ttu-id="dceac-115">Denetim türü</span><span class="sxs-lookup"><span data-stu-id="dceac-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="dceac-116">Düğme</span><span class="sxs-lookup"><span data-stu-id="dceac-116">Button</span></span>|<span data-ttu-id="dceac-117">Düğme</span><span class="sxs-lookup"><span data-stu-id="dceac-117">Button</span></span>|  
|<span data-ttu-id="dceac-118">Düğme</span><span class="sxs-lookup"><span data-stu-id="dceac-118">Button</span></span>|<span data-ttu-id="dceac-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="dceac-119">RadioButton</span></span>|  
|<span data-ttu-id="dceac-120">Düğme</span><span class="sxs-lookup"><span data-stu-id="dceac-120">Button</span></span>|<span data-ttu-id="dceac-121">Grup</span><span class="sxs-lookup"><span data-stu-id="dceac-121">Group</span></span>|  
|<span data-ttu-id="dceac-122">Düğme</span><span class="sxs-lookup"><span data-stu-id="dceac-122">Button</span></span>|<span data-ttu-id="dceac-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="dceac-123">CheckBox</span></span>|  
|<span data-ttu-id="dceac-124">Düğme</span><span class="sxs-lookup"><span data-stu-id="dceac-124">Button</span></span>|<span data-ttu-id="dceac-125">Köprü</span><span class="sxs-lookup"><span data-stu-id="dceac-125">Hyperlink</span></span>|  
|<span data-ttu-id="dceac-126">Düğme</span><span class="sxs-lookup"><span data-stu-id="dceac-126">Button</span></span>|<span data-ttu-id="dceac-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="dceac-127">SplitButton</span></span>|  
|<span data-ttu-id="dceac-128">Düğme</span><span class="sxs-lookup"><span data-stu-id="dceac-128">Button</span></span>|<span data-ttu-id="dceac-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="dceac-129">CheckBox</span></span>|  
|<span data-ttu-id="dceac-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="dceac-130">ComboBoxEx32</span></span>|<span data-ttu-id="dceac-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="dceac-131">ComboBox</span></span>|  
|<span data-ttu-id="dceac-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="dceac-132">ComboBox</span></span>|<span data-ttu-id="dceac-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="dceac-133">ComboBox</span></span>|  
|<span data-ttu-id="dceac-134">Düzenle</span><span class="sxs-lookup"><span data-stu-id="dceac-134">Edit</span></span>|<span data-ttu-id="dceac-135">Belge</span><span class="sxs-lookup"><span data-stu-id="dceac-135">Document</span></span>|  
|<span data-ttu-id="dceac-136">Düzenle</span><span class="sxs-lookup"><span data-stu-id="dceac-136">Edit</span></span>|<span data-ttu-id="dceac-137">Düzenle</span><span class="sxs-lookup"><span data-stu-id="dceac-137">Edit</span></span>|  
|<span data-ttu-id="dceac-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="dceac-138">SysLink</span></span>|<span data-ttu-id="dceac-139">Köprü</span><span class="sxs-lookup"><span data-stu-id="dceac-139">Hyperlink</span></span>|  
|<span data-ttu-id="dceac-140">Statik</span><span class="sxs-lookup"><span data-stu-id="dceac-140">Static</span></span>|<span data-ttu-id="dceac-141">Metin</span><span class="sxs-lookup"><span data-stu-id="dceac-141">Text</span></span>|  
|<span data-ttu-id="dceac-142">Statik</span><span class="sxs-lookup"><span data-stu-id="dceac-142">Static</span></span>|<span data-ttu-id="dceac-143">Görüntü</span><span class="sxs-lookup"><span data-stu-id="dceac-143">Image</span></span>|  
|<span data-ttu-id="dceac-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="dceac-144">SysIPAddress32</span></span>|<span data-ttu-id="dceac-145">Özel</span><span class="sxs-lookup"><span data-stu-id="dceac-145">Custom</span></span>|  
|<span data-ttu-id="dceac-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="dceac-146">SysHeader32</span></span>|<span data-ttu-id="dceac-147">Üstbilgi/Headerıtem</span><span class="sxs-lookup"><span data-stu-id="dceac-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="dceac-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="dceac-148">SysListView32</span></span>|<span data-ttu-id="dceac-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="dceac-149">DataGrid</span></span>|  
|<span data-ttu-id="dceac-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="dceac-150">SysListView32</span></span>|<span data-ttu-id="dceac-151">List</span><span class="sxs-lookup"><span data-stu-id="dceac-151">List</span></span>|  
|<span data-ttu-id="dceac-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="dceac-152">ListBox</span></span>|<span data-ttu-id="dceac-153">List</span><span class="sxs-lookup"><span data-stu-id="dceac-153">List</span></span>|  
|<span data-ttu-id="dceac-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="dceac-154">ListBox</span></span>|<span data-ttu-id="dceac-155">ListItem</span><span class="sxs-lookup"><span data-stu-id="dceac-155">ListItem</span></span>|  
|<span data-ttu-id="dceac-156">#32768</span><span class="sxs-lookup"><span data-stu-id="dceac-156">#32768</span></span>|<span data-ttu-id="dceac-157">Menü</span><span class="sxs-lookup"><span data-stu-id="dceac-157">Menu</span></span>|  
|<span data-ttu-id="dceac-158">#32768</span><span class="sxs-lookup"><span data-stu-id="dceac-158">#32768</span></span>|<span data-ttu-id="dceac-159">MenuItem</span><span class="sxs-lookup"><span data-stu-id="dceac-159">MenuItem</span></span>|  
|<span data-ttu-id="dceac-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="dceac-160">msctls_progress32</span></span>|<span data-ttu-id="dceac-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="dceac-161">ProgressBar</span></span>|  
|<span data-ttu-id="dceac-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="dceac-162">RichEdit</span></span>|<span data-ttu-id="dceac-163">Belge.</span><span class="sxs-lookup"><span data-stu-id="dceac-163">Document.</span></span> <span data-ttu-id="dceac-164">Nota bakın.</span><span class="sxs-lookup"><span data-stu-id="dceac-164">See note.</span></span>|  
|<span data-ttu-id="dceac-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="dceac-165">RichEdit20A</span></span>|<span data-ttu-id="dceac-166">Belge</span><span class="sxs-lookup"><span data-stu-id="dceac-166">Document</span></span>|  
|<span data-ttu-id="dceac-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="dceac-167">RichEdit20W</span></span>|<span data-ttu-id="dceac-168">Belge</span><span class="sxs-lookup"><span data-stu-id="dceac-168">Document</span></span>|  
|<span data-ttu-id="dceac-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="dceac-169">RichEdit50W</span></span>|<span data-ttu-id="dceac-170">Belge</span><span class="sxs-lookup"><span data-stu-id="dceac-170">Document</span></span>|  
|<span data-ttu-id="dceac-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="dceac-171">ScrollBar</span></span>|<span data-ttu-id="dceac-172">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="dceac-172">Slider</span></span>|  
|<span data-ttu-id="dceac-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="dceac-173">msctls_trackbar32</span></span>|<span data-ttu-id="dceac-174">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="dceac-174">Slider</span></span>|  
|<span data-ttu-id="dceac-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="dceac-175">msctls_updown32</span></span>|<span data-ttu-id="dceac-176">Değer Değiştirici</span><span class="sxs-lookup"><span data-stu-id="dceac-176">Spinner</span></span>|  
|<span data-ttu-id="dceac-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="dceac-177">msctls_statusbar32</span></span>|<span data-ttu-id="dceac-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="dceac-178">StatusBar</span></span>|  
|<span data-ttu-id="dceac-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="dceac-179">SysTabControl32</span></span>|<span data-ttu-id="dceac-180">Tab</span><span class="sxs-lookup"><span data-stu-id="dceac-180">Tab</span></span>|  
|<span data-ttu-id="dceac-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="dceac-181">SysTabControl32</span></span>|<span data-ttu-id="dceac-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="dceac-182">TabItem</span></span>|  
|<span data-ttu-id="dceac-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="dceac-183">ToolbarWindow32</span></span>|<span data-ttu-id="dceac-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="dceac-184">ToolBar</span></span>|  
|<span data-ttu-id="dceac-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="dceac-185">ToolbarWindow32</span></span>|<span data-ttu-id="dceac-186">MenuItem</span><span class="sxs-lookup"><span data-stu-id="dceac-186">MenuItem</span></span>|  
|<span data-ttu-id="dceac-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="dceac-187">ToolbarWindow32</span></span>|<span data-ttu-id="dceac-188">Düğme</span><span class="sxs-lookup"><span data-stu-id="dceac-188">Button</span></span>|  
|<span data-ttu-id="dceac-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="dceac-189">ToolbarWindow32</span></span>|<span data-ttu-id="dceac-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="dceac-190">CheckBox</span></span>|  
|<span data-ttu-id="dceac-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="dceac-191">ToolbarWindow32</span></span>|<span data-ttu-id="dceac-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="dceac-192">RadioButton</span></span>|  
|<span data-ttu-id="dceac-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="dceac-193">ToolbarWindow32</span></span>|<span data-ttu-id="dceac-194">Ayırıcı</span><span class="sxs-lookup"><span data-stu-id="dceac-194">Separator</span></span>|  
|<span data-ttu-id="dceac-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="dceac-195">tooltips_class32</span></span>|<span data-ttu-id="dceac-196">ToolTip</span><span class="sxs-lookup"><span data-stu-id="dceac-196">ToolTip</span></span>|  
|<span data-ttu-id="dceac-197">#32774</span><span class="sxs-lookup"><span data-stu-id="dceac-197">#32774</span></span>|<span data-ttu-id="dceac-198">ToolTip</span><span class="sxs-lookup"><span data-stu-id="dceac-198">ToolTip</span></span>|  
|<span data-ttu-id="dceac-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="dceac-199">ReBarWindow32</span></span>|<span data-ttu-id="dceac-200">Araç Çubuğu</span><span class="sxs-lookup"><span data-stu-id="dceac-200">Toolbar</span></span>|  
|<span data-ttu-id="dceac-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="dceac-201">SysTreeView32</span></span>|<span data-ttu-id="dceac-202">Ağaç</span><span class="sxs-lookup"><span data-stu-id="dceac-202">Tree</span></span>|  
|<span data-ttu-id="dceac-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="dceac-203">SysTreeView32</span></span>|<span data-ttu-id="dceac-204">Treeıtem</span><span class="sxs-lookup"><span data-stu-id="dceac-204">TreeItem</span></span>|  
  
 <span data-ttu-id="dceac-205">**Not** RichEdit denetimini yalnızca sürümleri ile birlikte gelen için desteklenen [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (içinde RichEd20.dll sürüm 3.1 ve üzeri ve MsftEdit.dll sürümü 4.1 ve üzeri).</span><span class="sxs-lookup"><span data-stu-id="dceac-205">**Note** The RichEdit control is supported only for versions shipped with [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="dceac-206">Aşağıdaki denetimleri desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="dceac-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="dceac-207">Sınıf adı</span><span class="sxs-lookup"><span data-stu-id="dceac-207">Class name</span></span>|<span data-ttu-id="dceac-208">Denetim türü</span><span class="sxs-lookup"><span data-stu-id="dceac-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="dceac-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="dceac-209">SysAnimate32</span></span>|<span data-ttu-id="dceac-210">Görüntü</span><span class="sxs-lookup"><span data-stu-id="dceac-210">Image</span></span>|  
|<span data-ttu-id="dceac-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="dceac-211">SysPager</span></span>|<span data-ttu-id="dceac-212">Değer Değiştirici</span><span class="sxs-lookup"><span data-stu-id="dceac-212">Spinner</span></span>|  
|<span data-ttu-id="dceac-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="dceac-213">SysDateTimePick32</span></span>|<span data-ttu-id="dceac-214">Özel</span><span class="sxs-lookup"><span data-stu-id="dceac-214">Custom</span></span>|  
|<span data-ttu-id="dceac-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="dceac-215">SysMonthCal32</span></span>|<span data-ttu-id="dceac-216">Takvim</span><span class="sxs-lookup"><span data-stu-id="dceac-216">Calendar</span></span>|  
|<span data-ttu-id="dceac-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="dceac-217">MS_WINNOTE</span></span>|<span data-ttu-id="dceac-218">Araç İpucu</span><span class="sxs-lookup"><span data-stu-id="dceac-218">Tooltip</span></span>|  
|<span data-ttu-id="dceac-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="dceac-219">VBBubble</span></span>|<span data-ttu-id="dceac-220">Araç İpucu</span><span class="sxs-lookup"><span data-stu-id="dceac-220">Tooltip</span></span>|  
|<span data-ttu-id="dceac-221">(Tek başına denetim olarak kullanıldığında) bir kaydırma çubuğu</span><span class="sxs-lookup"><span data-stu-id="dceac-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="dceac-222">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="dceac-222">Slider</span></span>|  
|<span data-ttu-id="dceac-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="dceac-223">SuperGrid</span></span>|<span data-ttu-id="dceac-224">Özel</span><span class="sxs-lookup"><span data-stu-id="dceac-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="dceac-225">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="dceac-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="dceac-226">Windows Forms denetimleri için sunulur [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] UIAutomationClientsideProviders.dll istemci-tarafı sağlayıcıları aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="dceac-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="dceac-227">Bu derleme için UI otomasyon istemci uygulamaları ile kullanmak üzere otomatik olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="dceac-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="dceac-228">Genellikle, Windows Forms denetimleri yönetilen sarmalayıcıları için [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] tarafından desteklenen ortak denetimleri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dceac-228">Typically, Windows Forms controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="dceac-229">Aşağıdaki denetimleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="dceac-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="dceac-230">Sınıf Adı</span><span class="sxs-lookup"><span data-stu-id="dceac-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="dceac-231">Düğme</span><span class="sxs-lookup"><span data-stu-id="dceac-231">Button</span></span>|  
|<span data-ttu-id="dceac-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="dceac-232">CheckBox</span></span>|  
|<span data-ttu-id="dceac-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="dceac-233">CheckedListBox</span></span>|  
|<span data-ttu-id="dceac-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="dceac-234">ColorDialog</span></span>|  
|<span data-ttu-id="dceac-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="dceac-235">ComboBox</span></span>|  
|<span data-ttu-id="dceac-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="dceac-236">FolderBrowser</span></span>|  
|<span data-ttu-id="dceac-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="dceac-237">FontDialog</span></span>|  
|<span data-ttu-id="dceac-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="dceac-238">GroupBox</span></span>|  
|<span data-ttu-id="dceac-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="dceac-239">HscrollBar</span></span>|  
|<span data-ttu-id="dceac-240">ImageList</span><span class="sxs-lookup"><span data-stu-id="dceac-240">ImageList</span></span>|  
|<span data-ttu-id="dceac-241">Etiketle</span><span class="sxs-lookup"><span data-stu-id="dceac-241">Label</span></span>|  
|<span data-ttu-id="dceac-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="dceac-242">ListBox</span></span>|  
|<span data-ttu-id="dceac-243">ListView</span><span class="sxs-lookup"><span data-stu-id="dceac-243">ListView</span></span>|  
|<span data-ttu-id="dceac-244">MainMenu/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="dceac-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="dceac-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="dceac-245">MonthCalendar</span></span>|  
|<span data-ttu-id="dceac-246">Notifyıcon</span><span class="sxs-lookup"><span data-stu-id="dceac-246">NotifyIcon</span></span>|  
|<span data-ttu-id="dceac-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="dceac-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="dceac-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="dceac-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="dceac-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="dceac-249">PrintDialog</span></span>|  
|<span data-ttu-id="dceac-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="dceac-250">ProgressBar</span></span>|  
|<span data-ttu-id="dceac-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="dceac-251">RadioButton</span></span>|  
|<span data-ttu-id="dceac-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="dceac-252">RichTextBox</span></span>|  
|<span data-ttu-id="dceac-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="dceac-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="dceac-254">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="dceac-254">ScrollableControl</span></span>|  
|<span data-ttu-id="dceac-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="dceac-255">SoundPlayer</span></span>|  
|<span data-ttu-id="dceac-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="dceac-256">StatusBar</span></span>|  
|<span data-ttu-id="dceac-257">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="dceac-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="dceac-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="dceac-258">TextBox</span></span>|  
|<span data-ttu-id="dceac-259">Zamanlayıcı</span><span class="sxs-lookup"><span data-stu-id="dceac-259">Timer</span></span>|  
|<span data-ttu-id="dceac-260">Araç Çubuğu</span><span class="sxs-lookup"><span data-stu-id="dceac-260">Toolbar</span></span>|  
|<span data-ttu-id="dceac-261">ToolTip</span><span class="sxs-lookup"><span data-stu-id="dceac-261">ToolTip</span></span>|  
|<span data-ttu-id="dceac-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="dceac-262">TrackBar</span></span>|  
|<span data-ttu-id="dceac-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="dceac-263">TreeView</span></span>|  
|<span data-ttu-id="dceac-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="dceac-264">VscrollBar</span></span>|  
|<span data-ttu-id="dceac-265">WebBrowser</span><span class="sxs-lookup"><span data-stu-id="dceac-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="dceac-266">Aşağıdaki denetimler için sunulan [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] yalnızca kendi desteği aracılığıyla [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dceac-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span></span> <span data-ttu-id="dceac-267">Bazı işlevler kullanılamayabilir.</span><span class="sxs-lookup"><span data-stu-id="dceac-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="dceac-268">Denetim adı</span><span class="sxs-lookup"><span data-stu-id="dceac-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="dceac-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="dceac-269">BindingSource</span></span>|  
|<span data-ttu-id="dceac-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="dceac-270">DataGrid</span></span>|  
|<span data-ttu-id="dceac-271">DataGridView</span><span class="sxs-lookup"><span data-stu-id="dceac-271">DataGridView</span></span>|  
|<span data-ttu-id="dceac-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="dceac-272">DataNavigator</span></span>|  
|<span data-ttu-id="dceac-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="dceac-273">DomainUpDown</span></span>|  
|<span data-ttu-id="dceac-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="dceac-274">ErrorProvider</span></span>|  
|<span data-ttu-id="dceac-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="dceac-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="dceac-276">Form</span><span class="sxs-lookup"><span data-stu-id="dceac-276">Form</span></span>|  
|<span data-ttu-id="dceac-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="dceac-277">LinkLabel</span></span>|  
|<span data-ttu-id="dceac-278">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="dceac-278">HelpProvider</span></span>|  
|<span data-ttu-id="dceac-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="dceac-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="dceac-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="dceac-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="dceac-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="dceac-281">NumericUpDown</span></span>|  
|<span data-ttu-id="dceac-282">Panel</span><span class="sxs-lookup"><span data-stu-id="dceac-282">Panel</span></span>|  
|<span data-ttu-id="dceac-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="dceac-283">PictureBox</span></span>|  
|<span data-ttu-id="dceac-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="dceac-284">PrintDocument</span></span>|  
|<span data-ttu-id="dceac-285">PrintPreview denetimi</span><span class="sxs-lookup"><span data-stu-id="dceac-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="dceac-286">PrintPreview iletişim kutusu</span><span class="sxs-lookup"><span data-stu-id="dceac-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="dceac-287">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="dceac-287">PropertyGrid</span></span>|  
|<span data-ttu-id="dceac-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="dceac-288">UserControl</span></span>|  
|<span data-ttu-id="dceac-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="dceac-289">ToolStrip</span></span>|  
|<span data-ttu-id="dceac-290">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="dceac-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="dceac-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="dceac-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="dceac-292">Bölümlendirici</span><span class="sxs-lookup"><span data-stu-id="dceac-292">Splitter</span></span>|  
|<span data-ttu-id="dceac-293">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="dceac-293">RaftingContainer</span></span>|  
|<span data-ttu-id="dceac-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="dceac-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dceac-295">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dceac-295">See Also</span></span>  
 [<span data-ttu-id="dceac-296">UI Otomasyonu Denetim Türleri</span><span class="sxs-lookup"><span data-stu-id="dceac-296">UI Automation Control Types</span></span>](../../../docs/framework/ui-automation/ui-automation-control-types.md)
