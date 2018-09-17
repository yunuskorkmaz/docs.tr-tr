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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 24be4507e8ad6cde1e9c50582e352f0fc9b12ed3
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45741945"
---
# <a name="icordebugilframe4getcodeex-method"></a><span data-ttu-id="57548-102">ICorDebugILFrame4::GetCodeEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="57548-102">ICorDebugILFrame4::GetCodeEx Method</span></span>
<span data-ttu-id="57548-103">[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="57548-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="57548-104">Bu yığın çerçevesi yürütülmekte olan kod için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="57548-104">Gets a pointer to the code that this stack frame is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57548-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="57548-105">Syntax</span></span>  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugCode **ppCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="57548-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="57548-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="57548-107">[in] Bir [Ilcodekind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) numaralandırma üyesi, profil oluşturucunun ReJIT istek tarafından tanımlanan Ara dil (IL) çerçevede içerilip içerilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="57548-107">[in] An [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) enumeration member that specifies whether the intermediate language (IL) defined by the profiler's ReJIT request is included in the frame.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="57548-108">[out] Bu yığın çerçevesi yürütme kodunu temsil eden bir "ICorDebugCode" nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="57548-108">[out] A pointer to the address of an "ICorDebugCode" object that represents the code that this stack frame is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57548-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="57548-109">Remarks</span></span>  
 <span data-ttu-id="57548-110">Bu yöntem benzer [Icordebugframe::getcode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md) yöntemi dışında olan isteğe bağlı olarak kod profil oluşturucunun ReJIT istek tarafından tanımlanan erişir.</span><span class="sxs-lookup"><span data-stu-id="57548-110">This method is similar to the [ICorDebugFrame::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md) method, except that it optionally accesses code defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="57548-111">İle bu yöntemin çağrılması bir `flags` değerini `ILCODE_ORIGINAL_IL` çağırmakla eşdeğerdir [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md); yöntem işaretlenmiş ise, IL erişilemez.</span><span class="sxs-lookup"><span data-stu-id="57548-111">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md); if the method is instrumented, its IL will not be accessible.</span></span> <span data-ttu-id="57548-112">`ILCODE_REJIT_IL` hata ayıklayıcının profil oluşturucunun ReJIT istek tarafından tanımlanan IL erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="57548-112">`ILCODE_REJIT_IL` allows the debugger to access the IL defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="57548-113">IL izlenmiyor, `ppCode` olduğu **null**, ve yöntemi `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="57548-113">If the IL is not instrumented, `ppCode` is **null**, and the method returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57548-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="57548-114">Requirements</span></span>  
 <span data-ttu-id="57548-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57548-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57548-116">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="57548-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="57548-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="57548-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="57548-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57548-118">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57548-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="57548-119">See Also</span></span>  
 [<span data-ttu-id="57548-120">ICorDebugILFrame4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="57548-120">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [<span data-ttu-id="57548-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="57548-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="57548-122">ReJIT: Nasıl yapılır Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="57548-122">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
