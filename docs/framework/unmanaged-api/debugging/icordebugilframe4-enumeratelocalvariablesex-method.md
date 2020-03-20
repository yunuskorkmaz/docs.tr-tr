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
ms.openlocfilehash: 341a86f4c1c8367f979e193a6284bf89f1b03ca0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178799"
---
# <a name="icordebugilframe4enumeratelocalvariablesex-method"></a><span data-ttu-id="939be-102">ICorDebugILFrame4::EnumerateLocalVariablesEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="939be-102">ICorDebugILFrame4::EnumerateLocalVariablesEx Method</span></span>
<span data-ttu-id="939be-103">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="939be-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="939be-104">Çerçevedeki yerel değişken için bir sayıyalı madde alır ve isteğe bağlı olarak profil oluşturucu ReJIT enstrümantasyonuna eklenen değişkenleri içerir.</span><span class="sxs-lookup"><span data-stu-id="939be-104">Gets an enumerator for the local variable in the frame, and optionally includes variables added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="939be-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="939be-105">Syntax</span></span>  
  
```cpp
HRESULT EnumerateLocalVariablesEx(  
   [in] ILCodeKind flags,
   [out] ICorDebugValueEnum **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="939be-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="939be-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="939be-107">[içinde] Profiloluşturr ReJIT enstrümantasyonuna eklenen değişkenlerin çerçeveye dahil edilip edilmeyeceğini belirten bir [ILCodeKind](ilcodekind-enumeration.md) numaralandırma üyesi.</span><span class="sxs-lookup"><span data-stu-id="939be-107">[in] An [ILCodeKind](ilcodekind-enumeration.md) enumeration member that specifies whether variables added in profiler ReJIT instrumentation are included in the frame.</span></span>  
  
 `ppValueEnum`  
 <span data-ttu-id="939be-108">[çıkış] Bu çerçevedeki yerel değişkenlerin sayıcısı olan "ICorDebugValueEnum" nesnesinin adresine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="939be-108">[out] A pointer to the address of an "ICorDebugValueEnum" object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="939be-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="939be-109">Remarks</span></span>  
 <span data-ttu-id="939be-110">Bu yöntem, profiler ReJIT enstrümantasyonuna eklenen değişkenlere isteğe bağlı olarak erişilmesi dışında, [EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md) yöntemine benzer.</span><span class="sxs-lookup"><span data-stu-id="939be-110">This method is similar to the [EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md) method, except that it optionally accesses variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="939be-111">Ayar `flags` `ILCODE_ORIGINAL_IL` [iCorDebugILFrame::EnumerateLocalVariables arama eşdeğerdir.](icordebugilframe-enumeratelocalvariables-method.md)</span><span class="sxs-lookup"><span data-stu-id="939be-111">Setting `flags` to `ILCODE_ORIGINAL_IL` is equivalent to calling [ICorDebugILFrame::EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md).</span></span> <span data-ttu-id="939be-112">`flags` Hata `ILCODE_REJIT_IL` ayıklayıcının profil oluşturucu ReJIT enstrümantasyonuna eklenen yerel değişkenlere erişmesine olanak sağlayacak ayar.</span><span class="sxs-lookup"><span data-stu-id="939be-112">Setting `flags` to `ILCODE_REJIT_IL` allows the debugger to access the local variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="939be-113">Ara dil (IL) enstrümantasyon aletli değilse, numaralandırma boştur ve yöntem döndürür. `S_OK`</span><span class="sxs-lookup"><span data-stu-id="939be-113">If the intermediate language (IL) is not instrumented, the enumeration is empty and the method returns `S_OK`.</span></span>  
  
 <span data-ttu-id="939be-114">Enumerator, bazıları etkin olmayabilir, çünkü çalışan yöntemde tüm yerel değişkenleri içermeyebilir.</span><span class="sxs-lookup"><span data-stu-id="939be-114">The enumerator may not include all of the local variables in the running method, since some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="939be-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="939be-115">Requirements</span></span>  
 <span data-ttu-id="939be-116">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="939be-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="939be-117">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="939be-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="939be-118">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="939be-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="939be-119">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="939be-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="939be-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="939be-120">See also</span></span>

- [<span data-ttu-id="939be-121">ICorDebugILFrame4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="939be-121">ICorDebugILFrame4 Interface</span></span>](icordebugilframe4-interface.md)
- [<span data-ttu-id="939be-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="939be-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="939be-123">ReJIT: Nasıl Yapilir Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="939be-123">ReJIT: A How-To Guide</span></span>](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
