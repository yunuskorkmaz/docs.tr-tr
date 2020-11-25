---
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
ms.openlocfilehash: c50ba530d78296ebb956329b2f34b4f1e5cae94c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727427"
---
# <a name="cor_active_function-structure"></a><span data-ttu-id="4fb5d-102">COR_ACTIVE_FUNCTION Yapısı</span><span class="sxs-lookup"><span data-stu-id="4fb5d-102">COR_ACTIVE_FUNCTION Structure</span></span>

<span data-ttu-id="4fb5d-103">Şu anda bir iş parçacığının çerçevelerinde etkin olan işlevlerle ilgili bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="4fb5d-103">Contains information about the functions that are currently active in a thread's frames.</span></span> <span data-ttu-id="4fb5d-104">Bu yapı, [ICorDebugThread2:: GetActiveFunctions](icordebugthread2-getactivefunctions-method.md) yöntemi tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4fb5d-104">This structure is used by the [ICorDebugThread2::GetActiveFunctions](icordebugthread2-getactivefunctions-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fb5d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="4fb5d-105">Syntax</span></span>  
  
```cpp  
typedef struct  _COR_ACTIVE_FUNCTION {  
    ICorDebugAppDomain   *pAppDomain;  
    ICorDebugModule      *pModule;  
    ICorDebugFunction2   *pFunction;  
    ULONG32              ilOffset;  
    ULONG32              flags;  
} COR_ACTIVE_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="4fb5d-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="4fb5d-106">Members</span></span>  
  
|<span data-ttu-id="4fb5d-107">Üye</span><span class="sxs-lookup"><span data-stu-id="4fb5d-107">Member</span></span>|<span data-ttu-id="4fb5d-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4fb5d-108">Description</span></span>|  
|------------|-----------------|  
|`pAppDomain`|<span data-ttu-id="4fb5d-109">Alanın uygulama etki alanı sahibine yönelik işaretçi `ilOffset` .</span><span class="sxs-lookup"><span data-stu-id="4fb5d-109">Pointer to the application domain owner of the `ilOffset` field.</span></span>|  
|`pModule`|<span data-ttu-id="4fb5d-110">Alanın modül sahibine yönelik işaretçi `ilOffset` .</span><span class="sxs-lookup"><span data-stu-id="4fb5d-110">Pointer to the module owner of the `ilOffset` field.</span></span>|  
|`pFunction`|<span data-ttu-id="4fb5d-111">Alanın işlev sahibine yönelik işaretçi `ilOffset` .</span><span class="sxs-lookup"><span data-stu-id="4fb5d-111">Pointer to the function owner of the `ilOffset` field.</span></span>|  
|`ilOffset`|<span data-ttu-id="4fb5d-112">Çerçevenin Microsoft ara dili (MSIL) kayması.</span><span class="sxs-lookup"><span data-stu-id="4fb5d-112">The Microsoft intermediate language (MSIL) offset of the frame.</span></span>|  
|`flags`|<span data-ttu-id="4fb5d-113">Gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="4fb5d-113">Reserved for future extensibility.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4fb5d-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4fb5d-114">Requirements</span></span>  

 <span data-ttu-id="4fb5d-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4fb5d-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fb5d-116">**Üst bilgi:** CorDebug. IDL</span><span class="sxs-lookup"><span data-stu-id="4fb5d-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="4fb5d-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4fb5d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4fb5d-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fb5d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fb5d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4fb5d-119">See also</span></span>

- [<span data-ttu-id="4fb5d-120">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="4fb5d-120">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="4fb5d-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="4fb5d-121">Debugging</span></span>](index.md)
