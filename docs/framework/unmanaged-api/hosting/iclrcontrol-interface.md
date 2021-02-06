---
description: ': ICLRControl arabirimi hakkında daha fazla bilgi'
title: ICLRControl Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl
helpviewer_keywords:
- ICLRControl interface [.NET Framework hosting]
ms.assetid: a24fd905-1fa6-45a0-ad65-e9e2ee58861e
topic_type:
- apiref
ms.openlocfilehash: e108506d06b746d631f4c15c37d467399de30aba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637670"
---
# <a name="iclrcontrol-interface"></a><span data-ttu-id="82a35-103">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="82a35-103">ICLRControl Interface</span></span>

<span data-ttu-id="82a35-104">, Bir konağın ortak dil çalışma zamanı (CLR) için başvuruları almasını ve yönlerini yapılandırmasına izin veren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="82a35-104">Provides methods that allow a host to get references to, and configure aspects of, the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="82a35-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="82a35-105">Methods</span></span>  
  
|<span data-ttu-id="82a35-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="82a35-106">Method</span></span>|<span data-ttu-id="82a35-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="82a35-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="82a35-108">GetCLRManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="82a35-108">GetCLRManager Method</span></span>](iclrcontrol-getclrmanager-method.md)|<span data-ttu-id="82a35-109">Konağın CLR 'yi yapılandırmak için kullanabileceği bir yönetici türü örneğine yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="82a35-109">Gets an interface pointer to an instance of any of the manager types the host can use to configure the CLR.</span></span>|  
|[<span data-ttu-id="82a35-110">SetAppDomainManagerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="82a35-110">SetAppDomainManagerType Method</span></span>](iclrcontrol-setappdomainmanagertype-method.md)|<span data-ttu-id="82a35-111"><xref:System.AppDomainManager>Uygulama etki alanı yöneticileri için tür olarak türetilmiş bir tür belirler.</span><span class="sxs-lookup"><span data-stu-id="82a35-111">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="82a35-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="82a35-112">Requirements</span></span>  

 <span data-ttu-id="82a35-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82a35-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82a35-114">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="82a35-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="82a35-115">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="82a35-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="82a35-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82a35-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82a35-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82a35-117">See also</span></span>

- [<span data-ttu-id="82a35-118">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="82a35-118">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="82a35-119">ICLRDebugManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="82a35-119">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="82a35-120">ICLRGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="82a35-120">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)
- [<span data-ttu-id="82a35-121">ICLRHostBindingPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="82a35-121">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)
- [<span data-ttu-id="82a35-122">ICLRHostProtectionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="82a35-122">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="82a35-123">ICLROnEventManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="82a35-123">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
- [<span data-ttu-id="82a35-124">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="82a35-124">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="82a35-125">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="82a35-125">IHostControl Interface</span></span>](ihostcontrol-interface.md)
- [<span data-ttu-id="82a35-126">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="82a35-126">Hosting Interfaces</span></span>](hosting-interfaces.md)
