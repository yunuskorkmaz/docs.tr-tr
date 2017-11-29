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
ms.openlocfilehash: ce56486453e88a18ebd9dbb42f30bcfdafcf328e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="esymbolreadingpolicy-enumeration"></a><span data-ttu-id="75ecb-102">ESymbolReadingPolicy Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="75ecb-102">ESymbolReadingPolicy Enumeration</span></span>
<span data-ttu-id="75ecb-103">Program veritabanı (PDB) dosyaları okumak için ilke ayarlama değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="75ecb-103">Contains values that set the policy for reading program database (PDB) files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75ecb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="75ecb-104">Syntax</span></span>  
  
```  
typedef enum {  
    eSymbolReadingNever,  
    eSymbolReadingAlways,  
    eSymbolReadingFullTrustOnly  
} ESymbolReadingPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="75ecb-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="75ecb-105">Members</span></span>  
  
|<span data-ttu-id="75ecb-106">Üye</span><span class="sxs-lookup"><span data-stu-id="75ecb-106">Member</span></span>|<span data-ttu-id="75ecb-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="75ecb-107">Description</span></span>|  
|------------|-----------------|  
|`eSymbolReadingAlways`|<span data-ttu-id="75ecb-108">Hata ayıklayıcı PDB dosyaları her zaman okumalısınız belirtir.</span><span class="sxs-lookup"><span data-stu-id="75ecb-108">Specifies that the debugger should always read PDB files.</span></span>|  
|`eSymbolReadingFullTrustOnly`|<span data-ttu-id="75ecb-109">Hata ayıklayıcı tam güven derlemeler ile ilişkilendirilmiş PDB dosyalarını okumalısınız belirtir.</span><span class="sxs-lookup"><span data-stu-id="75ecb-109">Specifies that the debugger should read only PDB files that are associated with full-trust assemblies.</span></span>|  
|`eSymbolReadingNever`|<span data-ttu-id="75ecb-110">Hata ayıklayıcı PDB dosyalarını hiçbir zaman okumalısınız belirtir.</span><span class="sxs-lookup"><span data-stu-id="75ecb-110">Specifies that the debugger should never read PDB files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75ecb-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="75ecb-111">Remarks</span></span>  
 <span data-ttu-id="75ecb-112">`ESymbolReadingPolicy` Numaralandırması ile kullanılır [Iclrdebugmanager::setsymbolreadingpolicy](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="75ecb-112">The `ESymbolReadingPolicy` enumeration is used with the [ICLRDebugManager::SetSymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75ecb-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="75ecb-113">Requirements</span></span>  
 <span data-ttu-id="75ecb-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75ecb-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75ecb-115">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="75ecb-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="75ecb-116">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="75ecb-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="75ecb-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75ecb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75ecb-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="75ecb-118">See Also</span></span>  
 [<span data-ttu-id="75ecb-119">Barındırma numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="75ecb-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
