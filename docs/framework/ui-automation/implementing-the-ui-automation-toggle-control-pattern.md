---
title: UI Otomasyonu Değiştirme Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- Toggle control pattern
- control patterns, Toggle
- UI Automation, Toggle control pattern
ms.assetid: 3cfe875f-b0c0-413d-9703-5f14e6a1a30e
ms.openlocfilehash: c25f2d3b73e90adb3299ff8c4ff7c8a77fc5fc5e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447066"
---
# <a name="implementing-the-ui-automation-toggle-control-pattern"></a><span data-ttu-id="b64c1-102">UI Otomasyonu Değiştirme Denetim Düzenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="b64c1-102">Implementing the UI Automation Toggle Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="b64c1-103">Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="b64c1-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="b64c1-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="b64c1-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="b64c1-105">Bu konu, Yöntemler ve özellikler hakkında bilgiler de dahil olmak üzere <xref:System.Windows.Automation.Provider.IToggleProvider>uygulamak için kılavuz ve kuralları tanıtır.</span><span class="sxs-lookup"><span data-stu-id="b64c1-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>, including information about methods and properties.</span></span> <span data-ttu-id="b64c1-106">Ek başvuruların bağlantıları konunun sonunda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="b64c1-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="b64c1-107"><xref:System.Windows.Automation.TogglePattern> denetim stili, bir durum kümesinde geçiş yapan ve bir kez ayarlandıktan sonra bir durumu korumak için kullanılan denetimleri desteklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b64c1-107">The <xref:System.Windows.Automation.TogglePattern> control pattern is used to support controls that can cycle through a set of states and maintain a state once set.</span></span> <span data-ttu-id="b64c1-108">Bu denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="b64c1-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="b64c1-109">Uygulama kılavuzları ve kuralları</span><span class="sxs-lookup"><span data-stu-id="b64c1-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="b64c1-110">Iki durumlu denetim modelini uygularken aşağıdaki kılavuz ve kurallara göz önünde</span><span class="sxs-lookup"><span data-stu-id="b64c1-110">When implementing the Toggle control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="b64c1-111">Düğme, araç çubuğu düğmeleri ve köprüler gibi etkinleştirildiğinde durumu korumayan denetimler, bunun yerine <xref:System.Windows.Automation.Provider.IInvokeProvider> gerçekleştirmelidir.</span><span class="sxs-lookup"><span data-stu-id="b64c1-111">Controls that do not maintain state when activated, such as buttons, toolbar buttons, and hyperlinks, must implement <xref:System.Windows.Automation.Provider.IInvokeProvider> instead.</span></span>  
  
- <span data-ttu-id="b64c1-112">Bir denetim, <xref:System.Windows.Automation.ToggleState> şu sırada bir şekilde çalışmalıdır: <xref:System.Windows.Automation.ToggleState.On>, <xref:System.Windows.Automation.ToggleState.Off> ve destekleniyorsa, <xref:System.Windows.Automation.ToggleState.Indeterminate>.</span><span class="sxs-lookup"><span data-stu-id="b64c1-112">A control must cycle through its <xref:System.Windows.Automation.ToggleState> in the following order: <xref:System.Windows.Automation.ToggleState.On>, <xref:System.Windows.Automation.ToggleState.Off> and, if supported, <xref:System.Windows.Automation.ToggleState.Indeterminate>.</span></span>  
  
- <span data-ttu-id="b64c1-113"><xref:System.Windows.Automation.TogglePattern>, Üçlü durum onay kutusunun doğrudan ayarını çevreleyen sorunlar nedeniyle uygun <xref:System.Windows.Automation.ToggleState> sırası boyunca geçiş yapılmadan bir SetState (newState) yöntemi sağlamıyor.</span><span class="sxs-lookup"><span data-stu-id="b64c1-113"><xref:System.Windows.Automation.TogglePattern> does not provide a SetState(newState) method due to issues surrounding the direct setting of a tri-state CheckBox without cycling through its appropriate <xref:System.Windows.Automation.ToggleState> sequence.</span></span>  
  
- <span data-ttu-id="b64c1-114">RadioButton denetimi geçerli durumları arasında geçiş yapamayacağı için <xref:System.Windows.Automation.Provider.IToggleProvider>uygulamaz.</span><span class="sxs-lookup"><span data-stu-id="b64c1-114">The RadioButton control does not implement <xref:System.Windows.Automation.Provider.IToggleProvider>, as it is not capable of cycling through its valid states.</span></span>  
  
<a name="Required_Members_for_IToggleProvider"></a>   
## <a name="required-members-for-itoggleprovider"></a><span data-ttu-id="b64c1-115">IToggleProvider için gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="b64c1-115">Required Members for IToggleProvider</span></span>  
 <span data-ttu-id="b64c1-116"><xref:System.Windows.Automation.Provider.IToggleProvider>uygulamak için aşağıdaki özellikler ve Yöntemler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b64c1-116">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>.</span></span>  
  
|<span data-ttu-id="b64c1-117">Gerekli üye</span><span class="sxs-lookup"><span data-stu-id="b64c1-117">Required member</span></span>|<span data-ttu-id="b64c1-118">Üye türü</span><span class="sxs-lookup"><span data-stu-id="b64c1-118">Member type</span></span>|<span data-ttu-id="b64c1-119">Notlar</span><span class="sxs-lookup"><span data-stu-id="b64c1-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.TogglePattern.Toggle%2A>|<span data-ttu-id="b64c1-120">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b64c1-120">Method</span></span>|<span data-ttu-id="b64c1-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="b64c1-121">None</span></span>|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>|<span data-ttu-id="b64c1-122">Özellik</span><span class="sxs-lookup"><span data-stu-id="b64c1-122">Property</span></span>|<span data-ttu-id="b64c1-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="b64c1-123">None</span></span>|  
  
 <span data-ttu-id="b64c1-124">Bu denetim deseninin ilişkili olayları yok.</span><span class="sxs-lookup"><span data-stu-id="b64c1-124">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="b64c1-125">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="b64c1-125">Exceptions</span></span>  
 <span data-ttu-id="b64c1-126">Bu denetim deseninin ilişkili özel durumları yok.</span><span class="sxs-lookup"><span data-stu-id="b64c1-126">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b64c1-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b64c1-127">See also</span></span>

- [<span data-ttu-id="b64c1-128">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b64c1-128">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="b64c1-129">UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="b64c1-129">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="b64c1-130">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="b64c1-130">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="b64c1-131">UI Otomasyonunu Kullanarak Onay Kutusunun Değiştir Durumunu Alma</span><span class="sxs-lookup"><span data-stu-id="b64c1-131">Get the Toggle State of a Check Box Using UI Automation</span></span>](get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [<span data-ttu-id="b64c1-132">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b64c1-132">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="b64c1-133">UI Otomasyonunda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="b64c1-133">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
