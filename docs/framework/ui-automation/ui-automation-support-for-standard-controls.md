---
title: Standart Denetimler İçin UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 5dbd547378faf885f5d0349ff77d124b0b860591
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57677636"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="ce5c1-102">Standart Denetimler İçin UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="ce5c1-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
>  <span data-ttu-id="ce5c1-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="ce5c1-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="ce5c1-104">En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="ce5c1-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="ce5c1-105">Bu konu hakkında bilgiler içerir. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] desteklemek için geliştirilen uygulamalarda standart denetimler için [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], ve [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] çerçeveleri.</span><span class="sxs-lookup"><span data-stu-id="ce5c1-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="ce5c1-106">Windows Presentation Foundation denetimleri</span><span class="sxs-lookup"><span data-stu-id="ce5c1-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="ce5c1-107">Tüm [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] bilgi veya destek için kullanıcı etkileşimi sağlayan denetim öğeleri tam yerel desteği olan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ce5c1-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="ce5c1-108">Panel gibi diğer öğeler için görünür değildir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ce5c1-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="ce5c1-109">Win32 denetimleri</span><span class="sxs-lookup"><span data-stu-id="ce5c1-109">Win32 Controls</span></span>  
 <span data-ttu-id="ce5c1-110">Çoğu [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] denetimleri için sunulur [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] UIAutomationClientsideProviders.dll istemci-tarafı sağlayıcıları aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="ce5c1-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="ce5c1-111">Bu derleme için UI otomasyon istemci uygulamaları ile kullanmak üzere otomatik olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="ce5c1-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="ce5c1-112">Yalnızca 6 sürümünden ComCtrl32.dll denetimleri için tam destek sağlanır (bulunan [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] ve üzeri).</span><span class="sxs-lookup"><span data-stu-id="ce5c1-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span></span>  
  
 <span data-ttu-id="ce5c1-113">Aşağıdaki denetimleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ce5c1-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="ce5c1-114">Sınıf adı</span><span class="sxs-lookup"><span data-stu-id="ce5c1-114">Class name</span></span>|<span data-ttu-id="ce5c1-115">Denetim türü</span><span class="sxs-lookup"><span data-stu-id="ce5c1-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="ce5c1-116">Düğme</span><span class="sxs-lookup"><span data-stu-id="ce5c1-116">Button</span></span>|<span data-ttu-id="ce5c1-117">Düğme</span><span class="sxs-lookup"><span data-stu-id="ce5c1-117">Button</span></span>|  
|<span data-ttu-id="ce5c1-118">Düğme</span><span class="sxs-lookup"><span data-stu-id="ce5c1-118">Button</span></span>|<span data-ttu-id="ce5c1-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="ce5c1-119">RadioButton</span></span>|  
|<span data-ttu-id="ce5c1-120">Düğme</span><span class="sxs-lookup"><span data-stu-id="ce5c1-120">Button</span></span>|<span data-ttu-id="ce5c1-121">Grup</span><span class="sxs-lookup"><span data-stu-id="ce5c1-121">Group</span></span>|  
|<span data-ttu-id="ce5c1-122">Düğme</span><span class="sxs-lookup"><span data-stu-id="ce5c1-122">Button</span></span>|<span data-ttu-id="ce5c1-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="ce5c1-123">CheckBox</span></span>|  
|<span data-ttu-id="ce5c1-124">Düğme</span><span class="sxs-lookup"><span data-stu-id="ce5c1-124">Button</span></span>|<span data-ttu-id="ce5c1-125">Köprü</span><span class="sxs-lookup"><span data-stu-id="ce5c1-125">Hyperlink</span></span>|  
|<span data-ttu-id="ce5c1-126">Düğme</span><span class="sxs-lookup"><span data-stu-id="ce5c1-126">Button</span></span>|<span data-ttu-id="ce5c1-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="ce5c1-127">SplitButton</span></span>|  
|<span data-ttu-id="ce5c1-128">Düğme</span><span class="sxs-lookup"><span data-stu-id="ce5c1-128">Button</span></span>|<span data-ttu-id="ce5c1-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="ce5c1-129">CheckBox</span></span>|  
|<span data-ttu-id="ce5c1-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="ce5c1-130">ComboBoxEx32</span></span>|<span data-ttu-id="ce5c1-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="ce5c1-131">ComboBox</span></span>|  
|<span data-ttu-id="ce5c1-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="ce5c1-132">ComboBox</span></span>|<span data-ttu-id="ce5c1-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="ce5c1-133">ComboBox</span></span>|  
|<span data-ttu-id="ce5c1-134">Düzenle</span><span class="sxs-lookup"><span data-stu-id="ce5c1-134">Edit</span></span>|<span data-ttu-id="ce5c1-135">Belge</span><span class="sxs-lookup"><span data-stu-id="ce5c1-135">Document</span></span>|  
|<span data-ttu-id="ce5c1-136">Düzenle</span><span class="sxs-lookup"><span data-stu-id="ce5c1-136">Edit</span></span>|<span data-ttu-id="ce5c1-137">Düzenle</span><span class="sxs-lookup"><span data-stu-id="ce5c1-137">Edit</span></span>|  
|<span data-ttu-id="ce5c1-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="ce5c1-138">SysLink</span></span>|<span data-ttu-id="ce5c1-139">Köprü</span><span class="sxs-lookup"><span data-stu-id="ce5c1-139">Hyperlink</span></span>|  
|<span data-ttu-id="ce5c1-140">Statik</span><span class="sxs-lookup"><span data-stu-id="ce5c1-140">Static</span></span>|<span data-ttu-id="ce5c1-141">Metin</span><span class="sxs-lookup"><span data-stu-id="ce5c1-141">Text</span></span>|  
|<span data-ttu-id="ce5c1-142">Statik</span><span class="sxs-lookup"><span data-stu-id="ce5c1-142">Static</span></span>|<span data-ttu-id="ce5c1-143">Görüntü</span><span class="sxs-lookup"><span data-stu-id="ce5c1-143">Image</span></span>|  
|<span data-ttu-id="ce5c1-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="ce5c1-144">SysIPAddress32</span></span>|<span data-ttu-id="ce5c1-145">Özel</span><span class="sxs-lookup"><span data-stu-id="ce5c1-145">Custom</span></span>|  
|<span data-ttu-id="ce5c1-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="ce5c1-146">SysHeader32</span></span>|<span data-ttu-id="ce5c1-147">Üstbilgi/Headerıtem</span><span class="sxs-lookup"><span data-stu-id="ce5c1-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="ce5c1-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="ce5c1-148">SysListView32</span></span>|<span data-ttu-id="ce5c1-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="ce5c1-149">DataGrid</span></span>|  
|<span data-ttu-id="ce5c1-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="ce5c1-150">SysListView32</span></span>|<span data-ttu-id="ce5c1-151">List</span><span class="sxs-lookup"><span data-stu-id="ce5c1-151">List</span></span>|  
|<span data-ttu-id="ce5c1-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="ce5c1-152">ListBox</span></span>|<span data-ttu-id="ce5c1-153">List</span><span class="sxs-lookup"><span data-stu-id="ce5c1-153">List</span></span>|  
|<span data-ttu-id="ce5c1-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="ce5c1-154">ListBox</span></span>|<span data-ttu-id="ce5c1-155">ListItem</span><span class="sxs-lookup"><span data-stu-id="ce5c1-155">ListItem</span></span>|  
|<span data-ttu-id="ce5c1-156">#32768</span><span class="sxs-lookup"><span data-stu-id="ce5c1-156">#32768</span></span>|<span data-ttu-id="ce5c1-157">Menü</span><span class="sxs-lookup"><span data-stu-id="ce5c1-157">Menu</span></span>|  
|<span data-ttu-id="ce5c1-158">#32768</span><span class="sxs-lookup"><span data-stu-id="ce5c1-158">#32768</span></span>|<span data-ttu-id="ce5c1-159">MenuItem</span><span class="sxs-lookup"><span data-stu-id="ce5c1-159">MenuItem</span></span>|  
|<span data-ttu-id="ce5c1-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="ce5c1-160">msctls_progress32</span></span>|<span data-ttu-id="ce5c1-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="ce5c1-161">ProgressBar</span></span>|  
|<span data-ttu-id="ce5c1-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="ce5c1-162">RichEdit</span></span>|<span data-ttu-id="ce5c1-163">Belge.</span><span class="sxs-lookup"><span data-stu-id="ce5c1-163">Document.</span></span> <span data-ttu-id="ce5c1-164">Nota bakın.</span><span class="sxs-lookup"><span data-stu-id="ce5c1-164">See note.</span></span>|  
|<span data-ttu-id="ce5c1-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="ce5c1-165">RichEdit20A</span></span>|<span data-ttu-id="ce5c1-166">Belge</span><span class="sxs-lookup"><span data-stu-id="ce5c1-166">Document</span></span>|  
|<span data-ttu-id="ce5c1-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="ce5c1-167">RichEdit20W</span></span>|<span data-ttu-id="ce5c1-168">Belge</span><span class="sxs-lookup"><span data-stu-id="ce5c1-168">Document</span></span>|  
|<span data-ttu-id="ce5c1-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="ce5c1-169">RichEdit50W</span></span>|<span data-ttu-id="ce5c1-170">Belge</span><span class="sxs-lookup"><span data-stu-id="ce5c1-170">Document</span></span>|  
|<span data-ttu-id="ce5c1-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="ce5c1-171">ScrollBar</span></span>|<span data-ttu-id="ce5c1-172">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="ce5c1-172">Slider</span></span>|  
|<span data-ttu-id="ce5c1-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="ce5c1-173">msctls_trackbar32</span></span>|<span data-ttu-id="ce5c1-174">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="ce5c1-174">Slider</span></span>|  
|<span data-ttu-id="ce5c1-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="ce5c1-175">msctls_updown32</span></span>|<span data-ttu-id="ce5c1-176">Değer Değiştirici</span><span class="sxs-lookup"><span data-stu-id="ce5c1-176">Spinner</span></span>|  
|<span data-ttu-id="ce5c1-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="ce5c1-177">msctls_statusbar32</span></span>|<span data-ttu-id="ce5c1-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="ce5c1-178">StatusBar</span></span>|  
|<span data-ttu-id="ce5c1-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="ce5c1-179">SysTabControl32</span></span>|<span data-ttu-id="ce5c1-180">Tab</span><span class="sxs-lookup"><span data-stu-id="ce5c1-180">Tab</span></span>|  
|<span data-ttu-id="ce5c1-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="ce5c1-181">SysTabControl32</span></span>|<span data-ttu-id="ce5c1-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="ce5c1-182">TabItem</span></span>|  
|<span data-ttu-id="ce5c1-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="ce5c1-183">ToolbarWindow32</span></span>|<span data-ttu-id="ce5c1-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="ce5c1-184">ToolBar</span></span>|  
|<span data-ttu-id="ce5c1-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="ce5c1-185">ToolbarWindow32</span></span>|<span data-ttu-id="ce5c1-186">MenuItem</span><span class="sxs-lookup"><span data-stu-id="ce5c1-186">MenuItem</span></span>|  
|<span data-ttu-id="ce5c1-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="ce5c1-187">ToolbarWindow32</span></span>|<span data-ttu-id="ce5c1-188">Düğme</span><span class="sxs-lookup"><span data-stu-id="ce5c1-188">Button</span></span>|  
|<span data-ttu-id="ce5c1-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="ce5c1-189">ToolbarWindow32</span></span>|<span data-ttu-id="ce5c1-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="ce5c1-190">CheckBox</span></span>|  
|<span data-ttu-id="ce5c1-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="ce5c1-191">ToolbarWindow32</span></span>|<span data-ttu-id="ce5c1-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="ce5c1-192">RadioButton</span></span>|  
|<span data-ttu-id="ce5c1-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="ce5c1-193">ToolbarWindow32</span></span>|<span data-ttu-id="ce5c1-194">Ayırıcı</span><span class="sxs-lookup"><span data-stu-id="ce5c1-194">Separator</span></span>|  
|<span data-ttu-id="ce5c1-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="ce5c1-195">tooltips_class32</span></span>|<span data-ttu-id="ce5c1-196">ToolTip</span><span class="sxs-lookup"><span data-stu-id="ce5c1-196">ToolTip</span></span>|  
|<span data-ttu-id="ce5c1-197">#32774</span><span class="sxs-lookup"><span data-stu-id="ce5c1-197">#32774</span></span>|<span data-ttu-id="ce5c1-198">ToolTip</span><span class="sxs-lookup"><span data-stu-id="ce5c1-198">ToolTip</span></span>|  
|<span data-ttu-id="ce5c1-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="ce5c1-199">ReBarWindow32</span></span>|<span data-ttu-id="ce5c1-200">Araç Çubuğu</span><span class="sxs-lookup"><span data-stu-id="ce5c1-200">Toolbar</span></span>|  
|<span data-ttu-id="ce5c1-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="ce5c1-201">SysTreeView32</span></span>|<span data-ttu-id="ce5c1-202">Ağaç</span><span class="sxs-lookup"><span data-stu-id="ce5c1-202">Tree</span></span>|  
|<span data-ttu-id="ce5c1-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="ce5c1-203">SysTreeView32</span></span>|<span data-ttu-id="ce5c1-204">Treeıtem</span><span class="sxs-lookup"><span data-stu-id="ce5c1-204">TreeItem</span></span>|  
  
 <span data-ttu-id="ce5c1-205">**Not** RichEdit denetimini yalnızca sürümleri ile birlikte gelen için desteklenen [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (içinde RichEd20.dll sürüm 3.1 ve üzeri ve MsftEdit.dll sürümü 4.1 ve üzeri).</span><span class="sxs-lookup"><span data-stu-id="ce5c1-205">**Note** The RichEdit control is supported only for versions shipped with [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="ce5c1-206">Aşağıdaki denetimleri desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="ce5c1-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="ce5c1-207">Sınıf adı</span><span class="sxs-lookup"><span data-stu-id="ce5c1-207">Class name</span></span>|<span data-ttu-id="ce5c1-208">Denetim türü</span><span class="sxs-lookup"><span data-stu-id="ce5c1-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="ce5c1-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="ce5c1-209">SysAnimate32</span></span>|<span data-ttu-id="ce5c1-210">Görüntü</span><span class="sxs-lookup"><span data-stu-id="ce5c1-210">Image</span></span>|  
|<span data-ttu-id="ce5c1-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="ce5c1-211">SysPager</span></span>|<span data-ttu-id="ce5c1-212">Değer Değiştirici</span><span class="sxs-lookup"><span data-stu-id="ce5c1-212">Spinner</span></span>|  
|<span data-ttu-id="ce5c1-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="ce5c1-213">SysDateTimePick32</span></span>|<span data-ttu-id="ce5c1-214">Özel</span><span class="sxs-lookup"><span data-stu-id="ce5c1-214">Custom</span></span>|  
|<span data-ttu-id="ce5c1-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="ce5c1-215">SysMonthCal32</span></span>|<span data-ttu-id="ce5c1-216">Takvim</span><span class="sxs-lookup"><span data-stu-id="ce5c1-216">Calendar</span></span>|  
|<span data-ttu-id="ce5c1-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="ce5c1-217">MS_WINNOTE</span></span>|<span data-ttu-id="ce5c1-218">Araç İpucu</span><span class="sxs-lookup"><span data-stu-id="ce5c1-218">Tooltip</span></span>|  
|<span data-ttu-id="ce5c1-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="ce5c1-219">VBBubble</span></span>|<span data-ttu-id="ce5c1-220">Araç İpucu</span><span class="sxs-lookup"><span data-stu-id="ce5c1-220">Tooltip</span></span>|  
|<span data-ttu-id="ce5c1-221">(Tek başına denetim olarak kullanıldığında) bir kaydırma çubuğu</span><span class="sxs-lookup"><span data-stu-id="ce5c1-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="ce5c1-222">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="ce5c1-222">Slider</span></span>|  
|<span data-ttu-id="ce5c1-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="ce5c1-223">SuperGrid</span></span>|<span data-ttu-id="ce5c1-224">Özel</span><span class="sxs-lookup"><span data-stu-id="ce5c1-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="ce5c1-225">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="ce5c1-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="ce5c1-226">Windows Forms denetimleri için sunulur [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] UIAutomationClientsideProviders.dll istemci-tarafı sağlayıcıları aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="ce5c1-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="ce5c1-227">Bu derleme için UI otomasyon istemci uygulamaları ile kullanmak üzere otomatik olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="ce5c1-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="ce5c1-228">Genellikle, Windows Forms denetimleri yönetilen sarmalayıcıları için [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] tarafından desteklenen ortak denetimleri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ce5c1-228">Typically, Windows Forms controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="ce5c1-229">Aşağıdaki denetimleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ce5c1-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="ce5c1-230">Sınıf Adı</span><span class="sxs-lookup"><span data-stu-id="ce5c1-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="ce5c1-231">Düğme</span><span class="sxs-lookup"><span data-stu-id="ce5c1-231">Button</span></span>|  
|<span data-ttu-id="ce5c1-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="ce5c1-232">CheckBox</span></span>|  
|<span data-ttu-id="ce5c1-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="ce5c1-233">CheckedListBox</span></span>|  
|<span data-ttu-id="ce5c1-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="ce5c1-234">ColorDialog</span></span>|  
|<span data-ttu-id="ce5c1-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="ce5c1-235">ComboBox</span></span>|  
|<span data-ttu-id="ce5c1-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="ce5c1-236">FolderBrowser</span></span>|  
|<span data-ttu-id="ce5c1-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="ce5c1-237">FontDialog</span></span>|  
|<span data-ttu-id="ce5c1-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="ce5c1-238">GroupBox</span></span>|  
|<span data-ttu-id="ce5c1-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="ce5c1-239">HscrollBar</span></span>|  
|<span data-ttu-id="ce5c1-240">ImageList</span><span class="sxs-lookup"><span data-stu-id="ce5c1-240">ImageList</span></span>|  
|<span data-ttu-id="ce5c1-241">Etiketle</span><span class="sxs-lookup"><span data-stu-id="ce5c1-241">Label</span></span>|  
|<span data-ttu-id="ce5c1-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="ce5c1-242">ListBox</span></span>|  
|<span data-ttu-id="ce5c1-243">ListView</span><span class="sxs-lookup"><span data-stu-id="ce5c1-243">ListView</span></span>|  
|<span data-ttu-id="ce5c1-244">MainMenu/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="ce5c1-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="ce5c1-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="ce5c1-245">MonthCalendar</span></span>|  
|<span data-ttu-id="ce5c1-246">Notifyıcon</span><span class="sxs-lookup"><span data-stu-id="ce5c1-246">NotifyIcon</span></span>|  
|<span data-ttu-id="ce5c1-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="ce5c1-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="ce5c1-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="ce5c1-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="ce5c1-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="ce5c1-249">PrintDialog</span></span>|  
|<span data-ttu-id="ce5c1-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="ce5c1-250">ProgressBar</span></span>|  
|<span data-ttu-id="ce5c1-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="ce5c1-251">RadioButton</span></span>|  
|<span data-ttu-id="ce5c1-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="ce5c1-252">RichTextBox</span></span>|  
|<span data-ttu-id="ce5c1-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="ce5c1-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="ce5c1-254">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="ce5c1-254">ScrollableControl</span></span>|  
|<span data-ttu-id="ce5c1-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="ce5c1-255">SoundPlayer</span></span>|  
|<span data-ttu-id="ce5c1-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="ce5c1-256">StatusBar</span></span>|  
|<span data-ttu-id="ce5c1-257">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="ce5c1-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="ce5c1-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="ce5c1-258">TextBox</span></span>|  
|<span data-ttu-id="ce5c1-259">Zamanlayıcı</span><span class="sxs-lookup"><span data-stu-id="ce5c1-259">Timer</span></span>|  
|<span data-ttu-id="ce5c1-260">Araç Çubuğu</span><span class="sxs-lookup"><span data-stu-id="ce5c1-260">Toolbar</span></span>|  
|<span data-ttu-id="ce5c1-261">ToolTip</span><span class="sxs-lookup"><span data-stu-id="ce5c1-261">ToolTip</span></span>|  
|<span data-ttu-id="ce5c1-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="ce5c1-262">TrackBar</span></span>|  
|<span data-ttu-id="ce5c1-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="ce5c1-263">TreeView</span></span>|  
|<span data-ttu-id="ce5c1-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="ce5c1-264">VscrollBar</span></span>|  
|<span data-ttu-id="ce5c1-265">WebBrowser</span><span class="sxs-lookup"><span data-stu-id="ce5c1-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="ce5c1-266">Aşağıdaki denetimler için sunulan [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] yalnızca kendi desteği aracılığıyla [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ce5c1-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span></span> <span data-ttu-id="ce5c1-267">Bazı işlevler kullanılamayabilir.</span><span class="sxs-lookup"><span data-stu-id="ce5c1-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="ce5c1-268">Denetim adı</span><span class="sxs-lookup"><span data-stu-id="ce5c1-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="ce5c1-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="ce5c1-269">BindingSource</span></span>|  
|<span data-ttu-id="ce5c1-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="ce5c1-270">DataGrid</span></span>|  
|<span data-ttu-id="ce5c1-271">DataGridView</span><span class="sxs-lookup"><span data-stu-id="ce5c1-271">DataGridView</span></span>|  
|<span data-ttu-id="ce5c1-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="ce5c1-272">DataNavigator</span></span>|  
|<span data-ttu-id="ce5c1-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="ce5c1-273">DomainUpDown</span></span>|  
|<span data-ttu-id="ce5c1-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="ce5c1-274">ErrorProvider</span></span>|  
|<span data-ttu-id="ce5c1-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="ce5c1-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="ce5c1-276">Form</span><span class="sxs-lookup"><span data-stu-id="ce5c1-276">Form</span></span>|  
|<span data-ttu-id="ce5c1-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="ce5c1-277">LinkLabel</span></span>|  
|<span data-ttu-id="ce5c1-278">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="ce5c1-278">HelpProvider</span></span>|  
|<span data-ttu-id="ce5c1-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="ce5c1-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="ce5c1-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="ce5c1-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="ce5c1-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="ce5c1-281">NumericUpDown</span></span>|  
|<span data-ttu-id="ce5c1-282">Panel</span><span class="sxs-lookup"><span data-stu-id="ce5c1-282">Panel</span></span>|  
|<span data-ttu-id="ce5c1-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="ce5c1-283">PictureBox</span></span>|  
|<span data-ttu-id="ce5c1-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="ce5c1-284">PrintDocument</span></span>|  
|<span data-ttu-id="ce5c1-285">PrintPreview denetimi</span><span class="sxs-lookup"><span data-stu-id="ce5c1-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="ce5c1-286">PrintPreview iletişim kutusu</span><span class="sxs-lookup"><span data-stu-id="ce5c1-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="ce5c1-287">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="ce5c1-287">PropertyGrid</span></span>|  
|<span data-ttu-id="ce5c1-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="ce5c1-288">UserControl</span></span>|  
|<span data-ttu-id="ce5c1-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="ce5c1-289">ToolStrip</span></span>|  
|<span data-ttu-id="ce5c1-290">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="ce5c1-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="ce5c1-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="ce5c1-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="ce5c1-292">Bölümlendirici</span><span class="sxs-lookup"><span data-stu-id="ce5c1-292">Splitter</span></span>|  
|<span data-ttu-id="ce5c1-293">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="ce5c1-293">RaftingContainer</span></span>|  
|<span data-ttu-id="ce5c1-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="ce5c1-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ce5c1-295">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ce5c1-295">See also</span></span>
- [<span data-ttu-id="ce5c1-296">UI Otomasyonu Denetim Türleri</span><span class="sxs-lookup"><span data-stu-id="ce5c1-296">UI Automation Control Types</span></span>](../../../docs/framework/ui-automation/ui-automation-control-types.md)
