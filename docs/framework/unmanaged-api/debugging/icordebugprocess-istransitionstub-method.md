---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugProcess:: ısgeçişli Tionstub yöntemi'
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
ms.openlocfilehash: 0da8527538c2573b1ec0d26f8711644fe8fcca2a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782019"
---
# <a name="icordebugprocessistransitionstub-method"></a><span data-ttu-id="1b1fc-103">ICorDebugProcess::IsTransitionStub Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1b1fc-103">ICorDebugProcess::IsTransitionStub Method</span></span>

<span data-ttu-id="1b1fc-104">Bir adresin, yönetilen koda geçişe neden olacak bir saplama içinde olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="1b1fc-104">Gets a value that indicates whether an address is inside a stub that will cause a transition to managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b1fc-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1b1fc-105">Syntax</span></span>  
  
```cpp  
HRESULT IsTransitionStub(  
    [in]  CORDB_ADDRESS address,  
    [out] BOOL *pbTransitionStub);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b1fc-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1b1fc-106">Parameters</span></span>  

 `address`  
 <span data-ttu-id="1b1fc-107">'ndaki `CORDB_ADDRESS` Söz konusu adresi belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="1b1fc-107">[in] A `CORDB_ADDRESS` value that specifies the address in question.</span></span>  
  
 `pbTransitionStub`  
 <span data-ttu-id="1b1fc-108">dışı `true` Belirtilen adres, yönetilen koda geçişe neden olacak bir saplama içindeyse bir Boole değeri işaretçisi; Aksi takdirde \* `pbTransitionStub` olur `false` .</span><span class="sxs-lookup"><span data-stu-id="1b1fc-108">[out] A pointer to a Boolean value that is `true` if the specified address is inside a stub that will cause a transition to managed code; otherwise \*`pbTransitionStub` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b1fc-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1b1fc-109">Remarks</span></span>  

 <span data-ttu-id="1b1fc-110">`IsTransitionStub`Yöntemi, yönetilmeyen atlama kodu tarafından, yönetilen Stepper üzerinde atlama denetimini ne zaman döneceğine karar vermek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1b1fc-110">The `IsTransitionStub` method can be used by unmanaged stepping code to decide when to return stepping control to the managed stepper.</span></span>  
  
 <span data-ttu-id="1b1fc-111">Taşınabilir çalıştırılabilir (PE) dosyasındaki bilgilere bakarak da geçiş saplamalarını de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1b1fc-111">You can also identity transition stubs by looking at information in the portable executable (PE) file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b1fc-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1b1fc-112">Requirements</span></span>  

 <span data-ttu-id="1b1fc-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b1fc-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b1fc-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1b1fc-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1b1fc-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1b1fc-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b1fc-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b1fc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
