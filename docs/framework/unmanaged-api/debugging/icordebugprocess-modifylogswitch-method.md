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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4b1c85499e5269027da2c2a01ab67aab2c5da626
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775556"
---
# <a name="icordebugprocessmodifylogswitch-method"></a><span data-ttu-id="222ff-102">ICorDebugProcess::ModifyLogSwitch Yöntemi</span><span class="sxs-lookup"><span data-stu-id="222ff-102">ICorDebugProcess::ModifyLogSwitch Method</span></span>
<span data-ttu-id="222ff-103">Belirtilen log anahtarı önem düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="222ff-103">Sets the severity level of the specified log switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="222ff-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="222ff-104">Syntax</span></span>  
  
```  
HRESULT ModifyLogSwitch(  
    [in] WCHAR *pLogSwitchName,  
    [in] LONG  lLevel);  
```  
  
## <a name="parameters"></a><span data-ttu-id="222ff-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="222ff-105">Parameters</span></span>  
 `pLogSwitchName`  
 <span data-ttu-id="222ff-106">[in] Log anahtarı adını belirten bir dize işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="222ff-106">[in] A pointer to a string that specifies the name of the log switch.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="222ff-107">[in] Belirtilen log anahtarı için ayarlanacak önem düzeyi.</span><span class="sxs-lookup"><span data-stu-id="222ff-107">[in] The severity level to be set for the specified log switch.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="222ff-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="222ff-108">Remarks</span></span>  
 <span data-ttu-id="222ff-109">Bu yöntem yalnızca geçerli [Icordebugmanagedcallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) geri çağırma oluştu.</span><span class="sxs-lookup"><span data-stu-id="222ff-109">This method is valid only after the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="222ff-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="222ff-110">Requirements</span></span>  
 <span data-ttu-id="222ff-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="222ff-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="222ff-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="222ff-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="222ff-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="222ff-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="222ff-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="222ff-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
