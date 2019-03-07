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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fe8be6a7c18fff54825f981672f0f640bb60c35c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57482216"
---
# <a name="cordebuggctype-enumeration"></a><span data-ttu-id="2801c-102">CorDebugGCType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="2801c-102">CorDebugGCType Enumeration</span></span>
<span data-ttu-id="2801c-103">Atık toplayıcı bir iş istasyonunda veya sunucuda çalışıp çalışmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2801c-103">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2801c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2801c-104">Syntax</span></span>  
  
```  
typedef enum CorDebugGCType {  
    CorDebugWorkstationGC  = 0,  
    CorDebugServerGC       = ( CorDebugWorkstationGC + 1 )  
} CorDebugGCType;  
```  
  
## <a name="parameters"></a><span data-ttu-id="2801c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2801c-105">Parameters</span></span>  
  
## <a name="members"></a><span data-ttu-id="2801c-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="2801c-106">Members</span></span>  
  
|<span data-ttu-id="2801c-107">Üye adı</span><span class="sxs-lookup"><span data-stu-id="2801c-107">Member name</span></span>|<span data-ttu-id="2801c-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2801c-108">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebugWorkstationGC`|<span data-ttu-id="2801c-109">Çöp toplayıcı, bir iş istasyonunda çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="2801c-109">The garbage collector is running on a workstation.</span></span>|  
|`CorDebugServerGC`|<span data-ttu-id="2801c-110">Çöp toplayıcı, bir sunucu üzerinde çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="2801c-110">The garbage collector is running on a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2801c-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2801c-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2801c-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2801c-112">Requirements</span></span>  
 <span data-ttu-id="2801c-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2801c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2801c-114">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2801c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2801c-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2801c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2801c-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2801c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2801c-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2801c-117">See also</span></span>
- [<span data-ttu-id="2801c-118">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="2801c-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
