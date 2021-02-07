---
description: ': ICorDebugProcess:: ModifyLogSwitch yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 3c825d6c6b075139793b54526dca696c8fba35a4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746782"
---
# <a name="icordebugprocessmodifylogswitch-method"></a><span data-ttu-id="e1dc1-103">ICorDebugProcess::ModifyLogSwitch Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e1dc1-103">ICorDebugProcess::ModifyLogSwitch Method</span></span>

<span data-ttu-id="e1dc1-104">Belirtilen günlük anahtarının önem derecesini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e1dc1-104">Sets the severity level of the specified log switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1dc1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e1dc1-105">Syntax</span></span>  
  
```cpp  
HRESULT ModifyLogSwitch(  
    [in] WCHAR *pLogSwitchName,  
    [in] LONG  lLevel);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1dc1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e1dc1-106">Parameters</span></span>  

 `pLogSwitchName`  
 <span data-ttu-id="e1dc1-107">'ndaki Günlük anahtarının adını belirten bir dize işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e1dc1-107">[in] A pointer to a string that specifies the name of the log switch.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="e1dc1-108">'ndaki Belirtilen günlük anahtarı için ayarlanacak önem düzeyi.</span><span class="sxs-lookup"><span data-stu-id="e1dc1-108">[in] The severity level to be set for the specified log switch.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1dc1-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e1dc1-109">Remarks</span></span>  

 <span data-ttu-id="e1dc1-110">Bu yöntem yalnızca [ICorDebugManagedCallback:: CreateProcess](icordebugmanagedcallback-createprocess-method.md) geri çağırma işlemi gerçekleştirildikten sonra geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e1dc1-110">This method is valid only after the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1dc1-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e1dc1-111">Requirements</span></span>  

 <span data-ttu-id="e1dc1-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1dc1-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1dc1-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e1dc1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e1dc1-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e1dc1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1dc1-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1dc1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
