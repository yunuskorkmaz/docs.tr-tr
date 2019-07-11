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
ms.openlocfilehash: 96db1ca115ffed47b5eb8eadd9c3d2f620060c4a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755453"
---
# <a name="icordebugprocessmodifylogswitch-method"></a><span data-ttu-id="909a5-102">ICorDebugProcess::ModifyLogSwitch Yöntemi</span><span class="sxs-lookup"><span data-stu-id="909a5-102">ICorDebugProcess::ModifyLogSwitch Method</span></span>
<span data-ttu-id="909a5-103">Belirtilen log anahtarı önem düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="909a5-103">Sets the severity level of the specified log switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="909a5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="909a5-104">Syntax</span></span>  
  
```cpp  
HRESULT ModifyLogSwitch(  
    [in] WCHAR *pLogSwitchName,  
    [in] LONG  lLevel);  
```  
  
## <a name="parameters"></a><span data-ttu-id="909a5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="909a5-105">Parameters</span></span>  
 `pLogSwitchName`  
 <span data-ttu-id="909a5-106">[in] Log anahtarı adını belirten bir dize işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="909a5-106">[in] A pointer to a string that specifies the name of the log switch.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="909a5-107">[in] Belirtilen log anahtarı için ayarlanacak önem düzeyi.</span><span class="sxs-lookup"><span data-stu-id="909a5-107">[in] The severity level to be set for the specified log switch.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="909a5-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="909a5-108">Remarks</span></span>  
 <span data-ttu-id="909a5-109">Bu yöntem yalnızca geçerli [Icordebugmanagedcallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) geri çağırma oluştu.</span><span class="sxs-lookup"><span data-stu-id="909a5-109">This method is valid only after the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="909a5-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="909a5-110">Requirements</span></span>  
 <span data-ttu-id="909a5-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="909a5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="909a5-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="909a5-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="909a5-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="909a5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="909a5-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="909a5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
