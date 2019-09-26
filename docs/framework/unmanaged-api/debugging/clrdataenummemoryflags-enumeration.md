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
ms.openlocfilehash: 67b85917be590bdba7ed3f10972ad39b731dbcdd
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274237"
---
# <a name="clrdataenummemoryflags-enumeration"></a><span data-ttu-id="bdf49-102">CLRDataEnumMemoryFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="bdf49-102">CLRDataEnumMemoryFlags Enumeration</span></span>
<span data-ttu-id="bdf49-103">Hangi bellek bölgelerinin [ıclrdataenummemoryregion:: EnumMemoryRegion](iclrdataenummemoryregions-enummemoryregions-method.md) yöntemine yönelik bir çağrı içermesi gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="bdf49-103">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdf49-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bdf49-104">Syntax</span></span>  
  
```cpp  
typedef enum CLRDataEnumMemoryFlags {  
    CLRDATA_ENUM_MEM_DEFAULT  = 0x0,  
    CLRDATA_ENUM_MEM_MINI     = CLRDATA_ENUM_MEM_DEFAULT,  
    CLRDATA_ENUM_MEM_HEAP     = 0x1  
} CLRDataEnumMemoryFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="bdf49-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="bdf49-105">Members</span></span>  
  
|<span data-ttu-id="bdf49-106">Üye</span><span class="sxs-lookup"><span data-stu-id="bdf49-106">Member</span></span>|<span data-ttu-id="bdf49-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bdf49-107">Description</span></span>|  
|------------|-----------------|  
|`CLRDATA_ENUM_MEM_DEFAULT`|<span data-ttu-id="bdf49-108">Bir mini döküm, diğer bir deyişle seyrek bellek dökümü.</span><span class="sxs-lookup"><span data-stu-id="bdf49-108">A minidump, that is, a sparse memory dump.</span></span>|  
|`CLRDATA_ENUM_MEM_HEAP`|<span data-ttu-id="bdf49-109">Tam bir yığın dökümü.</span><span class="sxs-lookup"><span data-stu-id="bdf49-109">A full heap dump.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bdf49-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bdf49-110">Requirements</span></span>  
 <span data-ttu-id="bdf49-111">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bdf49-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdf49-112">**Üst bilgi** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="bdf49-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="bdf49-113">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="bdf49-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bdf49-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdf49-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdf49-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bdf49-115">See also</span></span>

- [<span data-ttu-id="bdf49-116">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="bdf49-116">Debugging Enumerations</span></span>](debugging-enumerations.md)
