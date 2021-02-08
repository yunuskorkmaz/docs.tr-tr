---
description: 'Şu konuda daha fazla bilgi edinin: EInitializeNewDomainFlags numaralandırması'
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
ms.openlocfilehash: b856d061e86c0c79b35f842975378307b79a37e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785471"
---
# <a name="einitializenewdomainflags-enumeration"></a><span data-ttu-id="f8972-103">EInitializeNewDomainFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="f8972-103">EInitializeNewDomainFlags Enumeration</span></span>

<span data-ttu-id="f8972-104">Bir uygulama etki alanının başlatılması hakkında bilgi içeren konağın çalışma zamanına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f8972-104">Enables the host to provide the runtime with information about the initialization of an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8972-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f8972-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="f8972-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="f8972-106">Members</span></span>  
  
|<span data-ttu-id="f8972-107">Üye</span><span class="sxs-lookup"><span data-stu-id="f8972-107">Member</span></span>|<span data-ttu-id="f8972-108">Description</span><span class="sxs-lookup"><span data-stu-id="f8972-108">Description</span></span>|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|<span data-ttu-id="f8972-109">Bayrak yok.</span><span class="sxs-lookup"><span data-stu-id="f8972-109">No flags.</span></span>|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|<span data-ttu-id="f8972-110">Ortak dil çalışma zamanına (CLR), ana bilgisayarın yöntemdeki uygulama etki alanının güvenlik durumunda değişiklik yapmayacağı konusunda bilgilendirir <xref:System.AppDomainManager.InitializeNewDomain%2A> .</span><span class="sxs-lookup"><span data-stu-id="f8972-110">Informs the common language runtime (CLR) that the host will not make changes to the security state of the application domain in the <xref:System.AppDomainManager.InitializeNewDomain%2A> method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8972-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f8972-111">Remarks</span></span>  

 <span data-ttu-id="f8972-112">[ICLRDomainManager:: SetAppDomainManagerType](iclrdomainmanager-setappdomainmanagertype-method.md) yöntemi türünde bir parametre alır `EInitializeNewDomainFlags` .</span><span class="sxs-lookup"><span data-stu-id="f8972-112">The [ICLRDomainManager::SetAppDomainManagerType](iclrdomainmanager-setappdomainmanagertype-method.md) method takes a parameter of type `EInitializeNewDomainFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8972-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f8972-113">Requirements</span></span>  

 <span data-ttu-id="f8972-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8972-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8972-115">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f8972-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f8972-116">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f8972-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f8972-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8972-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8972-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f8972-118">See also</span></span>

- [<span data-ttu-id="f8972-119">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="f8972-119">Hosting Enumerations</span></span>](hosting-enumerations.md)
- [<span data-ttu-id="f8972-120">SetAppDomainManagerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f8972-120">SetAppDomainManagerType Method</span></span>](iclrdomainmanager-setappdomainmanagertype-method.md)
