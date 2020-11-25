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
ms.openlocfilehash: 859853521b741f42f1de7921de813941d2501173
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729102"
---
# <a name="cordebugguidtotypemapping-structure"></a><span data-ttu-id="7df4d-102">CorDebugGuidToTypeMapping Yapısı</span><span class="sxs-lookup"><span data-stu-id="7df4d-102">CorDebugGuidToTypeMapping Structure</span></span>

<span data-ttu-id="7df4d-103">Windows Çalışma Zamanı GUID 'sini karşılık gelen ICorDebugType nesnesine eşler.</span><span class="sxs-lookup"><span data-stu-id="7df4d-103">Maps a Windows Runtime GUID to its corresponding ICorDebugType object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7df4d-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="7df4d-104">Syntax</span></span>  
  
```cpp
typedef struct CorDebugGuidToTypeMapping {  
    GUID iid;  
    ICorDebugType *pType;  
} CorDebugGuidToTypeMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="7df4d-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="7df4d-105">Members</span></span>  
  
|<span data-ttu-id="7df4d-106">Üye</span><span class="sxs-lookup"><span data-stu-id="7df4d-106">Member</span></span>|<span data-ttu-id="7df4d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7df4d-107">Description</span></span>|  
|------------|-----------------|  
|`iid`|<span data-ttu-id="7df4d-108">Önbelleğe alınan Windows Çalışma Zamanı türünün GUID 'SI.</span><span class="sxs-lookup"><span data-stu-id="7df4d-108">The GUID of the cached Windows Runtime type.</span></span>|  
|`pType`|<span data-ttu-id="7df4d-109">Önbelleğe alınmış tür hakkında bilgi sağlayan ICorDebugType nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7df4d-109">A pointer to an ICorDebugType object that provides information about the cached type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7df4d-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7df4d-110">Requirements</span></span>  

 <span data-ttu-id="7df4d-111">**Platformlar:** Windows Çalışma Zamanı.</span><span class="sxs-lookup"><span data-stu-id="7df4d-111">**Platforms:** Windows Runtime.</span></span>  
  
 <span data-ttu-id="7df4d-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7df4d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7df4d-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7df4d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7df4d-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7df4d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7df4d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7df4d-115">See also</span></span>

- [<span data-ttu-id="7df4d-116">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="7df4d-116">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="7df4d-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="7df4d-117">Debugging</span></span>](index.md)
