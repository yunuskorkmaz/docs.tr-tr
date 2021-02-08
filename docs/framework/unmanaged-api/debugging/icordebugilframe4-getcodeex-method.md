---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugILFrame4:: GetCodeEx yöntemi'
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
ms.openlocfilehash: 1d17dfa531354b8a4b0dd3c0d3d2eb47206900cc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791237"
---
# <a name="icordebugilframe4getcodeex-method"></a><span data-ttu-id="c9776-103">ICorDebugILFrame4::GetCodeEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c9776-103">ICorDebugILFrame4::GetCodeEx Method</span></span>

<span data-ttu-id="c9776-104">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="c9776-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="c9776-105">Bu yığın çerçevesinin yürütüldüğü koda yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="c9776-105">Gets a pointer to the code that this stack frame is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9776-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c9776-106">Syntax</span></span>  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,
   [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9776-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c9776-107">Parameters</span></span>  

 `flags`  
 <span data-ttu-id="c9776-108">'ndaki Profiler 'ın ReJIT isteği tarafından tanımlanan ara dilin (IL) çerçeveye dahil edilip edilmeyeceğini belirten bir [ılcodekind](ilcodekind-enumeration.md) numaralandırma üyesi.</span><span class="sxs-lookup"><span data-stu-id="c9776-108">[in] An [ILCodeKind](ilcodekind-enumeration.md) enumeration member that specifies whether the intermediate language (IL) defined by the profiler's ReJIT request is included in the frame.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="c9776-109">dışı Bu yığın çerçevesinin yürütüldüğü kodu temsil eden bir "ICorDebugCode" nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c9776-109">[out] A pointer to the address of an "ICorDebugCode" object that represents the code that this stack frame is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9776-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c9776-110">Remarks</span></span>  

 <span data-ttu-id="c9776-111">Bu yöntem [ICorDebugFrame:: GetCode](icordebugframe-getcode-method.md) yöntemine benzer, isteğe bağlı olarak Profiler 'ın ReJIT isteği tarafından tanımlanan koda erişir.</span><span class="sxs-lookup"><span data-stu-id="c9776-111">This method is similar to the [ICorDebugFrame::GetCode](icordebugframe-getcode-method.md) method, except that it optionally accesses code defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="c9776-112">Bu yöntemin bir değeriyle çağrılması `flags` `ILCODE_ORIGINAL_IL` [GetCode](icordebugframe-getcode-method.md)çağırma ile eşdeğerdir; Eğer Eğer Eğer Eğer Eğer Eğer bu yöntem BELGELENMIŞ ise, onun Il 'ye erişilemeyecektir.</span><span class="sxs-lookup"><span data-stu-id="c9776-112">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetCode](icordebugframe-getcode-method.md); if the method is instrumented, its IL will not be accessible.</span></span> <span data-ttu-id="c9776-113">`ILCODE_REJIT_IL` hata ayıklayıcının profil oluşturucunun ReJIT isteği tarafından tanımlanan Il 'ye erişmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="c9776-113">`ILCODE_REJIT_IL` allows the debugger to access the IL defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="c9776-114">Il görünmüyorsa, `ppCode` **null** olur ve yöntemi döndürür `S_OK` .</span><span class="sxs-lookup"><span data-stu-id="c9776-114">If the IL is not instrumented, `ppCode` is **null**, and the method returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9776-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c9776-115">Requirements</span></span>  

 <span data-ttu-id="c9776-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9776-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9776-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c9776-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c9776-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c9776-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9776-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9776-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9776-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9776-120">See also</span></span>

- [<span data-ttu-id="c9776-121">ICorDebugILFrame4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c9776-121">ICorDebugILFrame4 Interface</span></span>](icordebugilframe4-interface.md)
- [<span data-ttu-id="c9776-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c9776-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="c9776-123">ReJIT: A How-To Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c9776-123">ReJIT: A How-To Guide</span></span>](/archive/blogs/davbr/rejit-a-how-to-guide)
