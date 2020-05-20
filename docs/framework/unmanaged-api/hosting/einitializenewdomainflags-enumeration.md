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
ms.openlocfilehash: 7ff10f84d8d270d31c5d560fb3c9bd3c81cf3e24
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616235"
---
# <a name="einitializenewdomainflags-enumeration"></a><span data-ttu-id="db9e2-102">EInitializeNewDomainFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="db9e2-102">EInitializeNewDomainFlags Enumeration</span></span>
<span data-ttu-id="db9e2-103">Bir uygulama etki alanının başlatılması hakkında bilgi içeren konağın çalışma zamanına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="db9e2-103">Enables the host to provide the runtime with information about the initialization of an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db9e2-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="db9e2-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="db9e2-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="db9e2-105">Members</span></span>  
  
|<span data-ttu-id="db9e2-106">Üye</span><span class="sxs-lookup"><span data-stu-id="db9e2-106">Member</span></span>|<span data-ttu-id="db9e2-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="db9e2-107">Description</span></span>|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|<span data-ttu-id="db9e2-108">Bayrak yok.</span><span class="sxs-lookup"><span data-stu-id="db9e2-108">No flags.</span></span>|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|<span data-ttu-id="db9e2-109">Ortak dil çalışma zamanına (CLR), ana bilgisayarın yöntemdeki uygulama etki alanının güvenlik durumunda değişiklik yapmayacağı konusunda bilgilendirir <xref:System.AppDomainManager.InitializeNewDomain%2A> .</span><span class="sxs-lookup"><span data-stu-id="db9e2-109">Informs the common language runtime (CLR) that the host will not make changes to the security state of the application domain in the <xref:System.AppDomainManager.InitializeNewDomain%2A> method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db9e2-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="db9e2-110">Remarks</span></span>  
 <span data-ttu-id="db9e2-111">[ICLRDomainManager:: SetAppDomainManagerType](iclrdomainmanager-setappdomainmanagertype-method.md) yöntemi türünde bir parametre alır `EInitializeNewDomainFlags` .</span><span class="sxs-lookup"><span data-stu-id="db9e2-111">The [ICLRDomainManager::SetAppDomainManagerType](iclrdomainmanager-setappdomainmanagertype-method.md) method takes a parameter of type `EInitializeNewDomainFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db9e2-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="db9e2-112">Requirements</span></span>  
 <span data-ttu-id="db9e2-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db9e2-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db9e2-114">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="db9e2-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="db9e2-115">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="db9e2-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="db9e2-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db9e2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db9e2-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db9e2-117">See also</span></span>

- [<span data-ttu-id="db9e2-118">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="db9e2-118">Hosting Enumerations</span></span>](hosting-enumerations.md)
- [<span data-ttu-id="db9e2-119">SetAppDomainManagerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="db9e2-119">SetAppDomainManagerType Method</span></span>](iclrdomainmanager-setappdomainmanagertype-method.md)
