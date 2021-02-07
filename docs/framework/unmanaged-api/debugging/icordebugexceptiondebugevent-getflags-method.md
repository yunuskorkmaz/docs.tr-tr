---
description: ': Icordebugexceptiondebugger gevent:: GetFlags yöntemi hakkında daha fazla bilgi edinin'
title: 'Icordebugexceptiondebugger gevent:: GetFlags metodu'
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
ms.openlocfilehash: 54a6c9b0dff2346ca130f80e72fe06dbb3017f10
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693479"
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="daaff-103">Icordebugexceptiondebugger gevent:: GetFlags metodu</span><span class="sxs-lookup"><span data-stu-id="daaff-103">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>

<span data-ttu-id="daaff-104">Özel durumun yakalanıp yakalanamayacağını gösteren bir bayrak alır.</span><span class="sxs-lookup"><span data-stu-id="daaff-104">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="daaff-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="daaff-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="daaff-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="daaff-106">Parameters</span></span>  

 `pdwFlags`  
 <span data-ttu-id="daaff-107">dışı Özel durumun yakalanıp yakalanamayacağını belirten [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) değerine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="daaff-107">[out] A pointer to a [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="daaff-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="daaff-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="daaff-109">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="daaff-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="daaff-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="daaff-110">Requirements</span></span>  

 <span data-ttu-id="daaff-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="daaff-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="daaff-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="daaff-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="daaff-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="daaff-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="daaff-114">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="daaff-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daaff-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="daaff-115">See also</span></span>

- [<span data-ttu-id="daaff-116">ICorDebugExceptionDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="daaff-116">ICorDebugExceptionDebugEvent Interface</span></span>](icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="daaff-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="daaff-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
