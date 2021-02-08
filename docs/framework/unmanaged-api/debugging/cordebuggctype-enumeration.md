---
description: 'Daha fazla bilgi edinin: Cortcggctype numaralandırması'
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
ms.openlocfilehash: 4be835a9a028a882fa050991beb31d2a8dec5354
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801663"
---
# <a name="cordebuggctype-enumeration"></a><span data-ttu-id="c628b-103">CorDebugGCType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="c628b-103">CorDebugGCType Enumeration</span></span>

<span data-ttu-id="c628b-104">Çöp toplayıcının bir iş istasyonunda veya sunucuda çalışıp çalışmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c628b-104">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c628b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c628b-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugGCType {  
    CorDebugWorkstationGC  = 0,  
    CorDebugServerGC       = ( CorDebugWorkstationGC + 1 )  
} CorDebugGCType;  
```  
  
## <a name="parameters"></a><span data-ttu-id="c628b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c628b-106">Parameters</span></span>  
  
## <a name="members"></a><span data-ttu-id="c628b-107">Üyeler</span><span class="sxs-lookup"><span data-stu-id="c628b-107">Members</span></span>  
  
|<span data-ttu-id="c628b-108">Üye adı</span><span class="sxs-lookup"><span data-stu-id="c628b-108">Member name</span></span>|<span data-ttu-id="c628b-109">Description</span><span class="sxs-lookup"><span data-stu-id="c628b-109">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebugWorkstationGC`|<span data-ttu-id="c628b-110">Çöp toplayıcı bir iş istasyonunda çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="c628b-110">The garbage collector is running on a workstation.</span></span>|  
|`CorDebugServerGC`|<span data-ttu-id="c628b-111">Çöp toplayıcı bir sunucuda çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="c628b-111">The garbage collector is running on a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c628b-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c628b-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c628b-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c628b-113">Requirements</span></span>  

 <span data-ttu-id="c628b-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c628b-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c628b-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c628b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c628b-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c628b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c628b-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c628b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c628b-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c628b-118">See also</span></span>

- [<span data-ttu-id="c628b-119">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="c628b-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
