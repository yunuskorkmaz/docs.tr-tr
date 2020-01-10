---
title: Standart Denetimler İçin UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: ed5e4f6ab23fe9ae77c94616a668da8accb46d4b
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75741707"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="19584-102">Standart Denetimler İçin UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="19584-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
> <span data-ttu-id="19584-103">Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="19584-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="19584-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="19584-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="19584-105">Bu konu, [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], Win32 ve [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] çerçeveleri için geliştirilen uygulamalardaki standart denetimler için [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] desteği hakkında bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="19584-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], Win32, and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="19584-106">Windows Presentation Foundation denetimleri</span><span class="sxs-lookup"><span data-stu-id="19584-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="19584-107">Kullanıcı etkileşimi için bilgi veya destek sağlayan tüm [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] denetim öğelerinin [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]tam yerel desteği vardır.</span><span class="sxs-lookup"><span data-stu-id="19584-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="19584-108">Paneller gibi diğer öğeler [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]görünmüyor.</span><span class="sxs-lookup"><span data-stu-id="19584-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="19584-109">Win32 denetimleri</span><span class="sxs-lookup"><span data-stu-id="19584-109">Win32 Controls</span></span>  
 <span data-ttu-id="19584-110">Çoğu Win32 denetimi, UIAutomationClientsideProviders. dll içindeki istemci tarafı sağlayıcılar aracılığıyla [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] gösterilir.</span><span class="sxs-lookup"><span data-stu-id="19584-110">Most Win32 controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="19584-111">Bu derleme, UI Otomasyonu istemci uygulamalarıyla kullanılmak üzere otomatik olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="19584-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="19584-112">Tam destek yalnızca *ComCtrl32. dll*sürüm 6 ' dan denetimler için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="19584-112">Full support is provided only for controls from version 6 of *ComCtrl32.dll*.</span></span>  
  
 <span data-ttu-id="19584-113">Aşağıdaki denetimler desteklenir.</span><span class="sxs-lookup"><span data-stu-id="19584-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="19584-114">Sınıf adı</span><span class="sxs-lookup"><span data-stu-id="19584-114">Class name</span></span>|<span data-ttu-id="19584-115">Denetim türü</span><span class="sxs-lookup"><span data-stu-id="19584-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="19584-116">Düğme</span><span class="sxs-lookup"><span data-stu-id="19584-116">Button</span></span>|<span data-ttu-id="19584-117">Düğme</span><span class="sxs-lookup"><span data-stu-id="19584-117">Button</span></span>|  
|<span data-ttu-id="19584-118">Düğme</span><span class="sxs-lookup"><span data-stu-id="19584-118">Button</span></span>|<span data-ttu-id="19584-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="19584-119">RadioButton</span></span>|  
|<span data-ttu-id="19584-120">Düğme</span><span class="sxs-lookup"><span data-stu-id="19584-120">Button</span></span>|<span data-ttu-id="19584-121">Grup</span><span class="sxs-lookup"><span data-stu-id="19584-121">Group</span></span>|  
|<span data-ttu-id="19584-122">Düğme</span><span class="sxs-lookup"><span data-stu-id="19584-122">Button</span></span>|<span data-ttu-id="19584-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="19584-123">CheckBox</span></span>|  
|<span data-ttu-id="19584-124">Düğme</span><span class="sxs-lookup"><span data-stu-id="19584-124">Button</span></span>|<span data-ttu-id="19584-125">Köprü</span><span class="sxs-lookup"><span data-stu-id="19584-125">Hyperlink</span></span>|  
|<span data-ttu-id="19584-126">Düğme</span><span class="sxs-lookup"><span data-stu-id="19584-126">Button</span></span>|<span data-ttu-id="19584-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="19584-127">SplitButton</span></span>|  
|<span data-ttu-id="19584-128">Düğme</span><span class="sxs-lookup"><span data-stu-id="19584-128">Button</span></span>|<span data-ttu-id="19584-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="19584-129">CheckBox</span></span>|  
|<span data-ttu-id="19584-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="19584-130">ComboBoxEx32</span></span>|<span data-ttu-id="19584-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="19584-131">ComboBox</span></span>|  
|<span data-ttu-id="19584-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="19584-132">ComboBox</span></span>|<span data-ttu-id="19584-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="19584-133">ComboBox</span></span>|  
|<span data-ttu-id="19584-134">Düzenle</span><span class="sxs-lookup"><span data-stu-id="19584-134">Edit</span></span>|<span data-ttu-id="19584-135">Belge</span><span class="sxs-lookup"><span data-stu-id="19584-135">Document</span></span>|  
|<span data-ttu-id="19584-136">Düzenle</span><span class="sxs-lookup"><span data-stu-id="19584-136">Edit</span></span>|<span data-ttu-id="19584-137">Düzenle</span><span class="sxs-lookup"><span data-stu-id="19584-137">Edit</span></span>|  
|<span data-ttu-id="19584-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="19584-138">SysLink</span></span>|<span data-ttu-id="19584-139">Köprü</span><span class="sxs-lookup"><span data-stu-id="19584-139">Hyperlink</span></span>|  
|<span data-ttu-id="19584-140">Statik</span><span class="sxs-lookup"><span data-stu-id="19584-140">Static</span></span>|<span data-ttu-id="19584-141">Metin</span><span class="sxs-lookup"><span data-stu-id="19584-141">Text</span></span>|  
|<span data-ttu-id="19584-142">Statik</span><span class="sxs-lookup"><span data-stu-id="19584-142">Static</span></span>|<span data-ttu-id="19584-143">Görüntü</span><span class="sxs-lookup"><span data-stu-id="19584-143">Image</span></span>|  
|<span data-ttu-id="19584-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="19584-144">SysIPAddress32</span></span>|<span data-ttu-id="19584-145">Özel</span><span class="sxs-lookup"><span data-stu-id="19584-145">Custom</span></span>|  
|<span data-ttu-id="19584-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="19584-146">SysHeader32</span></span>|<span data-ttu-id="19584-147">Üstbilgi/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="19584-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="19584-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="19584-148">SysListView32</span></span>|<span data-ttu-id="19584-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="19584-149">DataGrid</span></span>|  
|<span data-ttu-id="19584-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="19584-150">SysListView32</span></span>|<span data-ttu-id="19584-151">List</span><span class="sxs-lookup"><span data-stu-id="19584-151">List</span></span>|  
|<span data-ttu-id="19584-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="19584-152">ListBox</span></span>|<span data-ttu-id="19584-153">List</span><span class="sxs-lookup"><span data-stu-id="19584-153">List</span></span>|  
|<span data-ttu-id="19584-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="19584-154">ListBox</span></span>|<span data-ttu-id="19584-155">Liste</span><span class="sxs-lookup"><span data-stu-id="19584-155">ListItem</span></span>|  
|<span data-ttu-id="19584-156">#32768</span><span class="sxs-lookup"><span data-stu-id="19584-156">#32768</span></span>|<span data-ttu-id="19584-157">Menü</span><span class="sxs-lookup"><span data-stu-id="19584-157">Menu</span></span>|  
|<span data-ttu-id="19584-158">#32768</span><span class="sxs-lookup"><span data-stu-id="19584-158">#32768</span></span>|<span data-ttu-id="19584-159">MenuItem</span><span class="sxs-lookup"><span data-stu-id="19584-159">MenuItem</span></span>|  
|<span data-ttu-id="19584-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="19584-160">msctls_progress32</span></span>|<span data-ttu-id="19584-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="19584-161">ProgressBar</span></span>|  
|<span data-ttu-id="19584-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="19584-162">RichEdit</span></span>|<span data-ttu-id="19584-163">Belgedeki.</span><span class="sxs-lookup"><span data-stu-id="19584-163">Document.</span></span> <span data-ttu-id="19584-164">Bkz. Note.</span><span class="sxs-lookup"><span data-stu-id="19584-164">See note.</span></span>|  
|<span data-ttu-id="19584-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="19584-165">RichEdit20A</span></span>|<span data-ttu-id="19584-166">Belge</span><span class="sxs-lookup"><span data-stu-id="19584-166">Document</span></span>|  
|<span data-ttu-id="19584-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="19584-167">RichEdit20W</span></span>|<span data-ttu-id="19584-168">Belge</span><span class="sxs-lookup"><span data-stu-id="19584-168">Document</span></span>|  
|<span data-ttu-id="19584-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="19584-169">RichEdit50W</span></span>|<span data-ttu-id="19584-170">Belge</span><span class="sxs-lookup"><span data-stu-id="19584-170">Document</span></span>|  
|<span data-ttu-id="19584-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="19584-171">ScrollBar</span></span>|<span data-ttu-id="19584-172">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="19584-172">Slider</span></span>|  
|<span data-ttu-id="19584-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="19584-173">msctls_trackbar32</span></span>|<span data-ttu-id="19584-174">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="19584-174">Slider</span></span>|  
|<span data-ttu-id="19584-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="19584-175">msctls_updown32</span></span>|<span data-ttu-id="19584-176">Değer Değiştirici</span><span class="sxs-lookup"><span data-stu-id="19584-176">Spinner</span></span>|  
|<span data-ttu-id="19584-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="19584-177">msctls_statusbar32</span></span>|<span data-ttu-id="19584-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="19584-178">StatusBar</span></span>|  
|<span data-ttu-id="19584-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="19584-179">SysTabControl32</span></span>|<span data-ttu-id="19584-180">Tab</span><span class="sxs-lookup"><span data-stu-id="19584-180">Tab</span></span>|  
|<span data-ttu-id="19584-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="19584-181">SysTabControl32</span></span>|<span data-ttu-id="19584-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="19584-182">TabItem</span></span>|  
|<span data-ttu-id="19584-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="19584-183">ToolbarWindow32</span></span>|<span data-ttu-id="19584-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="19584-184">ToolBar</span></span>|  
|<span data-ttu-id="19584-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="19584-185">ToolbarWindow32</span></span>|<span data-ttu-id="19584-186">MenuItem</span><span class="sxs-lookup"><span data-stu-id="19584-186">MenuItem</span></span>|  
|<span data-ttu-id="19584-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="19584-187">ToolbarWindow32</span></span>|<span data-ttu-id="19584-188">Düğme</span><span class="sxs-lookup"><span data-stu-id="19584-188">Button</span></span>|  
|<span data-ttu-id="19584-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="19584-189">ToolbarWindow32</span></span>|<span data-ttu-id="19584-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="19584-190">CheckBox</span></span>|  
|<span data-ttu-id="19584-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="19584-191">ToolbarWindow32</span></span>|<span data-ttu-id="19584-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="19584-192">RadioButton</span></span>|  
|<span data-ttu-id="19584-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="19584-193">ToolbarWindow32</span></span>|<span data-ttu-id="19584-194">Ayırıcı</span><span class="sxs-lookup"><span data-stu-id="19584-194">Separator</span></span>|  
|<span data-ttu-id="19584-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="19584-195">tooltips_class32</span></span>|<span data-ttu-id="19584-196">ToolTip</span><span class="sxs-lookup"><span data-stu-id="19584-196">ToolTip</span></span>|  
|<span data-ttu-id="19584-197">#32774</span><span class="sxs-lookup"><span data-stu-id="19584-197">#32774</span></span>|<span data-ttu-id="19584-198">ToolTip</span><span class="sxs-lookup"><span data-stu-id="19584-198">ToolTip</span></span>|  
|<span data-ttu-id="19584-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="19584-199">ReBarWindow32</span></span>|<span data-ttu-id="19584-200">Araç Çubuğu</span><span class="sxs-lookup"><span data-stu-id="19584-200">Toolbar</span></span>|  
|<span data-ttu-id="19584-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="19584-201">SysTreeView32</span></span>|<span data-ttu-id="19584-202">Ağaç</span><span class="sxs-lookup"><span data-stu-id="19584-202">Tree</span></span>|  
|<span data-ttu-id="19584-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="19584-203">SysTreeView32</span></span>|<span data-ttu-id="19584-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="19584-204">TreeItem</span></span>|  
  
 <span data-ttu-id="19584-205">**Göz önünde** RichEdit denetimi yalnızca Windows Vista ile birlikte gelen sürümler için desteklenir (RichEd20. dll sürümü 3,1 ve üzeri ve MsftEdit. dll sürüm 4,1 ve üzeri).</span><span class="sxs-lookup"><span data-stu-id="19584-205">**Note** The RichEdit control is supported only for versions shipped with Windows Vista (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="19584-206">Aşağıdaki denetimler desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="19584-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="19584-207">Sınıf adı</span><span class="sxs-lookup"><span data-stu-id="19584-207">Class name</span></span>|<span data-ttu-id="19584-208">Denetim türü</span><span class="sxs-lookup"><span data-stu-id="19584-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="19584-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="19584-209">SysAnimate32</span></span>|<span data-ttu-id="19584-210">Görüntü</span><span class="sxs-lookup"><span data-stu-id="19584-210">Image</span></span>|  
|<span data-ttu-id="19584-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="19584-211">SysPager</span></span>|<span data-ttu-id="19584-212">Değer Değiştirici</span><span class="sxs-lookup"><span data-stu-id="19584-212">Spinner</span></span>|  
|<span data-ttu-id="19584-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="19584-213">SysDateTimePick32</span></span>|<span data-ttu-id="19584-214">Özel</span><span class="sxs-lookup"><span data-stu-id="19584-214">Custom</span></span>|  
|<span data-ttu-id="19584-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="19584-215">SysMonthCal32</span></span>|<span data-ttu-id="19584-216">Takvim</span><span class="sxs-lookup"><span data-stu-id="19584-216">Calendar</span></span>|  
|<span data-ttu-id="19584-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="19584-217">MS_WINNOTE</span></span>|<span data-ttu-id="19584-218">Araç ipucu</span><span class="sxs-lookup"><span data-stu-id="19584-218">Tooltip</span></span>|  
|<span data-ttu-id="19584-219">Vbkabarcık</span><span class="sxs-lookup"><span data-stu-id="19584-219">VBBubble</span></span>|<span data-ttu-id="19584-220">Araç ipucu</span><span class="sxs-lookup"><span data-stu-id="19584-220">Tooltip</span></span>|  
|<span data-ttu-id="19584-221">Kaydırma çubuğu (tek başına denetim olarak kullanıldığında)</span><span class="sxs-lookup"><span data-stu-id="19584-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="19584-222">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="19584-222">Slider</span></span>|  
|<span data-ttu-id="19584-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="19584-223">SuperGrid</span></span>|<span data-ttu-id="19584-224">Özel</span><span class="sxs-lookup"><span data-stu-id="19584-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="19584-225">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="19584-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="19584-226">Windows Forms denetimleri, UIAutomationClientsideProviders. dll içindeki istemci tarafı sağlayıcılar aracılığıyla [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] kullanıma sunulur.</span><span class="sxs-lookup"><span data-stu-id="19584-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="19584-227">Bu derleme, UI Otomasyonu istemci uygulamalarıyla kullanılmak üzere otomatik olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="19584-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="19584-228">Genellikle, Win32 ortak denetimleri için yönetilen sarmalayıcılar olan Windows Forms denetimleri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="19584-228">Typically, Windows Forms controls that are managed wrappers for Win32 common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="19584-229">Aşağıdaki denetimler desteklenir.</span><span class="sxs-lookup"><span data-stu-id="19584-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="19584-230">Sınıf Adı</span><span class="sxs-lookup"><span data-stu-id="19584-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="19584-231">Düğme</span><span class="sxs-lookup"><span data-stu-id="19584-231">Button</span></span>|  
|<span data-ttu-id="19584-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="19584-232">CheckBox</span></span>|  
|<span data-ttu-id="19584-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="19584-233">CheckedListBox</span></span>|  
|<span data-ttu-id="19584-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="19584-234">ColorDialog</span></span>|  
|<span data-ttu-id="19584-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="19584-235">ComboBox</span></span>|  
|<span data-ttu-id="19584-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="19584-236">FolderBrowser</span></span>|  
|<span data-ttu-id="19584-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="19584-237">FontDialog</span></span>|  
|<span data-ttu-id="19584-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="19584-238">GroupBox</span></span>|  
|<span data-ttu-id="19584-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="19584-239">HscrollBar</span></span>|  
|<span data-ttu-id="19584-240">'I</span><span class="sxs-lookup"><span data-stu-id="19584-240">ImageList</span></span>|  
|<span data-ttu-id="19584-241">Etiketle</span><span class="sxs-lookup"><span data-stu-id="19584-241">Label</span></span>|  
|<span data-ttu-id="19584-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="19584-242">ListBox</span></span>|  
|<span data-ttu-id="19584-243">ListView</span><span class="sxs-lookup"><span data-stu-id="19584-243">ListView</span></span>|  
|<span data-ttu-id="19584-244">MainMenu/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="19584-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="19584-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="19584-245">MonthCalendar</span></span>|  
|<span data-ttu-id="19584-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="19584-246">NotifyIcon</span></span>|  
|<span data-ttu-id="19584-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="19584-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="19584-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="19584-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="19584-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="19584-249">PrintDialog</span></span>|  
|<span data-ttu-id="19584-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="19584-250">ProgressBar</span></span>|  
|<span data-ttu-id="19584-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="19584-251">RadioButton</span></span>|  
|<span data-ttu-id="19584-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="19584-252">RichTextBox</span></span>|  
|<span data-ttu-id="19584-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="19584-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="19584-254">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="19584-254">ScrollableControl</span></span>|  
|<span data-ttu-id="19584-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="19584-255">SoundPlayer</span></span>|  
|<span data-ttu-id="19584-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="19584-256">StatusBar</span></span>|  
|<span data-ttu-id="19584-257">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="19584-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="19584-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="19584-258">TextBox</span></span>|  
|<span data-ttu-id="19584-259">Zamanlayıcı</span><span class="sxs-lookup"><span data-stu-id="19584-259">Timer</span></span>|  
|<span data-ttu-id="19584-260">Araç Çubuğu</span><span class="sxs-lookup"><span data-stu-id="19584-260">Toolbar</span></span>|  
|<span data-ttu-id="19584-261">ToolTip</span><span class="sxs-lookup"><span data-stu-id="19584-261">ToolTip</span></span>|  
|<span data-ttu-id="19584-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="19584-262">TrackBar</span></span>|  
|<span data-ttu-id="19584-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="19584-263">TreeView</span></span>|  
|<span data-ttu-id="19584-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="19584-264">VscrollBar</span></span>|  
|<span data-ttu-id="19584-265">'A</span><span class="sxs-lookup"><span data-stu-id="19584-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="19584-266">Aşağıdaki denetimler yalnızca Microsoft Etkin Erişilebilirlik desteğiyle [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] açıktır.</span><span class="sxs-lookup"><span data-stu-id="19584-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for Microsoft Active Accessibility.</span></span> <span data-ttu-id="19584-267">Bazı işlevler kullanılamayabilir.</span><span class="sxs-lookup"><span data-stu-id="19584-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="19584-268">Denetim adı</span><span class="sxs-lookup"><span data-stu-id="19584-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="19584-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="19584-269">BindingSource</span></span>|  
|<span data-ttu-id="19584-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="19584-270">DataGrid</span></span>|  
|<span data-ttu-id="19584-271">DataGridView</span><span class="sxs-lookup"><span data-stu-id="19584-271">DataGridView</span></span>|  
|<span data-ttu-id="19584-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="19584-272">DataNavigator</span></span>|  
|<span data-ttu-id="19584-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="19584-273">DomainUpDown</span></span>|  
|<span data-ttu-id="19584-274">Bileþeni</span><span class="sxs-lookup"><span data-stu-id="19584-274">ErrorProvider</span></span>|  
|<span data-ttu-id="19584-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="19584-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="19584-276">Form</span><span class="sxs-lookup"><span data-stu-id="19584-276">Form</span></span>|  
|<span data-ttu-id="19584-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="19584-277">LinkLabel</span></span>|  
|<span data-ttu-id="19584-278">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="19584-278">HelpProvider</span></span>|  
|<span data-ttu-id="19584-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="19584-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="19584-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="19584-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="19584-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="19584-281">NumericUpDown</span></span>|  
|<span data-ttu-id="19584-282">Panel</span><span class="sxs-lookup"><span data-stu-id="19584-282">Panel</span></span>|  
|<span data-ttu-id="19584-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="19584-283">PictureBox</span></span>|  
|<span data-ttu-id="19584-284">Öniz</span><span class="sxs-lookup"><span data-stu-id="19584-284">PrintDocument</span></span>|  
|<span data-ttu-id="19584-285">PrintPreview-denetim</span><span class="sxs-lookup"><span data-stu-id="19584-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="19584-286">PrintPreview-Iletişim kutusu</span><span class="sxs-lookup"><span data-stu-id="19584-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="19584-287">'In</span><span class="sxs-lookup"><span data-stu-id="19584-287">PropertyGrid</span></span>|  
|<span data-ttu-id="19584-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="19584-288">UserControl</span></span>|  
|<span data-ttu-id="19584-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="19584-289">ToolStrip</span></span>|  
|<span data-ttu-id="19584-290">Ekleyecek</span><span class="sxs-lookup"><span data-stu-id="19584-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="19584-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="19584-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="19584-292">Bölücü</span><span class="sxs-lookup"><span data-stu-id="19584-292">Splitter</span></span>|  
|<span data-ttu-id="19584-293">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="19584-293">RaftingContainer</span></span>|  
|<span data-ttu-id="19584-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="19584-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="19584-295">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19584-295">See also</span></span>

- [<span data-ttu-id="19584-296">UI Otomasyonu Denetim Türleri</span><span class="sxs-lookup"><span data-stu-id="19584-296">UI Automation Control Types</span></span>](ui-automation-control-types.md)
