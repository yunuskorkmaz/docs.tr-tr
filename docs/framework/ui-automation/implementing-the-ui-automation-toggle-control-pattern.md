---
title: UI Otomasyonu Değiştirme Denetim Düzenini Uygulama
description: UI otomasyonunda Iki durumlu denetim deseninin uygulanması için yönergeleri ve kuralları gözden geçirin. IToggleProvider arabirimi için gerekli üyeleri öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- Toggle control pattern
- control patterns, Toggle
- UI Automation, Toggle control pattern
ms.assetid: 3cfe875f-b0c0-413d-9703-5f14e6a1a30e
ms.openlocfilehash: f9ae850a560101582b5f1a461de19f260ef59798
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168038"
---
# <a name="implementing-the-ui-automation-toggle-control-pattern"></a><span data-ttu-id="f922a-104">UI Otomasyonu Değiştirme Denetim Düzenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="f922a-104">Implementing the UI Automation Toggle Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="f922a-105">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> .</span><span class="sxs-lookup"><span data-stu-id="f922a-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="f922a-106">Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="f922a-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="f922a-107">Bu konu <xref:System.Windows.Automation.Provider.IToggleProvider> , Yöntemler ve özellikler hakkında bilgiler de dahil olmak üzere uygulama yönergelerini ve kurallarını tanıtır.</span><span class="sxs-lookup"><span data-stu-id="f922a-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>, including information about methods and properties.</span></span> <span data-ttu-id="f922a-108">Ek başvuruların bağlantıları konunun sonunda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="f922a-108">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="f922a-109"><xref:System.Windows.Automation.TogglePattern>Denetim stili, bir durum kümesi boyunca geçiş yapan ve bir kez ayarlandıktan sonra bir durumu korumak için kullanılan denetimleri desteklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f922a-109">The <xref:System.Windows.Automation.TogglePattern> control pattern is used to support controls that can cycle through a set of states and maintain a state once set.</span></span> <span data-ttu-id="f922a-110">Bu denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="f922a-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="f922a-111">Uygulama kılavuzları ve kuralları</span><span class="sxs-lookup"><span data-stu-id="f922a-111">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="f922a-112">Iki durumlu denetim modelini uygularken aşağıdaki kılavuz ve kurallara göz önünde</span><span class="sxs-lookup"><span data-stu-id="f922a-112">When implementing the Toggle control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="f922a-113">Etkin olduğunda, düğme, araç çubuğu düğmeleri ve köprüler gibi durumları korumayan denetimler <xref:System.Windows.Automation.Provider.IInvokeProvider> bunun yerine uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f922a-113">Controls that do not maintain state when activated, such as buttons, toolbar buttons, and hyperlinks, must implement <xref:System.Windows.Automation.Provider.IInvokeProvider> instead.</span></span>  
  
- <span data-ttu-id="f922a-114">Bir denetim,, destekleniyorsa, <xref:System.Windows.Automation.ToggleState> aşağıdaki sırayla ilerlemeli: <xref:System.Windows.Automation.ToggleState.On> , <xref:System.Windows.Automation.ToggleState.Off> ve destekleniyorsa <xref:System.Windows.Automation.ToggleState.Indeterminate> .</span><span class="sxs-lookup"><span data-stu-id="f922a-114">A control must cycle through its <xref:System.Windows.Automation.ToggleState> in the following order: <xref:System.Windows.Automation.ToggleState.On>, <xref:System.Windows.Automation.ToggleState.Off> and, if supported, <xref:System.Windows.Automation.ToggleState.Indeterminate>.</span></span>  
  
- <span data-ttu-id="f922a-115"><xref:System.Windows.Automation.TogglePattern>, Üçlü durum onay kutusunun doğrudan ayarını çevreleyen sorunlar nedeniyle, uygun sırası boyunca geçiş yapılmadan bir SetState (newState) yöntemi sağlamaz <xref:System.Windows.Automation.ToggleState> .</span><span class="sxs-lookup"><span data-stu-id="f922a-115"><xref:System.Windows.Automation.TogglePattern> does not provide a SetState(newState) method due to issues surrounding the direct setting of a tri-state CheckBox without cycling through its appropriate <xref:System.Windows.Automation.ToggleState> sequence.</span></span>  
  
- <span data-ttu-id="f922a-116">RadioButton denetimi <xref:System.Windows.Automation.Provider.IToggleProvider> geçerli durumları arasında geçiş yeteneğine sahip olmadığından uygulamaz.</span><span class="sxs-lookup"><span data-stu-id="f922a-116">The RadioButton control does not implement <xref:System.Windows.Automation.Provider.IToggleProvider>, as it is not capable of cycling through its valid states.</span></span>  
  
<a name="Required_Members_for_IToggleProvider"></a>
## <a name="required-members-for-itoggleprovider"></a><span data-ttu-id="f922a-117">IToggleProvider için gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="f922a-117">Required Members for IToggleProvider</span></span>  
 <span data-ttu-id="f922a-118">Uygulamak için aşağıdaki özellikler ve Yöntemler gereklidir <xref:System.Windows.Automation.Provider.IToggleProvider> .</span><span class="sxs-lookup"><span data-stu-id="f922a-118">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>.</span></span>  
  
|<span data-ttu-id="f922a-119">Gerekli üye</span><span class="sxs-lookup"><span data-stu-id="f922a-119">Required member</span></span>|<span data-ttu-id="f922a-120">Üye türü</span><span class="sxs-lookup"><span data-stu-id="f922a-120">Member type</span></span>|<span data-ttu-id="f922a-121">Notlar</span><span class="sxs-lookup"><span data-stu-id="f922a-121">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.TogglePattern.Toggle%2A>|<span data-ttu-id="f922a-122">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f922a-122">Method</span></span>|<span data-ttu-id="f922a-123">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="f922a-123">None</span></span>|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>|<span data-ttu-id="f922a-124">Özellik</span><span class="sxs-lookup"><span data-stu-id="f922a-124">Property</span></span>|<span data-ttu-id="f922a-125">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="f922a-125">None</span></span>|  
  
 <span data-ttu-id="f922a-126">Bu denetim deseninin ilişkili olayları yok.</span><span class="sxs-lookup"><span data-stu-id="f922a-126">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="f922a-127">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="f922a-127">Exceptions</span></span>  
 <span data-ttu-id="f922a-128">Bu denetim deseninin ilişkili özel durumları yok.</span><span class="sxs-lookup"><span data-stu-id="f922a-128">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f922a-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f922a-129">See also</span></span>

- [<span data-ttu-id="f922a-130">UI Otomasyon Denetim Düzenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f922a-130">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="f922a-131">UI Otomasyon Sağlayıcısında Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="f922a-131">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="f922a-132">İstemciler İçin UI Otomasyon Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="f922a-132">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="f922a-133">UI Otomasyonunu Kullanarak Onay Kutusunun Değiştir Durumunu Alma</span><span class="sxs-lookup"><span data-stu-id="f922a-133">Get the Toggle State of a Check Box Using UI Automation</span></span>](get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [<span data-ttu-id="f922a-134">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f922a-134">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="f922a-135">UI Otomasyonda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="f922a-135">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
