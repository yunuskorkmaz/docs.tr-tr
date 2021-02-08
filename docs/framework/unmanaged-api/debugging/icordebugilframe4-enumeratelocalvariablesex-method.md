---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugILFrame4:: EnumerateLocalVariablesEx Yöntemi'
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
ms.openlocfilehash: 8808b1ac337304ab37a35f7733b317dad274d48e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791250"
---
# <a name="icordebugilframe4enumeratelocalvariablesex-method"></a><span data-ttu-id="5019d-103">ICorDebugILFrame4::EnumerateLocalVariablesEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5019d-103">ICorDebugILFrame4::EnumerateLocalVariablesEx Method</span></span>

<span data-ttu-id="5019d-104">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="5019d-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="5019d-105">Çerçevede yerel değişken için bir Numaralandırıcı alır ve isteğe bağlı olarak profil oluşturucu yeniden JIT araçlarına eklenen değişkenleri içerir.</span><span class="sxs-lookup"><span data-stu-id="5019d-105">Gets an enumerator for the local variable in the frame, and optionally includes variables added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5019d-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5019d-106">Syntax</span></span>  
  
```cpp
HRESULT EnumerateLocalVariablesEx(  
   [in] ILCodeKind flags,
   [out] ICorDebugValueEnum **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5019d-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5019d-107">Parameters</span></span>  

 `flags`  
 <span data-ttu-id="5019d-108">'ndaki Profil Oluşturucu yeniden JIT araçlarına eklenen değişkenlerin çerçeveye dahil edilip edilmeyeceğini belirten bir [ılcodekind](ilcodekind-enumeration.md) numaralandırma üyesi.</span><span class="sxs-lookup"><span data-stu-id="5019d-108">[in] An [ILCodeKind](ilcodekind-enumeration.md) enumeration member that specifies whether variables added in profiler ReJIT instrumentation are included in the frame.</span></span>  
  
 `ppValueEnum`  
 <span data-ttu-id="5019d-109">dışı Bu çerçevedeki yerel değişkenlerin numaralandırıcısının bulunduğu bir "ICorDebugValueEnum" nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5019d-109">[out] A pointer to the address of an "ICorDebugValueEnum" object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5019d-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5019d-110">Remarks</span></span>  

 <span data-ttu-id="5019d-111">Bu yöntem, isteğe bağlı olarak profil oluşturucu yeniden JIT araçları 'nda eklenen değişkenlere erişmesi dışında, [EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md) yöntemine benzerdir.</span><span class="sxs-lookup"><span data-stu-id="5019d-111">This method is similar to the [EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md) method, except that it optionally accesses variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="5019d-112">Ayarı `flags` `ILCODE_ORIGINAL_IL` [ICorDebugILFrame:: EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md)çağırma ile eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="5019d-112">Setting `flags` to `ILCODE_ORIGINAL_IL` is equivalent to calling [ICorDebugILFrame::EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md).</span></span> <span data-ttu-id="5019d-113">`flags`İçin ayarı `ILCODE_REJIT_IL` , hata ayıklayıcının profil oluşturucu ReJIT araçları 'nda eklenen yerel değişkenlere erişmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="5019d-113">Setting `flags` to `ILCODE_REJIT_IL` allows the debugger to access the local variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="5019d-114">Ara dil (IL) görünmüyorsa, numaralandırma boştur ve yöntemi döndürülür `S_OK` .</span><span class="sxs-lookup"><span data-stu-id="5019d-114">If the intermediate language (IL) is not instrumented, the enumeration is empty and the method returns `S_OK`.</span></span>  
  
 <span data-ttu-id="5019d-115">Numaralandırıcı etkin olmayabilir, bu, çalışan yöntemdeki tüm yerel değişkenleri içermeyebilir.</span><span class="sxs-lookup"><span data-stu-id="5019d-115">The enumerator may not include all of the local variables in the running method, since some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5019d-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5019d-116">Requirements</span></span>  

 <span data-ttu-id="5019d-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5019d-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5019d-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5019d-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5019d-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5019d-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5019d-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5019d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5019d-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5019d-121">See also</span></span>

- [<span data-ttu-id="5019d-122">ICorDebugILFrame4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5019d-122">ICorDebugILFrame4 Interface</span></span>](icordebugilframe4-interface.md)
- [<span data-ttu-id="5019d-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5019d-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="5019d-124">ReJIT: A How-To Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5019d-124">ReJIT: A How-To Guide</span></span>](/archive/blogs/davbr/rejit-a-how-to-guide)
