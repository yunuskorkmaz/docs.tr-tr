---
title: ICorDebugDebugEvent::GetEventKind Metodu
ms.date: 03/30/2017
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9bbc9581db839d9c0a48362eac2108f43665b0fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414862"
---
# <a name="icordebugdebugeventgeteventkind-method"></a><span data-ttu-id="254ac-102">ICorDebugDebugEvent::GetEventKind Metodu</span><span class="sxs-lookup"><span data-stu-id="254ac-102">ICorDebugDebugEvent::GetEventKind Method</span></span>
<span data-ttu-id="254ac-103">Bu olay türlerini gösterir `ICorDebugDebugEvent` nesne temsil eder.</span><span class="sxs-lookup"><span data-stu-id="254ac-103">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="254ac-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="254ac-104">Syntax</span></span>  
  
```  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="254ac-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="254ac-105">Parameters</span></span>  
 <span data-ttu-id="254ac-106">pDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="254ac-106">pDebugEventKind</span></span>  
 <span data-ttu-id="254ac-107">Bir işaretçi bir [CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) olay türünü gösteren numaralandırma üyesi.</span><span class="sxs-lookup"><span data-stu-id="254ac-107">A pointer to a [CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) enumeration member that indicates the type of event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="254ac-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="254ac-108">Remarks</span></span>  
 <span data-ttu-id="254ac-109">Değerine göre `pDebugEventKind`, çağırabilirsiniz `QueryInterface` ek verileri içeren daha kesin bir hata ayıklama olay arabirimi alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="254ac-109">Based on the value of `pDebugEventKind`, you can call `QueryInterface` to get a more precise debug event interface that has additional data.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="254ac-110">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="254ac-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="254ac-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="254ac-111">Requirements</span></span>  
 <span data-ttu-id="254ac-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="254ac-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="254ac-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="254ac-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="254ac-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="254ac-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="254ac-115">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="254ac-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="254ac-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="254ac-116">See Also</span></span>  
 [<span data-ttu-id="254ac-117">ICorDebugDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="254ac-117">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)  
 [<span data-ttu-id="254ac-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="254ac-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
