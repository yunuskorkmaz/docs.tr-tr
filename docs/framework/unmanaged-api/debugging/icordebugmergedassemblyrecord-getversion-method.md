---
title: 'Icordebugmergedassemblyrecord:: GetVersion yöntemi'
ms.date: 03/30/2017
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7d9133ab1b7d3985d3a383bb36dcbea315548c00
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939923"
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a><span data-ttu-id="7da6d-102">Icordebugmergedassemblyrecord:: GetVersion yöntemi</span><span class="sxs-lookup"><span data-stu-id="7da6d-102">ICorDebugMergedAssemblyRecord::GetVersion Method</span></span>
<span data-ttu-id="7da6d-103">Derlemenin sürüm bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="7da6d-103">Gets the assembly's version information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7da6d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7da6d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersion(  
   [out] USHORT *pMajor,   
   [out] USHORT *pMinor,   
   [out] USHORT *pBuild,   
   [out] USHORT *pRevision  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7da6d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7da6d-105">Parameters</span></span>  
 `pMajor`  
 <span data-ttu-id="7da6d-106">dışı Ana sürüm numarasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7da6d-106">[out] A pointer to the major version number.</span></span>  
  
 `pMinor`  
 <span data-ttu-id="7da6d-107">dışı Küçük sürüm numarasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7da6d-107">[out] A pointer to the minor version number.</span></span>  
  
 `pBuild`  
 <span data-ttu-id="7da6d-108">dışı Yapı numarasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7da6d-108">[out] A pointer to the build number.</span></span>  
  
 `pRevision`  
 <span data-ttu-id="7da6d-109">dışı Düzeltme numarasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7da6d-109">[out] A pointer to the revision number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7da6d-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7da6d-110">Remarks</span></span>  
 <span data-ttu-id="7da6d-111">Derleme sürüm numaraları hakkında bilgi için bkz <xref:System.Version> . sınıf konusu.</span><span class="sxs-lookup"><span data-stu-id="7da6d-111">For information on assembly version numbers, see the <xref:System.Version> class topic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7da6d-112">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7da6d-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7da6d-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7da6d-113">Requirements</span></span>  
 <span data-ttu-id="7da6d-114">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7da6d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7da6d-115">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7da6d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7da6d-116">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7da6d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7da6d-117">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7da6d-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7da6d-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7da6d-118">See also</span></span>

- [<span data-ttu-id="7da6d-119">ICorDebugMergedAssemblyRecord Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7da6d-119">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="7da6d-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7da6d-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
