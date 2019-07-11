---
title: ICorDebugDebugEvent::GetEventKind Yöntemi
ms.date: 03/30/2017
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fdbc320e13e0cb140f5ef7aa63b878b43ca0189b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750057"
---
# <a name="icordebugdebugeventgeteventkind-method"></a><span data-ttu-id="6bb55-102">ICorDebugDebugEvent::GetEventKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6bb55-102">ICorDebugDebugEvent::GetEventKind Method</span></span>
<span data-ttu-id="6bb55-103">Bu olay türünü gösterir `ICorDebugDebugEvent` nesnesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6bb55-103">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bb55-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6bb55-104">Syntax</span></span>  
  
```cpp  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6bb55-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6bb55-105">Parameters</span></span>  
 <span data-ttu-id="6bb55-106">pDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="6bb55-106">pDebugEventKind</span></span>  
 <span data-ttu-id="6bb55-107">Bir işaretçi bir [CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) olay türünü belirten sabit listesi üyesi.</span><span class="sxs-lookup"><span data-stu-id="6bb55-107">A pointer to a [CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) enumeration member that indicates the type of event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6bb55-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6bb55-108">Remarks</span></span>  
 <span data-ttu-id="6bb55-109">Değerine göre `pDebugEventKind`, çağırabilirsiniz `QueryInterface` ek veriler içeren daha kesin bir hata ayıklama olay arabirimi alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="6bb55-109">Based on the value of `pDebugEventKind`, you can call `QueryInterface` to get a more precise debug event interface that has additional data.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6bb55-110">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6bb55-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bb55-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6bb55-111">Requirements</span></span>  
 <span data-ttu-id="6bb55-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6bb55-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bb55-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6bb55-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6bb55-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6bb55-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6bb55-115">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bb55-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bb55-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6bb55-116">See also</span></span>

- [<span data-ttu-id="6bb55-117">ICorDebugDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6bb55-117">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)
- [<span data-ttu-id="6bb55-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6bb55-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
