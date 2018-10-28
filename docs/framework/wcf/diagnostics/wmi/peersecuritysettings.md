---
title: PeerSecuritySettings
ms.date: 03/30/2017
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
ms.openlocfilehash: 92aca4c790607de91314aacf6414d0dfacea9a9f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50193168"
---
# <a name="peersecuritysettings"></a><span data-ttu-id="a8aa8-102">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="a8aa8-102">PeerSecuritySettings</span></span>
<span data-ttu-id="a8aa8-103">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="a8aa8-103">PeerSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8aa8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a8aa8-104">Syntax</span></span>  
  
```csharp
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="a8aa8-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a8aa8-105">Methods</span></span>  
 <span data-ttu-id="a8aa8-106">PeerSecuritySettings sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="a8aa8-106">The PeerSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a8aa8-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="a8aa8-107">Properties</span></span>  
 <span data-ttu-id="a8aa8-108">PeerSecuritySettings sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="a8aa8-108">The PeerSecuritySettings class has the following properties:</span></span>  
  
### <a name="mode"></a><span data-ttu-id="a8aa8-109">Mod</span><span class="sxs-lookup"><span data-stu-id="a8aa8-109">Mode</span></span>  
 <span data-ttu-id="a8aa8-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="a8aa8-110">Data type: string</span></span>  
  
 <span data-ttu-id="a8aa8-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="a8aa8-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a8aa8-112">İleti düzeyi olup olmadığını ve aktarım düzeyi güvenlik bağlama ile yapılandırılan bir uç nokta tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a8aa8-112">Whether message-level and transport-level security are used by an endpoint configured with the binding.</span></span>  
  
### <a name="transport"></a><span data-ttu-id="a8aa8-113">Taşıma</span><span class="sxs-lookup"><span data-stu-id="a8aa8-113">Transport</span></span>  
 <span data-ttu-id="a8aa8-114">Veri türü: PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="a8aa8-114">Data type: PeerTransportSecuritySettings</span></span>  
  
 <span data-ttu-id="a8aa8-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="a8aa8-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a8aa8-116">Taşıma güvenliği ayarları.</span><span class="sxs-lookup"><span data-stu-id="a8aa8-116">Transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8aa8-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a8aa8-117">Requirements</span></span>  
  
|<span data-ttu-id="a8aa8-118">MOF</span><span class="sxs-lookup"><span data-stu-id="a8aa8-118">MOF</span></span>|<span data-ttu-id="a8aa8-119">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="a8aa8-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a8aa8-120">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="a8aa8-120">Namespace</span></span>|<span data-ttu-id="a8aa8-121">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a8aa8-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a8aa8-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a8aa8-122">See Also</span></span>  
 <xref:System.ServiceModel.PeerSecuritySettings>
