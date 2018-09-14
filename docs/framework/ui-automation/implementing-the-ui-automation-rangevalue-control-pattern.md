---
title: UI Otomasyon RangeValue Denetim Düzeni Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 3736d1e8b23b8e05882a3fe016be0ac1a18ef51d
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45585440"
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a><span data-ttu-id="8eaa8-102">UI Otomasyon RangeValue Denetim Düzeni Uygulama</span><span class="sxs-lookup"><span data-stu-id="8eaa8-102">Implementing the UI Automation RangeValue Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="8eaa8-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="8eaa8-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="8eaa8-104">En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="8eaa8-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="8eaa8-105">Bu konu, yönergeleri ve uygulama kuralları tanıtır <xref:System.Windows.Automation.Provider.IRangeValueProvider>, olayları ve özellikleri hakkında bilgi dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="8eaa8-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IRangeValueProvider>, including information about events and properties.</span></span> <span data-ttu-id="8eaa8-106">Ek başvurular bağlantılar konunun sonunda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="8eaa8-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="8eaa8-107"><xref:System.Windows.Automation.RangeValuePattern> Denetim düzeni, bir aralık içindeki bir değere ayarlanabilir denetimleri desteklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8eaa8-107">The <xref:System.Windows.Automation.RangeValuePattern> control pattern is used to support controls that can be set to a value within a range.</span></span> <span data-ttu-id="8eaa8-108">Bu denetim düzeni uygulama denetimleri örnekleri için bkz: [denetim düzeni eşlemesi için UI Otomasyonu istemcileri](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="8eaa8-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="8eaa8-109">Uygulama yönergeleri ve kuralları</span><span class="sxs-lookup"><span data-stu-id="8eaa8-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="8eaa8-110">Aralık değeri denetim düzeni uygularken aşağıdaki yönergeler ve kuralları dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="8eaa8-110">When implementing the Range Value control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="8eaa8-111">Denetimler yerel ayarına veya kullanıcı tercihi göre kendi desteklenen özellikler recalibration izin verir.</span><span class="sxs-lookup"><span data-stu-id="8eaa8-111">Controls allow recalibration of their supported properties based upon locale or user preference.</span></span> <span data-ttu-id="8eaa8-112">Buna örnek olarak, sıcaklığı Fahrenhayt veya Santigrat cinsinden görüntülemek için ayarlanabilir bir termometre denetimdir.</span><span class="sxs-lookup"><span data-stu-id="8eaa8-112">An example of this is a thermometer control that can be set to display the temperature in Fahrenheit or Celsius.</span></span>  
  
-   <span data-ttu-id="8eaa8-113">İlerleme çubukları veya kaydırıcıları, gibi belirsiz aralık değerleri denetimleri normalleştirilmiş bu değerlere sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8eaa8-113">Controls that have ambiguous range values, such as progress bars or sliders, should have those values normalized.</span></span>  
  
 <span data-ttu-id="8eaa8-114">![İlerleme çubuğu. ](../../../docs/framework/ui-automation/media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span><span class="sxs-lookup"><span data-stu-id="8eaa8-114">![Progress bar.](../../../docs/framework/ui-automation/media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span></span>  
<span data-ttu-id="8eaa8-115">Değerin türü tamsayı ve Minimum ve maksimum özellik değerlerini olduğu bir ilerleme çubuğu örneği normalleştirilmiş 0 ile 100 için sırasıyla</span><span class="sxs-lookup"><span data-stu-id="8eaa8-115">Example of a Progress Bar Where Value Is of Type Integer and Minimum and Maximum Property Values Are Normalized to 0 and 100, Respectively</span></span>  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>   
## <a name="required-members-for-irangevalueprovider"></a><span data-ttu-id="8eaa8-116">Gerekli üyeleri IRangeValueProvider için</span><span class="sxs-lookup"><span data-stu-id="8eaa8-116">Required Members for IRangeValueProvider</span></span>  
  
|<span data-ttu-id="8eaa8-117">Gerekli üye</span><span class="sxs-lookup"><span data-stu-id="8eaa8-117">Required member</span></span>|<span data-ttu-id="8eaa8-118">Üye türü</span><span class="sxs-lookup"><span data-stu-id="8eaa8-118">Member type</span></span>|<span data-ttu-id="8eaa8-119">Notlar</span><span class="sxs-lookup"><span data-stu-id="8eaa8-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|<span data-ttu-id="8eaa8-120">Özellik</span><span class="sxs-lookup"><span data-stu-id="8eaa8-120">Property</span></span>|<span data-ttu-id="8eaa8-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="8eaa8-121">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|<span data-ttu-id="8eaa8-122">Özellik</span><span class="sxs-lookup"><span data-stu-id="8eaa8-122">Property</span></span>|<span data-ttu-id="8eaa8-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="8eaa8-123">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|<span data-ttu-id="8eaa8-124">Özellik</span><span class="sxs-lookup"><span data-stu-id="8eaa8-124">Property</span></span>|<span data-ttu-id="8eaa8-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="8eaa8-125">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|<span data-ttu-id="8eaa8-126">Özellik</span><span class="sxs-lookup"><span data-stu-id="8eaa8-126">Property</span></span>|<span data-ttu-id="8eaa8-127">Yok.</span><span class="sxs-lookup"><span data-stu-id="8eaa8-127">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|<span data-ttu-id="8eaa8-128">Özellik</span><span class="sxs-lookup"><span data-stu-id="8eaa8-128">Property</span></span>|<span data-ttu-id="8eaa8-129">Yok.</span><span class="sxs-lookup"><span data-stu-id="8eaa8-129">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|<span data-ttu-id="8eaa8-130">Özellik</span><span class="sxs-lookup"><span data-stu-id="8eaa8-130">Property</span></span>|<span data-ttu-id="8eaa8-131">Yok.</span><span class="sxs-lookup"><span data-stu-id="8eaa8-131">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|<span data-ttu-id="8eaa8-132">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8eaa8-132">Methods</span></span>|<span data-ttu-id="8eaa8-133">Yok.</span><span class="sxs-lookup"><span data-stu-id="8eaa8-133">None</span></span>|  
  
 <span data-ttu-id="8eaa8-134">Bu denetim düzeni, ilişkili olay vardır.</span><span class="sxs-lookup"><span data-stu-id="8eaa8-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="8eaa8-135">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="8eaa8-135">Exceptions</span></span>  
 <span data-ttu-id="8eaa8-136">Sağlayıcıları, aşağıdaki özel durumlar gerekir.</span><span class="sxs-lookup"><span data-stu-id="8eaa8-136">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="8eaa8-137">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="8eaa8-137">Exception type</span></span>|<span data-ttu-id="8eaa8-138">Koşul</span><span class="sxs-lookup"><span data-stu-id="8eaa8-138">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<span data-ttu-id="8eaa8-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> Geçerli bir değerle çağrılır büyüktür <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> veya küçüktür <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span><span class="sxs-lookup"><span data-stu-id="8eaa8-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> is called with a value that is either greater than <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> or less than <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8eaa8-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8eaa8-140">See Also</span></span>  
 [<span data-ttu-id="8eaa8-141">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8eaa8-141">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="8eaa8-142">UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="8eaa8-142">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="8eaa8-143">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="8eaa8-143">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="8eaa8-144">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8eaa8-144">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="8eaa8-145">UI Otomasyonunda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="8eaa8-145">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
