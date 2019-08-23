---
title: 'Icordebugexceptiondebugger gevent:: GetFlags metodu'
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fbe6f6a2953c3f815606e881b86a693b7a0e6ec7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951897"
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="f2630-102">Icordebugexceptiondebugger gevent:: GetFlags metodu</span><span class="sxs-lookup"><span data-stu-id="f2630-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>
<span data-ttu-id="f2630-103">Özel durumun yakalanıp yakalanamayacağını gösteren bir bayrak alır.</span><span class="sxs-lookup"><span data-stu-id="f2630-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2630-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f2630-104">Syntax</span></span>  
  
```  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2630-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f2630-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="f2630-106">dışı Özel durumun yakalanıp yakalanamayacağını belirten [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) değerine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f2630-106">[out] A pointer to a [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2630-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f2630-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f2630-108">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f2630-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2630-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f2630-109">Requirements</span></span>  
 <span data-ttu-id="f2630-110">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2630-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2630-111">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f2630-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f2630-112">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f2630-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2630-113">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2630-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2630-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2630-114">See also</span></span>

- [<span data-ttu-id="f2630-115">ICorDebugExceptionDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f2630-115">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="f2630-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f2630-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
