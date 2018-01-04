---
title: "Standart Denetimler İçin UI Otomasyon Desteği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
caps.latest.revision: "11"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: f7529c68e96f93ebbba9fc5e750e09331bda9699
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="cc9aa-102">Standart Denetimler İçin UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="cc9aa-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
>  <span data-ttu-id="cc9aa-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="cc9aa-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="cc9aa-104">Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="cc9aa-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="cc9aa-105">Bu konu aşağıdakiler hakkında bilgi içerir [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] standart denetimleri için geliştirilen uygulamaları için destek [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], ve [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] çerçeveleri.</span><span class="sxs-lookup"><span data-stu-id="cc9aa-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="cc9aa-106">Windows Presentation Foundation denetimleri</span><span class="sxs-lookup"><span data-stu-id="cc9aa-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="cc9aa-107">Tüm [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] bilgi veya destek sağlamak için kullanıcı etkileşimi denetim öğelerine sahip yönelik tam destek [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cc9aa-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="cc9aa-108">Paneller gibi diğer öğeler için görünür değildir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cc9aa-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="cc9aa-109">Win32 denetimleri</span><span class="sxs-lookup"><span data-stu-id="cc9aa-109">Win32 Controls</span></span>  
 <span data-ttu-id="cc9aa-110">Çoğu [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] denetimleri için açığa [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] UIAutomationClientsideProviders.dll istemci tarafı sağlayıcı üzerinden.</span><span class="sxs-lookup"><span data-stu-id="cc9aa-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="cc9aa-111">Bu derleme UI otomasyon istemci uygulamaları ile kullanmak için otomatik olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="cc9aa-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="cc9aa-112">Yalnızca ComCtrl32.dll 6 sürümünden denetimleri için tam destek sağlanır (bulunan [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] ve üzeri).</span><span class="sxs-lookup"><span data-stu-id="cc9aa-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span></span>  
  
 <span data-ttu-id="cc9aa-113">Aşağıdaki denetimleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="cc9aa-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="cc9aa-114">Sınıf adı</span><span class="sxs-lookup"><span data-stu-id="cc9aa-114">Class name</span></span>|<span data-ttu-id="cc9aa-115">Denetim türü</span><span class="sxs-lookup"><span data-stu-id="cc9aa-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="cc9aa-116">Düğme</span><span class="sxs-lookup"><span data-stu-id="cc9aa-116">Button</span></span>|<span data-ttu-id="cc9aa-117">Düğme</span><span class="sxs-lookup"><span data-stu-id="cc9aa-117">Button</span></span>|  
|<span data-ttu-id="cc9aa-118">Düğme</span><span class="sxs-lookup"><span data-stu-id="cc9aa-118">Button</span></span>|<span data-ttu-id="cc9aa-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="cc9aa-119">RadioButton</span></span>|  
|<span data-ttu-id="cc9aa-120">Düğme</span><span class="sxs-lookup"><span data-stu-id="cc9aa-120">Button</span></span>|<span data-ttu-id="cc9aa-121">Grup</span><span class="sxs-lookup"><span data-stu-id="cc9aa-121">Group</span></span>|  
|<span data-ttu-id="cc9aa-122">Düğme</span><span class="sxs-lookup"><span data-stu-id="cc9aa-122">Button</span></span>|<span data-ttu-id="cc9aa-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="cc9aa-123">CheckBox</span></span>|  
|<span data-ttu-id="cc9aa-124">Düğme</span><span class="sxs-lookup"><span data-stu-id="cc9aa-124">Button</span></span>|<span data-ttu-id="cc9aa-125">Köprü</span><span class="sxs-lookup"><span data-stu-id="cc9aa-125">Hyperlink</span></span>|  
|<span data-ttu-id="cc9aa-126">Düğme</span><span class="sxs-lookup"><span data-stu-id="cc9aa-126">Button</span></span>|<span data-ttu-id="cc9aa-127">Bölünmüş düğme</span><span class="sxs-lookup"><span data-stu-id="cc9aa-127">SplitButton</span></span>|  
|<span data-ttu-id="cc9aa-128">Düğme</span><span class="sxs-lookup"><span data-stu-id="cc9aa-128">Button</span></span>|<span data-ttu-id="cc9aa-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="cc9aa-129">CheckBox</span></span>|  
|<span data-ttu-id="cc9aa-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="cc9aa-130">ComboBoxEx32</span></span>|<span data-ttu-id="cc9aa-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="cc9aa-131">ComboBox</span></span>|  
|<span data-ttu-id="cc9aa-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="cc9aa-132">ComboBox</span></span>|<span data-ttu-id="cc9aa-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="cc9aa-133">ComboBox</span></span>|  
|<span data-ttu-id="cc9aa-134">Düzenle</span><span class="sxs-lookup"><span data-stu-id="cc9aa-134">Edit</span></span>|<span data-ttu-id="cc9aa-135">Belge</span><span class="sxs-lookup"><span data-stu-id="cc9aa-135">Document</span></span>|  
|<span data-ttu-id="cc9aa-136">Düzenle</span><span class="sxs-lookup"><span data-stu-id="cc9aa-136">Edit</span></span>|<span data-ttu-id="cc9aa-137">Düzenle</span><span class="sxs-lookup"><span data-stu-id="cc9aa-137">Edit</span></span>|  
|<span data-ttu-id="cc9aa-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="cc9aa-138">SysLink</span></span>|<span data-ttu-id="cc9aa-139">Köprü</span><span class="sxs-lookup"><span data-stu-id="cc9aa-139">Hyperlink</span></span>|  
|<span data-ttu-id="cc9aa-140">Statik</span><span class="sxs-lookup"><span data-stu-id="cc9aa-140">Static</span></span>|<span data-ttu-id="cc9aa-141">Metin</span><span class="sxs-lookup"><span data-stu-id="cc9aa-141">Text</span></span>|  
|<span data-ttu-id="cc9aa-142">Statik</span><span class="sxs-lookup"><span data-stu-id="cc9aa-142">Static</span></span>|<span data-ttu-id="cc9aa-143">Görüntü</span><span class="sxs-lookup"><span data-stu-id="cc9aa-143">Image</span></span>|  
|<span data-ttu-id="cc9aa-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="cc9aa-144">SysIPAddress32</span></span>|<span data-ttu-id="cc9aa-145">Özel</span><span class="sxs-lookup"><span data-stu-id="cc9aa-145">Custom</span></span>|  
|<span data-ttu-id="cc9aa-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="cc9aa-146">SysHeader32</span></span>|<span data-ttu-id="cc9aa-147">Üstbilgi/Headerıtem</span><span class="sxs-lookup"><span data-stu-id="cc9aa-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="cc9aa-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="cc9aa-148">SysListView32</span></span>|<span data-ttu-id="cc9aa-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="cc9aa-149">DataGrid</span></span>|  
|<span data-ttu-id="cc9aa-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="cc9aa-150">SysListView32</span></span>|<span data-ttu-id="cc9aa-151">List</span><span class="sxs-lookup"><span data-stu-id="cc9aa-151">List</span></span>|  
|<span data-ttu-id="cc9aa-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="cc9aa-152">ListBox</span></span>|<span data-ttu-id="cc9aa-153">List</span><span class="sxs-lookup"><span data-stu-id="cc9aa-153">List</span></span>|  
|<span data-ttu-id="cc9aa-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="cc9aa-154">ListBox</span></span>|<span data-ttu-id="cc9aa-155">ListItem</span><span class="sxs-lookup"><span data-stu-id="cc9aa-155">ListItem</span></span>|  
|<span data-ttu-id="cc9aa-156">#32768</span><span class="sxs-lookup"><span data-stu-id="cc9aa-156">#32768</span></span>|<span data-ttu-id="cc9aa-157">Menü</span><span class="sxs-lookup"><span data-stu-id="cc9aa-157">Menu</span></span>|  
|<span data-ttu-id="cc9aa-158">#32768</span><span class="sxs-lookup"><span data-stu-id="cc9aa-158">#32768</span></span>|<span data-ttu-id="cc9aa-159">MenuItem</span><span class="sxs-lookup"><span data-stu-id="cc9aa-159">MenuItem</span></span>|  
|<span data-ttu-id="cc9aa-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="cc9aa-160">msctls_progress32</span></span>|<span data-ttu-id="cc9aa-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="cc9aa-161">ProgressBar</span></span>|  
|<span data-ttu-id="cc9aa-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="cc9aa-162">RichEdit</span></span>|<span data-ttu-id="cc9aa-163">Belge.</span><span class="sxs-lookup"><span data-stu-id="cc9aa-163">Document.</span></span> <span data-ttu-id="cc9aa-164">Nota bakın.</span><span class="sxs-lookup"><span data-stu-id="cc9aa-164">See note.</span></span>|  
|<span data-ttu-id="cc9aa-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="cc9aa-165">RichEdit20A</span></span>|<span data-ttu-id="cc9aa-166">Belge</span><span class="sxs-lookup"><span data-stu-id="cc9aa-166">Document</span></span>|  
|<span data-ttu-id="cc9aa-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="cc9aa-167">RichEdit20W</span></span>|<span data-ttu-id="cc9aa-168">Belge</span><span class="sxs-lookup"><span data-stu-id="cc9aa-168">Document</span></span>|  
|<span data-ttu-id="cc9aa-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="cc9aa-169">RichEdit50W</span></span>|<span data-ttu-id="cc9aa-170">Belge</span><span class="sxs-lookup"><span data-stu-id="cc9aa-170">Document</span></span>|  
|<span data-ttu-id="cc9aa-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="cc9aa-171">ScrollBar</span></span>|<span data-ttu-id="cc9aa-172">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="cc9aa-172">Slider</span></span>|  
|<span data-ttu-id="cc9aa-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="cc9aa-173">msctls_trackbar32</span></span>|<span data-ttu-id="cc9aa-174">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="cc9aa-174">Slider</span></span>|  
|<span data-ttu-id="cc9aa-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="cc9aa-175">msctls_updown32</span></span>|<span data-ttu-id="cc9aa-176">Değer Değiştirici</span><span class="sxs-lookup"><span data-stu-id="cc9aa-176">Spinner</span></span>|  
|<span data-ttu-id="cc9aa-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="cc9aa-177">msctls_statusbar32</span></span>|<span data-ttu-id="cc9aa-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="cc9aa-178">StatusBar</span></span>|  
|<span data-ttu-id="cc9aa-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="cc9aa-179">SysTabControl32</span></span>|<span data-ttu-id="cc9aa-180">Tab</span><span class="sxs-lookup"><span data-stu-id="cc9aa-180">Tab</span></span>|  
|<span data-ttu-id="cc9aa-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="cc9aa-181">SysTabControl32</span></span>|<span data-ttu-id="cc9aa-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="cc9aa-182">TabItem</span></span>|  
|<span data-ttu-id="cc9aa-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="cc9aa-183">ToolbarWindow32</span></span>|<span data-ttu-id="cc9aa-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="cc9aa-184">ToolBar</span></span>|  
|<span data-ttu-id="cc9aa-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="cc9aa-185">ToolbarWindow32</span></span>|<span data-ttu-id="cc9aa-186">MenuItem</span><span class="sxs-lookup"><span data-stu-id="cc9aa-186">MenuItem</span></span>|  
|<span data-ttu-id="cc9aa-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="cc9aa-187">ToolbarWindow32</span></span>|<span data-ttu-id="cc9aa-188">Düğme</span><span class="sxs-lookup"><span data-stu-id="cc9aa-188">Button</span></span>|  
|<span data-ttu-id="cc9aa-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="cc9aa-189">ToolbarWindow32</span></span>|<span data-ttu-id="cc9aa-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="cc9aa-190">CheckBox</span></span>|  
|<span data-ttu-id="cc9aa-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="cc9aa-191">ToolbarWindow32</span></span>|<span data-ttu-id="cc9aa-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="cc9aa-192">RadioButton</span></span>|  
|<span data-ttu-id="cc9aa-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="cc9aa-193">ToolbarWindow32</span></span>|<span data-ttu-id="cc9aa-194">Ayırıcı</span><span class="sxs-lookup"><span data-stu-id="cc9aa-194">Separator</span></span>|  
|<span data-ttu-id="cc9aa-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="cc9aa-195">tooltips_class32</span></span>|<span data-ttu-id="cc9aa-196">ToolTip</span><span class="sxs-lookup"><span data-stu-id="cc9aa-196">ToolTip</span></span>|  
|<span data-ttu-id="cc9aa-197">#32774</span><span class="sxs-lookup"><span data-stu-id="cc9aa-197">#32774</span></span>|<span data-ttu-id="cc9aa-198">ToolTip</span><span class="sxs-lookup"><span data-stu-id="cc9aa-198">ToolTip</span></span>|  
|<span data-ttu-id="cc9aa-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="cc9aa-199">ReBarWindow32</span></span>|<span data-ttu-id="cc9aa-200">Araç Çubuğu</span><span class="sxs-lookup"><span data-stu-id="cc9aa-200">Toolbar</span></span>|  
|<span data-ttu-id="cc9aa-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="cc9aa-201">SysTreeView32</span></span>|<span data-ttu-id="cc9aa-202">Ağaç</span><span class="sxs-lookup"><span data-stu-id="cc9aa-202">Tree</span></span>|  
|<span data-ttu-id="cc9aa-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="cc9aa-203">SysTreeView32</span></span>|<span data-ttu-id="cc9aa-204">Treeıtem</span><span class="sxs-lookup"><span data-stu-id="cc9aa-204">TreeItem</span></span>|  
  
 <span data-ttu-id="cc9aa-205">**Not** RichEdit denetimi yalnızca sürümleri ile birlikte gelen için desteklenen [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (içinde RichEd20.dll sürüm 3.1 ve sonrası ve MsftEdit.dll sürümü 4.1 ve üzeri).</span><span class="sxs-lookup"><span data-stu-id="cc9aa-205">**Note** The RichEdit control is supported only for versions shipped with [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="cc9aa-206">Aşağıdaki denetimleri desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="cc9aa-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="cc9aa-207">Sınıf adı</span><span class="sxs-lookup"><span data-stu-id="cc9aa-207">Class name</span></span>|<span data-ttu-id="cc9aa-208">Denetim türü</span><span class="sxs-lookup"><span data-stu-id="cc9aa-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="cc9aa-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="cc9aa-209">SysAnimate32</span></span>|<span data-ttu-id="cc9aa-210">Görüntü</span><span class="sxs-lookup"><span data-stu-id="cc9aa-210">Image</span></span>|  
|<span data-ttu-id="cc9aa-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="cc9aa-211">SysPager</span></span>|<span data-ttu-id="cc9aa-212">Değer Değiştirici</span><span class="sxs-lookup"><span data-stu-id="cc9aa-212">Spinner</span></span>|  
|<span data-ttu-id="cc9aa-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="cc9aa-213">SysDateTimePick32</span></span>|<span data-ttu-id="cc9aa-214">Özel</span><span class="sxs-lookup"><span data-stu-id="cc9aa-214">Custom</span></span>|  
|<span data-ttu-id="cc9aa-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="cc9aa-215">SysMonthCal32</span></span>|<span data-ttu-id="cc9aa-216">Takvim</span><span class="sxs-lookup"><span data-stu-id="cc9aa-216">Calendar</span></span>|  
|<span data-ttu-id="cc9aa-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="cc9aa-217">MS_WINNOTE</span></span>|<span data-ttu-id="cc9aa-218">Araç İpucu</span><span class="sxs-lookup"><span data-stu-id="cc9aa-218">Tooltip</span></span>|  
|<span data-ttu-id="cc9aa-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="cc9aa-219">VBBubble</span></span>|<span data-ttu-id="cc9aa-220">Araç İpucu</span><span class="sxs-lookup"><span data-stu-id="cc9aa-220">Tooltip</span></span>|  
|<span data-ttu-id="cc9aa-221">(Tek başına denetimi olarak kullanıldığında) kaydırma çubuğu</span><span class="sxs-lookup"><span data-stu-id="cc9aa-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="cc9aa-222">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="cc9aa-222">Slider</span></span>|  
|<span data-ttu-id="cc9aa-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="cc9aa-223">SuperGrid</span></span>|<span data-ttu-id="cc9aa-224">Özel</span><span class="sxs-lookup"><span data-stu-id="cc9aa-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="cc9aa-225">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="cc9aa-225">Windows Forms Controls</span></span>  
 [!INCLUDE[TLA2#tla_winforms](../../../includes/tla2sharptla-winforms-md.md)]<span data-ttu-id="cc9aa-226">denetimler için açığa [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] UIAutomationClientsideProviders.dll istemci tarafı sağlayıcı üzerinden.</span><span class="sxs-lookup"><span data-stu-id="cc9aa-226"> controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="cc9aa-227">Bu derleme UI otomasyon istemci uygulamaları ile kullanmak için otomatik olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="cc9aa-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="cc9aa-228">Genellikle, [!INCLUDE[TLA2#tla_winforms](../../../includes/tla2sharptla-winforms-md.md)] denetimleri için sarmalayıcıları yönetilen [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] tarafından desteklenen ortak denetimleri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cc9aa-228">Typically, [!INCLUDE[TLA2#tla_winforms](../../../includes/tla2sharptla-winforms-md.md)] controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="cc9aa-229">Aşağıdaki denetimleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="cc9aa-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="cc9aa-230">Sınıf Adı</span><span class="sxs-lookup"><span data-stu-id="cc9aa-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="cc9aa-231">Düğme</span><span class="sxs-lookup"><span data-stu-id="cc9aa-231">Button</span></span>|  
|<span data-ttu-id="cc9aa-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="cc9aa-232">CheckBox</span></span>|  
|<span data-ttu-id="cc9aa-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="cc9aa-233">CheckedListBox</span></span>|  
|<span data-ttu-id="cc9aa-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="cc9aa-234">ColorDialog</span></span>|  
|<span data-ttu-id="cc9aa-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="cc9aa-235">ComboBox</span></span>|  
|<span data-ttu-id="cc9aa-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="cc9aa-236">FolderBrowser</span></span>|  
|<span data-ttu-id="cc9aa-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="cc9aa-237">FontDialog</span></span>|  
|<span data-ttu-id="cc9aa-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="cc9aa-238">GroupBox</span></span>|  
|<span data-ttu-id="cc9aa-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="cc9aa-239">HscrollBar</span></span>|  
|<span data-ttu-id="cc9aa-240">ImageList</span><span class="sxs-lookup"><span data-stu-id="cc9aa-240">ImageList</span></span>|  
|<span data-ttu-id="cc9aa-241">Etiketle</span><span class="sxs-lookup"><span data-stu-id="cc9aa-241">Label</span></span>|  
|<span data-ttu-id="cc9aa-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="cc9aa-242">ListBox</span></span>|  
|<span data-ttu-id="cc9aa-243">ListView</span><span class="sxs-lookup"><span data-stu-id="cc9aa-243">ListView</span></span>|  
|<span data-ttu-id="cc9aa-244">MainMenu/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="cc9aa-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="cc9aa-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="cc9aa-245">MonthCalendar</span></span>|  
|<span data-ttu-id="cc9aa-246">Notifyıcon</span><span class="sxs-lookup"><span data-stu-id="cc9aa-246">NotifyIcon</span></span>|  
|<span data-ttu-id="cc9aa-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="cc9aa-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="cc9aa-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="cc9aa-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="cc9aa-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="cc9aa-249">PrintDialog</span></span>|  
|<span data-ttu-id="cc9aa-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="cc9aa-250">ProgressBar</span></span>|  
|<span data-ttu-id="cc9aa-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="cc9aa-251">RadioButton</span></span>|  
|<span data-ttu-id="cc9aa-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="cc9aa-252">RichTextBox</span></span>|  
|<span data-ttu-id="cc9aa-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="cc9aa-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="cc9aa-254">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="cc9aa-254">ScrollableControl</span></span>|  
|<span data-ttu-id="cc9aa-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="cc9aa-255">SoundPlayer</span></span>|  
|<span data-ttu-id="cc9aa-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="cc9aa-256">StatusBar</span></span>|  
|<span data-ttu-id="cc9aa-257">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="cc9aa-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="cc9aa-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="cc9aa-258">TextBox</span></span>|  
|<span data-ttu-id="cc9aa-259">Zamanlayıcı</span><span class="sxs-lookup"><span data-stu-id="cc9aa-259">Timer</span></span>|  
|<span data-ttu-id="cc9aa-260">Araç Çubuğu</span><span class="sxs-lookup"><span data-stu-id="cc9aa-260">Toolbar</span></span>|  
|<span data-ttu-id="cc9aa-261">ToolTip</span><span class="sxs-lookup"><span data-stu-id="cc9aa-261">ToolTip</span></span>|  
|<span data-ttu-id="cc9aa-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="cc9aa-262">TrackBar</span></span>|  
|<span data-ttu-id="cc9aa-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="cc9aa-263">TreeView</span></span>|  
|<span data-ttu-id="cc9aa-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="cc9aa-264">VscrollBar</span></span>|  
|<span data-ttu-id="cc9aa-265">WebBrowser</span><span class="sxs-lookup"><span data-stu-id="cc9aa-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="cc9aa-266">Aşağıdaki denetimleri sunulur [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] yalnızca kendi desteği aracılığıyla [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cc9aa-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span></span> <span data-ttu-id="cc9aa-267">Bazı işlevler kullanılamayabilir.</span><span class="sxs-lookup"><span data-stu-id="cc9aa-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="cc9aa-268">Denetim adı</span><span class="sxs-lookup"><span data-stu-id="cc9aa-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="cc9aa-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="cc9aa-269">BindingSource</span></span>|  
|<span data-ttu-id="cc9aa-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="cc9aa-270">DataGrid</span></span>|  
|<span data-ttu-id="cc9aa-271">DataGridView</span><span class="sxs-lookup"><span data-stu-id="cc9aa-271">DataGridView</span></span>|  
|<span data-ttu-id="cc9aa-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="cc9aa-272">DataNavigator</span></span>|  
|<span data-ttu-id="cc9aa-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="cc9aa-273">DomainUpDown</span></span>|  
|<span data-ttu-id="cc9aa-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="cc9aa-274">ErrorProvider</span></span>|  
|<span data-ttu-id="cc9aa-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="cc9aa-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="cc9aa-276">Form</span><span class="sxs-lookup"><span data-stu-id="cc9aa-276">Form</span></span>|  
|<span data-ttu-id="cc9aa-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="cc9aa-277">LinkLabel</span></span>|  
|<span data-ttu-id="cc9aa-278">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="cc9aa-278">HelpProvider</span></span>|  
|<span data-ttu-id="cc9aa-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="cc9aa-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="cc9aa-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="cc9aa-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="cc9aa-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="cc9aa-281">NumericUpDown</span></span>|  
|<span data-ttu-id="cc9aa-282">Panel</span><span class="sxs-lookup"><span data-stu-id="cc9aa-282">Panel</span></span>|  
|<span data-ttu-id="cc9aa-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="cc9aa-283">PictureBox</span></span>|  
|<span data-ttu-id="cc9aa-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="cc9aa-284">PrintDocument</span></span>|  
|<span data-ttu-id="cc9aa-285">PrintPreview denetimi</span><span class="sxs-lookup"><span data-stu-id="cc9aa-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="cc9aa-286">PrintPreview iletişim kutusu</span><span class="sxs-lookup"><span data-stu-id="cc9aa-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="cc9aa-287">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="cc9aa-287">PropertyGrid</span></span>|  
|<span data-ttu-id="cc9aa-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="cc9aa-288">UserControl</span></span>|  
|<span data-ttu-id="cc9aa-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="cc9aa-289">ToolStrip</span></span>|  
|<span data-ttu-id="cc9aa-290">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="cc9aa-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="cc9aa-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="cc9aa-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="cc9aa-292">Bölümlendirici</span><span class="sxs-lookup"><span data-stu-id="cc9aa-292">Splitter</span></span>|  
|<span data-ttu-id="cc9aa-293">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="cc9aa-293">RaftingContainer</span></span>|  
|<span data-ttu-id="cc9aa-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="cc9aa-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cc9aa-295">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cc9aa-295">See Also</span></span>  
 [<span data-ttu-id="cc9aa-296">UI Otomasyonu Denetim Türleri</span><span class="sxs-lookup"><span data-stu-id="cc9aa-296">UI Automation Control Types</span></span>](../../../docs/framework/ui-automation/ui-automation-control-types.md)
