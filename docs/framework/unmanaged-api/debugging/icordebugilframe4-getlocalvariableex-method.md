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
ms.openlocfilehash: ee263e8c49cd6da7278bd2299557336629720d2f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178772"
---
# <a name="icordebugilframe4getlocalvariableex-method"></a><span data-ttu-id="d8f2f-102">ICorDebugILFrame4::GetLocalVariableEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d8f2f-102">ICorDebugILFrame4::GetLocalVariableEx Method</span></span>
<span data-ttu-id="d8f2f-103">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="d8f2f-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="d8f2f-104">Bu ara dil (IL) yığın çerçevesinde belirtilen yerel değişkenin değerini alır ve isteğe bağlı olarak profiloluşturucu ReJIT enstrümantasyonuna eklenen bir değişkene erişir.</span><span class="sxs-lookup"><span data-stu-id="d8f2f-104">Gets the value of the specified local variable in this intermediate language (IL) stack frame, and optionally accesses a variable added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8f2f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8f2f-105">Syntax</span></span>  
  
```cpp
HRESULT GetLocalVariableEx(  
   [in] ILCodeKind flags,
   [in] DWORD dwIndex,
   [out] ICorDebugValue **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8f2f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d8f2f-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="d8f2f-107">[içinde] Profiloluşturr ReJIT enstrümantasyonuna eklenen bir değişkenin çerçeveye dahil edilip edilmeyeceğini belirten bir [ILCodeKind](ilcodekind-enumeration.md) numaralandırma üyesi.</span><span class="sxs-lookup"><span data-stu-id="d8f2f-107">[in] An [ILCodeKind](ilcodekind-enumeration.md) enumeration member that specifies whether a variable added in profiler ReJIT instrumentation is included in the frame.</span></span>  
  
 `dwIndex`  
 <span data-ttu-id="d8f2f-108">[içinde] IL yığın çerçevesinde yerel değişkenin dizin.</span><span class="sxs-lookup"><span data-stu-id="d8f2f-108">[in] The index of the local variable in the IL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="d8f2f-109">[çıkış] Alınan değeri temsil eden bir "ICorDebugValue" nesnesinin adresine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d8f2f-109">[out] A pointer to the address of an "ICorDebugValue" object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8f2f-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d8f2f-110">Remarks</span></span>  
 <span data-ttu-id="d8f2f-111">Bu yöntem, profiler ReJIT enstrümantasyonuna eklenen bir değişkene isteğe bağlı olarak erişilmesi dışında [GetLocalVariable](icordebugilframe-getlocalvariable-method.md) yöntemine benzer.</span><span class="sxs-lookup"><span data-stu-id="d8f2f-111">This method is similar to the [GetLocalVariable](icordebugilframe-getlocalvariable-method.md) method, except that it optionally accesses a variable added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="d8f2f-112">Bu yöntemi `flags` bir değerle çağırmak [GetLocalVariable'i](icordebugilframe-getlocalvariable-method.md)aramaya `ILCODE_ORIGINAL_IL` eşdeğerdir; yöntem ek yerel değişkenlerle çalgılanmışsa, bu değişkenlere erişilemez.</span><span class="sxs-lookup"><span data-stu-id="d8f2f-112">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetLocalVariable](icordebugilframe-getlocalvariable-method.md); if the method is instrumented with additional local variables, those variables cannot be accessed.</span></span> <span data-ttu-id="d8f2f-113">`ILCODE_REJIT_IL`hata ayıklayıcının profil oluşturucu ReJIT enstrümantasyonuna eklenen yerel değişkenlere erişmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="d8f2f-113">`ILCODE_REJIT_IL` allows the debugger to access the local variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="d8f2f-114">IL aracılı değilse, yöntem döndürür. `E_INVALIDARG`</span><span class="sxs-lookup"><span data-stu-id="d8f2f-114">If the IL is not instrumented, the method returns `E_INVALIDARG`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8f2f-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d8f2f-115">Requirements</span></span>  
 <span data-ttu-id="d8f2f-116">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8f2f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8f2f-117">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d8f2f-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8f2f-118">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8f2f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8f2f-119">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8f2f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8f2f-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8f2f-120">See also</span></span>

- [<span data-ttu-id="d8f2f-121">ICorDebugILFrame4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8f2f-121">ICorDebugILFrame4 Interface</span></span>](icordebugilframe4-interface.md)
- [<span data-ttu-id="d8f2f-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d8f2f-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="d8f2f-123">ReJIT: Nasıl Yapilir Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d8f2f-123">ReJIT: A How-To Guide</span></span>](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
