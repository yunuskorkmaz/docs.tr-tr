---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo9 Interface'
title: ICorProfilerInfo9 Arabirimi
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 954cb16d2b789359693f6a8fa3e0f6e19ad19b3e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736914"
---
# <a name="icorprofilerinfo9-interface"></a><span data-ttu-id="d065b-103">ICorProfilerInfo9 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d065b-103">ICorProfilerInfo9 Interface</span></span>

<span data-ttu-id="d065b-104">Birden çok yerel kod sürümüne sahip işlevlerle ilgili bilgileri sorgulamak için yöntemler sağlayan bir [ICorProfilerInfo8](icorprofilerinfo8-interface.md) alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d065b-104">A subclass of [ICorProfilerInfo8](icorprofilerinfo8-interface.md) that provides methods to query information about functions with multiple native code versions.</span></span>  

## <a name="methods"></a><span data-ttu-id="d065b-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d065b-105">Methods</span></span>  

| <span data-ttu-id="d065b-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d065b-106">Method</span></span>|<span data-ttu-id="d065b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d065b-107">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="d065b-108">GetNativeCodeStartAddresses Metodu</span><span class="sxs-lookup"><span data-stu-id="d065b-108">GetNativeCodeStartAddresses Method</span></span>](icorprofilerinfo9-getnativecodestartaddresses-method.md)| <span data-ttu-id="d065b-109">Bir FunctionID ve ReJITID verildiğinde, bu kodun Şu anda var olan tüm jıderlenen sürümlerinin yerel kod başlangıç adresini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="d065b-109">Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.</span></span> |
|[<span data-ttu-id="d065b-110">GetILToNativeMapping3 Metodu</span><span class="sxs-lookup"><span data-stu-id="d065b-110">GetILToNativeMapping3 Method</span></span>](icorprofilerinfo9-getiltonativemapping3-method.md)| <span data-ttu-id="d065b-111">Yerel kod başlangıç adresi verildiğinde, kodun bu jderlenen sürümü için yerel-Il eşleme bilgilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="d065b-111">Given the native code start address, returns the native to IL mapping information for this jitted version of the code.</span></span> |
|[<span data-ttu-id="d065b-112">GetCodeInfo4 Metodu</span><span class="sxs-lookup"><span data-stu-id="d065b-112">GetCodeInfo4 Method</span></span>](icorprofilerinfo9-getcodeinfo4-method.md)| <span data-ttu-id="d065b-113">Yerel kod başlangıç adresi verildiğinde, bu kodu depolayan sanal bellek bloklarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="d065b-113">Given the native code start address, returns the blocks of virtual memory that store this code.</span></span> |

## <a name="requirements"></a><span data-ttu-id="d065b-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d065b-114">Requirements</span></span>  

<span data-ttu-id="d065b-115">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="d065b-115">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
<span data-ttu-id="d065b-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d065b-116">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="d065b-117">**.NET sürümleri:**[!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d065b-117">**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="d065b-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d065b-118">See also</span></span>

- [<span data-ttu-id="d065b-119">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d065b-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
