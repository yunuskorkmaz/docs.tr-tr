---
description: ': ICorProfilerInfo11:: GetEnvironmentVariable yöntemi hakkında daha fazla bilgi edinin'
title: 'ICorProfilerInfo11:: GetEnvironmentVariable yöntemi'
ms.date: 03/19/2021
api_name:
- ICorProfilerInfo11.GetEnvironmentVariable
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 635c5fb67b880c39f15fbc194a51a706d9ef7fe4
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805837"
---
# <a name="icorprofilerinfo11getenvironmentvariable-method"></a><span data-ttu-id="b3007-103">ICorProfilerInfo11:: GetEnvironmentVariable yöntemi</span><span class="sxs-lookup"><span data-stu-id="b3007-103">ICorProfilerInfo11::GetEnvironmentVariable Method</span></span>

<span data-ttu-id="b3007-104">İşlemden bir ortam değişkeni alır.</span><span class="sxs-lookup"><span data-stu-id="b3007-104">Gets an environment variable from the process.</span></span> <span data-ttu-id="b3007-105">Windows dışı platformlarda çalışma zamanı, iş parçacığı güvenliğini sağlamak için ortam değişkenlerinin iç önbelleğini tutar.</span><span class="sxs-lookup"><span data-stu-id="b3007-105">On non-Windows platforms the runtime keeps an internal cache of environment variables to ensure thread safety.</span></span> <span data-ttu-id="b3007-106">Bu, çağırmanın `getenv` , başlangıçtan sonra işlemde çalışan yönetilen kodla ayarlanan yeni veya güncelleştirilmiş ortam değişkenlerini okumayacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b3007-106">This means that calling `getenv` will not read any new or updated environment variables set by managed code running in the process after startup.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="b3007-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b3007-107">Syntax</span></span>  
  
```cpp  
    HRESULT GetEnvironmentVariable(
                [in, string] const WCHAR *szName,
                [in]         ULONG cchValue,
                [out]        ULONG *pcchValue,
                [out, annotation("_Out_writes_to_(cchValue, *pcchValue)")]
                             WCHAR szValue[]);
```  
  
## <a name="parameters"></a><span data-ttu-id="b3007-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b3007-108">Parameters</span></span>

<span data-ttu-id="b3007-109">`szName` 'ndaki Alınacak ortam değişkeninin adını içeren, null sonlandırılmış geniş bir karakter dizesinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="b3007-109">`szName` [in] A pointer to a null terminated wide character string containing the name of the environment variable to get.</span></span>

<span data-ttu-id="b3007-110">`cchValue` 'ndaki Karakter cinsinden uzunluğu `szValue` .</span><span class="sxs-lookup"><span data-stu-id="b3007-110">`cchValue` [in] The length, in characters, of `szValue`.</span></span>

<span data-ttu-id="b3007-111">`pcchValue` dışı Toplam karakter uzunluğuna yönelik bir işaretçi `szValue` .</span><span class="sxs-lookup"><span data-stu-id="b3007-111">`pcchValue` [out] A pointer to the total character length of `szValue`.</span></span>

<span data-ttu-id="b3007-112">`szValue` dışı Çağıran, geniş karakter arabelleği sağladı.</span><span class="sxs-lookup"><span data-stu-id="b3007-112">`szValue` [out] A caller provided wide character buffer.</span></span> <span data-ttu-id="b3007-113">İşlev, arabelleği döndürdüğünde, ortam değişkeninin değerini içerir.</span><span class="sxs-lookup"><span data-stu-id="b3007-113">When the function returns the buffer will contain the value of the environment variable.</span></span>

## <a name="requirements"></a><span data-ttu-id="b3007-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b3007-114">Requirements</span></span>  

<span data-ttu-id="b3007-115">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="b3007-115">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
<span data-ttu-id="b3007-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b3007-116">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="b3007-117">**.NET sürümleri:**[!INCLUDE[net_core](../../../../includes/net-core-31-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3007-117">**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-31-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3007-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3007-118">See also</span></span>

- [<span data-ttu-id="b3007-119">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b3007-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="b3007-120">ICorProfilerInfo11 arabirimi</span><span class="sxs-lookup"><span data-stu-id="b3007-120">ICorProfilerInfo11 Interface</span></span>](icorprofilerinfo11-interface.md)
