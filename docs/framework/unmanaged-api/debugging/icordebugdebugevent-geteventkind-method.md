---
title: ICorDebugDebugEvent::GetEventKind Yöntemi
ms.date: 03/30/2017
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a87dda8d8a263df1989a685d94c5163212f41382
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911335"
---
# <a name="icordebugdebugeventgeteventkind-method"></a><span data-ttu-id="c9fe5-102">ICorDebugDebugEvent::GetEventKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c9fe5-102">ICorDebugDebugEvent::GetEventKind Method</span></span>
<span data-ttu-id="c9fe5-103">Bu `ICorDebugDebugEvent` nesnenin ne tür bir olayın temsil ettiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c9fe5-103">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9fe5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c9fe5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9fe5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c9fe5-105">Parameters</span></span>  
 <span data-ttu-id="c9fe5-106">Pıbu Geventkind</span><span class="sxs-lookup"><span data-stu-id="c9fe5-106">pDebugEventKind</span></span>  
 <span data-ttu-id="c9fe5-107">Olayın türünü gösteren bir [Cordebugdebugger Geventkind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) numaralandırma üyesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c9fe5-107">A pointer to a [CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) enumeration member that indicates the type of event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9fe5-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c9fe5-108">Remarks</span></span>  
 <span data-ttu-id="c9fe5-109">Değerine `pDebugEventKind`bağlı olarak, ek verilere sahip daha kesin `QueryInterface` bir hata ayıklama olay arabirimi almak için öğesini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9fe5-109">Based on the value of `pDebugEventKind`, you can call `QueryInterface` to get a more precise debug event interface that has additional data.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c9fe5-110">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c9fe5-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9fe5-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c9fe5-111">Requirements</span></span>  
 <span data-ttu-id="c9fe5-112">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9fe5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9fe5-113">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c9fe5-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c9fe5-114">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c9fe5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9fe5-115">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9fe5-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9fe5-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9fe5-116">See also</span></span>

- [<span data-ttu-id="c9fe5-117">ICorDebugDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c9fe5-117">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)
- [<span data-ttu-id="c9fe5-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c9fe5-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
