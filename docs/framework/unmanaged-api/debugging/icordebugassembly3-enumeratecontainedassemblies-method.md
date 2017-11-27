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
ms.openlocfilehash: b927d065f26a13d496aec8cd6c8cbc69cf3a8bc9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugassembly3enumeratecontainedassemblies-method"></a><span data-ttu-id="e7576-102">ICorDebugAssembly3::EnumerateContainedAssemblies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e7576-102">ICorDebugAssembly3::EnumerateContainedAssemblies Method</span></span>
<span data-ttu-id="e7576-103">Bu derlemede bulunan derlemeler için bir numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="e7576-103">Gets an enumerator for the assemblies contained in this assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7576-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e7576-104">Syntax</span></span>  
  
```  
HRESULT EnumerateContainedAssemblies(  
    ICorDebugAssemblyEnum **ppAssemblies  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e7576-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e7576-105">Parameters</span></span>  
 `ppAssemblies`  
 <span data-ttu-id="e7576-106">[out] Numaralayıcı bir Icordebugassemblyenum arabirimi nesne adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e7576-106">[out] A pointer to the address of an ICorDebugAssemblyEnum interface object that is the enumerator.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e7576-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e7576-107">Return Value</span></span>  
 <span data-ttu-id="e7576-108">`S_OK`Bu `ICorDebugAssembly3` nesnesi bir kapsayıcıdır; Aksi halde, `S_FALSE`, ve numaralandırma boştur.</span><span class="sxs-lookup"><span data-stu-id="e7576-108">`S_OK` if this `ICorDebugAssembly3` object is a container; otherwise, `S_FALSE`, and the enumeration is empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7576-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e7576-109">Remarks</span></span>  
 <span data-ttu-id="e7576-110">Simgeler kapsanan derlemeleri numaralandırmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e7576-110">Symbols are needed to enumerate the contained assemblies.</span></span> <span data-ttu-id="e7576-111">Bunlar mevcut değil ise, yöntem döndürür `S_FALSE`, ve hiçbir geçerli Numaralandırıcı sağlanır.</span><span class="sxs-lookup"><span data-stu-id="e7576-111">If they aren't present, the method returns `S_FALSE`, and no valid enumerator is provided.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e7576-112">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e7576-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7576-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e7576-113">Requirements</span></span>  
 <span data-ttu-id="e7576-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7576-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7576-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e7576-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e7576-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7576-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7576-117">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7576-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7576-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e7576-118">See Also</span></span>  
 [<span data-ttu-id="e7576-119">Icordebugassembly3 arabirimi</span><span class="sxs-lookup"><span data-stu-id="e7576-119">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)  
 [<span data-ttu-id="e7576-120">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e7576-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
