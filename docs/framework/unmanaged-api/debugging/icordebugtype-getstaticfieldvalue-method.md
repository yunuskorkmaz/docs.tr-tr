---
description: ': ICorDebugType:: GetStaticFieldValue metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 378c72f24fedd76f40704ff684781bed124055bb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658236"
---
# <a name="icordebugtypegetstaticfieldvalue-method"></a><span data-ttu-id="5deb2-103">ICorDebugType::GetStaticFieldValue Metodu</span><span class="sxs-lookup"><span data-stu-id="5deb2-103">ICorDebugType::GetStaticFieldValue Method</span></span>

<span data-ttu-id="5deb2-104">Belirtilen yığın çerçevesindeki belirtilen alan belirtecinin başvurduğu statik alanın değerini içeren bir ICorDebugValue nesnesine bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="5deb2-104">Gets an interface pointer to an ICorDebugValue object that contains the value of the static field referenced by the specified field token in the specified stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5deb2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5deb2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef        fieldDef,  
    [in]  ICorDebugFrame    *pFrame,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5deb2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5deb2-106">Parameters</span></span>  

 `fieldDef`  
 <span data-ttu-id="5deb2-107">'ndaki `mdFieldDef` Statik alanı belirten bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="5deb2-107">[in] An `mdFieldDef` token that specifies the static field.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="5deb2-108">'ndaki Yığın çerçevesini temsil eden bir ICorDebugFrame işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="5deb2-108">[in] A pointer to an ICorDebugFrame that represents the stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="5deb2-109">dışı `ICorDebugValue` Statik alanın değerini içeren adresinin bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="5deb2-109">[out] A pointer to the address of an `ICorDebugValue` that contains the value of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5deb2-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5deb2-110">Remarks</span></span>  

 <span data-ttu-id="5deb2-111">`GetStaticFieldValue`Yöntemi, [ICorDebugType:: GetType](icordebugtype-gettype-method.md) yönteminde gösterildiği gibi, yalnızca tür element_type_class veya element_type_valuetype olduğunda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5deb2-111">The `GetStaticFieldValue` method may be used only if the type is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, as indicated by the [ICorDebugType::GetType](icordebugtype-gettype-method.md) method.</span></span>  
  
 <span data-ttu-id="5deb2-112">Genel olmayan türler için, tarafından gerçekleştirilen işlem ICorDebugClass `GetStaticFieldValue` [:: GetStaticFieldValue](icordebugclass-getstaticfieldvalue-method.md) ' ı [ICorDebugType:: GetClass](icordebugtype-getclass-method.md)tarafından döndürülen ICorDebugClass nesnesinde çağırmaya eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="5deb2-112">For non-generic types, the operation performed by `GetStaticFieldValue` is identical to calling [ICorDebugClass::GetStaticFieldValue](icordebugclass-getstaticfieldvalue-method.md) on the ICorDebugClass object that is returned by [ICorDebugType::GetClass](icordebugtype-getclass-method.md).</span></span>  
  
 <span data-ttu-id="5deb2-113">Genel türler için, statik bir alan değeri belirli bir örnek oluşturma ile göreli olur.</span><span class="sxs-lookup"><span data-stu-id="5deb2-113">For generic types, a static field value will be relative to a particular instantiation.</span></span> <span data-ttu-id="5deb2-114">Ayrıca, statik alan muhtemelen bir iş parçacığına, bir içeriğe veya bir uygulama etki alanına göreli olabilir, yığın çerçevesi hata ayıklayıcının doğru değeri belirlemesine yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="5deb2-114">Also, if the static field could possibly be relative to a thread, a context, or an application domain, then the stack frame will help the debugger determine the proper value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5deb2-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5deb2-115">Remarks</span></span>  

 <span data-ttu-id="5deb2-116">`GetStaticFieldValue` yalnızca bir çağrı `ICorDebugType::GetType` element_type_class veya element_type_valuetype değerini döndürdüğünde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5deb2-116">`GetStaticFieldValue` can be used only when a call to `ICorDebugType::GetType` returns a value of ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5deb2-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5deb2-117">Requirements</span></span>  

 <span data-ttu-id="5deb2-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5deb2-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5deb2-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5deb2-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5deb2-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5deb2-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5deb2-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5deb2-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
