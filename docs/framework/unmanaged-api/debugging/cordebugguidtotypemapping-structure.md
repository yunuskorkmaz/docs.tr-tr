---
title: "CorDebugGuidToTypeMapping Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: CorDebugGuidToTypeMapping
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugGuidToTypeMapping
helpviewer_keywords: CorDebugGuidToTypeMapping structure [.NET Framework debugging]
ms.assetid: 57dbccd9-b16d-4da3-ae25-7a2cf9adf679
topic_type: apiref
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ecdadc96c0fb850fef13ba978fc97eef91dadd65
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugguidtotypemapping-structure"></a><span data-ttu-id="4ff5c-102">CorDebugGuidToTypeMapping Yapısı</span><span class="sxs-lookup"><span data-stu-id="4ff5c-102">CorDebugGuidToTypeMapping Structure</span></span>
<span data-ttu-id="4ff5c-103">MAPS bir [!INCLUDE[wrt](../../../../includes/wrt-md.md)] karşılık gelen Icordebugtype nesne için GUID.</span><span class="sxs-lookup"><span data-stu-id="4ff5c-103">Maps a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID to its corresponding ICorDebugType object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ff5c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4ff5c-104">Syntax</span></span>  
  
```cpp
typedef struct CorDebugGuidToTypeMapping {  
    GUID iid;  
    ICorDebugType *pType;  
} CorDebugGuidToTypeMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="4ff5c-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="4ff5c-105">Members</span></span>  
  
|<span data-ttu-id="4ff5c-106">Üye</span><span class="sxs-lookup"><span data-stu-id="4ff5c-106">Member</span></span>|<span data-ttu-id="4ff5c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4ff5c-107">Description</span></span>|  
|------------|-----------------|  
|`iid`|<span data-ttu-id="4ff5c-108">Önbelleğe alınan GUID'i [!INCLUDE[wrt](../../../../includes/wrt-md.md)] türü.</span><span class="sxs-lookup"><span data-stu-id="4ff5c-108">The GUID of the cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] type.</span></span>|  
|`pType`|<span data-ttu-id="4ff5c-109">Bir işaretçi Icordebugtype nesneye önbelleğe alınmış türü hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="4ff5c-109">A pointer to an ICorDebugType object that provides information about the cached type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4ff5c-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4ff5c-110">Requirements</span></span>  
 <span data-ttu-id="4ff5c-111">**Platformlar:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4ff5c-111">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)].</span></span>  
  
 <span data-ttu-id="4ff5c-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4ff5c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4ff5c-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4ff5c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4ff5c-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ff5c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ff5c-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4ff5c-115">See Also</span></span>  
 [<span data-ttu-id="4ff5c-116">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="4ff5c-116">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="4ff5c-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="4ff5c-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
