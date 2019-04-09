---
title: EInitializeNewDomainFlags Numaralandırması
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 04b0d9989d66888c33de0359e4c93529fcfbf8d1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59095366"
---
# <a name="einitializenewdomainflags-enumeration"></a><span data-ttu-id="b3209-102">EInitializeNewDomainFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b3209-102">EInitializeNewDomainFlags Enumeration</span></span>
<span data-ttu-id="b3209-103">Çalışma zamanının bir uygulama etki alanının başlatma hakkında bilgi sağlamak konak sağlar.</span><span class="sxs-lookup"><span data-stu-id="b3209-103">Enables the host to provide the runtime with information about the initialization of an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3209-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b3209-104">Syntax</span></span>  
  
```  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="b3209-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="b3209-105">Members</span></span>  
  
|<span data-ttu-id="b3209-106">Üye</span><span class="sxs-lookup"><span data-stu-id="b3209-106">Member</span></span>|<span data-ttu-id="b3209-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b3209-107">Description</span></span>|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|<span data-ttu-id="b3209-108">Bayrak.</span><span class="sxs-lookup"><span data-stu-id="b3209-108">No flags.</span></span>|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|<span data-ttu-id="b3209-109">Konak güvenlik durumuna ilişkin uygulama etki alanında bir değişiklik değil, ortak dil çalışma zamanı (CLR) bildirir <xref:System.AppDomainManager.InitializeNewDomain%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b3209-109">Informs the common language runtime (CLR) that the host will not make changes to the security state of the application domain in the <xref:System.AppDomainManager.InitializeNewDomain%2A> method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3209-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b3209-110">Remarks</span></span>  
 <span data-ttu-id="b3209-111">[Iclrdomainmanager::setappdomainmanagertype](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) yöntemi türünde bir parametre alır `EInitializeNewDomainFlags`.</span><span class="sxs-lookup"><span data-stu-id="b3209-111">The [ICLRDomainManager::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) method takes a parameter of type `EInitializeNewDomainFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3209-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b3209-112">Requirements</span></span>  
 <span data-ttu-id="b3209-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3209-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3209-114">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b3209-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b3209-115">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b3209-115">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="b3209-116">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="b3209-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b3209-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3209-117">See also</span></span>

- [<span data-ttu-id="b3209-118">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="b3209-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
- [<span data-ttu-id="b3209-119">SetAppDomainManagerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b3209-119">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)
