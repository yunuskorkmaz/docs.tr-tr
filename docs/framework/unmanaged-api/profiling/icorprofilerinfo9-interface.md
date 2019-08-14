---
title: ICorProfilerInfo9 arabirimi
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 0ba4f2b4a515143d50bc812f04ea75d821b69471
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973689"
---
# <a name="icorprofilerinfo9-interface"></a><span data-ttu-id="10bf2-102">ICorProfilerInfo9 arabirimi</span><span class="sxs-lookup"><span data-stu-id="10bf2-102">ICorProfilerInfo9 Interface</span></span>

<span data-ttu-id="10bf2-103">Birden çok yerel kod sürümüne sahip işlevlerle ilgili bilgileri sorgulamak için yöntemler sağlayan bir [ICorProfilerInfo8](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md) alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="10bf2-103">A subclass of [ICorProfilerInfo8](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md) that provides methods to query information about functions with multiple native code versions.</span></span>  

## <a name="methods"></a><span data-ttu-id="10bf2-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="10bf2-104">Methods</span></span>  

| <span data-ttu-id="10bf2-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="10bf2-105">Method</span></span>|<span data-ttu-id="10bf2-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10bf2-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="10bf2-107">Getnativecodestartaadresler yöntemi</span><span class="sxs-lookup"><span data-stu-id="10bf2-107">GetNativeCodeStartAddresses Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getnativecodestartaddresses-method.md)| <span data-ttu-id="10bf2-108">Bir FunctionID ve ReJITID verildiğinde, bu kodun Şu anda var olan tüm jıderlenen sürümlerinin yerel kod başlangıç adresini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="10bf2-108">Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.</span></span> |
|[<span data-ttu-id="10bf2-109">GetILToNativeMapping3 yöntemi</span><span class="sxs-lookup"><span data-stu-id="10bf2-109">GetILToNativeMapping3 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getiltonativemapping3-method.md)| <span data-ttu-id="10bf2-110">Yerel kod başlangıç adresi verildiğinde, kodun bu jderlenen sürümü için yerel-Il eşleme bilgilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="10bf2-110">Given the native code start address, returns the native to IL mapping information for this jitted version of the code.</span></span> |
|[<span data-ttu-id="10bf2-111">GetCodeInfo4 yöntemi</span><span class="sxs-lookup"><span data-stu-id="10bf2-111">GetCodeInfo4 Method</span></span>](icorprofilerinfo9-getcodeinfo4-method.md)| <span data-ttu-id="10bf2-112">Yerel kod başlangıç adresi verildiğinde, bu kodu depolayan sanal bellek bloklarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="10bf2-112">Given the native code start address, returns the blocks of virtual memory that store this code.</span></span> |

## <a name="requirements"></a><span data-ttu-id="10bf2-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="10bf2-113">Requirements</span></span>  
<span data-ttu-id="10bf2-114">**Platform** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="10bf2-114">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>  
<span data-ttu-id="10bf2-115">**Üst bilgi** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="10bf2-115">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="10bf2-116">**.NET sürümleri:** [!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10bf2-116">**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]</span></span>  
## <a name="see-also"></a><span data-ttu-id="10bf2-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10bf2-117">See also</span></span>
- [<span data-ttu-id="10bf2-118">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="10bf2-118">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
