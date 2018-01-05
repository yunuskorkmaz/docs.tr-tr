---
title: "ICorDebugProcess::IsTransitionStub Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.IsTransitionStub
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::IsTransitionStub
helpviewer_keywords:
- ICorDebugProcess::IsTransitionStub method [.NET Framework debugging]
- IsTransitionStub method [.NET Framework debugging]
ms.assetid: f7653317-7e48-4163-be03-f50f1a4b0f70
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9fe38cf5f53c2514b845238c1d52fa12df526fdd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessistransitionstub-method"></a><span data-ttu-id="d3e45-102">ICorDebugProcess::IsTransitionStub Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d3e45-102">ICorDebugProcess::IsTransitionStub Method</span></span>
<span data-ttu-id="d3e45-103">Bir adresi yönetilen kod geçiş neden olacak bir saplama içinde olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="d3e45-103">Gets a value that indicates whether an address is inside a stub that will cause a transition to managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3e45-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d3e45-104">Syntax</span></span>  
  
```  
HRESULT IsTransitionStub(  
    [in]  CORDB_ADDRESS address,  
    [out] BOOL *pbTransitionStub);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d3e45-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d3e45-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="d3e45-106">[in] A `CORDB_ADDRESS` söz konusu adresini belirten değer.</span><span class="sxs-lookup"><span data-stu-id="d3e45-106">[in] A `CORDB_ADDRESS` value that specifies the address in question.</span></span>  
  
 `pbTransitionStub`  
 <span data-ttu-id="d3e45-107">[out] Boolean bir değer için bir işaretçi `true` yönetilen kod; geçiş neden olacak bir saplama içinde belirtilen adres ise, aksi takdirde *`pbTransitionStub` olan `false`.</span><span class="sxs-lookup"><span data-stu-id="d3e45-107">[out] A pointer to a Boolean value that is `true` if the specified address is inside a stub that will cause a transition to managed code; otherwise *`pbTransitionStub` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3e45-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d3e45-108">Remarks</span></span>  
 <span data-ttu-id="d3e45-109">`IsTransitionStub` Yöntemi yönetilen Adımlayıcı sürüm denetimi döndürmek karar vermenize olanak yönetilmeyen sürüm kodu tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d3e45-109">The `IsTransitionStub` method can be used by unmanaged stepping code to decide when to return stepping control to the managed stepper.</span></span>  
  
 <span data-ttu-id="d3e45-110">Taşınabilir yürütülebilir (PE) dosyasındaki bilgilere bakarak kimlik geçiş saplamalar de gruplandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3e45-110">You can also identity transition stubs by looking at information in the portable executable (PE) file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3e45-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d3e45-111">Requirements</span></span>  
 <span data-ttu-id="d3e45-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3e45-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3e45-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d3e45-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d3e45-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d3e45-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3e45-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3e45-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
