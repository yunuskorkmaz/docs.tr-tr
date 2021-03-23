---
description: ': ICorProfilerInfo11:: SetEnvironmentVariable yöntemi hakkında daha fazla bilgi edinin'
title: 'ICorProfilerInfo11:: SetEnvironmentVariable yöntemi'
ms.date: 03/19/2021
api_name:
- ICorProfilerInfo11.SetEnvironmentVariable
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 77dc3fc992dec037881573323822dc11481a56be
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805616"
---
# <a name="icorprofilerinfo11setenvironmentvariable-method"></a><span data-ttu-id="a8257-103">ICorProfilerInfo11:: SetEnvironmentVariable yöntemi</span><span class="sxs-lookup"><span data-stu-id="a8257-103">ICorProfilerInfo11::SetEnvironmentVariable Method</span></span>

<span data-ttu-id="a8257-104">İşlemdeki bir ortam değişkenini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a8257-104">Sets an environment variable in the process.</span></span> <span data-ttu-id="a8257-105">Windows dışı platformlarda çalışma zamanı, iş parçacığı güvenliğini sağlamak için ortam değişkenlerinin iç önbelleğini tutar.</span><span class="sxs-lookup"><span data-stu-id="a8257-105">On non-Windows platforms the runtime keeps an internal cache of environment variables to ensure thread safety.</span></span> <span data-ttu-id="a8257-106">Bu, profil oluşturucu `setenv` Yeni ortam değişkenini çağırdığında, işlemde çalışan yönetilen kod tarafından çekilmeyeceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a8257-106">This means that if the profiler calls `setenv` the new environment variable will not be picked up by managed code running in the process.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="a8257-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a8257-107">Syntax</span></span>  
  
```cpp  
    HRESULT SetEnvironmentVariable(
                [in, string] const WCHAR *szName,
                [in, string] const WCHAR *szValue);
```  
  
## <a name="parameters"></a><span data-ttu-id="a8257-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a8257-108">Parameters</span></span>

<span data-ttu-id="a8257-109">`szName` 'ndaki Ayarlanacak ortam değişkeninin adını içeren, null sonlandırılmış geniş bir karakter dizesinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="a8257-109">`szName` [in] A pointer to a null terminated wide character string containing the name of the environment variable to set.</span></span>

<span data-ttu-id="a8257-110">`szValue` 'ndaki Ayarlanacak ortam değişkeninin değerini içeren, null sonlandırılmış geniş bir karakter dizesinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="a8257-110">`szValue` [in] A pointer to a null terminated wide character string containing the value of the environment variable to set.</span></span>

## <a name="requirements"></a><span data-ttu-id="a8257-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a8257-111">Requirements</span></span>  

<span data-ttu-id="a8257-112">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="a8257-112">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
<span data-ttu-id="a8257-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a8257-113">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="a8257-114">**.NET sürümleri:**[!INCLUDE[net_core](../../../../includes/net-core-31-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8257-114">**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-31-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8257-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a8257-115">See also</span></span>

- [<span data-ttu-id="a8257-116">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a8257-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="a8257-117">ICorProfilerInfo11 arabirimi</span><span class="sxs-lookup"><span data-stu-id="a8257-117">ICorProfilerInfo11 Interface</span></span>](icorprofilerinfo11-interface.md)
