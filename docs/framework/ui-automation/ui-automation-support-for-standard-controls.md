---
title: Standart Denetimler İçin UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 36028d589e98177f6a0e83092edd656860b1a8d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179857"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="673b7-102">Standart Denetimler İçin UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="673b7-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
> <span data-ttu-id="673b7-103">Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="673b7-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="673b7-104">Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="673b7-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="673b7-105">Bu [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]konu, [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] Win32 ve Windows Forms çerçeveleri için geliştirilen uygulamalarda standart denetimdesteği hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="673b7-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], Win32, and Windows Forms frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="673b7-106">Windows Sunum Temel Denetimleri</span><span class="sxs-lookup"><span data-stu-id="673b7-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="673b7-107">Kullanıcı [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] etkileşimi için bilgi veya destek sağlayan tüm [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]denetim öğeleri için tam yerel destek var.</span><span class="sxs-lookup"><span data-stu-id="673b7-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="673b7-108">Paneller gibi diğer öğeler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]görünmez.</span><span class="sxs-lookup"><span data-stu-id="673b7-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>
## <a name="win32-controls"></a><span data-ttu-id="673b7-109">Win32 Kontroller</span><span class="sxs-lookup"><span data-stu-id="673b7-109">Win32 Controls</span></span>  
 <span data-ttu-id="673b7-110">Win32 denetimlerinin çoğu, UIAutomationClientsideProviders.dll'deki istemci tarafındaki sağlayıcılar [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] aracılığıyla uygulanır.</span><span class="sxs-lookup"><span data-stu-id="673b7-110">Most Win32 controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="673b7-111">Bu derleme otomatik olarak UI Automation istemci uygulamalarında kullanılmak üzere kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="673b7-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="673b7-112">Tam destek yalnızca *ComCtrl32.dll'nin*6.</span><span class="sxs-lookup"><span data-stu-id="673b7-112">Full support is provided only for controls from version 6 of *ComCtrl32.dll*.</span></span>  
  
 <span data-ttu-id="673b7-113">Aşağıdaki denetimler desteklenir.</span><span class="sxs-lookup"><span data-stu-id="673b7-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="673b7-114">Sınıf adı</span><span class="sxs-lookup"><span data-stu-id="673b7-114">Class name</span></span>|<span data-ttu-id="673b7-115">Kontrol Türü</span><span class="sxs-lookup"><span data-stu-id="673b7-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="673b7-116">Düğme</span><span class="sxs-lookup"><span data-stu-id="673b7-116">Button</span></span>|<span data-ttu-id="673b7-117">Düğme</span><span class="sxs-lookup"><span data-stu-id="673b7-117">Button</span></span>|  
|<span data-ttu-id="673b7-118">Düğme</span><span class="sxs-lookup"><span data-stu-id="673b7-118">Button</span></span>|<span data-ttu-id="673b7-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="673b7-119">RadioButton</span></span>|  
|<span data-ttu-id="673b7-120">Düğme</span><span class="sxs-lookup"><span data-stu-id="673b7-120">Button</span></span>|<span data-ttu-id="673b7-121">Grup</span><span class="sxs-lookup"><span data-stu-id="673b7-121">Group</span></span>|  
|<span data-ttu-id="673b7-122">Düğme</span><span class="sxs-lookup"><span data-stu-id="673b7-122">Button</span></span>|<span data-ttu-id="673b7-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="673b7-123">CheckBox</span></span>|  
|<span data-ttu-id="673b7-124">Düğme</span><span class="sxs-lookup"><span data-stu-id="673b7-124">Button</span></span>|<span data-ttu-id="673b7-125">Köprü</span><span class="sxs-lookup"><span data-stu-id="673b7-125">Hyperlink</span></span>|  
|<span data-ttu-id="673b7-126">Düğme</span><span class="sxs-lookup"><span data-stu-id="673b7-126">Button</span></span>|<span data-ttu-id="673b7-127">Splitbutton</span><span class="sxs-lookup"><span data-stu-id="673b7-127">SplitButton</span></span>|  
|<span data-ttu-id="673b7-128">Düğme</span><span class="sxs-lookup"><span data-stu-id="673b7-128">Button</span></span>|<span data-ttu-id="673b7-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="673b7-129">CheckBox</span></span>|  
|<span data-ttu-id="673b7-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="673b7-130">ComboBoxEx32</span></span>|<span data-ttu-id="673b7-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="673b7-131">ComboBox</span></span>|  
|<span data-ttu-id="673b7-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="673b7-132">ComboBox</span></span>|<span data-ttu-id="673b7-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="673b7-133">ComboBox</span></span>|  
|<span data-ttu-id="673b7-134">Düzenle</span><span class="sxs-lookup"><span data-stu-id="673b7-134">Edit</span></span>|<span data-ttu-id="673b7-135">Belge</span><span class="sxs-lookup"><span data-stu-id="673b7-135">Document</span></span>|  
|<span data-ttu-id="673b7-136">Düzenle</span><span class="sxs-lookup"><span data-stu-id="673b7-136">Edit</span></span>|<span data-ttu-id="673b7-137">Düzenle</span><span class="sxs-lookup"><span data-stu-id="673b7-137">Edit</span></span>|  
|<span data-ttu-id="673b7-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="673b7-138">SysLink</span></span>|<span data-ttu-id="673b7-139">Köprü</span><span class="sxs-lookup"><span data-stu-id="673b7-139">Hyperlink</span></span>|  
|<span data-ttu-id="673b7-140">Statik</span><span class="sxs-lookup"><span data-stu-id="673b7-140">Static</span></span>|<span data-ttu-id="673b7-141">Metin</span><span class="sxs-lookup"><span data-stu-id="673b7-141">Text</span></span>|  
|<span data-ttu-id="673b7-142">Statik</span><span class="sxs-lookup"><span data-stu-id="673b7-142">Static</span></span>|<span data-ttu-id="673b7-143">Görüntü</span><span class="sxs-lookup"><span data-stu-id="673b7-143">Image</span></span>|  
|<span data-ttu-id="673b7-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="673b7-144">SysIPAddress32</span></span>|<span data-ttu-id="673b7-145">Özel</span><span class="sxs-lookup"><span data-stu-id="673b7-145">Custom</span></span>|  
|<span data-ttu-id="673b7-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="673b7-146">SysHeader32</span></span>|<span data-ttu-id="673b7-147">Üstbilgi/Üstbilgi Öğesi</span><span class="sxs-lookup"><span data-stu-id="673b7-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="673b7-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="673b7-148">SysListView32</span></span>|<span data-ttu-id="673b7-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="673b7-149">DataGrid</span></span>|  
|<span data-ttu-id="673b7-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="673b7-150">SysListView32</span></span>|<span data-ttu-id="673b7-151">Liste</span><span class="sxs-lookup"><span data-stu-id="673b7-151">List</span></span>|  
|<span data-ttu-id="673b7-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="673b7-152">ListBox</span></span>|<span data-ttu-id="673b7-153">Liste</span><span class="sxs-lookup"><span data-stu-id="673b7-153">List</span></span>|  
|<span data-ttu-id="673b7-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="673b7-154">ListBox</span></span>|<span data-ttu-id="673b7-155">Listıtem</span><span class="sxs-lookup"><span data-stu-id="673b7-155">ListItem</span></span>|  
|<span data-ttu-id="673b7-156">#32768</span><span class="sxs-lookup"><span data-stu-id="673b7-156">#32768</span></span>|<span data-ttu-id="673b7-157">Menü</span><span class="sxs-lookup"><span data-stu-id="673b7-157">Menu</span></span>|  
|<span data-ttu-id="673b7-158">#32768</span><span class="sxs-lookup"><span data-stu-id="673b7-158">#32768</span></span>|<span data-ttu-id="673b7-159">MenuItem</span><span class="sxs-lookup"><span data-stu-id="673b7-159">MenuItem</span></span>|  
|<span data-ttu-id="673b7-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="673b7-160">msctls_progress32</span></span>|<span data-ttu-id="673b7-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="673b7-161">ProgressBar</span></span>|  
|<span data-ttu-id="673b7-162">Richedit</span><span class="sxs-lookup"><span data-stu-id="673b7-162">RichEdit</span></span>|<span data-ttu-id="673b7-163">Belge.</span><span class="sxs-lookup"><span data-stu-id="673b7-163">Document.</span></span> <span data-ttu-id="673b7-164">Nota bakın.</span><span class="sxs-lookup"><span data-stu-id="673b7-164">See note.</span></span>|  
|<span data-ttu-id="673b7-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="673b7-165">RichEdit20A</span></span>|<span data-ttu-id="673b7-166">Belge</span><span class="sxs-lookup"><span data-stu-id="673b7-166">Document</span></span>|  
|<span data-ttu-id="673b7-167">ZenginEdit20W</span><span class="sxs-lookup"><span data-stu-id="673b7-167">RichEdit20W</span></span>|<span data-ttu-id="673b7-168">Belge</span><span class="sxs-lookup"><span data-stu-id="673b7-168">Document</span></span>|  
|<span data-ttu-id="673b7-169">ZenginEdit50W</span><span class="sxs-lookup"><span data-stu-id="673b7-169">RichEdit50W</span></span>|<span data-ttu-id="673b7-170">Belge</span><span class="sxs-lookup"><span data-stu-id="673b7-170">Document</span></span>|  
|<span data-ttu-id="673b7-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="673b7-171">ScrollBar</span></span>|<span data-ttu-id="673b7-172">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="673b7-172">Slider</span></span>|  
|<span data-ttu-id="673b7-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="673b7-173">msctls_trackbar32</span></span>|<span data-ttu-id="673b7-174">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="673b7-174">Slider</span></span>|  
|<span data-ttu-id="673b7-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="673b7-175">msctls_updown32</span></span>|<span data-ttu-id="673b7-176">Değer Değiştirici</span><span class="sxs-lookup"><span data-stu-id="673b7-176">Spinner</span></span>|  
|<span data-ttu-id="673b7-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="673b7-177">msctls_statusbar32</span></span>|<span data-ttu-id="673b7-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="673b7-178">StatusBar</span></span>|  
|<span data-ttu-id="673b7-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="673b7-179">SysTabControl32</span></span>|<span data-ttu-id="673b7-180">Tab</span><span class="sxs-lookup"><span data-stu-id="673b7-180">Tab</span></span>|  
|<span data-ttu-id="673b7-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="673b7-181">SysTabControl32</span></span>|<span data-ttu-id="673b7-182">Tabıtem</span><span class="sxs-lookup"><span data-stu-id="673b7-182">TabItem</span></span>|  
|<span data-ttu-id="673b7-183">Araç ÇubuğuWindow32</span><span class="sxs-lookup"><span data-stu-id="673b7-183">ToolbarWindow32</span></span>|<span data-ttu-id="673b7-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="673b7-184">ToolBar</span></span>|  
|<span data-ttu-id="673b7-185">Araç ÇubuğuWindow32</span><span class="sxs-lookup"><span data-stu-id="673b7-185">ToolbarWindow32</span></span>|<span data-ttu-id="673b7-186">MenuItem</span><span class="sxs-lookup"><span data-stu-id="673b7-186">MenuItem</span></span>|  
|<span data-ttu-id="673b7-187">Araç ÇubuğuWindow32</span><span class="sxs-lookup"><span data-stu-id="673b7-187">ToolbarWindow32</span></span>|<span data-ttu-id="673b7-188">Düğme</span><span class="sxs-lookup"><span data-stu-id="673b7-188">Button</span></span>|  
|<span data-ttu-id="673b7-189">Araç ÇubuğuWindow32</span><span class="sxs-lookup"><span data-stu-id="673b7-189">ToolbarWindow32</span></span>|<span data-ttu-id="673b7-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="673b7-190">CheckBox</span></span>|  
|<span data-ttu-id="673b7-191">Araç ÇubuğuWindow32</span><span class="sxs-lookup"><span data-stu-id="673b7-191">ToolbarWindow32</span></span>|<span data-ttu-id="673b7-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="673b7-192">RadioButton</span></span>|  
|<span data-ttu-id="673b7-193">Araç ÇubuğuWindow32</span><span class="sxs-lookup"><span data-stu-id="673b7-193">ToolbarWindow32</span></span>|<span data-ttu-id="673b7-194">Ayırıcı</span><span class="sxs-lookup"><span data-stu-id="673b7-194">Separator</span></span>|  
|<span data-ttu-id="673b7-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="673b7-195">tooltips_class32</span></span>|<span data-ttu-id="673b7-196">ToolTip</span><span class="sxs-lookup"><span data-stu-id="673b7-196">ToolTip</span></span>|  
|<span data-ttu-id="673b7-197">#32774</span><span class="sxs-lookup"><span data-stu-id="673b7-197">#32774</span></span>|<span data-ttu-id="673b7-198">ToolTip</span><span class="sxs-lookup"><span data-stu-id="673b7-198">ToolTip</span></span>|  
|<span data-ttu-id="673b7-199">RebarWindow32</span><span class="sxs-lookup"><span data-stu-id="673b7-199">ReBarWindow32</span></span>|<span data-ttu-id="673b7-200">Araç Çubuğu</span><span class="sxs-lookup"><span data-stu-id="673b7-200">Toolbar</span></span>|  
|<span data-ttu-id="673b7-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="673b7-201">SysTreeView32</span></span>|<span data-ttu-id="673b7-202">Ağaç</span><span class="sxs-lookup"><span data-stu-id="673b7-202">Tree</span></span>|  
|<span data-ttu-id="673b7-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="673b7-203">SysTreeView32</span></span>|<span data-ttu-id="673b7-204">Treeıtem</span><span class="sxs-lookup"><span data-stu-id="673b7-204">TreeItem</span></span>|  
  
 <span data-ttu-id="673b7-205">**Not** RichEdit denetimi yalnızca Windows Vista (RichEd20.dll sürüm 3.1 ve daha sonra ve MsftEdit.dll sürüm 4.1 ve sonraki sürümlerde) ile gönderilen sürümler için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="673b7-205">**Note** The RichEdit control is supported only for versions shipped with Windows Vista (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="673b7-206">Aşağıdaki denetimler desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="673b7-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="673b7-207">Sınıf adı</span><span class="sxs-lookup"><span data-stu-id="673b7-207">Class name</span></span>|<span data-ttu-id="673b7-208">Denetim türü</span><span class="sxs-lookup"><span data-stu-id="673b7-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="673b7-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="673b7-209">SysAnimate32</span></span>|<span data-ttu-id="673b7-210">Görüntü</span><span class="sxs-lookup"><span data-stu-id="673b7-210">Image</span></span>|  
|<span data-ttu-id="673b7-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="673b7-211">SysPager</span></span>|<span data-ttu-id="673b7-212">Değer Değiştirici</span><span class="sxs-lookup"><span data-stu-id="673b7-212">Spinner</span></span>|  
|<span data-ttu-id="673b7-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="673b7-213">SysDateTimePick32</span></span>|<span data-ttu-id="673b7-214">Özel</span><span class="sxs-lookup"><span data-stu-id="673b7-214">Custom</span></span>|  
|<span data-ttu-id="673b7-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="673b7-215">SysMonthCal32</span></span>|<span data-ttu-id="673b7-216">Takvim</span><span class="sxs-lookup"><span data-stu-id="673b7-216">Calendar</span></span>|  
|<span data-ttu-id="673b7-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="673b7-217">MS_WINNOTE</span></span>|<span data-ttu-id="673b7-218">Araç İpucu</span><span class="sxs-lookup"><span data-stu-id="673b7-218">Tooltip</span></span>|  
|<span data-ttu-id="673b7-219">VBBubble</span><span class="sxs-lookup"><span data-stu-id="673b7-219">VBBubble</span></span>|<span data-ttu-id="673b7-220">Araç İpucu</span><span class="sxs-lookup"><span data-stu-id="673b7-220">Tooltip</span></span>|  
|<span data-ttu-id="673b7-221">ScrollBar (bağımsız denetim olarak kullanıldığında)</span><span class="sxs-lookup"><span data-stu-id="673b7-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="673b7-222">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="673b7-222">Slider</span></span>|  
|<span data-ttu-id="673b7-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="673b7-223">SuperGrid</span></span>|<span data-ttu-id="673b7-224">Özel</span><span class="sxs-lookup"><span data-stu-id="673b7-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>
## <a name="windows-forms-controls"></a><span data-ttu-id="673b7-225">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="673b7-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="673b7-226">Windows Forms denetimleri, UIAutomationClientsideProviders.dll'deki istemci tarafındaki sağlayıcılar [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] aracılığıyla uygulanır.</span><span class="sxs-lookup"><span data-stu-id="673b7-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="673b7-227">Bu derleme otomatik olarak UI Automation istemci uygulamalarında kullanılmak üzere kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="673b7-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="673b7-228">Genellikle, Win32 ortak denetimleri için yönetilen Windows Forms denetimleri tarafından [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]desteklenir.</span><span class="sxs-lookup"><span data-stu-id="673b7-228">Typically, Windows Forms controls that are managed wrappers for Win32 common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="673b7-229">Aşağıdaki denetimler desteklenir.</span><span class="sxs-lookup"><span data-stu-id="673b7-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="673b7-230">Sınıf Adı</span><span class="sxs-lookup"><span data-stu-id="673b7-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="673b7-231">Düğme</span><span class="sxs-lookup"><span data-stu-id="673b7-231">Button</span></span>|  
|<span data-ttu-id="673b7-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="673b7-232">CheckBox</span></span>|  
|<span data-ttu-id="673b7-233">Checkedlistbox</span><span class="sxs-lookup"><span data-stu-id="673b7-233">CheckedListBox</span></span>|  
|<span data-ttu-id="673b7-234">Colordialog</span><span class="sxs-lookup"><span data-stu-id="673b7-234">ColorDialog</span></span>|  
|<span data-ttu-id="673b7-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="673b7-235">ComboBox</span></span>|  
|<span data-ttu-id="673b7-236">KlasörTarayıcı</span><span class="sxs-lookup"><span data-stu-id="673b7-236">FolderBrowser</span></span>|  
|<span data-ttu-id="673b7-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="673b7-237">FontDialog</span></span>|  
|<span data-ttu-id="673b7-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="673b7-238">GroupBox</span></span>|  
|<span data-ttu-id="673b7-239">Hscrollbar</span><span class="sxs-lookup"><span data-stu-id="673b7-239">HscrollBar</span></span>|  
|<span data-ttu-id="673b7-240">ımagelist</span><span class="sxs-lookup"><span data-stu-id="673b7-240">ImageList</span></span>|  
|<span data-ttu-id="673b7-241">Etiketle</span><span class="sxs-lookup"><span data-stu-id="673b7-241">Label</span></span>|  
|<span data-ttu-id="673b7-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="673b7-242">ListBox</span></span>|  
|<span data-ttu-id="673b7-243">ListView</span><span class="sxs-lookup"><span data-stu-id="673b7-243">ListView</span></span>|  
|<span data-ttu-id="673b7-244">MainMenu/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="673b7-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="673b7-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="673b7-245">MonthCalendar</span></span>|  
|<span data-ttu-id="673b7-246">Notifyıcon</span><span class="sxs-lookup"><span data-stu-id="673b7-246">NotifyIcon</span></span>|  
|<span data-ttu-id="673b7-247">Openfiledialog</span><span class="sxs-lookup"><span data-stu-id="673b7-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="673b7-248">SayfaSetupDialog</span><span class="sxs-lookup"><span data-stu-id="673b7-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="673b7-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="673b7-249">PrintDialog</span></span>|  
|<span data-ttu-id="673b7-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="673b7-250">ProgressBar</span></span>|  
|<span data-ttu-id="673b7-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="673b7-251">RadioButton</span></span>|  
|<span data-ttu-id="673b7-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="673b7-252">RichTextBox</span></span>|  
|<span data-ttu-id="673b7-253">Savefiledialog</span><span class="sxs-lookup"><span data-stu-id="673b7-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="673b7-254">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="673b7-254">ScrollableControl</span></span>|  
|<span data-ttu-id="673b7-255">Soundplayer</span><span class="sxs-lookup"><span data-stu-id="673b7-255">SoundPlayer</span></span>|  
|<span data-ttu-id="673b7-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="673b7-256">StatusBar</span></span>|  
|<span data-ttu-id="673b7-257">Sekme/Sekme Sayfası</span><span class="sxs-lookup"><span data-stu-id="673b7-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="673b7-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="673b7-258">TextBox</span></span>|  
|<span data-ttu-id="673b7-259">Zamanlayıcı</span><span class="sxs-lookup"><span data-stu-id="673b7-259">Timer</span></span>|  
|<span data-ttu-id="673b7-260">Araç Çubuğu</span><span class="sxs-lookup"><span data-stu-id="673b7-260">Toolbar</span></span>|  
|<span data-ttu-id="673b7-261">ToolTip</span><span class="sxs-lookup"><span data-stu-id="673b7-261">ToolTip</span></span>|  
|<span data-ttu-id="673b7-262">Trackbar</span><span class="sxs-lookup"><span data-stu-id="673b7-262">TrackBar</span></span>|  
|<span data-ttu-id="673b7-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="673b7-263">TreeView</span></span>|  
|<span data-ttu-id="673b7-264">Vscrollbar</span><span class="sxs-lookup"><span data-stu-id="673b7-264">VscrollBar</span></span>|  
|<span data-ttu-id="673b7-265">Webbrowser</span><span class="sxs-lookup"><span data-stu-id="673b7-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="673b7-266">Aşağıdaki denetimler yalnızca [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] Microsoft Etkin Erişilebilirlik desteği ile maruz kalır.</span><span class="sxs-lookup"><span data-stu-id="673b7-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for Microsoft Active Accessibility.</span></span> <span data-ttu-id="673b7-267">Bazı işlevler kullanılamayabilir.</span><span class="sxs-lookup"><span data-stu-id="673b7-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="673b7-268">Kontrol Adı</span><span class="sxs-lookup"><span data-stu-id="673b7-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="673b7-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="673b7-269">BindingSource</span></span>|  
|<span data-ttu-id="673b7-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="673b7-270">DataGrid</span></span>|  
|<span data-ttu-id="673b7-271">Datagridview</span><span class="sxs-lookup"><span data-stu-id="673b7-271">DataGridView</span></span>|  
|<span data-ttu-id="673b7-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="673b7-272">DataNavigator</span></span>|  
|<span data-ttu-id="673b7-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="673b7-273">DomainUpDown</span></span>|  
|<span data-ttu-id="673b7-274">Hata Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="673b7-274">ErrorProvider</span></span>|  
|<span data-ttu-id="673b7-275">Flowlayoutpanel</span><span class="sxs-lookup"><span data-stu-id="673b7-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="673b7-276">Form</span><span class="sxs-lookup"><span data-stu-id="673b7-276">Form</span></span>|  
|<span data-ttu-id="673b7-277">Bağlantı Etiketi</span><span class="sxs-lookup"><span data-stu-id="673b7-277">LinkLabel</span></span>|  
|<span data-ttu-id="673b7-278">Yardım Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="673b7-278">HelpProvider</span></span>|  
|<span data-ttu-id="673b7-279">Maskedtextbox</span><span class="sxs-lookup"><span data-stu-id="673b7-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="673b7-280">MenüŞeridi/BağlammenüŞeridi</span><span class="sxs-lookup"><span data-stu-id="673b7-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="673b7-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="673b7-281">NumericUpDown</span></span>|  
|<span data-ttu-id="673b7-282">Panel</span><span class="sxs-lookup"><span data-stu-id="673b7-282">Panel</span></span>|  
|<span data-ttu-id="673b7-283">Picturebox</span><span class="sxs-lookup"><span data-stu-id="673b7-283">PictureBox</span></span>|  
|<span data-ttu-id="673b7-284">Printdocument</span><span class="sxs-lookup"><span data-stu-id="673b7-284">PrintDocument</span></span>|  
|<span data-ttu-id="673b7-285">PrintPreview-Control</span><span class="sxs-lookup"><span data-stu-id="673b7-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="673b7-286">PrintPreview-Dialog</span><span class="sxs-lookup"><span data-stu-id="673b7-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="673b7-287">Emlak Grid</span><span class="sxs-lookup"><span data-stu-id="673b7-287">PropertyGrid</span></span>|  
|<span data-ttu-id="673b7-288">Usercontrol</span><span class="sxs-lookup"><span data-stu-id="673b7-288">UserControl</span></span>|  
|<span data-ttu-id="673b7-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="673b7-289">ToolStrip</span></span>|  
|<span data-ttu-id="673b7-290">Tablelayoutpanel</span><span class="sxs-lookup"><span data-stu-id="673b7-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="673b7-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="673b7-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="673b7-292">Bölücü</span><span class="sxs-lookup"><span data-stu-id="673b7-292">Splitter</span></span>|  
|<span data-ttu-id="673b7-293">RaftingKonteyner</span><span class="sxs-lookup"><span data-stu-id="673b7-293">RaftingContainer</span></span>|  
|<span data-ttu-id="673b7-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="673b7-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="673b7-295">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="673b7-295">See also</span></span>

- [<span data-ttu-id="673b7-296">UI Otomasyon Denetim Türleri</span><span class="sxs-lookup"><span data-stu-id="673b7-296">UI Automation Control Types</span></span>](ui-automation-control-types.md)
