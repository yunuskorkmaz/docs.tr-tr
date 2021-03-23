---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo9 Interface'
title: ICorProfilerInfo9 Arabirimi
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 44e3d694b426f87ee4e4bc12181f46322b0d246f
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805681"
---
# <a name="icorprofilerinfo9-interface"></a><span data-ttu-id="76cbb-103">ICorProfilerInfo9 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="76cbb-103">ICorProfilerInfo9 Interface</span></span>

<span data-ttu-id="76cbb-104">Birden çok yerel kod sürümüne sahip işlevlerle ilgili bilgileri sorgulamak için yöntemler sağlayan bir [ICorProfilerInfo8](icorprofilerinfo8-interface.md) alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="76cbb-104">A subclass of [ICorProfilerInfo8](icorprofilerinfo8-interface.md) that provides methods to query information about functions with multiple native code versions.</span></span>  

## <a name="methods"></a><span data-ttu-id="76cbb-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="76cbb-105">Methods</span></span>  

| <span data-ttu-id="76cbb-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="76cbb-106">Method</span></span>|<span data-ttu-id="76cbb-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="76cbb-107">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="76cbb-108">GetNativeCodeStartAddresses Metodu</span><span class="sxs-lookup"><span data-stu-id="76cbb-108">GetNativeCodeStartAddresses Method</span></span>](icorprofilerinfo9-getnativecodestartaddresses-method.md)| <span data-ttu-id="76cbb-109">Bir FunctionID ve ReJITID verildiğinde, bu kodun Şu anda var olan tüm jıderlenen sürümlerinin yerel kod başlangıç adresini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="76cbb-109">Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.</span></span> |
|[<span data-ttu-id="76cbb-110">GetILToNativeMapping3 Metodu</span><span class="sxs-lookup"><span data-stu-id="76cbb-110">GetILToNativeMapping3 Method</span></span>](icorprofilerinfo9-getiltonativemapping3-method.md)| <span data-ttu-id="76cbb-111">Yerel kod başlangıç adresi verildiğinde, kodun bu jderlenen sürümü için yerel-Il eşleme bilgilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="76cbb-111">Given the native code start address, returns the native to IL mapping information for this jitted version of the code.</span></span> |
|[<span data-ttu-id="76cbb-112">GetCodeInfo4 Metodu</span><span class="sxs-lookup"><span data-stu-id="76cbb-112">GetCodeInfo4 Method</span></span>](icorprofilerinfo9-getcodeinfo4-method.md)| <span data-ttu-id="76cbb-113">Yerel kod başlangıç adresi verildiğinde, bu kodu depolayan sanal bellek bloklarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="76cbb-113">Given the native code start address, returns the blocks of virtual memory that store this code.</span></span> |

## <a name="requirements"></a><span data-ttu-id="76cbb-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="76cbb-114">Requirements</span></span>  

<span data-ttu-id="76cbb-115">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="76cbb-115">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
<span data-ttu-id="76cbb-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="76cbb-116">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="76cbb-117">**.NET sürümleri:**[!INCLUDE[net_core](../../../../includes/net-core-21-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76cbb-117">**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-21-md.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="76cbb-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="76cbb-118">See also</span></span>

- [<span data-ttu-id="76cbb-119">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="76cbb-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
