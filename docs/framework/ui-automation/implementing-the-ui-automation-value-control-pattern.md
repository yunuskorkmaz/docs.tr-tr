---
title: "UI Otomasyonu Değer Denetim Düzenini Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, Value
- UI Automation, Value control pattern
- Value control pattern
ms.assetid: b0fcdd87-3add-4345-bca9-e891205e02ba
caps.latest.revision: "25"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 5f74b103092032e35cce47d893f9e3b6e9d7727b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="implementing-the-ui-automation-value-control-pattern"></a><span data-ttu-id="d0105-102">UI Otomasyonu Değer Denetim Düzenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="d0105-102">Implementing the UI Automation Value Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="d0105-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="d0105-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="d0105-104">Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="d0105-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="d0105-105">Bu konu kılavuzları ve uygulamak için kuralları tanıtır <xref:System.Windows.Automation.Provider.IValueProvider>, olaylar ve özellikler hakkında bilgiler dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="d0105-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IValueProvider>, including information on events and properties.</span></span> <span data-ttu-id="d0105-106">Ek başvurular bağlantılar konunun sonunda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="d0105-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="d0105-107"><xref:System.Windows.Automation.ValuePattern> Denetim düzeni aralığı kapsayıcı olmayan bir değer varsa ve, temsil bir dize olarak denetimleri desteklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d0105-107">The <xref:System.Windows.Automation.ValuePattern> control pattern is used to support controls that have an intrinsic value not spanning a range and that can be represented as a string.</span></span> <span data-ttu-id="d0105-108">Bu dize denetim ve ayarlarına bağlı olarak düzenlenebilir olabilir.</span><span class="sxs-lookup"><span data-stu-id="d0105-108">This string can be editable, depending on the control and its settings.</span></span> <span data-ttu-id="d0105-109">Bu deseni uygulayan denetimleri örnekleri için bkz: [denetim düzeni eşleştirmesi UI Otomasyon istemcileri için](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="d0105-109">For examples of controls that implement this pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="d0105-110">Uygulama rehberi ve kuralları</span><span class="sxs-lookup"><span data-stu-id="d0105-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="d0105-111">Değer denetim düzenini uygulama, aşağıdaki yönergeleri ve kuralları dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="d0105-111">When implementing the Value control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="d0105-112">Gibi denetimler <xref:System.Windows.Automation.ControlType.ListItem> ve <xref:System.Windows.Automation.ControlType.TreeItem> desteklemelidir <xref:System.Windows.Automation.ValuePattern> öğelerden herhangi birini değerini düzenlenebilir ise, bağımsız olarak geçerli düzenleme moduna denetimi.</span><span class="sxs-lookup"><span data-stu-id="d0105-112">Controls such as <xref:System.Windows.Automation.ControlType.ListItem> and <xref:System.Windows.Automation.ControlType.TreeItem> must support <xref:System.Windows.Automation.ValuePattern> if the value of any of the items is editable, regardless of the current edit mode of the control.</span></span> <span data-ttu-id="d0105-113">Üst denetim de desteklemelidir <xref:System.Windows.Automation.ValuePattern> alt öğeleri düzenlenebilir ise.</span><span class="sxs-lookup"><span data-stu-id="d0105-113">The parent control must also support <xref:System.Windows.Automation.ValuePattern> if the child items are editable.</span></span>  
  
 <span data-ttu-id="d0105-114">![Düzenlenebilir bir liste öğesi. ] (../../../docs/framework/ui-automation/media/uia-valuepattern-editable-listitem.PNG "UIA_ValuePattern_Editable_ListItem")</span><span class="sxs-lookup"><span data-stu-id="d0105-114">![Editable list item.](../../../docs/framework/ui-automation/media/uia-valuepattern-editable-listitem.PNG "UIA_ValuePattern_Editable_ListItem")</span></span>  
<span data-ttu-id="d0105-115">Düzenlenebilir bir liste öğesi örneği</span><span class="sxs-lookup"><span data-stu-id="d0105-115">Example of an Editable List Item</span></span>  
  
-   <span data-ttu-id="d0105-116">Tek satırlı düzenleme denetimleri uygulayarak içeriklerini program erişimi destekleyen <xref:System.Windows.Automation.Provider.IValueProvider>.</span><span class="sxs-lookup"><span data-stu-id="d0105-116">Single-line edit controls support programmatic access to their contents by implementing <xref:System.Windows.Automation.Provider.IValueProvider>.</span></span> <span data-ttu-id="d0105-117">Ancak, çok satırlı düzenleme denetimlerinde uygulamayan <xref:System.Windows.Automation.Provider.IValueProvider>; bunun yerine uygulayarak içeriğine erişim sağlar <xref:System.Windows.Automation.Provider.ITextProvider>.</span><span class="sxs-lookup"><span data-stu-id="d0105-117">However, multi-line edit controls do not implement <xref:System.Windows.Automation.Provider.IValueProvider>; instead they provide access to their content by implementing <xref:System.Windows.Automation.Provider.ITextProvider>.</span></span>  
  
-   <span data-ttu-id="d0105-118">Çok satırlı düzenleme denetimi metin içeriğini almak için Denetim uygulamalıdır <xref:System.Windows.Automation.Provider.ITextProvider>.</span><span class="sxs-lookup"><span data-stu-id="d0105-118">To retrieve the textual contents of a multi-line edit control, the control must implement <xref:System.Windows.Automation.Provider.ITextProvider>.</span></span> <span data-ttu-id="d0105-119">Ancak, <xref:System.Windows.Automation.Provider.ITextProvider> bir denetimin değeri ayarını desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="d0105-119">However, <xref:System.Windows.Automation.Provider.ITextProvider> does not support setting the value of a control.</span></span>  
  
-   <span data-ttu-id="d0105-120"><xref:System.Windows.Automation.Provider.IValueProvider>bilgi veya alt dize değerleri biçimlendirme alma desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d0105-120"><xref:System.Windows.Automation.Provider.IValueProvider> does not support the retrieval of formatting information or substring values.</span></span> <span data-ttu-id="d0105-121">Uygulama <xref:System.Windows.Automation.Provider.ITextProvider> bu senaryolarda.</span><span class="sxs-lookup"><span data-stu-id="d0105-121">Implement <xref:System.Windows.Automation.Provider.ITextProvider> in these scenarios.</span></span>  
  
-   <span data-ttu-id="d0105-122"><xref:System.Windows.Automation.Provider.IValueProvider>denetimleri tarafından gibi uygulanmalı **Renk Seçici** Seçim denetiminden [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] (aşağıda Resimli), bir renk değeri (örneğin, "Sarı") ile eşdeğer bir iç arasındadizeeşlemedestekleyen[!INCLUDE[TLA#tla_rgb](../../../includes/tlasharptla-rgb-md.md)]yapısı.</span><span class="sxs-lookup"><span data-stu-id="d0105-122"><xref:System.Windows.Automation.Provider.IValueProvider> must be implemented by controls such as the **Color Picker** selection control from [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] (illustrated below), which supports string mapping between a color value (for example, "yellow") and an equivalent internal [!INCLUDE[TLA#tla_rgb](../../../includes/tlasharptla-rgb-md.md)] structure.</span></span>  
  
 <span data-ttu-id="d0105-123">![Renk Seçici vurgulanan sarı ile. ] (../../../docs/framework/ui-automation/media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")</span><span class="sxs-lookup"><span data-stu-id="d0105-123">![Color picker with yellow highlighted.](../../../docs/framework/ui-automation/media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")</span></span>  
<span data-ttu-id="d0105-124">Renk örneği dize eşleme örneği</span><span class="sxs-lookup"><span data-stu-id="d0105-124">Example of Color Swatch String Mapping</span></span>  
  
-   <span data-ttu-id="d0105-125">Bir denetim olmalıdır, <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> kümesine `true` ve kendi <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> kümesine `false` yapılan bir çağrı izin vermeden önce <xref:System.Windows.Automation.Provider.IValueProvider.SetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="d0105-125">A control should have its <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> set to `true` and its <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> set to `false` before allowing a call to <xref:System.Windows.Automation.Provider.IValueProvider.SetValue%2A>.</span></span>  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-ivalueprovider"></a><span data-ttu-id="d0105-126">Gerekli üyeleri IValueProvider için</span><span class="sxs-lookup"><span data-stu-id="d0105-126">Required Members for IValueProvider</span></span>  
 <span data-ttu-id="d0105-127">Aşağıdaki özellikleri ve yöntemleri uygulamak için gerekli olan <xref:System.Windows.Automation.Provider.IValueProvider>.</span><span class="sxs-lookup"><span data-stu-id="d0105-127">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IValueProvider>.</span></span>  
  
|<span data-ttu-id="d0105-128">Gerekli üyeleri</span><span class="sxs-lookup"><span data-stu-id="d0105-128">Required members</span></span>|<span data-ttu-id="d0105-129">Üye türü</span><span class="sxs-lookup"><span data-stu-id="d0105-129">Member type</span></span>|<span data-ttu-id="d0105-130">Notlar</span><span class="sxs-lookup"><span data-stu-id="d0105-130">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty>|<span data-ttu-id="d0105-131">Özellik</span><span class="sxs-lookup"><span data-stu-id="d0105-131">Property</span></span>|<span data-ttu-id="d0105-132">Yok.</span><span class="sxs-lookup"><span data-stu-id="d0105-132">None</span></span>|  
|<xref:System.Windows.Automation.ValuePattern.ValueProperty>|<span data-ttu-id="d0105-133">Özellik</span><span class="sxs-lookup"><span data-stu-id="d0105-133">Property</span></span>|<span data-ttu-id="d0105-134">Yok.</span><span class="sxs-lookup"><span data-stu-id="d0105-134">None</span></span>|  
|<xref:System.Windows.Automation.ValuePattern.SetValue%2A>|<span data-ttu-id="d0105-135">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d0105-135">Method</span></span>|<span data-ttu-id="d0105-136">Yok.</span><span class="sxs-lookup"><span data-stu-id="d0105-136">None</span></span>|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="d0105-137">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="d0105-137">Exceptions</span></span>  
 <span data-ttu-id="d0105-138">Sağlayıcıları aşağıdaki özel durumlar oluşturma gerekir.</span><span class="sxs-lookup"><span data-stu-id="d0105-138">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="d0105-139">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="d0105-139">Exception type</span></span>|<span data-ttu-id="d0105-140">Koşul</span><span class="sxs-lookup"><span data-stu-id="d0105-140">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> <span data-ttu-id="d0105-141">-Yerel ayarlara özgü bilgiler denetim hatalı biçimlendirilmiş bir tarihi gibi hatalı bir biçimde geçirilir</span><span class="sxs-lookup"><span data-stu-id="d0105-141">-   If locale-specific information is passed to a control in an incorrect format such as an incorrectly formatted date.</span></span>|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> <span data-ttu-id="d0105-142">-Yeni bir değer bir dizeden bir biçime dönüştürülemiyorsa denetimi tanır.</span><span class="sxs-lookup"><span data-stu-id="d0105-142">-   If a new value cannot be converted from a string to a format the control recognizes.</span></span>|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> <span data-ttu-id="d0105-143">-Zaman girişimini etkin bir denetim işlemek için yapılır.</span><span class="sxs-lookup"><span data-stu-id="d0105-143">-   When an attempt is made to manipulate a control that is not enabled.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d0105-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d0105-144">See Also</span></span>  
 [<span data-ttu-id="d0105-145">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d0105-145">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="d0105-146">UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="d0105-146">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="d0105-147">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="d0105-147">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="d0105-148">TextPattern Ekle metin örneği</span><span class="sxs-lookup"><span data-stu-id="d0105-148">TextPattern Insert Text Sample</span></span>](http://msdn.microsoft.com/library/67353f93-7ee2-42f2-ab76-5c078cf6ca16)  
 [<span data-ttu-id="d0105-149">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d0105-149">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="d0105-150">UI Otomasyonunda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="d0105-150">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
