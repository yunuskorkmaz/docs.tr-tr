---
title: "ICorDebugMergedAssemblyRecord::GetVersion yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 68fa2b1b7502f13876c6e613f012a0c78ab7c5d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a><span data-ttu-id="71906-102">ICorDebugMergedAssemblyRecord::GetVersion yöntemi</span><span class="sxs-lookup"><span data-stu-id="71906-102">ICorDebugMergedAssemblyRecord::GetVersion Method</span></span>
<span data-ttu-id="71906-103">Derlemenin sürüm bilgisi alır.</span><span class="sxs-lookup"><span data-stu-id="71906-103">Gets the assembly's version information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71906-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="71906-104">Syntax</span></span>  
  
```  
HRESULT GetVersion(  
   [out] USHORT *pMajor,   
   [out] USHORT *pMinor,   
   [out] USHORT *pBuild,   
   [out] USHORT *pRevision  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="71906-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="71906-105">Parameters</span></span>  
 `pMajor`  
 <span data-ttu-id="71906-106">[out] Ana sürüm numarasını gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="71906-106">[out] A pointer to the major version number.</span></span>  
  
 `pMinor`  
 <span data-ttu-id="71906-107">[out] Alt sürüm numarasını gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="71906-107">[out] A pointer to the minor version number.</span></span>  
  
 `pBuild`  
 <span data-ttu-id="71906-108">[out] Yapı numarası için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="71906-108">[out] A pointer to the build number.</span></span>  
  
 `pRevision`  
 <span data-ttu-id="71906-109">[out] Düzeltme numarası için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="71906-109">[out] A pointer to the revision number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71906-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="71906-110">Remarks</span></span>  
 <span data-ttu-id="71906-111">Derleme sürüm numaraları hakkında daha fazla bilgi için bkz: <xref:System.Version> sınıfı konu.</span><span class="sxs-lookup"><span data-stu-id="71906-111">For information on assembly version numbers, see the <xref:System.Version> class topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="71906-112">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="71906-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71906-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="71906-113">Requirements</span></span>  
 <span data-ttu-id="71906-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71906-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71906-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="71906-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="71906-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="71906-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="71906-117">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71906-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71906-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="71906-118">See Also</span></span>  
 [<span data-ttu-id="71906-119">ICorDebugMergedAssemblyRecord arabirimi</span><span class="sxs-lookup"><span data-stu-id="71906-119">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [<span data-ttu-id="71906-120">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="71906-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
