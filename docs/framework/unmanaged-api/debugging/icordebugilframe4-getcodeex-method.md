---
title: ICorDebugILFrame4::GetCodeEx Metodu
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
ms.openlocfilehash: edaea49d95eeb9856b949f118f16aa49e528f7ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421040"
---
# <a name="icordebugilframe4getcodeex-method"></a><span data-ttu-id="65b5b-102">ICorDebugILFrame4::GetCodeEx Metodu</span><span class="sxs-lookup"><span data-stu-id="65b5b-102">ICorDebugILFrame4::GetCodeEx Method</span></span>
<span data-ttu-id="65b5b-103">[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="65b5b-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="65b5b-104">Bir işaretçi Bu yığın çerçevesi yürütülen kodu alır.</span><span class="sxs-lookup"><span data-stu-id="65b5b-104">Gets a pointer to the code that this stack frame is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65b5b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="65b5b-105">Syntax</span></span>  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugCode **ppCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="65b5b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="65b5b-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="65b5b-107">[in] Bir [Ilcodekind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) Profil Oluşturucu'nın ReJIT isteği tarafından tanımlanan Ara dile (IL) çerçevede dahil edilip edilmediğini belirten numaralandırma üyesi.</span><span class="sxs-lookup"><span data-stu-id="65b5b-107">[in] An [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) enumeration member that specifies whether the intermediate language (IL) defined by the profiler's ReJIT request is included in the frame.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="65b5b-108">[out] Bir işaretçi adresine "ICorDebugCode" nesnenin Bu yığın çerçevesi yürütüyor kodunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="65b5b-108">[out] A pointer to the address of an "ICorDebugCode" object that represents the code that this stack frame is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65b5b-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="65b5b-109">Remarks</span></span>  
 <span data-ttu-id="65b5b-110">Bu yöntem benzer [Icordebugframe::getcode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md) olan isteğe bağlı olarak kod Profil Oluşturucu'nın ReJIT isteği tarafından tanımlanan erişen dışında yöntemi.</span><span class="sxs-lookup"><span data-stu-id="65b5b-110">This method is similar to the [ICorDebugFrame::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md) method, except that it optionally accesses code defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="65b5b-111">Bu yöntem çağırma bir `flags` değerini `ILCODE_ORIGINAL_IL` arama için eşdeğer bir gruba [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md); yöntemi sürümlerde desteklenir, kendi IL erişilemeyecek.</span><span class="sxs-lookup"><span data-stu-id="65b5b-111">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md); if the method is instrumented, its IL will not be accessible.</span></span> <span data-ttu-id="65b5b-112">`ILCODE_REJIT_IL` Profil Oluşturucu'nın ReJIT isteği tarafından tanımlanan IL erişmek hata ayıklayıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="65b5b-112">`ILCODE_REJIT_IL` allows the debugger to access the IL defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="65b5b-113">IL izlenmemektedir, `ppCode` olan **null**, ve yöntemi `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="65b5b-113">If the IL is not instrumented, `ppCode` is **null**, and the method returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65b5b-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="65b5b-114">Requirements</span></span>  
 <span data-ttu-id="65b5b-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65b5b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65b5b-116">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="65b5b-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="65b5b-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65b5b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65b5b-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65b5b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65b5b-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="65b5b-119">See Also</span></span>  
 [<span data-ttu-id="65b5b-120">ICorDebugILFrame4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="65b5b-120">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [<span data-ttu-id="65b5b-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="65b5b-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="65b5b-122">ReJIT: Nasıl yapılır Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="65b5b-122">ReJIT: A How-To Guide</span></span>](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
