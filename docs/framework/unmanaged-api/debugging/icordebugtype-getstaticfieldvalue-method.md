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
ms.openlocfilehash: 95183701987d3ddec3835a17c5d256c25c2c4c64
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132074"
---
# <a name="icordebugtypegetstaticfieldvalue-method"></a><span data-ttu-id="cff37-102">ICorDebugType::GetStaticFieldValue Metodu</span><span class="sxs-lookup"><span data-stu-id="cff37-102">ICorDebugType::GetStaticFieldValue Method</span></span>
<span data-ttu-id="cff37-103">Belirtilen yığın çerçevesindeki belirtilen alan belirtecinin başvurduğu statik alanın değerini içeren bir ICorDebugValue nesnesine bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="cff37-103">Gets an interface pointer to an ICorDebugValue object that contains the value of the static field referenced by the specified field token in the specified stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cff37-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cff37-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef        fieldDef,  
    [in]  ICorDebugFrame    *pFrame,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cff37-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cff37-105">Parameters</span></span>  
 `fieldDef`  
 <span data-ttu-id="cff37-106">'ndaki Statik alanı belirten `mdFieldDef` belirteç.</span><span class="sxs-lookup"><span data-stu-id="cff37-106">[in] An `mdFieldDef` token that specifies the static field.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="cff37-107">'ndaki Yığın çerçevesini temsil eden bir ICorDebugFrame işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="cff37-107">[in] A pointer to an ICorDebugFrame that represents the stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="cff37-108">dışı Statik alanın değerini içeren `ICorDebugValue` adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cff37-108">[out] A pointer to the address of an `ICorDebugValue` that contains the value of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cff37-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cff37-109">Remarks</span></span>  
 <span data-ttu-id="cff37-110">`GetStaticFieldValue` yöntemi, [ICorDebugType:: GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) yönteminde gösterildiği gibi yalnızca tür element_type_class veya element_type_valuetype olduğunda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cff37-110">The `GetStaticFieldValue` method may be used only if the type is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, as indicated by the [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) method.</span></span>  
  
 <span data-ttu-id="cff37-111">Genel olmayan türler için, `GetStaticFieldValue` tarafından gerçekleştirilen işlem ICorDebugClass [:: GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md) ' ı [ICorDebugType:: GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md)tarafından döndürülen ICorDebugClass nesnesinde çağırma ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="cff37-111">For non-generic types, the operation performed by `GetStaticFieldValue` is identical to calling [ICorDebugClass::GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md) on the ICorDebugClass object that is returned by [ICorDebugType::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md).</span></span>  
  
 <span data-ttu-id="cff37-112">Genel türler için, statik bir alan değeri belirli bir örnek oluşturma ile göreli olur.</span><span class="sxs-lookup"><span data-stu-id="cff37-112">For generic types, a static field value will be relative to a particular instantiation.</span></span> <span data-ttu-id="cff37-113">Ayrıca, statik alan muhtemelen bir iş parçacığına, bir içeriğe veya bir uygulama etki alanına göreli olabilir, yığın çerçevesi hata ayıklayıcının doğru değeri belirlemesine yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="cff37-113">Also, if the static field could possibly be relative to a thread, a context, or an application domain, then the stack frame will help the debugger determine the proper value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cff37-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cff37-114">Remarks</span></span>  
 <span data-ttu-id="cff37-115">`GetStaticFieldValue`, yalnızca `ICorDebugType::GetType` çağrısı ELEMENT_TYPE_CLASS veya ELEMENT_TYPE_VALUETYPE değerini döndürdüğünde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cff37-115">`GetStaticFieldValue` can be used only when a call to `ICorDebugType::GetType` returns a value of ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cff37-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cff37-116">Requirements</span></span>  
 <span data-ttu-id="cff37-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cff37-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cff37-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cff37-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cff37-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cff37-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cff37-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cff37-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
