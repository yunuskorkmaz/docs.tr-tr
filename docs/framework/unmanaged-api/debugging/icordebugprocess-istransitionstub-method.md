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
ms.openlocfilehash: 852c77be0dc8ef91933bacbbd3d6b3f5a69ae8c8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139394"
---
# <a name="icordebugprocessistransitionstub-method"></a><span data-ttu-id="36a06-102">ICorDebugProcess::IsTransitionStub Yöntemi</span><span class="sxs-lookup"><span data-stu-id="36a06-102">ICorDebugProcess::IsTransitionStub Method</span></span>
<span data-ttu-id="36a06-103">Bir adresin, yönetilen koda geçişe neden olacak bir saplama içinde olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="36a06-103">Gets a value that indicates whether an address is inside a stub that will cause a transition to managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36a06-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="36a06-104">Syntax</span></span>  
  
```cpp  
HRESULT IsTransitionStub(  
    [in]  CORDB_ADDRESS address,  
    [out] BOOL *pbTransitionStub);  
```  
  
## <a name="parameters"></a><span data-ttu-id="36a06-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="36a06-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="36a06-106">'ndaki Söz konusu adresi belirten bir `CORDB_ADDRESS` değeri.</span><span class="sxs-lookup"><span data-stu-id="36a06-106">[in] A `CORDB_ADDRESS` value that specifies the address in question.</span></span>  
  
 `pbTransitionStub`  
 <span data-ttu-id="36a06-107">dışı Belirtilen adres, yönetilen koda geçişe neden olacak bir saplama içindeyse, `true` Boole değeri işaretçisi; Aksi halde \*`pbTransitionStub` `false`.</span><span class="sxs-lookup"><span data-stu-id="36a06-107">[out] A pointer to a Boolean value that is `true` if the specified address is inside a stub that will cause a transition to managed code; otherwise \*`pbTransitionStub` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36a06-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="36a06-108">Remarks</span></span>  
 <span data-ttu-id="36a06-109">`IsTransitionStub` yöntemi, yönetilmeyen atlama kodu tarafından, yönetilen Stepper üzerinde atlama denetimini ne zaman döneceğine karar vermek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="36a06-109">The `IsTransitionStub` method can be used by unmanaged stepping code to decide when to return stepping control to the managed stepper.</span></span>  
  
 <span data-ttu-id="36a06-110">Taşınabilir çalıştırılabilir (PE) dosyasındaki bilgilere bakarak da geçiş saplamalarını de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36a06-110">You can also identity transition stubs by looking at information in the portable executable (PE) file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36a06-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="36a06-111">Requirements</span></span>  
 <span data-ttu-id="36a06-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36a06-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36a06-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="36a06-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="36a06-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="36a06-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36a06-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36a06-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
