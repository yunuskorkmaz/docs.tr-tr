---
description: ': Icordebugmergedassemblyrecord:: GetVersion yöntemi hakkında daha fazla bilgi edinin'
title: 'Icordebugmergedassemblyrecord:: GetVersion yöntemi'
ms.date: 03/30/2017
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
ms.openlocfilehash: 0e87e2bbb1207ebd1eb5775b7f52d5689b4e8727
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650345"
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a><span data-ttu-id="57973-103">Icordebugmergedassemblyrecord:: GetVersion yöntemi</span><span class="sxs-lookup"><span data-stu-id="57973-103">ICorDebugMergedAssemblyRecord::GetVersion Method</span></span>

<span data-ttu-id="57973-104">Derlemenin sürüm bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="57973-104">Gets the assembly's version information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57973-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="57973-105">Syntax</span></span>  
  
```cpp  
HRESULT GetVersion(  
   [out] USHORT *pMajor,
   [out] USHORT *pMinor,
   [out] USHORT *pBuild,
   [out] USHORT *pRevision  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57973-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="57973-106">Parameters</span></span>  

 `pMajor`  
 <span data-ttu-id="57973-107">dışı Ana sürüm numarasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="57973-107">[out] A pointer to the major version number.</span></span>  
  
 `pMinor`  
 <span data-ttu-id="57973-108">dışı Küçük sürüm numarasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="57973-108">[out] A pointer to the minor version number.</span></span>  
  
 `pBuild`  
 <span data-ttu-id="57973-109">dışı Yapı numarasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="57973-109">[out] A pointer to the build number.</span></span>  
  
 `pRevision`  
 <span data-ttu-id="57973-110">dışı Düzeltme numarasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="57973-110">[out] A pointer to the revision number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57973-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="57973-111">Remarks</span></span>  

 <span data-ttu-id="57973-112">Derleme sürüm numaraları hakkında bilgi için bkz <xref:System.Version> . sınıf konusu.</span><span class="sxs-lookup"><span data-stu-id="57973-112">For information on assembly version numbers, see the <xref:System.Version> class topic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="57973-113">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="57973-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57973-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="57973-114">Requirements</span></span>  

 <span data-ttu-id="57973-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57973-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57973-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="57973-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="57973-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="57973-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="57973-118">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57973-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57973-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="57973-119">See also</span></span>

- [<span data-ttu-id="57973-120">ICorDebugMergedAssemblyRecord Arabirimi</span><span class="sxs-lookup"><span data-stu-id="57973-120">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="57973-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="57973-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
