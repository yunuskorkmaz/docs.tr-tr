---
title: ICorDebugChain::EnumerateFrames Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugChain.EnumerateFrames
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::EnumerateFrames method
helpviewer_keywords:
- EnumerateFrames method [.NET Framework debugging]
- ICorDebugChain::EnumerateFrames method [.NET Framework debugging]
ms.assetid: 9fcefa98-750d-4168-8915-8173a43accf2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fc647805fcb7d8354a2540ac9424dc7155853444
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745041"
---
# <a name="icordebugchainenumerateframes-method"></a><span data-ttu-id="5b2fd-102">ICorDebugChain::EnumerateFrames Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5b2fd-102">ICorDebugChain::EnumerateFrames Method</span></span>
<span data-ttu-id="5b2fd-103">En son çerçeve ile başlayan zincirindeki tüm yönetilen yığın çerçevesi içeren bir numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="5b2fd-103">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b2fd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5b2fd-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateFrames (  
    [out] ICorDebugFrameEnum **ppFrames  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b2fd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5b2fd-105">Parameters</span></span>  
 `ppFrames`  
 <span data-ttu-id="5b2fd-106">[out] Yığın çerçevesi için Numaralandırıcı Icordebugframeenum nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5b2fd-106">[out] A pointer to the address of an ICorDebugFrameEnum object that is the enumerator for the stack frames.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b2fd-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5b2fd-107">Remarks</span></span>  
 <span data-ttu-id="5b2fd-108">Zinciri, iş parçacığı için fiziksel çağrı yığınını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5b2fd-108">The chain represents the physical call stack for the thread.</span></span>  
  
 <span data-ttu-id="5b2fd-109">`EnumerateFrames` Yöntemi yalnızca yönetilen zincirleri için çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="5b2fd-109">The `EnumerateFrames` method should be called only for managed chains.</span></span> <span data-ttu-id="5b2fd-110">Hata ayıklama API yöntemleri yönetilmeyen zincirde bulunan çerçeveleri almak için sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="5b2fd-110">The debugging API does not provide methods for obtaining frames contained in unmanaged chains.</span></span> <span data-ttu-id="5b2fd-111">Hata ayıklayıcı bu bilgiyi elde etmek için başka bir yolla kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5b2fd-111">The debugger must use other means to obtain this information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b2fd-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5b2fd-112">Requirements</span></span>  
 <span data-ttu-id="5b2fd-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b2fd-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b2fd-114">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5b2fd-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5b2fd-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5b2fd-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5b2fd-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b2fd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
