---
title: Standart Denetimler İçin UI Otomasyon Desteği
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
caps.latest.revision: 11
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: af46a984f1b4c2577daee120752590ff18b9d1d8
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="25cb9-102">Standart Denetimler İçin UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="25cb9-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
>  <span data-ttu-id="25cb9-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="25cb9-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="25cb9-104">Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="25cb9-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="25cb9-105">Bu konu aşağıdakiler hakkında bilgi içerir [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] standart denetimleri için geliştirilen uygulamaları için destek [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], ve [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] çerçeveleri.</span><span class="sxs-lookup"><span data-stu-id="25cb9-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="25cb9-106">Windows Presentation Foundation denetimleri</span><span class="sxs-lookup"><span data-stu-id="25cb9-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="25cb9-107">Tüm [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] bilgi veya destek sağlamak için kullanıcı etkileşimi denetim öğelerine sahip yönelik tam destek [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="25cb9-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="25cb9-108">Paneller gibi diğer öğeler için görünür değildir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="25cb9-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="25cb9-109">Win32 denetimleri</span><span class="sxs-lookup"><span data-stu-id="25cb9-109">Win32 Controls</span></span>  
 <span data-ttu-id="25cb9-110">Çoğu [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] denetimleri için açığa [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] UIAutomationClientsideProviders.dll istemci tarafı sağlayıcı üzerinden.</span><span class="sxs-lookup"><span data-stu-id="25cb9-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="25cb9-111">Bu derleme UI otomasyon istemci uygulamaları ile kullanmak için otomatik olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="25cb9-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="25cb9-112">Yalnızca ComCtrl32.dll 6 sürümünden denetimleri için tam destek sağlanır (bulunan [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] ve üzeri).</span><span class="sxs-lookup"><span data-stu-id="25cb9-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span></span>  
  
 <span data-ttu-id="25cb9-113">Aşağıdaki denetimleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="25cb9-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="25cb9-114">Sınıf adı</span><span class="sxs-lookup"><span data-stu-id="25cb9-114">Class name</span></span>|<span data-ttu-id="25cb9-115">Denetim türü</span><span class="sxs-lookup"><span data-stu-id="25cb9-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="25cb9-116">Düğme</span><span class="sxs-lookup"><span data-stu-id="25cb9-116">Button</span></span>|<span data-ttu-id="25cb9-117">Düğme</span><span class="sxs-lookup"><span data-stu-id="25cb9-117">Button</span></span>|  
|<span data-ttu-id="25cb9-118">Düğme</span><span class="sxs-lookup"><span data-stu-id="25cb9-118">Button</span></span>|<span data-ttu-id="25cb9-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="25cb9-119">RadioButton</span></span>|  
|<span data-ttu-id="25cb9-120">Düğme</span><span class="sxs-lookup"><span data-stu-id="25cb9-120">Button</span></span>|<span data-ttu-id="25cb9-121">Grup</span><span class="sxs-lookup"><span data-stu-id="25cb9-121">Group</span></span>|  
|<span data-ttu-id="25cb9-122">Düğme</span><span class="sxs-lookup"><span data-stu-id="25cb9-122">Button</span></span>|<span data-ttu-id="25cb9-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="25cb9-123">CheckBox</span></span>|  
|<span data-ttu-id="25cb9-124">Düğme</span><span class="sxs-lookup"><span data-stu-id="25cb9-124">Button</span></span>|<span data-ttu-id="25cb9-125">Köprü</span><span class="sxs-lookup"><span data-stu-id="25cb9-125">Hyperlink</span></span>|  
|<span data-ttu-id="25cb9-126">Düğme</span><span class="sxs-lookup"><span data-stu-id="25cb9-126">Button</span></span>|<span data-ttu-id="25cb9-127">Bölünmüş düğme</span><span class="sxs-lookup"><span data-stu-id="25cb9-127">SplitButton</span></span>|  
|<span data-ttu-id="25cb9-128">Düğme</span><span class="sxs-lookup"><span data-stu-id="25cb9-128">Button</span></span>|<span data-ttu-id="25cb9-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="25cb9-129">CheckBox</span></span>|  
|<span data-ttu-id="25cb9-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="25cb9-130">ComboBoxEx32</span></span>|<span data-ttu-id="25cb9-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="25cb9-131">ComboBox</span></span>|  
|<span data-ttu-id="25cb9-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="25cb9-132">ComboBox</span></span>|<span data-ttu-id="25cb9-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="25cb9-133">ComboBox</span></span>|  
|<span data-ttu-id="25cb9-134">Düzenle</span><span class="sxs-lookup"><span data-stu-id="25cb9-134">Edit</span></span>|<span data-ttu-id="25cb9-135">Belge</span><span class="sxs-lookup"><span data-stu-id="25cb9-135">Document</span></span>|  
|<span data-ttu-id="25cb9-136">Düzenle</span><span class="sxs-lookup"><span data-stu-id="25cb9-136">Edit</span></span>|<span data-ttu-id="25cb9-137">Düzenle</span><span class="sxs-lookup"><span data-stu-id="25cb9-137">Edit</span></span>|  
|<span data-ttu-id="25cb9-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="25cb9-138">SysLink</span></span>|<span data-ttu-id="25cb9-139">Köprü</span><span class="sxs-lookup"><span data-stu-id="25cb9-139">Hyperlink</span></span>|  
|<span data-ttu-id="25cb9-140">Statik</span><span class="sxs-lookup"><span data-stu-id="25cb9-140">Static</span></span>|<span data-ttu-id="25cb9-141">Metin</span><span class="sxs-lookup"><span data-stu-id="25cb9-141">Text</span></span>|  
|<span data-ttu-id="25cb9-142">Statik</span><span class="sxs-lookup"><span data-stu-id="25cb9-142">Static</span></span>|<span data-ttu-id="25cb9-143">Görüntü</span><span class="sxs-lookup"><span data-stu-id="25cb9-143">Image</span></span>|  
|<span data-ttu-id="25cb9-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="25cb9-144">SysIPAddress32</span></span>|<span data-ttu-id="25cb9-145">Özel</span><span class="sxs-lookup"><span data-stu-id="25cb9-145">Custom</span></span>|  
|<span data-ttu-id="25cb9-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="25cb9-146">SysHeader32</span></span>|<span data-ttu-id="25cb9-147">Üstbilgi/Headerıtem</span><span class="sxs-lookup"><span data-stu-id="25cb9-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="25cb9-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="25cb9-148">SysListView32</span></span>|<span data-ttu-id="25cb9-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="25cb9-149">DataGrid</span></span>|  
|<span data-ttu-id="25cb9-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="25cb9-150">SysListView32</span></span>|<span data-ttu-id="25cb9-151">List</span><span class="sxs-lookup"><span data-stu-id="25cb9-151">List</span></span>|  
|<span data-ttu-id="25cb9-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="25cb9-152">ListBox</span></span>|<span data-ttu-id="25cb9-153">List</span><span class="sxs-lookup"><span data-stu-id="25cb9-153">List</span></span>|  
|<span data-ttu-id="25cb9-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="25cb9-154">ListBox</span></span>|<span data-ttu-id="25cb9-155">ListItem</span><span class="sxs-lookup"><span data-stu-id="25cb9-155">ListItem</span></span>|  
|<span data-ttu-id="25cb9-156">#32768</span><span class="sxs-lookup"><span data-stu-id="25cb9-156">#32768</span></span>|<span data-ttu-id="25cb9-157">Menü</span><span class="sxs-lookup"><span data-stu-id="25cb9-157">Menu</span></span>|  
|<span data-ttu-id="25cb9-158">#32768</span><span class="sxs-lookup"><span data-stu-id="25cb9-158">#32768</span></span>|<span data-ttu-id="25cb9-159">MenuItem</span><span class="sxs-lookup"><span data-stu-id="25cb9-159">MenuItem</span></span>|  
|<span data-ttu-id="25cb9-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="25cb9-160">msctls_progress32</span></span>|<span data-ttu-id="25cb9-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="25cb9-161">ProgressBar</span></span>|  
|<span data-ttu-id="25cb9-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="25cb9-162">RichEdit</span></span>|<span data-ttu-id="25cb9-163">Belge.</span><span class="sxs-lookup"><span data-stu-id="25cb9-163">Document.</span></span> <span data-ttu-id="25cb9-164">Nota bakın.</span><span class="sxs-lookup"><span data-stu-id="25cb9-164">See note.</span></span>|  
|<span data-ttu-id="25cb9-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="25cb9-165">RichEdit20A</span></span>|<span data-ttu-id="25cb9-166">Belge</span><span class="sxs-lookup"><span data-stu-id="25cb9-166">Document</span></span>|  
|<span data-ttu-id="25cb9-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="25cb9-167">RichEdit20W</span></span>|<span data-ttu-id="25cb9-168">Belge</span><span class="sxs-lookup"><span data-stu-id="25cb9-168">Document</span></span>|  
|<span data-ttu-id="25cb9-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="25cb9-169">RichEdit50W</span></span>|<span data-ttu-id="25cb9-170">Belge</span><span class="sxs-lookup"><span data-stu-id="25cb9-170">Document</span></span>|  
|<span data-ttu-id="25cb9-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="25cb9-171">ScrollBar</span></span>|<span data-ttu-id="25cb9-172">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="25cb9-172">Slider</span></span>|  
|<span data-ttu-id="25cb9-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="25cb9-173">msctls_trackbar32</span></span>|<span data-ttu-id="25cb9-174">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="25cb9-174">Slider</span></span>|  
|<span data-ttu-id="25cb9-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="25cb9-175">msctls_updown32</span></span>|<span data-ttu-id="25cb9-176">Değer Değiştirici</span><span class="sxs-lookup"><span data-stu-id="25cb9-176">Spinner</span></span>|  
|<span data-ttu-id="25cb9-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="25cb9-177">msctls_statusbar32</span></span>|<span data-ttu-id="25cb9-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="25cb9-178">StatusBar</span></span>|  
|<span data-ttu-id="25cb9-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="25cb9-179">SysTabControl32</span></span>|<span data-ttu-id="25cb9-180">Tab</span><span class="sxs-lookup"><span data-stu-id="25cb9-180">Tab</span></span>|  
|<span data-ttu-id="25cb9-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="25cb9-181">SysTabControl32</span></span>|<span data-ttu-id="25cb9-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="25cb9-182">TabItem</span></span>|  
|<span data-ttu-id="25cb9-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="25cb9-183">ToolbarWindow32</span></span>|<span data-ttu-id="25cb9-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="25cb9-184">ToolBar</span></span>|  
|<span data-ttu-id="25cb9-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="25cb9-185">ToolbarWindow32</span></span>|<span data-ttu-id="25cb9-186">MenuItem</span><span class="sxs-lookup"><span data-stu-id="25cb9-186">MenuItem</span></span>|  
|<span data-ttu-id="25cb9-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="25cb9-187">ToolbarWindow32</span></span>|<span data-ttu-id="25cb9-188">Düğme</span><span class="sxs-lookup"><span data-stu-id="25cb9-188">Button</span></span>|  
|<span data-ttu-id="25cb9-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="25cb9-189">ToolbarWindow32</span></span>|<span data-ttu-id="25cb9-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="25cb9-190">CheckBox</span></span>|  
|<span data-ttu-id="25cb9-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="25cb9-191">ToolbarWindow32</span></span>|<span data-ttu-id="25cb9-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="25cb9-192">RadioButton</span></span>|  
|<span data-ttu-id="25cb9-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="25cb9-193">ToolbarWindow32</span></span>|<span data-ttu-id="25cb9-194">Ayırıcı</span><span class="sxs-lookup"><span data-stu-id="25cb9-194">Separator</span></span>|  
|<span data-ttu-id="25cb9-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="25cb9-195">tooltips_class32</span></span>|<span data-ttu-id="25cb9-196">ToolTip</span><span class="sxs-lookup"><span data-stu-id="25cb9-196">ToolTip</span></span>|  
|<span data-ttu-id="25cb9-197">#32774</span><span class="sxs-lookup"><span data-stu-id="25cb9-197">#32774</span></span>|<span data-ttu-id="25cb9-198">ToolTip</span><span class="sxs-lookup"><span data-stu-id="25cb9-198">ToolTip</span></span>|  
|<span data-ttu-id="25cb9-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="25cb9-199">ReBarWindow32</span></span>|<span data-ttu-id="25cb9-200">Araç Çubuğu</span><span class="sxs-lookup"><span data-stu-id="25cb9-200">Toolbar</span></span>|  
|<span data-ttu-id="25cb9-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="25cb9-201">SysTreeView32</span></span>|<span data-ttu-id="25cb9-202">Ağaç</span><span class="sxs-lookup"><span data-stu-id="25cb9-202">Tree</span></span>|  
|<span data-ttu-id="25cb9-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="25cb9-203">SysTreeView32</span></span>|<span data-ttu-id="25cb9-204">Treeıtem</span><span class="sxs-lookup"><span data-stu-id="25cb9-204">TreeItem</span></span>|  
  
 <span data-ttu-id="25cb9-205">**Not** RichEdit denetimi yalnızca sürümleri ile birlikte gelen için desteklenen [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (içinde RichEd20.dll sürüm 3.1 ve sonrası ve MsftEdit.dll sürümü 4.1 ve üzeri).</span><span class="sxs-lookup"><span data-stu-id="25cb9-205">**Note** The RichEdit control is supported only for versions shipped with [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="25cb9-206">Aşağıdaki denetimleri desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="25cb9-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="25cb9-207">Sınıf adı</span><span class="sxs-lookup"><span data-stu-id="25cb9-207">Class name</span></span>|<span data-ttu-id="25cb9-208">Denetim türü</span><span class="sxs-lookup"><span data-stu-id="25cb9-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="25cb9-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="25cb9-209">SysAnimate32</span></span>|<span data-ttu-id="25cb9-210">Görüntü</span><span class="sxs-lookup"><span data-stu-id="25cb9-210">Image</span></span>|  
|<span data-ttu-id="25cb9-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="25cb9-211">SysPager</span></span>|<span data-ttu-id="25cb9-212">Değer Değiştirici</span><span class="sxs-lookup"><span data-stu-id="25cb9-212">Spinner</span></span>|  
|<span data-ttu-id="25cb9-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="25cb9-213">SysDateTimePick32</span></span>|<span data-ttu-id="25cb9-214">Özel</span><span class="sxs-lookup"><span data-stu-id="25cb9-214">Custom</span></span>|  
|<span data-ttu-id="25cb9-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="25cb9-215">SysMonthCal32</span></span>|<span data-ttu-id="25cb9-216">Takvim</span><span class="sxs-lookup"><span data-stu-id="25cb9-216">Calendar</span></span>|  
|<span data-ttu-id="25cb9-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="25cb9-217">MS_WINNOTE</span></span>|<span data-ttu-id="25cb9-218">Araç İpucu</span><span class="sxs-lookup"><span data-stu-id="25cb9-218">Tooltip</span></span>|  
|<span data-ttu-id="25cb9-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="25cb9-219">VBBubble</span></span>|<span data-ttu-id="25cb9-220">Araç İpucu</span><span class="sxs-lookup"><span data-stu-id="25cb9-220">Tooltip</span></span>|  
|<span data-ttu-id="25cb9-221">(Tek başına denetimi olarak kullanıldığında) kaydırma çubuğu</span><span class="sxs-lookup"><span data-stu-id="25cb9-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="25cb9-222">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="25cb9-222">Slider</span></span>|  
|<span data-ttu-id="25cb9-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="25cb9-223">SuperGrid</span></span>|<span data-ttu-id="25cb9-224">Özel</span><span class="sxs-lookup"><span data-stu-id="25cb9-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="25cb9-225">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="25cb9-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="25cb9-226">Windows Forms denetimleri için açığa [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] UIAutomationClientsideProviders.dll istemci tarafı sağlayıcı üzerinden.</span><span class="sxs-lookup"><span data-stu-id="25cb9-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="25cb9-227">Bu derleme UI otomasyon istemci uygulamaları ile kullanmak için otomatik olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="25cb9-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="25cb9-228">Windows Forms denetimleri için sarmalayıcıları genellikle yönetilen [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] tarafından desteklenen ortak denetimleri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="25cb9-228">Typically, Windows Forms controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="25cb9-229">Aşağıdaki denetimleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="25cb9-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="25cb9-230">Sınıf Adı</span><span class="sxs-lookup"><span data-stu-id="25cb9-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="25cb9-231">Düğme</span><span class="sxs-lookup"><span data-stu-id="25cb9-231">Button</span></span>|  
|<span data-ttu-id="25cb9-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="25cb9-232">CheckBox</span></span>|  
|<span data-ttu-id="25cb9-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="25cb9-233">CheckedListBox</span></span>|  
|<span data-ttu-id="25cb9-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="25cb9-234">ColorDialog</span></span>|  
|<span data-ttu-id="25cb9-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="25cb9-235">ComboBox</span></span>|  
|<span data-ttu-id="25cb9-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="25cb9-236">FolderBrowser</span></span>|  
|<span data-ttu-id="25cb9-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="25cb9-237">FontDialog</span></span>|  
|<span data-ttu-id="25cb9-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="25cb9-238">GroupBox</span></span>|  
|<span data-ttu-id="25cb9-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="25cb9-239">HscrollBar</span></span>|  
|<span data-ttu-id="25cb9-240">ImageList</span><span class="sxs-lookup"><span data-stu-id="25cb9-240">ImageList</span></span>|  
|<span data-ttu-id="25cb9-241">Etiketle</span><span class="sxs-lookup"><span data-stu-id="25cb9-241">Label</span></span>|  
|<span data-ttu-id="25cb9-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="25cb9-242">ListBox</span></span>|  
|<span data-ttu-id="25cb9-243">ListView</span><span class="sxs-lookup"><span data-stu-id="25cb9-243">ListView</span></span>|  
|<span data-ttu-id="25cb9-244">MainMenu/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="25cb9-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="25cb9-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="25cb9-245">MonthCalendar</span></span>|  
|<span data-ttu-id="25cb9-246">Notifyıcon</span><span class="sxs-lookup"><span data-stu-id="25cb9-246">NotifyIcon</span></span>|  
|<span data-ttu-id="25cb9-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="25cb9-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="25cb9-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="25cb9-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="25cb9-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="25cb9-249">PrintDialog</span></span>|  
|<span data-ttu-id="25cb9-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="25cb9-250">ProgressBar</span></span>|  
|<span data-ttu-id="25cb9-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="25cb9-251">RadioButton</span></span>|  
|<span data-ttu-id="25cb9-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="25cb9-252">RichTextBox</span></span>|  
|<span data-ttu-id="25cb9-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="25cb9-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="25cb9-254">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="25cb9-254">ScrollableControl</span></span>|  
|<span data-ttu-id="25cb9-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="25cb9-255">SoundPlayer</span></span>|  
|<span data-ttu-id="25cb9-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="25cb9-256">StatusBar</span></span>|  
|<span data-ttu-id="25cb9-257">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="25cb9-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="25cb9-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="25cb9-258">TextBox</span></span>|  
|<span data-ttu-id="25cb9-259">Zamanlayıcı</span><span class="sxs-lookup"><span data-stu-id="25cb9-259">Timer</span></span>|  
|<span data-ttu-id="25cb9-260">Araç Çubuğu</span><span class="sxs-lookup"><span data-stu-id="25cb9-260">Toolbar</span></span>|  
|<span data-ttu-id="25cb9-261">ToolTip</span><span class="sxs-lookup"><span data-stu-id="25cb9-261">ToolTip</span></span>|  
|<span data-ttu-id="25cb9-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="25cb9-262">TrackBar</span></span>|  
|<span data-ttu-id="25cb9-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="25cb9-263">TreeView</span></span>|  
|<span data-ttu-id="25cb9-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="25cb9-264">VscrollBar</span></span>|  
|<span data-ttu-id="25cb9-265">WebBrowser</span><span class="sxs-lookup"><span data-stu-id="25cb9-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="25cb9-266">Aşağıdaki denetimleri sunulur [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] yalnızca kendi desteği aracılığıyla [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span><span class="sxs-lookup"><span data-stu-id="25cb9-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)].</span></span> <span data-ttu-id="25cb9-267">Bazı işlevler kullanılamayabilir.</span><span class="sxs-lookup"><span data-stu-id="25cb9-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="25cb9-268">Denetim adı</span><span class="sxs-lookup"><span data-stu-id="25cb9-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="25cb9-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="25cb9-269">BindingSource</span></span>|  
|<span data-ttu-id="25cb9-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="25cb9-270">DataGrid</span></span>|  
|<span data-ttu-id="25cb9-271">DataGridView</span><span class="sxs-lookup"><span data-stu-id="25cb9-271">DataGridView</span></span>|  
|<span data-ttu-id="25cb9-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="25cb9-272">DataNavigator</span></span>|  
|<span data-ttu-id="25cb9-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="25cb9-273">DomainUpDown</span></span>|  
|<span data-ttu-id="25cb9-274">ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="25cb9-274">ErrorProvider</span></span>|  
|<span data-ttu-id="25cb9-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="25cb9-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="25cb9-276">Form</span><span class="sxs-lookup"><span data-stu-id="25cb9-276">Form</span></span>|  
|<span data-ttu-id="25cb9-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="25cb9-277">LinkLabel</span></span>|  
|<span data-ttu-id="25cb9-278">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="25cb9-278">HelpProvider</span></span>|  
|<span data-ttu-id="25cb9-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="25cb9-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="25cb9-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="25cb9-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="25cb9-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="25cb9-281">NumericUpDown</span></span>|  
|<span data-ttu-id="25cb9-282">Panel</span><span class="sxs-lookup"><span data-stu-id="25cb9-282">Panel</span></span>|  
|<span data-ttu-id="25cb9-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="25cb9-283">PictureBox</span></span>|  
|<span data-ttu-id="25cb9-284">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="25cb9-284">PrintDocument</span></span>|  
|<span data-ttu-id="25cb9-285">PrintPreview denetimi</span><span class="sxs-lookup"><span data-stu-id="25cb9-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="25cb9-286">PrintPreview iletişim kutusu</span><span class="sxs-lookup"><span data-stu-id="25cb9-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="25cb9-287">PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="25cb9-287">PropertyGrid</span></span>|  
|<span data-ttu-id="25cb9-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="25cb9-288">UserControl</span></span>|  
|<span data-ttu-id="25cb9-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="25cb9-289">ToolStrip</span></span>|  
|<span data-ttu-id="25cb9-290">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="25cb9-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="25cb9-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="25cb9-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="25cb9-292">Bölümlendirici</span><span class="sxs-lookup"><span data-stu-id="25cb9-292">Splitter</span></span>|  
|<span data-ttu-id="25cb9-293">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="25cb9-293">RaftingContainer</span></span>|  
|<span data-ttu-id="25cb9-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="25cb9-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="25cb9-295">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="25cb9-295">See Also</span></span>  
 [<span data-ttu-id="25cb9-296">UI Otomasyonu Denetim Türleri</span><span class="sxs-lookup"><span data-stu-id="25cb9-296">UI Automation Control Types</span></span>](../../../docs/framework/ui-automation/ui-automation-control-types.md)
