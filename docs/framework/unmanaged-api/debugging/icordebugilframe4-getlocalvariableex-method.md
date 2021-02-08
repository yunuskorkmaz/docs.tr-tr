---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugILFrame4:: GetLocalVariableEx yöntemi'
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
ms.openlocfilehash: 4eb6b3abbaf05c0373a487d9bd9d575b58a9af49
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791224"
---
# <a name="icordebugilframe4getlocalvariableex-method"></a><span data-ttu-id="f1335-103">ICorDebugILFrame4::GetLocalVariableEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f1335-103">ICorDebugILFrame4::GetLocalVariableEx Method</span></span>

<span data-ttu-id="f1335-104">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="f1335-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="f1335-105">Bu ara dil (IL) yığın çerçevesinde belirtilen yerel değişkenin değerini alır ve isteğe bağlı olarak profil oluşturucu yeniden JIT araçlarına eklenen bir değişkene erişir.</span><span class="sxs-lookup"><span data-stu-id="f1335-105">Gets the value of the specified local variable in this intermediate language (IL) stack frame, and optionally accesses a variable added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1335-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f1335-106">Syntax</span></span>  
  
```cpp
HRESULT GetLocalVariableEx(  
   [in] ILCodeKind flags,
   [in] DWORD dwIndex,
   [out] ICorDebugValue **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1335-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f1335-107">Parameters</span></span>  

 `flags`  
 <span data-ttu-id="f1335-108">'ndaki Profil Oluşturucu ReJIT araçlarına eklenen bir değişkenin çerçeveye dahil edilip edilmeyeceğini belirten bir [ılcodekind](ilcodekind-enumeration.md) numaralandırma üyesi.</span><span class="sxs-lookup"><span data-stu-id="f1335-108">[in] An [ILCodeKind](ilcodekind-enumeration.md) enumeration member that specifies whether a variable added in profiler ReJIT instrumentation is included in the frame.</span></span>  
  
 `dwIndex`  
 <span data-ttu-id="f1335-109">'ndaki Il yığın çerçevesindeki yerel değişkenin dizini.</span><span class="sxs-lookup"><span data-stu-id="f1335-109">[in] The index of the local variable in the IL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="f1335-110">dışı Alınan değeri temsil eden bir "ICorDebugValue" nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f1335-110">[out] A pointer to the address of an "ICorDebugValue" object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1335-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f1335-111">Remarks</span></span>  

 <span data-ttu-id="f1335-112">Bu yöntem, isteğe bağlı olarak profil oluşturucu yeniden JIT araçları 'nda eklenen bir değişkene eriştiği için [GetLocalVariable](icordebugilframe-getlocalvariable-method.md) yöntemine benzerdir.</span><span class="sxs-lookup"><span data-stu-id="f1335-112">This method is similar to the [GetLocalVariable](icordebugilframe-getlocalvariable-method.md) method, except that it optionally accesses a variable added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="f1335-113">Bu yöntemin bir değeriyle çağrılması `flags` `ILCODE_ORIGINAL_IL` [GetLocalVariable](icordebugilframe-getlocalvariable-method.md)çağrısı ile eşdeğerdir; Eğer Yöntem ek yerel değişkenlerle birlikte işaretlenmiş ise, bu değişkenlere erişilemez.</span><span class="sxs-lookup"><span data-stu-id="f1335-113">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetLocalVariable](icordebugilframe-getlocalvariable-method.md); if the method is instrumented with additional local variables, those variables cannot be accessed.</span></span> <span data-ttu-id="f1335-114">`ILCODE_REJIT_IL` hata ayıklayıcının profil oluşturucu ReJIT araçları 'nda eklenen yerel değişkenlere erişmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="f1335-114">`ILCODE_REJIT_IL` allows the debugger to access the local variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="f1335-115">Il görünmüyorsa, yöntemi döndürür `E_INVALIDARG` .</span><span class="sxs-lookup"><span data-stu-id="f1335-115">If the IL is not instrumented, the method returns `E_INVALIDARG`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1335-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f1335-116">Requirements</span></span>  

 <span data-ttu-id="f1335-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1335-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1335-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f1335-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f1335-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f1335-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1335-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1335-120">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1335-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1335-121">See also</span></span>

- [<span data-ttu-id="f1335-122">ICorDebugILFrame4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f1335-122">ICorDebugILFrame4 Interface</span></span>](icordebugilframe4-interface.md)
- [<span data-ttu-id="f1335-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f1335-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="f1335-124">ReJIT: A How-To Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f1335-124">ReJIT: A How-To Guide</span></span>](/archive/blogs/davbr/rejit-a-how-to-guide)
