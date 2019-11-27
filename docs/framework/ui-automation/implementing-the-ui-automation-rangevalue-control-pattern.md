---
title: UI Otomasyon RangeValue Denetim Düzeni Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
ms.openlocfilehash: 04db9f97ccea10cf8c65df0f0117c272a5e868dd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435109"
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a><span data-ttu-id="a05b4-102">UI Otomasyon RangeValue Denetim Düzeni Uygulama</span><span class="sxs-lookup"><span data-stu-id="a05b4-102">Implementing the UI Automation RangeValue Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="a05b4-103">Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="a05b4-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="a05b4-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="a05b4-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="a05b4-105">Bu konu, olaylar ve özellikler hakkında bilgiler de dahil olmak üzere <xref:System.Windows.Automation.Provider.IRangeValueProvider>uygulamak için kılavuz ve kuralları tanıtır.</span><span class="sxs-lookup"><span data-stu-id="a05b4-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IRangeValueProvider>, including information about events and properties.</span></span> <span data-ttu-id="a05b4-106">Ek başvuruların bağlantıları konunun sonunda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="a05b4-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="a05b4-107"><xref:System.Windows.Automation.RangeValuePattern> denetim deseninin bir Aralık içindeki bir değere ayarlanabilir denetimleri desteklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a05b4-107">The <xref:System.Windows.Automation.RangeValuePattern> control pattern is used to support controls that can be set to a value within a range.</span></span> <span data-ttu-id="a05b4-108">Bu denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="a05b4-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="a05b4-109">Uygulama kılavuzları ve kuralları</span><span class="sxs-lookup"><span data-stu-id="a05b4-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="a05b4-110">Aralık değeri denetim modelini uygularken, aşağıdaki kılavuz ve kurallara göz önünde aklınızda olmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="a05b4-110">When implementing the Range Value control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="a05b4-111">Denetimler, yerel ayar veya kullanıcı tercihlerine göre desteklenen özelliklerinin yeniden yüklenmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="a05b4-111">Controls allow recalibration of their supported properties based upon locale or user preference.</span></span> <span data-ttu-id="a05b4-112">Bunun bir örneği, sıcaklığın Fahrenveya santigrat cinsinden gösterilmesi için ayarlanabilir bir termometre denetimidir.</span><span class="sxs-lookup"><span data-stu-id="a05b4-112">An example of this is a thermometer control that can be set to display the temperature in Fahrenheit or Celsius.</span></span>  
  
- <span data-ttu-id="a05b4-113">İlerleme çubukları veya kaydırıcılar gibi belirsiz Aralık değerlerine sahip denetimler bu değerlerin normalleştirilmesine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a05b4-113">Controls that have ambiguous range values, such as progress bars or sliders, should have those values normalized.</span></span>  
  
 <span data-ttu-id="a05b4-114">![İlerleme çubuğu.](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span><span class="sxs-lookup"><span data-stu-id="a05b4-114">![Progress bar.](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span></span>  
<span data-ttu-id="a05b4-115">Değerin tamsayı türünde ve en düşük ve en yüksek özellik değerlerinin, sırasıyla 0 ve 100 olarak normalleştirilme Ilerleme çubuğu örneği</span><span class="sxs-lookup"><span data-stu-id="a05b4-115">Example of a Progress Bar Where Value Is of Type Integer and Minimum and Maximum Property Values Are Normalized to 0 and 100, Respectively</span></span>  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>   
## <a name="required-members-for-irangevalueprovider"></a><span data-ttu-id="a05b4-116">IRangeValueProvider için gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="a05b4-116">Required Members for IRangeValueProvider</span></span>  
  
|<span data-ttu-id="a05b4-117">Gerekli üye</span><span class="sxs-lookup"><span data-stu-id="a05b4-117">Required member</span></span>|<span data-ttu-id="a05b4-118">Üye türü</span><span class="sxs-lookup"><span data-stu-id="a05b4-118">Member type</span></span>|<span data-ttu-id="a05b4-119">Notlar</span><span class="sxs-lookup"><span data-stu-id="a05b4-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|<span data-ttu-id="a05b4-120">Özellik</span><span class="sxs-lookup"><span data-stu-id="a05b4-120">Property</span></span>|<span data-ttu-id="a05b4-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="a05b4-121">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|<span data-ttu-id="a05b4-122">Özellik</span><span class="sxs-lookup"><span data-stu-id="a05b4-122">Property</span></span>|<span data-ttu-id="a05b4-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="a05b4-123">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|<span data-ttu-id="a05b4-124">Özellik</span><span class="sxs-lookup"><span data-stu-id="a05b4-124">Property</span></span>|<span data-ttu-id="a05b4-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="a05b4-125">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|<span data-ttu-id="a05b4-126">Özellik</span><span class="sxs-lookup"><span data-stu-id="a05b4-126">Property</span></span>|<span data-ttu-id="a05b4-127">Yok.</span><span class="sxs-lookup"><span data-stu-id="a05b4-127">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|<span data-ttu-id="a05b4-128">Özellik</span><span class="sxs-lookup"><span data-stu-id="a05b4-128">Property</span></span>|<span data-ttu-id="a05b4-129">Yok.</span><span class="sxs-lookup"><span data-stu-id="a05b4-129">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|<span data-ttu-id="a05b4-130">Özellik</span><span class="sxs-lookup"><span data-stu-id="a05b4-130">Property</span></span>|<span data-ttu-id="a05b4-131">Yok.</span><span class="sxs-lookup"><span data-stu-id="a05b4-131">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|<span data-ttu-id="a05b4-132">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a05b4-132">Methods</span></span>|<span data-ttu-id="a05b4-133">Yok.</span><span class="sxs-lookup"><span data-stu-id="a05b4-133">None</span></span>|  
  
 <span data-ttu-id="a05b4-134">Bu denetim deseninin ilişkili olayları yok.</span><span class="sxs-lookup"><span data-stu-id="a05b4-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="a05b4-135">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="a05b4-135">Exceptions</span></span>  
 <span data-ttu-id="a05b4-136">Sağlayıcılar aşağıdaki özel durumları oluşturması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a05b4-136">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="a05b4-137">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="a05b4-137">Exception type</span></span>|<span data-ttu-id="a05b4-138">Koşul</span><span class="sxs-lookup"><span data-stu-id="a05b4-138">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<span data-ttu-id="a05b4-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>, <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> daha büyük veya <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>'den küçük bir değerle çağırılır.</span><span class="sxs-lookup"><span data-stu-id="a05b4-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> is called with a value that is either greater than <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> or less than <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a05b4-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a05b4-140">See also</span></span>

- [<span data-ttu-id="a05b4-141">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a05b4-141">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="a05b4-142">UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="a05b4-142">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="a05b4-143">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="a05b4-143">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="a05b4-144">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a05b4-144">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="a05b4-145">UI Otomasyonunda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="a05b4-145">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
