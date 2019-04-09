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
ms.openlocfilehash: 9dc7093edaf12e801a1e1adc52b0be823ff92b91
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079922"
---
# <a name="cordebugguidtotypemapping-structure"></a><span data-ttu-id="9ff88-102">CorDebugGuidToTypeMapping Yapısı</span><span class="sxs-lookup"><span data-stu-id="9ff88-102">CorDebugGuidToTypeMapping Structure</span></span>
<span data-ttu-id="9ff88-103">Eşlemeleri bir [!INCLUDE[wrt](../../../../includes/wrt-md.md)] karşılık gelen Icordebugtype nesne için GUID.</span><span class="sxs-lookup"><span data-stu-id="9ff88-103">Maps a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID to its corresponding ICorDebugType object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ff88-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9ff88-104">Syntax</span></span>  
  
```cpp
typedef struct CorDebugGuidToTypeMapping {  
    GUID iid;  
    ICorDebugType *pType;  
} CorDebugGuidToTypeMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="9ff88-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="9ff88-105">Members</span></span>  
  
|<span data-ttu-id="9ff88-106">Üye</span><span class="sxs-lookup"><span data-stu-id="9ff88-106">Member</span></span>|<span data-ttu-id="9ff88-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9ff88-107">Description</span></span>|  
|------------|-----------------|  
|`iid`|<span data-ttu-id="9ff88-108">Önbelleğe alınan GUID [!INCLUDE[wrt](../../../../includes/wrt-md.md)] türü.</span><span class="sxs-lookup"><span data-stu-id="9ff88-108">The GUID of the cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] type.</span></span>|  
|`pType`|<span data-ttu-id="9ff88-109">Önbelleğe alınan türü hakkında bilgi sağlayan Icordebugtype nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="9ff88-109">A pointer to an ICorDebugType object that provides information about the cached type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9ff88-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9ff88-110">Requirements</span></span>  
 <span data-ttu-id="9ff88-111">**Platformlar:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9ff88-111">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)].</span></span>  
  
 <span data-ttu-id="9ff88-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9ff88-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9ff88-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ff88-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="9ff88-114">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="9ff88-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9ff88-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ff88-115">See also</span></span>

- [<span data-ttu-id="9ff88-116">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="9ff88-116">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="9ff88-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="9ff88-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
