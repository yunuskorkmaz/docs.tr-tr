---
title: ICorDebugClass::GetStaticFieldValue Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugClass.GetStaticFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass::GetStaticFieldValue
helpviewer_keywords:
- GetStaticFieldValue method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetStaticFieldValue method [.NET Framework debugging]
ms.assetid: 56e718b4-fabd-418b-a5b3-3cc33c745683
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 21176eb73b3655fe8bd4b2187b6da49a3c31bd82
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugclassgetstaticfieldvalue-method"></a><span data-ttu-id="d6c22-102">ICorDebugClass::GetStaticFieldValue Metodu</span><span class="sxs-lookup"><span data-stu-id="d6c22-102">ICorDebugClass::GetStaticFieldValue Method</span></span>
<span data-ttu-id="d6c22-103">Belirtilen statik alanın değerini alır.</span><span class="sxs-lookup"><span data-stu-id="d6c22-103">Gets the value of the specified static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6c22-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d6c22-104">Syntax</span></span>  
  
```  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef         fieldDef,  
    [in]  ICorDebugFrame     *pFrame,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d6c22-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d6c22-105">Parameters</span></span>  
 `fieldDef`  
 <span data-ttu-id="d6c22-106">[in] Bir alan `Def` alınacak alanın başvuran belirteci.</span><span class="sxs-lookup"><span data-stu-id="d6c22-106">[in] A field `Def` token that references the field to be retrieved.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="d6c22-107">[in] Bir işaretçi Icordebugframe nesneye iş parçacığı, bağlamı veya uygulama etki alanı istatistikleri arasında belirsizliğini ortadan kaldırmak için kullanılacak çerçeveyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d6c22-107">[in] A pointer to an ICorDebugFrame object that represents the frame to be used to disambiguate among thread, context, or application domain statics.</span></span>  
  
 <span data-ttu-id="d6c22-108">Statik alan bir iş parçacığı, bir içerik veya uygulama etki alanı göreli ise, çerçeve uygun değeri belirler.</span><span class="sxs-lookup"><span data-stu-id="d6c22-108">If the static field is relative to a thread, a context, or an application domain, the frame will determine the proper value.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="d6c22-109">[out] Bir işaretçi adresine Icordebugvalue nesnenin statik alanın değerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d6c22-109">[out] A pointer to the address of an ICorDebugValue object that represents the value of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6c22-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d6c22-110">Remarks</span></span>  
 <span data-ttu-id="d6c22-111">Parametreli türler için statik bir alana göre belirli örneklemesi değeridir.</span><span class="sxs-lookup"><span data-stu-id="d6c22-111">For parameterized types, the value of a static field is relative to the particular instantiation.</span></span> <span data-ttu-id="d6c22-112">Bu nedenle, sınıf oluşturucu türünde parametre sürerse <xref:System.Type>, çağrı [Icordebugtype::getstaticfieldvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md) yerine `ICorDebugClass::GetStaticFieldValue`.</span><span class="sxs-lookup"><span data-stu-id="d6c22-112">Therefore, if the class constructor takes parameters of type <xref:System.Type>, call [ICorDebugType::GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md) instead of `ICorDebugClass::GetStaticFieldValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6c22-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d6c22-113">Requirements</span></span>  
 <span data-ttu-id="d6c22-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6c22-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6c22-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d6c22-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d6c22-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d6c22-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6c22-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6c22-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
