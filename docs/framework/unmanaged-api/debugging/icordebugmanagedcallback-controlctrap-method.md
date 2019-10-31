---
title: ICorDebugManagedCallback::ControlCTrap Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ControlCTrap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ControlCTrap
helpviewer_keywords:
- ICorDebugManagedCallback::ControlCTrap method [.NET Framework debugging]
- ControlCTrap method [.NET Framework debugging]
ms.assetid: 0500854e-2121-43d9-a028-64312da35258
topic_type:
- apiref
ms.openlocfilehash: da35db8a943fda5fb3fbf4126684bb9cb7243001
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137421"
---
# <a name="icordebugmanagedcallbackcontrolctrap-method"></a><span data-ttu-id="232c8-102">ICorDebugManagedCallback::ControlCTrap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="232c8-102">ICorDebugManagedCallback::ControlCTrap Method</span></span>
<span data-ttu-id="232c8-103">Hata ayıklayıcıya CTRL + C 'nin hata ayıklamakta olan işlemde yakalandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="232c8-103">Notifies the debugger that a CTRL+C is trapped in the process that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="232c8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="232c8-104">Syntax</span></span>  
  
```cpp  
HRESULT ControlCTrap (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="232c8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="232c8-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="232c8-106">'ndaki CTRL + C 'nin bindirildiği işlemi temsil eden ICorDebugProcess nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="232c8-106">[in] A pointer to an ICorDebugProcess object that represents the process in which the CTRL+C is trapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="232c8-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="232c8-107">Return Value</span></span>  
  
|<span data-ttu-id="232c8-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="232c8-108">HRESULT</span></span>|<span data-ttu-id="232c8-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="232c8-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="232c8-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="232c8-110">S_OK</span></span>|<span data-ttu-id="232c8-111">Hata ayıklayıcı CTRL + C yakalamasını işleymeyecektir.</span><span class="sxs-lookup"><span data-stu-id="232c8-111">The debugger will handle the CTRL+C trap.</span></span>|  
|<span data-ttu-id="232c8-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="232c8-112">S_FALSE</span></span>|<span data-ttu-id="232c8-113">Hata ayıklayıcı CTRL + C yakalamasını işlemez.</span><span class="sxs-lookup"><span data-stu-id="232c8-113">The debugger will not handle the CTRL+C trap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="232c8-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="232c8-114">Remarks</span></span>  
 <span data-ttu-id="232c8-115">İşlemdeki tüm uygulama etki alanları bu geri çağırma için durdurulur.</span><span class="sxs-lookup"><span data-stu-id="232c8-115">All application domains within the process are stopped for this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="232c8-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="232c8-116">Requirements</span></span>  
 <span data-ttu-id="232c8-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="232c8-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="232c8-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="232c8-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="232c8-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="232c8-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="232c8-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="232c8-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="232c8-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="232c8-121">See also</span></span>

- [<span data-ttu-id="232c8-122">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="232c8-122">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
