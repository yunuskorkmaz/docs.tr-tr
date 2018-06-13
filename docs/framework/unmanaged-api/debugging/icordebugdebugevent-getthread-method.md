---
title: ICorDebugDebugEvent::GetThread Metodu
ms.date: 03/30/2017
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c5b4a15f637526cd2faadd2d9d3da143c40140f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414911"
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="ef9e8-102">ICorDebugDebugEvent::GetThread Metodu</span><span class="sxs-lookup"><span data-stu-id="ef9e8-102">ICorDebugDebugEvent::GetThread Method</span></span>
<span data-ttu-id="ef9e8-103">Olayın oluştuğu iş parçacığı alır.</span><span class="sxs-lookup"><span data-stu-id="ef9e8-103">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef9e8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ef9e8-104">Syntax</span></span>  
  
```  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ef9e8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ef9e8-105">Parameters</span></span>  
 <span data-ttu-id="ef9e8-106">ppThread</span><span class="sxs-lookup"><span data-stu-id="ef9e8-106">ppThread</span></span>  
 <span data-ttu-id="ef9e8-107">[out] Bir işaretçi adresine Icordebugthread nesnenin olayın oluştuğu iş parçacığı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ef9e8-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef9e8-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ef9e8-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ef9e8-109">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ef9e8-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef9e8-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ef9e8-110">Requirements</span></span>  
 <span data-ttu-id="ef9e8-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef9e8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef9e8-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ef9e8-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ef9e8-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ef9e8-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef9e8-114">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef9e8-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef9e8-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ef9e8-115">See Also</span></span>  
 [<span data-ttu-id="ef9e8-116">ICorDebugDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ef9e8-116">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)  
 [<span data-ttu-id="ef9e8-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ef9e8-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
