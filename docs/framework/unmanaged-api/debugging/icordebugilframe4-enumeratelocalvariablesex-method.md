---
title: ICorDebugILFrame4::EnumerateLocalVariablesEx Yöntemi
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.EnumerateLocalVariablesEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6f60aae6-70ec-4c4c-963a-138df98c4668
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4f9d20eda8684a9a5ae43c6240d0f8a9722c4d97
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59076841"
---
# <a name="icordebugilframe4enumeratelocalvariablesex-method"></a><span data-ttu-id="353e5-102">ICorDebugILFrame4::EnumerateLocalVariablesEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="353e5-102">ICorDebugILFrame4::EnumerateLocalVariablesEx Method</span></span>
<span data-ttu-id="353e5-103">[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="353e5-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="353e5-104">Bir numaralandırıcı yerel değişken için çerçeveyi alır ve isteğe bağlı olarak ReJIT izleme profil oluşturucu, eklenen değişkenler içerir.</span><span class="sxs-lookup"><span data-stu-id="353e5-104">Gets an enumerator for the local variable in the frame, and optionally includes variables added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="353e5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="353e5-105">Syntax</span></span>  
  
```cpp
HRESULT EnumerateLocalVariablesEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugValueEnum **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="353e5-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="353e5-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="353e5-107">[in] Bir [Ilcodekind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) çerçevede ReJIT izleme profil oluşturucu, eklenen değişkenleri dahil edilip edilmeyeceğini belirten sabit listesi üyesi.</span><span class="sxs-lookup"><span data-stu-id="353e5-107">[in] An [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) enumeration member that specifies whether variables added in profiler ReJIT instrumentation are included in the frame.</span></span>  
  
 `ppValueEnum`  
 <span data-ttu-id="353e5-108">[out] Numaralandırıcı bu çerçevesinde yerel değişkenler için bir "ICorDebugValueEnum" Nesne adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="353e5-108">[out] A pointer to the address of an "ICorDebugValueEnum" object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="353e5-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="353e5-109">Remarks</span></span>  
 <span data-ttu-id="353e5-110">Bu yöntem benzer [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md) dışında olan isteğe bağlı olarak ReJIT izleme profil oluşturucu, eklenen değişkenlere erişimi yöntemi.</span><span class="sxs-lookup"><span data-stu-id="353e5-110">This method is similar to the [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md) method, except that it optionally accesses variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="353e5-111">Ayarı `flags` için `ILCODE_ORIGINAL_IL` çağırmakla eşdeğerdir [Icordebugılframe::enumeratelocalvariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md).</span><span class="sxs-lookup"><span data-stu-id="353e5-111">Setting `flags` to `ILCODE_ORIGINAL_IL` is equivalent to calling [ICorDebugILFrame::EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md).</span></span> <span data-ttu-id="353e5-112">Ayarı `flags` için `ILCODE_REJIT_IL` ReJIT izleme profil oluşturucu, eklenen yerel değişkenlere erişmek hata ayıklayıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="353e5-112">Setting `flags` to `ILCODE_REJIT_IL` allows the debugger to access the local variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="353e5-113">Ara dil (IL) izlenmiyor numaralandırma boştur ve yöntemi döndürür `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="353e5-113">If the intermediate language (IL) is not instrumented, the enumeration is empty and the method returns `S_OK`.</span></span>  
  
 <span data-ttu-id="353e5-114">Bunlardan bazıları etkin olmayabilir olduğundan Numaralandırıcı çalışan yönteminde, tüm yerel değişkenlerin içermeyebilir.</span><span class="sxs-lookup"><span data-stu-id="353e5-114">The enumerator may not include all of the local variables in the running method, since some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="353e5-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="353e5-115">Requirements</span></span>  
 <span data-ttu-id="353e5-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="353e5-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="353e5-117">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="353e5-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="353e5-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="353e5-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="353e5-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="353e5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="353e5-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="353e5-120">See also</span></span>

- [<span data-ttu-id="353e5-121">ICorDebugILFrame4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="353e5-121">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)
- [<span data-ttu-id="353e5-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="353e5-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="353e5-123">ReJIT: Nasıl yapılır Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="353e5-123">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
