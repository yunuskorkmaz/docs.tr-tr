---
title: "ICorDebugEval::CallFunction Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval.CallFunction
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval::CallFunction
helpviewer_keywords:
- ICorDebugEval::CallFunction method [.NET Framework debugging]
- CallFunction method [.NET Framework debugging]
ms.assetid: 7f470c5c-e1c0-4d8d-aad8-830f113ae751
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 72713d81931b53e8d61fb39cee146fd30a59bfcc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugevalcallfunction-method"></a><span data-ttu-id="4f5d8-102">ICorDebugEval::CallFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4f5d8-102">ICorDebugEval::CallFunction Method</span></span>
<span data-ttu-id="4f5d8-103">Belirtilen işlev çağrısı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4f5d8-103">Sets up a call to the specified function.</span></span>  
  
 <span data-ttu-id="4f5d8-104">Bu yöntem .NET Framework 2.0 sürümünde kullanımdan kalkmıştır.</span><span class="sxs-lookup"><span data-stu-id="4f5d8-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="4f5d8-105">Kullanım [Icordebugeval2::callparameterizedfunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md) yerine.</span><span class="sxs-lookup"><span data-stu-id="4f5d8-105">Use [ICorDebugEval2::CallParameterizedFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f5d8-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4f5d8-106">Syntax</span></span>  
  
```  
HRESULT CallFunction (  
    [in] ICorDebugFunction  *pFunction,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4f5d8-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4f5d8-107">Parameters</span></span>  
 `pFunction`  
 <span data-ttu-id="4f5d8-108">[in] İşaretçi ICorDebugFunction nesneye çağrılacak işlev belirtir.</span><span class="sxs-lookup"><span data-stu-id="4f5d8-108">[in] Pointer to an ICorDebugFunction object that specifies the function to be called.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="4f5d8-109">[in] İşlevin bağımsız değişken sayısı.</span><span class="sxs-lookup"><span data-stu-id="4f5d8-109">[in] The number of arguments for the function.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="4f5d8-110">[in] Her biri işleve iletilecek bağımsız değişken belirten Icordebugvalue nesneye işaret dizisi işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="4f5d8-110">[in] An array of pointers, each of which points to an ICorDebugValue object that specifies an argument to be passed to the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f5d8-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4f5d8-111">Remarks</span></span>  
 <span data-ttu-id="4f5d8-112">İşlev sanal ise `CallFunction` sanal gönderme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="4f5d8-112">If the function is virtual, `CallFunction` will perform virtual dispatch.</span></span> <span data-ttu-id="4f5d8-113">İşlev farklı uygulama etki alanında ise, tüm bağımsız değişkenler de o uygulama etki alanında olduğu sürece bir geçiş meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="4f5d8-113">If the function is in a different application domain, a transition will occur as long as all arguments are also in that application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f5d8-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4f5d8-114">Requirements</span></span>  
 <span data-ttu-id="4f5d8-115">**Platformlar:** WindowSee [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f5d8-115">**Platforms:** WindowSee [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f5d8-116">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4f5d8-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4f5d8-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4f5d8-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f5d8-118">**.NET framework sürümleri:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="4f5d8-118">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f5d8-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4f5d8-119">See Also</span></span>  
 [<span data-ttu-id="4f5d8-120">CallParameterizedFunction yöntemi</span><span class="sxs-lookup"><span data-stu-id="4f5d8-120">CallParameterizedFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)
