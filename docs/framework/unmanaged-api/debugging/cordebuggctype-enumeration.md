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
ms.openlocfilehash: 8dd070d2c895a94ac996be81e672bd67f59b83b7
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795904"
---
# <a name="cordebuggctype-enumeration"></a><span data-ttu-id="a3090-102">CorDebugGCType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="a3090-102">CorDebugGCType Enumeration</span></span>
<span data-ttu-id="a3090-103">Çöp toplayıcının bir iş istasyonunda veya sunucuda çalışıp çalışmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a3090-103">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3090-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a3090-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugGCType {  
    CorDebugWorkstationGC  = 0,  
    CorDebugServerGC       = ( CorDebugWorkstationGC + 1 )  
} CorDebugGCType;  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3090-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a3090-105">Parameters</span></span>  
  
## <a name="members"></a><span data-ttu-id="a3090-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="a3090-106">Members</span></span>  
  
|<span data-ttu-id="a3090-107">Üye adı</span><span class="sxs-lookup"><span data-stu-id="a3090-107">Member name</span></span>|<span data-ttu-id="a3090-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a3090-108">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebugWorkstationGC`|<span data-ttu-id="a3090-109">Çöp toplayıcı bir iş istasyonunda çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="a3090-109">The garbage collector is running on a workstation.</span></span>|  
|`CorDebugServerGC`|<span data-ttu-id="a3090-110">Çöp toplayıcı bir sunucuda çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="a3090-110">The garbage collector is running on a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3090-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a3090-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3090-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a3090-112">Requirements</span></span>  
 <span data-ttu-id="a3090-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3090-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3090-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a3090-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a3090-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a3090-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3090-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3090-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3090-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a3090-117">See also</span></span>

- [<span data-ttu-id="a3090-118">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="a3090-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
