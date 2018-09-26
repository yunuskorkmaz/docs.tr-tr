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
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47157031"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="b8f39-102">Standart Denetimler İçin UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="b8f39-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
>  <span data-ttu-id="b8f39-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="b8f39-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="b8f39-104">En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="b8f39-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="b8f39-105">Bu konu hakkında bilgiler içerir. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] desteklemek için geliştirilen uygulamalarda standart denetimler için [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], ve [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] çerçeveleri.</span><span class="sxs-lookup"><span data-stu-id="b8f39-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="b8f39-106">Windows Presentation Foundation denetimleri</span><span class="sxs-lookup"><span data-stu-id="b8f39-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="b8f39-107">Tüm [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] bilgi veya destek için kullanıcı etkileşimi sağlayan denetim öğeleri tam yerel desteği olan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b8f39-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="b8f39-108">Panel gibi diğer öğeler için görünür değildir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b8f39-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="b8f39-109">Win32 denetimleri</span><span class="sxs-lookup"><span data-stu-id="b8f39-109">Win32 Controls</span></span>  
 <span data-ttu-id="b8f39-110">Çoğu [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] denetimleri için sunulur [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] UIAutomationClientsideProviders.dll istemci-tarafı sağlayıcıları aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="b8f39-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="b8f39-111">Bu derleme için UI otomasyon istemci uygulamaları ile kullanmak üzere otomatik olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="b8f39-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="b8f39-112">Yalnızca 6 sürümünden ComCtrl32.dll denetimleri için tam destek sağlanır (bulunan [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] ve üzeri).</span><span class="sxs-lookup"><span data-stu-id="b8f39-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span></span>  
  
 <span data-ttu-id="b8f39-113">Aşağıdaki denetimleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="b8f39-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="b8f39-114">Sınıf adı</span><span class="sxs-lookup"><span data-stu-id="b8f39-114">Class name</span></span>|<span data-ttu-id="b8f39-115">Denetim türü</span><span class="sxs-lookup"><span data-stu-id="b8f39-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="b8f39-116">Düğme</span><span class="sxs-lookup"><span data-stu-id="b8f39-116">Button</span></span>|<span data-ttu-id="b8f39-117">Düğme</span><span class="sxs-lookup"><span data-stu-id="b8f39-117">Button</span></span>|  
|<span data-ttu-id="b8f39-118">Düğme</span><span class="sxs-lookup"><span data-stu-id="b8f39-118">Button</span></span>|<span data-ttu-id="b8f39-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="b8f39-119">RadioButton</span></span>|  
|<span data-ttu-id="b8f39-120">Düğme</span><span class="sxs-lookup"><span data-stu-id="b8f39-120">Button</span></span>|<span data-ttu-id="b8f39-121">Grup</span><span class="sxs-lookup"><span data-stu-id="b8f39-121">Group</span></span>|  
|<span data-ttu-id="b8f39-122">Düğme</span><span class="sxs-lookup"><span data-stu-id="b8f39-122">Button</span></span>|<span data-ttu-id="b8f39-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="b8f39-123">CheckBox</span></span>|  
|<span data-ttu-id="b8f39-124">Düğme</span><span class="sxs-lookup"><span data-stu-id="b8f39-124">Button</span></span>|<span data-ttu-id="b8f39-125">Köprü</span><span class="sxs-lookup"><span data-stu-id="b8f39-125">Hyperlink</span></span>|  
|<span data-ttu-id="b8f39-126">Düğme</span><span class="sxs-lookup"><span data-stu-id="b8f39-126">Button</span></span>|<span data-ttu-id="b8f39-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="b8f39-127">SplitButton</span></span>|  
|<span data-ttu-id="b8f39-128">Düğme</span><span class="sxs-lookup"><span data-stu-id="b8f39-128">Button</span></span>|<span data-ttu-id="b8f39-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="b8f39-129">CheckBox</span></span>|  
|<span data-ttu-id="b8f39-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="b8f39-130">ComboBoxEx32</span></span>|<span data-ttu-id="b8f39-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="b8f39-131">ComboBox</span></span>|  
|<span data-ttu-id="b8f39-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="b8f39-132">ComboBox</span></span>|<span data-ttu-id="b8f39-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="b8f39-133">ComboBox</span></span>|  
|<span data-ttu-id="b8f39-134">Düzenle</span><span class="sxs-lookup"><span data-stu-id="b8f39-134">Edit</span></span>|<span data-ttu-id="b8f39-135">Belge</span><span class="sxs-lookup"><span data-stu-id="b8f39-135">Document</span></span>|  
|<span data-ttu-id="b8f39-136">Düzenle</span><span class="sxs-lookup"><span data-stu-id="b8f39-136">Edit</span></span>|<span data-ttu-id="b8f39-137">Düzenle</span><span class="sxs-lookup"><span data-stu-id="b8f39-137">Edit</span></span>|  
|<span data-ttu-id="b8f39-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="b8f39-138">SysLink</span></span>|<span data-ttu-id="b8f39-139">Köprü</span><span class="sxs-lookup"><span data-stu-id="b8f39-139">Hyperlink</span></span>|  
|<span data-ttu-id="b8f39-140">Statik</span><span class="sxs-lookup"><span data-stu-id="b8f39-140">Static</span></span>|<span data-ttu-id="b8f39-141">Metin</span><span class="sxs-lookup"><span data-stu-id="b8f39-141">Text</span></span>|  
|<span data-ttu-id="b8f39-142">Statik</span><span class="sxs-lookup"><span data-stu-id="b8f39-142">Static</span></span>|<span data-ttu-id="b8f39-143">Görüntü</span><span class="sxs-lookup"><span data-stu-id="b8f39-143">Image</span></span>|  
|<span data-ttu-id="b8f39-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="b8f39-144">SysIPAddress32</span></span>|<span data-ttu-id="b8f39-145">Özel</span><span class="sxs-lookup"><span data-stu-id="b8f39-145">Custom</span></span>|  
|<span data-ttu-id="b8f39-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="b8f39-146">SysHeader32</span></span>|<span data-ttu-id="b8f39-147">Üstbilgi/Headerıtem</span><span class="sxs-lookup"><span data-stu-id="b8f39-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="b8f39-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="b8f39-148">SysListView32</span></span>|<span data-ttu-id="b8f39-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="b8f39-149">DataGrid</span></span>|  
|<span data-ttu-id="b8f39-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="b8f39-150">SysListView32</span></span>|<span data-ttu-id="b8f39-151">List</span><span class="sxs-lookup"><span data-stu-id="b8f39-151">List</span></span>|  
|<span data-ttu-id="b8f39-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="b8f39-152">ListBox</span></span>|<span data-ttu-id="b8f39-153">List</span><span class="sxs-lookup"><span data-stu-id="b8f39-153">List</span></span>|  
|<span data-ttu-id="b8f39-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="b8f39-154">ListBox</span></span>|<span data-ttu-id="b8f39-155">ListItem</span><span class="sxs-lookup"><span data-stu-id="b8f39-155">ListItem</span></span>|  
|<span data-ttu-id="b8f39-156">#32768</span><span class="sxs-lookup"><span data-stu-id="b8f39-156">#32768</span></span>|<span data-ttu-id="b8f39-157">Menü</span><span class="sxs-lookup"><span data-stu-id="b8f39-157">Menu</span></span>|  
|<span data-ttu-id="b8f39-158">#32768</span><span class="sxs-lookup"><span data-stu-id="b8f39-158">#32768</span></span>|<span data-ttu-id="b8f39-159">MenuItem</span><span class="sxs-lookup"><span data-stu-id="b8f39-159">MenuItem</span></span>|  
|<span data-ttu-id="b8f39-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="b8f39-160">msctls_progress32</span></span>|<span data-ttu-id="b8f39-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="b8f39-161">ProgressBar</span></span>|  
|<span data-ttu-id="b8f39-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="b8f39-162">RichEdit</span></span>|<span data-ttu-id="b8f39-163">Belge.</span><span class="sxs-lookup"><span data-stu-id="b8f39-163">Document.</span></span> <span data-ttu-id="b8f39-164">Nota bakın.</span><span class="sxs-lookup"><span data-stu-id="b8f39-164">See note.</span></span>|  
|<span data-ttu-id="b8f39-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="b8f39-165">RichEdit20A</span></span>|<span data-ttu-id="b8f39-166">Belge</span><span class="sxs-lookup"><span data-stu-id="b8f39-166">Document</span></span>|  
|<span data-ttu-id="b8f39-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="b8f39-167">RichEdit20W</span></span>|<span data-ttu-id="b8f39-168">Belge</span><span class="sxs-lookup"><span data-stu-id="b8f39-168">Document</span></span>|  
|<span data-ttu-id="b8f39-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="b8f39-169">RichEdit50W</span></span>|<span data-ttu-id="b8f39-170">Belge</span><span class="sxs-lookup"><span data-stu-id="b8f39-170">Document</span></span>|  
|<span data-ttu-id="b8f39-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="b8f39-171">ScrollBar</span></span>|<span data-ttu-id="b8f39-172">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="b8f39-172">Slider</span></span>|  
|<span data-ttu-id="b8f39-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="b8f39-173">msctls_trackbar32</span></span>|<span data-ttu-id="b8f39-174">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="b8f39-174">Slider</span></span>|  
|<span data-ttu-id="b8f39-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="b8f39-175">msctls_updown32</span></span>|<span data-ttu-id="b8f39-176">Değer Değiştirici</span><span class="sxs-lookup"><span data-stu-id="b8f39-176">Spinner</span></span>|  
|<span data-ttu-id="b8f39-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="b8f39-177">msctls_statusbar32</span></span>|<span data-ttu-id="b8f39-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="b8f39-178">StatusBar</span></span>|  
|<span data-ttu-id="b8f39-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="b8f39-179">SysTabControl32</span></span>|<span data-ttu-id="b8f39-180">Tab</span><span class="sxs-lookup"><span data-stu-id="b8f39-180">Tab</span></span>|  
|<span data-ttu-id="b8f39-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="b8f39-181">SysTabControl32</span></span>|<span data-ttu-id="b8f39-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="b8f39-182">TabItem</span></span>|  
|<span data-ttu-id="b8f39-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="b8f39-183">ToolbarWindow32</span></span>|<span data-ttu-id="b8f39-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="b8f39-184">ToolBar</span></span>|  
|<span data-ttu-id="b8f39-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="b8f39-185">ToolbarWindow32</span></span>|<span data-ttu-id="b8f39-186">MenuItem</span><span class="sxs-lookup"><span data-stu-id="b8f39-186">MenuItem</span></span>|  
|<span data-ttu-id="b8f39-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="b8f39-187">ToolbarWindow32</span></span>|<span data-ttu-id="b8f39-188">Düğme</span><span class="sxs-lookup"><span data-stu-id="b8f39-188">Button</span></span>|  
|<span data-ttu-id="b8f39-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="b8f39-189">ToolbarWindow32</span></span>|<span data-ttu-id="b8f39-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="b8f39-190">CheckBox</span></span>|  
|<span data-ttu-id="b8f39-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="b8f39-191">ToolbarWindow32</span></span>|<span data-ttu-id="b8f39-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="b8f39-192">RadioButton</span></span>|  
|<span data-ttu-id="b8f39-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="b8f39-193">ToolbarWindow32</span></span>|<span data-ttu-id="b8f39-194">Ayırıcı</span><span class="sxs-lookup"><span data-stu-id="b8f39-194">Separator</span></span>|  
|<span data-ttu-id="b8f39-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="b8f39-195">tooltips_class32</span></span>|<span data-ttu-id="b8f39-196">ToolTip</span><span class="sxs-lookup"><span data-stu-id="b8f39-196">ToolTip</span></span>|  
|<span data-ttu-id="b8f39-197">#32774</span><span class="sxs-lookup"><span data-stu-id="b8f39-197">#32774</span></span>|<span data-ttu-id="b8f39-198">ToolTip</span><span class="sxs-lookup"><span data-stu-id="b8f39-198">ToolTip</span></span>|  
|<span data-ttu-id="b8f39-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="b8f39-199">ReBarWindow32</span></span>|<span data-ttu-id="b8f39-200">Araç Çubuğu</span><span class="sxs-lookup"><span data-stu-id="b8f39-200">Toolbar</span></span>|  
|<span data-ttu-id="b8f39-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="b8f39-201">SysTreeView32</span></span>|<span data-ttu-id="b8f39-202">Ağaç</span><span class="sxs-lookup"><span data-stu-id="b8f39-202">Tree</span></span>|  
|<span data-ttu-id="b8f39-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="b8f39-203">SysTreeView32</span></span>|<span data-ttu-id="b8f39-204">Treeıtem</span><span class="sxs-lookup"><span data-stu-id="b8f39-204">TreeItem</span></span>|  
  
 <span data-ttu-id="b8f39-205">**Not** RichEdit denetimini yalnızca sürümleri ile birlikte gelen için desteklenen [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (içinde RichEd20.dll sürüm 3.1 ve üzeri ve MsftEdit.dll sürümü 4.1 ve üzeri).</span><span class="sxs-lookup"><span data-stu-id="b8f39-205">**Note** The RichEdit control is supported only for versions shipped with [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="b8f39-206">Aşağıdaki denetimleri desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="b8f39-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="b8f39-207">Sınıf adı</span><span class="sxs-lookup"><span data-stu-id="b8f39-207">Class name</span></span>|<span data-ttu-id="b8f39-208">Denetim türü</span><span class="sxs-lookup"><span data-stu-id="b8f39-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="b8f39-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="b8f39-209">SysAnimate32</span></span>|<span data-ttu-id="b8f39-210">Görüntü</span><span class="sxs-lookup"><span data-stu-id="b8f39-210">Image</span></span>|  
|<span data-ttu-id="b8f39-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="b8f39-211">SysPager</span></span>|<span data-ttu-id="b8f39-212">Değer Değiştirici</span><span class="sxs-lookup"><span data-stu-id="b8f39-212">Spinner</span></span>|  
|<span data-ttu-id="b8f39-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="b8f39-213">SysDateTimePick32</span></span>|<span data-ttu-id="b8f39-214">Özel</span><span class="sxs-lookup"><span data-stu-id="b8f39-214">Custom</span></span>|  
|<span data-ttu-id="b8f39-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="b8f39-215">SysMonthCal32</span></span>|<span data-ttu-id="b8f39-216">Takvim</span><span class="sxs-lookup"><span data-stu-id="b8f39-216">Calendar</span></span>|  
|<span data-ttu-id="b8f39-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="b8f39-217">MS_WINNOTE</span></span>|<span data-ttu-id="b8f39-218">Araç İpucu</span><span class="sxs-lookup"><span data-stu-id="b8f39-218">Tooltip</span></span>|  
|<span data-ttu-id="b8f39-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="b8f39-219">VBBubble</span></span>|<span data-ttu-id="b8f39-220">Araç İpucu</span><span class="sxs-lookup"><span data-stu-id="b8f39-220">Tooltip</span></span>|  
|<span data-ttu-id="b8f39-221">(Tek başına denetim olarak kullanıldığında) bir kaydırma çubuğu</span><span class="sxs-lookup"><span data-stu-id="b8f39-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="b8f39-222">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="b8f39-222">Slider</span></span>|  
|<span data-ttu-id="b8f39-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="b8f39-223">SuperGrid</span></span>|<span data-ttu-id="b8f39-224">Özel</span><span class="sxs-lookup"><span data-stu-id="b8f39-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="b8f39-225">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="b8f39-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="b8f39-226">Windows Forms denetimleri için sunulur [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] UIAutomationClientsideProviders.dll istemci-tarafı sağlayıcıları aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="b8f39-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="b8f39-227">Bu derleme için UI otomasyon istemci uygulamaları ile kullanmak üzere otomatik olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="b8f39-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="b8f39-228">Genellikle, Windows Forms denetimleri yönetilen sarmalayıcıları için [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] tarafından desteklenen ortak denetimleri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b8f39-228">Typically, Windows Forms controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="b8f39-229">Aşağıdaki denetimleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="b8f39-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="b8f39-230">Sınıf Adı</span><span class="sxs-lookup"><span data-stu-id="b8f39-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="b8f39-231">Düğme</span><span class="sxs-lookup"><span data-stu-id="b8f39-231">Button</span></span>|  
|<span data-ttu-id="b8f39-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="b8f39-232">CheckBox</span></span>|  
|<span data-ttu-id="b8f39-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="b8f39-233">CheckedListBox</span></span>|  
|<span data-ttu-id="b8f39-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="b8f39-234">ColorDialog</span></span>|  
|<span data-ttu-id="b8f39-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="b8f39-235">ComboBox</span></span>|  
|<span data-ttu-id="b8f39-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="b8f39-236">FolderBrowser</span></span>|  
|<span data-ttu-id="b8f39-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="b8f39-237">FontDialog</span></span>|  
|<span data-ttu-id="b8f39-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="b8f39-238">GroupBox</span></span>|  
|<span data-ttu-id="b8f39-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="b8f39-239">HscrollBar</span></span>|  
|<span data-ttu-id="b8f39-240">ImageList</span><span class="sxs-lookup"><span data-stu-id="b8f39-240">ImageList</span></span>|  
|<span data-ttu-id="b8f39-241">Etiketle</span><span class="sxs-lookup"><span data-stu-id="b8f39-241">Label</span></span>|  
|<span data-ttu-id="b8f39-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="b8f39-242">ListBox</span></span>|  
|<span data-ttu-id="b8f39-243">ListView</span><span class="sxs-lookup"><span data-stu-id="b8f39-243">ListView</span></span>|  
|<span data-ttu-id="b8f39-244">MainMenu/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="b8f39-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="b8f39-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="b8f39-245">MonthCalendar</span></span>|  
|<span data-ttu-id="b8f39-246">Notifyıcon</span><span class="sxs-lookup"><span data-stu-id="b8f39-246">NotifyIcon</span></span>|  
|<span data-ttu-id="b8f39-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="b8f39-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="b8f39-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="b8f39-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="b8f39-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="b8f39-249">PrintDialog</span></span>|  
|<span data-ttu-id="b8f39-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="b8f39-250">ProgressBar</span></span>|  
|<span data-ttu-id="b8f39-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="b8f39-251">RadioButton</span></span>|  
|<span data-ttu-id="b8f39-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="b8f39-252">RichTextBox</span></span>|  
|<span data-ttu-id="b8f39-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="b8f39-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="b8f39-254">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="b8f39-254">ScrollableControl</span></span>|  
|<span data-ttu-id="b8f39-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="b8f39-255">SoundPlayer</span></span>|  
|<span data-ttu-id="b8f39-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="b8f39-256">StatusBar</span></span>|  
|<span data-ttu-id="b8f39-257">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="b8f39-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="b8f39-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="b8f39-258">TextBox</span></span>|  
|<span data-ttu-id="b8f39-259">Zamanlayıcı</span><span class="sxs-lookup"><span data-stu-id="b8f39-259">Timer</span></span>|  
|<span data-ttu-id="b8f39-260">Araç Çubuğu</span><span class="sxs-lookup"><span data-stu-id="b8f39-260">Toolbar</span></span>|  
|<span data-ttu-id="b8f39-261">ToolTip</span><span class="sxs-lookup"><span data-stu-id="b8f39-261">ToolTip</span></span>|  
|<span data-ttu-id="b8f39-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="b8f39-262">TrackBar</span></span>|  
|<span data-ttu-id="b8f39-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="b8f39-263">TreeView</span></span>|  
|<span data-ttu-id="b8f39-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="b8f39-264">VscrollBar</span></span>|  
|<span data-ttu-id="b8f39-265">WebBrowser</span><span class="sxs-lookup"><span data-stu-id="b8f39-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="b8f39-266">Aşağıdaki denetimler için sunulan [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] yalnızca kendi desteği aracılığıyla [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b8f39-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span></span> <span data-ttu-id="b8f39-267">Bazı işlevler kullanılamayabilir.</span><span class="sxs-lookup"><span data-stu-id="b8f39-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="b8f39-268">Denetim adı</span><span class="sxs-lookup"><span data-stu-id="b8f39-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="b8f39-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="b8f39-269">BindingSource</span></span>|  
|<span data-ttu-id="b8f39-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="b8f39-270">DataGrid</span></span>|  
|<span data-ttu-id="b8f39-271">DataGridView</span><span class="sxs-lookup"><span data-stu-id="b8f39-271">DataGridView</span></span>|  
|<span data-ttu-id="b8f39-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="b8f39-272">DataNavigator</span></span>|  
|<span data-ttu-id="b8f39-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="b8f39-273">DomainUpDown</span></span>|  
|<span data-ttu-id="b8f39-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="b8f39-274">ErrorProvider</span></span>|  
|<span data-ttu-id="b8f39-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="b8f39-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="b8f39-276">Form</span><span class="sxs-lookup"><span data-stu-id="b8f39-276">Form</span></span>|  
|<span data-ttu-id="b8f39-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="b8f39-277">LinkLabel</span></span>|  
|<span data-ttu-id="b8f39-278">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="b8f39-278">HelpProvider</span></span>|  
|<span data-ttu-id="b8f39-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="b8f39-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="b8f39-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="b8f39-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="b8f39-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="b8f39-281">NumericUpDown</span></span>|  
|<span data-ttu-id="b8f39-282">Panel</span><span class="sxs-lookup"><span data-stu-id="b8f39-282">Panel</span></span>|  
|<span data-ttu-id="b8f39-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="b8f39-283">PictureBox</span></span>|  
|<span data-ttu-id="b8f39-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="b8f39-284">PrintDocument</span></span>|  
|<span data-ttu-id="b8f39-285">PrintPreview denetimi</span><span class="sxs-lookup"><span data-stu-id="b8f39-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="b8f39-286">PrintPreview iletişim kutusu</span><span class="sxs-lookup"><span data-stu-id="b8f39-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="b8f39-287">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="b8f39-287">PropertyGrid</span></span>|  
|<span data-ttu-id="b8f39-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="b8f39-288">UserControl</span></span>|  
|<span data-ttu-id="b8f39-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="b8f39-289">ToolStrip</span></span>|  
|<span data-ttu-id="b8f39-290">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="b8f39-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="b8f39-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="b8f39-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="b8f39-292">Bölümlendirici</span><span class="sxs-lookup"><span data-stu-id="b8f39-292">Splitter</span></span>|  
|<span data-ttu-id="b8f39-293">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="b8f39-293">RaftingContainer</span></span>|  
|<span data-ttu-id="b8f39-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="b8f39-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b8f39-295">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b8f39-295">See Also</span></span>  
 [<span data-ttu-id="b8f39-296">UI Otomasyonu Denetim Türleri</span><span class="sxs-lookup"><span data-stu-id="b8f39-296">UI Automation Control Types</span></span>](../../../docs/framework/ui-automation/ui-automation-control-types.md)
