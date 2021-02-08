---
description: 'Şu konuda daha fazla bilgi edinin: CorDebugGuidToTypeMapping yapısı'
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
ms.openlocfilehash: 5f6e99a17483b4fc16eb36ebb5fb5fd81380944b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801624"
---
# <a name="cordebugguidtotypemapping-structure"></a><span data-ttu-id="3cf66-103">CorDebugGuidToTypeMapping Yapısı</span><span class="sxs-lookup"><span data-stu-id="3cf66-103">CorDebugGuidToTypeMapping Structure</span></span>

<span data-ttu-id="3cf66-104">Windows Çalışma Zamanı GUID 'sini karşılık gelen ICorDebugType nesnesine eşler.</span><span class="sxs-lookup"><span data-stu-id="3cf66-104">Maps a Windows Runtime GUID to its corresponding ICorDebugType object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cf66-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="3cf66-105">Syntax</span></span>  
  
```cpp
typedef struct CorDebugGuidToTypeMapping {  
    GUID iid;  
    ICorDebugType *pType;  
} CorDebugGuidToTypeMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="3cf66-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="3cf66-106">Members</span></span>  
  
|<span data-ttu-id="3cf66-107">Üye</span><span class="sxs-lookup"><span data-stu-id="3cf66-107">Member</span></span>|<span data-ttu-id="3cf66-108">Description</span><span class="sxs-lookup"><span data-stu-id="3cf66-108">Description</span></span>|  
|------------|-----------------|  
|`iid`|<span data-ttu-id="3cf66-109">Önbelleğe alınan Windows Çalışma Zamanı türünün GUID 'SI.</span><span class="sxs-lookup"><span data-stu-id="3cf66-109">The GUID of the cached Windows Runtime type.</span></span>|  
|`pType`|<span data-ttu-id="3cf66-110">Önbelleğe alınmış tür hakkında bilgi sağlayan ICorDebugType nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3cf66-110">A pointer to an ICorDebugType object that provides information about the cached type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3cf66-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3cf66-111">Requirements</span></span>  

 <span data-ttu-id="3cf66-112">**Platformlar:** Windows Çalışma Zamanı.</span><span class="sxs-lookup"><span data-stu-id="3cf66-112">**Platforms:** Windows Runtime.</span></span>  
  
 <span data-ttu-id="3cf66-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3cf66-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3cf66-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3cf66-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3cf66-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3cf66-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cf66-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3cf66-116">See also</span></span>

- [<span data-ttu-id="3cf66-117">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="3cf66-117">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="3cf66-118">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="3cf66-118">Debugging</span></span>](index.md)
