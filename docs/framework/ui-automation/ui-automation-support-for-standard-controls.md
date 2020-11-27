---
title: Standart Denetimler İçin UI Otomasyon Desteği
description: Windows Presentation Foundation (WPF), Win32 ve Windows Forms için geliştirilen uygulamalardaki standart denetimler için UI Otomasyonu desteği hakkında bilgi alın.
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 0a5a0b61a6492d9efb62799fa610859b247cf26e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96261078"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="2c3c5-103">Standart Denetimler İçin UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="2c3c5-103">UI Automation Support for Standard Controls</span></span>

> [!NOTE]
> <span data-ttu-id="2c3c5-104">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> .</span><span class="sxs-lookup"><span data-stu-id="2c3c5-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="2c3c5-105">Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="2c3c5-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="2c3c5-106">Bu konu [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] , Win32 ve Windows Forms çerçeveleri için geliştirilen uygulamalardaki standart denetimler için destek hakkında bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="2c3c5-106">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], Win32, and Windows Forms frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>

## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="2c3c5-107">Windows Presentation Foundation denetimleri</span><span class="sxs-lookup"><span data-stu-id="2c3c5-107">Windows Presentation Foundation Controls</span></span>  

 <span data-ttu-id="2c3c5-108">[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]Kullanıcı etkileşimi için bilgi veya destek sağlayan tüm denetim öğeleri için tam yerel destek vardır [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="2c3c5-108">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="2c3c5-109">Paneller gibi diğer öğeler, için görünür değildir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="2c3c5-109">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>

## <a name="win32-controls"></a><span data-ttu-id="2c3c5-110">Win32 denetimleri</span><span class="sxs-lookup"><span data-stu-id="2c3c5-110">Win32 Controls</span></span>  

 <span data-ttu-id="2c3c5-111">Çoğu Win32 denetimi, [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] UIAutomationClientsideProviders.dll istemci tarafı sağlayıcılar aracılığıyla sunulur.</span><span class="sxs-lookup"><span data-stu-id="2c3c5-111">Most Win32 controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="2c3c5-112">Bu derleme, UI Otomasyonu istemci uygulamalarıyla kullanılmak üzere otomatik olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="2c3c5-112">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="2c3c5-113">Tam destek yalnızca *ComCtrl32.dll* sürüm 6 ' dan denetimler için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="2c3c5-113">Full support is provided only for controls from version 6 of *ComCtrl32.dll*.</span></span>  
  
 <span data-ttu-id="2c3c5-114">Aşağıdaki denetimler desteklenir.</span><span class="sxs-lookup"><span data-stu-id="2c3c5-114">The following controls are supported.</span></span>  
  
|<span data-ttu-id="2c3c5-115">Sınıf adı</span><span class="sxs-lookup"><span data-stu-id="2c3c5-115">Class name</span></span>|<span data-ttu-id="2c3c5-116">Denetim türü</span><span class="sxs-lookup"><span data-stu-id="2c3c5-116">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="2c3c5-117">Düğme</span><span class="sxs-lookup"><span data-stu-id="2c3c5-117">Button</span></span>|<span data-ttu-id="2c3c5-118">Düğme</span><span class="sxs-lookup"><span data-stu-id="2c3c5-118">Button</span></span>|  
|<span data-ttu-id="2c3c5-119">Düğme</span><span class="sxs-lookup"><span data-stu-id="2c3c5-119">Button</span></span>|<span data-ttu-id="2c3c5-120">RadioButton</span><span class="sxs-lookup"><span data-stu-id="2c3c5-120">RadioButton</span></span>|  
|<span data-ttu-id="2c3c5-121">Düğme</span><span class="sxs-lookup"><span data-stu-id="2c3c5-121">Button</span></span>|<span data-ttu-id="2c3c5-122">Grup</span><span class="sxs-lookup"><span data-stu-id="2c3c5-122">Group</span></span>|  
|<span data-ttu-id="2c3c5-123">Düğme</span><span class="sxs-lookup"><span data-stu-id="2c3c5-123">Button</span></span>|<span data-ttu-id="2c3c5-124">CheckBox</span><span class="sxs-lookup"><span data-stu-id="2c3c5-124">CheckBox</span></span>|  
|<span data-ttu-id="2c3c5-125">Düğme</span><span class="sxs-lookup"><span data-stu-id="2c3c5-125">Button</span></span>|<span data-ttu-id="2c3c5-126">Köprü</span><span class="sxs-lookup"><span data-stu-id="2c3c5-126">Hyperlink</span></span>|  
|<span data-ttu-id="2c3c5-127">Düğme</span><span class="sxs-lookup"><span data-stu-id="2c3c5-127">Button</span></span>|<span data-ttu-id="2c3c5-128">SplitButton</span><span class="sxs-lookup"><span data-stu-id="2c3c5-128">SplitButton</span></span>|  
|<span data-ttu-id="2c3c5-129">Düğme</span><span class="sxs-lookup"><span data-stu-id="2c3c5-129">Button</span></span>|<span data-ttu-id="2c3c5-130">CheckBox</span><span class="sxs-lookup"><span data-stu-id="2c3c5-130">CheckBox</span></span>|  
|<span data-ttu-id="2c3c5-131">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="2c3c5-131">ComboBoxEx32</span></span>|<span data-ttu-id="2c3c5-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="2c3c5-132">ComboBox</span></span>|  
|<span data-ttu-id="2c3c5-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="2c3c5-133">ComboBox</span></span>|<span data-ttu-id="2c3c5-134">ComboBox</span><span class="sxs-lookup"><span data-stu-id="2c3c5-134">ComboBox</span></span>|  
|<span data-ttu-id="2c3c5-135">Düzenle</span><span class="sxs-lookup"><span data-stu-id="2c3c5-135">Edit</span></span>|<span data-ttu-id="2c3c5-136">Belge</span><span class="sxs-lookup"><span data-stu-id="2c3c5-136">Document</span></span>|  
|<span data-ttu-id="2c3c5-137">Düzenle</span><span class="sxs-lookup"><span data-stu-id="2c3c5-137">Edit</span></span>|<span data-ttu-id="2c3c5-138">Düzenle</span><span class="sxs-lookup"><span data-stu-id="2c3c5-138">Edit</span></span>|  
|<span data-ttu-id="2c3c5-139">SysLink</span><span class="sxs-lookup"><span data-stu-id="2c3c5-139">SysLink</span></span>|<span data-ttu-id="2c3c5-140">Köprü</span><span class="sxs-lookup"><span data-stu-id="2c3c5-140">Hyperlink</span></span>|  
|<span data-ttu-id="2c3c5-141">Statik</span><span class="sxs-lookup"><span data-stu-id="2c3c5-141">Static</span></span>|<span data-ttu-id="2c3c5-142">Metin</span><span class="sxs-lookup"><span data-stu-id="2c3c5-142">Text</span></span>|  
|<span data-ttu-id="2c3c5-143">Statik</span><span class="sxs-lookup"><span data-stu-id="2c3c5-143">Static</span></span>|<span data-ttu-id="2c3c5-144">Görüntü</span><span class="sxs-lookup"><span data-stu-id="2c3c5-144">Image</span></span>|  
|<span data-ttu-id="2c3c5-145">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="2c3c5-145">SysIPAddress32</span></span>|<span data-ttu-id="2c3c5-146">Özel</span><span class="sxs-lookup"><span data-stu-id="2c3c5-146">Custom</span></span>|  
|<span data-ttu-id="2c3c5-147">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="2c3c5-147">SysHeader32</span></span>|<span data-ttu-id="2c3c5-148">Üstbilgi/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="2c3c5-148">Header/HeaderItem</span></span>|  
|<span data-ttu-id="2c3c5-149">SysListView32</span><span class="sxs-lookup"><span data-stu-id="2c3c5-149">SysListView32</span></span>|<span data-ttu-id="2c3c5-150">DataGrid</span><span class="sxs-lookup"><span data-stu-id="2c3c5-150">DataGrid</span></span>|  
|<span data-ttu-id="2c3c5-151">SysListView32</span><span class="sxs-lookup"><span data-stu-id="2c3c5-151">SysListView32</span></span>|<span data-ttu-id="2c3c5-152">Liste</span><span class="sxs-lookup"><span data-stu-id="2c3c5-152">List</span></span>|  
|<span data-ttu-id="2c3c5-153">ListBox</span><span class="sxs-lookup"><span data-stu-id="2c3c5-153">ListBox</span></span>|<span data-ttu-id="2c3c5-154">Liste</span><span class="sxs-lookup"><span data-stu-id="2c3c5-154">List</span></span>|  
|<span data-ttu-id="2c3c5-155">ListBox</span><span class="sxs-lookup"><span data-stu-id="2c3c5-155">ListBox</span></span>|<span data-ttu-id="2c3c5-156">Liste</span><span class="sxs-lookup"><span data-stu-id="2c3c5-156">ListItem</span></span>|  
|<span data-ttu-id="2c3c5-157">#32768</span><span class="sxs-lookup"><span data-stu-id="2c3c5-157">#32768</span></span>|<span data-ttu-id="2c3c5-158">Menü</span><span class="sxs-lookup"><span data-stu-id="2c3c5-158">Menu</span></span>|  
|<span data-ttu-id="2c3c5-159">#32768</span><span class="sxs-lookup"><span data-stu-id="2c3c5-159">#32768</span></span>|<span data-ttu-id="2c3c5-160">MenuItem</span><span class="sxs-lookup"><span data-stu-id="2c3c5-160">MenuItem</span></span>|  
|<span data-ttu-id="2c3c5-161">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="2c3c5-161">msctls_progress32</span></span>|<span data-ttu-id="2c3c5-162">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="2c3c5-162">ProgressBar</span></span>|  
|<span data-ttu-id="2c3c5-163">RichEdit</span><span class="sxs-lookup"><span data-stu-id="2c3c5-163">RichEdit</span></span>|<span data-ttu-id="2c3c5-164">Belgedeki.</span><span class="sxs-lookup"><span data-stu-id="2c3c5-164">Document.</span></span> <span data-ttu-id="2c3c5-165">Bkz. Note.</span><span class="sxs-lookup"><span data-stu-id="2c3c5-165">See note.</span></span>|  
|<span data-ttu-id="2c3c5-166">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="2c3c5-166">RichEdit20A</span></span>|<span data-ttu-id="2c3c5-167">Belge</span><span class="sxs-lookup"><span data-stu-id="2c3c5-167">Document</span></span>|  
|<span data-ttu-id="2c3c5-168">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="2c3c5-168">RichEdit20W</span></span>|<span data-ttu-id="2c3c5-169">Belge</span><span class="sxs-lookup"><span data-stu-id="2c3c5-169">Document</span></span>|  
|<span data-ttu-id="2c3c5-170">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="2c3c5-170">RichEdit50W</span></span>|<span data-ttu-id="2c3c5-171">Belge</span><span class="sxs-lookup"><span data-stu-id="2c3c5-171">Document</span></span>|  
|<span data-ttu-id="2c3c5-172">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="2c3c5-172">ScrollBar</span></span>|<span data-ttu-id="2c3c5-173">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="2c3c5-173">Slider</span></span>|  
|<span data-ttu-id="2c3c5-174">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="2c3c5-174">msctls_trackbar32</span></span>|<span data-ttu-id="2c3c5-175">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="2c3c5-175">Slider</span></span>|  
|<span data-ttu-id="2c3c5-176">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="2c3c5-176">msctls_updown32</span></span>|<span data-ttu-id="2c3c5-177">Değer Değiştirici</span><span class="sxs-lookup"><span data-stu-id="2c3c5-177">Spinner</span></span>|  
|<span data-ttu-id="2c3c5-178">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="2c3c5-178">msctls_statusbar32</span></span>|<span data-ttu-id="2c3c5-179">StatusBar</span><span class="sxs-lookup"><span data-stu-id="2c3c5-179">StatusBar</span></span>|  
|<span data-ttu-id="2c3c5-180">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="2c3c5-180">SysTabControl32</span></span>|<span data-ttu-id="2c3c5-181">Tab</span><span class="sxs-lookup"><span data-stu-id="2c3c5-181">Tab</span></span>|  
|<span data-ttu-id="2c3c5-182">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="2c3c5-182">SysTabControl32</span></span>|<span data-ttu-id="2c3c5-183">TabItem</span><span class="sxs-lookup"><span data-stu-id="2c3c5-183">TabItem</span></span>|  
|<span data-ttu-id="2c3c5-184">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="2c3c5-184">ToolbarWindow32</span></span>|<span data-ttu-id="2c3c5-185">ToolBar</span><span class="sxs-lookup"><span data-stu-id="2c3c5-185">ToolBar</span></span>|  
|<span data-ttu-id="2c3c5-186">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="2c3c5-186">ToolbarWindow32</span></span>|<span data-ttu-id="2c3c5-187">MenuItem</span><span class="sxs-lookup"><span data-stu-id="2c3c5-187">MenuItem</span></span>|  
|<span data-ttu-id="2c3c5-188">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="2c3c5-188">ToolbarWindow32</span></span>|<span data-ttu-id="2c3c5-189">Düğme</span><span class="sxs-lookup"><span data-stu-id="2c3c5-189">Button</span></span>|  
|<span data-ttu-id="2c3c5-190">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="2c3c5-190">ToolbarWindow32</span></span>|<span data-ttu-id="2c3c5-191">CheckBox</span><span class="sxs-lookup"><span data-stu-id="2c3c5-191">CheckBox</span></span>|  
|<span data-ttu-id="2c3c5-192">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="2c3c5-192">ToolbarWindow32</span></span>|<span data-ttu-id="2c3c5-193">RadioButton</span><span class="sxs-lookup"><span data-stu-id="2c3c5-193">RadioButton</span></span>|  
|<span data-ttu-id="2c3c5-194">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="2c3c5-194">ToolbarWindow32</span></span>|<span data-ttu-id="2c3c5-195">Ayırıcı</span><span class="sxs-lookup"><span data-stu-id="2c3c5-195">Separator</span></span>|  
|<span data-ttu-id="2c3c5-196">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="2c3c5-196">tooltips_class32</span></span>|<span data-ttu-id="2c3c5-197">ToolTip</span><span class="sxs-lookup"><span data-stu-id="2c3c5-197">ToolTip</span></span>|  
|<span data-ttu-id="2c3c5-198">#32774</span><span class="sxs-lookup"><span data-stu-id="2c3c5-198">#32774</span></span>|<span data-ttu-id="2c3c5-199">ToolTip</span><span class="sxs-lookup"><span data-stu-id="2c3c5-199">ToolTip</span></span>|  
|<span data-ttu-id="2c3c5-200">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="2c3c5-200">ReBarWindow32</span></span>|<span data-ttu-id="2c3c5-201">Araç Çubuğu</span><span class="sxs-lookup"><span data-stu-id="2c3c5-201">Toolbar</span></span>|  
|<span data-ttu-id="2c3c5-202">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="2c3c5-202">SysTreeView32</span></span>|<span data-ttu-id="2c3c5-203">Ağaç</span><span class="sxs-lookup"><span data-stu-id="2c3c5-203">Tree</span></span>|  
|<span data-ttu-id="2c3c5-204">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="2c3c5-204">SysTreeView32</span></span>|<span data-ttu-id="2c3c5-205">TreeItem</span><span class="sxs-lookup"><span data-stu-id="2c3c5-205">TreeItem</span></span>|  
  
 <span data-ttu-id="2c3c5-206">**Göz önünde** RichEdit denetimi yalnızca Windows Vista ile birlikte gelen sürümler için desteklenir (RichEd20.dll sürüm 3,1 ve üzeri sürümlerde ve MsftEdit.dll sürüm 4,1 ve üzeri).</span><span class="sxs-lookup"><span data-stu-id="2c3c5-206">**Note** The RichEdit control is supported only for versions shipped with Windows Vista (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="2c3c5-207">Aşağıdaki denetimler desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="2c3c5-207">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="2c3c5-208">Sınıf adı</span><span class="sxs-lookup"><span data-stu-id="2c3c5-208">Class name</span></span>|<span data-ttu-id="2c3c5-209">Denetim türü</span><span class="sxs-lookup"><span data-stu-id="2c3c5-209">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="2c3c5-210">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="2c3c5-210">SysAnimate32</span></span>|<span data-ttu-id="2c3c5-211">Görüntü</span><span class="sxs-lookup"><span data-stu-id="2c3c5-211">Image</span></span>|  
|<span data-ttu-id="2c3c5-212">SysPager</span><span class="sxs-lookup"><span data-stu-id="2c3c5-212">SysPager</span></span>|<span data-ttu-id="2c3c5-213">Değer Değiştirici</span><span class="sxs-lookup"><span data-stu-id="2c3c5-213">Spinner</span></span>|  
|<span data-ttu-id="2c3c5-214">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="2c3c5-214">SysDateTimePick32</span></span>|<span data-ttu-id="2c3c5-215">Özel</span><span class="sxs-lookup"><span data-stu-id="2c3c5-215">Custom</span></span>|  
|<span data-ttu-id="2c3c5-216">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="2c3c5-216">SysMonthCal32</span></span>|<span data-ttu-id="2c3c5-217">Takvim</span><span class="sxs-lookup"><span data-stu-id="2c3c5-217">Calendar</span></span>|  
|<span data-ttu-id="2c3c5-218">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="2c3c5-218">MS_WINNOTE</span></span>|<span data-ttu-id="2c3c5-219">Araç ipucu</span><span class="sxs-lookup"><span data-stu-id="2c3c5-219">Tooltip</span></span>|  
|<span data-ttu-id="2c3c5-220">Vbkabarcık</span><span class="sxs-lookup"><span data-stu-id="2c3c5-220">VBBubble</span></span>|<span data-ttu-id="2c3c5-221">Araç ipucu</span><span class="sxs-lookup"><span data-stu-id="2c3c5-221">Tooltip</span></span>|  
|<span data-ttu-id="2c3c5-222">Kaydırma çubuğu (tek başına denetim olarak kullanıldığında)</span><span class="sxs-lookup"><span data-stu-id="2c3c5-222">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="2c3c5-223">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="2c3c5-223">Slider</span></span>|  
|<span data-ttu-id="2c3c5-224">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="2c3c5-224">SuperGrid</span></span>|<span data-ttu-id="2c3c5-225">Özel</span><span class="sxs-lookup"><span data-stu-id="2c3c5-225">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>

## <a name="windows-forms-controls"></a><span data-ttu-id="2c3c5-226">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="2c3c5-226">Windows Forms Controls</span></span>  

 <span data-ttu-id="2c3c5-227">Windows Forms denetimleri, [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] UIAutomationClientsideProviders.dll istemci tarafı sağlayıcılar aracılığıyla sunulur.</span><span class="sxs-lookup"><span data-stu-id="2c3c5-227">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="2c3c5-228">Bu derleme, UI Otomasyonu istemci uygulamalarıyla kullanılmak üzere otomatik olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="2c3c5-228">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="2c3c5-229">Genellikle, Win32 ortak denetimleri için yönetilen sarmalayıcılar olan Windows Forms denetimleri tarafından desteklenir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="2c3c5-229">Typically, Windows Forms controls that are managed wrappers for Win32 common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="2c3c5-230">Aşağıdaki denetimler desteklenir.</span><span class="sxs-lookup"><span data-stu-id="2c3c5-230">The following controls are supported.</span></span>  
  
|<span data-ttu-id="2c3c5-231">Sınıf Adı</span><span class="sxs-lookup"><span data-stu-id="2c3c5-231">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="2c3c5-232">Düğme</span><span class="sxs-lookup"><span data-stu-id="2c3c5-232">Button</span></span>|  
|<span data-ttu-id="2c3c5-233">CheckBox</span><span class="sxs-lookup"><span data-stu-id="2c3c5-233">CheckBox</span></span>|  
|<span data-ttu-id="2c3c5-234">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="2c3c5-234">CheckedListBox</span></span>|  
|<span data-ttu-id="2c3c5-235">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="2c3c5-235">ColorDialog</span></span>|  
|<span data-ttu-id="2c3c5-236">ComboBox</span><span class="sxs-lookup"><span data-stu-id="2c3c5-236">ComboBox</span></span>|  
|<span data-ttu-id="2c3c5-237">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="2c3c5-237">FolderBrowser</span></span>|  
|<span data-ttu-id="2c3c5-238">FontDialog</span><span class="sxs-lookup"><span data-stu-id="2c3c5-238">FontDialog</span></span>|  
|<span data-ttu-id="2c3c5-239">GroupBox</span><span class="sxs-lookup"><span data-stu-id="2c3c5-239">GroupBox</span></span>|  
|<span data-ttu-id="2c3c5-240">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="2c3c5-240">HscrollBar</span></span>|  
|<span data-ttu-id="2c3c5-241">'I</span><span class="sxs-lookup"><span data-stu-id="2c3c5-241">ImageList</span></span>|  
|<span data-ttu-id="2c3c5-242">Etiketle</span><span class="sxs-lookup"><span data-stu-id="2c3c5-242">Label</span></span>|  
|<span data-ttu-id="2c3c5-243">ListBox</span><span class="sxs-lookup"><span data-stu-id="2c3c5-243">ListBox</span></span>|  
|<span data-ttu-id="2c3c5-244">ListView</span><span class="sxs-lookup"><span data-stu-id="2c3c5-244">ListView</span></span>|  
|<span data-ttu-id="2c3c5-245">MainMenu/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="2c3c5-245">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="2c3c5-246">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="2c3c5-246">MonthCalendar</span></span>|  
|<span data-ttu-id="2c3c5-247">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="2c3c5-247">NotifyIcon</span></span>|  
|<span data-ttu-id="2c3c5-248">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="2c3c5-248">OpenFileDialog</span></span>|  
|<span data-ttu-id="2c3c5-249">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="2c3c5-249">PageSetupDialog</span></span>|  
|<span data-ttu-id="2c3c5-250">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="2c3c5-250">PrintDialog</span></span>|  
|<span data-ttu-id="2c3c5-251">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="2c3c5-251">ProgressBar</span></span>|  
|<span data-ttu-id="2c3c5-252">RadioButton</span><span class="sxs-lookup"><span data-stu-id="2c3c5-252">RadioButton</span></span>|  
|<span data-ttu-id="2c3c5-253">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="2c3c5-253">RichTextBox</span></span>|  
|<span data-ttu-id="2c3c5-254">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="2c3c5-254">SaveFileDialog</span></span>|  
|<span data-ttu-id="2c3c5-255">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="2c3c5-255">ScrollableControl</span></span>|  
|<span data-ttu-id="2c3c5-256">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="2c3c5-256">SoundPlayer</span></span>|  
|<span data-ttu-id="2c3c5-257">StatusBar</span><span class="sxs-lookup"><span data-stu-id="2c3c5-257">StatusBar</span></span>|  
|<span data-ttu-id="2c3c5-258">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="2c3c5-258">TabControl/TabPage</span></span>|  
|<span data-ttu-id="2c3c5-259">TextBox</span><span class="sxs-lookup"><span data-stu-id="2c3c5-259">TextBox</span></span>|  
|<span data-ttu-id="2c3c5-260">Zamanlayıcı</span><span class="sxs-lookup"><span data-stu-id="2c3c5-260">Timer</span></span>|  
|<span data-ttu-id="2c3c5-261">Araç Çubuğu</span><span class="sxs-lookup"><span data-stu-id="2c3c5-261">Toolbar</span></span>|  
|<span data-ttu-id="2c3c5-262">ToolTip</span><span class="sxs-lookup"><span data-stu-id="2c3c5-262">ToolTip</span></span>|  
|<span data-ttu-id="2c3c5-263">TrackBar</span><span class="sxs-lookup"><span data-stu-id="2c3c5-263">TrackBar</span></span>|  
|<span data-ttu-id="2c3c5-264">TreeView</span><span class="sxs-lookup"><span data-stu-id="2c3c5-264">TreeView</span></span>|  
|<span data-ttu-id="2c3c5-265">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="2c3c5-265">VscrollBar</span></span>|  
|<span data-ttu-id="2c3c5-266">'A</span><span class="sxs-lookup"><span data-stu-id="2c3c5-266">WebBrowser</span></span>|  
  
 <span data-ttu-id="2c3c5-267">Aşağıdaki denetimler [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] yalnızca Microsoft Etkin Erişilebilirlik desteğiyle kullanıma sunulur.</span><span class="sxs-lookup"><span data-stu-id="2c3c5-267">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for Microsoft Active Accessibility.</span></span> <span data-ttu-id="2c3c5-268">Bazı işlevler kullanılamayabilir.</span><span class="sxs-lookup"><span data-stu-id="2c3c5-268">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="2c3c5-269">Denetim adı</span><span class="sxs-lookup"><span data-stu-id="2c3c5-269">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="2c3c5-270">BindingSource</span><span class="sxs-lookup"><span data-stu-id="2c3c5-270">BindingSource</span></span>|  
|<span data-ttu-id="2c3c5-271">DataGrid</span><span class="sxs-lookup"><span data-stu-id="2c3c5-271">DataGrid</span></span>|  
|<span data-ttu-id="2c3c5-272">DataGridView</span><span class="sxs-lookup"><span data-stu-id="2c3c5-272">DataGridView</span></span>|  
|<span data-ttu-id="2c3c5-273">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="2c3c5-273">DataNavigator</span></span>|  
|<span data-ttu-id="2c3c5-274">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="2c3c5-274">DomainUpDown</span></span>|  
|<span data-ttu-id="2c3c5-275">Bileþeni</span><span class="sxs-lookup"><span data-stu-id="2c3c5-275">ErrorProvider</span></span>|  
|<span data-ttu-id="2c3c5-276">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="2c3c5-276">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="2c3c5-277">Form</span><span class="sxs-lookup"><span data-stu-id="2c3c5-277">Form</span></span>|  
|<span data-ttu-id="2c3c5-278">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="2c3c5-278">LinkLabel</span></span>|  
|<span data-ttu-id="2c3c5-279">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="2c3c5-279">HelpProvider</span></span>|  
|<span data-ttu-id="2c3c5-280">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="2c3c5-280">MaskedTextBox</span></span>|  
|<span data-ttu-id="2c3c5-281">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="2c3c5-281">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="2c3c5-282">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="2c3c5-282">NumericUpDown</span></span>|  
|<span data-ttu-id="2c3c5-283">Panel</span><span class="sxs-lookup"><span data-stu-id="2c3c5-283">Panel</span></span>|  
|<span data-ttu-id="2c3c5-284">PictureBox</span><span class="sxs-lookup"><span data-stu-id="2c3c5-284">PictureBox</span></span>|  
|<span data-ttu-id="2c3c5-285">Öniz</span><span class="sxs-lookup"><span data-stu-id="2c3c5-285">PrintDocument</span></span>|  
|<span data-ttu-id="2c3c5-286">PrintPreview-Control</span><span class="sxs-lookup"><span data-stu-id="2c3c5-286">PrintPreview-Control</span></span>|  
|<span data-ttu-id="2c3c5-287">PrintPreview-Dialog</span><span class="sxs-lookup"><span data-stu-id="2c3c5-287">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="2c3c5-288">'In</span><span class="sxs-lookup"><span data-stu-id="2c3c5-288">PropertyGrid</span></span>|  
|<span data-ttu-id="2c3c5-289">UserControl</span><span class="sxs-lookup"><span data-stu-id="2c3c5-289">UserControl</span></span>|  
|<span data-ttu-id="2c3c5-290">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="2c3c5-290">ToolStrip</span></span>|  
|<span data-ttu-id="2c3c5-291">TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="2c3c5-291">TableLayoutPanel</span></span>|  
|<span data-ttu-id="2c3c5-292">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="2c3c5-292">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="2c3c5-293">Bölücü</span><span class="sxs-lookup"><span data-stu-id="2c3c5-293">Splitter</span></span>|  
|<span data-ttu-id="2c3c5-294">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="2c3c5-294">RaftingContainer</span></span>|  
|<span data-ttu-id="2c3c5-295">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="2c3c5-295">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2c3c5-296">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c3c5-296">See also</span></span>

- [<span data-ttu-id="2c3c5-297">UI Otomasyon Denetim Türleri</span><span class="sxs-lookup"><span data-stu-id="2c3c5-297">UI Automation Control Types</span></span>](ui-automation-control-types.md)
