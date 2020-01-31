---
title: ICorDebugILFrame4::GetLocalVariableEx Yöntemi
ms.date: 03/30/2017
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
ms.openlocfilehash: 017c14e9170087f3c3c9de64f50d165fc91aa297
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782412"
---
# <a name="icordebugilframe4getlocalvariableex-method"></a><span data-ttu-id="85615-102">ICorDebugILFrame4::GetLocalVariableEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="85615-102">ICorDebugILFrame4::GetLocalVariableEx Method</span></span>
<span data-ttu-id="85615-103">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="85615-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="85615-104">Bu ara dil (IL) yığın çerçevesinde belirtilen yerel değişkenin değerini alır ve isteğe bağlı olarak profil oluşturucu yeniden JIT araçlarına eklenen bir değişkene erişir.</span><span class="sxs-lookup"><span data-stu-id="85615-104">Gets the value of the specified local variable in this intermediate language (IL) stack frame, and optionally accesses a variable added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85615-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="85615-105">Syntax</span></span>  
  
```cpp
HRESULT GetLocalVariableEx(  
   [in] ILCodeKind flags,   
   [in] DWORD dwIndex,   
   [out] ICorDebugValue **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85615-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="85615-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="85615-107">'ndaki Profil Oluşturucu ReJIT araçlarına eklenen bir değişkenin çerçeveye dahil edilip edilmeyeceğini belirten bir [ılcodekind](ilcodekind-enumeration.md) numaralandırma üyesi.</span><span class="sxs-lookup"><span data-stu-id="85615-107">[in] An [ILCodeKind](ilcodekind-enumeration.md) enumeration member that specifies whether a variable added in profiler ReJIT instrumentation is included in the frame.</span></span>  
  
 `dwIndex`  
 <span data-ttu-id="85615-108">'ndaki Il yığın çerçevesindeki yerel değişkenin dizini.</span><span class="sxs-lookup"><span data-stu-id="85615-108">[in] The index of the local variable in the IL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="85615-109">dışı Alınan değeri temsil eden bir "ICorDebugValue" nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="85615-109">[out] A pointer to the address of an "ICorDebugValue" object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85615-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="85615-110">Remarks</span></span>  
 <span data-ttu-id="85615-111">Bu yöntem, isteğe bağlı olarak profil oluşturucu yeniden JIT araçları 'nda eklenen bir değişkene eriştiği için [GetLocalVariable](icordebugilframe-getlocalvariable-method.md) yöntemine benzerdir.</span><span class="sxs-lookup"><span data-stu-id="85615-111">This method is similar to the [GetLocalVariable](icordebugilframe-getlocalvariable-method.md) method, except that it optionally accesses a variable added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="85615-112">Bu yöntemin `flags` bir `ILCODE_ORIGINAL_IL` çağrısı [GetLocalVariable](icordebugilframe-getlocalvariable-method.md)çağrısı ile eşdeğerdir; Yöntem ek yerel değişkenlerle birlikte işaretlenmiş ise, bu değişkenlere erişilemez.</span><span class="sxs-lookup"><span data-stu-id="85615-112">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetLocalVariable](icordebugilframe-getlocalvariable-method.md); if the method is instrumented with additional local variables, those variables cannot be accessed.</span></span> <span data-ttu-id="85615-113">`ILCODE_REJIT_IL`, hata ayıklayıcının profil oluşturucu ReJIT araçları 'nda eklenen yerel değişkenlere erişmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="85615-113">`ILCODE_REJIT_IL` allows the debugger to access the local variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="85615-114">Il görünmüyorsa, yöntem `E_INVALIDARG`döndürür.</span><span class="sxs-lookup"><span data-stu-id="85615-114">If the IL is not instrumented, the method returns `E_INVALIDARG`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85615-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="85615-115">Requirements</span></span>  
 <span data-ttu-id="85615-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85615-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85615-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="85615-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="85615-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="85615-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85615-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85615-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85615-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85615-120">See also</span></span>

- [<span data-ttu-id="85615-121">ICorDebugILFrame4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="85615-121">ICorDebugILFrame4 Interface</span></span>](icordebugilframe4-interface.md)
- [<span data-ttu-id="85615-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="85615-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="85615-123">ReJIT: nasıl yapılır Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="85615-123">ReJIT: A How-To Guide</span></span>](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
