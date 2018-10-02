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
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48037345"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="2d31a-102">Standart Denetimler İçin UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="2d31a-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
>  <span data-ttu-id="2d31a-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="2d31a-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="2d31a-104">En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="2d31a-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="2d31a-105">Bu konu hakkında bilgiler içerir. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] desteklemek için geliştirilen uygulamalarda standart denetimler için [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], ve [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] çerçeveleri.</span><span class="sxs-lookup"><span data-stu-id="2d31a-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="2d31a-106">Windows Presentation Foundation denetimleri</span><span class="sxs-lookup"><span data-stu-id="2d31a-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="2d31a-107">Tüm [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] bilgi veya destek için kullanıcı etkileşimi sağlayan denetim öğeleri tam yerel desteği olan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2d31a-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="2d31a-108">Panel gibi diğer öğeler için görünür değildir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2d31a-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="2d31a-109">Win32 denetimleri</span><span class="sxs-lookup"><span data-stu-id="2d31a-109">Win32 Controls</span></span>  
 <span data-ttu-id="2d31a-110">Çoğu [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] denetimleri için sunulur [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] UIAutomationClientsideProviders.dll istemci-tarafı sağlayıcıları aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="2d31a-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="2d31a-111">Bu derleme için UI otomasyon istemci uygulamaları ile kullanmak üzere otomatik olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="2d31a-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="2d31a-112">Yalnızca 6 sürümünden ComCtrl32.dll denetimleri için tam destek sağlanır (bulunan [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] ve üzeri).</span><span class="sxs-lookup"><span data-stu-id="2d31a-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span></span>  
  
 <span data-ttu-id="2d31a-113">Aşağıdaki denetimleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="2d31a-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="2d31a-114">Sınıf adı</span><span class="sxs-lookup"><span data-stu-id="2d31a-114">Class name</span></span>|<span data-ttu-id="2d31a-115">Denetim türü</span><span class="sxs-lookup"><span data-stu-id="2d31a-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="2d31a-116">Düğme</span><span class="sxs-lookup"><span data-stu-id="2d31a-116">Button</span></span>|<span data-ttu-id="2d31a-117">Düğme</span><span class="sxs-lookup"><span data-stu-id="2d31a-117">Button</span></span>|  
|<span data-ttu-id="2d31a-118">Düğme</span><span class="sxs-lookup"><span data-stu-id="2d31a-118">Button</span></span>|<span data-ttu-id="2d31a-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="2d31a-119">RadioButton</span></span>|  
|<span data-ttu-id="2d31a-120">Düğme</span><span class="sxs-lookup"><span data-stu-id="2d31a-120">Button</span></span>|<span data-ttu-id="2d31a-121">Grup</span><span class="sxs-lookup"><span data-stu-id="2d31a-121">Group</span></span>|  
|<span data-ttu-id="2d31a-122">Düğme</span><span class="sxs-lookup"><span data-stu-id="2d31a-122">Button</span></span>|<span data-ttu-id="2d31a-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="2d31a-123">CheckBox</span></span>|  
|<span data-ttu-id="2d31a-124">Düğme</span><span class="sxs-lookup"><span data-stu-id="2d31a-124">Button</span></span>|<span data-ttu-id="2d31a-125">Köprü</span><span class="sxs-lookup"><span data-stu-id="2d31a-125">Hyperlink</span></span>|  
|<span data-ttu-id="2d31a-126">Düğme</span><span class="sxs-lookup"><span data-stu-id="2d31a-126">Button</span></span>|<span data-ttu-id="2d31a-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="2d31a-127">SplitButton</span></span>|  
|<span data-ttu-id="2d31a-128">Düğme</span><span class="sxs-lookup"><span data-stu-id="2d31a-128">Button</span></span>|<span data-ttu-id="2d31a-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="2d31a-129">CheckBox</span></span>|  
|<span data-ttu-id="2d31a-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="2d31a-130">ComboBoxEx32</span></span>|<span data-ttu-id="2d31a-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="2d31a-131">ComboBox</span></span>|  
|<span data-ttu-id="2d31a-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="2d31a-132">ComboBox</span></span>|<span data-ttu-id="2d31a-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="2d31a-133">ComboBox</span></span>|  
|<span data-ttu-id="2d31a-134">Düzenle</span><span class="sxs-lookup"><span data-stu-id="2d31a-134">Edit</span></span>|<span data-ttu-id="2d31a-135">Belge</span><span class="sxs-lookup"><span data-stu-id="2d31a-135">Document</span></span>|  
|<span data-ttu-id="2d31a-136">Düzenle</span><span class="sxs-lookup"><span data-stu-id="2d31a-136">Edit</span></span>|<span data-ttu-id="2d31a-137">Düzenle</span><span class="sxs-lookup"><span data-stu-id="2d31a-137">Edit</span></span>|  
|<span data-ttu-id="2d31a-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="2d31a-138">SysLink</span></span>|<span data-ttu-id="2d31a-139">Köprü</span><span class="sxs-lookup"><span data-stu-id="2d31a-139">Hyperlink</span></span>|  
|<span data-ttu-id="2d31a-140">Statik</span><span class="sxs-lookup"><span data-stu-id="2d31a-140">Static</span></span>|<span data-ttu-id="2d31a-141">Metin</span><span class="sxs-lookup"><span data-stu-id="2d31a-141">Text</span></span>|  
|<span data-ttu-id="2d31a-142">Statik</span><span class="sxs-lookup"><span data-stu-id="2d31a-142">Static</span></span>|<span data-ttu-id="2d31a-143">Görüntü</span><span class="sxs-lookup"><span data-stu-id="2d31a-143">Image</span></span>|  
|<span data-ttu-id="2d31a-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="2d31a-144">SysIPAddress32</span></span>|<span data-ttu-id="2d31a-145">Özel</span><span class="sxs-lookup"><span data-stu-id="2d31a-145">Custom</span></span>|  
|<span data-ttu-id="2d31a-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="2d31a-146">SysHeader32</span></span>|<span data-ttu-id="2d31a-147">Üstbilgi/Headerıtem</span><span class="sxs-lookup"><span data-stu-id="2d31a-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="2d31a-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="2d31a-148">SysListView32</span></span>|<span data-ttu-id="2d31a-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="2d31a-149">DataGrid</span></span>|  
|<span data-ttu-id="2d31a-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="2d31a-150">SysListView32</span></span>|<span data-ttu-id="2d31a-151">List</span><span class="sxs-lookup"><span data-stu-id="2d31a-151">List</span></span>|  
|<span data-ttu-id="2d31a-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="2d31a-152">ListBox</span></span>|<span data-ttu-id="2d31a-153">List</span><span class="sxs-lookup"><span data-stu-id="2d31a-153">List</span></span>|  
|<span data-ttu-id="2d31a-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="2d31a-154">ListBox</span></span>|<span data-ttu-id="2d31a-155">ListItem</span><span class="sxs-lookup"><span data-stu-id="2d31a-155">ListItem</span></span>|  
|<span data-ttu-id="2d31a-156">#32768</span><span class="sxs-lookup"><span data-stu-id="2d31a-156">#32768</span></span>|<span data-ttu-id="2d31a-157">Menü</span><span class="sxs-lookup"><span data-stu-id="2d31a-157">Menu</span></span>|  
|<span data-ttu-id="2d31a-158">#32768</span><span class="sxs-lookup"><span data-stu-id="2d31a-158">#32768</span></span>|<span data-ttu-id="2d31a-159">MenuItem</span><span class="sxs-lookup"><span data-stu-id="2d31a-159">MenuItem</span></span>|  
|<span data-ttu-id="2d31a-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="2d31a-160">msctls_progress32</span></span>|<span data-ttu-id="2d31a-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="2d31a-161">ProgressBar</span></span>|  
|<span data-ttu-id="2d31a-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="2d31a-162">RichEdit</span></span>|<span data-ttu-id="2d31a-163">Belge.</span><span class="sxs-lookup"><span data-stu-id="2d31a-163">Document.</span></span> <span data-ttu-id="2d31a-164">Nota bakın.</span><span class="sxs-lookup"><span data-stu-id="2d31a-164">See note.</span></span>|  
|<span data-ttu-id="2d31a-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="2d31a-165">RichEdit20A</span></span>|<span data-ttu-id="2d31a-166">Belge</span><span class="sxs-lookup"><span data-stu-id="2d31a-166">Document</span></span>|  
|<span data-ttu-id="2d31a-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="2d31a-167">RichEdit20W</span></span>|<span data-ttu-id="2d31a-168">Belge</span><span class="sxs-lookup"><span data-stu-id="2d31a-168">Document</span></span>|  
|<span data-ttu-id="2d31a-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="2d31a-169">RichEdit50W</span></span>|<span data-ttu-id="2d31a-170">Belge</span><span class="sxs-lookup"><span data-stu-id="2d31a-170">Document</span></span>|  
|<span data-ttu-id="2d31a-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="2d31a-171">ScrollBar</span></span>|<span data-ttu-id="2d31a-172">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="2d31a-172">Slider</span></span>|  
|<span data-ttu-id="2d31a-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="2d31a-173">msctls_trackbar32</span></span>|<span data-ttu-id="2d31a-174">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="2d31a-174">Slider</span></span>|  
|<span data-ttu-id="2d31a-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="2d31a-175">msctls_updown32</span></span>|<span data-ttu-id="2d31a-176">Değer Değiştirici</span><span class="sxs-lookup"><span data-stu-id="2d31a-176">Spinner</span></span>|  
|<span data-ttu-id="2d31a-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="2d31a-177">msctls_statusbar32</span></span>|<span data-ttu-id="2d31a-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="2d31a-178">StatusBar</span></span>|  
|<span data-ttu-id="2d31a-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="2d31a-179">SysTabControl32</span></span>|<span data-ttu-id="2d31a-180">Tab</span><span class="sxs-lookup"><span data-stu-id="2d31a-180">Tab</span></span>|  
|<span data-ttu-id="2d31a-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="2d31a-181">SysTabControl32</span></span>|<span data-ttu-id="2d31a-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="2d31a-182">TabItem</span></span>|  
|<span data-ttu-id="2d31a-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="2d31a-183">ToolbarWindow32</span></span>|<span data-ttu-id="2d31a-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="2d31a-184">ToolBar</span></span>|  
|<span data-ttu-id="2d31a-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="2d31a-185">ToolbarWindow32</span></span>|<span data-ttu-id="2d31a-186">MenuItem</span><span class="sxs-lookup"><span data-stu-id="2d31a-186">MenuItem</span></span>|  
|<span data-ttu-id="2d31a-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="2d31a-187">ToolbarWindow32</span></span>|<span data-ttu-id="2d31a-188">Düğme</span><span class="sxs-lookup"><span data-stu-id="2d31a-188">Button</span></span>|  
|<span data-ttu-id="2d31a-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="2d31a-189">ToolbarWindow32</span></span>|<span data-ttu-id="2d31a-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="2d31a-190">CheckBox</span></span>|  
|<span data-ttu-id="2d31a-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="2d31a-191">ToolbarWindow32</span></span>|<span data-ttu-id="2d31a-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="2d31a-192">RadioButton</span></span>|  
|<span data-ttu-id="2d31a-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="2d31a-193">ToolbarWindow32</span></span>|<span data-ttu-id="2d31a-194">Ayırıcı</span><span class="sxs-lookup"><span data-stu-id="2d31a-194">Separator</span></span>|  
|<span data-ttu-id="2d31a-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="2d31a-195">tooltips_class32</span></span>|<span data-ttu-id="2d31a-196">ToolTip</span><span class="sxs-lookup"><span data-stu-id="2d31a-196">ToolTip</span></span>|  
|<span data-ttu-id="2d31a-197">#32774</span><span class="sxs-lookup"><span data-stu-id="2d31a-197">#32774</span></span>|<span data-ttu-id="2d31a-198">ToolTip</span><span class="sxs-lookup"><span data-stu-id="2d31a-198">ToolTip</span></span>|  
|<span data-ttu-id="2d31a-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="2d31a-199">ReBarWindow32</span></span>|<span data-ttu-id="2d31a-200">Araç Çubuğu</span><span class="sxs-lookup"><span data-stu-id="2d31a-200">Toolbar</span></span>|  
|<span data-ttu-id="2d31a-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="2d31a-201">SysTreeView32</span></span>|<span data-ttu-id="2d31a-202">Ağaç</span><span class="sxs-lookup"><span data-stu-id="2d31a-202">Tree</span></span>|  
|<span data-ttu-id="2d31a-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="2d31a-203">SysTreeView32</span></span>|<span data-ttu-id="2d31a-204">Treeıtem</span><span class="sxs-lookup"><span data-stu-id="2d31a-204">TreeItem</span></span>|  
  
 <span data-ttu-id="2d31a-205">**Not** RichEdit denetimini yalnızca sürümleri ile birlikte gelen için desteklenen [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (içinde RichEd20.dll sürüm 3.1 ve üzeri ve MsftEdit.dll sürümü 4.1 ve üzeri).</span><span class="sxs-lookup"><span data-stu-id="2d31a-205">**Note** The RichEdit control is supported only for versions shipped with [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="2d31a-206">Aşağıdaki denetimleri desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="2d31a-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="2d31a-207">Sınıf adı</span><span class="sxs-lookup"><span data-stu-id="2d31a-207">Class name</span></span>|<span data-ttu-id="2d31a-208">Denetim türü</span><span class="sxs-lookup"><span data-stu-id="2d31a-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="2d31a-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="2d31a-209">SysAnimate32</span></span>|<span data-ttu-id="2d31a-210">Görüntü</span><span class="sxs-lookup"><span data-stu-id="2d31a-210">Image</span></span>|  
|<span data-ttu-id="2d31a-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="2d31a-211">SysPager</span></span>|<span data-ttu-id="2d31a-212">Değer Değiştirici</span><span class="sxs-lookup"><span data-stu-id="2d31a-212">Spinner</span></span>|  
|<span data-ttu-id="2d31a-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="2d31a-213">SysDateTimePick32</span></span>|<span data-ttu-id="2d31a-214">Özel</span><span class="sxs-lookup"><span data-stu-id="2d31a-214">Custom</span></span>|  
|<span data-ttu-id="2d31a-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="2d31a-215">SysMonthCal32</span></span>|<span data-ttu-id="2d31a-216">Takvim</span><span class="sxs-lookup"><span data-stu-id="2d31a-216">Calendar</span></span>|  
|<span data-ttu-id="2d31a-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="2d31a-217">MS_WINNOTE</span></span>|<span data-ttu-id="2d31a-218">Araç İpucu</span><span class="sxs-lookup"><span data-stu-id="2d31a-218">Tooltip</span></span>|  
|<span data-ttu-id="2d31a-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="2d31a-219">VBBubble</span></span>|<span data-ttu-id="2d31a-220">Araç İpucu</span><span class="sxs-lookup"><span data-stu-id="2d31a-220">Tooltip</span></span>|  
|<span data-ttu-id="2d31a-221">(Tek başına denetim olarak kullanıldığında) bir kaydırma çubuğu</span><span class="sxs-lookup"><span data-stu-id="2d31a-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="2d31a-222">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="2d31a-222">Slider</span></span>|  
|<span data-ttu-id="2d31a-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="2d31a-223">SuperGrid</span></span>|<span data-ttu-id="2d31a-224">Özel</span><span class="sxs-lookup"><span data-stu-id="2d31a-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="2d31a-225">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="2d31a-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="2d31a-226">Windows Forms denetimleri için sunulur [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] UIAutomationClientsideProviders.dll istemci-tarafı sağlayıcıları aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="2d31a-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="2d31a-227">Bu derleme için UI otomasyon istemci uygulamaları ile kullanmak üzere otomatik olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="2d31a-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="2d31a-228">Genellikle, Windows Forms denetimleri yönetilen sarmalayıcıları için [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] tarafından desteklenen ortak denetimleri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2d31a-228">Typically, Windows Forms controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="2d31a-229">Aşağıdaki denetimleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="2d31a-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="2d31a-230">Sınıf Adı</span><span class="sxs-lookup"><span data-stu-id="2d31a-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="2d31a-231">Düğme</span><span class="sxs-lookup"><span data-stu-id="2d31a-231">Button</span></span>|  
|<span data-ttu-id="2d31a-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="2d31a-232">CheckBox</span></span>|  
|<span data-ttu-id="2d31a-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="2d31a-233">CheckedListBox</span></span>|  
|<span data-ttu-id="2d31a-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="2d31a-234">ColorDialog</span></span>|  
|<span data-ttu-id="2d31a-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="2d31a-235">ComboBox</span></span>|  
|<span data-ttu-id="2d31a-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="2d31a-236">FolderBrowser</span></span>|  
|<span data-ttu-id="2d31a-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="2d31a-237">FontDialog</span></span>|  
|<span data-ttu-id="2d31a-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="2d31a-238">GroupBox</span></span>|  
|<span data-ttu-id="2d31a-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="2d31a-239">HscrollBar</span></span>|  
|<span data-ttu-id="2d31a-240">ImageList</span><span class="sxs-lookup"><span data-stu-id="2d31a-240">ImageList</span></span>|  
|<span data-ttu-id="2d31a-241">Etiketle</span><span class="sxs-lookup"><span data-stu-id="2d31a-241">Label</span></span>|  
|<span data-ttu-id="2d31a-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="2d31a-242">ListBox</span></span>|  
|<span data-ttu-id="2d31a-243">ListView</span><span class="sxs-lookup"><span data-stu-id="2d31a-243">ListView</span></span>|  
|<span data-ttu-id="2d31a-244">MainMenu/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="2d31a-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="2d31a-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="2d31a-245">MonthCalendar</span></span>|  
|<span data-ttu-id="2d31a-246">Notifyıcon</span><span class="sxs-lookup"><span data-stu-id="2d31a-246">NotifyIcon</span></span>|  
|<span data-ttu-id="2d31a-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="2d31a-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="2d31a-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="2d31a-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="2d31a-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="2d31a-249">PrintDialog</span></span>|  
|<span data-ttu-id="2d31a-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="2d31a-250">ProgressBar</span></span>|  
|<span data-ttu-id="2d31a-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="2d31a-251">RadioButton</span></span>|  
|<span data-ttu-id="2d31a-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="2d31a-252">RichTextBox</span></span>|  
|<span data-ttu-id="2d31a-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="2d31a-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="2d31a-254">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="2d31a-254">ScrollableControl</span></span>|  
|<span data-ttu-id="2d31a-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="2d31a-255">SoundPlayer</span></span>|  
|<span data-ttu-id="2d31a-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="2d31a-256">StatusBar</span></span>|  
|<span data-ttu-id="2d31a-257">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="2d31a-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="2d31a-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="2d31a-258">TextBox</span></span>|  
|<span data-ttu-id="2d31a-259">Zamanlayıcı</span><span class="sxs-lookup"><span data-stu-id="2d31a-259">Timer</span></span>|  
|<span data-ttu-id="2d31a-260">Araç Çubuğu</span><span class="sxs-lookup"><span data-stu-id="2d31a-260">Toolbar</span></span>|  
|<span data-ttu-id="2d31a-261">ToolTip</span><span class="sxs-lookup"><span data-stu-id="2d31a-261">ToolTip</span></span>|  
|<span data-ttu-id="2d31a-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="2d31a-262">TrackBar</span></span>|  
|<span data-ttu-id="2d31a-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="2d31a-263">TreeView</span></span>|  
|<span data-ttu-id="2d31a-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="2d31a-264">VscrollBar</span></span>|  
|<span data-ttu-id="2d31a-265">WebBrowser</span><span class="sxs-lookup"><span data-stu-id="2d31a-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="2d31a-266">Aşağıdaki denetimler için sunulan [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] yalnızca kendi desteği aracılığıyla [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2d31a-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span></span> <span data-ttu-id="2d31a-267">Bazı işlevler kullanılamayabilir.</span><span class="sxs-lookup"><span data-stu-id="2d31a-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="2d31a-268">Denetim adı</span><span class="sxs-lookup"><span data-stu-id="2d31a-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="2d31a-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="2d31a-269">BindingSource</span></span>|  
|<span data-ttu-id="2d31a-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="2d31a-270">DataGrid</span></span>|  
|<span data-ttu-id="2d31a-271">DataGridView</span><span class="sxs-lookup"><span data-stu-id="2d31a-271">DataGridView</span></span>|  
|<span data-ttu-id="2d31a-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="2d31a-272">DataNavigator</span></span>|  
|<span data-ttu-id="2d31a-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="2d31a-273">DomainUpDown</span></span>|  
|<span data-ttu-id="2d31a-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="2d31a-274">ErrorProvider</span></span>|  
|<span data-ttu-id="2d31a-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="2d31a-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="2d31a-276">Form</span><span class="sxs-lookup"><span data-stu-id="2d31a-276">Form</span></span>|  
|<span data-ttu-id="2d31a-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="2d31a-277">LinkLabel</span></span>|  
|<span data-ttu-id="2d31a-278">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="2d31a-278">HelpProvider</span></span>|  
|<span data-ttu-id="2d31a-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="2d31a-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="2d31a-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="2d31a-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="2d31a-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="2d31a-281">NumericUpDown</span></span>|  
|<span data-ttu-id="2d31a-282">Panel</span><span class="sxs-lookup"><span data-stu-id="2d31a-282">Panel</span></span>|  
|<span data-ttu-id="2d31a-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="2d31a-283">PictureBox</span></span>|  
|<span data-ttu-id="2d31a-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="2d31a-284">PrintDocument</span></span>|  
|<span data-ttu-id="2d31a-285">PrintPreview denetimi</span><span class="sxs-lookup"><span data-stu-id="2d31a-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="2d31a-286">PrintPreview iletişim kutusu</span><span class="sxs-lookup"><span data-stu-id="2d31a-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="2d31a-287">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="2d31a-287">PropertyGrid</span></span>|  
|<span data-ttu-id="2d31a-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="2d31a-288">UserControl</span></span>|  
|<span data-ttu-id="2d31a-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="2d31a-289">ToolStrip</span></span>|  
|<span data-ttu-id="2d31a-290">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="2d31a-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="2d31a-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="2d31a-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="2d31a-292">Bölümlendirici</span><span class="sxs-lookup"><span data-stu-id="2d31a-292">Splitter</span></span>|  
|<span data-ttu-id="2d31a-293">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="2d31a-293">RaftingContainer</span></span>|  
|<span data-ttu-id="2d31a-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="2d31a-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2d31a-295">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2d31a-295">See Also</span></span>  
 [<span data-ttu-id="2d31a-296">UI Otomasyonu Denetim Türleri</span><span class="sxs-lookup"><span data-stu-id="2d31a-296">UI Automation Control Types</span></span>](../../../docs/framework/ui-automation/ui-automation-control-types.md)
