---
title: ICorDebugAssembly3::EnumerateContainedAssemblies Yöntemi
ms.date: 03/30/2017
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 54ccb52468a530280527252e0e0c43cc9edbb2c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645480"
---
# <a name="icordebugassembly3enumeratecontainedassemblies-method"></a><span data-ttu-id="c7064-102">ICorDebugAssembly3::EnumerateContainedAssemblies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c7064-102">ICorDebugAssembly3::EnumerateContainedAssemblies Method</span></span>
<span data-ttu-id="c7064-103">Bu derlemede bulunan derlemeler için bir numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="c7064-103">Gets an enumerator for the assemblies contained in this assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7064-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c7064-104">Syntax</span></span>  
  
```  
HRESULT EnumerateContainedAssemblies(  
    ICorDebugAssemblyEnum **ppAssemblies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7064-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c7064-105">Parameters</span></span>  
 `ppAssemblies`  
 <span data-ttu-id="c7064-106">[out] Numaralandırıcı Icordebugassemblyenum arabirimi nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c7064-106">[out] A pointer to the address of an ICorDebugAssemblyEnum interface object that is the enumerator.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c7064-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c7064-107">Return Value</span></span>  
 <span data-ttu-id="c7064-108">`S_OK` Bu `ICorDebugAssembly3` nesne bir kapsayıcıdır; Aksi takdirde `S_FALSE`, ve sabit listesi boş.</span><span class="sxs-lookup"><span data-stu-id="c7064-108">`S_OK` if this `ICorDebugAssembly3` object is a container; otherwise, `S_FALSE`, and the enumeration is empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7064-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c7064-109">Remarks</span></span>  
 <span data-ttu-id="c7064-110">Semboller kapsanan derlemeleri numaralandırmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c7064-110">Symbols are needed to enumerate the contained assemblies.</span></span> <span data-ttu-id="c7064-111">Bunlar mevcut değil ise, yöntem döndürür `S_FALSE`, ve geçerli hiçbir Numaralandırıcı sağlanır.</span><span class="sxs-lookup"><span data-stu-id="c7064-111">If they aren't present, the method returns `S_FALSE`, and no valid enumerator is provided.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c7064-112">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c7064-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7064-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c7064-113">Requirements</span></span>  
 <span data-ttu-id="c7064-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7064-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7064-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c7064-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c7064-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7064-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7064-117">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7064-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7064-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7064-118">See also</span></span>

- [<span data-ttu-id="c7064-119">ICorDebugAssembly3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c7064-119">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)
- [<span data-ttu-id="c7064-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c7064-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
