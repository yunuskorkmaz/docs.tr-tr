---
title: 'Icordebugexceptiondebugger gevent:: GetFlags metodu'
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
ms.openlocfilehash: aaf137b1d851d0de86bde697c9e3a512f34d2aa9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782913"
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="b91a3-102">Icordebugexceptiondebugger gevent:: GetFlags metodu</span><span class="sxs-lookup"><span data-stu-id="b91a3-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>
<span data-ttu-id="b91a3-103">Özel durumun yakalanıp yakalanamayacağını gösteren bir bayrak alır.</span><span class="sxs-lookup"><span data-stu-id="b91a3-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b91a3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b91a3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b91a3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b91a3-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="b91a3-106">dışı Özel durumun yakalanıp yakalanamayacağını belirten [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) değerine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b91a3-106">[out] A pointer to a [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b91a3-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b91a3-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b91a3-108">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b91a3-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b91a3-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b91a3-109">Requirements</span></span>  
 <span data-ttu-id="b91a3-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b91a3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b91a3-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b91a3-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b91a3-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b91a3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b91a3-113">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b91a3-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b91a3-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b91a3-114">See also</span></span>

- [<span data-ttu-id="b91a3-115">ICorDebugExceptionDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b91a3-115">ICorDebugExceptionDebugEvent Interface</span></span>](icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="b91a3-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b91a3-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
