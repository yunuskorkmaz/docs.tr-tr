---
title: Standart Denetimler İçin UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 68fa7753be76b0681c40e540e86b11c89e7a8ca1
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47193894"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="3de28-102">Standart Denetimler İçin UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="3de28-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
>  <span data-ttu-id="3de28-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="3de28-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="3de28-104">En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="3de28-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="3de28-105">Bu konu hakkında bilgiler içerir. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] desteklemek için geliştirilen uygulamalarda standart denetimler için [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], ve [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] çerçeveleri.</span><span class="sxs-lookup"><span data-stu-id="3de28-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="3de28-106">Windows Presentation Foundation denetimleri</span><span class="sxs-lookup"><span data-stu-id="3de28-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="3de28-107">Tüm [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] bilgi veya destek için kullanıcı etkileşimi sağlayan denetim öğeleri tam yerel desteği olan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3de28-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="3de28-108">Panel gibi diğer öğeler için görünür değildir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3de28-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="3de28-109">Win32 denetimleri</span><span class="sxs-lookup"><span data-stu-id="3de28-109">Win32 Controls</span></span>  
 <span data-ttu-id="3de28-110">Çoğu [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] denetimleri için sunulur [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] UIAutomationClientsideProviders.dll istemci-tarafı sağlayıcıları aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="3de28-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="3de28-111">Bu derleme için UI otomasyon istemci uygulamaları ile kullanmak üzere otomatik olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="3de28-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="3de28-112">Yalnızca 6 sürümünden ComCtrl32.dll denetimleri için tam destek sağlanır (bulunan [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] ve üzeri).</span><span class="sxs-lookup"><span data-stu-id="3de28-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span></span>  
  
 <span data-ttu-id="3de28-113">Aşağıdaki denetimleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="3de28-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="3de28-114">Sınıf adı</span><span class="sxs-lookup"><span data-stu-id="3de28-114">Class name</span></span>|<span data-ttu-id="3de28-115">Denetim türü</span><span class="sxs-lookup"><span data-stu-id="3de28-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="3de28-116">Düğme</span><span class="sxs-lookup"><span data-stu-id="3de28-116">Button</span></span>|<span data-ttu-id="3de28-117">Düğme</span><span class="sxs-lookup"><span data-stu-id="3de28-117">Button</span></span>|  
|<span data-ttu-id="3de28-118">Düğme</span><span class="sxs-lookup"><span data-stu-id="3de28-118">Button</span></span>|<span data-ttu-id="3de28-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="3de28-119">RadioButton</span></span>|  
|<span data-ttu-id="3de28-120">Düğme</span><span class="sxs-lookup"><span data-stu-id="3de28-120">Button</span></span>|<span data-ttu-id="3de28-121">Grup</span><span class="sxs-lookup"><span data-stu-id="3de28-121">Group</span></span>|  
|<span data-ttu-id="3de28-122">Düğme</span><span class="sxs-lookup"><span data-stu-id="3de28-122">Button</span></span>|<span data-ttu-id="3de28-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="3de28-123">CheckBox</span></span>|  
|<span data-ttu-id="3de28-124">Düğme</span><span class="sxs-lookup"><span data-stu-id="3de28-124">Button</span></span>|<span data-ttu-id="3de28-125">Köprü</span><span class="sxs-lookup"><span data-stu-id="3de28-125">Hyperlink</span></span>|  
|<span data-ttu-id="3de28-126">Düğme</span><span class="sxs-lookup"><span data-stu-id="3de28-126">Button</span></span>|<span data-ttu-id="3de28-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="3de28-127">SplitButton</span></span>|  
|<span data-ttu-id="3de28-128">Düğme</span><span class="sxs-lookup"><span data-stu-id="3de28-128">Button</span></span>|<span data-ttu-id="3de28-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="3de28-129">CheckBox</span></span>|  
|<span data-ttu-id="3de28-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="3de28-130">ComboBoxEx32</span></span>|<span data-ttu-id="3de28-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="3de28-131">ComboBox</span></span>|  
|<span data-ttu-id="3de28-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="3de28-132">ComboBox</span></span>|<span data-ttu-id="3de28-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="3de28-133">ComboBox</span></span>|  
|<span data-ttu-id="3de28-134">Düzenle</span><span class="sxs-lookup"><span data-stu-id="3de28-134">Edit</span></span>|<span data-ttu-id="3de28-135">Belge</span><span class="sxs-lookup"><span data-stu-id="3de28-135">Document</span></span>|  
|<span data-ttu-id="3de28-136">Düzenle</span><span class="sxs-lookup"><span data-stu-id="3de28-136">Edit</span></span>|<span data-ttu-id="3de28-137">Düzenle</span><span class="sxs-lookup"><span data-stu-id="3de28-137">Edit</span></span>|  
|<span data-ttu-id="3de28-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="3de28-138">SysLink</span></span>|<span data-ttu-id="3de28-139">Köprü</span><span class="sxs-lookup"><span data-stu-id="3de28-139">Hyperlink</span></span>|  
|<span data-ttu-id="3de28-140">Statik</span><span class="sxs-lookup"><span data-stu-id="3de28-140">Static</span></span>|<span data-ttu-id="3de28-141">Metin</span><span class="sxs-lookup"><span data-stu-id="3de28-141">Text</span></span>|  
|<span data-ttu-id="3de28-142">Statik</span><span class="sxs-lookup"><span data-stu-id="3de28-142">Static</span></span>|<span data-ttu-id="3de28-143">Görüntü</span><span class="sxs-lookup"><span data-stu-id="3de28-143">Image</span></span>|  
|<span data-ttu-id="3de28-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="3de28-144">SysIPAddress32</span></span>|<span data-ttu-id="3de28-145">Özel</span><span class="sxs-lookup"><span data-stu-id="3de28-145">Custom</span></span>|  
|<span data-ttu-id="3de28-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="3de28-146">SysHeader32</span></span>|<span data-ttu-id="3de28-147">Üstbilgi/Headerıtem</span><span class="sxs-lookup"><span data-stu-id="3de28-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="3de28-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="3de28-148">SysListView32</span></span>|<span data-ttu-id="3de28-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="3de28-149">DataGrid</span></span>|  
|<span data-ttu-id="3de28-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="3de28-150">SysListView32</span></span>|<span data-ttu-id="3de28-151">List</span><span class="sxs-lookup"><span data-stu-id="3de28-151">List</span></span>|  
|<span data-ttu-id="3de28-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="3de28-152">ListBox</span></span>|<span data-ttu-id="3de28-153">List</span><span class="sxs-lookup"><span data-stu-id="3de28-153">List</span></span>|  
|<span data-ttu-id="3de28-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="3de28-154">ListBox</span></span>|<span data-ttu-id="3de28-155">ListItem</span><span class="sxs-lookup"><span data-stu-id="3de28-155">ListItem</span></span>|  
|<span data-ttu-id="3de28-156">#32768</span><span class="sxs-lookup"><span data-stu-id="3de28-156">#32768</span></span>|<span data-ttu-id="3de28-157">Menü</span><span class="sxs-lookup"><span data-stu-id="3de28-157">Menu</span></span>|  
|<span data-ttu-id="3de28-158">#32768</span><span class="sxs-lookup"><span data-stu-id="3de28-158">#32768</span></span>|<span data-ttu-id="3de28-159">MenuItem</span><span class="sxs-lookup"><span data-stu-id="3de28-159">MenuItem</span></span>|  
|<span data-ttu-id="3de28-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="3de28-160">msctls_progress32</span></span>|<span data-ttu-id="3de28-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="3de28-161">ProgressBar</span></span>|  
|<span data-ttu-id="3de28-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="3de28-162">RichEdit</span></span>|<span data-ttu-id="3de28-163">Belge.</span><span class="sxs-lookup"><span data-stu-id="3de28-163">Document.</span></span> <span data-ttu-id="3de28-164">Nota bakın.</span><span class="sxs-lookup"><span data-stu-id="3de28-164">See note.</span></span>|  
|<span data-ttu-id="3de28-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="3de28-165">RichEdit20A</span></span>|<span data-ttu-id="3de28-166">Belge</span><span class="sxs-lookup"><span data-stu-id="3de28-166">Document</span></span>|  
|<span data-ttu-id="3de28-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="3de28-167">RichEdit20W</span></span>|<span data-ttu-id="3de28-168">Belge</span><span class="sxs-lookup"><span data-stu-id="3de28-168">Document</span></span>|  
|<span data-ttu-id="3de28-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="3de28-169">RichEdit50W</span></span>|<span data-ttu-id="3de28-170">Belge</span><span class="sxs-lookup"><span data-stu-id="3de28-170">Document</span></span>|  
|<span data-ttu-id="3de28-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="3de28-171">ScrollBar</span></span>|<span data-ttu-id="3de28-172">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="3de28-172">Slider</span></span>|  
|<span data-ttu-id="3de28-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="3de28-173">msctls_trackbar32</span></span>|<span data-ttu-id="3de28-174">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="3de28-174">Slider</span></span>|  
|<span data-ttu-id="3de28-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="3de28-175">msctls_updown32</span></span>|<span data-ttu-id="3de28-176">Değer Değiştirici</span><span class="sxs-lookup"><span data-stu-id="3de28-176">Spinner</span></span>|  
|<span data-ttu-id="3de28-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="3de28-177">msctls_statusbar32</span></span>|<span data-ttu-id="3de28-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="3de28-178">StatusBar</span></span>|  
|<span data-ttu-id="3de28-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="3de28-179">SysTabControl32</span></span>|<span data-ttu-id="3de28-180">Tab</span><span class="sxs-lookup"><span data-stu-id="3de28-180">Tab</span></span>|  
|<span data-ttu-id="3de28-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="3de28-181">SysTabControl32</span></span>|<span data-ttu-id="3de28-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="3de28-182">TabItem</span></span>|  
|<span data-ttu-id="3de28-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="3de28-183">ToolbarWindow32</span></span>|<span data-ttu-id="3de28-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="3de28-184">ToolBar</span></span>|  
|<span data-ttu-id="3de28-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="3de28-185">ToolbarWindow32</span></span>|<span data-ttu-id="3de28-186">MenuItem</span><span class="sxs-lookup"><span data-stu-id="3de28-186">MenuItem</span></span>|  
|<span data-ttu-id="3de28-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="3de28-187">ToolbarWindow32</span></span>|<span data-ttu-id="3de28-188">Düğme</span><span class="sxs-lookup"><span data-stu-id="3de28-188">Button</span></span>|  
|<span data-ttu-id="3de28-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="3de28-189">ToolbarWindow32</span></span>|<span data-ttu-id="3de28-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="3de28-190">CheckBox</span></span>|  
|<span data-ttu-id="3de28-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="3de28-191">ToolbarWindow32</span></span>|<span data-ttu-id="3de28-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="3de28-192">RadioButton</span></span>|  
|<span data-ttu-id="3de28-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="3de28-193">ToolbarWindow32</span></span>|<span data-ttu-id="3de28-194">Ayırıcı</span><span class="sxs-lookup"><span data-stu-id="3de28-194">Separator</span></span>|  
|<span data-ttu-id="3de28-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="3de28-195">tooltips_class32</span></span>|<span data-ttu-id="3de28-196">ToolTip</span><span class="sxs-lookup"><span data-stu-id="3de28-196">ToolTip</span></span>|  
|<span data-ttu-id="3de28-197">#32774</span><span class="sxs-lookup"><span data-stu-id="3de28-197">#32774</span></span>|<span data-ttu-id="3de28-198">ToolTip</span><span class="sxs-lookup"><span data-stu-id="3de28-198">ToolTip</span></span>|  
|<span data-ttu-id="3de28-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="3de28-199">ReBarWindow32</span></span>|<span data-ttu-id="3de28-200">Araç Çubuğu</span><span class="sxs-lookup"><span data-stu-id="3de28-200">Toolbar</span></span>|  
|<span data-ttu-id="3de28-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="3de28-201">SysTreeView32</span></span>|<span data-ttu-id="3de28-202">Ağaç</span><span class="sxs-lookup"><span data-stu-id="3de28-202">Tree</span></span>|  
|<span data-ttu-id="3de28-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="3de28-203">SysTreeView32</span></span>|<span data-ttu-id="3de28-204">Treeıtem</span><span class="sxs-lookup"><span data-stu-id="3de28-204">TreeItem</span></span>|  
  
 <span data-ttu-id="3de28-205">**Not** RichEdit denetimini yalnızca sürümleri ile birlikte gelen için desteklenen [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (içinde RichEd20.dll sürüm 3.1 ve üzeri ve MsftEdit.dll sürümü 4.1 ve üzeri).</span><span class="sxs-lookup"><span data-stu-id="3de28-205">**Note** The RichEdit control is supported only for versions shipped with [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="3de28-206">Aşağıdaki denetimleri desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="3de28-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="3de28-207">Sınıf adı</span><span class="sxs-lookup"><span data-stu-id="3de28-207">Class name</span></span>|<span data-ttu-id="3de28-208">Denetim türü</span><span class="sxs-lookup"><span data-stu-id="3de28-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="3de28-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="3de28-209">SysAnimate32</span></span>|<span data-ttu-id="3de28-210">Görüntü</span><span class="sxs-lookup"><span data-stu-id="3de28-210">Image</span></span>|  
|<span data-ttu-id="3de28-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="3de28-211">SysPager</span></span>|<span data-ttu-id="3de28-212">Değer Değiştirici</span><span class="sxs-lookup"><span data-stu-id="3de28-212">Spinner</span></span>|  
|<span data-ttu-id="3de28-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="3de28-213">SysDateTimePick32</span></span>|<span data-ttu-id="3de28-214">Özel</span><span class="sxs-lookup"><span data-stu-id="3de28-214">Custom</span></span>|  
|<span data-ttu-id="3de28-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="3de28-215">SysMonthCal32</span></span>|<span data-ttu-id="3de28-216">Takvim</span><span class="sxs-lookup"><span data-stu-id="3de28-216">Calendar</span></span>|  
|<span data-ttu-id="3de28-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="3de28-217">MS_WINNOTE</span></span>|<span data-ttu-id="3de28-218">Araç İpucu</span><span class="sxs-lookup"><span data-stu-id="3de28-218">Tooltip</span></span>|  
|<span data-ttu-id="3de28-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="3de28-219">VBBubble</span></span>|<span data-ttu-id="3de28-220">Araç İpucu</span><span class="sxs-lookup"><span data-stu-id="3de28-220">Tooltip</span></span>|  
|<span data-ttu-id="3de28-221">(Tek başına denetim olarak kullanıldığında) bir kaydırma çubuğu</span><span class="sxs-lookup"><span data-stu-id="3de28-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="3de28-222">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="3de28-222">Slider</span></span>|  
|<span data-ttu-id="3de28-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="3de28-223">SuperGrid</span></span>|<span data-ttu-id="3de28-224">Özel</span><span class="sxs-lookup"><span data-stu-id="3de28-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="3de28-225">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="3de28-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="3de28-226">Windows Forms denetimleri için sunulur [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] UIAutomationClientsideProviders.dll istemci-tarafı sağlayıcıları aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="3de28-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="3de28-227">Bu derleme için UI otomasyon istemci uygulamaları ile kullanmak üzere otomatik olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="3de28-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="3de28-228">Genellikle, Windows Forms denetimleri yönetilen sarmalayıcıları için [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] tarafından desteklenen ortak denetimleri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3de28-228">Typically, Windows Forms controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="3de28-229">Aşağıdaki denetimleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="3de28-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="3de28-230">Sınıf Adı</span><span class="sxs-lookup"><span data-stu-id="3de28-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="3de28-231">Düğme</span><span class="sxs-lookup"><span data-stu-id="3de28-231">Button</span></span>|  
|<span data-ttu-id="3de28-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="3de28-232">CheckBox</span></span>|  
|<span data-ttu-id="3de28-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="3de28-233">CheckedListBox</span></span>|  
|<span data-ttu-id="3de28-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="3de28-234">ColorDialog</span></span>|  
|<span data-ttu-id="3de28-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="3de28-235">ComboBox</span></span>|  
|<span data-ttu-id="3de28-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="3de28-236">FolderBrowser</span></span>|  
|<span data-ttu-id="3de28-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="3de28-237">FontDialog</span></span>|  
|<span data-ttu-id="3de28-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="3de28-238">GroupBox</span></span>|  
|<span data-ttu-id="3de28-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="3de28-239">HscrollBar</span></span>|  
|<span data-ttu-id="3de28-240">ImageList</span><span class="sxs-lookup"><span data-stu-id="3de28-240">ImageList</span></span>|  
|<span data-ttu-id="3de28-241">Etiketle</span><span class="sxs-lookup"><span data-stu-id="3de28-241">Label</span></span>|  
|<span data-ttu-id="3de28-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="3de28-242">ListBox</span></span>|  
|<span data-ttu-id="3de28-243">ListView</span><span class="sxs-lookup"><span data-stu-id="3de28-243">ListView</span></span>|  
|<span data-ttu-id="3de28-244">MainMenu/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="3de28-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="3de28-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="3de28-245">MonthCalendar</span></span>|  
|<span data-ttu-id="3de28-246">Notifyıcon</span><span class="sxs-lookup"><span data-stu-id="3de28-246">NotifyIcon</span></span>|  
|<span data-ttu-id="3de28-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="3de28-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="3de28-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="3de28-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="3de28-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="3de28-249">PrintDialog</span></span>|  
|<span data-ttu-id="3de28-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="3de28-250">ProgressBar</span></span>|  
|<span data-ttu-id="3de28-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="3de28-251">RadioButton</span></span>|  
|<span data-ttu-id="3de28-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="3de28-252">RichTextBox</span></span>|  
|<span data-ttu-id="3de28-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="3de28-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="3de28-254">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="3de28-254">ScrollableControl</span></span>|  
|<span data-ttu-id="3de28-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="3de28-255">SoundPlayer</span></span>|  
|<span data-ttu-id="3de28-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="3de28-256">StatusBar</span></span>|  
|<span data-ttu-id="3de28-257">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="3de28-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="3de28-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="3de28-258">TextBox</span></span>|  
|<span data-ttu-id="3de28-259">Zamanlayıcı</span><span class="sxs-lookup"><span data-stu-id="3de28-259">Timer</span></span>|  
|<span data-ttu-id="3de28-260">Araç Çubuğu</span><span class="sxs-lookup"><span data-stu-id="3de28-260">Toolbar</span></span>|  
|<span data-ttu-id="3de28-261">ToolTip</span><span class="sxs-lookup"><span data-stu-id="3de28-261">ToolTip</span></span>|  
|<span data-ttu-id="3de28-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="3de28-262">TrackBar</span></span>|  
|<span data-ttu-id="3de28-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="3de28-263">TreeView</span></span>|  
|<span data-ttu-id="3de28-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="3de28-264">VscrollBar</span></span>|  
|<span data-ttu-id="3de28-265">WebBrowser</span><span class="sxs-lookup"><span data-stu-id="3de28-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="3de28-266">Aşağıdaki denetimler için sunulan [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] yalnızca kendi desteği aracılığıyla [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3de28-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span></span> <span data-ttu-id="3de28-267">Bazı işlevler kullanılamayabilir.</span><span class="sxs-lookup"><span data-stu-id="3de28-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="3de28-268">Denetim adı</span><span class="sxs-lookup"><span data-stu-id="3de28-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="3de28-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="3de28-269">BindingSource</span></span>|  
|<span data-ttu-id="3de28-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="3de28-270">DataGrid</span></span>|  
|<span data-ttu-id="3de28-271">DataGridView</span><span class="sxs-lookup"><span data-stu-id="3de28-271">DataGridView</span></span>|  
|<span data-ttu-id="3de28-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="3de28-272">DataNavigator</span></span>|  
|<span data-ttu-id="3de28-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="3de28-273">DomainUpDown</span></span>|  
|<span data-ttu-id="3de28-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="3de28-274">ErrorProvider</span></span>|  
|<span data-ttu-id="3de28-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="3de28-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="3de28-276">Form</span><span class="sxs-lookup"><span data-stu-id="3de28-276">Form</span></span>|  
|<span data-ttu-id="3de28-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="3de28-277">LinkLabel</span></span>|  
|<span data-ttu-id="3de28-278">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="3de28-278">HelpProvider</span></span>|  
|<span data-ttu-id="3de28-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="3de28-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="3de28-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="3de28-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="3de28-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="3de28-281">NumericUpDown</span></span>|  
|<span data-ttu-id="3de28-282">Panel</span><span class="sxs-lookup"><span data-stu-id="3de28-282">Panel</span></span>|  
|<span data-ttu-id="3de28-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="3de28-283">PictureBox</span></span>|  
|<span data-ttu-id="3de28-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="3de28-284">PrintDocument</span></span>|  
|<span data-ttu-id="3de28-285">PrintPreview denetimi</span><span class="sxs-lookup"><span data-stu-id="3de28-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="3de28-286">PrintPreview iletişim kutusu</span><span class="sxs-lookup"><span data-stu-id="3de28-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="3de28-287">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="3de28-287">PropertyGrid</span></span>|  
|<span data-ttu-id="3de28-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="3de28-288">UserControl</span></span>|  
|<span data-ttu-id="3de28-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="3de28-289">ToolStrip</span></span>|  
|<span data-ttu-id="3de28-290">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="3de28-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="3de28-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="3de28-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="3de28-292">Bölümlendirici</span><span class="sxs-lookup"><span data-stu-id="3de28-292">Splitter</span></span>|  
|<span data-ttu-id="3de28-293">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="3de28-293">RaftingContainer</span></span>|  
|<span data-ttu-id="3de28-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="3de28-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3de28-295">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3de28-295">See Also</span></span>  
 [<span data-ttu-id="3de28-296">UI Otomasyonu Denetim Türleri</span><span class="sxs-lookup"><span data-stu-id="3de28-296">UI Automation Control Types</span></span>](../../../docs/framework/ui-automation/ui-automation-control-types.md)
