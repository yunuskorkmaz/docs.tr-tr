---
title: ICorDebugDebugEvent::GetThread Yöntemi
ms.date: 03/30/2017
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
ms.openlocfilehash: 0900ac2ae5bcf2141e720dad6efdf68d4fafaccc
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793528"
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="57de9-102">ICorDebugDebugEvent::GetThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="57de9-102">ICorDebugDebugEvent::GetThread Method</span></span>
<span data-ttu-id="57de9-103">Olayın gerçekleştiği iş parçacığını alır.</span><span class="sxs-lookup"><span data-stu-id="57de9-103">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57de9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="57de9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57de9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="57de9-105">Parameters</span></span>  
 <span data-ttu-id="57de9-106">ppThread</span><span class="sxs-lookup"><span data-stu-id="57de9-106">ppThread</span></span>  
 <span data-ttu-id="57de9-107">dışı Olayın gerçekleştiği iş parçacığını temsil eden ICorDebugThread nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="57de9-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57de9-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="57de9-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="57de9-109">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="57de9-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57de9-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="57de9-110">Requirements</span></span>  
 <span data-ttu-id="57de9-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57de9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57de9-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="57de9-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="57de9-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="57de9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="57de9-114">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57de9-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57de9-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="57de9-115">See also</span></span>

- [<span data-ttu-id="57de9-116">ICorDebugDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="57de9-116">ICorDebugDebugEvent Interface</span></span>](icordebugdebugevent-interface.md)
- [<span data-ttu-id="57de9-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="57de9-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
