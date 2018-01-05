---
title: "ICorDebugAssembly3::EnumerateContainedAssemblies Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8633ce497cd282303c46692a942fe5f88be444c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugassembly3enumeratecontainedassemblies-method"></a><span data-ttu-id="d7142-102">ICorDebugAssembly3::EnumerateContainedAssemblies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d7142-102">ICorDebugAssembly3::EnumerateContainedAssemblies Method</span></span>
<span data-ttu-id="d7142-103">Bu derlemede bulunan derlemeler için bir numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="d7142-103">Gets an enumerator for the assemblies contained in this assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7142-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d7142-104">Syntax</span></span>  
  
```  
HRESULT EnumerateContainedAssemblies(  
    ICorDebugAssemblyEnum **ppAssemblies  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d7142-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d7142-105">Parameters</span></span>  
 `ppAssemblies`  
 <span data-ttu-id="d7142-106">[out] Numaralayıcı bir Icordebugassemblyenum arabirimi nesne adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d7142-106">[out] A pointer to the address of an ICorDebugAssemblyEnum interface object that is the enumerator.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d7142-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d7142-107">Return Value</span></span>  
 <span data-ttu-id="d7142-108">`S_OK`Bu `ICorDebugAssembly3` nesnesi bir kapsayıcıdır; Aksi halde, `S_FALSE`, ve numaralandırma boştur.</span><span class="sxs-lookup"><span data-stu-id="d7142-108">`S_OK` if this `ICorDebugAssembly3` object is a container; otherwise, `S_FALSE`, and the enumeration is empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7142-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d7142-109">Remarks</span></span>  
 <span data-ttu-id="d7142-110">Simgeler kapsanan derlemeleri numaralandırmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d7142-110">Symbols are needed to enumerate the contained assemblies.</span></span> <span data-ttu-id="d7142-111">Bunlar mevcut değil ise, yöntem döndürür `S_FALSE`, ve hiçbir geçerli Numaralandırıcı sağlanır.</span><span class="sxs-lookup"><span data-stu-id="d7142-111">If they aren't present, the method returns `S_FALSE`, and no valid enumerator is provided.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d7142-112">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d7142-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7142-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d7142-113">Requirements</span></span>  
 <span data-ttu-id="d7142-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7142-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7142-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d7142-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7142-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7142-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7142-117">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7142-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7142-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d7142-118">See Also</span></span>  
 [<span data-ttu-id="d7142-119">ICorDebugAssembly3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d7142-119">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)  
 [<span data-ttu-id="d7142-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d7142-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
