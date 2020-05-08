---
title: ICorDebugDebugEvent::GetEventKind Yöntemi
ms.date: 03/30/2017
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
ms.openlocfilehash: 6e3ebdcb5b3e85f6f5a329ed249aa58be903e30f
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976401"
---
# <a name="icordebugdebugeventgeteventkind-method"></a><span data-ttu-id="2108f-102">ICorDebugDebugEvent::GetEventKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2108f-102">ICorDebugDebugEvent::GetEventKind Method</span></span>
<span data-ttu-id="2108f-103">Bu `ICorDebugDebugEvent` nesnenin ne tür bir olayın temsil ettiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2108f-103">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2108f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2108f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2108f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2108f-105">Parameters</span></span>  
 <span data-ttu-id="2108f-106">Pıbu Geventkind</span><span class="sxs-lookup"><span data-stu-id="2108f-106">pDebugEventKind</span></span>  
 <span data-ttu-id="2108f-107">Olayın türünü gösteren bir [Cordebugdebugger Geventkind](cordebugdebugeventkind-enumeration.md) numaralandırma üyesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2108f-107">A pointer to a [CorDebugDebugEventKind](cordebugdebugeventkind-enumeration.md) enumeration member that indicates the type of event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2108f-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2108f-108">Remarks</span></span>  
 <span data-ttu-id="2108f-109">Değerine bağlı `pDebugEventKind`olarak, ek verilere sahip daha kesin `QueryInterface` bir hata ayıklama olay arabirimi almak için öğesini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2108f-109">Based on the value of `pDebugEventKind`, you can call `QueryInterface` to get a more precise debug event interface that has additional data.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2108f-110">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2108f-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2108f-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2108f-111">Requirements</span></span>  
 <span data-ttu-id="2108f-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2108f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2108f-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2108f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2108f-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2108f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2108f-115">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2108f-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2108f-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2108f-116">See also</span></span>

- [<span data-ttu-id="2108f-117">ICorDebugDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2108f-117">ICorDebugDebugEvent Interface</span></span>](icordebugdebugevent-interface.md)
- [<span data-ttu-id="2108f-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2108f-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
