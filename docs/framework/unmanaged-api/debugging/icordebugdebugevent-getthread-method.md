---
title: ICorDebugDebugEvent::GetThread Yöntemi
ms.date: 03/30/2017
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
ms.openlocfilehash: ca6aba7897d9e97743d29db49bd058e140f84e6e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713593"
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="0f691-102">ICorDebugDebugEvent::GetThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f691-102">ICorDebugDebugEvent::GetThread Method</span></span>

<span data-ttu-id="0f691-103">Olayın gerçekleştiği iş parçacığını alır.</span><span class="sxs-lookup"><span data-stu-id="0f691-103">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f691-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="0f691-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f691-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0f691-105">Parameters</span></span>  

 <span data-ttu-id="0f691-106">ppThread</span><span class="sxs-lookup"><span data-stu-id="0f691-106">ppThread</span></span>  
 <span data-ttu-id="0f691-107">dışı Olayın gerçekleştiği iş parçacığını temsil eden ICorDebugThread nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0f691-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f691-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0f691-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0f691-109">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0f691-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f691-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0f691-110">Requirements</span></span>  

 <span data-ttu-id="0f691-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f691-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f691-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0f691-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0f691-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0f691-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0f691-114">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f691-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f691-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f691-115">See also</span></span>

- [<span data-ttu-id="0f691-116">ICorDebugDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0f691-116">ICorDebugDebugEvent Interface</span></span>](icordebugdebugevent-interface.md)
- [<span data-ttu-id="0f691-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0f691-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
