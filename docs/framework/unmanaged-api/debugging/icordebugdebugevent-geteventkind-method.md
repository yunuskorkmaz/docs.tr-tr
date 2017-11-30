---
title: ICorDebugDebugEvent::GetEventKind Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cf3296eafb3e3ff933092240f8f353b2b69a89c3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdebugeventgeteventkind-method"></a><span data-ttu-id="3fb1e-102">ICorDebugDebugEvent::GetEventKind Metodu</span><span class="sxs-lookup"><span data-stu-id="3fb1e-102">ICorDebugDebugEvent::GetEventKind Method</span></span>
<span data-ttu-id="3fb1e-103">Bu olay türlerini gösterir `ICorDebugDebugEvent` nesne temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3fb1e-103">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fb1e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3fb1e-104">Syntax</span></span>  
  
```  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3fb1e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3fb1e-105">Parameters</span></span>  
 <span data-ttu-id="3fb1e-106">pDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="3fb1e-106">pDebugEventKind</span></span>  
 <span data-ttu-id="3fb1e-107">Bir işaretçi bir [CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) olay türünü gösteren numaralandırma üyesi.</span><span class="sxs-lookup"><span data-stu-id="3fb1e-107">A pointer to a [CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) enumeration member that indicates the type of event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3fb1e-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3fb1e-108">Remarks</span></span>  
 <span data-ttu-id="3fb1e-109">Değerine göre `pDebugEventKind`, çağırabilirsiniz `QueryInterface` ek verileri içeren daha kesin bir hata ayıklama olay arabirimi alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="3fb1e-109">Based on the value of `pDebugEventKind`, you can call `QueryInterface` to get a more precise debug event interface that has additional data.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3fb1e-110">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3fb1e-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fb1e-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3fb1e-111">Requirements</span></span>  
 <span data-ttu-id="3fb1e-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fb1e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fb1e-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3fb1e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3fb1e-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3fb1e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3fb1e-115">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fb1e-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fb1e-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3fb1e-116">See Also</span></span>  
 [<span data-ttu-id="3fb1e-117">Icordebugdebugevent arabirimi</span><span class="sxs-lookup"><span data-stu-id="3fb1e-117">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)  
 [<span data-ttu-id="3fb1e-118">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3fb1e-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
