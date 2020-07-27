---
title: Standart Denetimler İçin UI Otomasyon Desteği
description: Windows Presentation Foundation (WPF), Win32 ve Windows Forms için geliştirilen uygulamalardaki standart denetimler için UI Otomasyonu desteği hakkında bilgi alın.
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 17916a6978008439e91caae00d8b6f26045f9018
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166127"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="90e18-103">Standart Denetimler İçin UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="90e18-103">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
> <span data-ttu-id="90e18-104">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> .</span><span class="sxs-lookup"><span data-stu-id="90e18-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="90e18-105">Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="90e18-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="90e18-106">Bu konu [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] , Win32 ve Windows Forms çerçeveleri için geliştirilen uygulamalardaki standart denetimler için destek hakkında bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="90e18-106">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], Win32, and Windows Forms frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="90e18-107">Windows Presentation Foundation denetimleri</span><span class="sxs-lookup"><span data-stu-id="90e18-107">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="90e18-108">[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]Kullanıcı etkileşimi için bilgi veya destek sağlayan tüm denetim öğeleri için tam yerel destek vardır [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="90e18-108">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="90e18-109">Paneller gibi diğer öğeler, için görünür değildir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="90e18-109">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>
## <a name="win32-controls"></a><span data-ttu-id="90e18-110">Win32 denetimleri</span><span class="sxs-lookup"><span data-stu-id="90e18-110">Win32 Controls</span></span>  
 <span data-ttu-id="90e18-111">Çoğu Win32 denetimi, [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] UIAutomationClientsideProviders.dll istemci tarafı sağlayıcılar aracılığıyla sunulur.</span><span class="sxs-lookup"><span data-stu-id="90e18-111">Most Win32 controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="90e18-112">Bu derleme, UI Otomasyonu istemci uygulamalarıyla kullanılmak üzere otomatik olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="90e18-112">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="90e18-113">Tam destek yalnızca *ComCtrl32.dll*sürüm 6 ' dan denetimler için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="90e18-113">Full support is provided only for controls from version 6 of *ComCtrl32.dll*.</span></span>  
  
 <span data-ttu-id="90e18-114">Aşağıdaki denetimler desteklenir.</span><span class="sxs-lookup"><span data-stu-id="90e18-114">The following controls are supported.</span></span>  
  
|<span data-ttu-id="90e18-115">Sınıf adı</span><span class="sxs-lookup"><span data-stu-id="90e18-115">Class name</span></span>|<span data-ttu-id="90e18-116">Denetim türü</span><span class="sxs-lookup"><span data-stu-id="90e18-116">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="90e18-117">Düğme</span><span class="sxs-lookup"><span data-stu-id="90e18-117">Button</span></span>|<span data-ttu-id="90e18-118">Düğme</span><span class="sxs-lookup"><span data-stu-id="90e18-118">Button</span></span>|  
|<span data-ttu-id="90e18-119">Düğme</span><span class="sxs-lookup"><span data-stu-id="90e18-119">Button</span></span>|<span data-ttu-id="90e18-120">RadioButton</span><span class="sxs-lookup"><span data-stu-id="90e18-120">RadioButton</span></span>|  
|<span data-ttu-id="90e18-121">Düğme</span><span class="sxs-lookup"><span data-stu-id="90e18-121">Button</span></span>|<span data-ttu-id="90e18-122">Grup</span><span class="sxs-lookup"><span data-stu-id="90e18-122">Group</span></span>|  
|<span data-ttu-id="90e18-123">Düğme</span><span class="sxs-lookup"><span data-stu-id="90e18-123">Button</span></span>|<span data-ttu-id="90e18-124">CheckBox</span><span class="sxs-lookup"><span data-stu-id="90e18-124">CheckBox</span></span>|  
|<span data-ttu-id="90e18-125">Düğme</span><span class="sxs-lookup"><span data-stu-id="90e18-125">Button</span></span>|<span data-ttu-id="90e18-126">Köprü</span><span class="sxs-lookup"><span data-stu-id="90e18-126">Hyperlink</span></span>|  
|<span data-ttu-id="90e18-127">Düğme</span><span class="sxs-lookup"><span data-stu-id="90e18-127">Button</span></span>|<span data-ttu-id="90e18-128">SplitButton</span><span class="sxs-lookup"><span data-stu-id="90e18-128">SplitButton</span></span>|  
|<span data-ttu-id="90e18-129">Düğme</span><span class="sxs-lookup"><span data-stu-id="90e18-129">Button</span></span>|<span data-ttu-id="90e18-130">CheckBox</span><span class="sxs-lookup"><span data-stu-id="90e18-130">CheckBox</span></span>|  
|<span data-ttu-id="90e18-131">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="90e18-131">ComboBoxEx32</span></span>|<span data-ttu-id="90e18-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="90e18-132">ComboBox</span></span>|  
|<span data-ttu-id="90e18-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="90e18-133">ComboBox</span></span>|<span data-ttu-id="90e18-134">ComboBox</span><span class="sxs-lookup"><span data-stu-id="90e18-134">ComboBox</span></span>|  
|<span data-ttu-id="90e18-135">Düzenle</span><span class="sxs-lookup"><span data-stu-id="90e18-135">Edit</span></span>|<span data-ttu-id="90e18-136">Belge</span><span class="sxs-lookup"><span data-stu-id="90e18-136">Document</span></span>|  
|<span data-ttu-id="90e18-137">Düzenle</span><span class="sxs-lookup"><span data-stu-id="90e18-137">Edit</span></span>|<span data-ttu-id="90e18-138">Düzenle</span><span class="sxs-lookup"><span data-stu-id="90e18-138">Edit</span></span>|  
|<span data-ttu-id="90e18-139">SysLink</span><span class="sxs-lookup"><span data-stu-id="90e18-139">SysLink</span></span>|<span data-ttu-id="90e18-140">Köprü</span><span class="sxs-lookup"><span data-stu-id="90e18-140">Hyperlink</span></span>|  
|<span data-ttu-id="90e18-141">Statik</span><span class="sxs-lookup"><span data-stu-id="90e18-141">Static</span></span>|<span data-ttu-id="90e18-142">Metin</span><span class="sxs-lookup"><span data-stu-id="90e18-142">Text</span></span>|  
|<span data-ttu-id="90e18-143">Statik</span><span class="sxs-lookup"><span data-stu-id="90e18-143">Static</span></span>|<span data-ttu-id="90e18-144">Görüntü</span><span class="sxs-lookup"><span data-stu-id="90e18-144">Image</span></span>|  
|<span data-ttu-id="90e18-145">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="90e18-145">SysIPAddress32</span></span>|<span data-ttu-id="90e18-146">Özel</span><span class="sxs-lookup"><span data-stu-id="90e18-146">Custom</span></span>|  
|<span data-ttu-id="90e18-147">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="90e18-147">SysHeader32</span></span>|<span data-ttu-id="90e18-148">Üstbilgi/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="90e18-148">Header/HeaderItem</span></span>|  
|<span data-ttu-id="90e18-149">SysListView32</span><span class="sxs-lookup"><span data-stu-id="90e18-149">SysListView32</span></span>|<span data-ttu-id="90e18-150">DataGrid</span><span class="sxs-lookup"><span data-stu-id="90e18-150">DataGrid</span></span>|  
|<span data-ttu-id="90e18-151">SysListView32</span><span class="sxs-lookup"><span data-stu-id="90e18-151">SysListView32</span></span>|<span data-ttu-id="90e18-152">Liste</span><span class="sxs-lookup"><span data-stu-id="90e18-152">List</span></span>|  
|<span data-ttu-id="90e18-153">ListBox</span><span class="sxs-lookup"><span data-stu-id="90e18-153">ListBox</span></span>|<span data-ttu-id="90e18-154">Liste</span><span class="sxs-lookup"><span data-stu-id="90e18-154">List</span></span>|  
|<span data-ttu-id="90e18-155">ListBox</span><span class="sxs-lookup"><span data-stu-id="90e18-155">ListBox</span></span>|<span data-ttu-id="90e18-156">Liste</span><span class="sxs-lookup"><span data-stu-id="90e18-156">ListItem</span></span>|  
|<span data-ttu-id="90e18-157">#32768</span><span class="sxs-lookup"><span data-stu-id="90e18-157">#32768</span></span>|<span data-ttu-id="90e18-158">Menü</span><span class="sxs-lookup"><span data-stu-id="90e18-158">Menu</span></span>|  
|<span data-ttu-id="90e18-159">#32768</span><span class="sxs-lookup"><span data-stu-id="90e18-159">#32768</span></span>|<span data-ttu-id="90e18-160">MenuItem</span><span class="sxs-lookup"><span data-stu-id="90e18-160">MenuItem</span></span>|  
|<span data-ttu-id="90e18-161">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="90e18-161">msctls_progress32</span></span>|<span data-ttu-id="90e18-162">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="90e18-162">ProgressBar</span></span>|  
|<span data-ttu-id="90e18-163">RichEdit</span><span class="sxs-lookup"><span data-stu-id="90e18-163">RichEdit</span></span>|<span data-ttu-id="90e18-164">Belgedeki.</span><span class="sxs-lookup"><span data-stu-id="90e18-164">Document.</span></span> <span data-ttu-id="90e18-165">Bkz. Note.</span><span class="sxs-lookup"><span data-stu-id="90e18-165">See note.</span></span>|  
|<span data-ttu-id="90e18-166">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="90e18-166">RichEdit20A</span></span>|<span data-ttu-id="90e18-167">Belge</span><span class="sxs-lookup"><span data-stu-id="90e18-167">Document</span></span>|  
|<span data-ttu-id="90e18-168">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="90e18-168">RichEdit20W</span></span>|<span data-ttu-id="90e18-169">Belge</span><span class="sxs-lookup"><span data-stu-id="90e18-169">Document</span></span>|  
|<span data-ttu-id="90e18-170">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="90e18-170">RichEdit50W</span></span>|<span data-ttu-id="90e18-171">Belge</span><span class="sxs-lookup"><span data-stu-id="90e18-171">Document</span></span>|  
|<span data-ttu-id="90e18-172">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="90e18-172">ScrollBar</span></span>|<span data-ttu-id="90e18-173">Slider</span><span class="sxs-lookup"><span data-stu-id="90e18-173">Slider</span></span>|  
|<span data-ttu-id="90e18-174">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="90e18-174">msctls_trackbar32</span></span>|<span data-ttu-id="90e18-175">Slider</span><span class="sxs-lookup"><span data-stu-id="90e18-175">Slider</span></span>|  
|<span data-ttu-id="90e18-176">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="90e18-176">msctls_updown32</span></span>|<span data-ttu-id="90e18-177">Değer Değiştirici</span><span class="sxs-lookup"><span data-stu-id="90e18-177">Spinner</span></span>|  
|<span data-ttu-id="90e18-178">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="90e18-178">msctls_statusbar32</span></span>|<span data-ttu-id="90e18-179">StatusBar</span><span class="sxs-lookup"><span data-stu-id="90e18-179">StatusBar</span></span>|  
|<span data-ttu-id="90e18-180">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="90e18-180">SysTabControl32</span></span>|<span data-ttu-id="90e18-181">Tab</span><span class="sxs-lookup"><span data-stu-id="90e18-181">Tab</span></span>|  
|<span data-ttu-id="90e18-182">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="90e18-182">SysTabControl32</span></span>|<span data-ttu-id="90e18-183">TabItem</span><span class="sxs-lookup"><span data-stu-id="90e18-183">TabItem</span></span>|  
|<span data-ttu-id="90e18-184">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="90e18-184">ToolbarWindow32</span></span>|<span data-ttu-id="90e18-185">ToolBar</span><span class="sxs-lookup"><span data-stu-id="90e18-185">ToolBar</span></span>|  
|<span data-ttu-id="90e18-186">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="90e18-186">ToolbarWindow32</span></span>|<span data-ttu-id="90e18-187">MenuItem</span><span class="sxs-lookup"><span data-stu-id="90e18-187">MenuItem</span></span>|  
|<span data-ttu-id="90e18-188">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="90e18-188">ToolbarWindow32</span></span>|<span data-ttu-id="90e18-189">Düğme</span><span class="sxs-lookup"><span data-stu-id="90e18-189">Button</span></span>|  
|<span data-ttu-id="90e18-190">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="90e18-190">ToolbarWindow32</span></span>|<span data-ttu-id="90e18-191">CheckBox</span><span class="sxs-lookup"><span data-stu-id="90e18-191">CheckBox</span></span>|  
|<span data-ttu-id="90e18-192">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="90e18-192">ToolbarWindow32</span></span>|<span data-ttu-id="90e18-193">RadioButton</span><span class="sxs-lookup"><span data-stu-id="90e18-193">RadioButton</span></span>|  
|<span data-ttu-id="90e18-194">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="90e18-194">ToolbarWindow32</span></span>|<span data-ttu-id="90e18-195">Ayırıcı</span><span class="sxs-lookup"><span data-stu-id="90e18-195">Separator</span></span>|  
|<span data-ttu-id="90e18-196">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="90e18-196">tooltips_class32</span></span>|<span data-ttu-id="90e18-197">ToolTip</span><span class="sxs-lookup"><span data-stu-id="90e18-197">ToolTip</span></span>|  
|<span data-ttu-id="90e18-198">#32774</span><span class="sxs-lookup"><span data-stu-id="90e18-198">#32774</span></span>|<span data-ttu-id="90e18-199">ToolTip</span><span class="sxs-lookup"><span data-stu-id="90e18-199">ToolTip</span></span>|  
|<span data-ttu-id="90e18-200">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="90e18-200">ReBarWindow32</span></span>|<span data-ttu-id="90e18-201">Araç Çubuğu</span><span class="sxs-lookup"><span data-stu-id="90e18-201">Toolbar</span></span>|  
|<span data-ttu-id="90e18-202">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="90e18-202">SysTreeView32</span></span>|<span data-ttu-id="90e18-203">Ağaç</span><span class="sxs-lookup"><span data-stu-id="90e18-203">Tree</span></span>|  
|<span data-ttu-id="90e18-204">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="90e18-204">SysTreeView32</span></span>|<span data-ttu-id="90e18-205">TreeItem</span><span class="sxs-lookup"><span data-stu-id="90e18-205">TreeItem</span></span>|  
  
 <span data-ttu-id="90e18-206">**Göz önünde** RichEdit denetimi yalnızca Windows Vista ile birlikte gelen sürümler için desteklenir (RichEd20.dll sürüm 3,1 ve üzeri sürümlerde ve MsftEdit.dll sürüm 4,1 ve üzeri).</span><span class="sxs-lookup"><span data-stu-id="90e18-206">**Note** The RichEdit control is supported only for versions shipped with Windows Vista (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="90e18-207">Aşağıdaki denetimler desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="90e18-207">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="90e18-208">Sınıf adı</span><span class="sxs-lookup"><span data-stu-id="90e18-208">Class name</span></span>|<span data-ttu-id="90e18-209">Denetim türü</span><span class="sxs-lookup"><span data-stu-id="90e18-209">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="90e18-210">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="90e18-210">SysAnimate32</span></span>|<span data-ttu-id="90e18-211">Görüntü</span><span class="sxs-lookup"><span data-stu-id="90e18-211">Image</span></span>|  
|<span data-ttu-id="90e18-212">SysPager</span><span class="sxs-lookup"><span data-stu-id="90e18-212">SysPager</span></span>|<span data-ttu-id="90e18-213">Değer Değiştirici</span><span class="sxs-lookup"><span data-stu-id="90e18-213">Spinner</span></span>|  
|<span data-ttu-id="90e18-214">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="90e18-214">SysDateTimePick32</span></span>|<span data-ttu-id="90e18-215">Özel</span><span class="sxs-lookup"><span data-stu-id="90e18-215">Custom</span></span>|  
|<span data-ttu-id="90e18-216">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="90e18-216">SysMonthCal32</span></span>|<span data-ttu-id="90e18-217">Takvim</span><span class="sxs-lookup"><span data-stu-id="90e18-217">Calendar</span></span>|  
|<span data-ttu-id="90e18-218">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="90e18-218">MS_WINNOTE</span></span>|<span data-ttu-id="90e18-219">Araç ipucu</span><span class="sxs-lookup"><span data-stu-id="90e18-219">Tooltip</span></span>|  
|<span data-ttu-id="90e18-220">Vbkabarcık</span><span class="sxs-lookup"><span data-stu-id="90e18-220">VBBubble</span></span>|<span data-ttu-id="90e18-221">Araç ipucu</span><span class="sxs-lookup"><span data-stu-id="90e18-221">Tooltip</span></span>|  
|<span data-ttu-id="90e18-222">Kaydırma çubuğu (tek başına denetim olarak kullanıldığında)</span><span class="sxs-lookup"><span data-stu-id="90e18-222">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="90e18-223">Slider</span><span class="sxs-lookup"><span data-stu-id="90e18-223">Slider</span></span>|  
|<span data-ttu-id="90e18-224">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="90e18-224">SuperGrid</span></span>|<span data-ttu-id="90e18-225">Özel</span><span class="sxs-lookup"><span data-stu-id="90e18-225">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>
## <a name="windows-forms-controls"></a><span data-ttu-id="90e18-226">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="90e18-226">Windows Forms Controls</span></span>  
 <span data-ttu-id="90e18-227">Windows Forms denetimleri, [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] UIAutomationClientsideProviders.dll istemci tarafı sağlayıcılar aracılığıyla sunulur.</span><span class="sxs-lookup"><span data-stu-id="90e18-227">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="90e18-228">Bu derleme, UI Otomasyonu istemci uygulamalarıyla kullanılmak üzere otomatik olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="90e18-228">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="90e18-229">Genellikle, Win32 ortak denetimleri için yönetilen sarmalayıcılar olan Windows Forms denetimleri tarafından desteklenir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="90e18-229">Typically, Windows Forms controls that are managed wrappers for Win32 common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="90e18-230">Aşağıdaki denetimler desteklenir.</span><span class="sxs-lookup"><span data-stu-id="90e18-230">The following controls are supported.</span></span>  
  
|<span data-ttu-id="90e18-231">Sınıf Adı</span><span class="sxs-lookup"><span data-stu-id="90e18-231">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="90e18-232">Düğme</span><span class="sxs-lookup"><span data-stu-id="90e18-232">Button</span></span>|  
|<span data-ttu-id="90e18-233">CheckBox</span><span class="sxs-lookup"><span data-stu-id="90e18-233">CheckBox</span></span>|  
|<span data-ttu-id="90e18-234">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="90e18-234">CheckedListBox</span></span>|  
|<span data-ttu-id="90e18-235">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="90e18-235">ColorDialog</span></span>|  
|<span data-ttu-id="90e18-236">ComboBox</span><span class="sxs-lookup"><span data-stu-id="90e18-236">ComboBox</span></span>|  
|<span data-ttu-id="90e18-237">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="90e18-237">FolderBrowser</span></span>|  
|<span data-ttu-id="90e18-238">FontDialog</span><span class="sxs-lookup"><span data-stu-id="90e18-238">FontDialog</span></span>|  
|<span data-ttu-id="90e18-239">GroupBox</span><span class="sxs-lookup"><span data-stu-id="90e18-239">GroupBox</span></span>|  
|<span data-ttu-id="90e18-240">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="90e18-240">HscrollBar</span></span>|  
|<span data-ttu-id="90e18-241">'I</span><span class="sxs-lookup"><span data-stu-id="90e18-241">ImageList</span></span>|  
|<span data-ttu-id="90e18-242">Etiketle</span><span class="sxs-lookup"><span data-stu-id="90e18-242">Label</span></span>|  
|<span data-ttu-id="90e18-243">ListBox</span><span class="sxs-lookup"><span data-stu-id="90e18-243">ListBox</span></span>|  
|<span data-ttu-id="90e18-244">ListView</span><span class="sxs-lookup"><span data-stu-id="90e18-244">ListView</span></span>|  
|<span data-ttu-id="90e18-245">MainMenu/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="90e18-245">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="90e18-246">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="90e18-246">MonthCalendar</span></span>|  
|<span data-ttu-id="90e18-247">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="90e18-247">NotifyIcon</span></span>|  
|<span data-ttu-id="90e18-248">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="90e18-248">OpenFileDialog</span></span>|  
|<span data-ttu-id="90e18-249">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="90e18-249">PageSetupDialog</span></span>|  
|<span data-ttu-id="90e18-250">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="90e18-250">PrintDialog</span></span>|  
|<span data-ttu-id="90e18-251">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="90e18-251">ProgressBar</span></span>|  
|<span data-ttu-id="90e18-252">RadioButton</span><span class="sxs-lookup"><span data-stu-id="90e18-252">RadioButton</span></span>|  
|<span data-ttu-id="90e18-253">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="90e18-253">RichTextBox</span></span>|  
|<span data-ttu-id="90e18-254">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="90e18-254">SaveFileDialog</span></span>|  
|<span data-ttu-id="90e18-255">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="90e18-255">ScrollableControl</span></span>|  
|<span data-ttu-id="90e18-256">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="90e18-256">SoundPlayer</span></span>|  
|<span data-ttu-id="90e18-257">StatusBar</span><span class="sxs-lookup"><span data-stu-id="90e18-257">StatusBar</span></span>|  
|<span data-ttu-id="90e18-258">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="90e18-258">TabControl/TabPage</span></span>|  
|<span data-ttu-id="90e18-259">TextBox</span><span class="sxs-lookup"><span data-stu-id="90e18-259">TextBox</span></span>|  
|<span data-ttu-id="90e18-260">Zamanlayıcı</span><span class="sxs-lookup"><span data-stu-id="90e18-260">Timer</span></span>|  
|<span data-ttu-id="90e18-261">Araç Çubuğu</span><span class="sxs-lookup"><span data-stu-id="90e18-261">Toolbar</span></span>|  
|<span data-ttu-id="90e18-262">ToolTip</span><span class="sxs-lookup"><span data-stu-id="90e18-262">ToolTip</span></span>|  
|<span data-ttu-id="90e18-263">TrackBar</span><span class="sxs-lookup"><span data-stu-id="90e18-263">TrackBar</span></span>|  
|<span data-ttu-id="90e18-264">TreeView</span><span class="sxs-lookup"><span data-stu-id="90e18-264">TreeView</span></span>|  
|<span data-ttu-id="90e18-265">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="90e18-265">VscrollBar</span></span>|  
|<span data-ttu-id="90e18-266">'A</span><span class="sxs-lookup"><span data-stu-id="90e18-266">WebBrowser</span></span>|  
  
 <span data-ttu-id="90e18-267">Aşağıdaki denetimler [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] yalnızca Microsoft Etkin Erişilebilirlik desteğiyle kullanıma sunulur.</span><span class="sxs-lookup"><span data-stu-id="90e18-267">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for Microsoft Active Accessibility.</span></span> <span data-ttu-id="90e18-268">Bazı işlevler kullanılamayabilir.</span><span class="sxs-lookup"><span data-stu-id="90e18-268">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="90e18-269">Denetim adı</span><span class="sxs-lookup"><span data-stu-id="90e18-269">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="90e18-270">BindingSource</span><span class="sxs-lookup"><span data-stu-id="90e18-270">BindingSource</span></span>|  
|<span data-ttu-id="90e18-271">DataGrid</span><span class="sxs-lookup"><span data-stu-id="90e18-271">DataGrid</span></span>|  
|<span data-ttu-id="90e18-272">DataGridView</span><span class="sxs-lookup"><span data-stu-id="90e18-272">DataGridView</span></span>|  
|<span data-ttu-id="90e18-273">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="90e18-273">DataNavigator</span></span>|  
|<span data-ttu-id="90e18-274">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="90e18-274">DomainUpDown</span></span>|  
|<span data-ttu-id="90e18-275">Bileþeni</span><span class="sxs-lookup"><span data-stu-id="90e18-275">ErrorProvider</span></span>|  
|<span data-ttu-id="90e18-276">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="90e18-276">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="90e18-277">Form</span><span class="sxs-lookup"><span data-stu-id="90e18-277">Form</span></span>|  
|<span data-ttu-id="90e18-278">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="90e18-278">LinkLabel</span></span>|  
|<span data-ttu-id="90e18-279">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="90e18-279">HelpProvider</span></span>|  
|<span data-ttu-id="90e18-280">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="90e18-280">MaskedTextBox</span></span>|  
|<span data-ttu-id="90e18-281">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="90e18-281">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="90e18-282">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="90e18-282">NumericUpDown</span></span>|  
|<span data-ttu-id="90e18-283">Panel</span><span class="sxs-lookup"><span data-stu-id="90e18-283">Panel</span></span>|  
|<span data-ttu-id="90e18-284">PictureBox</span><span class="sxs-lookup"><span data-stu-id="90e18-284">PictureBox</span></span>|  
|<span data-ttu-id="90e18-285">Öniz</span><span class="sxs-lookup"><span data-stu-id="90e18-285">PrintDocument</span></span>|  
|<span data-ttu-id="90e18-286">PrintPreview-denetim</span><span class="sxs-lookup"><span data-stu-id="90e18-286">PrintPreview-Control</span></span>|  
|<span data-ttu-id="90e18-287">PrintPreview-Iletişim kutusu</span><span class="sxs-lookup"><span data-stu-id="90e18-287">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="90e18-288">'In</span><span class="sxs-lookup"><span data-stu-id="90e18-288">PropertyGrid</span></span>|  
|<span data-ttu-id="90e18-289">UserControl</span><span class="sxs-lookup"><span data-stu-id="90e18-289">UserControl</span></span>|  
|<span data-ttu-id="90e18-290">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="90e18-290">ToolStrip</span></span>|  
|<span data-ttu-id="90e18-291">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="90e18-291">TableLayoutPanel</span></span>|  
|<span data-ttu-id="90e18-292">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="90e18-292">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="90e18-293">Bölücü</span><span class="sxs-lookup"><span data-stu-id="90e18-293">Splitter</span></span>|  
|<span data-ttu-id="90e18-294">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="90e18-294">RaftingContainer</span></span>|  
|<span data-ttu-id="90e18-295">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="90e18-295">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="90e18-296">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="90e18-296">See also</span></span>

- [<span data-ttu-id="90e18-297">UI Otomasyon Denetim Türleri</span><span class="sxs-lookup"><span data-stu-id="90e18-297">UI Automation Control Types</span></span>](ui-automation-control-types.md)
