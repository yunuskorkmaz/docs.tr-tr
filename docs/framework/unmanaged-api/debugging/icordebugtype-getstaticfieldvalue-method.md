---
title: ICorDebugType::GetStaticFieldValue Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugType.GetStaticFieldValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType::GetStaticFieldValue
helpviewer_keywords:
- GetStaticFieldValue method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::GetStaticFieldValue method [.NET Framework debugging]
ms.assetid: 62eb5d55-53ee-4fb3-8d47-7b6c96808f9e
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 34a37ef9a28dd0e6325db9bee61146f14d4638a6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugtypegetstaticfieldvalue-method"></a><span data-ttu-id="ecdb0-102">ICorDebugType::GetStaticFieldValue Metodu</span><span class="sxs-lookup"><span data-stu-id="ecdb0-102">ICorDebugType::GetStaticFieldValue Method</span></span>
<span data-ttu-id="ecdb0-103">Arabirim işaretçisi belirtilen alanı tarafından başvurulan statik alanın değerini içeren bir Icordebugvalue nesne için belirtilen yığın çerçevesinde belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="ecdb0-103">Gets an interface pointer to an ICorDebugValue object that contains the value of the static field referenced by the specified field token in the specified stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecdb0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ecdb0-104">Syntax</span></span>  
  
```  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef        fieldDef,  
    [in]  ICorDebugFrame    *pFrame,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ecdb0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ecdb0-105">Parameters</span></span>  
 `fieldDef`  
 <span data-ttu-id="ecdb0-106">[in] Bir `mdFieldDef` statik alan belirtir belirteci.</span><span class="sxs-lookup"><span data-stu-id="ecdb0-106">[in] An `mdFieldDef` token that specifies the static field.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="ecdb0-107">[in] Yığın çerçevesi temsil eden bir Icordebugframe gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ecdb0-107">[in] A pointer to an ICorDebugFrame that represents the stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="ecdb0-108">[out] Adresine bir işaretçi bir `ICorDebugValue` statik alanın değerini içerir.</span><span class="sxs-lookup"><span data-stu-id="ecdb0-108">[out] A pointer to the address of an `ICorDebugValue` that contains the value of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ecdb0-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ecdb0-109">Remarks</span></span>  
 <span data-ttu-id="ecdb0-110">`GetStaticFieldValue` Yöntemi yalnızca tür ELEMENT_TYPE_CLASS veya ELEMENT_TYPE_VALUETYPE, ise belirttiği olarak kullanılabilir [Icordebugtype::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ecdb0-110">The `GetStaticFieldValue` method may be used only if the type is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, as indicated by the [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) method.</span></span>  
  
 <span data-ttu-id="ecdb0-111">Genel olmayan türlerinde işlemi tarafından gerçekleştirilen `GetStaticFieldValue` için arama aynıdır [Icordebugclass::getstaticfieldvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md) tarafından döndürülen Icordebugclass nesne üzerinde [Icordebugtype::getclass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md).</span><span class="sxs-lookup"><span data-stu-id="ecdb0-111">For non-generic types, the operation performed by `GetStaticFieldValue` is identical to calling [ICorDebugClass::GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md) on the ICorDebugClass object that is returned by [ICorDebugType::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md).</span></span>  
  
 <span data-ttu-id="ecdb0-112">Genel türler için bir statik alan değeri göre belirli bir örnek oluşturma olacaktır.</span><span class="sxs-lookup"><span data-stu-id="ecdb0-112">For generic types, a static field value will be relative to a particular instantiation.</span></span> <span data-ttu-id="ecdb0-113">Ayrıca, statik alanı, büyük olasılıkla bir iş parçacığı, bir içerik veya uygulama etki alanı göreli olabilir, yığın çerçevesi uygun değeri belirlemek hata ayıklayıcı yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="ecdb0-113">Also, if the static field could possibly be relative to a thread, a context, or an application domain, then the stack frame will help the debugger determine the proper value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ecdb0-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ecdb0-114">Remarks</span></span>  
 <span data-ttu-id="ecdb0-115">`GetStaticFieldValue`sadece bir çağrı sırasında kullanılan `ICorDebugType::GetType` ELEMENT_TYPE_CLASS veya ELEMENT_TYPE_VALUETYPE değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="ecdb0-115">`GetStaticFieldValue` can be used only when a call to `ICorDebugType::GetType` returns a value of ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecdb0-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ecdb0-116">Requirements</span></span>  
 <span data-ttu-id="ecdb0-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecdb0-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecdb0-118">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ecdb0-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ecdb0-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ecdb0-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ecdb0-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecdb0-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
