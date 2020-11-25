---
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
ms.openlocfilehash: acf449014f5bf5683d5488f8ed2ead963676fe6b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728348"
---
# <a name="iclrcontrol-interface"></a><span data-ttu-id="c26da-102">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c26da-102">ICLRControl Interface</span></span>

<span data-ttu-id="c26da-103">, Bir konağın ortak dil çalışma zamanı (CLR) için başvuruları almasını ve yönlerini yapılandırmasına izin veren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c26da-103">Provides methods that allow a host to get references to, and configure aspects of, the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c26da-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c26da-104">Methods</span></span>  
  
|<span data-ttu-id="c26da-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c26da-105">Method</span></span>|<span data-ttu-id="c26da-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c26da-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c26da-107">GetCLRManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c26da-107">GetCLRManager Method</span></span>](iclrcontrol-getclrmanager-method.md)|<span data-ttu-id="c26da-108">Konağın CLR 'yi yapılandırmak için kullanabileceği bir yönetici türü örneğine yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="c26da-108">Gets an interface pointer to an instance of any of the manager types the host can use to configure the CLR.</span></span>|  
|[<span data-ttu-id="c26da-109">SetAppDomainManagerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c26da-109">SetAppDomainManagerType Method</span></span>](iclrcontrol-setappdomainmanagertype-method.md)|<span data-ttu-id="c26da-110"><xref:System.AppDomainManager>Uygulama etki alanı yöneticileri için tür olarak türetilmiş bir tür belirler.</span><span class="sxs-lookup"><span data-stu-id="c26da-110">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c26da-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c26da-111">Requirements</span></span>  

 <span data-ttu-id="c26da-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c26da-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c26da-113">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c26da-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c26da-114">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="c26da-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c26da-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c26da-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c26da-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c26da-116">See also</span></span>

- [<span data-ttu-id="c26da-117">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c26da-117">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="c26da-118">ICLRDebugManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c26da-118">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="c26da-119">ICLRGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c26da-119">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)
- [<span data-ttu-id="c26da-120">ICLRHostBindingPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c26da-120">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)
- [<span data-ttu-id="c26da-121">ICLRHostProtectionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c26da-121">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="c26da-122">ICLROnEventManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c26da-122">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
- [<span data-ttu-id="c26da-123">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c26da-123">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="c26da-124">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c26da-124">IHostControl Interface</span></span>](ihostcontrol-interface.md)
- [<span data-ttu-id="c26da-125">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c26da-125">Hosting Interfaces</span></span>](hosting-interfaces.md)
