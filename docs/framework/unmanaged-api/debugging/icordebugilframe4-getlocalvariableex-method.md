---
title: ICorDebugILFrame4::GetLocalVariableEx Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.GetCodeEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 0c8676f8-ca0d-4998-b64d-fefac7e38912
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 968e504eadb5f7444095a6a98dea414aa4486dce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframe4getlocalvariableex-method"></a><span data-ttu-id="6d8d4-102">ICorDebugILFrame4::GetLocalVariableEx Metodu</span><span class="sxs-lookup"><span data-stu-id="6d8d4-102">ICorDebugILFrame4::GetLocalVariableEx Method</span></span>
<span data-ttu-id="6d8d4-103">[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="6d8d4-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="6d8d4-104">Bu Ara dile (IL) yığın çerçevesinde belirtilen yerel değişkenin değerini alır ve isteğe bağlı olarak profiler ReJIT araçları eklenen bir değişken erişir.</span><span class="sxs-lookup"><span data-stu-id="6d8d4-104">Gets the value of the specified local variable in this intermediate language (IL) stack frame, and optionally accesses a variable added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d8d4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6d8d4-105">Syntax</span></span>  
  
```cpp
HRESULT GetLocalVariableEx(  
   [in] ILCodeKind flags,   
   [in] DWORD dwIndex,   
   [out] ICorDebugValue **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6d8d4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6d8d4-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="6d8d4-107">[in] Bir [Ilcodekind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) profiler ReJIT araçları eklenen bir değişken çerçevede dahil edilip edilmediğini belirten numaralandırma üyesi.</span><span class="sxs-lookup"><span data-stu-id="6d8d4-107">[in] An [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) enumeration member that specifies whether a variable added in profiler ReJIT instrumentation is included in the frame.</span></span>  
  
 `dwIndex`  
 <span data-ttu-id="6d8d4-108">[in] IL yığın çerçevesi yerel değişkende dizini.</span><span class="sxs-lookup"><span data-stu-id="6d8d4-108">[in] The index of the local variable in the IL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="6d8d4-109">[out] Alınan değerin temsil eden bir "ICorDebugValue" nesnesinin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6d8d4-109">[out] A pointer to the address of an "ICorDebugValue" object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d8d4-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6d8d4-110">Remarks</span></span>  
 <span data-ttu-id="6d8d4-111">Bu yöntem benzer [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) olan isteğe bağlı olarak profiler ReJIT araçları eklenen bir değişken erişen dışında yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6d8d4-111">This method is similar to the [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) method, except that it optionally accesses a variable added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="6d8d4-112">Bu yöntemle çağırma bir `flags` değerini `ILCODE_ORIGINAL_IL` arama için eşdeğer bir gruba [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md); yöntemi ek yerel değişkenleriyle izlenmiş olan değişkenlere erişilemiyor.</span><span class="sxs-lookup"><span data-stu-id="6d8d4-112">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md); if the method is instrumented with additional local variables, those variables cannot be accessed.</span></span> <span data-ttu-id="6d8d4-113">`ILCODE_REJIT_IL`Profil Oluşturucusu ReJIT Araçları'nda eklenen yerel değişkenler erişmek hata ayıklayıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="6d8d4-113">`ILCODE_REJIT_IL` allows the debugger to access the local variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="6d8d4-114">IL izlenmemektedir ise, yöntem `E_INVALIDARG`.</span><span class="sxs-lookup"><span data-stu-id="6d8d4-114">If the IL is not instrumented, the method returns `E_INVALIDARG`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d8d4-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6d8d4-115">Requirements</span></span>  
 <span data-ttu-id="6d8d4-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d8d4-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d8d4-117">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6d8d4-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d8d4-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d8d4-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d8d4-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d8d4-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d8d4-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6d8d4-120">See Also</span></span>  
 [<span data-ttu-id="6d8d4-121">ICorDebugILFrame4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6d8d4-121">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [<span data-ttu-id="6d8d4-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6d8d4-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="6d8d4-123">ReJIT: Nasıl yapılır Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6d8d4-123">ReJIT: A How-To Guide</span></span>](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
