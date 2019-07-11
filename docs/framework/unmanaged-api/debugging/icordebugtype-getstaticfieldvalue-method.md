---
title: ICorDebugType::GetStaticFieldValue Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetStaticFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetStaticFieldValue
helpviewer_keywords:
- GetStaticFieldValue method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::GetStaticFieldValue method [.NET Framework debugging]
ms.assetid: 62eb5d55-53ee-4fb3-8d47-7b6c96808f9e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1054c7c977a487bb5a4bbf464322a65bcc039608
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755740"
---
# <a name="icordebugtypegetstaticfieldvalue-method"></a><span data-ttu-id="9399e-102">ICorDebugType::GetStaticFieldValue Metodu</span><span class="sxs-lookup"><span data-stu-id="9399e-102">ICorDebugType::GetStaticFieldValue Method</span></span>
<span data-ttu-id="9399e-103">Bir arabirim işaretçisi Icordebugvalue nesneye belirtilen alan tarafından başvurulan statik alanının değeri içeren belirtilen bir yığın çerçevesine belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="9399e-103">Gets an interface pointer to an ICorDebugValue object that contains the value of the static field referenced by the specified field token in the specified stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9399e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9399e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef        fieldDef,  
    [in]  ICorDebugFrame    *pFrame,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9399e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9399e-105">Parameters</span></span>  
 `fieldDef`  
 <span data-ttu-id="9399e-106">[in] Bir `mdFieldDef` statik alanı belirten belirteç.</span><span class="sxs-lookup"><span data-stu-id="9399e-106">[in] An `mdFieldDef` token that specifies the static field.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="9399e-107">[in] Yığın çerçevesini temsil eden bir Icordebugframe işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="9399e-107">[in] A pointer to an ICorDebugFrame that represents the stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="9399e-108">[out] Adresine bir işaretçi bir `ICorDebugValue` statik alanı değerini içeren.</span><span class="sxs-lookup"><span data-stu-id="9399e-108">[out] A pointer to the address of an `ICorDebugValue` that contains the value of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9399e-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9399e-109">Remarks</span></span>  
 <span data-ttu-id="9399e-110">`GetStaticFieldValue` Yöntemi kullanılabilir yalnızca tür ELEMENT_TYPE_CLASS veya ELEMENT_TYPE_VALUETYPE, ise tarafından belirtildiği şekilde [Icordebugtype::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9399e-110">The `GetStaticFieldValue` method may be used only if the type is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, as indicated by the [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) method.</span></span>  
  
 <span data-ttu-id="9399e-111">Genel olmayan türler için işlemin gerçekleştirilmesinden tarafından `GetStaticFieldValue` çağırmakla aynıdır [Icordebugclass::getstaticfieldvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md) tarafından döndürülen Icordebugclass nesne [Icordebugtype::getclass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md).</span><span class="sxs-lookup"><span data-stu-id="9399e-111">For non-generic types, the operation performed by `GetStaticFieldValue` is identical to calling [ICorDebugClass::GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md) on the ICorDebugClass object that is returned by [ICorDebugType::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md).</span></span>  
  
 <span data-ttu-id="9399e-112">Genel türler için statik alan değerine göre belirli bir örneğini oluşturmada olacaktır.</span><span class="sxs-lookup"><span data-stu-id="9399e-112">For generic types, a static field value will be relative to a particular instantiation.</span></span> <span data-ttu-id="9399e-113">Ayrıca, statik alan büyük olasılıkla bir iş parçacığı, bir bağlamı veya uygulama etki alanı göreli olabilir, yığın çerçevesinin uygun değeri belirlemek hata ayıklayıcı yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="9399e-113">Also, if the static field could possibly be relative to a thread, a context, or an application domain, then the stack frame will help the debugger determine the proper value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9399e-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9399e-114">Remarks</span></span>  
 <span data-ttu-id="9399e-115">`GetStaticFieldValue` yalnızca bir çağrı kullanılabilir `ICorDebugType::GetType` ELEMENT_TYPE_CLASS veya ELEMENT_TYPE_VALUETYPE değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="9399e-115">`GetStaticFieldValue` can be used only when a call to `ICorDebugType::GetType` returns a value of ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9399e-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9399e-116">Requirements</span></span>  
 <span data-ttu-id="9399e-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9399e-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9399e-118">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9399e-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9399e-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9399e-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9399e-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9399e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
