---
title: PeerSecuritySettings
ms.date: 03/30/2017
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 58b372f26fee7dc180d75731fd4855db569c87c7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33484527"
---
# <a name="peersecuritysettings"></a><span data-ttu-id="d324c-102">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="d324c-102">PeerSecuritySettings</span></span>
<span data-ttu-id="d324c-103">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="d324c-103">PeerSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d324c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d324c-104">Syntax</span></span>  
  
```  
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="d324c-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d324c-105">Methods</span></span>  
 <span data-ttu-id="d324c-106">PeerSecuritySettings sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="d324c-106">The PeerSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d324c-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d324c-107">Properties</span></span>  
 <span data-ttu-id="d324c-108">PeerSecuritySettings sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="d324c-108">The PeerSecuritySettings class has the following properties:</span></span>  
  
### <a name="mode"></a><span data-ttu-id="d324c-109">Mod</span><span class="sxs-lookup"><span data-stu-id="d324c-109">Mode</span></span>  
 <span data-ttu-id="d324c-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="d324c-110">Data type: string</span></span>  
  
 <span data-ttu-id="d324c-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d324c-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d324c-112">İleti düzeyi olup olmadığını ve aktarım düzeyinde güvenlik bağlama ile yapılandırılan bir uç nokta tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d324c-112">Whether message-level and transport-level security are used by an endpoint configured with the binding.</span></span>  
  
### <a name="transport"></a><span data-ttu-id="d324c-113">Taşıma</span><span class="sxs-lookup"><span data-stu-id="d324c-113">Transport</span></span>  
 <span data-ttu-id="d324c-114">Veri türü: PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="d324c-114">Data type: PeerTransportSecuritySettings</span></span>  
  
 <span data-ttu-id="d324c-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d324c-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d324c-116">Taşıma güvenliği ayarları.</span><span class="sxs-lookup"><span data-stu-id="d324c-116">Transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d324c-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d324c-117">Requirements</span></span>  
  
|<span data-ttu-id="d324c-118">MOF</span><span class="sxs-lookup"><span data-stu-id="d324c-118">MOF</span></span>|<span data-ttu-id="d324c-119">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="d324c-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d324c-120">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="d324c-120">Namespace</span></span>|<span data-ttu-id="d324c-121">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d324c-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d324c-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d324c-122">See Also</span></span>  
 <xref:System.ServiceModel.PeerSecuritySettings>
