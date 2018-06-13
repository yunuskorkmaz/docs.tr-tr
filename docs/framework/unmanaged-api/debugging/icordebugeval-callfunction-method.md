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
ms.openlocfilehash: 86d48461c601b53d4461331a11a0e0ac7ddc6e7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412558"
---
# <a name="icordebugevalcallfunction-method"></a><span data-ttu-id="89496-102">ICorDebugEval::CallFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="89496-102">ICorDebugEval::CallFunction Method</span></span>
<span data-ttu-id="89496-103">Belirtilen işlev çağrısı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="89496-103">Sets up a call to the specified function.</span></span>  
  
 <span data-ttu-id="89496-104">Bu yöntem .NET Framework 2.0 sürümünde kullanımdan kalkmıştır.</span><span class="sxs-lookup"><span data-stu-id="89496-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="89496-105">Kullanım [Icordebugeval2::callparameterizedfunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md) yerine.</span><span class="sxs-lookup"><span data-stu-id="89496-105">Use [ICorDebugEval2::CallParameterizedFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89496-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="89496-106">Syntax</span></span>  
  
```  
HRESULT CallFunction (  
    [in] ICorDebugFunction  *pFunction,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="89496-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="89496-107">Parameters</span></span>  
 `pFunction`  
 <span data-ttu-id="89496-108">[in] İşaretçi ICorDebugFunction nesneye çağrılacak işlev belirtir.</span><span class="sxs-lookup"><span data-stu-id="89496-108">[in] Pointer to an ICorDebugFunction object that specifies the function to be called.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="89496-109">[in] İşlevin bağımsız değişken sayısı.</span><span class="sxs-lookup"><span data-stu-id="89496-109">[in] The number of arguments for the function.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="89496-110">[in] Her biri işleve iletilecek bağımsız değişken belirten Icordebugvalue nesneye işaret dizisi işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="89496-110">[in] An array of pointers, each of which points to an ICorDebugValue object that specifies an argument to be passed to the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="89496-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="89496-111">Remarks</span></span>  
 <span data-ttu-id="89496-112">İşlev sanal ise `CallFunction` sanal gönderme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="89496-112">If the function is virtual, `CallFunction` will perform virtual dispatch.</span></span> <span data-ttu-id="89496-113">İşlev farklı uygulama etki alanında ise, tüm bağımsız değişkenler de o uygulama etki alanında olduğu sürece bir geçiş meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="89496-113">If the function is in a different application domain, a transition will occur as long as all arguments are also in that application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89496-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="89496-114">Requirements</span></span>  
 <span data-ttu-id="89496-115">**Platformlar:** WindowSee [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89496-115">**Platforms:** WindowSee [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89496-116">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="89496-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="89496-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="89496-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89496-118">**.NET framework sürümleri:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="89496-118">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89496-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="89496-119">See Also</span></span>  
 [<span data-ttu-id="89496-120">CallParameterizedFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="89496-120">CallParameterizedFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)
