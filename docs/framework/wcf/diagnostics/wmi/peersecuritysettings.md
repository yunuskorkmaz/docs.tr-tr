---
title: PeerSecuritySettings
ms.date: 03/30/2017
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
ms.openlocfilehash: 2de417e4a4f5c6197551c1408da6907e2fa7c635
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96269008"
---
# <a name="peersecuritysettings"></a><span data-ttu-id="d3a2a-102">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="d3a2a-102">PeerSecuritySettings</span></span>

<span data-ttu-id="d3a2a-103">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="d3a2a-103">PeerSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3a2a-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="d3a2a-104">Syntax</span></span>  
  
```csharp
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="d3a2a-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d3a2a-105">Methods</span></span>  

 <span data-ttu-id="d3a2a-106">PeerSecuritySettings sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="d3a2a-106">The PeerSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d3a2a-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d3a2a-107">Properties</span></span>  

 <span data-ttu-id="d3a2a-108">PeerSecuritySettings sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="d3a2a-108">The PeerSecuritySettings class has the following properties:</span></span>  
  
### <a name="mode"></a><span data-ttu-id="d3a2a-109">Mod</span><span class="sxs-lookup"><span data-stu-id="d3a2a-109">Mode</span></span>  

 <span data-ttu-id="d3a2a-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="d3a2a-110">Data type: string</span></span>  
  
 <span data-ttu-id="d3a2a-111">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="d3a2a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d3a2a-112">Bağlama ile yapılandırılan bir uç nokta tarafından ileti düzeyi ve aktarım düzeyi güvenlik kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d3a2a-112">Whether message-level and transport-level security are used by an endpoint configured with the binding.</span></span>  
  
### <a name="transport"></a><span data-ttu-id="d3a2a-113">Aktarım</span><span class="sxs-lookup"><span data-stu-id="d3a2a-113">Transport</span></span>  

 <span data-ttu-id="d3a2a-114">Veri türü: PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="d3a2a-114">Data type: PeerTransportSecuritySettings</span></span>  
  
 <span data-ttu-id="d3a2a-115">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="d3a2a-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d3a2a-116">Taşıma güvenlik ayarları.</span><span class="sxs-lookup"><span data-stu-id="d3a2a-116">Transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3a2a-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d3a2a-117">Requirements</span></span>  
  
|<span data-ttu-id="d3a2a-118">MOF</span><span class="sxs-lookup"><span data-stu-id="d3a2a-118">MOF</span></span>|<span data-ttu-id="d3a2a-119">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d3a2a-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d3a2a-120">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="d3a2a-120">Namespace</span></span>|<span data-ttu-id="d3a2a-121">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="d3a2a-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d3a2a-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3a2a-122">See also</span></span>

- <xref:System.ServiceModel.PeerSecuritySettings>
