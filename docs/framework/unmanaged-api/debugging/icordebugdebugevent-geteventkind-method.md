---
title: ICorDebugDebugEvent::GetEventKind Yöntemi
ms.date: 03/30/2017
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 62eede48eea01563dbc3e170720694a24343d0a5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150533"
---
# <a name="icordebugdebugeventgeteventkind-method"></a><span data-ttu-id="279df-102">ICorDebugDebugEvent::GetEventKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="279df-102">ICorDebugDebugEvent::GetEventKind Method</span></span>
<span data-ttu-id="279df-103">Bu olay türünü gösterir `ICorDebugDebugEvent` nesnesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="279df-103">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="279df-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="279df-104">Syntax</span></span>  
  
```  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="279df-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="279df-105">Parameters</span></span>  
 <span data-ttu-id="279df-106">pDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="279df-106">pDebugEventKind</span></span>  
 <span data-ttu-id="279df-107">Bir işaretçi bir [CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) olay türünü belirten sabit listesi üyesi.</span><span class="sxs-lookup"><span data-stu-id="279df-107">A pointer to a [CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) enumeration member that indicates the type of event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="279df-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="279df-108">Remarks</span></span>  
 <span data-ttu-id="279df-109">Değerine göre `pDebugEventKind`, çağırabilirsiniz `QueryInterface` ek veriler içeren daha kesin bir hata ayıklama olay arabirimi alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="279df-109">Based on the value of `pDebugEventKind`, you can call `QueryInterface` to get a more precise debug event interface that has additional data.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="279df-110">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="279df-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="279df-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="279df-111">Requirements</span></span>  
 <span data-ttu-id="279df-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="279df-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="279df-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="279df-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="279df-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="279df-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="279df-115">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="279df-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="279df-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="279df-116">See also</span></span>

- [<span data-ttu-id="279df-117">ICorDebugDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="279df-117">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)
- [<span data-ttu-id="279df-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="279df-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
