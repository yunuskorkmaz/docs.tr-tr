---
description: 'Daha fazla bilgi edinin: COR_ACTIVE_FUNCTION yapısı'
title: COR_ACTIVE_FUNCTION Yapısı
ms.date: 03/30/2017
api_name:
- COR_ACTIVE_FUNCTION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_ACTIVE_FUNCTION
helpviewer_keywords:
- COR_ACTIVE_FUNCTION structure [.NET Framework debugging]
ms.assetid: ed86185f-2152-459c-961f-10c06d62e83f
topic_type:
- apiref
ms.openlocfilehash: 7cc4a314c11ca4e2cdb4fe2b4090c471bcda26d5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747250"
---
# <a name="cor_active_function-structure"></a><span data-ttu-id="b6ebd-103">COR_ACTIVE_FUNCTION Yapısı</span><span class="sxs-lookup"><span data-stu-id="b6ebd-103">COR_ACTIVE_FUNCTION Structure</span></span>

<span data-ttu-id="b6ebd-104">Şu anda bir iş parçacığının çerçevelerinde etkin olan işlevlerle ilgili bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="b6ebd-104">Contains information about the functions that are currently active in a thread's frames.</span></span> <span data-ttu-id="b6ebd-105">Bu yapı, [ICorDebugThread2:: GetActiveFunctions](icordebugthread2-getactivefunctions-method.md) yöntemi tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b6ebd-105">This structure is used by the [ICorDebugThread2::GetActiveFunctions](icordebugthread2-getactivefunctions-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6ebd-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="b6ebd-106">Syntax</span></span>  
  
```cpp  
typedef struct  _COR_ACTIVE_FUNCTION {  
    ICorDebugAppDomain   *pAppDomain;  
    ICorDebugModule      *pModule;  
    ICorDebugFunction2   *pFunction;  
    ULONG32              ilOffset;  
    ULONG32              flags;  
} COR_ACTIVE_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="b6ebd-107">Üyeler</span><span class="sxs-lookup"><span data-stu-id="b6ebd-107">Members</span></span>  
  
|<span data-ttu-id="b6ebd-108">Üye</span><span class="sxs-lookup"><span data-stu-id="b6ebd-108">Member</span></span>|<span data-ttu-id="b6ebd-109">Description</span><span class="sxs-lookup"><span data-stu-id="b6ebd-109">Description</span></span>|  
|------------|-----------------|  
|`pAppDomain`|<span data-ttu-id="b6ebd-110">Alanın uygulama etki alanı sahibine yönelik işaretçi `ilOffset` .</span><span class="sxs-lookup"><span data-stu-id="b6ebd-110">Pointer to the application domain owner of the `ilOffset` field.</span></span>|  
|`pModule`|<span data-ttu-id="b6ebd-111">Alanın modül sahibine yönelik işaretçi `ilOffset` .</span><span class="sxs-lookup"><span data-stu-id="b6ebd-111">Pointer to the module owner of the `ilOffset` field.</span></span>|  
|`pFunction`|<span data-ttu-id="b6ebd-112">Alanın işlev sahibine yönelik işaretçi `ilOffset` .</span><span class="sxs-lookup"><span data-stu-id="b6ebd-112">Pointer to the function owner of the `ilOffset` field.</span></span>|  
|`ilOffset`|<span data-ttu-id="b6ebd-113">Çerçevenin Microsoft ara dili (MSIL) kayması.</span><span class="sxs-lookup"><span data-stu-id="b6ebd-113">The Microsoft intermediate language (MSIL) offset of the frame.</span></span>|  
|`flags`|<span data-ttu-id="b6ebd-114">Gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="b6ebd-114">Reserved for future extensibility.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b6ebd-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b6ebd-115">Requirements</span></span>  

 <span data-ttu-id="b6ebd-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6ebd-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6ebd-117">**Üst bilgi:** CorDebug. IDL</span><span class="sxs-lookup"><span data-stu-id="b6ebd-117">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="b6ebd-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b6ebd-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6ebd-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6ebd-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6ebd-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b6ebd-120">See also</span></span>

- [<span data-ttu-id="b6ebd-121">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="b6ebd-121">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="b6ebd-122">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="b6ebd-122">Debugging</span></span>](index.md)
