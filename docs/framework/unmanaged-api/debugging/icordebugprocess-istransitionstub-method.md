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
ms.openlocfilehash: 2996c219ccf4e975c45fb531807abc4a608bae73
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95694782"
---
# <a name="icordebugprocessistransitionstub-method"></a><span data-ttu-id="d325a-102">ICorDebugProcess::IsTransitionStub Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d325a-102">ICorDebugProcess::IsTransitionStub Method</span></span>

<span data-ttu-id="d325a-103">Bir adresin, yönetilen koda geçişe neden olacak bir saplama içinde olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="d325a-103">Gets a value that indicates whether an address is inside a stub that will cause a transition to managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d325a-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="d325a-104">Syntax</span></span>  
  
```cpp  
HRESULT IsTransitionStub(  
    [in]  CORDB_ADDRESS address,  
    [out] BOOL *pbTransitionStub);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d325a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d325a-105">Parameters</span></span>  

 `address`  
 <span data-ttu-id="d325a-106">'ndaki `CORDB_ADDRESS` Söz konusu adresi belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="d325a-106">[in] A `CORDB_ADDRESS` value that specifies the address in question.</span></span>  
  
 `pbTransitionStub`  
 <span data-ttu-id="d325a-107">dışı `true` Belirtilen adres, yönetilen koda geçişe neden olacak bir saplama içindeyse bir Boole değeri işaretçisi; Aksi takdirde \* `pbTransitionStub` olur `false` .</span><span class="sxs-lookup"><span data-stu-id="d325a-107">[out] A pointer to a Boolean value that is `true` if the specified address is inside a stub that will cause a transition to managed code; otherwise \*`pbTransitionStub` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d325a-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d325a-108">Remarks</span></span>  

 <span data-ttu-id="d325a-109">`IsTransitionStub`Yöntemi, yönetilmeyen atlama kodu tarafından, yönetilen Stepper üzerinde atlama denetimini ne zaman döneceğine karar vermek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d325a-109">The `IsTransitionStub` method can be used by unmanaged stepping code to decide when to return stepping control to the managed stepper.</span></span>  
  
 <span data-ttu-id="d325a-110">Taşınabilir çalıştırılabilir (PE) dosyasındaki bilgilere bakarak da geçiş saplamalarını de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d325a-110">You can also identity transition stubs by looking at information in the portable executable (PE) file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d325a-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d325a-111">Requirements</span></span>  

 <span data-ttu-id="d325a-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d325a-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d325a-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d325a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d325a-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d325a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d325a-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d325a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
