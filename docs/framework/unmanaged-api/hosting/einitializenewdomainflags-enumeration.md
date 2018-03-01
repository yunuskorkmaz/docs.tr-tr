---
title: "EInitializeNewDomainFlags Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- EInitializeNewDomainFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EInitializeNewDomainFlags
helpviewer_keywords:
- EInitializeNewDomainFlags enumeration [.NET Framework hosting]
ms.assetid: 3a120ab2-f5ef-4c9b-8595-d3ed7247c342
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fa5c9aa050e0f5e634c43080d9caa5011a126529
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="einitializenewdomainflags-enumeration"></a><span data-ttu-id="d77fa-102">EInitializeNewDomainFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="d77fa-102">EInitializeNewDomainFlags Enumeration</span></span>
<span data-ttu-id="d77fa-103">Çalışma zamanı uygulama etki alanı başlatma hakkında bilgi sağlamak ana bilgisayarı sağlar.</span><span class="sxs-lookup"><span data-stu-id="d77fa-103">Enables the host to provide the runtime with information about the initialization of an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d77fa-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d77fa-104">Syntax</span></span>  
  
```  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="d77fa-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="d77fa-105">Members</span></span>  
  
|<span data-ttu-id="d77fa-106">Üye</span><span class="sxs-lookup"><span data-stu-id="d77fa-106">Member</span></span>|<span data-ttu-id="d77fa-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d77fa-107">Description</span></span>|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|<span data-ttu-id="d77fa-108">Hiçbir bayraklar.</span><span class="sxs-lookup"><span data-stu-id="d77fa-108">No flags.</span></span>|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|<span data-ttu-id="d77fa-109">Ortak dil çalışma zamanı (CLR) ana uygulama etki alanı güvenlik durumunu bir değişiklik değil olduğunu bildiren <xref:System.AppDomainManager.InitializeNewDomain%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d77fa-109">Informs the common language runtime (CLR) that the host will not make changes to the security state of the application domain in the <xref:System.AppDomainManager.InitializeNewDomain%2A> method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d77fa-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d77fa-110">Remarks</span></span>  
 <span data-ttu-id="d77fa-111">[Iclrdomainmanager::setappdomainmanagertype](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) yöntemi türünde bir parametre alan `EInitializeNewDomainFlags`.</span><span class="sxs-lookup"><span data-stu-id="d77fa-111">The [ICLRDomainManager::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) method takes a parameter of type `EInitializeNewDomainFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d77fa-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d77fa-112">Requirements</span></span>  
 <span data-ttu-id="d77fa-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d77fa-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d77fa-114">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d77fa-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d77fa-115">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d77fa-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d77fa-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d77fa-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d77fa-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d77fa-117">See Also</span></span>  
 [<span data-ttu-id="d77fa-118">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="d77fa-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
 [<span data-ttu-id="d77fa-119">SetAppDomainManagerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d77fa-119">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)
