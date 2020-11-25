---
title: CorDebugGCType Sabit Listesi
ms.date: 03/30/2017
api_name:
- CorDebugGCType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugGCType
helpviewer_keywords:
- CorDebugGCType enumeration [.NET Framework debugging]
ms.assetid: 880ca92a-42d4-42a5-9b9c-c2848eb39c6a
topic_type:
- apiref
ms.openlocfilehash: 6b3075613af0403527ecf67d574c0f5733a5cd8b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712618"
---
# <a name="cordebuggctype-enumeration"></a><span data-ttu-id="59604-102">CorDebugGCType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="59604-102">CorDebugGCType Enumeration</span></span>

<span data-ttu-id="59604-103">Çöp toplayıcının bir iş istasyonunda veya sunucuda çalışıp çalışmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="59604-103">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59604-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="59604-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugGCType {  
    CorDebugWorkstationGC  = 0,  
    CorDebugServerGC       = ( CorDebugWorkstationGC + 1 )  
} CorDebugGCType;  
```  
  
## <a name="parameters"></a><span data-ttu-id="59604-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="59604-105">Parameters</span></span>  
  
## <a name="members"></a><span data-ttu-id="59604-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="59604-106">Members</span></span>  
  
|<span data-ttu-id="59604-107">Üye adı</span><span class="sxs-lookup"><span data-stu-id="59604-107">Member name</span></span>|<span data-ttu-id="59604-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="59604-108">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebugWorkstationGC`|<span data-ttu-id="59604-109">Çöp toplayıcı bir iş istasyonunda çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="59604-109">The garbage collector is running on a workstation.</span></span>|  
|`CorDebugServerGC`|<span data-ttu-id="59604-110">Çöp toplayıcı bir sunucuda çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="59604-110">The garbage collector is running on a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59604-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="59604-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59604-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="59604-112">Requirements</span></span>  

 <span data-ttu-id="59604-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59604-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59604-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="59604-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="59604-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="59604-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59604-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59604-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59604-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="59604-117">See also</span></span>

- [<span data-ttu-id="59604-118">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="59604-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
