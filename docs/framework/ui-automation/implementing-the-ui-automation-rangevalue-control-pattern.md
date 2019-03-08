---
title: UI Otomasyon RangeValue Denetim Düzeni Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
ms.openlocfilehash: 34044b337dfb7498fd75f7f9a8bd17c2db9eb7d2
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57680119"
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a><span data-ttu-id="912aa-102">UI Otomasyon RangeValue Denetim Düzeni Uygulama</span><span class="sxs-lookup"><span data-stu-id="912aa-102">Implementing the UI Automation RangeValue Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="912aa-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="912aa-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="912aa-104">En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="912aa-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="912aa-105">Bu konu, yönergeleri ve uygulama kuralları tanıtır <xref:System.Windows.Automation.Provider.IRangeValueProvider>, olayları ve özellikleri hakkında bilgi dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="912aa-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IRangeValueProvider>, including information about events and properties.</span></span> <span data-ttu-id="912aa-106">Ek başvurular bağlantılar konunun sonunda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="912aa-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="912aa-107"><xref:System.Windows.Automation.RangeValuePattern> Denetim düzeni, bir aralık içindeki bir değere ayarlanabilir denetimleri desteklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="912aa-107">The <xref:System.Windows.Automation.RangeValuePattern> control pattern is used to support controls that can be set to a value within a range.</span></span> <span data-ttu-id="912aa-108">Bu denetim düzeni uygulama denetimleri örnekleri için bkz: [denetim düzeni eşlemesi için UI Otomasyonu istemcileri](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="912aa-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="912aa-109">Uygulama yönergeleri ve kuralları</span><span class="sxs-lookup"><span data-stu-id="912aa-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="912aa-110">Aralık değeri denetim düzeni uygularken aşağıdaki yönergeler ve kuralları dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="912aa-110">When implementing the Range Value control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="912aa-111">Denetimler yerel ayarına veya kullanıcı tercihi göre kendi desteklenen özellikler recalibration izin verir.</span><span class="sxs-lookup"><span data-stu-id="912aa-111">Controls allow recalibration of their supported properties based upon locale or user preference.</span></span> <span data-ttu-id="912aa-112">Buna örnek olarak, sıcaklığı Fahrenhayt veya Santigrat cinsinden görüntülemek için ayarlanabilir bir termometre denetimdir.</span><span class="sxs-lookup"><span data-stu-id="912aa-112">An example of this is a thermometer control that can be set to display the temperature in Fahrenheit or Celsius.</span></span>  
  
-   <span data-ttu-id="912aa-113">İlerleme çubukları veya kaydırıcıları, gibi belirsiz aralık değerleri denetimleri normalleştirilmiş bu değerlere sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="912aa-113">Controls that have ambiguous range values, such as progress bars or sliders, should have those values normalized.</span></span>  
  
 <span data-ttu-id="912aa-114">![Progress bar.](../../../docs/framework/ui-automation/media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span><span class="sxs-lookup"><span data-stu-id="912aa-114">![Progress bar.](../../../docs/framework/ui-automation/media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span></span>  
<span data-ttu-id="912aa-115">Değerin türü tamsayı ve Minimum ve maksimum özellik değerlerini olduğu bir ilerleme çubuğu örneği normalleştirilmiş 0 ile 100 için sırasıyla</span><span class="sxs-lookup"><span data-stu-id="912aa-115">Example of a Progress Bar Where Value Is of Type Integer and Minimum and Maximum Property Values Are Normalized to 0 and 100, Respectively</span></span>  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>   
## <a name="required-members-for-irangevalueprovider"></a><span data-ttu-id="912aa-116">Gerekli üyeleri IRangeValueProvider için</span><span class="sxs-lookup"><span data-stu-id="912aa-116">Required Members for IRangeValueProvider</span></span>  
  
|<span data-ttu-id="912aa-117">Gerekli üye</span><span class="sxs-lookup"><span data-stu-id="912aa-117">Required member</span></span>|<span data-ttu-id="912aa-118">Üye türü</span><span class="sxs-lookup"><span data-stu-id="912aa-118">Member type</span></span>|<span data-ttu-id="912aa-119">Notlar</span><span class="sxs-lookup"><span data-stu-id="912aa-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|<span data-ttu-id="912aa-120">Özellik</span><span class="sxs-lookup"><span data-stu-id="912aa-120">Property</span></span>|<span data-ttu-id="912aa-121">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="912aa-121">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|<span data-ttu-id="912aa-122">Özellik</span><span class="sxs-lookup"><span data-stu-id="912aa-122">Property</span></span>|<span data-ttu-id="912aa-123">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="912aa-123">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|<span data-ttu-id="912aa-124">Özellik</span><span class="sxs-lookup"><span data-stu-id="912aa-124">Property</span></span>|<span data-ttu-id="912aa-125">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="912aa-125">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|<span data-ttu-id="912aa-126">Özellik</span><span class="sxs-lookup"><span data-stu-id="912aa-126">Property</span></span>|<span data-ttu-id="912aa-127">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="912aa-127">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|<span data-ttu-id="912aa-128">Özellik</span><span class="sxs-lookup"><span data-stu-id="912aa-128">Property</span></span>|<span data-ttu-id="912aa-129">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="912aa-129">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|<span data-ttu-id="912aa-130">Özellik</span><span class="sxs-lookup"><span data-stu-id="912aa-130">Property</span></span>|<span data-ttu-id="912aa-131">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="912aa-131">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|<span data-ttu-id="912aa-132">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="912aa-132">Methods</span></span>|<span data-ttu-id="912aa-133">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="912aa-133">None</span></span>|  
  
 <span data-ttu-id="912aa-134">Bu denetim düzeni, ilişkili olay vardır.</span><span class="sxs-lookup"><span data-stu-id="912aa-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="912aa-135">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="912aa-135">Exceptions</span></span>  
 <span data-ttu-id="912aa-136">Sağlayıcıları, aşağıdaki özel durumlar gerekir.</span><span class="sxs-lookup"><span data-stu-id="912aa-136">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="912aa-137">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="912aa-137">Exception type</span></span>|<span data-ttu-id="912aa-138">Koşul</span><span class="sxs-lookup"><span data-stu-id="912aa-138">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<span data-ttu-id="912aa-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> Geçerli bir değerle çağrılır büyüktür <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> veya küçüktür <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span><span class="sxs-lookup"><span data-stu-id="912aa-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> is called with a value that is either greater than <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> or less than <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="912aa-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="912aa-140">See also</span></span>
- [<span data-ttu-id="912aa-141">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="912aa-141">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="912aa-142">UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="912aa-142">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="912aa-143">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="912aa-143">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="912aa-144">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="912aa-144">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [<span data-ttu-id="912aa-145">UI Otomasyonunda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="912aa-145">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
