---
title: CorDebugGuidToTypeMapping Yapısı
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugGuidToTypeMapping
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugGuidToTypeMapping
helpviewer_keywords:
- CorDebugGuidToTypeMapping structure [.NET Framework debugging]
ms.assetid: 57dbccd9-b16d-4da3-ae25-7a2cf9adf679
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49290a37ca7ea101e3c8b458a5daa4995cb3beee
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54610051"
---
# <a name="cordebugguidtotypemapping-structure"></a><span data-ttu-id="b297a-102">CorDebugGuidToTypeMapping Yapısı</span><span class="sxs-lookup"><span data-stu-id="b297a-102">CorDebugGuidToTypeMapping Structure</span></span>
<span data-ttu-id="b297a-103">Eşlemeleri bir [!INCLUDE[wrt](../../../../includes/wrt-md.md)] karşılık gelen Icordebugtype nesne için GUID.</span><span class="sxs-lookup"><span data-stu-id="b297a-103">Maps a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID to its corresponding ICorDebugType object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b297a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b297a-104">Syntax</span></span>  
  
```cpp
typedef struct CorDebugGuidToTypeMapping {  
    GUID iid;  
    ICorDebugType *pType;  
} CorDebugGuidToTypeMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="b297a-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="b297a-105">Members</span></span>  
  
|<span data-ttu-id="b297a-106">Üye</span><span class="sxs-lookup"><span data-stu-id="b297a-106">Member</span></span>|<span data-ttu-id="b297a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b297a-107">Description</span></span>|  
|------------|-----------------|  
|`iid`|<span data-ttu-id="b297a-108">Önbelleğe alınan GUID [!INCLUDE[wrt](../../../../includes/wrt-md.md)] türü.</span><span class="sxs-lookup"><span data-stu-id="b297a-108">The GUID of the cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] type.</span></span>|  
|`pType`|<span data-ttu-id="b297a-109">Önbelleğe alınan türü hakkında bilgi sağlayan Icordebugtype nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="b297a-109">A pointer to an ICorDebugType object that provides information about the cached type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b297a-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b297a-110">Requirements</span></span>  
 <span data-ttu-id="b297a-111">**Platformlar:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b297a-111">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)].</span></span>  
  
 <span data-ttu-id="b297a-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b297a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b297a-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b297a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b297a-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b297a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b297a-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b297a-115">See also</span></span>
- [<span data-ttu-id="b297a-116">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="b297a-116">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="b297a-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="b297a-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
