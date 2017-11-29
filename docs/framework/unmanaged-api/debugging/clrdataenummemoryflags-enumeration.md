---
title: "CLRDataEnumMemoryFlags Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CLRDataEnumMemoryFlags
api_location: mscordbi.dll
api_type: COM
f1_keywords: CLRDataEnumMemoryFlags
helpviewer_keywords: CLRDataEnumMemoryFlags enumeration [.NET Framework debugging]
ms.assetid: e249f9fc-e24a-4506-903c-92781f6eab7c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6c88fe4e6bcbe4f2ec3f13c08450f7dea44ccdbf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="clrdataenummemoryflags-enumeration"></a><span data-ttu-id="33945-102">CLRDataEnumMemoryFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="33945-102">CLRDataEnumMemoryFlags Enumeration</span></span>
<span data-ttu-id="33945-103">Hangi bellek bölümlerinin yapılan bir çağrı gösterir [Iclrdataenummemoryregions::enummemoryregions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) yöntemi içermelidir.</span><span class="sxs-lookup"><span data-stu-id="33945-103">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33945-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="33945-104">Syntax</span></span>  
  
```  
typedef enum CLRDataEnumMemoryFlags {  
    CLRDATA_ENUM_MEM_DEFAULT  = 0x0,  
    CLRDATA_ENUM_MEM_MINI     = CLRDATA_ENUM_MEM_DEFAULT,  
    CLRDATA_ENUM_MEM_HEAP     = 0x1  
} CLRDataEnumMemoryFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="33945-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="33945-105">Members</span></span>  
  
|<span data-ttu-id="33945-106">Üye</span><span class="sxs-lookup"><span data-stu-id="33945-106">Member</span></span>|<span data-ttu-id="33945-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="33945-107">Description</span></span>|  
|------------|-----------------|  
|`CLRDATA_ENUM_MEM_DEFAULT`|<span data-ttu-id="33945-108">Bir mini döküm, diğer bir deyişle, bir seyrek bellek dökümü.</span><span class="sxs-lookup"><span data-stu-id="33945-108">A minidump, that is, a sparse memory dump.</span></span>|  
|`CLRDATA_ENUM_MEM_HEAP`|<span data-ttu-id="33945-109">Bir tam yığın dökümü.</span><span class="sxs-lookup"><span data-stu-id="33945-109">A full heap dump.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="33945-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="33945-110">Requirements</span></span>  
 <span data-ttu-id="33945-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33945-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33945-112">**Başlık:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="33945-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="33945-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="33945-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33945-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33945-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33945-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="33945-115">See Also</span></span>  
 [<span data-ttu-id="33945-116">Hata ayıklama numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="33945-116">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
