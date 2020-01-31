---
title: Standart Denetimler İçin UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 49277073706444fd611ae41e762442388ac50b71
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789611"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="6a016-102">Standart Denetimler İçin UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="6a016-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
> <span data-ttu-id="6a016-103">Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="6a016-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="6a016-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="6a016-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="6a016-105">Bu konu, [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], Win32 ve Windows Forms çerçeveleri için geliştirilen uygulamalardaki standart denetimler için [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] desteği hakkında bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="6a016-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], Win32, and Windows Forms frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="6a016-106">Windows Presentation Foundation denetimleri</span><span class="sxs-lookup"><span data-stu-id="6a016-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="6a016-107">Kullanıcı etkileşimi için bilgi veya destek sağlayan tüm [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] denetim öğelerinin [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]tam yerel desteği vardır.</span><span class="sxs-lookup"><span data-stu-id="6a016-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="6a016-108">Paneller gibi diğer öğeler [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]görünmüyor.</span><span class="sxs-lookup"><span data-stu-id="6a016-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="6a016-109">Win32 denetimleri</span><span class="sxs-lookup"><span data-stu-id="6a016-109">Win32 Controls</span></span>  
 <span data-ttu-id="6a016-110">Çoğu Win32 denetimi, UIAutomationClientsideProviders. dll içindeki istemci tarafı sağlayıcılar aracılığıyla [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] gösterilir.</span><span class="sxs-lookup"><span data-stu-id="6a016-110">Most Win32 controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="6a016-111">Bu derleme, UI Otomasyonu istemci uygulamalarıyla kullanılmak üzere otomatik olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="6a016-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="6a016-112">Tam destek yalnızca *ComCtrl32. dll*sürüm 6 ' dan denetimler için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="6a016-112">Full support is provided only for controls from version 6 of *ComCtrl32.dll*.</span></span>  
  
 <span data-ttu-id="6a016-113">Aşağıdaki denetimler desteklenir.</span><span class="sxs-lookup"><span data-stu-id="6a016-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="6a016-114">Sınıf adı</span><span class="sxs-lookup"><span data-stu-id="6a016-114">Class name</span></span>|<span data-ttu-id="6a016-115">Denetim türü</span><span class="sxs-lookup"><span data-stu-id="6a016-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="6a016-116">Düğme</span><span class="sxs-lookup"><span data-stu-id="6a016-116">Button</span></span>|<span data-ttu-id="6a016-117">Düğme</span><span class="sxs-lookup"><span data-stu-id="6a016-117">Button</span></span>|  
|<span data-ttu-id="6a016-118">Düğme</span><span class="sxs-lookup"><span data-stu-id="6a016-118">Button</span></span>|<span data-ttu-id="6a016-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="6a016-119">RadioButton</span></span>|  
|<span data-ttu-id="6a016-120">Düğme</span><span class="sxs-lookup"><span data-stu-id="6a016-120">Button</span></span>|<span data-ttu-id="6a016-121">Grup</span><span class="sxs-lookup"><span data-stu-id="6a016-121">Group</span></span>|  
|<span data-ttu-id="6a016-122">Düğme</span><span class="sxs-lookup"><span data-stu-id="6a016-122">Button</span></span>|<span data-ttu-id="6a016-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="6a016-123">CheckBox</span></span>|  
|<span data-ttu-id="6a016-124">Düğme</span><span class="sxs-lookup"><span data-stu-id="6a016-124">Button</span></span>|<span data-ttu-id="6a016-125">Köprü</span><span class="sxs-lookup"><span data-stu-id="6a016-125">Hyperlink</span></span>|  
|<span data-ttu-id="6a016-126">Düğme</span><span class="sxs-lookup"><span data-stu-id="6a016-126">Button</span></span>|<span data-ttu-id="6a016-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="6a016-127">SplitButton</span></span>|  
|<span data-ttu-id="6a016-128">Düğme</span><span class="sxs-lookup"><span data-stu-id="6a016-128">Button</span></span>|<span data-ttu-id="6a016-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="6a016-129">CheckBox</span></span>|  
|<span data-ttu-id="6a016-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="6a016-130">ComboBoxEx32</span></span>|<span data-ttu-id="6a016-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="6a016-131">ComboBox</span></span>|  
|<span data-ttu-id="6a016-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="6a016-132">ComboBox</span></span>|<span data-ttu-id="6a016-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="6a016-133">ComboBox</span></span>|  
|<span data-ttu-id="6a016-134">Düzenle</span><span class="sxs-lookup"><span data-stu-id="6a016-134">Edit</span></span>|<span data-ttu-id="6a016-135">Belge</span><span class="sxs-lookup"><span data-stu-id="6a016-135">Document</span></span>|  
|<span data-ttu-id="6a016-136">Düzenle</span><span class="sxs-lookup"><span data-stu-id="6a016-136">Edit</span></span>|<span data-ttu-id="6a016-137">Düzenle</span><span class="sxs-lookup"><span data-stu-id="6a016-137">Edit</span></span>|  
|<span data-ttu-id="6a016-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="6a016-138">SysLink</span></span>|<span data-ttu-id="6a016-139">Köprü</span><span class="sxs-lookup"><span data-stu-id="6a016-139">Hyperlink</span></span>|  
|<span data-ttu-id="6a016-140">Statik</span><span class="sxs-lookup"><span data-stu-id="6a016-140">Static</span></span>|<span data-ttu-id="6a016-141">Metin</span><span class="sxs-lookup"><span data-stu-id="6a016-141">Text</span></span>|  
|<span data-ttu-id="6a016-142">Statik</span><span class="sxs-lookup"><span data-stu-id="6a016-142">Static</span></span>|<span data-ttu-id="6a016-143">Görüntü</span><span class="sxs-lookup"><span data-stu-id="6a016-143">Image</span></span>|  
|<span data-ttu-id="6a016-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="6a016-144">SysIPAddress32</span></span>|<span data-ttu-id="6a016-145">Özel</span><span class="sxs-lookup"><span data-stu-id="6a016-145">Custom</span></span>|  
|<span data-ttu-id="6a016-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="6a016-146">SysHeader32</span></span>|<span data-ttu-id="6a016-147">Üstbilgi/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="6a016-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="6a016-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="6a016-148">SysListView32</span></span>|<span data-ttu-id="6a016-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="6a016-149">DataGrid</span></span>|  
|<span data-ttu-id="6a016-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="6a016-150">SysListView32</span></span>|<span data-ttu-id="6a016-151">List</span><span class="sxs-lookup"><span data-stu-id="6a016-151">List</span></span>|  
|<span data-ttu-id="6a016-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="6a016-152">ListBox</span></span>|<span data-ttu-id="6a016-153">List</span><span class="sxs-lookup"><span data-stu-id="6a016-153">List</span></span>|  
|<span data-ttu-id="6a016-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="6a016-154">ListBox</span></span>|<span data-ttu-id="6a016-155">Liste</span><span class="sxs-lookup"><span data-stu-id="6a016-155">ListItem</span></span>|  
|<span data-ttu-id="6a016-156">#32768</span><span class="sxs-lookup"><span data-stu-id="6a016-156">#32768</span></span>|<span data-ttu-id="6a016-157">Menü</span><span class="sxs-lookup"><span data-stu-id="6a016-157">Menu</span></span>|  
|<span data-ttu-id="6a016-158">#32768</span><span class="sxs-lookup"><span data-stu-id="6a016-158">#32768</span></span>|<span data-ttu-id="6a016-159">MenuItem</span><span class="sxs-lookup"><span data-stu-id="6a016-159">MenuItem</span></span>|  
|<span data-ttu-id="6a016-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="6a016-160">msctls_progress32</span></span>|<span data-ttu-id="6a016-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="6a016-161">ProgressBar</span></span>|  
|<span data-ttu-id="6a016-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="6a016-162">RichEdit</span></span>|<span data-ttu-id="6a016-163">Belgedeki.</span><span class="sxs-lookup"><span data-stu-id="6a016-163">Document.</span></span> <span data-ttu-id="6a016-164">Bkz. Note.</span><span class="sxs-lookup"><span data-stu-id="6a016-164">See note.</span></span>|  
|<span data-ttu-id="6a016-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="6a016-165">RichEdit20A</span></span>|<span data-ttu-id="6a016-166">Belge</span><span class="sxs-lookup"><span data-stu-id="6a016-166">Document</span></span>|  
|<span data-ttu-id="6a016-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="6a016-167">RichEdit20W</span></span>|<span data-ttu-id="6a016-168">Belge</span><span class="sxs-lookup"><span data-stu-id="6a016-168">Document</span></span>|  
|<span data-ttu-id="6a016-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="6a016-169">RichEdit50W</span></span>|<span data-ttu-id="6a016-170">Belge</span><span class="sxs-lookup"><span data-stu-id="6a016-170">Document</span></span>|  
|<span data-ttu-id="6a016-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="6a016-171">ScrollBar</span></span>|<span data-ttu-id="6a016-172">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="6a016-172">Slider</span></span>|  
|<span data-ttu-id="6a016-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="6a016-173">msctls_trackbar32</span></span>|<span data-ttu-id="6a016-174">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="6a016-174">Slider</span></span>|  
|<span data-ttu-id="6a016-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="6a016-175">msctls_updown32</span></span>|<span data-ttu-id="6a016-176">Değer Değiştirici</span><span class="sxs-lookup"><span data-stu-id="6a016-176">Spinner</span></span>|  
|<span data-ttu-id="6a016-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="6a016-177">msctls_statusbar32</span></span>|<span data-ttu-id="6a016-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="6a016-178">StatusBar</span></span>|  
|<span data-ttu-id="6a016-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="6a016-179">SysTabControl32</span></span>|<span data-ttu-id="6a016-180">Tab</span><span class="sxs-lookup"><span data-stu-id="6a016-180">Tab</span></span>|  
|<span data-ttu-id="6a016-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="6a016-181">SysTabControl32</span></span>|<span data-ttu-id="6a016-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="6a016-182">TabItem</span></span>|  
|<span data-ttu-id="6a016-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="6a016-183">ToolbarWindow32</span></span>|<span data-ttu-id="6a016-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="6a016-184">ToolBar</span></span>|  
|<span data-ttu-id="6a016-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="6a016-185">ToolbarWindow32</span></span>|<span data-ttu-id="6a016-186">MenuItem</span><span class="sxs-lookup"><span data-stu-id="6a016-186">MenuItem</span></span>|  
|<span data-ttu-id="6a016-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="6a016-187">ToolbarWindow32</span></span>|<span data-ttu-id="6a016-188">Düğme</span><span class="sxs-lookup"><span data-stu-id="6a016-188">Button</span></span>|  
|<span data-ttu-id="6a016-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="6a016-189">ToolbarWindow32</span></span>|<span data-ttu-id="6a016-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="6a016-190">CheckBox</span></span>|  
|<span data-ttu-id="6a016-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="6a016-191">ToolbarWindow32</span></span>|<span data-ttu-id="6a016-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="6a016-192">RadioButton</span></span>|  
|<span data-ttu-id="6a016-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="6a016-193">ToolbarWindow32</span></span>|<span data-ttu-id="6a016-194">Ayırıcı</span><span class="sxs-lookup"><span data-stu-id="6a016-194">Separator</span></span>|  
|<span data-ttu-id="6a016-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="6a016-195">tooltips_class32</span></span>|<span data-ttu-id="6a016-196">ToolTip</span><span class="sxs-lookup"><span data-stu-id="6a016-196">ToolTip</span></span>|  
|<span data-ttu-id="6a016-197">#32774</span><span class="sxs-lookup"><span data-stu-id="6a016-197">#32774</span></span>|<span data-ttu-id="6a016-198">ToolTip</span><span class="sxs-lookup"><span data-stu-id="6a016-198">ToolTip</span></span>|  
|<span data-ttu-id="6a016-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="6a016-199">ReBarWindow32</span></span>|<span data-ttu-id="6a016-200">Araç Çubuğu</span><span class="sxs-lookup"><span data-stu-id="6a016-200">Toolbar</span></span>|  
|<span data-ttu-id="6a016-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="6a016-201">SysTreeView32</span></span>|<span data-ttu-id="6a016-202">Ağaç</span><span class="sxs-lookup"><span data-stu-id="6a016-202">Tree</span></span>|  
|<span data-ttu-id="6a016-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="6a016-203">SysTreeView32</span></span>|<span data-ttu-id="6a016-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="6a016-204">TreeItem</span></span>|  
  
 <span data-ttu-id="6a016-205">**Göz önünde** RichEdit denetimi yalnızca Windows Vista ile birlikte gelen sürümler için desteklenir (RichEd20. dll sürümü 3,1 ve üzeri ve MsftEdit. dll sürüm 4,1 ve üzeri).</span><span class="sxs-lookup"><span data-stu-id="6a016-205">**Note** The RichEdit control is supported only for versions shipped with Windows Vista (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="6a016-206">Aşağıdaki denetimler desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="6a016-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="6a016-207">Sınıf adı</span><span class="sxs-lookup"><span data-stu-id="6a016-207">Class name</span></span>|<span data-ttu-id="6a016-208">Denetim türü</span><span class="sxs-lookup"><span data-stu-id="6a016-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="6a016-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="6a016-209">SysAnimate32</span></span>|<span data-ttu-id="6a016-210">Görüntü</span><span class="sxs-lookup"><span data-stu-id="6a016-210">Image</span></span>|  
|<span data-ttu-id="6a016-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="6a016-211">SysPager</span></span>|<span data-ttu-id="6a016-212">Değer Değiştirici</span><span class="sxs-lookup"><span data-stu-id="6a016-212">Spinner</span></span>|  
|<span data-ttu-id="6a016-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="6a016-213">SysDateTimePick32</span></span>|<span data-ttu-id="6a016-214">Özel</span><span class="sxs-lookup"><span data-stu-id="6a016-214">Custom</span></span>|  
|<span data-ttu-id="6a016-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="6a016-215">SysMonthCal32</span></span>|<span data-ttu-id="6a016-216">Takvim</span><span class="sxs-lookup"><span data-stu-id="6a016-216">Calendar</span></span>|  
|<span data-ttu-id="6a016-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="6a016-217">MS_WINNOTE</span></span>|<span data-ttu-id="6a016-218">ipucuna</span><span class="sxs-lookup"><span data-stu-id="6a016-218">Tooltip</span></span>|  
|<span data-ttu-id="6a016-219">Vbkabarcık</span><span class="sxs-lookup"><span data-stu-id="6a016-219">VBBubble</span></span>|<span data-ttu-id="6a016-220">ipucuna</span><span class="sxs-lookup"><span data-stu-id="6a016-220">Tooltip</span></span>|  
|<span data-ttu-id="6a016-221">Kaydırma çubuğu (tek başına denetim olarak kullanıldığında)</span><span class="sxs-lookup"><span data-stu-id="6a016-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="6a016-222">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="6a016-222">Slider</span></span>|  
|<span data-ttu-id="6a016-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="6a016-223">SuperGrid</span></span>|<span data-ttu-id="6a016-224">Özel</span><span class="sxs-lookup"><span data-stu-id="6a016-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="6a016-225">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="6a016-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="6a016-226">Windows Forms denetimleri, UIAutomationClientsideProviders. dll içindeki istemci tarafı sağlayıcılar aracılığıyla [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] kullanıma sunulur.</span><span class="sxs-lookup"><span data-stu-id="6a016-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="6a016-227">Bu derleme, UI Otomasyonu istemci uygulamalarıyla kullanılmak üzere otomatik olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="6a016-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="6a016-228">Genellikle, Win32 ortak denetimleri için yönetilen sarmalayıcılar olan Windows Forms denetimleri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="6a016-228">Typically, Windows Forms controls that are managed wrappers for Win32 common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="6a016-229">Aşağıdaki denetimler desteklenir.</span><span class="sxs-lookup"><span data-stu-id="6a016-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="6a016-230">Sınıf Adı</span><span class="sxs-lookup"><span data-stu-id="6a016-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="6a016-231">Düğme</span><span class="sxs-lookup"><span data-stu-id="6a016-231">Button</span></span>|  
|<span data-ttu-id="6a016-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="6a016-232">CheckBox</span></span>|  
|<span data-ttu-id="6a016-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="6a016-233">CheckedListBox</span></span>|  
|<span data-ttu-id="6a016-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="6a016-234">ColorDialog</span></span>|  
|<span data-ttu-id="6a016-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="6a016-235">ComboBox</span></span>|  
|<span data-ttu-id="6a016-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="6a016-236">FolderBrowser</span></span>|  
|<span data-ttu-id="6a016-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="6a016-237">FontDialog</span></span>|  
|<span data-ttu-id="6a016-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="6a016-238">GroupBox</span></span>|  
|<span data-ttu-id="6a016-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="6a016-239">HscrollBar</span></span>|  
|<span data-ttu-id="6a016-240">'I</span><span class="sxs-lookup"><span data-stu-id="6a016-240">ImageList</span></span>|  
|<span data-ttu-id="6a016-241">Etiketle</span><span class="sxs-lookup"><span data-stu-id="6a016-241">Label</span></span>|  
|<span data-ttu-id="6a016-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="6a016-242">ListBox</span></span>|  
|<span data-ttu-id="6a016-243">ListView</span><span class="sxs-lookup"><span data-stu-id="6a016-243">ListView</span></span>|  
|<span data-ttu-id="6a016-244">MainMenu/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="6a016-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="6a016-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="6a016-245">MonthCalendar</span></span>|  
|<span data-ttu-id="6a016-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="6a016-246">NotifyIcon</span></span>|  
|<span data-ttu-id="6a016-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="6a016-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="6a016-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="6a016-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="6a016-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="6a016-249">PrintDialog</span></span>|  
|<span data-ttu-id="6a016-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="6a016-250">ProgressBar</span></span>|  
|<span data-ttu-id="6a016-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="6a016-251">RadioButton</span></span>|  
|<span data-ttu-id="6a016-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="6a016-252">RichTextBox</span></span>|  
|<span data-ttu-id="6a016-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="6a016-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="6a016-254">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="6a016-254">ScrollableControl</span></span>|  
|<span data-ttu-id="6a016-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="6a016-255">SoundPlayer</span></span>|  
|<span data-ttu-id="6a016-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="6a016-256">StatusBar</span></span>|  
|<span data-ttu-id="6a016-257">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="6a016-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="6a016-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="6a016-258">TextBox</span></span>|  
|<span data-ttu-id="6a016-259">Zamanlayıcı</span><span class="sxs-lookup"><span data-stu-id="6a016-259">Timer</span></span>|  
|<span data-ttu-id="6a016-260">Araç Çubuğu</span><span class="sxs-lookup"><span data-stu-id="6a016-260">Toolbar</span></span>|  
|<span data-ttu-id="6a016-261">ToolTip</span><span class="sxs-lookup"><span data-stu-id="6a016-261">ToolTip</span></span>|  
|<span data-ttu-id="6a016-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="6a016-262">TrackBar</span></span>|  
|<span data-ttu-id="6a016-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="6a016-263">TreeView</span></span>|  
|<span data-ttu-id="6a016-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="6a016-264">VscrollBar</span></span>|  
|<span data-ttu-id="6a016-265">'A</span><span class="sxs-lookup"><span data-stu-id="6a016-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="6a016-266">Aşağıdaki denetimler yalnızca Microsoft Etkin Erişilebilirlik desteğiyle [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] açıktır.</span><span class="sxs-lookup"><span data-stu-id="6a016-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for Microsoft Active Accessibility.</span></span> <span data-ttu-id="6a016-267">Bazı işlevler kullanılamayabilir.</span><span class="sxs-lookup"><span data-stu-id="6a016-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="6a016-268">Denetim adı</span><span class="sxs-lookup"><span data-stu-id="6a016-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="6a016-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="6a016-269">BindingSource</span></span>|  
|<span data-ttu-id="6a016-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="6a016-270">DataGrid</span></span>|  
|<span data-ttu-id="6a016-271">DataGridView</span><span class="sxs-lookup"><span data-stu-id="6a016-271">DataGridView</span></span>|  
|<span data-ttu-id="6a016-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="6a016-272">DataNavigator</span></span>|  
|<span data-ttu-id="6a016-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="6a016-273">DomainUpDown</span></span>|  
|<span data-ttu-id="6a016-274">Bileþeni</span><span class="sxs-lookup"><span data-stu-id="6a016-274">ErrorProvider</span></span>|  
|<span data-ttu-id="6a016-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="6a016-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="6a016-276">Form</span><span class="sxs-lookup"><span data-stu-id="6a016-276">Form</span></span>|  
|<span data-ttu-id="6a016-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="6a016-277">LinkLabel</span></span>|  
|<span data-ttu-id="6a016-278">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="6a016-278">HelpProvider</span></span>|  
|<span data-ttu-id="6a016-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="6a016-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="6a016-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="6a016-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="6a016-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="6a016-281">NumericUpDown</span></span>|  
|<span data-ttu-id="6a016-282">Panel</span><span class="sxs-lookup"><span data-stu-id="6a016-282">Panel</span></span>|  
|<span data-ttu-id="6a016-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="6a016-283">PictureBox</span></span>|  
|<span data-ttu-id="6a016-284">Öniz</span><span class="sxs-lookup"><span data-stu-id="6a016-284">PrintDocument</span></span>|  
|<span data-ttu-id="6a016-285">PrintPreview-denetim</span><span class="sxs-lookup"><span data-stu-id="6a016-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="6a016-286">PrintPreview-Iletişim kutusu</span><span class="sxs-lookup"><span data-stu-id="6a016-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="6a016-287">'In</span><span class="sxs-lookup"><span data-stu-id="6a016-287">PropertyGrid</span></span>|  
|<span data-ttu-id="6a016-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="6a016-288">UserControl</span></span>|  
|<span data-ttu-id="6a016-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="6a016-289">ToolStrip</span></span>|  
|<span data-ttu-id="6a016-290">Ekleyecek</span><span class="sxs-lookup"><span data-stu-id="6a016-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="6a016-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="6a016-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="6a016-292">Bölücü</span><span class="sxs-lookup"><span data-stu-id="6a016-292">Splitter</span></span>|  
|<span data-ttu-id="6a016-293">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="6a016-293">RaftingContainer</span></span>|  
|<span data-ttu-id="6a016-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="6a016-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6a016-295">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a016-295">See also</span></span>

- [<span data-ttu-id="6a016-296">UI Otomasyonu Denetim Türleri</span><span class="sxs-lookup"><span data-stu-id="6a016-296">UI Automation Control Types</span></span>](ui-automation-control-types.md)
