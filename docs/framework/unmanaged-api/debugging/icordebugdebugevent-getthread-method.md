---
title: ICorDebugDebugEvent::GetThread Yöntemi
ms.date: 03/30/2017
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
ms.openlocfilehash: 66b4abc4bebfbbde2e6a6b25d2bc0e88839a363f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136640"
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="ab24b-102">ICorDebugDebugEvent::GetThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ab24b-102">ICorDebugDebugEvent::GetThread Method</span></span>
<span data-ttu-id="ab24b-103">Olayın gerçekleştiği iş parçacığını alır.</span><span class="sxs-lookup"><span data-stu-id="ab24b-103">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab24b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ab24b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab24b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ab24b-105">Parameters</span></span>  
 <span data-ttu-id="ab24b-106">ppThread</span><span class="sxs-lookup"><span data-stu-id="ab24b-106">ppThread</span></span>  
 <span data-ttu-id="ab24b-107">dışı Olayın gerçekleştiği iş parçacığını temsil eden ICorDebugThread nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ab24b-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab24b-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ab24b-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ab24b-109">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ab24b-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab24b-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ab24b-110">Requirements</span></span>  
 <span data-ttu-id="ab24b-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab24b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab24b-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ab24b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ab24b-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ab24b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab24b-114">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab24b-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab24b-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab24b-115">See also</span></span>

- [<span data-ttu-id="ab24b-116">ICorDebugDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ab24b-116">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)
- [<span data-ttu-id="ab24b-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ab24b-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
