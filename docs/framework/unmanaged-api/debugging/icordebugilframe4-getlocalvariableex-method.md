---
title: ICorDebugILFrame4::GetLocalVariableEx Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorDebugILFrame4.GetCodeEx
api_location: mscordbi.dll
api_type: COM
ms.assetid: 0c8676f8-ca0d-4998-b64d-fefac7e38912
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: eca9919555d0ee7c4398ecff51f9a6ee3936a41b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugilframe4getlocalvariableex-method"></a><span data-ttu-id="dd87e-102">ICorDebugILFrame4::GetLocalVariableEx Metodu</span><span class="sxs-lookup"><span data-stu-id="dd87e-102">ICorDebugILFrame4::GetLocalVariableEx Method</span></span>
<span data-ttu-id="dd87e-103">[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="dd87e-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="dd87e-104">Bu Ara dile (IL) yığın çerçevesinde belirtilen yerel değişkenin değerini alır ve isteğe bağlı olarak profiler ReJIT araçları eklenen bir değişken erişir.</span><span class="sxs-lookup"><span data-stu-id="dd87e-104">Gets the value of the specified local variable in this intermediate language (IL) stack frame, and optionally accesses a variable added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd87e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dd87e-105">Syntax</span></span>  
  
```cpp
HRESULT GetLocalVariableEx(  
   [in] ILCodeKind flags,   
   [in] DWORD dwIndex,   
   [out] ICorDebugValue **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dd87e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dd87e-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="dd87e-107">[in] Bir [Ilcodekind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) profiler ReJIT araçları eklenen bir değişken çerçevede dahil edilip edilmediğini belirten numaralandırma üyesi.</span><span class="sxs-lookup"><span data-stu-id="dd87e-107">[in] An [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) enumeration member that specifies whether a variable added in profiler ReJIT instrumentation is included in the frame.</span></span>  
  
 `dwIndex`  
 <span data-ttu-id="dd87e-108">[in] IL yığın çerçevesi yerel değişkende dizini.</span><span class="sxs-lookup"><span data-stu-id="dd87e-108">[in] The index of the local variable in the IL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="dd87e-109">[out] Alınan değerin temsil eden bir "ICorDebugValue" nesnesinin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="dd87e-109">[out] A pointer to the address of an "ICorDebugValue" object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd87e-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dd87e-110">Remarks</span></span>  
 <span data-ttu-id="dd87e-111">Bu yöntem benzer [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) olan isteğe bağlı olarak profiler ReJIT araçları eklenen bir değişken erişen dışında yöntemi.</span><span class="sxs-lookup"><span data-stu-id="dd87e-111">This method is similar to the [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) method, except that it optionally accesses a variable added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="dd87e-112">Bu yöntemle çağırma bir `flags` değerini `ILCODE_ORIGINAL_IL` arama için eşdeğer bir gruba [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md); yöntemi ek yerel değişkenleriyle izlenmiş olan değişkenlere erişilemiyor.</span><span class="sxs-lookup"><span data-stu-id="dd87e-112">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md); if the method is instrumented with additional local variables, those variables cannot be accessed.</span></span> <span data-ttu-id="dd87e-113">`ILCODE_REJIT_IL`Profil Oluşturucusu ReJIT Araçları'nda eklenen yerel değişkenler erişmek hata ayıklayıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="dd87e-113">`ILCODE_REJIT_IL` allows the debugger to access the local variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="dd87e-114">IL izlenmemektedir ise, yöntem `E_INVALIDARG`.</span><span class="sxs-lookup"><span data-stu-id="dd87e-114">If the IL is not instrumented, the method returns `E_INVALIDARG`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd87e-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dd87e-115">Requirements</span></span>  
 <span data-ttu-id="dd87e-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd87e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd87e-117">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dd87e-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dd87e-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dd87e-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dd87e-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd87e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd87e-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dd87e-120">See Also</span></span>  
 [<span data-ttu-id="dd87e-121">Icordebugılframe4 arabirimi</span><span class="sxs-lookup"><span data-stu-id="dd87e-121">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [<span data-ttu-id="dd87e-122">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="dd87e-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="dd87e-123">ReJIT: Nasıl yapılır Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="dd87e-123">ReJIT: A How-To Guide</span></span>](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
