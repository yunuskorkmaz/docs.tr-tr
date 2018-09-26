---
title: PeerSecuritySettings
ms.date: 03/30/2017
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
author: BrucePerlerMS
ms.openlocfilehash: c74ee82d7aa3a23f0ee6a69185ad45857c31bb0b
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47087885"
---
# <a name="peersecuritysettings"></a><span data-ttu-id="9d319-102">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="9d319-102">PeerSecuritySettings</span></span>
<span data-ttu-id="9d319-103">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="9d319-103">PeerSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d319-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9d319-104">Syntax</span></span>  
  
```  
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="9d319-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9d319-105">Methods</span></span>  
 <span data-ttu-id="9d319-106">PeerSecuritySettings sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="9d319-106">The PeerSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="9d319-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="9d319-107">Properties</span></span>  
 <span data-ttu-id="9d319-108">PeerSecuritySettings sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="9d319-108">The PeerSecuritySettings class has the following properties:</span></span>  
  
### <a name="mode"></a><span data-ttu-id="9d319-109">Mod</span><span class="sxs-lookup"><span data-stu-id="9d319-109">Mode</span></span>  
 <span data-ttu-id="9d319-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="9d319-110">Data type: string</span></span>  
  
 <span data-ttu-id="9d319-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9d319-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9d319-112">İleti düzeyi olup olmadığını ve aktarım düzeyi güvenlik bağlama ile yapılandırılan bir uç nokta tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9d319-112">Whether message-level and transport-level security are used by an endpoint configured with the binding.</span></span>  
  
### <a name="transport"></a><span data-ttu-id="9d319-113">Taşıma</span><span class="sxs-lookup"><span data-stu-id="9d319-113">Transport</span></span>  
 <span data-ttu-id="9d319-114">Veri türü: PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="9d319-114">Data type: PeerTransportSecuritySettings</span></span>  
  
 <span data-ttu-id="9d319-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9d319-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9d319-116">Taşıma güvenliği ayarları.</span><span class="sxs-lookup"><span data-stu-id="9d319-116">Transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d319-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9d319-117">Requirements</span></span>  
  
|<span data-ttu-id="9d319-118">MOF</span><span class="sxs-lookup"><span data-stu-id="9d319-118">MOF</span></span>|<span data-ttu-id="9d319-119">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="9d319-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="9d319-120">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="9d319-120">Namespace</span></span>|<span data-ttu-id="9d319-121">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="9d319-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9d319-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9d319-122">See Also</span></span>  
 <xref:System.ServiceModel.PeerSecuritySettings>
