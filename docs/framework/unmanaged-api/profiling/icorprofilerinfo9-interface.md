---
title: ICorProfilerInfo9 Arabirimi
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 74031fd822550f8a0752d02ce0c2d89b2f5ae546
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444954"
---
# <a name="icorprofilerinfo9-interface"></a><span data-ttu-id="6d36f-102">ICorProfilerInfo9 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6d36f-102">ICorProfilerInfo9 Interface</span></span>

<span data-ttu-id="6d36f-103">Birden çok yerel kod sürümüne sahip işlevlerle ilgili bilgileri sorgulamak için yöntemler sağlayan bir [ICorProfilerInfo8](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md) alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6d36f-103">A subclass of [ICorProfilerInfo8](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md) that provides methods to query information about functions with multiple native code versions.</span></span>  

## <a name="methods"></a><span data-ttu-id="6d36f-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6d36f-104">Methods</span></span>  

| <span data-ttu-id="6d36f-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6d36f-105">Method</span></span>|<span data-ttu-id="6d36f-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6d36f-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="6d36f-107">Getnativecodestartaadresler yöntemi</span><span class="sxs-lookup"><span data-stu-id="6d36f-107">GetNativeCodeStartAddresses Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getnativecodestartaddresses-method.md)| <span data-ttu-id="6d36f-108">Bir FunctionID ve ReJITID verildiğinde, bu kodun Şu anda var olan tüm jıderlenen sürümlerinin yerel kod başlangıç adresini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="6d36f-108">Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.</span></span> |
|[<span data-ttu-id="6d36f-109">GetILToNativeMapping3 yöntemi</span><span class="sxs-lookup"><span data-stu-id="6d36f-109">GetILToNativeMapping3 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getiltonativemapping3-method.md)| <span data-ttu-id="6d36f-110">Yerel kod başlangıç adresi verildiğinde, kodun bu jderlenen sürümü için yerel-Il eşleme bilgilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="6d36f-110">Given the native code start address, returns the native to IL mapping information for this jitted version of the code.</span></span> |
|[<span data-ttu-id="6d36f-111">GetCodeInfo4 yöntemi</span><span class="sxs-lookup"><span data-stu-id="6d36f-111">GetCodeInfo4 Method</span></span>](icorprofilerinfo9-getcodeinfo4-method.md)| <span data-ttu-id="6d36f-112">Yerel kod başlangıç adresi verildiğinde, bu kodu depolayan sanal bellek bloklarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="6d36f-112">Given the native code start address, returns the blocks of virtual memory that store this code.</span></span> |

## <a name="requirements"></a><span data-ttu-id="6d36f-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6d36f-113">Requirements</span></span>  
<span data-ttu-id="6d36f-114">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="6d36f-114">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>  
<span data-ttu-id="6d36f-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="6d36f-115">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="6d36f-116">**.NET sürümleri:** [!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d36f-116">**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="6d36f-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d36f-117">See also</span></span>

- [<span data-ttu-id="6d36f-118">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6d36f-118">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
