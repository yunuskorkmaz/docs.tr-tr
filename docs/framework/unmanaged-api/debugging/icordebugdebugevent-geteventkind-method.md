---
description: ': Icordebugdebugger gevent:: GetEventKind yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugDebugEvent::GetEventKind Yöntemi
ms.date: 03/30/2017
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
ms.openlocfilehash: 9e15eb82195fae8aa3797ea47cb04d0bb407d2ad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764326"
---
# <a name="icordebugdebugeventgeteventkind-method"></a><span data-ttu-id="87d68-103">ICorDebugDebugEvent::GetEventKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="87d68-103">ICorDebugDebugEvent::GetEventKind Method</span></span>

<span data-ttu-id="87d68-104">Bu nesnenin ne tür bir olayın `ICorDebugDebugEvent` temsil ettiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="87d68-104">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87d68-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="87d68-105">Syntax</span></span>  
  
```cpp  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87d68-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="87d68-106">Parameters</span></span>  

 <span data-ttu-id="87d68-107">Pıbu Geventkind</span><span class="sxs-lookup"><span data-stu-id="87d68-107">pDebugEventKind</span></span>  
 <span data-ttu-id="87d68-108">Olayın türünü gösteren bir [Cordebugdebugger Geventkind](cordebugdebugeventkind-enumeration.md) numaralandırma üyesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="87d68-108">A pointer to a [CorDebugDebugEventKind](cordebugdebugeventkind-enumeration.md) enumeration member that indicates the type of event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87d68-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="87d68-109">Remarks</span></span>  

 <span data-ttu-id="87d68-110">Değerine bağlı `pDebugEventKind` olarak, `QueryInterface` ek verilere sahip daha kesin bir hata ayıklama olay arabirimi almak için öğesini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87d68-110">Based on the value of `pDebugEventKind`, you can call `QueryInterface` to get a more precise debug event interface that has additional data.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="87d68-111">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="87d68-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87d68-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="87d68-112">Requirements</span></span>  

 <span data-ttu-id="87d68-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87d68-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87d68-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="87d68-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="87d68-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="87d68-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87d68-116">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87d68-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87d68-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87d68-117">See also</span></span>

- [<span data-ttu-id="87d68-118">ICorDebugDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="87d68-118">ICorDebugDebugEvent Interface</span></span>](icordebugdebugevent-interface.md)
- [<span data-ttu-id="87d68-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="87d68-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
