---
title: UI Otomasyonu Dönüştürme Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Transform
- Transform control pattern
- UI Automation, Transform control pattern
ms.assetid: 5f49d843-5845-4800-9d9c-56ce0d146844
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 65c90e8e9f0653181b98645bf453c9d78c14bc15
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408271"
---
# <a name="implementing-the-ui-automation-transform-control-pattern"></a><span data-ttu-id="e9e16-102">UI Otomasyonu Dönüştürme Denetim Düzenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="e9e16-102">Implementing the UI Automation Transform Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="e9e16-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="e9e16-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="e9e16-104">Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="e9e16-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="e9e16-105">Bu konu kılavuzları ve uygulamak için kuralları tanıtır <xref:System.Windows.Automation.Provider.ITransformProvider>, özellikleri, yöntemleri ve etkinlikleri hakkında bilgiler dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="e9e16-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITransformProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="e9e16-106">Ek başvurular bağlantılar konunun sonunda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="e9e16-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="e9e16-107"><xref:System.Windows.Automation.TransformPattern> Denetim düzeni taşınmış, yeniden boyutlandırılmış veya iki boyutlu bir boşluğuna Döndürülmüş denetimleri desteklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e9e16-107">The <xref:System.Windows.Automation.TransformPattern> control pattern is used to support controls that can be moved, resized, or rotated within a two-dimensional space.</span></span> <span data-ttu-id="e9e16-108">Bu denetim düzeni uygulama denetimleri örnekleri için bkz: [denetim düzeni eşleştirmesi UI Otomasyon istemcileri için](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="e9e16-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="e9e16-109">Uygulama rehberi ve kuralları</span><span class="sxs-lookup"><span data-stu-id="e9e16-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="e9e16-110">Dönüştürme denetim düzenini uygulama, aşağıdaki yönergeleri ve kuralları dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="e9e16-110">When implementing the Transform control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="e9e16-111">Bu denetim düzeni için destek masaüstündeki nesneler için sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="e9e16-111">Support for this control pattern is not limited to objects on the desktop.</span></span> <span data-ttu-id="e9e16-112">Alt taşınmış, yeniden boyutlandırılmış veya serbestçe kapsayıcı sınırlar içinde Döndürülmüş bu denetim düzeni ayrıca bir kapsayıcı nesne gruplar tarafından desteklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e9e16-112">This control pattern must also be supported by the children of a container object if the children can be moved, resized, or rotated freely within the boundaries of the container.</span></span>  
  
-   <span data-ttu-id="e9e16-113">Bir nesne taşınamaz, yeniden boyutlandırılabilir ya da sonuçta elde edilen ekran konumuna veya tamamen kapsayıcısının ve bu nedenle klavye için erişilemez koordinatları dışında olabilir (örneğin, üst düzey bir pencere off-screen taşındığında veya bir fare şekilde Döndürülmüş alt nesne kapsayıcının görünüm penceresinin sınırları dışında taşınır).</span><span class="sxs-lookup"><span data-stu-id="e9e16-113">An object cannot be moved, resized, or rotated such that its resulting screen location would be completely outside the coordinates of its container and therefore inaccessible to the keyboard or mouse (for example, when a top-level window is moved off-screen or a child object is moved outside the boundaries of the container's viewport).</span></span> <span data-ttu-id="e9e16-114">Bu durumlarda, nesne, istenen ekran koordinatları olarak mümkün olduğunca kapsayıcı sınırlar içinde geçersiz üst veya sol koordinatları ile yakın yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e9e16-114">In these cases, the object is placed as close to the requested screen coordinates as possible with the top or left coordinates overridden to be within the container boundaries.</span></span>  
  
-   <span data-ttu-id="e9e16-115">Bir nesne taşınırsa, birden çok monitör sistemler için yeniden boyutlandırılmış veya birleştirilmiş masaüstü ekran koordinatları tamamen dışında döndürülen nesne birincil monitörde istenen koordinatları olarak mümkün olduğunca yakın yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e9e16-115">For multi-monitor systems, if an object is moved, resized, or rotated completely outside the combined desktop screen coordinates, the object is placed on the primary monitor as close to the requested coordinates as possible.</span></span>  
  
-   <span data-ttu-id="e9e16-116">Tüm parametreleri ve özellik değerlerini mutlak ve yerel ayar bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="e9e16-116">All parameters and property values are absolute and independent of locale.</span></span>  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-itransformprovider"></a><span data-ttu-id="e9e16-117">Gerekli üyeleri ITransformProvider için</span><span class="sxs-lookup"><span data-stu-id="e9e16-117">Required Members for ITransformProvider</span></span>  
 <span data-ttu-id="e9e16-118">Aşağıdaki özellikleri ve yöntemleri uygulamak için gerekli olan <xref:System.Windows.Automation.Provider.ITransformProvider>.</span><span class="sxs-lookup"><span data-stu-id="e9e16-118">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.ITransformProvider>.</span></span>  
  
|<span data-ttu-id="e9e16-119">Gerekli üyeleri</span><span class="sxs-lookup"><span data-stu-id="e9e16-119">Required members</span></span>|<span data-ttu-id="e9e16-120">Üye türü</span><span class="sxs-lookup"><span data-stu-id="e9e16-120">Member type</span></span>|<span data-ttu-id="e9e16-121">Notlar</span><span class="sxs-lookup"><span data-stu-id="e9e16-121">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanMove%2A>|<span data-ttu-id="e9e16-122">Özellik</span><span class="sxs-lookup"><span data-stu-id="e9e16-122">Property</span></span>|<span data-ttu-id="e9e16-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="e9e16-123">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanResize%2A>|<span data-ttu-id="e9e16-124">Özellik</span><span class="sxs-lookup"><span data-stu-id="e9e16-124">Property</span></span>|<span data-ttu-id="e9e16-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="e9e16-125">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanRotate%2A>|<span data-ttu-id="e9e16-126">Özellik</span><span class="sxs-lookup"><span data-stu-id="e9e16-126">Property</span></span>|<span data-ttu-id="e9e16-127">Yok.</span><span class="sxs-lookup"><span data-stu-id="e9e16-127">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A>|<span data-ttu-id="e9e16-128">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e9e16-128">Method</span></span>|<span data-ttu-id="e9e16-129">Yok.</span><span class="sxs-lookup"><span data-stu-id="e9e16-129">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A>|<span data-ttu-id="e9e16-130">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e9e16-130">Method</span></span>|<span data-ttu-id="e9e16-131">Yok.</span><span class="sxs-lookup"><span data-stu-id="e9e16-131">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A>|<span data-ttu-id="e9e16-132">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e9e16-132">Method</span></span>|<span data-ttu-id="e9e16-133">Yok.</span><span class="sxs-lookup"><span data-stu-id="e9e16-133">None</span></span>|  
  
 <span data-ttu-id="e9e16-134">Bu denetim düzeni ilişkili olay vardır.</span><span class="sxs-lookup"><span data-stu-id="e9e16-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="e9e16-135">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="e9e16-135">Exceptions</span></span>  
 <span data-ttu-id="e9e16-136">Sağlayıcıları aşağıdaki özel durumlar oluşturma gerekir.</span><span class="sxs-lookup"><span data-stu-id="e9e16-136">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="e9e16-137">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="e9e16-137">Exception Type</span></span>|<span data-ttu-id="e9e16-138">Koşul</span><span class="sxs-lookup"><span data-stu-id="e9e16-138">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A><br /><br /> <span data-ttu-id="e9e16-139">-İf <xref:System.Windows.Automation.TransformPatternIdentifiers.CanMoveProperty> false olur.</span><span class="sxs-lookup"><span data-stu-id="e9e16-139">-   If the <xref:System.Windows.Automation.TransformPatternIdentifiers.CanMoveProperty> is false.</span></span>|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A><br /><br /> <span data-ttu-id="e9e16-140">-İf <xref:System.Windows.Automation.TransformPatternIdentifiers.CanResizeProperty> false olur.</span><span class="sxs-lookup"><span data-stu-id="e9e16-140">-   If the <xref:System.Windows.Automation.TransformPatternIdentifiers.CanResizeProperty> is false.</span></span>|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A><br /><br /> <span data-ttu-id="e9e16-141">-İf <xref:System.Windows.Automation.TransformPatternIdentifiers.CanRotateProperty> false olur.</span><span class="sxs-lookup"><span data-stu-id="e9e16-141">-   If the <xref:System.Windows.Automation.TransformPatternIdentifiers.CanRotateProperty> is false.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e9e16-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e9e16-142">See Also</span></span>  
 [<span data-ttu-id="e9e16-143">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e9e16-143">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="e9e16-144">UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="e9e16-144">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="e9e16-145">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="e9e16-145">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="e9e16-146">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e9e16-146">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="e9e16-147">UI Otomasyonunda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="e9e16-147">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
