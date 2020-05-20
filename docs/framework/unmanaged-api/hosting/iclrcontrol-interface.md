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
ms.openlocfilehash: 54748fdeaf911591c21f4495335e54c777878f04
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615845"
---
# <a name="iclrcontrol-interface"></a><span data-ttu-id="9d51b-102">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d51b-102">ICLRControl Interface</span></span>
<span data-ttu-id="9d51b-103">, Bir konağın ortak dil çalışma zamanı (CLR) için başvuruları almasını ve yönlerini yapılandırmasına izin veren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9d51b-103">Provides methods that allow a host to get references to, and configure aspects of, the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9d51b-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9d51b-104">Methods</span></span>  
  
|<span data-ttu-id="9d51b-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="9d51b-105">Method</span></span>|<span data-ttu-id="9d51b-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9d51b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9d51b-107">GetCLRManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9d51b-107">GetCLRManager Method</span></span>](iclrcontrol-getclrmanager-method.md)|<span data-ttu-id="9d51b-108">Konağın CLR 'yi yapılandırmak için kullanabileceği bir yönetici türü örneğine yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="9d51b-108">Gets an interface pointer to an instance of any of the manager types the host can use to configure the CLR.</span></span>|  
|[<span data-ttu-id="9d51b-109">SetAppDomainManagerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9d51b-109">SetAppDomainManagerType Method</span></span>](iclrcontrol-setappdomainmanagertype-method.md)|<span data-ttu-id="9d51b-110"><xref:System.AppDomainManager>Uygulama etki alanı yöneticileri için tür olarak türetilmiş bir tür belirler.</span><span class="sxs-lookup"><span data-stu-id="9d51b-110">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9d51b-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9d51b-111">Requirements</span></span>  
 <span data-ttu-id="9d51b-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d51b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d51b-113">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9d51b-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9d51b-114">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="9d51b-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9d51b-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d51b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d51b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d51b-116">See also</span></span>

- [<span data-ttu-id="9d51b-117">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d51b-117">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="9d51b-118">ICLRDebugManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d51b-118">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="9d51b-119">ICLRGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d51b-119">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)
- [<span data-ttu-id="9d51b-120">ICLRHostBindingPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d51b-120">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)
- [<span data-ttu-id="9d51b-121">ICLRHostProtectionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d51b-121">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="9d51b-122">ICLROnEventManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d51b-122">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
- [<span data-ttu-id="9d51b-123">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d51b-123">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="9d51b-124">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d51b-124">IHostControl Interface</span></span>](ihostcontrol-interface.md)
- [<span data-ttu-id="9d51b-125">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9d51b-125">Hosting Interfaces</span></span>](hosting-interfaces.md)
