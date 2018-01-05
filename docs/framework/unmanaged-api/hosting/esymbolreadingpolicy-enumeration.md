---
title: "ESymbolReadingPolicy Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ESymbolReadingPolicy
api_location: mscoree.dll
api_type: COM
f1_keywords: ESymbolReadingPolicy
helpviewer_keywords: ESymbolReadingPolicy enumeration [.NET Framework hosting]
ms.assetid: 4dc6c80d-b694-480b-a378-d5b18420ce17
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4fdb18a343f91e85619f6d62e466fdd558044727
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="esymbolreadingpolicy-enumeration"></a><span data-ttu-id="7ada8-102">ESymbolReadingPolicy Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7ada8-102">ESymbolReadingPolicy Enumeration</span></span>
<span data-ttu-id="7ada8-103">Program veritabanı (PDB) dosyaları okumak için ilke ayarlama değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="7ada8-103">Contains values that set the policy for reading program database (PDB) files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ada8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7ada8-104">Syntax</span></span>  
  
```  
typedef enum {  
    eSymbolReadingNever,  
    eSymbolReadingAlways,  
    eSymbolReadingFullTrustOnly  
} ESymbolReadingPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="7ada8-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="7ada8-105">Members</span></span>  
  
|<span data-ttu-id="7ada8-106">Üye</span><span class="sxs-lookup"><span data-stu-id="7ada8-106">Member</span></span>|<span data-ttu-id="7ada8-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7ada8-107">Description</span></span>|  
|------------|-----------------|  
|`eSymbolReadingAlways`|<span data-ttu-id="7ada8-108">Hata ayıklayıcı PDB dosyaları her zaman okumalısınız belirtir.</span><span class="sxs-lookup"><span data-stu-id="7ada8-108">Specifies that the debugger should always read PDB files.</span></span>|  
|`eSymbolReadingFullTrustOnly`|<span data-ttu-id="7ada8-109">Hata ayıklayıcı tam güven derlemeler ile ilişkilendirilmiş PDB dosyalarını okumalısınız belirtir.</span><span class="sxs-lookup"><span data-stu-id="7ada8-109">Specifies that the debugger should read only PDB files that are associated with full-trust assemblies.</span></span>|  
|`eSymbolReadingNever`|<span data-ttu-id="7ada8-110">Hata ayıklayıcı PDB dosyalarını hiçbir zaman okumalısınız belirtir.</span><span class="sxs-lookup"><span data-stu-id="7ada8-110">Specifies that the debugger should never read PDB files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ada8-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7ada8-111">Remarks</span></span>  
 <span data-ttu-id="7ada8-112">`ESymbolReadingPolicy` Numaralandırması ile kullanılır [Iclrdebugmanager::setsymbolreadingpolicy](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7ada8-112">The `ESymbolReadingPolicy` enumeration is used with the [ICLRDebugManager::SetSymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ada8-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7ada8-113">Requirements</span></span>  
 <span data-ttu-id="7ada8-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ada8-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ada8-115">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7ada8-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7ada8-116">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7ada8-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7ada8-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ada8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ada8-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7ada8-118">See Also</span></span>  
 [<span data-ttu-id="7ada8-119">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="7ada8-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
