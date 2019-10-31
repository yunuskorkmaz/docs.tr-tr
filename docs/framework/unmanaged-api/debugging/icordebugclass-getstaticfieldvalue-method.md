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
ms.openlocfilehash: 867db3325f9b18b31f66429d01ea02be3603c0f6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125755"
---
# <a name="icordebugclassgetstaticfieldvalue-method"></a><span data-ttu-id="d9a08-102">ICorDebugClass::GetStaticFieldValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d9a08-102">ICorDebugClass::GetStaticFieldValue Method</span></span>
<span data-ttu-id="d9a08-103">Belirtilen statik alanın değerini alır.</span><span class="sxs-lookup"><span data-stu-id="d9a08-103">Gets the value of the specified static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9a08-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d9a08-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef         fieldDef,  
    [in]  ICorDebugFrame     *pFrame,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9a08-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d9a08-105">Parameters</span></span>  
 `fieldDef`  
 <span data-ttu-id="d9a08-106">'ndaki Alınacak alana başvuran bir alan `Def` belirteç.</span><span class="sxs-lookup"><span data-stu-id="d9a08-106">[in] A field `Def` token that references the field to be retrieved.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="d9a08-107">'ndaki İş parçacığı, bağlam veya uygulama etki alanı hazırlama arasında belirsizliği ortadan kaldırmak için kullanılacak çerçeveyi temsil eden ICorDebugFrame nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d9a08-107">[in] A pointer to an ICorDebugFrame object that represents the frame to be used to disambiguate among thread, context, or application domain statics.</span></span>  
  
 <span data-ttu-id="d9a08-108">Statik alan bir iş parçacığına, bir içeriğe veya bir uygulama etki alanına göreli ise, çerçeve uygun değeri tespit eder.</span><span class="sxs-lookup"><span data-stu-id="d9a08-108">If the static field is relative to a thread, a context, or an application domain, the frame will determine the proper value.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="d9a08-109">dışı Statik alanın değerini temsil eden bir ICorDebugValue nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d9a08-109">[out] A pointer to the address of an ICorDebugValue object that represents the value of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9a08-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d9a08-110">Remarks</span></span>  
 <span data-ttu-id="d9a08-111">Parametreli türler için, statik bir alanın değeri, belirli bir örnek oluşturma ile ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="d9a08-111">For parameterized types, the value of a static field is relative to the particular instantiation.</span></span> <span data-ttu-id="d9a08-112">Bu nedenle, sınıf Oluşturucu <xref:System.Type>türü parametreler alırsa, `ICorDebugClass::GetStaticFieldValue`yerine [ICorDebugType:: GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md) öğesini çağırın.</span><span class="sxs-lookup"><span data-stu-id="d9a08-112">Therefore, if the class constructor takes parameters of type <xref:System.Type>, call [ICorDebugType::GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md) instead of `ICorDebugClass::GetStaticFieldValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9a08-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d9a08-113">Requirements</span></span>  
 <span data-ttu-id="d9a08-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9a08-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9a08-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d9a08-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d9a08-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d9a08-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d9a08-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9a08-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
