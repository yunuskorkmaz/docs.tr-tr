---
description: ': ICorDebugManagedCallback:: ControlCTrap yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 9fa71dacb20ff6df21d8aabb687c2601f27643c7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791076"
---
# <a name="icordebugmanagedcallbackcontrolctrap-method"></a><span data-ttu-id="ae834-103">ICorDebugManagedCallback::ControlCTrap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ae834-103">ICorDebugManagedCallback::ControlCTrap Method</span></span>

<span data-ttu-id="ae834-104">Hata ayıklayıcıya CTRL + C 'nin hata ayıklamakta olan işlemde yakalandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="ae834-104">Notifies the debugger that a CTRL+C is trapped in the process that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae834-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ae834-105">Syntax</span></span>  
  
```cpp  
HRESULT ControlCTrap (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae834-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ae834-106">Parameters</span></span>  

 `pProcess`  
 <span data-ttu-id="ae834-107">'ndaki CTRL + C 'nin bindirildiği işlemi temsil eden ICorDebugProcess nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ae834-107">[in] A pointer to an ICorDebugProcess object that represents the process in which the CTRL+C is trapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ae834-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ae834-108">Return Value</span></span>  
  
|<span data-ttu-id="ae834-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ae834-109">HRESULT</span></span>|<span data-ttu-id="ae834-110">Description</span><span class="sxs-lookup"><span data-stu-id="ae834-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ae834-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ae834-111">S_OK</span></span>|<span data-ttu-id="ae834-112">Hata ayıklayıcı CTRL + C yakalamasını işleymeyecektir.</span><span class="sxs-lookup"><span data-stu-id="ae834-112">The debugger will handle the CTRL+C trap.</span></span>|  
|<span data-ttu-id="ae834-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="ae834-113">S_FALSE</span></span>|<span data-ttu-id="ae834-114">Hata ayıklayıcı CTRL + C yakalamasını işlemez.</span><span class="sxs-lookup"><span data-stu-id="ae834-114">The debugger will not handle the CTRL+C trap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae834-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ae834-115">Remarks</span></span>  

 <span data-ttu-id="ae834-116">İşlemdeki tüm uygulama etki alanları bu geri çağırma için durdurulur.</span><span class="sxs-lookup"><span data-stu-id="ae834-116">All application domains within the process are stopped for this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae834-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ae834-117">Requirements</span></span>  

 <span data-ttu-id="ae834-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae834-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae834-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ae834-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ae834-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ae834-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae834-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae834-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae834-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae834-122">See also</span></span>

- [<span data-ttu-id="ae834-123">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ae834-123">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
