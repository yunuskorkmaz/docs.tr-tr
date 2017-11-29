---
title: ICorDebugAssembly3::GetContainerAssembly Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f9a32520c2a67c0bc51a3f88e9822db49e4a3974
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugassembly3getcontainerassembly-method"></a><span data-ttu-id="e1a7e-102">ICorDebugAssembly3::GetContainerAssembly Metodu</span><span class="sxs-lookup"><span data-stu-id="e1a7e-102">ICorDebugAssembly3::GetContainerAssembly Method</span></span>
<span data-ttu-id="e1a7e-103">Bu kapsayıcı derleme döndürür `ICorDebugAssembly3` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="e1a7e-103">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1a7e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e1a7e-104">Syntax</span></span>  
  
```  
HRESULT GetContainerAssembly(  
    ICorDebugAssembly **ppAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e1a7e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e1a7e-105">Parameters</span></span>  
 `ppAssembly`  
 <span data-ttu-id="e1a7e-106">Kapsayıcı derleme temsil eden Icordebugassembly nesne adresini gösteren bir işaretçi veya **null** yöntem çağrısının başarısız olursa.</span><span class="sxs-lookup"><span data-stu-id="e1a7e-106">A pointer to the address of an ICorDebugAssembly object that represents the container assembly, or **null** if the method call fails.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e1a7e-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e1a7e-107">Return Value</span></span>  
 <span data-ttu-id="e1a7e-108">`S_OK`yöntem çağrısının başarılı olursa; Aksi takdirde, `S_FALSE`, ve `ppAssembly` olan **null**.</span><span class="sxs-lookup"><span data-stu-id="e1a7e-108">`S_OK` if the method call succeeds; otherwise, `S_FALSE`, and `ppAssembly` is **null**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1a7e-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e1a7e-109">Remarks</span></span>  
 <span data-ttu-id="e1a7e-110">Bu derleme başkalarıyla tek kapsayıcı derleme içinde birleştirilmedi varsa, bu yöntem kapsayıcı derleme döndürür.</span><span class="sxs-lookup"><span data-stu-id="e1a7e-110">If this assembly has been merged with others inside a single container assembly, this method returns the container assembly.</span></span> <span data-ttu-id="e1a7e-111">Daha fazla bilgi ve terimler için bkz: [Icordebugprocess6::enablevirtualmodulesplitting](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md) konu.</span><span class="sxs-lookup"><span data-stu-id="e1a7e-111">For more information and terminology, see the [ICorDebugProcess6::EnableVirtualModuleSplitting](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md) topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e1a7e-112">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e1a7e-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1a7e-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e1a7e-113">Requirements</span></span>  
 <span data-ttu-id="e1a7e-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1a7e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1a7e-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e1a7e-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e1a7e-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e1a7e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1a7e-117">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1a7e-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1a7e-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e1a7e-118">See Also</span></span>  
 [<span data-ttu-id="e1a7e-119">Icordebugassembly3 arabirimi</span><span class="sxs-lookup"><span data-stu-id="e1a7e-119">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)  
 [<span data-ttu-id="e1a7e-120">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e1a7e-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
