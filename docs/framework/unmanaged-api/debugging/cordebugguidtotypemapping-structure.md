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
ms.openlocfilehash: c803a805da605bd52fd50eb1e292c0e277143d7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405265"
---
# <a name="cordebugguidtotypemapping-structure"></a><span data-ttu-id="3f47b-102">CorDebugGuidToTypeMapping Yapısı</span><span class="sxs-lookup"><span data-stu-id="3f47b-102">CorDebugGuidToTypeMapping Structure</span></span>
<span data-ttu-id="3f47b-103">MAPS bir [!INCLUDE[wrt](../../../../includes/wrt-md.md)] karşılık gelen Icordebugtype nesne için GUID.</span><span class="sxs-lookup"><span data-stu-id="3f47b-103">Maps a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID to its corresponding ICorDebugType object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f47b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3f47b-104">Syntax</span></span>  
  
```cpp
typedef struct CorDebugGuidToTypeMapping {  
    GUID iid;  
    ICorDebugType *pType;  
} CorDebugGuidToTypeMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="3f47b-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="3f47b-105">Members</span></span>  
  
|<span data-ttu-id="3f47b-106">Üye</span><span class="sxs-lookup"><span data-stu-id="3f47b-106">Member</span></span>|<span data-ttu-id="3f47b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3f47b-107">Description</span></span>|  
|------------|-----------------|  
|`iid`|<span data-ttu-id="3f47b-108">Önbelleğe alınan GUID'i [!INCLUDE[wrt](../../../../includes/wrt-md.md)] türü.</span><span class="sxs-lookup"><span data-stu-id="3f47b-108">The GUID of the cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] type.</span></span>|  
|`pType`|<span data-ttu-id="3f47b-109">Bir işaretçi Icordebugtype nesneye önbelleğe alınmış türü hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="3f47b-109">A pointer to an ICorDebugType object that provides information about the cached type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3f47b-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3f47b-110">Requirements</span></span>  
 <span data-ttu-id="3f47b-111">**Platformlar:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3f47b-111">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)].</span></span>  
  
 <span data-ttu-id="3f47b-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3f47b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3f47b-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3f47b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3f47b-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f47b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f47b-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3f47b-115">See Also</span></span>  
 [<span data-ttu-id="3f47b-116">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="3f47b-116">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="3f47b-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="3f47b-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
