---
title: "ICorDebugILFrame4::EnumerateLocalVariablesEx Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorDebugILFrame4.EnumerateLocalVariablesEx
api_location: mscordbi.dll
api_type: COM
ms.assetid: 6f60aae6-70ec-4c4c-963a-138df98c4668
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c82ecd9045deb772e31e549bf1050f85b148fd0b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframe4enumeratelocalvariablesex-method"></a><span data-ttu-id="de6f4-102">ICorDebugILFrame4::EnumerateLocalVariablesEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="de6f4-102">ICorDebugILFrame4::EnumerateLocalVariablesEx Method</span></span>
<span data-ttu-id="de6f4-103">[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="de6f4-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="de6f4-104">Çerçevede yerel değişken için bir numaralandırıcı alır ve isteğe bağlı olarak profiler ReJIT araçları eklenen değişkenleri içerir.</span><span class="sxs-lookup"><span data-stu-id="de6f4-104">Gets an enumerator for the local variable in the frame, and optionally includes variables added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de6f4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="de6f4-105">Syntax</span></span>  
  
```cpp
HRESULT EnumerateLocalVariablesEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugValueEnum **ppValueEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="de6f4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="de6f4-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="de6f4-107">[in] Bir [Ilcodekind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) profiler ReJIT araçları eklenen değişkenleri çerçevede dahil edilip edilmediğini belirten numaralandırma üyesi.</span><span class="sxs-lookup"><span data-stu-id="de6f4-107">[in] An [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) enumeration member that specifies whether variables added in profiler ReJIT instrumentation are included in the frame.</span></span>  
  
 `ppValueEnum`  
 <span data-ttu-id="de6f4-108">[out] Bu çerçeve yerel değişkenleri için Numaralandırıcı bir "ICorDebugValueEnum" nesne adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="de6f4-108">[out] A pointer to the address of an "ICorDebugValueEnum" object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de6f4-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="de6f4-109">Remarks</span></span>  
 <span data-ttu-id="de6f4-110">Bu yöntem benzer [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md) olan isteğe bağlı olarak profiler ReJIT araçları eklenen değişkenleri erişen dışında yöntemi.</span><span class="sxs-lookup"><span data-stu-id="de6f4-110">This method is similar to the [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md) method, except that it optionally accesses variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="de6f4-111">Ayarı `flags` için `ILCODE_ORIGINAL_IL` arama için eşdeğer bir gruba [Icordebugılframe::enumeratelocalvariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md).</span><span class="sxs-lookup"><span data-stu-id="de6f4-111">Setting `flags` to `ILCODE_ORIGINAL_IL` is equivalent to calling [ICorDebugILFrame::EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md).</span></span> <span data-ttu-id="de6f4-112">Ayarı `flags` için `ILCODE_REJIT_IL` profiler ReJIT araçları eklenen yerel değişkenler erişmek hata ayıklayıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="de6f4-112">Setting `flags` to `ILCODE_REJIT_IL` allows the debugger to access the local variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="de6f4-113">Ara dile (IL) değil izlenmiş numaralandırması boştur ve yöntemi döndürür `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="de6f4-113">If the intermediate language (IL) is not instrumented, the enumeration is empty and the method returns `S_OK`.</span></span>  
  
 <span data-ttu-id="de6f4-114">Bunlardan bazıları etkin olmayabilir beri Numaralandırıcı çalışan yönteminde tüm yerel değişkenleri içermeyebilir.</span><span class="sxs-lookup"><span data-stu-id="de6f4-114">The enumerator may not include all of the local variables in the running method, since some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de6f4-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="de6f4-115">Requirements</span></span>  
 <span data-ttu-id="de6f4-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de6f4-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de6f4-117">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="de6f4-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="de6f4-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="de6f4-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="de6f4-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de6f4-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de6f4-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="de6f4-120">See Also</span></span>  
 [<span data-ttu-id="de6f4-121">ICorDebugILFrame4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="de6f4-121">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [<span data-ttu-id="de6f4-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="de6f4-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="de6f4-123">ReJIT: Nasıl yapılır Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="de6f4-123">ReJIT: A How-To Guide</span></span>](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
