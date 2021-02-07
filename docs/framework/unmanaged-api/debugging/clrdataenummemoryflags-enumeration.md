---
description: 'Şu konuda daha fazla bilgi edinin: CLRDataEnumMemoryFlags sabit listesi'
title: CLRDataEnumMemoryFlags Numaralandırması
ms.date: 03/30/2017
api_name:
- CLRDataEnumMemoryFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLRDataEnumMemoryFlags
helpviewer_keywords:
- CLRDataEnumMemoryFlags enumeration [.NET Framework debugging]
ms.assetid: e249f9fc-e24a-4506-903c-92781f6eab7c
topic_type:
- apiref
ms.openlocfilehash: 3522649c59177de8295416ce260c374df605efb3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662253"
---
# <a name="clrdataenummemoryflags-enumeration"></a><span data-ttu-id="ada83-103">CLRDataEnumMemoryFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="ada83-103">CLRDataEnumMemoryFlags Enumeration</span></span>

<span data-ttu-id="ada83-104">Hangi bellek bölgelerinin [ıclrdataenummemoryregion:: EnumMemoryRegion](iclrdataenummemoryregions-enummemoryregions-method.md) yöntemine yönelik bir çağrı içermesi gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ada83-104">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ada83-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ada83-105">Syntax</span></span>  
  
```cpp  
typedef enum CLRDataEnumMemoryFlags {  
    CLRDATA_ENUM_MEM_DEFAULT  = 0x0,  
    CLRDATA_ENUM_MEM_MINI     = CLRDATA_ENUM_MEM_DEFAULT,  
    CLRDATA_ENUM_MEM_HEAP     = 0x1  
} CLRDataEnumMemoryFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="ada83-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="ada83-106">Members</span></span>  
  
|<span data-ttu-id="ada83-107">Üye</span><span class="sxs-lookup"><span data-stu-id="ada83-107">Member</span></span>|<span data-ttu-id="ada83-108">Description</span><span class="sxs-lookup"><span data-stu-id="ada83-108">Description</span></span>|  
|------------|-----------------|  
|`CLRDATA_ENUM_MEM_DEFAULT`|<span data-ttu-id="ada83-109">Bir mini döküm, diğer bir deyişle seyrek bellek dökümü.</span><span class="sxs-lookup"><span data-stu-id="ada83-109">A minidump, that is, a sparse memory dump.</span></span>|  
|`CLRDATA_ENUM_MEM_HEAP`|<span data-ttu-id="ada83-110">Tam bir yığın dökümü.</span><span class="sxs-lookup"><span data-stu-id="ada83-110">A full heap dump.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ada83-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ada83-111">Requirements</span></span>  

 <span data-ttu-id="ada83-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ada83-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ada83-113">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="ada83-113">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="ada83-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ada83-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ada83-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ada83-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ada83-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ada83-116">See also</span></span>

- [<span data-ttu-id="ada83-117">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="ada83-117">Debugging Enumerations</span></span>](debugging-enumerations.md)
