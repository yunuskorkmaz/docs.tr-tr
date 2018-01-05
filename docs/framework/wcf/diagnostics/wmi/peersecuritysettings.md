---
title: PeerSecuritySettings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 48a9cc5a7a05b47a5589d1bf9a730184fb7f0543
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="peersecuritysettings"></a><span data-ttu-id="62ed4-102">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="62ed4-102">PeerSecuritySettings</span></span>
<span data-ttu-id="62ed4-103">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="62ed4-103">PeerSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62ed4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="62ed4-104">Syntax</span></span>  
  
```  
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="62ed4-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="62ed4-105">Methods</span></span>  
 <span data-ttu-id="62ed4-106">PeerSecuritySettings sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="62ed4-106">The PeerSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="62ed4-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="62ed4-107">Properties</span></span>  
 <span data-ttu-id="62ed4-108">PeerSecuritySettings sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="62ed4-108">The PeerSecuritySettings class has the following properties:</span></span>  
  
### <a name="mode"></a><span data-ttu-id="62ed4-109">Mod</span><span class="sxs-lookup"><span data-stu-id="62ed4-109">Mode</span></span>  
 <span data-ttu-id="62ed4-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="62ed4-110">Data type: string</span></span>  
  
 <span data-ttu-id="62ed4-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="62ed4-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="62ed4-112">İleti düzeyi olup olmadığını ve aktarım düzeyinde güvenlik bağlama ile yapılandırılan bir uç nokta tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="62ed4-112">Whether message-level and transport-level security are used by an endpoint configured with the binding.</span></span>  
  
### <a name="transport"></a><span data-ttu-id="62ed4-113">Taşıma</span><span class="sxs-lookup"><span data-stu-id="62ed4-113">Transport</span></span>  
 <span data-ttu-id="62ed4-114">Veri türü: PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="62ed4-114">Data type: PeerTransportSecuritySettings</span></span>  
  
 <span data-ttu-id="62ed4-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="62ed4-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="62ed4-116">Taşıma güvenliği ayarları.</span><span class="sxs-lookup"><span data-stu-id="62ed4-116">Transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62ed4-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="62ed4-117">Requirements</span></span>  
  
|<span data-ttu-id="62ed4-118">MOF</span><span class="sxs-lookup"><span data-stu-id="62ed4-118">MOF</span></span>|<span data-ttu-id="62ed4-119">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="62ed4-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="62ed4-120">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="62ed4-120">Namespace</span></span>|<span data-ttu-id="62ed4-121">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="62ed4-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="62ed4-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="62ed4-122">See Also</span></span>  
 <xref:System.ServiceModel.PeerSecuritySettings>
