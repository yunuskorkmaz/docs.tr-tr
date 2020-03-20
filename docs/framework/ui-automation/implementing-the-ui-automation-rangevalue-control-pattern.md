---
title: UI Otomasyon RangeValue Denetim Düzeni Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
ms.openlocfilehash: 847a8aae3fd0c3d6965c910d19a4cec11cd2a3b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180174"
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a><span data-ttu-id="0b454-102">UI Otomasyon RangeValue Denetim Düzeni Uygulama</span><span class="sxs-lookup"><span data-stu-id="0b454-102">Implementing the UI Automation RangeValue Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="0b454-103">Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0b454-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="0b454-104">Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="0b454-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="0b454-105">Bu <xref:System.Windows.Automation.Provider.IRangeValueProvider>konu, olaylar ve özellikler hakkında bilgiler de dahil olmak üzere, uygulama yönergeleri ve kuralları sunar.</span><span class="sxs-lookup"><span data-stu-id="0b454-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IRangeValueProvider>, including information about events and properties.</span></span> <span data-ttu-id="0b454-106">Ek başvurulara bağlantılar konunun sonunda listelenir.</span><span class="sxs-lookup"><span data-stu-id="0b454-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="0b454-107">Denetim <xref:System.Windows.Automation.RangeValuePattern> deseni, aralıktaki bir değere ayarlanabilen denetimleri desteklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0b454-107">The <xref:System.Windows.Automation.RangeValuePattern> control pattern is used to support controls that can be set to a value within a range.</span></span> <span data-ttu-id="0b454-108">Bu denetim deseni uygulayan denetim örnekleri için, [UI Otomasyon Istemcileri için Denetim Deseni Eşleciliği'ne](control-pattern-mapping-for-ui-automation-clients.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="0b454-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="0b454-109">Uygulama Yönergeleri ve Sözleşmeleri</span><span class="sxs-lookup"><span data-stu-id="0b454-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="0b454-110">Aralık Değeri denetim deseni uygulanırken aşağıdaki yönergeleri ve kuralları not edin:</span><span class="sxs-lookup"><span data-stu-id="0b454-110">When implementing the Range Value control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="0b454-111">Denetimler, desteklenen özelliklerinin yerel veya kullanıcı tercihine göre yeniden kalibrasyonuna olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="0b454-111">Controls allow recalibration of their supported properties based upon locale or user preference.</span></span> <span data-ttu-id="0b454-112">Bunun bir örneği, Sıcaklığı Fahrenhayt veya Santigrat cinsinden görüntülemek üzere ayarlanabilen bir termometre kontrolüdür.</span><span class="sxs-lookup"><span data-stu-id="0b454-112">An example of this is a thermometer control that can be set to display the temperature in Fahrenheit or Celsius.</span></span>  
  
- <span data-ttu-id="0b454-113">İlerleme çubukları veya kaydırıcılar gibi belirsiz aralık değerlerine sahip denetimler, bu değerleri normalleştirmelidir.</span><span class="sxs-lookup"><span data-stu-id="0b454-113">Controls that have ambiguous range values, such as progress bars or sliders, should have those values normalized.</span></span>  
  
 <span data-ttu-id="0b454-114">![İlerleme çubuğu.](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span><span class="sxs-lookup"><span data-stu-id="0b454-114">![Progress bar.](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span></span>  
<span data-ttu-id="0b454-115">Değerin Tür Tamsayı olduğu ve Minimum ve Maksimum Özellik Değerlerinin Sırasıyla 0 ve 100'e Normalleştirildiği İlerleme Çubuğu Örneği</span><span class="sxs-lookup"><span data-stu-id="0b454-115">Example of a Progress Bar Where Value Is of Type Integer and Minimum and Maximum Property Values Are Normalized to 0 and 100, Respectively</span></span>  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>
## <a name="required-members-for-irangevalueprovider"></a><span data-ttu-id="0b454-116">IRangeValueProvider için Gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="0b454-116">Required Members for IRangeValueProvider</span></span>  
  
|<span data-ttu-id="0b454-117">Gerekli üye</span><span class="sxs-lookup"><span data-stu-id="0b454-117">Required member</span></span>|<span data-ttu-id="0b454-118">Üye tipi</span><span class="sxs-lookup"><span data-stu-id="0b454-118">Member type</span></span>|<span data-ttu-id="0b454-119">Notlar</span><span class="sxs-lookup"><span data-stu-id="0b454-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|<span data-ttu-id="0b454-120">Özellik</span><span class="sxs-lookup"><span data-stu-id="0b454-120">Property</span></span>|<span data-ttu-id="0b454-121">None</span><span class="sxs-lookup"><span data-stu-id="0b454-121">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|<span data-ttu-id="0b454-122">Özellik</span><span class="sxs-lookup"><span data-stu-id="0b454-122">Property</span></span>|<span data-ttu-id="0b454-123">None</span><span class="sxs-lookup"><span data-stu-id="0b454-123">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|<span data-ttu-id="0b454-124">Özellik</span><span class="sxs-lookup"><span data-stu-id="0b454-124">Property</span></span>|<span data-ttu-id="0b454-125">None</span><span class="sxs-lookup"><span data-stu-id="0b454-125">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|<span data-ttu-id="0b454-126">Özellik</span><span class="sxs-lookup"><span data-stu-id="0b454-126">Property</span></span>|<span data-ttu-id="0b454-127">None</span><span class="sxs-lookup"><span data-stu-id="0b454-127">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|<span data-ttu-id="0b454-128">Özellik</span><span class="sxs-lookup"><span data-stu-id="0b454-128">Property</span></span>|<span data-ttu-id="0b454-129">None</span><span class="sxs-lookup"><span data-stu-id="0b454-129">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|<span data-ttu-id="0b454-130">Özellik</span><span class="sxs-lookup"><span data-stu-id="0b454-130">Property</span></span>|<span data-ttu-id="0b454-131">None</span><span class="sxs-lookup"><span data-stu-id="0b454-131">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|<span data-ttu-id="0b454-132">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0b454-132">Methods</span></span>|<span data-ttu-id="0b454-133">None</span><span class="sxs-lookup"><span data-stu-id="0b454-133">None</span></span>|  
  
 <span data-ttu-id="0b454-134">Bu denetim deseni ilişkili olaylar vardır.</span><span class="sxs-lookup"><span data-stu-id="0b454-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="0b454-135">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="0b454-135">Exceptions</span></span>  
 <span data-ttu-id="0b454-136">Sağlayıcılar aşağıdaki özel durumları atmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0b454-136">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="0b454-137">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="0b454-137">Exception type</span></span>|<span data-ttu-id="0b454-138">Koşul</span><span class="sxs-lookup"><span data-stu-id="0b454-138">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<span data-ttu-id="0b454-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>'den <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> büyük veya daha az bir <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>değerle çağrılır.</span><span class="sxs-lookup"><span data-stu-id="0b454-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> is called with a value that is either greater than <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> or less than <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0b454-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b454-140">See also</span></span>

- [<span data-ttu-id="0b454-141">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0b454-141">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="0b454-142">UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="0b454-142">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="0b454-143">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="0b454-143">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="0b454-144">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0b454-144">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="0b454-145">UI Otomasyonunda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="0b454-145">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
