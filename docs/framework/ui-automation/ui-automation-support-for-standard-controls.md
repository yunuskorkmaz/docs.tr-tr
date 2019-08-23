---
title: Standart Denetimler İçin UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: d83713a81e7675a68482890c2401f1a0a6803abc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914227"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="bfe9f-102">Standart Denetimler İçin UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="bfe9f-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
> <span data-ttu-id="bfe9f-103">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="bfe9f-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="bfe9f-104">Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="bfe9f-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="bfe9f-105">Bu konu,, ve [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]çerçeveleriiçin [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]geliştirilen uygulamalardakistandartdenetimleriçindestekhakkındabilgileriçerir.[!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bfe9f-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="bfe9f-106">Windows Presentation Foundation denetimleri</span><span class="sxs-lookup"><span data-stu-id="bfe9f-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="bfe9f-107">Kullanıcı [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] etkileşimi için bilgi veya destek sağlayan tüm denetim öğeleri için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]tam yerel destek vardır.</span><span class="sxs-lookup"><span data-stu-id="bfe9f-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="bfe9f-108">Paneller gibi diğer öğeler, için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]görünür değildir.</span><span class="sxs-lookup"><span data-stu-id="bfe9f-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="bfe9f-109">Win32 denetimleri</span><span class="sxs-lookup"><span data-stu-id="bfe9f-109">Win32 Controls</span></span>  
 <span data-ttu-id="bfe9f-110">Çoğu [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] denetim UIAutomationClientsideProviders. dll içindeki istemci tarafı sağlayıcılar [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] aracılığıyla sunulur.</span><span class="sxs-lookup"><span data-stu-id="bfe9f-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="bfe9f-111">Bu derleme, UI Otomasyonu istemci uygulamalarıyla kullanılmak üzere otomatik olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="bfe9f-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="bfe9f-112">Tam destek yalnızca ComCtrl32. dll sürüm 6 [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] ' dan (ve üzeri sürümlerde kullanılabilir) denetimler için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="bfe9f-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span></span>  
  
 <span data-ttu-id="bfe9f-113">Aşağıdaki denetimler desteklenir.</span><span class="sxs-lookup"><span data-stu-id="bfe9f-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="bfe9f-114">Sınıf adı</span><span class="sxs-lookup"><span data-stu-id="bfe9f-114">Class name</span></span>|<span data-ttu-id="bfe9f-115">Denetim türü</span><span class="sxs-lookup"><span data-stu-id="bfe9f-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="bfe9f-116">Düğme</span><span class="sxs-lookup"><span data-stu-id="bfe9f-116">Button</span></span>|<span data-ttu-id="bfe9f-117">Düğme</span><span class="sxs-lookup"><span data-stu-id="bfe9f-117">Button</span></span>|  
|<span data-ttu-id="bfe9f-118">Düğme</span><span class="sxs-lookup"><span data-stu-id="bfe9f-118">Button</span></span>|<span data-ttu-id="bfe9f-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="bfe9f-119">RadioButton</span></span>|  
|<span data-ttu-id="bfe9f-120">Düğme</span><span class="sxs-lookup"><span data-stu-id="bfe9f-120">Button</span></span>|<span data-ttu-id="bfe9f-121">Grup</span><span class="sxs-lookup"><span data-stu-id="bfe9f-121">Group</span></span>|  
|<span data-ttu-id="bfe9f-122">Düğme</span><span class="sxs-lookup"><span data-stu-id="bfe9f-122">Button</span></span>|<span data-ttu-id="bfe9f-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="bfe9f-123">CheckBox</span></span>|  
|<span data-ttu-id="bfe9f-124">Düğme</span><span class="sxs-lookup"><span data-stu-id="bfe9f-124">Button</span></span>|<span data-ttu-id="bfe9f-125">Köprü</span><span class="sxs-lookup"><span data-stu-id="bfe9f-125">Hyperlink</span></span>|  
|<span data-ttu-id="bfe9f-126">Düğme</span><span class="sxs-lookup"><span data-stu-id="bfe9f-126">Button</span></span>|<span data-ttu-id="bfe9f-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="bfe9f-127">SplitButton</span></span>|  
|<span data-ttu-id="bfe9f-128">Düğme</span><span class="sxs-lookup"><span data-stu-id="bfe9f-128">Button</span></span>|<span data-ttu-id="bfe9f-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="bfe9f-129">CheckBox</span></span>|  
|<span data-ttu-id="bfe9f-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="bfe9f-130">ComboBoxEx32</span></span>|<span data-ttu-id="bfe9f-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="bfe9f-131">ComboBox</span></span>|  
|<span data-ttu-id="bfe9f-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="bfe9f-132">ComboBox</span></span>|<span data-ttu-id="bfe9f-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="bfe9f-133">ComboBox</span></span>|  
|<span data-ttu-id="bfe9f-134">Düzenle</span><span class="sxs-lookup"><span data-stu-id="bfe9f-134">Edit</span></span>|<span data-ttu-id="bfe9f-135">Belge</span><span class="sxs-lookup"><span data-stu-id="bfe9f-135">Document</span></span>|  
|<span data-ttu-id="bfe9f-136">Düzenle</span><span class="sxs-lookup"><span data-stu-id="bfe9f-136">Edit</span></span>|<span data-ttu-id="bfe9f-137">Düzenle</span><span class="sxs-lookup"><span data-stu-id="bfe9f-137">Edit</span></span>|  
|<span data-ttu-id="bfe9f-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="bfe9f-138">SysLink</span></span>|<span data-ttu-id="bfe9f-139">Köprü</span><span class="sxs-lookup"><span data-stu-id="bfe9f-139">Hyperlink</span></span>|  
|<span data-ttu-id="bfe9f-140">Statik</span><span class="sxs-lookup"><span data-stu-id="bfe9f-140">Static</span></span>|<span data-ttu-id="bfe9f-141">Metin</span><span class="sxs-lookup"><span data-stu-id="bfe9f-141">Text</span></span>|  
|<span data-ttu-id="bfe9f-142">Statik</span><span class="sxs-lookup"><span data-stu-id="bfe9f-142">Static</span></span>|<span data-ttu-id="bfe9f-143">Görüntü</span><span class="sxs-lookup"><span data-stu-id="bfe9f-143">Image</span></span>|  
|<span data-ttu-id="bfe9f-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="bfe9f-144">SysIPAddress32</span></span>|<span data-ttu-id="bfe9f-145">Özel</span><span class="sxs-lookup"><span data-stu-id="bfe9f-145">Custom</span></span>|  
|<span data-ttu-id="bfe9f-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="bfe9f-146">SysHeader32</span></span>|<span data-ttu-id="bfe9f-147">Üstbilgi/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="bfe9f-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="bfe9f-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="bfe9f-148">SysListView32</span></span>|<span data-ttu-id="bfe9f-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="bfe9f-149">DataGrid</span></span>|  
|<span data-ttu-id="bfe9f-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="bfe9f-150">SysListView32</span></span>|<span data-ttu-id="bfe9f-151">List</span><span class="sxs-lookup"><span data-stu-id="bfe9f-151">List</span></span>|  
|<span data-ttu-id="bfe9f-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="bfe9f-152">ListBox</span></span>|<span data-ttu-id="bfe9f-153">List</span><span class="sxs-lookup"><span data-stu-id="bfe9f-153">List</span></span>|  
|<span data-ttu-id="bfe9f-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="bfe9f-154">ListBox</span></span>|<span data-ttu-id="bfe9f-155">Liste</span><span class="sxs-lookup"><span data-stu-id="bfe9f-155">ListItem</span></span>|  
|<span data-ttu-id="bfe9f-156">#32768</span><span class="sxs-lookup"><span data-stu-id="bfe9f-156">#32768</span></span>|<span data-ttu-id="bfe9f-157">Menü</span><span class="sxs-lookup"><span data-stu-id="bfe9f-157">Menu</span></span>|  
|<span data-ttu-id="bfe9f-158">#32768</span><span class="sxs-lookup"><span data-stu-id="bfe9f-158">#32768</span></span>|<span data-ttu-id="bfe9f-159">MenuItem</span><span class="sxs-lookup"><span data-stu-id="bfe9f-159">MenuItem</span></span>|  
|<span data-ttu-id="bfe9f-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="bfe9f-160">msctls_progress32</span></span>|<span data-ttu-id="bfe9f-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="bfe9f-161">ProgressBar</span></span>|  
|<span data-ttu-id="bfe9f-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="bfe9f-162">RichEdit</span></span>|<span data-ttu-id="bfe9f-163">Belgedeki.</span><span class="sxs-lookup"><span data-stu-id="bfe9f-163">Document.</span></span> <span data-ttu-id="bfe9f-164">Bkz. Note.</span><span class="sxs-lookup"><span data-stu-id="bfe9f-164">See note.</span></span>|  
|<span data-ttu-id="bfe9f-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="bfe9f-165">RichEdit20A</span></span>|<span data-ttu-id="bfe9f-166">Belge</span><span class="sxs-lookup"><span data-stu-id="bfe9f-166">Document</span></span>|  
|<span data-ttu-id="bfe9f-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="bfe9f-167">RichEdit20W</span></span>|<span data-ttu-id="bfe9f-168">Belge</span><span class="sxs-lookup"><span data-stu-id="bfe9f-168">Document</span></span>|  
|<span data-ttu-id="bfe9f-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="bfe9f-169">RichEdit50W</span></span>|<span data-ttu-id="bfe9f-170">Belge</span><span class="sxs-lookup"><span data-stu-id="bfe9f-170">Document</span></span>|  
|<span data-ttu-id="bfe9f-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="bfe9f-171">ScrollBar</span></span>|<span data-ttu-id="bfe9f-172">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="bfe9f-172">Slider</span></span>|  
|<span data-ttu-id="bfe9f-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="bfe9f-173">msctls_trackbar32</span></span>|<span data-ttu-id="bfe9f-174">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="bfe9f-174">Slider</span></span>|  
|<span data-ttu-id="bfe9f-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="bfe9f-175">msctls_updown32</span></span>|<span data-ttu-id="bfe9f-176">Değer Değiştirici</span><span class="sxs-lookup"><span data-stu-id="bfe9f-176">Spinner</span></span>|  
|<span data-ttu-id="bfe9f-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="bfe9f-177">msctls_statusbar32</span></span>|<span data-ttu-id="bfe9f-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="bfe9f-178">StatusBar</span></span>|  
|<span data-ttu-id="bfe9f-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="bfe9f-179">SysTabControl32</span></span>|<span data-ttu-id="bfe9f-180">Tab</span><span class="sxs-lookup"><span data-stu-id="bfe9f-180">Tab</span></span>|  
|<span data-ttu-id="bfe9f-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="bfe9f-181">SysTabControl32</span></span>|<span data-ttu-id="bfe9f-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="bfe9f-182">TabItem</span></span>|  
|<span data-ttu-id="bfe9f-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="bfe9f-183">ToolbarWindow32</span></span>|<span data-ttu-id="bfe9f-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="bfe9f-184">ToolBar</span></span>|  
|<span data-ttu-id="bfe9f-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="bfe9f-185">ToolbarWindow32</span></span>|<span data-ttu-id="bfe9f-186">MenuItem</span><span class="sxs-lookup"><span data-stu-id="bfe9f-186">MenuItem</span></span>|  
|<span data-ttu-id="bfe9f-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="bfe9f-187">ToolbarWindow32</span></span>|<span data-ttu-id="bfe9f-188">Düğme</span><span class="sxs-lookup"><span data-stu-id="bfe9f-188">Button</span></span>|  
|<span data-ttu-id="bfe9f-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="bfe9f-189">ToolbarWindow32</span></span>|<span data-ttu-id="bfe9f-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="bfe9f-190">CheckBox</span></span>|  
|<span data-ttu-id="bfe9f-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="bfe9f-191">ToolbarWindow32</span></span>|<span data-ttu-id="bfe9f-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="bfe9f-192">RadioButton</span></span>|  
|<span data-ttu-id="bfe9f-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="bfe9f-193">ToolbarWindow32</span></span>|<span data-ttu-id="bfe9f-194">Ayırıcı</span><span class="sxs-lookup"><span data-stu-id="bfe9f-194">Separator</span></span>|  
|<span data-ttu-id="bfe9f-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="bfe9f-195">tooltips_class32</span></span>|<span data-ttu-id="bfe9f-196">ToolTip</span><span class="sxs-lookup"><span data-stu-id="bfe9f-196">ToolTip</span></span>|  
|<span data-ttu-id="bfe9f-197">#32774</span><span class="sxs-lookup"><span data-stu-id="bfe9f-197">#32774</span></span>|<span data-ttu-id="bfe9f-198">ToolTip</span><span class="sxs-lookup"><span data-stu-id="bfe9f-198">ToolTip</span></span>|  
|<span data-ttu-id="bfe9f-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="bfe9f-199">ReBarWindow32</span></span>|<span data-ttu-id="bfe9f-200">Araç Çubuğu</span><span class="sxs-lookup"><span data-stu-id="bfe9f-200">Toolbar</span></span>|  
|<span data-ttu-id="bfe9f-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="bfe9f-201">SysTreeView32</span></span>|<span data-ttu-id="bfe9f-202">Ağaç</span><span class="sxs-lookup"><span data-stu-id="bfe9f-202">Tree</span></span>|  
|<span data-ttu-id="bfe9f-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="bfe9f-203">SysTreeView32</span></span>|<span data-ttu-id="bfe9f-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="bfe9f-204">TreeItem</span></span>|  
  
 <span data-ttu-id="bfe9f-205">**Göz önünde** RichEdit denetimi yalnızca ile [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] birlikte gelen sürümler için desteklenir (riched20. dll sürümü 3,1 ve üzeri ve Msftedit. dll sürüm 4,1 ve üzeri).</span><span class="sxs-lookup"><span data-stu-id="bfe9f-205">**Note** The RichEdit control is supported only for versions shipped with [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="bfe9f-206">Aşağıdaki denetimler desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="bfe9f-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="bfe9f-207">Sınıf adı</span><span class="sxs-lookup"><span data-stu-id="bfe9f-207">Class name</span></span>|<span data-ttu-id="bfe9f-208">Denetim türü</span><span class="sxs-lookup"><span data-stu-id="bfe9f-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="bfe9f-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="bfe9f-209">SysAnimate32</span></span>|<span data-ttu-id="bfe9f-210">Görüntü</span><span class="sxs-lookup"><span data-stu-id="bfe9f-210">Image</span></span>|  
|<span data-ttu-id="bfe9f-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="bfe9f-211">SysPager</span></span>|<span data-ttu-id="bfe9f-212">Değer Değiştirici</span><span class="sxs-lookup"><span data-stu-id="bfe9f-212">Spinner</span></span>|  
|<span data-ttu-id="bfe9f-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="bfe9f-213">SysDateTimePick32</span></span>|<span data-ttu-id="bfe9f-214">Özel</span><span class="sxs-lookup"><span data-stu-id="bfe9f-214">Custom</span></span>|  
|<span data-ttu-id="bfe9f-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="bfe9f-215">SysMonthCal32</span></span>|<span data-ttu-id="bfe9f-216">Takvim</span><span class="sxs-lookup"><span data-stu-id="bfe9f-216">Calendar</span></span>|  
|<span data-ttu-id="bfe9f-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="bfe9f-217">MS_WINNOTE</span></span>|<span data-ttu-id="bfe9f-218">İpucuna</span><span class="sxs-lookup"><span data-stu-id="bfe9f-218">Tooltip</span></span>|  
|<span data-ttu-id="bfe9f-219">Vbkabarcık</span><span class="sxs-lookup"><span data-stu-id="bfe9f-219">VBBubble</span></span>|<span data-ttu-id="bfe9f-220">İpucuna</span><span class="sxs-lookup"><span data-stu-id="bfe9f-220">Tooltip</span></span>|  
|<span data-ttu-id="bfe9f-221">Kaydırma çubuğu (tek başına denetim olarak kullanıldığında)</span><span class="sxs-lookup"><span data-stu-id="bfe9f-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="bfe9f-222">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="bfe9f-222">Slider</span></span>|  
|<span data-ttu-id="bfe9f-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="bfe9f-223">SuperGrid</span></span>|<span data-ttu-id="bfe9f-224">Özel</span><span class="sxs-lookup"><span data-stu-id="bfe9f-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="bfe9f-225">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="bfe9f-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="bfe9f-226">Windows Forms denetimleri, UIAutomationClientsideProviders. dll içindeki istemci tarafı sağlayıcılar [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] aracılığıyla sunulur.</span><span class="sxs-lookup"><span data-stu-id="bfe9f-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="bfe9f-227">Bu derleme, UI Otomasyonu istemci uygulamalarıyla kullanılmak üzere otomatik olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="bfe9f-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="bfe9f-228">Genellikle, [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] ortak denetimlerin yönetilen sarmalayıcılarını kullanan Windows Forms denetimleri tarafından [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]desteklenir.</span><span class="sxs-lookup"><span data-stu-id="bfe9f-228">Typically, Windows Forms controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="bfe9f-229">Aşağıdaki denetimler desteklenir.</span><span class="sxs-lookup"><span data-stu-id="bfe9f-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="bfe9f-230">Sınıf Adı</span><span class="sxs-lookup"><span data-stu-id="bfe9f-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="bfe9f-231">Düğme</span><span class="sxs-lookup"><span data-stu-id="bfe9f-231">Button</span></span>|  
|<span data-ttu-id="bfe9f-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="bfe9f-232">CheckBox</span></span>|  
|<span data-ttu-id="bfe9f-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="bfe9f-233">CheckedListBox</span></span>|  
|<span data-ttu-id="bfe9f-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="bfe9f-234">ColorDialog</span></span>|  
|<span data-ttu-id="bfe9f-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="bfe9f-235">ComboBox</span></span>|  
|<span data-ttu-id="bfe9f-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="bfe9f-236">FolderBrowser</span></span>|  
|<span data-ttu-id="bfe9f-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="bfe9f-237">FontDialog</span></span>|  
|<span data-ttu-id="bfe9f-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="bfe9f-238">GroupBox</span></span>|  
|<span data-ttu-id="bfe9f-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="bfe9f-239">HscrollBar</span></span>|  
|<span data-ttu-id="bfe9f-240">'I</span><span class="sxs-lookup"><span data-stu-id="bfe9f-240">ImageList</span></span>|  
|<span data-ttu-id="bfe9f-241">Etiketle</span><span class="sxs-lookup"><span data-stu-id="bfe9f-241">Label</span></span>|  
|<span data-ttu-id="bfe9f-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="bfe9f-242">ListBox</span></span>|  
|<span data-ttu-id="bfe9f-243">ListView</span><span class="sxs-lookup"><span data-stu-id="bfe9f-243">ListView</span></span>|  
|<span data-ttu-id="bfe9f-244">MainMenu/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="bfe9f-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="bfe9f-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="bfe9f-245">MonthCalendar</span></span>|  
|<span data-ttu-id="bfe9f-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="bfe9f-246">NotifyIcon</span></span>|  
|<span data-ttu-id="bfe9f-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="bfe9f-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="bfe9f-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="bfe9f-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="bfe9f-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="bfe9f-249">PrintDialog</span></span>|  
|<span data-ttu-id="bfe9f-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="bfe9f-250">ProgressBar</span></span>|  
|<span data-ttu-id="bfe9f-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="bfe9f-251">RadioButton</span></span>|  
|<span data-ttu-id="bfe9f-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="bfe9f-252">RichTextBox</span></span>|  
|<span data-ttu-id="bfe9f-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="bfe9f-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="bfe9f-254">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="bfe9f-254">ScrollableControl</span></span>|  
|<span data-ttu-id="bfe9f-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="bfe9f-255">SoundPlayer</span></span>|  
|<span data-ttu-id="bfe9f-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="bfe9f-256">StatusBar</span></span>|  
|<span data-ttu-id="bfe9f-257">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="bfe9f-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="bfe9f-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="bfe9f-258">TextBox</span></span>|  
|<span data-ttu-id="bfe9f-259">Zamanlayıcı</span><span class="sxs-lookup"><span data-stu-id="bfe9f-259">Timer</span></span>|  
|<span data-ttu-id="bfe9f-260">Araç Çubuğu</span><span class="sxs-lookup"><span data-stu-id="bfe9f-260">Toolbar</span></span>|  
|<span data-ttu-id="bfe9f-261">ToolTip</span><span class="sxs-lookup"><span data-stu-id="bfe9f-261">ToolTip</span></span>|  
|<span data-ttu-id="bfe9f-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="bfe9f-262">TrackBar</span></span>|  
|<span data-ttu-id="bfe9f-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="bfe9f-263">TreeView</span></span>|  
|<span data-ttu-id="bfe9f-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="bfe9f-264">VscrollBar</span></span>|  
|<span data-ttu-id="bfe9f-265">'A</span><span class="sxs-lookup"><span data-stu-id="bfe9f-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="bfe9f-266">Aşağıdaki denetimler [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] yalnızca Microsoft Etkin Erişilebilirlik desteğiyle kullanıma sunulur.</span><span class="sxs-lookup"><span data-stu-id="bfe9f-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for Microsoft Active Accessibility.</span></span> <span data-ttu-id="bfe9f-267">Bazı işlevler kullanılamayabilir.</span><span class="sxs-lookup"><span data-stu-id="bfe9f-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="bfe9f-268">Denetim adı</span><span class="sxs-lookup"><span data-stu-id="bfe9f-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="bfe9f-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="bfe9f-269">BindingSource</span></span>|  
|<span data-ttu-id="bfe9f-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="bfe9f-270">DataGrid</span></span>|  
|<span data-ttu-id="bfe9f-271">DataGridView</span><span class="sxs-lookup"><span data-stu-id="bfe9f-271">DataGridView</span></span>|  
|<span data-ttu-id="bfe9f-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="bfe9f-272">DataNavigator</span></span>|  
|<span data-ttu-id="bfe9f-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="bfe9f-273">DomainUpDown</span></span>|  
|<span data-ttu-id="bfe9f-274">Bileþeni</span><span class="sxs-lookup"><span data-stu-id="bfe9f-274">ErrorProvider</span></span>|  
|<span data-ttu-id="bfe9f-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="bfe9f-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="bfe9f-276">Form</span><span class="sxs-lookup"><span data-stu-id="bfe9f-276">Form</span></span>|  
|<span data-ttu-id="bfe9f-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="bfe9f-277">LinkLabel</span></span>|  
|<span data-ttu-id="bfe9f-278">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="bfe9f-278">HelpProvider</span></span>|  
|<span data-ttu-id="bfe9f-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="bfe9f-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="bfe9f-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="bfe9f-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="bfe9f-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="bfe9f-281">NumericUpDown</span></span>|  
|<span data-ttu-id="bfe9f-282">Panel</span><span class="sxs-lookup"><span data-stu-id="bfe9f-282">Panel</span></span>|  
|<span data-ttu-id="bfe9f-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="bfe9f-283">PictureBox</span></span>|  
|<span data-ttu-id="bfe9f-284">Öniz</span><span class="sxs-lookup"><span data-stu-id="bfe9f-284">PrintDocument</span></span>|  
|<span data-ttu-id="bfe9f-285">PrintPreview-denetim</span><span class="sxs-lookup"><span data-stu-id="bfe9f-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="bfe9f-286">PrintPreview-Iletişim kutusu</span><span class="sxs-lookup"><span data-stu-id="bfe9f-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="bfe9f-287">'In</span><span class="sxs-lookup"><span data-stu-id="bfe9f-287">PropertyGrid</span></span>|  
|<span data-ttu-id="bfe9f-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="bfe9f-288">UserControl</span></span>|  
|<span data-ttu-id="bfe9f-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="bfe9f-289">ToolStrip</span></span>|  
|<span data-ttu-id="bfe9f-290">Ekleyecek</span><span class="sxs-lookup"><span data-stu-id="bfe9f-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="bfe9f-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="bfe9f-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="bfe9f-292">Bölücü</span><span class="sxs-lookup"><span data-stu-id="bfe9f-292">Splitter</span></span>|  
|<span data-ttu-id="bfe9f-293">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="bfe9f-293">RaftingContainer</span></span>|  
|<span data-ttu-id="bfe9f-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="bfe9f-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bfe9f-295">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bfe9f-295">See also</span></span>

- [<span data-ttu-id="bfe9f-296">UI Otomasyonu Denetim Türleri</span><span class="sxs-lookup"><span data-stu-id="bfe9f-296">UI Automation Control Types</span></span>](../../../docs/framework/ui-automation/ui-automation-control-types.md)
