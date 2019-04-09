---
title: ICorDebugMergedAssemblyRecord::GetVersion yöntemi
ms.date: 03/30/2017
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36cf8647b3caafeaae2db3c2fd53471496e922fa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59109545"
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a><span data-ttu-id="eec39-102">ICorDebugMergedAssemblyRecord::GetVersion yöntemi</span><span class="sxs-lookup"><span data-stu-id="eec39-102">ICorDebugMergedAssemblyRecord::GetVersion Method</span></span>
<span data-ttu-id="eec39-103">Derlemenin sürüm bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="eec39-103">Gets the assembly's version information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eec39-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eec39-104">Syntax</span></span>  
  
```  
HRESULT GetVersion(  
   [out] USHORT *pMajor,   
   [out] USHORT *pMinor,   
   [out] USHORT *pBuild,   
   [out] USHORT *pRevision  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eec39-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="eec39-105">Parameters</span></span>  
 `pMajor`  
 <span data-ttu-id="eec39-106">[out] Ana sürüm numarası bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="eec39-106">[out] A pointer to the major version number.</span></span>  
  
 `pMinor`  
 <span data-ttu-id="eec39-107">[out] Alt sürüm numarasını bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="eec39-107">[out] A pointer to the minor version number.</span></span>  
  
 `pBuild`  
 <span data-ttu-id="eec39-108">[out] Yapı numarası bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="eec39-108">[out] A pointer to the build number.</span></span>  
  
 `pRevision`  
 <span data-ttu-id="eec39-109">[out] Düzeltme numarası için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="eec39-109">[out] A pointer to the revision number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eec39-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eec39-110">Remarks</span></span>  
 <span data-ttu-id="eec39-111">Derleme sürüm numaraları hakkında daha fazla bilgi için bkz: <xref:System.Version> sınıf konusuna.</span><span class="sxs-lookup"><span data-stu-id="eec39-111">For information on assembly version numbers, see the <xref:System.Version> class topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eec39-112">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="eec39-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eec39-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eec39-113">Requirements</span></span>  
 <span data-ttu-id="eec39-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eec39-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eec39-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eec39-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eec39-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eec39-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="eec39-117">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="eec39-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="eec39-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eec39-118">See also</span></span>

- [<span data-ttu-id="eec39-119">ICorDebugMergedAssemblyRecord Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eec39-119">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="eec39-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="eec39-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
