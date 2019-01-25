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
ms.openlocfilehash: e17f88cf7f0d8572e65d00d8500a1fd83aa44eeb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54663920"
---
# <a name="esymbolreadingpolicy-enumeration"></a><span data-ttu-id="7c1e9-102">ESymbolReadingPolicy Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7c1e9-102">ESymbolReadingPolicy Enumeration</span></span>
<span data-ttu-id="7c1e9-103">Program veritabanı (PDB) dosyaları okumak için ilkeyi değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="7c1e9-103">Contains values that set the policy for reading program database (PDB) files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c1e9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7c1e9-104">Syntax</span></span>  
  
```  
typedef enum {  
    eSymbolReadingNever,  
    eSymbolReadingAlways,  
    eSymbolReadingFullTrustOnly  
} ESymbolReadingPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="7c1e9-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="7c1e9-105">Members</span></span>  
  
|<span data-ttu-id="7c1e9-106">Üye</span><span class="sxs-lookup"><span data-stu-id="7c1e9-106">Member</span></span>|<span data-ttu-id="7c1e9-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7c1e9-107">Description</span></span>|  
|------------|-----------------|  
|`eSymbolReadingAlways`|<span data-ttu-id="7c1e9-108">Hata ayıklayıcı her zaman PDB dosyaları okuyup belirtir.</span><span class="sxs-lookup"><span data-stu-id="7c1e9-108">Specifies that the debugger should always read PDB files.</span></span>|  
|`eSymbolReadingFullTrustOnly`|<span data-ttu-id="7c1e9-109">Hata ayıklayıcı tam güven derlemeleri ile ilişkili olan PDB dosyaları okuyup belirtir.</span><span class="sxs-lookup"><span data-stu-id="7c1e9-109">Specifies that the debugger should read only PDB files that are associated with full-trust assemblies.</span></span>|  
|`eSymbolReadingNever`|<span data-ttu-id="7c1e9-110">Hata ayıklayıcı, PDB dosyaları hiçbir zaman okuyup belirtir.</span><span class="sxs-lookup"><span data-stu-id="7c1e9-110">Specifies that the debugger should never read PDB files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c1e9-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7c1e9-111">Remarks</span></span>  
 <span data-ttu-id="7c1e9-112">`ESymbolReadingPolicy` Numaralandırması ile kullanılan [Iclrdebugmanager::setsymbolreadingpolicy](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7c1e9-112">The `ESymbolReadingPolicy` enumeration is used with the [ICLRDebugManager::SetSymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c1e9-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7c1e9-113">Requirements</span></span>  
 <span data-ttu-id="7c1e9-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c1e9-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c1e9-115">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7c1e9-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7c1e9-116">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7c1e9-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7c1e9-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c1e9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c1e9-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7c1e9-118">See also</span></span>
- [<span data-ttu-id="7c1e9-119">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="7c1e9-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
