---
title: ICorDebugClass::GetStaticFieldValue Yöntemi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6b67f5ec233679461f61715d7562b47c2a195fb8
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471634"
---
# <a name="icordebugclassgetstaticfieldvalue-method"></a><span data-ttu-id="bb033-102">ICorDebugClass::GetStaticFieldValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bb033-102">ICorDebugClass::GetStaticFieldValue Method</span></span>
<span data-ttu-id="bb033-103">Belirtilen statik alan değerini alır.</span><span class="sxs-lookup"><span data-stu-id="bb033-103">Gets the value of the specified static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb033-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bb033-104">Syntax</span></span>  
  
```  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef         fieldDef,  
    [in]  ICorDebugFrame     *pFrame,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb033-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bb033-105">Parameters</span></span>  
 `fieldDef`  
 <span data-ttu-id="bb033-106">[in] Bir alan `Def` alınacak alana başvuran bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="bb033-106">[in] A field `Def` token that references the field to be retrieved.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="bb033-107">[in] İş parçacığı, içerik ve uygulama etki alanı statikler arasında ayırt etmek için kullanılacak çerçeveyi temsil eden bir Icordebugframe nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="bb033-107">[in] A pointer to an ICorDebugFrame object that represents the frame to be used to disambiguate among thread, context, or application domain statics.</span></span>  
  
 <span data-ttu-id="bb033-108">Statik alan bir iş parçacığı, bir bağlam veya bir uygulama etki alanına göre çerçeve uygun değeri belirler.</span><span class="sxs-lookup"><span data-stu-id="bb033-108">If the static field is relative to a thread, a context, or an application domain, the frame will determine the proper value.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="bb033-109">[out] Statik alan değerini temsil eden bir Icordebugvalue nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bb033-109">[out] A pointer to the address of an ICorDebugValue object that represents the value of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb033-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bb033-110">Remarks</span></span>  
 <span data-ttu-id="bb033-111">Parametreli türler için belirli bir örneğini oluşturmada göreli statik alan değerdir.</span><span class="sxs-lookup"><span data-stu-id="bb033-111">For parameterized types, the value of a static field is relative to the particular instantiation.</span></span> <span data-ttu-id="bb033-112">Bu nedenle, sınıf oluşturucusu tür parametrelerinin uzun sürerse <xref:System.Type>, çağrı [Icordebugtype::getstaticfieldvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md) yerine `ICorDebugClass::GetStaticFieldValue`.</span><span class="sxs-lookup"><span data-stu-id="bb033-112">Therefore, if the class constructor takes parameters of type <xref:System.Type>, call [ICorDebugType::GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md) instead of `ICorDebugClass::GetStaticFieldValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb033-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bb033-113">Requirements</span></span>  
 <span data-ttu-id="bb033-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb033-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb033-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bb033-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bb033-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bb033-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb033-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb033-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
