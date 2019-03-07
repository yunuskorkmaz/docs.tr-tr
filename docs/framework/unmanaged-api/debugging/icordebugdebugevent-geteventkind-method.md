---
title: ICorDebugDebugEvent::GetEventKind Yöntemi
ms.date: 03/30/2017
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5c778f281224daeec953f2e959444bd1413de433
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57488441"
---
# <a name="icordebugdebugeventgeteventkind-method"></a><span data-ttu-id="919c9-102">ICorDebugDebugEvent::GetEventKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="919c9-102">ICorDebugDebugEvent::GetEventKind Method</span></span>
<span data-ttu-id="919c9-103">Bu olay türünü gösterir `ICorDebugDebugEvent` nesnesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="919c9-103">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="919c9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="919c9-104">Syntax</span></span>  
  
```  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="919c9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="919c9-105">Parameters</span></span>  
 <span data-ttu-id="919c9-106">pDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="919c9-106">pDebugEventKind</span></span>  
 <span data-ttu-id="919c9-107">Bir işaretçi bir [CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) olay türünü belirten sabit listesi üyesi.</span><span class="sxs-lookup"><span data-stu-id="919c9-107">A pointer to a [CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) enumeration member that indicates the type of event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="919c9-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="919c9-108">Remarks</span></span>  
 <span data-ttu-id="919c9-109">Değerine göre `pDebugEventKind`, çağırabilirsiniz `QueryInterface` ek veriler içeren daha kesin bir hata ayıklama olay arabirimi alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="919c9-109">Based on the value of `pDebugEventKind`, you can call `QueryInterface` to get a more precise debug event interface that has additional data.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="919c9-110">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="919c9-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="919c9-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="919c9-111">Requirements</span></span>  
 <span data-ttu-id="919c9-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="919c9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="919c9-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="919c9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="919c9-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="919c9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="919c9-115">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="919c9-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="919c9-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="919c9-116">See also</span></span>
- [<span data-ttu-id="919c9-117">ICorDebugDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="919c9-117">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)
- [<span data-ttu-id="919c9-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="919c9-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
