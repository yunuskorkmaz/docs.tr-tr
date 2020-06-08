---
title: ICorProfilerInfo6 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo6
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 6f2bb148-1e2b-4e45-a5a5-0ceddc40064b
ms.openlocfilehash: fba57a88cd3af582b4edf0e5bdbf6ac48020c9f7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495521"
---
# <a name="icorprofilerinfo6-interface"></a><span data-ttu-id="a5048-102">ICorProfilerInfo6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a5048-102">ICorProfilerInfo6 Interface</span></span>
<span data-ttu-id="a5048-103">[.NET Framework 4,6 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="a5048-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="a5048-104">Belirli bir NGen modülünde tanımlanan ve belirli bir yöntemi satır içi olarak tanımlanmış tüm yöntemler için bir Numaralandırıcı sağlayan [ICorProfilerInfo5](icorprofilerinfo5-interface.md) öğesinin bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a5048-104">A subclass of [ICorProfilerInfo5](icorprofilerinfo5-interface.md) that provides an enumerator for all methods that are defined in a given NGen module and inline a given method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a5048-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a5048-105">Methods</span></span>  
  
|<span data-ttu-id="a5048-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a5048-106">Method</span></span>|<span data-ttu-id="a5048-107">Description</span><span class="sxs-lookup"><span data-stu-id="a5048-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a5048-108">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a5048-108">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>](icorprofilerinfo6-enumngenmodulemethodsinliningthismethod-method.md)|<span data-ttu-id="a5048-109">Belirli bir NGen modülüne ait olan ve belirli bir yöntemin gövdesinde satır içine alınmış tüm yöntemler için bir Numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="a5048-109">Returns an enumerator for all methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a5048-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a5048-110">Requirements</span></span>  
 <span data-ttu-id="a5048-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5048-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5048-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a5048-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a5048-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5048-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5048-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a5048-114">See also</span></span>

- [<span data-ttu-id="a5048-115">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a5048-115">Profiling Interfaces</span></span>](profiling-interfaces.md)
