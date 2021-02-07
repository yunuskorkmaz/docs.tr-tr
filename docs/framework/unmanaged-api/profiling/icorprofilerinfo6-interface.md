---
description: 'Daha fazla bilgi edinin: ıcorprofilerınfo6 Interface'
title: ICorProfilerInfo6 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo6
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 6f2bb148-1e2b-4e45-a5a5-0ceddc40064b
ms.openlocfilehash: c093930b102ca99a8524e6d5d6129690f80a5353
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737161"
---
# <a name="icorprofilerinfo6-interface"></a><span data-ttu-id="bbc72-103">ICorProfilerInfo6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bbc72-103">ICorProfilerInfo6 Interface</span></span>

<span data-ttu-id="bbc72-104">[.NET Framework 4,6 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="bbc72-104">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="bbc72-105">Belirli bir NGen modülünde tanımlanan ve belirli bir yöntemi satır içi olarak tanımlanmış tüm yöntemler için bir Numaralandırıcı sağlayan [ICorProfilerInfo5](icorprofilerinfo5-interface.md) öğesinin bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="bbc72-105">A subclass of [ICorProfilerInfo5](icorprofilerinfo5-interface.md) that provides an enumerator for all methods that are defined in a given NGen module and inline a given method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bbc72-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="bbc72-106">Methods</span></span>  
  
|<span data-ttu-id="bbc72-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="bbc72-107">Method</span></span>|<span data-ttu-id="bbc72-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bbc72-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bbc72-109">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bbc72-109">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>](icorprofilerinfo6-enumngenmodulemethodsinliningthismethod-method.md)|<span data-ttu-id="bbc72-110">Belirli bir NGen modülüne ait olan ve belirli bir yöntemin gövdesinde satır içine alınmış tüm yöntemler için bir Numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="bbc72-110">Returns an enumerator for all methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bbc72-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bbc72-111">Requirements</span></span>  

 <span data-ttu-id="bbc72-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bbc72-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbc72-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="bbc72-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bbc72-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbc72-114">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbc72-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bbc72-115">See also</span></span>

- [<span data-ttu-id="bbc72-116">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="bbc72-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
