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
ms.openlocfilehash: b1d31012662964132f8b65f030a062ae39ded56e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130365"
---
# <a name="icorprofilerinfo6-interface"></a><span data-ttu-id="258ed-102">ICorProfilerInfo6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="258ed-102">ICorProfilerInfo6 Interface</span></span>
<span data-ttu-id="258ed-103">[.NET Framework 4,6 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="258ed-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="258ed-104">Belirli bir NGen modülünde tanımlanan ve belirli bir yöntemi satır içi olarak tanımlanmış tüm yöntemler için bir Numaralandırıcı sağlayan [ICorProfilerInfo5](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md) öğesinin bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="258ed-104">A subclass of [ICorProfilerInfo5](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md) that provides an enumerator for all methods that are defined in a given NGen module and inline a given method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="258ed-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="258ed-105">Methods</span></span>  
  
|<span data-ttu-id="258ed-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="258ed-106">Method</span></span>|<span data-ttu-id="258ed-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="258ed-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="258ed-108">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="258ed-108">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-enumngenmodulemethodsinliningthismethod-method.md)|<span data-ttu-id="258ed-109">Belirli bir NGen modülüne ait olan ve belirli bir yöntemin gövdesinde satır içine alınmış tüm yöntemler için bir Numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="258ed-109">Returns an enumerator for all methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="258ed-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="258ed-110">Requirements</span></span>  
 <span data-ttu-id="258ed-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="258ed-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="258ed-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="258ed-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="258ed-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="258ed-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="258ed-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="258ed-114">See also</span></span>

- [<span data-ttu-id="258ed-115">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="258ed-115">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
