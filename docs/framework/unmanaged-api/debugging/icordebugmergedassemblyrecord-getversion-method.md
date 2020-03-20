---
title: ICorDebugMergedAssemblyRecord::GetVersion Yöntemi
ms.date: 03/30/2017
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
ms.openlocfilehash: 5dc9995e88086da854d2e9382cef81b229ff9dc9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178678"
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a><span data-ttu-id="8be79-102">ICorDebugMergedAssemblyRecord::GetVersion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8be79-102">ICorDebugMergedAssemblyRecord::GetVersion Method</span></span>
<span data-ttu-id="8be79-103">Derlemenin sürüm bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="8be79-103">Gets the assembly's version information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8be79-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8be79-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersion(  
   [out] USHORT *pMajor,
   [out] USHORT *pMinor,
   [out] USHORT *pBuild,
   [out] USHORT *pRevision  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8be79-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8be79-105">Parameters</span></span>  
 `pMajor`  
 <span data-ttu-id="8be79-106">[çıkış] Ana sürüm numarasıiçin bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8be79-106">[out] A pointer to the major version number.</span></span>  
  
 `pMinor`  
 <span data-ttu-id="8be79-107">[çıkış] Küçük sürüm numarasıiçin bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8be79-107">[out] A pointer to the minor version number.</span></span>  
  
 `pBuild`  
 <span data-ttu-id="8be79-108">[çıkış] Yapı numarasıiçin bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8be79-108">[out] A pointer to the build number.</span></span>  
  
 `pRevision`  
 <span data-ttu-id="8be79-109">[çıkış] Düzeltme numarasıiçin bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8be79-109">[out] A pointer to the revision number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8be79-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8be79-110">Remarks</span></span>  
 <span data-ttu-id="8be79-111">Derleme sürüm numaraları hakkında bilgi <xref:System.Version> için sınıf konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="8be79-111">For information on assembly version numbers, see the <xref:System.Version> class topic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8be79-112">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8be79-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8be79-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8be79-113">Requirements</span></span>  
 <span data-ttu-id="8be79-114">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8be79-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8be79-115">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8be79-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8be79-116">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8be79-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8be79-117">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8be79-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8be79-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8be79-118">See also</span></span>

- [<span data-ttu-id="8be79-119">ICorDebugMergedAssemblyRecord Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8be79-119">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="8be79-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8be79-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
