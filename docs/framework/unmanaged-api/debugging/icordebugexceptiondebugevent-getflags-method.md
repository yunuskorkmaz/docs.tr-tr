---
title: 'Icordebugexceptiondebugger gevent:: GetFlags metodu'
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
ms.openlocfilehash: 6c330ce5b375daacdf257eda16fd5e34012f5d69
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084762"
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="4f1b2-102">Icordebugexceptiondebugger gevent:: GetFlags metodu</span><span class="sxs-lookup"><span data-stu-id="4f1b2-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>
<span data-ttu-id="4f1b2-103">Özel durumun yakalanıp yakalanamayacağını gösteren bir bayrak alır.</span><span class="sxs-lookup"><span data-stu-id="4f1b2-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f1b2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4f1b2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f1b2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4f1b2-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="4f1b2-106">dışı Özel durumun yakalanıp yakalanamayacağını belirten [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) değerine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4f1b2-106">[out] A pointer to a [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f1b2-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4f1b2-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4f1b2-108">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4f1b2-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f1b2-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4f1b2-109">Requirements</span></span>  
 <span data-ttu-id="4f1b2-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f1b2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f1b2-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4f1b2-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4f1b2-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4f1b2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f1b2-113">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f1b2-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f1b2-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f1b2-114">See also</span></span>

- [<span data-ttu-id="4f1b2-115">ICorDebugExceptionDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4f1b2-115">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="4f1b2-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4f1b2-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
