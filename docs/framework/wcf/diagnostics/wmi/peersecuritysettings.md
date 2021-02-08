---
description: 'Daha fazla bilgi edinin: PeerSecuritySettings'
title: PeerSecuritySettings
ms.date: 03/30/2017
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
ms.openlocfilehash: a8b5b8c88e71cb46110fa35186599c0f9c366d17
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803015"
---
# <a name="peersecuritysettings"></a><span data-ttu-id="748fe-103">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="748fe-103">PeerSecuritySettings</span></span>

<span data-ttu-id="748fe-104">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="748fe-104">PeerSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="748fe-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="748fe-105">Syntax</span></span>  
  
```csharp
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="748fe-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="748fe-106">Methods</span></span>  

 <span data-ttu-id="748fe-107">PeerSecuritySettings sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="748fe-107">The PeerSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="748fe-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="748fe-108">Properties</span></span>  

 <span data-ttu-id="748fe-109">PeerSecuritySettings sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="748fe-109">The PeerSecuritySettings class has the following properties:</span></span>  
  
### <a name="mode"></a><span data-ttu-id="748fe-110">Mod</span><span class="sxs-lookup"><span data-stu-id="748fe-110">Mode</span></span>  

 <span data-ttu-id="748fe-111">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="748fe-111">Data type: string</span></span>  
  
 <span data-ttu-id="748fe-112">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="748fe-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="748fe-113">Bağlama ile yapılandırılan bir uç nokta tarafından ileti düzeyi ve aktarım düzeyi güvenlik kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="748fe-113">Whether message-level and transport-level security are used by an endpoint configured with the binding.</span></span>  
  
### <a name="transport"></a><span data-ttu-id="748fe-114">Aktarım</span><span class="sxs-lookup"><span data-stu-id="748fe-114">Transport</span></span>  

 <span data-ttu-id="748fe-115">Veri türü: PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="748fe-115">Data type: PeerTransportSecuritySettings</span></span>  
  
 <span data-ttu-id="748fe-116">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="748fe-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="748fe-117">Taşıma güvenlik ayarları.</span><span class="sxs-lookup"><span data-stu-id="748fe-117">Transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="748fe-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="748fe-118">Requirements</span></span>  
  
|<span data-ttu-id="748fe-119">MOF</span><span class="sxs-lookup"><span data-stu-id="748fe-119">MOF</span></span>|<span data-ttu-id="748fe-120">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="748fe-120">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="748fe-121">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="748fe-121">Namespace</span></span>|<span data-ttu-id="748fe-122">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="748fe-122">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="748fe-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="748fe-123">See also</span></span>

- <xref:System.ServiceModel.PeerSecuritySettings>
