---
title: ICorDebugProcess::ModifyLogSwitch Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ModifyLogSwitch
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ModifyLogSwitch
helpviewer_keywords:
- ICorDebugProcess::ModifyLogSwitch method [.NET Framework debugging]
- ModifyLogSwitch method [.NET Framework debugging]
ms.assetid: 5fd30875-555e-4e96-877b-5dd266cde7c4
topic_type:
- apiref
ms.openlocfilehash: 86b8737577bdb5f61f1061cb217620fae03ebd0c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139378"
---
# <a name="icordebugprocessmodifylogswitch-method"></a><span data-ttu-id="2f3da-102">ICorDebugProcess::ModifyLogSwitch Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2f3da-102">ICorDebugProcess::ModifyLogSwitch Method</span></span>
<span data-ttu-id="2f3da-103">Belirtilen günlük anahtarının önem derecesini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2f3da-103">Sets the severity level of the specified log switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f3da-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2f3da-104">Syntax</span></span>  
  
```cpp  
HRESULT ModifyLogSwitch(  
    [in] WCHAR *pLogSwitchName,  
    [in] LONG  lLevel);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f3da-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2f3da-105">Parameters</span></span>  
 `pLogSwitchName`  
 <span data-ttu-id="2f3da-106">'ndaki Günlük anahtarının adını belirten bir dize işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="2f3da-106">[in] A pointer to a string that specifies the name of the log switch.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="2f3da-107">'ndaki Belirtilen günlük anahtarı için ayarlanacak önem düzeyi.</span><span class="sxs-lookup"><span data-stu-id="2f3da-107">[in] The severity level to be set for the specified log switch.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f3da-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2f3da-108">Remarks</span></span>  
 <span data-ttu-id="2f3da-109">Bu yöntem yalnızca [ICorDebugManagedCallback:: CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) geri çağırma işlemi gerçekleştirildikten sonra geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="2f3da-109">This method is valid only after the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f3da-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2f3da-110">Requirements</span></span>  
 <span data-ttu-id="2f3da-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f3da-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f3da-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2f3da-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2f3da-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2f3da-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f3da-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f3da-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
