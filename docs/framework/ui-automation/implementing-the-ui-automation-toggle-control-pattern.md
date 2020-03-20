---
title: UI Otomasyonu Değiştirme Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- Toggle control pattern
- control patterns, Toggle
- UI Automation, Toggle control pattern
ms.assetid: 3cfe875f-b0c0-413d-9703-5f14e6a1a30e
ms.openlocfilehash: 5f64842d31d46af3d648b9b570d1cfb210e2910a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180058"
---
# <a name="implementing-the-ui-automation-toggle-control-pattern"></a><span data-ttu-id="9d121-102">UI Otomasyonu Değiştirme Denetim Düzenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="9d121-102">Implementing the UI Automation Toggle Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="9d121-103">Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="9d121-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="9d121-104">Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="9d121-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="9d121-105">Bu <xref:System.Windows.Automation.Provider.IToggleProvider>konu, yöntemler ve özellikler hakkında bilgi de dahil olmak üzere, uygulama yönergeleri ve kuralları tanıtır.</span><span class="sxs-lookup"><span data-stu-id="9d121-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>, including information about methods and properties.</span></span> <span data-ttu-id="9d121-106">Ek başvurulara bağlantılar konunun sonunda listelenir.</span><span class="sxs-lookup"><span data-stu-id="9d121-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="9d121-107">Denetim <xref:System.Windows.Automation.TogglePattern> deseni, bir dizi durum arasında geçiş yapabilecek ve bir kez ayarlanan durumu koruyabilen denetimleri desteklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9d121-107">The <xref:System.Windows.Automation.TogglePattern> control pattern is used to support controls that can cycle through a set of states and maintain a state once set.</span></span> <span data-ttu-id="9d121-108">Bu denetim deseni uygulayan denetim örnekleri için, [UI Otomasyon Istemcileri için Denetim Deseni Eşleciliği'ne](control-pattern-mapping-for-ui-automation-clients.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="9d121-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="9d121-109">Uygulama Yönergeleri ve Sözleşmeleri</span><span class="sxs-lookup"><span data-stu-id="9d121-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="9d121-110">Geçiş denetimi deseni uygularken aşağıdaki yönergeleri ve kuralları not edin:</span><span class="sxs-lookup"><span data-stu-id="9d121-110">When implementing the Toggle control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="9d121-111">Düğmeler, araç çubuğu düğmeleri ve köprüler gibi etkinleştirildiğinde durum tutmayan <xref:System.Windows.Automation.Provider.IInvokeProvider> denetimler bunun yerine uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9d121-111">Controls that do not maintain state when activated, such as buttons, toolbar buttons, and hyperlinks, must implement <xref:System.Windows.Automation.Provider.IInvokeProvider> instead.</span></span>  
  
- <span data-ttu-id="9d121-112">Bir <xref:System.Windows.Automation.ToggleState> denetim, aşağıdaki sırayla üzerinden <xref:System.Windows.Automation.ToggleState.On> <xref:System.Windows.Automation.ToggleState.Off> döngü gerekir: , <xref:System.Windows.Automation.ToggleState.Indeterminate>ve, eğer desteklenirse, .</span><span class="sxs-lookup"><span data-stu-id="9d121-112">A control must cycle through its <xref:System.Windows.Automation.ToggleState> in the following order: <xref:System.Windows.Automation.ToggleState.On>, <xref:System.Windows.Automation.ToggleState.Off> and, if supported, <xref:System.Windows.Automation.ToggleState.Indeterminate>.</span></span>  
  
- <span data-ttu-id="9d121-113"><xref:System.Windows.Automation.TogglePattern>uygun <xref:System.Windows.Automation.ToggleState> sırası ile bisiklet olmadan üç devletli CheckBox doğrudan ayarı çevreleyen sorunlar nedeniyle bir SetState (newState) yöntemi sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="9d121-113"><xref:System.Windows.Automation.TogglePattern> does not provide a SetState(newState) method due to issues surrounding the direct setting of a tri-state CheckBox without cycling through its appropriate <xref:System.Windows.Automation.ToggleState> sequence.</span></span>  
  
- <span data-ttu-id="9d121-114">RadioButton denetimi, geçerli <xref:System.Windows.Automation.Provider.IToggleProvider>durumları arasında bisiklete binme yeteneğine sahip olmadığı için uygulamaz.</span><span class="sxs-lookup"><span data-stu-id="9d121-114">The RadioButton control does not implement <xref:System.Windows.Automation.Provider.IToggleProvider>, as it is not capable of cycling through its valid states.</span></span>  
  
<a name="Required_Members_for_IToggleProvider"></a>
## <a name="required-members-for-itoggleprovider"></a><span data-ttu-id="9d121-115">IToggleProvider için Gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="9d121-115">Required Members for IToggleProvider</span></span>  
 <span data-ttu-id="9d121-116">Uygulamak için aşağıdaki özellikler ve <xref:System.Windows.Automation.Provider.IToggleProvider>yöntemler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9d121-116">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>.</span></span>  
  
|<span data-ttu-id="9d121-117">Gerekli üye</span><span class="sxs-lookup"><span data-stu-id="9d121-117">Required member</span></span>|<span data-ttu-id="9d121-118">Üye tipi</span><span class="sxs-lookup"><span data-stu-id="9d121-118">Member type</span></span>|<span data-ttu-id="9d121-119">Notlar</span><span class="sxs-lookup"><span data-stu-id="9d121-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.TogglePattern.Toggle%2A>|<span data-ttu-id="9d121-120">Yöntem</span><span class="sxs-lookup"><span data-stu-id="9d121-120">Method</span></span>|<span data-ttu-id="9d121-121">None</span><span class="sxs-lookup"><span data-stu-id="9d121-121">None</span></span>|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>|<span data-ttu-id="9d121-122">Özellik</span><span class="sxs-lookup"><span data-stu-id="9d121-122">Property</span></span>|<span data-ttu-id="9d121-123">None</span><span class="sxs-lookup"><span data-stu-id="9d121-123">None</span></span>|  
  
 <span data-ttu-id="9d121-124">Bu denetim deseni ilişkili olaylar vardır.</span><span class="sxs-lookup"><span data-stu-id="9d121-124">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="9d121-125">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="9d121-125">Exceptions</span></span>  
 <span data-ttu-id="9d121-126">Bu denetim deseni ilişkili özel durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="9d121-126">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d121-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d121-127">See also</span></span>

- [<span data-ttu-id="9d121-128">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9d121-128">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="9d121-129">UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="9d121-129">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="9d121-130">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="9d121-130">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="9d121-131">UI Otomasyonunu Kullanarak Onay Kutusunun Değiştir Durumunu Alma</span><span class="sxs-lookup"><span data-stu-id="9d121-131">Get the Toggle State of a Check Box Using UI Automation</span></span>](get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [<span data-ttu-id="9d121-132">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9d121-132">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="9d121-133">UI Otomasyonunda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="9d121-133">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
