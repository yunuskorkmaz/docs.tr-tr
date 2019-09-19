---
title: Standart Denetimler İçin UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 6cbf31c8a1cdf6e853e56445d22f4a7513bd1859
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71042003"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="5b9ab-102">Standart Denetimler İçin UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="5b9ab-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
> <span data-ttu-id="5b9ab-103">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="5b9ab-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="5b9ab-104">Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="5b9ab-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="5b9ab-105">Bu konu,, ve [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]çerçeveleriiçin [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]geliştirilen uygulamalardakistandartdenetimleriçindestekhakkındabilgileriçerir.[!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b9ab-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="5b9ab-106">Windows Presentation Foundation denetimleri</span><span class="sxs-lookup"><span data-stu-id="5b9ab-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="5b9ab-107">Kullanıcı [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] etkileşimi için bilgi veya destek sağlayan tüm denetim öğeleri için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]tam yerel destek vardır.</span><span class="sxs-lookup"><span data-stu-id="5b9ab-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="5b9ab-108">Paneller gibi diğer öğeler, için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]görünür değildir.</span><span class="sxs-lookup"><span data-stu-id="5b9ab-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="5b9ab-109">Win32 denetimleri</span><span class="sxs-lookup"><span data-stu-id="5b9ab-109">Win32 Controls</span></span>  
 <span data-ttu-id="5b9ab-110">Çoğu [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] denetim UIAutomationClientsideProviders. dll içindeki istemci tarafı sağlayıcılar [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] aracılığıyla sunulur.</span><span class="sxs-lookup"><span data-stu-id="5b9ab-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="5b9ab-111">Bu derleme, UI Otomasyonu istemci uygulamalarıyla kullanılmak üzere otomatik olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="5b9ab-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="5b9ab-112">Tam destek yalnızca ComCtrl32. dll sürüm 6 [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] ' dan (ve üzeri sürümlerde kullanılabilir) denetimler için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="5b9ab-112">Full support is provided only for controls from version 6 of ComCtrl32.dll (available with [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] and later).</span></span>  
  
 <span data-ttu-id="5b9ab-113">Aşağıdaki denetimler desteklenir.</span><span class="sxs-lookup"><span data-stu-id="5b9ab-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="5b9ab-114">Sınıf adı</span><span class="sxs-lookup"><span data-stu-id="5b9ab-114">Class name</span></span>|<span data-ttu-id="5b9ab-115">Denetim türü</span><span class="sxs-lookup"><span data-stu-id="5b9ab-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="5b9ab-116">Düğme</span><span class="sxs-lookup"><span data-stu-id="5b9ab-116">Button</span></span>|<span data-ttu-id="5b9ab-117">Düğme</span><span class="sxs-lookup"><span data-stu-id="5b9ab-117">Button</span></span>|  
|<span data-ttu-id="5b9ab-118">Düğme</span><span class="sxs-lookup"><span data-stu-id="5b9ab-118">Button</span></span>|<span data-ttu-id="5b9ab-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="5b9ab-119">RadioButton</span></span>|  
|<span data-ttu-id="5b9ab-120">Düğme</span><span class="sxs-lookup"><span data-stu-id="5b9ab-120">Button</span></span>|<span data-ttu-id="5b9ab-121">Grup</span><span class="sxs-lookup"><span data-stu-id="5b9ab-121">Group</span></span>|  
|<span data-ttu-id="5b9ab-122">Düğme</span><span class="sxs-lookup"><span data-stu-id="5b9ab-122">Button</span></span>|<span data-ttu-id="5b9ab-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="5b9ab-123">CheckBox</span></span>|  
|<span data-ttu-id="5b9ab-124">Düğme</span><span class="sxs-lookup"><span data-stu-id="5b9ab-124">Button</span></span>|<span data-ttu-id="5b9ab-125">Köprü</span><span class="sxs-lookup"><span data-stu-id="5b9ab-125">Hyperlink</span></span>|  
|<span data-ttu-id="5b9ab-126">Düğme</span><span class="sxs-lookup"><span data-stu-id="5b9ab-126">Button</span></span>|<span data-ttu-id="5b9ab-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="5b9ab-127">SplitButton</span></span>|  
|<span data-ttu-id="5b9ab-128">Düğme</span><span class="sxs-lookup"><span data-stu-id="5b9ab-128">Button</span></span>|<span data-ttu-id="5b9ab-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="5b9ab-129">CheckBox</span></span>|  
|<span data-ttu-id="5b9ab-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="5b9ab-130">ComboBoxEx32</span></span>|<span data-ttu-id="5b9ab-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="5b9ab-131">ComboBox</span></span>|  
|<span data-ttu-id="5b9ab-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="5b9ab-132">ComboBox</span></span>|<span data-ttu-id="5b9ab-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="5b9ab-133">ComboBox</span></span>|  
|<span data-ttu-id="5b9ab-134">Düzenle</span><span class="sxs-lookup"><span data-stu-id="5b9ab-134">Edit</span></span>|<span data-ttu-id="5b9ab-135">Belge</span><span class="sxs-lookup"><span data-stu-id="5b9ab-135">Document</span></span>|  
|<span data-ttu-id="5b9ab-136">Düzenle</span><span class="sxs-lookup"><span data-stu-id="5b9ab-136">Edit</span></span>|<span data-ttu-id="5b9ab-137">Düzenle</span><span class="sxs-lookup"><span data-stu-id="5b9ab-137">Edit</span></span>|  
|<span data-ttu-id="5b9ab-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="5b9ab-138">SysLink</span></span>|<span data-ttu-id="5b9ab-139">Köprü</span><span class="sxs-lookup"><span data-stu-id="5b9ab-139">Hyperlink</span></span>|  
|<span data-ttu-id="5b9ab-140">Statik</span><span class="sxs-lookup"><span data-stu-id="5b9ab-140">Static</span></span>|<span data-ttu-id="5b9ab-141">Metin</span><span class="sxs-lookup"><span data-stu-id="5b9ab-141">Text</span></span>|  
|<span data-ttu-id="5b9ab-142">Statik</span><span class="sxs-lookup"><span data-stu-id="5b9ab-142">Static</span></span>|<span data-ttu-id="5b9ab-143">Görüntü</span><span class="sxs-lookup"><span data-stu-id="5b9ab-143">Image</span></span>|  
|<span data-ttu-id="5b9ab-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="5b9ab-144">SysIPAddress32</span></span>|<span data-ttu-id="5b9ab-145">Özel</span><span class="sxs-lookup"><span data-stu-id="5b9ab-145">Custom</span></span>|  
|<span data-ttu-id="5b9ab-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="5b9ab-146">SysHeader32</span></span>|<span data-ttu-id="5b9ab-147">Üstbilgi/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="5b9ab-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="5b9ab-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="5b9ab-148">SysListView32</span></span>|<span data-ttu-id="5b9ab-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="5b9ab-149">DataGrid</span></span>|  
|<span data-ttu-id="5b9ab-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="5b9ab-150">SysListView32</span></span>|<span data-ttu-id="5b9ab-151">List</span><span class="sxs-lookup"><span data-stu-id="5b9ab-151">List</span></span>|  
|<span data-ttu-id="5b9ab-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="5b9ab-152">ListBox</span></span>|<span data-ttu-id="5b9ab-153">List</span><span class="sxs-lookup"><span data-stu-id="5b9ab-153">List</span></span>|  
|<span data-ttu-id="5b9ab-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="5b9ab-154">ListBox</span></span>|<span data-ttu-id="5b9ab-155">Liste</span><span class="sxs-lookup"><span data-stu-id="5b9ab-155">ListItem</span></span>|  
|<span data-ttu-id="5b9ab-156">#32768</span><span class="sxs-lookup"><span data-stu-id="5b9ab-156">#32768</span></span>|<span data-ttu-id="5b9ab-157">Menü</span><span class="sxs-lookup"><span data-stu-id="5b9ab-157">Menu</span></span>|  
|<span data-ttu-id="5b9ab-158">#32768</span><span class="sxs-lookup"><span data-stu-id="5b9ab-158">#32768</span></span>|<span data-ttu-id="5b9ab-159">MenuItem</span><span class="sxs-lookup"><span data-stu-id="5b9ab-159">MenuItem</span></span>|  
|<span data-ttu-id="5b9ab-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="5b9ab-160">msctls_progress32</span></span>|<span data-ttu-id="5b9ab-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="5b9ab-161">ProgressBar</span></span>|  
|<span data-ttu-id="5b9ab-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="5b9ab-162">RichEdit</span></span>|<span data-ttu-id="5b9ab-163">belgedeki.</span><span class="sxs-lookup"><span data-stu-id="5b9ab-163">Document.</span></span> <span data-ttu-id="5b9ab-164">Bkz. Note.</span><span class="sxs-lookup"><span data-stu-id="5b9ab-164">See note.</span></span>|  
|<span data-ttu-id="5b9ab-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="5b9ab-165">RichEdit20A</span></span>|<span data-ttu-id="5b9ab-166">Belge</span><span class="sxs-lookup"><span data-stu-id="5b9ab-166">Document</span></span>|  
|<span data-ttu-id="5b9ab-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="5b9ab-167">RichEdit20W</span></span>|<span data-ttu-id="5b9ab-168">Belge</span><span class="sxs-lookup"><span data-stu-id="5b9ab-168">Document</span></span>|  
|<span data-ttu-id="5b9ab-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="5b9ab-169">RichEdit50W</span></span>|<span data-ttu-id="5b9ab-170">Belge</span><span class="sxs-lookup"><span data-stu-id="5b9ab-170">Document</span></span>|  
|<span data-ttu-id="5b9ab-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="5b9ab-171">ScrollBar</span></span>|<span data-ttu-id="5b9ab-172">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="5b9ab-172">Slider</span></span>|  
|<span data-ttu-id="5b9ab-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="5b9ab-173">msctls_trackbar32</span></span>|<span data-ttu-id="5b9ab-174">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="5b9ab-174">Slider</span></span>|  
|<span data-ttu-id="5b9ab-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="5b9ab-175">msctls_updown32</span></span>|<span data-ttu-id="5b9ab-176">Değer Değiştirici</span><span class="sxs-lookup"><span data-stu-id="5b9ab-176">Spinner</span></span>|  
|<span data-ttu-id="5b9ab-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="5b9ab-177">msctls_statusbar32</span></span>|<span data-ttu-id="5b9ab-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="5b9ab-178">StatusBar</span></span>|  
|<span data-ttu-id="5b9ab-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="5b9ab-179">SysTabControl32</span></span>|<span data-ttu-id="5b9ab-180">Tab</span><span class="sxs-lookup"><span data-stu-id="5b9ab-180">Tab</span></span>|  
|<span data-ttu-id="5b9ab-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="5b9ab-181">SysTabControl32</span></span>|<span data-ttu-id="5b9ab-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="5b9ab-182">TabItem</span></span>|  
|<span data-ttu-id="5b9ab-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="5b9ab-183">ToolbarWindow32</span></span>|<span data-ttu-id="5b9ab-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="5b9ab-184">ToolBar</span></span>|  
|<span data-ttu-id="5b9ab-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="5b9ab-185">ToolbarWindow32</span></span>|<span data-ttu-id="5b9ab-186">MenuItem</span><span class="sxs-lookup"><span data-stu-id="5b9ab-186">MenuItem</span></span>|  
|<span data-ttu-id="5b9ab-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="5b9ab-187">ToolbarWindow32</span></span>|<span data-ttu-id="5b9ab-188">Düğme</span><span class="sxs-lookup"><span data-stu-id="5b9ab-188">Button</span></span>|  
|<span data-ttu-id="5b9ab-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="5b9ab-189">ToolbarWindow32</span></span>|<span data-ttu-id="5b9ab-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="5b9ab-190">CheckBox</span></span>|  
|<span data-ttu-id="5b9ab-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="5b9ab-191">ToolbarWindow32</span></span>|<span data-ttu-id="5b9ab-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="5b9ab-192">RadioButton</span></span>|  
|<span data-ttu-id="5b9ab-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="5b9ab-193">ToolbarWindow32</span></span>|<span data-ttu-id="5b9ab-194">Ayırıcı</span><span class="sxs-lookup"><span data-stu-id="5b9ab-194">Separator</span></span>|  
|<span data-ttu-id="5b9ab-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="5b9ab-195">tooltips_class32</span></span>|<span data-ttu-id="5b9ab-196">ToolTip</span><span class="sxs-lookup"><span data-stu-id="5b9ab-196">ToolTip</span></span>|  
|<span data-ttu-id="5b9ab-197">#32774</span><span class="sxs-lookup"><span data-stu-id="5b9ab-197">#32774</span></span>|<span data-ttu-id="5b9ab-198">ToolTip</span><span class="sxs-lookup"><span data-stu-id="5b9ab-198">ToolTip</span></span>|  
|<span data-ttu-id="5b9ab-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="5b9ab-199">ReBarWindow32</span></span>|<span data-ttu-id="5b9ab-200">Araç Çubuğu</span><span class="sxs-lookup"><span data-stu-id="5b9ab-200">Toolbar</span></span>|  
|<span data-ttu-id="5b9ab-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="5b9ab-201">SysTreeView32</span></span>|<span data-ttu-id="5b9ab-202">Ağaç</span><span class="sxs-lookup"><span data-stu-id="5b9ab-202">Tree</span></span>|  
|<span data-ttu-id="5b9ab-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="5b9ab-203">SysTreeView32</span></span>|<span data-ttu-id="5b9ab-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="5b9ab-204">TreeItem</span></span>|  
  
 <span data-ttu-id="5b9ab-205">**Göz önünde** RichEdit denetimi yalnızca ile [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] birlikte gelen sürümler için desteklenir (riched20. dll sürümü 3,1 ve üzeri ve Msftedit. dll sürüm 4,1 ve üzeri).</span><span class="sxs-lookup"><span data-stu-id="5b9ab-205">**Note** The RichEdit control is supported only for versions shipped with [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="5b9ab-206">Aşağıdaki denetimler desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="5b9ab-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="5b9ab-207">Sınıf adı</span><span class="sxs-lookup"><span data-stu-id="5b9ab-207">Class name</span></span>|<span data-ttu-id="5b9ab-208">Denetim türü</span><span class="sxs-lookup"><span data-stu-id="5b9ab-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="5b9ab-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="5b9ab-209">SysAnimate32</span></span>|<span data-ttu-id="5b9ab-210">Görüntü</span><span class="sxs-lookup"><span data-stu-id="5b9ab-210">Image</span></span>|  
|<span data-ttu-id="5b9ab-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="5b9ab-211">SysPager</span></span>|<span data-ttu-id="5b9ab-212">Değer Değiştirici</span><span class="sxs-lookup"><span data-stu-id="5b9ab-212">Spinner</span></span>|  
|<span data-ttu-id="5b9ab-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="5b9ab-213">SysDateTimePick32</span></span>|<span data-ttu-id="5b9ab-214">Özel</span><span class="sxs-lookup"><span data-stu-id="5b9ab-214">Custom</span></span>|  
|<span data-ttu-id="5b9ab-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="5b9ab-215">SysMonthCal32</span></span>|<span data-ttu-id="5b9ab-216">Takvim</span><span class="sxs-lookup"><span data-stu-id="5b9ab-216">Calendar</span></span>|  
|<span data-ttu-id="5b9ab-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="5b9ab-217">MS_WINNOTE</span></span>|<span data-ttu-id="5b9ab-218">İpucuna</span><span class="sxs-lookup"><span data-stu-id="5b9ab-218">Tooltip</span></span>|  
|<span data-ttu-id="5b9ab-219">Vbkabarcık</span><span class="sxs-lookup"><span data-stu-id="5b9ab-219">VBBubble</span></span>|<span data-ttu-id="5b9ab-220">İpucuna</span><span class="sxs-lookup"><span data-stu-id="5b9ab-220">Tooltip</span></span>|  
|<span data-ttu-id="5b9ab-221">Kaydırma çubuğu (tek başına denetim olarak kullanıldığında)</span><span class="sxs-lookup"><span data-stu-id="5b9ab-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="5b9ab-222">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="5b9ab-222">Slider</span></span>|  
|<span data-ttu-id="5b9ab-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="5b9ab-223">SuperGrid</span></span>|<span data-ttu-id="5b9ab-224">Özel</span><span class="sxs-lookup"><span data-stu-id="5b9ab-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="5b9ab-225">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="5b9ab-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="5b9ab-226">Windows Forms denetimleri, UIAutomationClientsideProviders. dll içindeki istemci tarafı sağlayıcılar [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] aracılığıyla sunulur.</span><span class="sxs-lookup"><span data-stu-id="5b9ab-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="5b9ab-227">Bu derleme, UI Otomasyonu istemci uygulamalarıyla kullanılmak üzere otomatik olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="5b9ab-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="5b9ab-228">Genellikle, [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] ortak denetimlerin yönetilen sarmalayıcılarını kullanan Windows Forms denetimleri tarafından [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]desteklenir.</span><span class="sxs-lookup"><span data-stu-id="5b9ab-228">Typically, Windows Forms controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="5b9ab-229">Aşağıdaki denetimler desteklenir.</span><span class="sxs-lookup"><span data-stu-id="5b9ab-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="5b9ab-230">Sınıf Adı</span><span class="sxs-lookup"><span data-stu-id="5b9ab-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="5b9ab-231">Düğme</span><span class="sxs-lookup"><span data-stu-id="5b9ab-231">Button</span></span>|  
|<span data-ttu-id="5b9ab-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="5b9ab-232">CheckBox</span></span>|  
|<span data-ttu-id="5b9ab-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="5b9ab-233">CheckedListBox</span></span>|  
|<span data-ttu-id="5b9ab-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="5b9ab-234">ColorDialog</span></span>|  
|<span data-ttu-id="5b9ab-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="5b9ab-235">ComboBox</span></span>|  
|<span data-ttu-id="5b9ab-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="5b9ab-236">FolderBrowser</span></span>|  
|<span data-ttu-id="5b9ab-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="5b9ab-237">FontDialog</span></span>|  
|<span data-ttu-id="5b9ab-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="5b9ab-238">GroupBox</span></span>|  
|<span data-ttu-id="5b9ab-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="5b9ab-239">HscrollBar</span></span>|  
|<span data-ttu-id="5b9ab-240">'I</span><span class="sxs-lookup"><span data-stu-id="5b9ab-240">ImageList</span></span>|  
|<span data-ttu-id="5b9ab-241">Etiketle</span><span class="sxs-lookup"><span data-stu-id="5b9ab-241">Label</span></span>|  
|<span data-ttu-id="5b9ab-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="5b9ab-242">ListBox</span></span>|  
|<span data-ttu-id="5b9ab-243">ListView</span><span class="sxs-lookup"><span data-stu-id="5b9ab-243">ListView</span></span>|  
|<span data-ttu-id="5b9ab-244">MainMenu/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="5b9ab-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="5b9ab-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="5b9ab-245">MonthCalendar</span></span>|  
|<span data-ttu-id="5b9ab-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="5b9ab-246">NotifyIcon</span></span>|  
|<span data-ttu-id="5b9ab-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="5b9ab-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="5b9ab-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="5b9ab-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="5b9ab-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="5b9ab-249">PrintDialog</span></span>|  
|<span data-ttu-id="5b9ab-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="5b9ab-250">ProgressBar</span></span>|  
|<span data-ttu-id="5b9ab-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="5b9ab-251">RadioButton</span></span>|  
|<span data-ttu-id="5b9ab-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="5b9ab-252">RichTextBox</span></span>|  
|<span data-ttu-id="5b9ab-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="5b9ab-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="5b9ab-254">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="5b9ab-254">ScrollableControl</span></span>|  
|<span data-ttu-id="5b9ab-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="5b9ab-255">SoundPlayer</span></span>|  
|<span data-ttu-id="5b9ab-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="5b9ab-256">StatusBar</span></span>|  
|<span data-ttu-id="5b9ab-257">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="5b9ab-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="5b9ab-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="5b9ab-258">TextBox</span></span>|  
|<span data-ttu-id="5b9ab-259">Zamanlayıcı</span><span class="sxs-lookup"><span data-stu-id="5b9ab-259">Timer</span></span>|  
|<span data-ttu-id="5b9ab-260">Araç Çubuğu</span><span class="sxs-lookup"><span data-stu-id="5b9ab-260">Toolbar</span></span>|  
|<span data-ttu-id="5b9ab-261">ToolTip</span><span class="sxs-lookup"><span data-stu-id="5b9ab-261">ToolTip</span></span>|  
|<span data-ttu-id="5b9ab-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="5b9ab-262">TrackBar</span></span>|  
|<span data-ttu-id="5b9ab-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="5b9ab-263">TreeView</span></span>|  
|<span data-ttu-id="5b9ab-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="5b9ab-264">VscrollBar</span></span>|  
|<span data-ttu-id="5b9ab-265">'A</span><span class="sxs-lookup"><span data-stu-id="5b9ab-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="5b9ab-266">Aşağıdaki denetimler [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] yalnızca Microsoft Etkin Erişilebilirlik desteğiyle kullanıma sunulur.</span><span class="sxs-lookup"><span data-stu-id="5b9ab-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for Microsoft Active Accessibility.</span></span> <span data-ttu-id="5b9ab-267">Bazı işlevler kullanılamayabilir.</span><span class="sxs-lookup"><span data-stu-id="5b9ab-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="5b9ab-268">Denetim adı</span><span class="sxs-lookup"><span data-stu-id="5b9ab-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="5b9ab-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="5b9ab-269">BindingSource</span></span>|  
|<span data-ttu-id="5b9ab-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="5b9ab-270">DataGrid</span></span>|  
|<span data-ttu-id="5b9ab-271">DataGridView</span><span class="sxs-lookup"><span data-stu-id="5b9ab-271">DataGridView</span></span>|  
|<span data-ttu-id="5b9ab-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="5b9ab-272">DataNavigator</span></span>|  
|<span data-ttu-id="5b9ab-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="5b9ab-273">DomainUpDown</span></span>|  
|<span data-ttu-id="5b9ab-274">Bileþeni</span><span class="sxs-lookup"><span data-stu-id="5b9ab-274">ErrorProvider</span></span>|  
|<span data-ttu-id="5b9ab-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="5b9ab-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="5b9ab-276">Form</span><span class="sxs-lookup"><span data-stu-id="5b9ab-276">Form</span></span>|  
|<span data-ttu-id="5b9ab-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="5b9ab-277">LinkLabel</span></span>|  
|<span data-ttu-id="5b9ab-278">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="5b9ab-278">HelpProvider</span></span>|  
|<span data-ttu-id="5b9ab-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="5b9ab-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="5b9ab-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="5b9ab-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="5b9ab-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="5b9ab-281">NumericUpDown</span></span>|  
|<span data-ttu-id="5b9ab-282">Panel</span><span class="sxs-lookup"><span data-stu-id="5b9ab-282">Panel</span></span>|  
|<span data-ttu-id="5b9ab-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="5b9ab-283">PictureBox</span></span>|  
|<span data-ttu-id="5b9ab-284">Öniz</span><span class="sxs-lookup"><span data-stu-id="5b9ab-284">PrintDocument</span></span>|  
|<span data-ttu-id="5b9ab-285">PrintPreview-denetim</span><span class="sxs-lookup"><span data-stu-id="5b9ab-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="5b9ab-286">PrintPreview-Iletişim kutusu</span><span class="sxs-lookup"><span data-stu-id="5b9ab-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="5b9ab-287">'In</span><span class="sxs-lookup"><span data-stu-id="5b9ab-287">PropertyGrid</span></span>|  
|<span data-ttu-id="5b9ab-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="5b9ab-288">UserControl</span></span>|  
|<span data-ttu-id="5b9ab-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="5b9ab-289">ToolStrip</span></span>|  
|<span data-ttu-id="5b9ab-290">Ekleyecek</span><span class="sxs-lookup"><span data-stu-id="5b9ab-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="5b9ab-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="5b9ab-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="5b9ab-292">Bölücü</span><span class="sxs-lookup"><span data-stu-id="5b9ab-292">Splitter</span></span>|  
|<span data-ttu-id="5b9ab-293">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="5b9ab-293">RaftingContainer</span></span>|  
|<span data-ttu-id="5b9ab-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="5b9ab-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5b9ab-295">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b9ab-295">See also</span></span>

- [<span data-ttu-id="5b9ab-296">UI Otomasyonu Denetim Türleri</span><span class="sxs-lookup"><span data-stu-id="5b9ab-296">UI Automation Control Types</span></span>](ui-automation-control-types.md)
