---
title: UI Otomasyonu Değiştirme Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- Toggle control pattern
- control patterns, Toggle
- UI Automation, Toggle control pattern
ms.assetid: 3cfe875f-b0c0-413d-9703-5f14e6a1a30e
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 3d9ab6de0c398f466efb5535f34553b78a715c8e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43394484"
---
# <a name="implementing-the-ui-automation-toggle-control-pattern"></a><span data-ttu-id="415cb-102">UI Otomasyonu Değiştirme Denetim Düzenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="415cb-102">Implementing the UI Automation Toggle Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="415cb-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="415cb-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="415cb-104">En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="415cb-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="415cb-105">Bu konu, yönergeleri ve uygulama kuralları tanıtır <xref:System.Windows.Automation.Provider.IToggleProvider>, yöntemleri ve özellikleri hakkında bilgi dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="415cb-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>, including information about methods and properties.</span></span> <span data-ttu-id="415cb-106">Ek başvurular bağlantılar konunun sonunda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="415cb-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="415cb-107"><xref:System.Windows.Automation.TogglePattern> Denetim düzeni geçiş durumları kümesi aracılığıyla ve bir durum ayarlamalı korumak denetimleri desteklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="415cb-107">The <xref:System.Windows.Automation.TogglePattern> control pattern is used to support controls that can cycle through a set of states and maintain a state once set.</span></span> <span data-ttu-id="415cb-108">Bu denetim düzeni uygulama denetimleri örnekleri için bkz: [denetim düzeni eşlemesi için UI Otomasyonu istemcileri](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="415cb-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="415cb-109">Uygulama yönergeleri ve kuralları</span><span class="sxs-lookup"><span data-stu-id="415cb-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="415cb-110">Toggle denetim desenini uygulama, aşağıdaki yönergeleri ve kuralları dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="415cb-110">When implementing the Toggle control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="415cb-111">Aktifleştirilmiş düğmeler, düğmeler ve köprüler gibi durum bilgisi bulundurmaz denetimleri uygulanmalı <xref:System.Windows.Automation.Provider.IInvokeProvider> yerine.</span><span class="sxs-lookup"><span data-stu-id="415cb-111">Controls that do not maintain state when activated, such as buttons, toolbar buttons, and hyperlinks, must implement <xref:System.Windows.Automation.Provider.IInvokeProvider> instead.</span></span>  
  
-   <span data-ttu-id="415cb-112">Bir denetim dolaşma gerekir, <xref:System.Windows.Automation.ToggleState> aşağıdaki sırayla: <xref:System.Windows.Automation.ToggleState.On>, <xref:System.Windows.Automation.ToggleState.Off> ve destekleniyorsa, <xref:System.Windows.Automation.ToggleState.Indeterminate>.</span><span class="sxs-lookup"><span data-stu-id="415cb-112">A control must cycle through its <xref:System.Windows.Automation.ToggleState> in the following order: <xref:System.Windows.Automation.ToggleState.On>, <xref:System.Windows.Automation.ToggleState.Off> and, if supported, <xref:System.Windows.Automation.ToggleState.Indeterminate>.</span></span>  
  
-   <span data-ttu-id="415cb-113"><xref:System.Windows.Automation.TogglePattern> üç durum onay kutusu doğrudan ayarını, uygun dönüşüm olmadan çevreleyen sorunları nedeniyle bir SetState(newState) yöntem sağlamaz <xref:System.Windows.Automation.ToggleState> dizisi.</span><span class="sxs-lookup"><span data-stu-id="415cb-113"><xref:System.Windows.Automation.TogglePattern> does not provide a SetState(newState) method due to issues surrounding the direct setting of a tri-state CheckBox without cycling through its appropriate <xref:System.Windows.Automation.ToggleState> sequence.</span></span>  
  
-   <span data-ttu-id="415cb-114">RadioButton denetimi uygulamıyor <xref:System.Windows.Automation.Provider.IToggleProvider>gibi geçerli durumları arasında geçiş yapma uyumlu değil.</span><span class="sxs-lookup"><span data-stu-id="415cb-114">The RadioButton control does not implement <xref:System.Windows.Automation.Provider.IToggleProvider>, as it is not capable of cycling through its valid states.</span></span>  
  
<a name="Required_Members_for_IToggleProvider"></a>   
## <a name="required-members-for-itoggleprovider"></a><span data-ttu-id="415cb-115">Gerekli üyeleri IToggleProvider için</span><span class="sxs-lookup"><span data-stu-id="415cb-115">Required Members for IToggleProvider</span></span>  
 <span data-ttu-id="415cb-116">Aşağıdaki özellikleri ve yöntemleri uygulamak için gerekli olan <xref:System.Windows.Automation.Provider.IToggleProvider>.</span><span class="sxs-lookup"><span data-stu-id="415cb-116">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>.</span></span>  
  
|<span data-ttu-id="415cb-117">Gerekli üye</span><span class="sxs-lookup"><span data-stu-id="415cb-117">Required member</span></span>|<span data-ttu-id="415cb-118">Üye türü</span><span class="sxs-lookup"><span data-stu-id="415cb-118">Member type</span></span>|<span data-ttu-id="415cb-119">Notlar</span><span class="sxs-lookup"><span data-stu-id="415cb-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.TogglePattern.Toggle%2A>|<span data-ttu-id="415cb-120">Yöntem</span><span class="sxs-lookup"><span data-stu-id="415cb-120">Method</span></span>|<span data-ttu-id="415cb-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="415cb-121">None</span></span>|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>|<span data-ttu-id="415cb-122">Özellik</span><span class="sxs-lookup"><span data-stu-id="415cb-122">Property</span></span>|<span data-ttu-id="415cb-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="415cb-123">None</span></span>|  
  
 <span data-ttu-id="415cb-124">Bu denetim düzeni, ilişkili olay vardır.</span><span class="sxs-lookup"><span data-stu-id="415cb-124">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="415cb-125">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="415cb-125">Exceptions</span></span>  
 <span data-ttu-id="415cb-126">Bu denetim düzeni ilişkili hiçbir özel durum vardır.</span><span class="sxs-lookup"><span data-stu-id="415cb-126">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="415cb-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="415cb-127">See Also</span></span>  
 [<span data-ttu-id="415cb-128">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="415cb-128">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="415cb-129">UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="415cb-129">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="415cb-130">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="415cb-130">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="415cb-131">UI Otomasyonunu Kullanarak Onay Kutusunun Değiştir Durumunu Alma</span><span class="sxs-lookup"><span data-stu-id="415cb-131">Get the Toggle State of a Check Box Using UI Automation</span></span>](../../../docs/framework/ui-automation/get-the-toggle-state-of-a-check-box-using-ui-automation.md)  
 [<span data-ttu-id="415cb-132">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="415cb-132">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="415cb-133">UI Otomasyonunda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="415cb-133">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
