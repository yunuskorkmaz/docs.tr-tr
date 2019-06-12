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
ms.openlocfilehash: 38e1b19d6340f559e6f8b7e0f7bc042a10df16c3
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025993"
---
# <a name="cordebugguidtotypemapping-structure"></a><span data-ttu-id="6f447-102">CorDebugGuidToTypeMapping Yapısı</span><span class="sxs-lookup"><span data-stu-id="6f447-102">CorDebugGuidToTypeMapping Structure</span></span>
<span data-ttu-id="6f447-103">Bir Windows çalışma zamanı GUID, karşılık gelen Icordebugtype nesnesine eşler.</span><span class="sxs-lookup"><span data-stu-id="6f447-103">Maps a Windows Runtime GUID to its corresponding ICorDebugType object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f447-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6f447-104">Syntax</span></span>  
  
```cpp
typedef struct CorDebugGuidToTypeMapping {  
    GUID iid;  
    ICorDebugType *pType;  
} CorDebugGuidToTypeMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="6f447-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="6f447-105">Members</span></span>  
  
|<span data-ttu-id="6f447-106">Üye</span><span class="sxs-lookup"><span data-stu-id="6f447-106">Member</span></span>|<span data-ttu-id="6f447-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f447-107">Description</span></span>|  
|------------|-----------------|  
|`iid`|<span data-ttu-id="6f447-108">Önbelleğe alınan Windows çalışma zamanı türü GUİD'si.</span><span class="sxs-lookup"><span data-stu-id="6f447-108">The GUID of the cached Windows Runtime type.</span></span>|  
|`pType`|<span data-ttu-id="6f447-109">Önbelleğe alınan türü hakkında bilgi sağlayan Icordebugtype nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="6f447-109">A pointer to an ICorDebugType object that provides information about the cached type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6f447-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6f447-110">Requirements</span></span>  
 <span data-ttu-id="6f447-111">**Platformlar:** Windows çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="6f447-111">**Platforms:** Windows Runtime.</span></span>  
  
 <span data-ttu-id="6f447-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6f447-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6f447-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6f447-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f447-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f447-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f447-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f447-115">See also</span></span>

- [<span data-ttu-id="6f447-116">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="6f447-116">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="6f447-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="6f447-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
