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
ms.openlocfilehash: 3693285e13d0650f7662e2187471027cc4c40704
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129416"
---
# <a name="einitializenewdomainflags-enumeration"></a><span data-ttu-id="2259f-102">EInitializeNewDomainFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="2259f-102">EInitializeNewDomainFlags Enumeration</span></span>
<span data-ttu-id="2259f-103">Bir uygulama etki alanının başlatılması hakkında bilgi içeren konağın çalışma zamanına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="2259f-103">Enables the host to provide the runtime with information about the initialization of an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2259f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2259f-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="2259f-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="2259f-105">Members</span></span>  
  
|<span data-ttu-id="2259f-106">Üye</span><span class="sxs-lookup"><span data-stu-id="2259f-106">Member</span></span>|<span data-ttu-id="2259f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2259f-107">Description</span></span>|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|<span data-ttu-id="2259f-108">Bayrak yok.</span><span class="sxs-lookup"><span data-stu-id="2259f-108">No flags.</span></span>|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|<span data-ttu-id="2259f-109">Ana bilgisayarın <xref:System.AppDomainManager.InitializeNewDomain%2A> yönteminde uygulama etki alanının güvenlik durumunda değişiklik yapmayacağı ortak dil çalışma zamanına (CLR) bildirir.</span><span class="sxs-lookup"><span data-stu-id="2259f-109">Informs the common language runtime (CLR) that the host will not make changes to the security state of the application domain in the <xref:System.AppDomainManager.InitializeNewDomain%2A> method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2259f-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2259f-110">Remarks</span></span>  
 <span data-ttu-id="2259f-111">[ICLRDomainManager:: SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) yöntemi, `EInitializeNewDomainFlags`türünde bir parametre alır.</span><span class="sxs-lookup"><span data-stu-id="2259f-111">The [ICLRDomainManager::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) method takes a parameter of type `EInitializeNewDomainFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2259f-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2259f-112">Requirements</span></span>  
 <span data-ttu-id="2259f-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2259f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2259f-114">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2259f-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2259f-115">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2259f-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2259f-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2259f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2259f-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2259f-117">See also</span></span>

- [<span data-ttu-id="2259f-118">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="2259f-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
- [<span data-ttu-id="2259f-119">SetAppDomainManagerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2259f-119">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)
