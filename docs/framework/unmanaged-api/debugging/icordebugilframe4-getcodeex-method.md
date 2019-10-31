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
ms.openlocfilehash: 9a74fd64e046ab3a8943e9a975e4de808c662677
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73090952"
---
# <a name="icordebugilframe4getcodeex-method"></a><span data-ttu-id="2c553-102">ICorDebugILFrame4::GetCodeEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2c553-102">ICorDebugILFrame4::GetCodeEx Method</span></span>
<span data-ttu-id="2c553-103">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="2c553-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="2c553-104">Bu yığın çerçevesinin yürütüldüğü koda yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="2c553-104">Gets a pointer to the code that this stack frame is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c553-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2c553-105">Syntax</span></span>  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c553-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2c553-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="2c553-107">'ndaki Profiler 'ın ReJIT isteği tarafından tanımlanan ara dilin (IL) çerçeveye dahil edilip edilmeyeceğini belirten bir [ılcodekind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) numaralandırma üyesi.</span><span class="sxs-lookup"><span data-stu-id="2c553-107">[in] An [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) enumeration member that specifies whether the intermediate language (IL) defined by the profiler's ReJIT request is included in the frame.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="2c553-108">dışı Bu yığın çerçevesinin yürütüldüğü kodu temsil eden bir "ICorDebugCode" nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2c553-108">[out] A pointer to the address of an "ICorDebugCode" object that represents the code that this stack frame is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c553-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2c553-109">Remarks</span></span>  
 <span data-ttu-id="2c553-110">Bu yöntem [ICorDebugFrame:: GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md) yöntemine benzer, isteğe bağlı olarak Profiler 'ın ReJIT isteği tarafından tanımlanan koda erişir.</span><span class="sxs-lookup"><span data-stu-id="2c553-110">This method is similar to the [ICorDebugFrame::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md) method, except that it optionally accesses code defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="2c553-111">Bu yöntemin `flags` bir `ILCODE_ORIGINAL_IL` ile çağrılması [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)çağırma ile eşdeğerdir; Yöntem belgelenmiş ise, onun Il 'ye erişilemeyecektir.</span><span class="sxs-lookup"><span data-stu-id="2c553-111">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md); if the method is instrumented, its IL will not be accessible.</span></span> <span data-ttu-id="2c553-112">`ILCODE_REJIT_IL`, hata ayıklayıcının profil oluşturucunun ReJIT isteği tarafından tanımlanan Il 'ye erişmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="2c553-112">`ILCODE_REJIT_IL` allows the debugger to access the IL defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="2c553-113">Il görünmüyorsa, `ppCode` **null**olur ve Yöntem `S_OK`döndürür.</span><span class="sxs-lookup"><span data-stu-id="2c553-113">If the IL is not instrumented, `ppCode` is **null**, and the method returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c553-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2c553-114">Requirements</span></span>  
 <span data-ttu-id="2c553-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c553-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c553-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2c553-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2c553-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2c553-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c553-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c553-118">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c553-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c553-119">See also</span></span>

- [<span data-ttu-id="2c553-120">ICorDebugILFrame4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2c553-120">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)
- [<span data-ttu-id="2c553-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2c553-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="2c553-122">ReJIT: nasıl yapılır Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2c553-122">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.microsoft.com/davbr/2011/10/12/rejit-a-how-to-guide/)
