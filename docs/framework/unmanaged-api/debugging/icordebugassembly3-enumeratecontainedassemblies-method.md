---
title: ICorDebugAssembly3::EnumerateContainedAssemblies Yöntemi
ms.date: 03/30/2017
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 54ccb52468a530280527252e0e0c43cc9edbb2c3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59080962"
---
# <a name="icordebugassembly3enumeratecontainedassemblies-method"></a><span data-ttu-id="dda6d-102">ICorDebugAssembly3::EnumerateContainedAssemblies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dda6d-102">ICorDebugAssembly3::EnumerateContainedAssemblies Method</span></span>
<span data-ttu-id="dda6d-103">Bu derlemede bulunan derlemeler için bir numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="dda6d-103">Gets an enumerator for the assemblies contained in this assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dda6d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dda6d-104">Syntax</span></span>  
  
```  
HRESULT EnumerateContainedAssemblies(  
    ICorDebugAssemblyEnum **ppAssemblies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dda6d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dda6d-105">Parameters</span></span>  
 `ppAssemblies`  
 <span data-ttu-id="dda6d-106">[out] Numaralandırıcı Icordebugassemblyenum arabirimi nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="dda6d-106">[out] A pointer to the address of an ICorDebugAssemblyEnum interface object that is the enumerator.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dda6d-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="dda6d-107">Return Value</span></span>  
 <span data-ttu-id="dda6d-108">`S_OK` Bu `ICorDebugAssembly3` nesne bir kapsayıcıdır; Aksi takdirde `S_FALSE`, ve sabit listesi boş.</span><span class="sxs-lookup"><span data-stu-id="dda6d-108">`S_OK` if this `ICorDebugAssembly3` object is a container; otherwise, `S_FALSE`, and the enumeration is empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dda6d-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dda6d-109">Remarks</span></span>  
 <span data-ttu-id="dda6d-110">Semboller kapsanan derlemeleri numaralandırmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="dda6d-110">Symbols are needed to enumerate the contained assemblies.</span></span> <span data-ttu-id="dda6d-111">Bunlar mevcut değil ise, yöntem döndürür `S_FALSE`, ve geçerli hiçbir Numaralandırıcı sağlanır.</span><span class="sxs-lookup"><span data-stu-id="dda6d-111">If they aren't present, the method returns `S_FALSE`, and no valid enumerator is provided.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dda6d-112">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dda6d-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dda6d-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dda6d-113">Requirements</span></span>  
 <span data-ttu-id="dda6d-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dda6d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dda6d-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dda6d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dda6d-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dda6d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dda6d-117">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dda6d-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dda6d-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dda6d-118">See also</span></span>

- [<span data-ttu-id="dda6d-119">ICorDebugAssembly3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dda6d-119">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)
- [<span data-ttu-id="dda6d-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="dda6d-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
