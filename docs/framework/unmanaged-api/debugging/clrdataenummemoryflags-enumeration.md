---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a19c6f22ee9fbe7eb1019a0b799d63e4ee650e98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406825"
---
# <a name="clrdataenummemoryflags-enumeration"></a><span data-ttu-id="d4560-102">CLRDataEnumMemoryFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="d4560-102">CLRDataEnumMemoryFlags Enumeration</span></span>
<span data-ttu-id="d4560-103">Hangi bellek bölümlerinin yapılan bir çağrı gösterir [Iclrdataenummemoryregions::enummemoryregions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) yöntemi içermelidir.</span><span class="sxs-lookup"><span data-stu-id="d4560-103">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4560-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d4560-104">Syntax</span></span>  
  
```  
typedef enum CLRDataEnumMemoryFlags {  
    CLRDATA_ENUM_MEM_DEFAULT  = 0x0,  
    CLRDATA_ENUM_MEM_MINI     = CLRDATA_ENUM_MEM_DEFAULT,  
    CLRDATA_ENUM_MEM_HEAP     = 0x1  
} CLRDataEnumMemoryFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="d4560-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="d4560-105">Members</span></span>  
  
|<span data-ttu-id="d4560-106">Üye</span><span class="sxs-lookup"><span data-stu-id="d4560-106">Member</span></span>|<span data-ttu-id="d4560-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d4560-107">Description</span></span>|  
|------------|-----------------|  
|`CLRDATA_ENUM_MEM_DEFAULT`|<span data-ttu-id="d4560-108">Bir mini döküm, diğer bir deyişle, bir seyrek bellek dökümü.</span><span class="sxs-lookup"><span data-stu-id="d4560-108">A minidump, that is, a sparse memory dump.</span></span>|  
|`CLRDATA_ENUM_MEM_HEAP`|<span data-ttu-id="d4560-109">Bir tam yığın dökümü.</span><span class="sxs-lookup"><span data-stu-id="d4560-109">A full heap dump.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d4560-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d4560-110">Requirements</span></span>  
 <span data-ttu-id="d4560-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4560-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4560-112">**Başlık:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="d4560-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="d4560-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d4560-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4560-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4560-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4560-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d4560-115">See Also</span></span>  
 [<span data-ttu-id="d4560-116">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="d4560-116">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
