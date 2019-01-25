---
title: ICorDebugEval::CallFunction Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugEval.CallFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::CallFunction
helpviewer_keywords:
- ICorDebugEval::CallFunction method [.NET Framework debugging]
- CallFunction method [.NET Framework debugging]
ms.assetid: 7f470c5c-e1c0-4d8d-aad8-830f113ae751
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 493b4850436b3724287210878992d1d8ce8fe168
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54589405"
---
# <a name="icordebugevalcallfunction-method"></a><span data-ttu-id="78c10-102">ICorDebugEval::CallFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="78c10-102">ICorDebugEval::CallFunction Method</span></span>
<span data-ttu-id="78c10-103">Belirtilen işlev çağrısı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="78c10-103">Sets up a call to the specified function.</span></span>  
  
 <span data-ttu-id="78c10-104">Bu yöntem .NET Framework 2.0 sürümünde artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="78c10-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="78c10-105">Kullanım [Icordebugeval2::callparameterizedfunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md) yerine.</span><span class="sxs-lookup"><span data-stu-id="78c10-105">Use [ICorDebugEval2::CallParameterizedFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78c10-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="78c10-106">Syntax</span></span>  
  
```  
HRESULT CallFunction (  
    [in] ICorDebugFunction  *pFunction,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="78c10-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="78c10-107">Parameters</span></span>  
 `pFunction`  
 <span data-ttu-id="78c10-108">[in] İşaretçi ICorDebugFunction nesneye çağrılacak işlevi belirtir.</span><span class="sxs-lookup"><span data-stu-id="78c10-108">[in] Pointer to an ICorDebugFunction object that specifies the function to be called.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="78c10-109">[in] İşlev için bağımsız değişken sayısı.</span><span class="sxs-lookup"><span data-stu-id="78c10-109">[in] The number of arguments for the function.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="78c10-110">[in] İşleve geçirilecek bağımsız değişken belirtir Icordebugvalue nesneyi işaret her biri bir işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="78c10-110">[in] An array of pointers, each of which points to an ICorDebugValue object that specifies an argument to be passed to the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78c10-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="78c10-111">Remarks</span></span>  
 <span data-ttu-id="78c10-112">Sanal bir işlev ise `CallFunction` sanal gönderim yapar.</span><span class="sxs-lookup"><span data-stu-id="78c10-112">If the function is virtual, `CallFunction` will perform virtual dispatch.</span></span> <span data-ttu-id="78c10-113">İşlev farklı uygulama etki alanında ise, tüm bağımsız değişkenler de, uygulama etki alanında olduğu sürece, bir geçiş meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="78c10-113">If the function is in a different application domain, a transition will occur as long as all arguments are also in that application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78c10-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="78c10-114">Requirements</span></span>  
 <span data-ttu-id="78c10-115">**Platformlar:** WindowSee [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78c10-115">**Platforms:** WindowSee [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78c10-116">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="78c10-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="78c10-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="78c10-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78c10-118">**.NET framework sürümleri:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="78c10-118">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78c10-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78c10-119">See also</span></span>
- [<span data-ttu-id="78c10-120">CallParameterizedFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="78c10-120">CallParameterizedFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)
