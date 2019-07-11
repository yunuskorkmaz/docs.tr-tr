---
title: ESymbolReadingPolicy Numaralandırması
ms.date: 03/30/2017
api_name:
- ESymbolReadingPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ESymbolReadingPolicy
helpviewer_keywords:
- ESymbolReadingPolicy enumeration [.NET Framework hosting]
ms.assetid: 4dc6c80d-b694-480b-a378-d5b18420ce17
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 45b6b8593331801dd237d0a730afbd5a6a714bbf
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774185"
---
# <a name="esymbolreadingpolicy-enumeration"></a><span data-ttu-id="211d0-102">ESymbolReadingPolicy Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="211d0-102">ESymbolReadingPolicy Enumeration</span></span>
<span data-ttu-id="211d0-103">Program veritabanı (PDB) dosyaları okumak için ilkeyi değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="211d0-103">Contains values that set the policy for reading program database (PDB) files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="211d0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="211d0-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eSymbolReadingNever,  
    eSymbolReadingAlways,  
    eSymbolReadingFullTrustOnly  
} ESymbolReadingPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="211d0-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="211d0-105">Members</span></span>  
  
|<span data-ttu-id="211d0-106">Üye</span><span class="sxs-lookup"><span data-stu-id="211d0-106">Member</span></span>|<span data-ttu-id="211d0-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="211d0-107">Description</span></span>|  
|------------|-----------------|  
|`eSymbolReadingAlways`|<span data-ttu-id="211d0-108">Hata ayıklayıcı her zaman PDB dosyaları okuyup belirtir.</span><span class="sxs-lookup"><span data-stu-id="211d0-108">Specifies that the debugger should always read PDB files.</span></span>|  
|`eSymbolReadingFullTrustOnly`|<span data-ttu-id="211d0-109">Hata ayıklayıcı tam güven derlemeleri ile ilişkili olan PDB dosyaları okuyup belirtir.</span><span class="sxs-lookup"><span data-stu-id="211d0-109">Specifies that the debugger should read only PDB files that are associated with full-trust assemblies.</span></span>|  
|`eSymbolReadingNever`|<span data-ttu-id="211d0-110">Hata ayıklayıcı, PDB dosyaları hiçbir zaman okuyup belirtir.</span><span class="sxs-lookup"><span data-stu-id="211d0-110">Specifies that the debugger should never read PDB files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="211d0-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="211d0-111">Remarks</span></span>  
 <span data-ttu-id="211d0-112">`ESymbolReadingPolicy` Numaralandırması ile kullanılan [Iclrdebugmanager::setsymbolreadingpolicy](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="211d0-112">The `ESymbolReadingPolicy` enumeration is used with the [ICLRDebugManager::SetSymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="211d0-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="211d0-113">Requirements</span></span>  
 <span data-ttu-id="211d0-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="211d0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="211d0-115">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="211d0-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="211d0-116">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="211d0-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="211d0-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="211d0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="211d0-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="211d0-118">See also</span></span>

- [<span data-ttu-id="211d0-119">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="211d0-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
