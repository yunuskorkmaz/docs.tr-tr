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
ms.openlocfilehash: e06dc35998a2874ed1d2f76725078874817e94d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420101"
---
# <a name="icordebugprocessistransitionstub-method"></a><span data-ttu-id="01747-102">ICorDebugProcess::IsTransitionStub Yöntemi</span><span class="sxs-lookup"><span data-stu-id="01747-102">ICorDebugProcess::IsTransitionStub Method</span></span>
<span data-ttu-id="01747-103">Bir adresi yönetilen kod geçiş neden olacak bir saplama içinde olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="01747-103">Gets a value that indicates whether an address is inside a stub that will cause a transition to managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01747-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="01747-104">Syntax</span></span>  
  
```  
HRESULT IsTransitionStub(  
    [in]  CORDB_ADDRESS address,  
    [out] BOOL *pbTransitionStub);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="01747-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="01747-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="01747-106">[in] A `CORDB_ADDRESS` söz konusu adresini belirten değer.</span><span class="sxs-lookup"><span data-stu-id="01747-106">[in] A `CORDB_ADDRESS` value that specifies the address in question.</span></span>  
  
 `pbTransitionStub`  
 <span data-ttu-id="01747-107">[out] Boolean bir değer için bir işaretçi `true` yönetilen kod; geçiş neden olacak bir saplama içinde belirtilen adres ise, aksi takdirde \*`pbTransitionStub` olan `false`.</span><span class="sxs-lookup"><span data-stu-id="01747-107">[out] A pointer to a Boolean value that is `true` if the specified address is inside a stub that will cause a transition to managed code; otherwise \*`pbTransitionStub` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01747-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="01747-108">Remarks</span></span>  
 <span data-ttu-id="01747-109">`IsTransitionStub` Yöntemi yönetilen Adımlayıcı sürüm denetimi döndürmek karar vermenize olanak yönetilmeyen sürüm kodu tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="01747-109">The `IsTransitionStub` method can be used by unmanaged stepping code to decide when to return stepping control to the managed stepper.</span></span>  
  
 <span data-ttu-id="01747-110">Taşınabilir yürütülebilir (PE) dosyasındaki bilgilere bakarak kimlik geçiş saplamalar de gruplandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01747-110">You can also identity transition stubs by looking at information in the portable executable (PE) file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01747-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="01747-111">Requirements</span></span>  
 <span data-ttu-id="01747-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01747-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01747-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="01747-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="01747-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01747-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01747-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01747-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
