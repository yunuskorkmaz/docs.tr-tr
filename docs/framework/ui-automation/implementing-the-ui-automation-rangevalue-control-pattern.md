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
ms.openlocfilehash: 219f460906d2892ae6cd76d13a2b17378e02b9b7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33399335"
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a><span data-ttu-id="d04e4-102">UI Otomasyon RangeValue Denetim Düzeni Uygulama</span><span class="sxs-lookup"><span data-stu-id="d04e4-102">Implementing the UI Automation RangeValue Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="d04e4-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="d04e4-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="d04e4-104">Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="d04e4-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="d04e4-105">Bu konu kılavuzları ve uygulamak için kuralları tanıtır <xref:System.Windows.Automation.Provider.IRangeValueProvider>, olayları ve özellikleri hakkındaki bilgileri de dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="d04e4-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IRangeValueProvider>, including information about events and properties.</span></span> <span data-ttu-id="d04e4-106">Ek başvurular bağlantılar konunun sonunda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="d04e4-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="d04e4-107"><xref:System.Windows.Automation.RangeValuePattern> Denetim düzeni bir aralık içinde bir değere ayarlanabilir denetimleri desteklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d04e4-107">The <xref:System.Windows.Automation.RangeValuePattern> control pattern is used to support controls that can be set to a value within a range.</span></span> <span data-ttu-id="d04e4-108">Bu denetim düzeni uygulama denetimleri örnekleri için bkz: [denetim düzeni eşleştirmesi UI Otomasyon istemcileri için](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="d04e4-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="d04e4-109">Uygulama rehberi ve kuralları</span><span class="sxs-lookup"><span data-stu-id="d04e4-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="d04e4-110">Aralık değeri denetim düzeni uygulama, aşağıdaki yönergeleri ve kuralları dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="d04e4-110">When implementing the Range Value control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="d04e4-111">Denetimler recalibration bunların desteklenen özelliklerinin yerel ayar veya kullanıcı alınarak izin verir.</span><span class="sxs-lookup"><span data-stu-id="d04e4-111">Controls allow recalibration of their supported properties based upon locale or user preference.</span></span> <span data-ttu-id="d04e4-112">Bunun bir örneğini sıcaklık Fahrenhayt veya derece cinsinden görüntülemek için ayarlayabileceğiniz bir termometre denetimdir.</span><span class="sxs-lookup"><span data-stu-id="d04e4-112">An example of this is a thermometer control that can be set to display the temperature in Fahrenheit or Celsius.</span></span>  
  
-   <span data-ttu-id="d04e4-113">İlerleme çubukları veya kaydırıcıları, gibi belirsiz aralık değerlerine sahip denetimleri normalleştirilmiş bu değerlere sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d04e4-113">Controls that have ambiguous range values, such as progress bars or sliders, should have those values normalized.</span></span>  
  
 <span data-ttu-id="d04e4-114">![İlerleme çubuğu. ] (../../../docs/framework/ui-automation/media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span><span class="sxs-lookup"><span data-stu-id="d04e4-114">![Progress bar.](../../../docs/framework/ui-automation/media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span></span>  
<span data-ttu-id="d04e4-115">Değerin türü tamsayı ve Minimum ve maksimum özellik değerlerini olduğu bir ilerleme çubuğu örneği normalleştirilmiş 0 ile 100, sırasıyla</span><span class="sxs-lookup"><span data-stu-id="d04e4-115">Example of a Progress Bar Where Value Is of Type Integer and Minimum and Maximum Property Values Are Normalized to 0 and 100, Respectively</span></span>  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>   
## <a name="required-members-for-irangevalueprovider"></a><span data-ttu-id="d04e4-116">Gerekli üyeleri IRangeValueProvider için</span><span class="sxs-lookup"><span data-stu-id="d04e4-116">Required Members for IRangeValueProvider</span></span>  
  
|<span data-ttu-id="d04e4-117">Gerekli üye</span><span class="sxs-lookup"><span data-stu-id="d04e4-117">Required member</span></span>|<span data-ttu-id="d04e4-118">Üye türü</span><span class="sxs-lookup"><span data-stu-id="d04e4-118">Member type</span></span>|<span data-ttu-id="d04e4-119">Notlar</span><span class="sxs-lookup"><span data-stu-id="d04e4-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|<span data-ttu-id="d04e4-120">Özellik</span><span class="sxs-lookup"><span data-stu-id="d04e4-120">Property</span></span>|<span data-ttu-id="d04e4-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="d04e4-121">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|<span data-ttu-id="d04e4-122">Özellik</span><span class="sxs-lookup"><span data-stu-id="d04e4-122">Property</span></span>|<span data-ttu-id="d04e4-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="d04e4-123">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|<span data-ttu-id="d04e4-124">Özellik</span><span class="sxs-lookup"><span data-stu-id="d04e4-124">Property</span></span>|<span data-ttu-id="d04e4-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="d04e4-125">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|<span data-ttu-id="d04e4-126">Özellik</span><span class="sxs-lookup"><span data-stu-id="d04e4-126">Property</span></span>|<span data-ttu-id="d04e4-127">Yok.</span><span class="sxs-lookup"><span data-stu-id="d04e4-127">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|<span data-ttu-id="d04e4-128">Özellik</span><span class="sxs-lookup"><span data-stu-id="d04e4-128">Property</span></span>|<span data-ttu-id="d04e4-129">Yok.</span><span class="sxs-lookup"><span data-stu-id="d04e4-129">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|<span data-ttu-id="d04e4-130">Özellik</span><span class="sxs-lookup"><span data-stu-id="d04e4-130">Property</span></span>|<span data-ttu-id="d04e4-131">Yok.</span><span class="sxs-lookup"><span data-stu-id="d04e4-131">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|<span data-ttu-id="d04e4-132">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d04e4-132">Methods</span></span>|<span data-ttu-id="d04e4-133">Yok.</span><span class="sxs-lookup"><span data-stu-id="d04e4-133">None</span></span>|  
  
 <span data-ttu-id="d04e4-134">Bu denetim düzeni ilişkili olay vardır.</span><span class="sxs-lookup"><span data-stu-id="d04e4-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="d04e4-135">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="d04e4-135">Exceptions</span></span>  
 <span data-ttu-id="d04e4-136">Sağlayıcıları aşağıdaki özel durumlar oluşturma gerekir.</span><span class="sxs-lookup"><span data-stu-id="d04e4-136">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="d04e4-137">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="d04e4-137">Exception type</span></span>|<span data-ttu-id="d04e4-138">Koşul</span><span class="sxs-lookup"><span data-stu-id="d04e4-138">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<span data-ttu-id="d04e4-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> herhangi bir değerle çağrılır büyük <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> veya küçüktür <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span><span class="sxs-lookup"><span data-stu-id="d04e4-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> is called with a value that is either greater than <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> or less than <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d04e4-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d04e4-140">See Also</span></span>  
 [<span data-ttu-id="d04e4-141">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d04e4-141">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="d04e4-142">UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="d04e4-142">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="d04e4-143">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="d04e4-143">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="d04e4-144">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d04e4-144">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="d04e4-145">UI Otomasyonunda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="d04e4-145">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
