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
ms.openlocfilehash: 8350b507609e63c060cda08514200d386c37a6b3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724331"
---
# <a name="einitializenewdomainflags-enumeration"></a><span data-ttu-id="96524-102">EInitializeNewDomainFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="96524-102">EInitializeNewDomainFlags Enumeration</span></span>

<span data-ttu-id="96524-103">Bir uygulama etki alanının başlatılması hakkında bilgi içeren konağın çalışma zamanına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="96524-103">Enables the host to provide the runtime with information about the initialization of an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96524-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="96524-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="96524-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="96524-105">Members</span></span>  
  
|<span data-ttu-id="96524-106">Üye</span><span class="sxs-lookup"><span data-stu-id="96524-106">Member</span></span>|<span data-ttu-id="96524-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="96524-107">Description</span></span>|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|<span data-ttu-id="96524-108">Bayrak yok.</span><span class="sxs-lookup"><span data-stu-id="96524-108">No flags.</span></span>|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|<span data-ttu-id="96524-109">Ortak dil çalışma zamanına (CLR), ana bilgisayarın yöntemdeki uygulama etki alanının güvenlik durumunda değişiklik yapmayacağı konusunda bilgilendirir <xref:System.AppDomainManager.InitializeNewDomain%2A> .</span><span class="sxs-lookup"><span data-stu-id="96524-109">Informs the common language runtime (CLR) that the host will not make changes to the security state of the application domain in the <xref:System.AppDomainManager.InitializeNewDomain%2A> method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96524-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="96524-110">Remarks</span></span>  

 <span data-ttu-id="96524-111">[ICLRDomainManager:: SetAppDomainManagerType](iclrdomainmanager-setappdomainmanagertype-method.md) yöntemi türünde bir parametre alır `EInitializeNewDomainFlags` .</span><span class="sxs-lookup"><span data-stu-id="96524-111">The [ICLRDomainManager::SetAppDomainManagerType](iclrdomainmanager-setappdomainmanagertype-method.md) method takes a parameter of type `EInitializeNewDomainFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96524-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="96524-112">Requirements</span></span>  

 <span data-ttu-id="96524-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96524-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96524-114">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="96524-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="96524-115">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="96524-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="96524-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96524-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96524-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96524-117">See also</span></span>

- [<span data-ttu-id="96524-118">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="96524-118">Hosting Enumerations</span></span>](hosting-enumerations.md)
- [<span data-ttu-id="96524-119">SetAppDomainManagerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="96524-119">SetAppDomainManagerType Method</span></span>](iclrdomainmanager-setappdomainmanagertype-method.md)
