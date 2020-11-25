---
title: 'Icordebugmergedassemblyrecord:: GetVersion yöntemi'
ms.date: 03/30/2017
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
ms.openlocfilehash: 7352a77fc8f41124d7e6c78a3dfc6ccd6d3a94aa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710512"
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a><span data-ttu-id="433d7-102">Icordebugmergedassemblyrecord:: GetVersion yöntemi</span><span class="sxs-lookup"><span data-stu-id="433d7-102">ICorDebugMergedAssemblyRecord::GetVersion Method</span></span>

<span data-ttu-id="433d7-103">Derlemenin sürüm bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="433d7-103">Gets the assembly's version information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="433d7-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="433d7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersion(  
   [out] USHORT *pMajor,
   [out] USHORT *pMinor,
   [out] USHORT *pBuild,
   [out] USHORT *pRevision  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="433d7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="433d7-105">Parameters</span></span>  

 `pMajor`  
 <span data-ttu-id="433d7-106">dışı Ana sürüm numarasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="433d7-106">[out] A pointer to the major version number.</span></span>  
  
 `pMinor`  
 <span data-ttu-id="433d7-107">dışı Küçük sürüm numarasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="433d7-107">[out] A pointer to the minor version number.</span></span>  
  
 `pBuild`  
 <span data-ttu-id="433d7-108">dışı Yapı numarasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="433d7-108">[out] A pointer to the build number.</span></span>  
  
 `pRevision`  
 <span data-ttu-id="433d7-109">dışı Düzeltme numarasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="433d7-109">[out] A pointer to the revision number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="433d7-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="433d7-110">Remarks</span></span>  

 <span data-ttu-id="433d7-111">Derleme sürüm numaraları hakkında bilgi için bkz <xref:System.Version> . sınıf konusu.</span><span class="sxs-lookup"><span data-stu-id="433d7-111">For information on assembly version numbers, see the <xref:System.Version> class topic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="433d7-112">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="433d7-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="433d7-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="433d7-113">Requirements</span></span>  

 <span data-ttu-id="433d7-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="433d7-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="433d7-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="433d7-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="433d7-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="433d7-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="433d7-117">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="433d7-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="433d7-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="433d7-118">See also</span></span>

- [<span data-ttu-id="433d7-119">ICorDebugMergedAssemblyRecord Arabirimi</span><span class="sxs-lookup"><span data-stu-id="433d7-119">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="433d7-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="433d7-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
