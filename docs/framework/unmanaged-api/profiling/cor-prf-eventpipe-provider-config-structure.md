---
description: 'Hakkında daha fazla bilgi edinin: COR_PRF_EVENTPIPE_PROVIDER_CONFIG numaralandırması'
title: COR_PRF_EVENTPIPE_PROVIDER_CONFIG numaralandırması
ms.date: 03/19/2021
api_name:
- COR_PRF_EVENTPIPE_PROVIDER_CONFIG
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 2a7a5e720e9468b44e6504d24a3b9ad836e13693
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805850"
---
# <a name="cor_prf_eventpipe_provider_config-enumeration"></a><span data-ttu-id="d848e-103">COR_PRF_EVENTPIPE_PROVIDER_CONFIG numaralandırması</span><span class="sxs-lookup"><span data-stu-id="d848e-103">COR_PRF_EVENTPIPE_PROVIDER_CONFIG Enumeration</span></span>

<span data-ttu-id="d848e-104">Bir EventPipe sağlayıcısını yapılandırmak için gereken alanları açıklar.</span><span class="sxs-lookup"><span data-stu-id="d848e-104">Describes the fields necessary to configure an EventPipe provider.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="d848e-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d848e-105">Syntax</span></span>  
  
```cpp  
typedef struct
{
    const WCHAR* providerName;
    UINT64       keywords;
    UINT32       loggingLevel;
    const WCHAR* filterData;
} COR_PRF_EVENTPIPE_PROVIDER_CONFIG;
```  
  
## <a name="members"></a><span data-ttu-id="d848e-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="d848e-106">Members</span></span>  
  
|<span data-ttu-id="d848e-107">Üye</span><span class="sxs-lookup"><span data-stu-id="d848e-107">Member</span></span>|<span data-ttu-id="d848e-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d848e-108">Description</span></span>|  
|------------|-----------------|  
|`providerName`|<span data-ttu-id="d848e-109">Etkinleştirilecek sağlayıcının adı.</span><span class="sxs-lookup"><span data-stu-id="d848e-109">The name of the provider to enable.</span></span>|  
|`keywords`|<span data-ttu-id="d848e-110">Sağlayıcıda etkinleştirilecek anahtar sözcükler.</span><span class="sxs-lookup"><span data-stu-id="d848e-110">The keywords to enable on the provider.</span></span>|  
|`loggingLevel`|<span data-ttu-id="d848e-111">Sağlayıcıda etkinleştirilecek düzey.</span><span class="sxs-lookup"><span data-stu-id="d848e-111">The level to enable on the provider.</span></span>|  
|`filterData`|<span data-ttu-id="d848e-112">Sağlayıcıyı etkinleştirirken kullanılacak filtreverileri içeren geniş bir karakter dizesi.</span><span class="sxs-lookup"><span data-stu-id="d848e-112">A wide character string containing the filterdata to use when enabling the provider.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d848e-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d848e-113">Remarks</span></span>  

 <span data-ttu-id="d848e-114">`COR_PRF_EVENTPIPE_PROVIDER_CONFIG`Yapı, oturuma eklenmekte olan sağlayıcının yapılandırmasını göstermek Için [ICorProfilerInfo12:: EventPipeAddProviderToSession](icorprofilerinfo12-eventpipeaddprovidertosession-method.md) yöntemi tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d848e-114">The `COR_PRF_EVENTPIPE_PROVIDER_CONFIG` structure is used by the [ICorProfilerInfo12::EventPipeAddProviderToSession](icorprofilerinfo12-eventpipeaddprovidertosession-method.md) method to indicate the configuration for the provider being added to the session.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="d848e-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d848e-115">Requirements</span></span>  

<span data-ttu-id="d848e-116">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="d848e-116">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>
<span data-ttu-id="d848e-117">**Üst bilgi:** CorProf. IDL, CorProf. h **.NET sürümleri:**[!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d848e-117">**Header:** CorProf.idl, CorProf.h **.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d848e-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d848e-118">See also</span></span>

- [<span data-ttu-id="d848e-119">Profil Oluşturma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="d848e-119">Profiling Enumerations</span></span>](profiling-enumerations.md)
- [<span data-ttu-id="d848e-120">ICorProfilerInfo12:: EventPipeAddProviderToSession</span><span class="sxs-lookup"><span data-stu-id="d848e-120">ICorProfilerInfo12::EventPipeAddProviderToSession</span></span>](icorprofilerinfo12-eventpipeaddprovidertosession-method.md)
