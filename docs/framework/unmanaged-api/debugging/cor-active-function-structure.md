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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6875ce0e7ae4cefa9b0c8abaded0dd4535bdf838
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740829"
---
# <a name="coractivefunction-structure"></a><span data-ttu-id="ccf5d-102">COR_ACTIVE_FUNCTION Yapısı</span><span class="sxs-lookup"><span data-stu-id="ccf5d-102">COR_ACTIVE_FUNCTION Structure</span></span>
<span data-ttu-id="ccf5d-103">Bir iş parçacığının çerçevelerde şu an etkin olan işlevler hakkında bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="ccf5d-103">Contains information about the functions that are currently active in a thread's frames.</span></span> <span data-ttu-id="ccf5d-104">Bu yapı tarafından kullanılan [Icordebugthread2::getactivefunctions](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ccf5d-104">This structure is used by the [ICorDebugThread2::GetActiveFunctions](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccf5d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ccf5d-105">Syntax</span></span>  
  
```cpp  
typedef struct  _COR_ACTIVE_FUNCTION {  
    ICorDebugAppDomain   *pAppDomain;  
    ICorDebugModule      *pModule;  
    ICorDebugFunction2   *pFunction;  
    ULONG32              ilOffset;  
    ULONG32              flags;  
} COR_ACTIVE_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="ccf5d-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="ccf5d-106">Members</span></span>  
  
|<span data-ttu-id="ccf5d-107">Üye</span><span class="sxs-lookup"><span data-stu-id="ccf5d-107">Member</span></span>|<span data-ttu-id="ccf5d-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ccf5d-108">Description</span></span>|  
|------------|-----------------|  
|`pAppDomain`|<span data-ttu-id="ccf5d-109">Uygulama etki alanı sahibi işaretçisine `ilOffset` alan.</span><span class="sxs-lookup"><span data-stu-id="ccf5d-109">Pointer to the application domain owner of the `ilOffset` field.</span></span>|  
|`pModule`|<span data-ttu-id="ccf5d-110">İşaretçi modülü sahibine `ilOffset` alan.</span><span class="sxs-lookup"><span data-stu-id="ccf5d-110">Pointer to the module owner of the `ilOffset` field.</span></span>|  
|`pFunction`|<span data-ttu-id="ccf5d-111">İşaretçi işlevi sahibine `ilOffset` alan.</span><span class="sxs-lookup"><span data-stu-id="ccf5d-111">Pointer to the function owner of the `ilOffset` field.</span></span>|  
|`ilOffset`|<span data-ttu-id="ccf5d-112">Çerçevenin Microsoft Ara dili (MSIL) uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="ccf5d-112">The Microsoft intermediate language (MSIL) offset of the frame.</span></span>|  
|`flags`|<span data-ttu-id="ccf5d-113">Sonra genişletilebilmek için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="ccf5d-113">Reserved for future extensibility.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ccf5d-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ccf5d-114">Requirements</span></span>  
 <span data-ttu-id="ccf5d-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ccf5d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccf5d-116">**Üst bilgi:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="ccf5d-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="ccf5d-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ccf5d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ccf5d-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ccf5d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccf5d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ccf5d-119">See also</span></span>

- [<span data-ttu-id="ccf5d-120">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="ccf5d-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="ccf5d-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="ccf5d-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
