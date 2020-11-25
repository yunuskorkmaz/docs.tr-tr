---
title: 'Icordebugexceptiondebugger gevent:: GetFlags metodu'
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
ms.openlocfilehash: 02a20b54b7fecc711bda010c6916fe036cf20dd9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729609"
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="257b5-102">Icordebugexceptiondebugger gevent:: GetFlags metodu</span><span class="sxs-lookup"><span data-stu-id="257b5-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>

<span data-ttu-id="257b5-103">Özel durumun yakalanıp yakalanamayacağını gösteren bir bayrak alır.</span><span class="sxs-lookup"><span data-stu-id="257b5-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="257b5-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="257b5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="257b5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="257b5-105">Parameters</span></span>  

 `pdwFlags`  
 <span data-ttu-id="257b5-106">dışı Özel durumun yakalanıp yakalanamayacağını belirten [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) değerine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="257b5-106">[out] A pointer to a [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="257b5-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="257b5-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="257b5-108">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="257b5-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="257b5-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="257b5-109">Requirements</span></span>  

 <span data-ttu-id="257b5-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="257b5-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="257b5-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="257b5-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="257b5-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="257b5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="257b5-113">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="257b5-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="257b5-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="257b5-114">See also</span></span>

- [<span data-ttu-id="257b5-115">ICorDebugExceptionDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="257b5-115">ICorDebugExceptionDebugEvent Interface</span></span>](icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="257b5-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="257b5-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
