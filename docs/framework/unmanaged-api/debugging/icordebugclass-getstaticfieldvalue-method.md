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
ms.openlocfilehash: dd1608badf553650b05b7de98d9bbcd76b2f3edf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728439"
---
# <a name="icordebugclassgetstaticfieldvalue-method"></a><span data-ttu-id="528aa-102">ICorDebugClass::GetStaticFieldValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="528aa-102">ICorDebugClass::GetStaticFieldValue Method</span></span>

<span data-ttu-id="528aa-103">Belirtilen statik alanın değerini alır.</span><span class="sxs-lookup"><span data-stu-id="528aa-103">Gets the value of the specified static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="528aa-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="528aa-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef         fieldDef,  
    [in]  ICorDebugFrame     *pFrame,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="528aa-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="528aa-105">Parameters</span></span>  

 `fieldDef`  
 <span data-ttu-id="528aa-106">'ndaki `Def` Alınacak alana başvuran bir alan belirteci.</span><span class="sxs-lookup"><span data-stu-id="528aa-106">[in] A field `Def` token that references the field to be retrieved.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="528aa-107">'ndaki İş parçacığı, bağlam veya uygulama etki alanı hazırlama arasında belirsizliği ortadan kaldırmak için kullanılacak çerçeveyi temsil eden ICorDebugFrame nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="528aa-107">[in] A pointer to an ICorDebugFrame object that represents the frame to be used to disambiguate among thread, context, or application domain statics.</span></span>  
  
 <span data-ttu-id="528aa-108">Statik alan bir iş parçacığına, bir içeriğe veya bir uygulama etki alanına göreli ise, çerçeve uygun değeri tespit eder.</span><span class="sxs-lookup"><span data-stu-id="528aa-108">If the static field is relative to a thread, a context, or an application domain, the frame will determine the proper value.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="528aa-109">dışı Statik alanın değerini temsil eden bir ICorDebugValue nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="528aa-109">[out] A pointer to the address of an ICorDebugValue object that represents the value of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="528aa-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="528aa-110">Remarks</span></span>  

 <span data-ttu-id="528aa-111">Parametreli türler için, statik bir alanın değeri, belirli bir örnek oluşturma ile ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="528aa-111">For parameterized types, the value of a static field is relative to the particular instantiation.</span></span> <span data-ttu-id="528aa-112">Bu nedenle, sınıf oluşturucusu türünde parametreler alırsa <xref:System.Type> , yerine [ICorDebugType:: GetStaticFieldValue](icordebugtype-getstaticfieldvalue-method.md) çağırın `ICorDebugClass::GetStaticFieldValue` .</span><span class="sxs-lookup"><span data-stu-id="528aa-112">Therefore, if the class constructor takes parameters of type <xref:System.Type>, call [ICorDebugType::GetStaticFieldValue](icordebugtype-getstaticfieldvalue-method.md) instead of `ICorDebugClass::GetStaticFieldValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="528aa-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="528aa-113">Requirements</span></span>  

 <span data-ttu-id="528aa-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="528aa-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="528aa-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="528aa-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="528aa-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="528aa-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="528aa-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="528aa-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
