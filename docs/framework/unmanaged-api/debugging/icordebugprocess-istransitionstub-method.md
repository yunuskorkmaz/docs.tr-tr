---
title: ICorDebugProcess::IsTransitionStub Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.IsTransitionStub
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::IsTransitionStub
helpviewer_keywords:
- ICorDebugProcess::IsTransitionStub method [.NET Framework debugging]
- IsTransitionStub method [.NET Framework debugging]
ms.assetid: f7653317-7e48-4163-be03-f50f1a4b0f70
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1ec29aa748c437199434fa1394e1a00c82154447
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766875"
---
# <a name="icordebugprocessistransitionstub-method"></a><span data-ttu-id="d6db5-102">ICorDebugProcess::IsTransitionStub Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d6db5-102">ICorDebugProcess::IsTransitionStub Method</span></span>
<span data-ttu-id="d6db5-103">Adres yönetilen koda geçiş neden olacak bir saplama içinde olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="d6db5-103">Gets a value that indicates whether an address is inside a stub that will cause a transition to managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6db5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d6db5-104">Syntax</span></span>  
  
```cpp  
HRESULT IsTransitionStub(  
    [in]  CORDB_ADDRESS address,  
    [out] BOOL *pbTransitionStub);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6db5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d6db5-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="d6db5-106">[in] A `CORDB_ADDRESS` söz konusu adresini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="d6db5-106">[in] A `CORDB_ADDRESS` value that specifies the address in question.</span></span>  
  
 `pbTransitionStub`  
 <span data-ttu-id="d6db5-107">[out] Boolean bir değer için bir işaretçi `true` yönetilen kod; geçiş neden olacak bir saplama içinde belirtilen adresi ise, aksi takdirde \*`pbTransitionStub` olduğu `false`.</span><span class="sxs-lookup"><span data-stu-id="d6db5-107">[out] A pointer to a Boolean value that is `true` if the specified address is inside a stub that will cause a transition to managed code; otherwise \*`pbTransitionStub` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6db5-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d6db5-108">Remarks</span></span>  
 <span data-ttu-id="d6db5-109">`IsTransitionStub` Yöntemi sürüm denetimi için yönetilen Adımlayıcı döndürmek ne zaman karar için yönetilmeyen bir atlama kodu tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d6db5-109">The `IsTransitionStub` method can be used by unmanaged stepping code to decide when to return stepping control to the managed stepper.</span></span>  
  
 <span data-ttu-id="d6db5-110">Kimlik geçişi saptamalar da taşınabilir yürütülebilir (PE) dosya bilgileri bakarak yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d6db5-110">You can also identity transition stubs by looking at information in the portable executable (PE) file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6db5-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d6db5-111">Requirements</span></span>  
 <span data-ttu-id="d6db5-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6db5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6db5-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d6db5-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d6db5-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d6db5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6db5-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6db5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
