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
ms.openlocfilehash: c9375854b45432eafb6cc706a1a62f5424e0fee8
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210494"
---
# <a name="icordebugprocessmodifylogswitch-method"></a><span data-ttu-id="cf852-102">ICorDebugProcess::ModifyLogSwitch Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cf852-102">ICorDebugProcess::ModifyLogSwitch Method</span></span>
<span data-ttu-id="cf852-103">Belirtilen günlük anahtarının önem derecesini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="cf852-103">Sets the severity level of the specified log switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf852-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cf852-104">Syntax</span></span>  
  
```cpp  
HRESULT ModifyLogSwitch(  
    [in] WCHAR *pLogSwitchName,  
    [in] LONG  lLevel);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf852-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cf852-105">Parameters</span></span>  
 `pLogSwitchName`  
 <span data-ttu-id="cf852-106">'ndaki Günlük anahtarının adını belirten bir dize işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="cf852-106">[in] A pointer to a string that specifies the name of the log switch.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="cf852-107">'ndaki Belirtilen günlük anahtarı için ayarlanacak önem düzeyi.</span><span class="sxs-lookup"><span data-stu-id="cf852-107">[in] The severity level to be set for the specified log switch.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf852-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cf852-108">Remarks</span></span>  
 <span data-ttu-id="cf852-109">Bu yöntem yalnızca [ICorDebugManagedCallback:: CreateProcess](icordebugmanagedcallback-createprocess-method.md) geri çağırma işlemi gerçekleştirildikten sonra geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="cf852-109">This method is valid only after the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf852-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cf852-110">Requirements</span></span>  
 <span data-ttu-id="cf852-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf852-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf852-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cf852-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cf852-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cf852-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cf852-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf852-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
