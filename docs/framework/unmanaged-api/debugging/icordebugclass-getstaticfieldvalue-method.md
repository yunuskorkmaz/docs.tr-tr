---
description: ': ICorDebugClass:: GetStaticFieldValue metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: a5406e44491ce89030731c35752066e4943cebfc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711530"
---
# <a name="icordebugclassgetstaticfieldvalue-method"></a><span data-ttu-id="e6652-103">ICorDebugClass::GetStaticFieldValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e6652-103">ICorDebugClass::GetStaticFieldValue Method</span></span>

<span data-ttu-id="e6652-104">Belirtilen statik alanın değerini alır.</span><span class="sxs-lookup"><span data-stu-id="e6652-104">Gets the value of the specified static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6652-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e6652-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef         fieldDef,  
    [in]  ICorDebugFrame     *pFrame,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6652-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e6652-106">Parameters</span></span>  

 `fieldDef`  
 <span data-ttu-id="e6652-107">'ndaki `Def` Alınacak alana başvuran bir alan belirteci.</span><span class="sxs-lookup"><span data-stu-id="e6652-107">[in] A field `Def` token that references the field to be retrieved.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="e6652-108">'ndaki İş parçacığı, bağlam veya uygulama etki alanı hazırlama arasında belirsizliği ortadan kaldırmak için kullanılacak çerçeveyi temsil eden ICorDebugFrame nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e6652-108">[in] A pointer to an ICorDebugFrame object that represents the frame to be used to disambiguate among thread, context, or application domain statics.</span></span>  
  
 <span data-ttu-id="e6652-109">Statik alan bir iş parçacığına, bir içeriğe veya bir uygulama etki alanına göreli ise, çerçeve uygun değeri tespit eder.</span><span class="sxs-lookup"><span data-stu-id="e6652-109">If the static field is relative to a thread, a context, or an application domain, the frame will determine the proper value.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="e6652-110">dışı Statik alanın değerini temsil eden bir ICorDebugValue nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e6652-110">[out] A pointer to the address of an ICorDebugValue object that represents the value of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6652-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e6652-111">Remarks</span></span>  

 <span data-ttu-id="e6652-112">Parametreli türler için, statik bir alanın değeri, belirli bir örnek oluşturma ile ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="e6652-112">For parameterized types, the value of a static field is relative to the particular instantiation.</span></span> <span data-ttu-id="e6652-113">Bu nedenle, sınıf oluşturucusu türünde parametreler alırsa <xref:System.Type> , yerine [ICorDebugType:: GetStaticFieldValue](icordebugtype-getstaticfieldvalue-method.md) çağırın `ICorDebugClass::GetStaticFieldValue` .</span><span class="sxs-lookup"><span data-stu-id="e6652-113">Therefore, if the class constructor takes parameters of type <xref:System.Type>, call [ICorDebugType::GetStaticFieldValue](icordebugtype-getstaticfieldvalue-method.md) instead of `ICorDebugClass::GetStaticFieldValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6652-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e6652-114">Requirements</span></span>  

 <span data-ttu-id="e6652-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6652-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6652-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e6652-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e6652-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e6652-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e6652-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6652-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
