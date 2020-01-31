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
ms.openlocfilehash: 27e13e298c1be61018a92e53a0ee82c786729c7d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792579"
---
# <a name="icordebugprocessmodifylogswitch-method"></a><span data-ttu-id="ee132-102">ICorDebugProcess::ModifyLogSwitch Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ee132-102">ICorDebugProcess::ModifyLogSwitch Method</span></span>
<span data-ttu-id="ee132-103">Belirtilen günlük anahtarının önem derecesini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ee132-103">Sets the severity level of the specified log switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee132-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ee132-104">Syntax</span></span>  
  
```cpp  
HRESULT ModifyLogSwitch(  
    [in] WCHAR *pLogSwitchName,  
    [in] LONG  lLevel);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee132-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ee132-105">Parameters</span></span>  
 `pLogSwitchName`  
 <span data-ttu-id="ee132-106">'ndaki Günlük anahtarının adını belirten bir dize işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="ee132-106">[in] A pointer to a string that specifies the name of the log switch.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="ee132-107">'ndaki Belirtilen günlük anahtarı için ayarlanacak önem düzeyi.</span><span class="sxs-lookup"><span data-stu-id="ee132-107">[in] The severity level to be set for the specified log switch.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee132-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ee132-108">Remarks</span></span>  
 <span data-ttu-id="ee132-109">Bu yöntem yalnızca [ICorDebugManagedCallback:: CreateProcess](icordebugmanagedcallback-createprocess-method.md) geri çağırma işlemi gerçekleştirildikten sonra geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="ee132-109">This method is valid only after the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee132-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ee132-110">Requirements</span></span>  
 <span data-ttu-id="ee132-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee132-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee132-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ee132-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ee132-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ee132-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee132-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee132-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
