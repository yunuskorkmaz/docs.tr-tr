---
title: ICorDebugILFrame4::GetCodeEx Yöntemi
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.GetLocalVariableEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: aeda0e42-29ee-4ca8-9f21-ac4641677a62
topic_type:
- apiref
ms.openlocfilehash: ef2e4bc0caddd6b13c8dbe8edb59e0673519421b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178790"
---
# <a name="icordebugilframe4getcodeex-method"></a><span data-ttu-id="d4d31-102">ICorDebugILFrame4::GetCodeEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d4d31-102">ICorDebugILFrame4::GetCodeEx Method</span></span>
<span data-ttu-id="d4d31-103">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="d4d31-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="d4d31-104">Bu yığın çerçevesinin yürütüldettiği koda bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="d4d31-104">Gets a pointer to the code that this stack frame is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4d31-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d4d31-105">Syntax</span></span>  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,
   [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4d31-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d4d31-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="d4d31-107">[içinde] Profilcinin ReJIT isteği tarafından tanımlanan ara dilin (IL) çerçeveye dahil edilip edilmeyeceğini belirten bir [ILCodeKind](ilcodekind-enumeration.md) numaralandırma üyesi.</span><span class="sxs-lookup"><span data-stu-id="d4d31-107">[in] An [ILCodeKind](ilcodekind-enumeration.md) enumeration member that specifies whether the intermediate language (IL) defined by the profiler's ReJIT request is included in the frame.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="d4d31-108">[çıkış] Bu yığın çerçevesinin yürütüldettiği kodu temsil eden bir "ICorDebugCode" nesnesinin adresine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d4d31-108">[out] A pointer to the address of an "ICorDebugCode" object that represents the code that this stack frame is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4d31-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d4d31-109">Remarks</span></span>  
 <span data-ttu-id="d4d31-110">Bu yöntem, profilcinin ReJIT isteği tarafından tanımlanan koda isteğe bağlı olarak erişmesi dışında [ICorDebugFrame::GetCode](icordebugframe-getcode-method.md) yöntemine benzer.</span><span class="sxs-lookup"><span data-stu-id="d4d31-110">This method is similar to the [ICorDebugFrame::GetCode](icordebugframe-getcode-method.md) method, except that it optionally accesses code defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="d4d31-111">Bu yöntemi `flags` bir değerle çağırmak [GetCode'u](icordebugframe-getcode-method.md)aramaya `ILCODE_ORIGINAL_IL` eşdeğerdir; yöntem işletilmişse, IL'sine erişilemez.</span><span class="sxs-lookup"><span data-stu-id="d4d31-111">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetCode](icordebugframe-getcode-method.md); if the method is instrumented, its IL will not be accessible.</span></span> <span data-ttu-id="d4d31-112">`ILCODE_REJIT_IL`hata ayıklayıcının profilcinin ReJIT isteği tarafından tanımlanan IL'ye erişmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="d4d31-112">`ILCODE_REJIT_IL` allows the debugger to access the IL defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="d4d31-113">IL enstrümante değilse, `ppCode` **null**ise , ve `S_OK`yöntem döndürür.</span><span class="sxs-lookup"><span data-stu-id="d4d31-113">If the IL is not instrumented, `ppCode` is **null**, and the method returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4d31-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d4d31-114">Requirements</span></span>  
 <span data-ttu-id="d4d31-115">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4d31-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4d31-116">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d4d31-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d4d31-117">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d4d31-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4d31-118">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4d31-118">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4d31-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4d31-119">See also</span></span>

- [<span data-ttu-id="d4d31-120">ICorDebugILFrame4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4d31-120">ICorDebugILFrame4 Interface</span></span>](icordebugilframe4-interface.md)
- [<span data-ttu-id="d4d31-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d4d31-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="d4d31-122">ReJIT: Nasıl Yapilir Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d4d31-122">ReJIT: A How-To Guide</span></span>](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
