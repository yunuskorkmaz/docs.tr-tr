---
title: UI Otomasyon RangeValue Denetim Düzeni Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
ms.openlocfilehash: 70ee5009e2763348f7c69613a1776e02e82e0391
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932132"
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a><span data-ttu-id="8135e-102">UI Otomasyon RangeValue Denetim Düzeni Uygulama</span><span class="sxs-lookup"><span data-stu-id="8135e-102">Implementing the UI Automation RangeValue Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="8135e-103">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="8135e-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="8135e-104">Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="8135e-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="8135e-105">Bu konu, olaylar ve özellikler hakkında bilgiler <xref:System.Windows.Automation.Provider.IRangeValueProvider>de dahil olmak üzere uygulama yönergelerini ve kurallarını tanıtır.</span><span class="sxs-lookup"><span data-stu-id="8135e-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IRangeValueProvider>, including information about events and properties.</span></span> <span data-ttu-id="8135e-106">Ek başvuruların bağlantıları konunun sonunda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="8135e-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="8135e-107"><xref:System.Windows.Automation.RangeValuePattern> Denetim deseninin bir Aralık içindeki bir değere ayarlanabilir denetimleri desteklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8135e-107">The <xref:System.Windows.Automation.RangeValuePattern> control pattern is used to support controls that can be set to a value within a range.</span></span> <span data-ttu-id="8135e-108">Bu denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="8135e-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="8135e-109">Uygulama kılavuzları ve kuralları</span><span class="sxs-lookup"><span data-stu-id="8135e-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="8135e-110">Aralık değeri denetim modelini uygularken, aşağıdaki kılavuz ve kurallara göz önünde aklınızda olmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="8135e-110">When implementing the Range Value control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="8135e-111">Denetimler, yerel ayar veya kullanıcı tercihlerine göre desteklenen özelliklerinin yeniden yüklenmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="8135e-111">Controls allow recalibration of their supported properties based upon locale or user preference.</span></span> <span data-ttu-id="8135e-112">Bunun bir örneği, sıcaklığın Fahrenveya santigrat cinsinden gösterilmesi için ayarlanabilir bir termometre denetimidir.</span><span class="sxs-lookup"><span data-stu-id="8135e-112">An example of this is a thermometer control that can be set to display the temperature in Fahrenheit or Celsius.</span></span>  
  
- <span data-ttu-id="8135e-113">İlerleme çubukları veya kaydırıcılar gibi belirsiz Aralık değerlerine sahip denetimler bu değerlerin normalleştirilmesine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8135e-113">Controls that have ambiguous range values, such as progress bars or sliders, should have those values normalized.</span></span>  
  
 <span data-ttu-id="8135e-114">![İlerleme çubuğu.](../../../docs/framework/ui-automation/media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span><span class="sxs-lookup"><span data-stu-id="8135e-114">![Progress bar.](../../../docs/framework/ui-automation/media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span></span>  
<span data-ttu-id="8135e-115">Değerin tamsayı türünde ve en düşük ve en yüksek özellik değerlerinin, sırasıyla 0 ve 100 olarak normalleştirilme Ilerleme çubuğu örneği</span><span class="sxs-lookup"><span data-stu-id="8135e-115">Example of a Progress Bar Where Value Is of Type Integer and Minimum and Maximum Property Values Are Normalized to 0 and 100, Respectively</span></span>  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>   
## <a name="required-members-for-irangevalueprovider"></a><span data-ttu-id="8135e-116">IRangeValueProvider için gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="8135e-116">Required Members for IRangeValueProvider</span></span>  
  
|<span data-ttu-id="8135e-117">Gerekli üye</span><span class="sxs-lookup"><span data-stu-id="8135e-117">Required member</span></span>|<span data-ttu-id="8135e-118">Üye türü</span><span class="sxs-lookup"><span data-stu-id="8135e-118">Member type</span></span>|<span data-ttu-id="8135e-119">Notlar</span><span class="sxs-lookup"><span data-stu-id="8135e-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|<span data-ttu-id="8135e-120">Özellik</span><span class="sxs-lookup"><span data-stu-id="8135e-120">Property</span></span>|<span data-ttu-id="8135e-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="8135e-121">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|<span data-ttu-id="8135e-122">Özellik</span><span class="sxs-lookup"><span data-stu-id="8135e-122">Property</span></span>|<span data-ttu-id="8135e-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="8135e-123">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|<span data-ttu-id="8135e-124">Özellik</span><span class="sxs-lookup"><span data-stu-id="8135e-124">Property</span></span>|<span data-ttu-id="8135e-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="8135e-125">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|<span data-ttu-id="8135e-126">Özellik</span><span class="sxs-lookup"><span data-stu-id="8135e-126">Property</span></span>|<span data-ttu-id="8135e-127">Yok.</span><span class="sxs-lookup"><span data-stu-id="8135e-127">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|<span data-ttu-id="8135e-128">Özellik</span><span class="sxs-lookup"><span data-stu-id="8135e-128">Property</span></span>|<span data-ttu-id="8135e-129">Yok.</span><span class="sxs-lookup"><span data-stu-id="8135e-129">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|<span data-ttu-id="8135e-130">Özellik</span><span class="sxs-lookup"><span data-stu-id="8135e-130">Property</span></span>|<span data-ttu-id="8135e-131">Yok.</span><span class="sxs-lookup"><span data-stu-id="8135e-131">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|<span data-ttu-id="8135e-132">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8135e-132">Methods</span></span>|<span data-ttu-id="8135e-133">Yok.</span><span class="sxs-lookup"><span data-stu-id="8135e-133">None</span></span>|  
  
 <span data-ttu-id="8135e-134">Bu denetim deseninin ilişkili olayları yok.</span><span class="sxs-lookup"><span data-stu-id="8135e-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="8135e-135">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="8135e-135">Exceptions</span></span>  
 <span data-ttu-id="8135e-136">Sağlayıcılar aşağıdaki özel durumları oluşturması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8135e-136">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="8135e-137">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="8135e-137">Exception type</span></span>|<span data-ttu-id="8135e-138">Koşul</span><span class="sxs-lookup"><span data-stu-id="8135e-138">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<span data-ttu-id="8135e-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>değerinden büyük <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> veya bundan <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>küçük bir değerle çağırılır.</span><span class="sxs-lookup"><span data-stu-id="8135e-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> is called with a value that is either greater than <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> or less than <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8135e-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8135e-140">See also</span></span>

- [<span data-ttu-id="8135e-141">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8135e-141">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="8135e-142">UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="8135e-142">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="8135e-143">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="8135e-143">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="8135e-144">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8135e-144">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [<span data-ttu-id="8135e-145">UI Otomasyonunda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="8135e-145">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
