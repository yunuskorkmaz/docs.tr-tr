---
title: 'ICorDebugCode4:: Enumeratevariableevler yöntemi'
ms.date: 03/30/2017
api_name:
- ICorDebugCode4.EnumerateVariableHomes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode4::EnumerateVariableHomes
helpviewer_keywords:
- EnumerateVariableHomes method [.NET Framework debugging]
- ICorDebugCode4::EnumerateVariableHomes method [.NET Framework debugging]
ms.assetid: 802c01ff-8b80-4733-b6dd-03ab6ff7fa11
topic_type:
- apiref
ms.openlocfilehash: 850cbd2367dddd9f46375817e271cb8e7183cf64
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121098"
---
# <a name="icordebugcode4enumeratevariablehomes-method"></a><span data-ttu-id="1d957-102">ICorDebugCode4:: Enumeratevariableevler yöntemi</span><span class="sxs-lookup"><span data-stu-id="1d957-102">ICorDebugCode4::EnumerateVariableHomes Method</span></span>
<span data-ttu-id="1d957-103">Bir işlevdeki yerel değişkenlere ve bağımsız değişkenlere bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="1d957-103">Gets an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d957-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1d957-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateVariableHomes(  
    [out] ICorDebugVariableHomeEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d957-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1d957-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="1d957-106">Bir işlevdeki yerel değişkenler ve bağımsız değişkenler için bir Numaralandırıcı olan [ıcordebugvariablehomeenum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) arabirim nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1d957-106">A pointer to the address of an [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) interface object that is an enumerator for the local variables and arguments in a function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d957-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1d957-107">Remarks</span></span>  
 <span data-ttu-id="1d957-108">[Icordebugvariablehomeenum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) arabirimi nesnesi, [ıcordebugvariablehome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) nesnelerini Listeletmanızı sağlayan "ıcordebugger genum" arabiriminden türetilmiş standart bir Numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="1d957-108">The [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) interface object is a standard enumerator derived from the "ICorDebugEnum" interface that allows you to enumerate [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objects.</span></span> <span data-ttu-id="1d957-109">Koleksiyonda farklı noktalarda farklı evler varsa, koleksiyonda aynı yuva veya bağımsız değişken dizini için birden çok [ıcordebugvariablehome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) nesnesi bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="1d957-109">The collection may include multiple [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objects for the same slot or      argument index if they have different homes at different points in the      function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d957-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1d957-110">Requirements</span></span>  
 <span data-ttu-id="1d957-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d957-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d957-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1d957-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1d957-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1d957-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1d957-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d957-114">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d957-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d957-115">See also</span></span>

- [<span data-ttu-id="1d957-116">ICorDebugCode4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1d957-116">ICorDebugCode4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md)
- [<span data-ttu-id="1d957-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1d957-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
