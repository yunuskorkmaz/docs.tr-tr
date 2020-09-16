---
title: ICorProfilerInfo9 Arabirimi
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: f38195b1a7983e23c7f5c20055ea8c2a8bfcb7d8
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556856"
---
# <a name="icorprofilerinfo9-interface"></a><span data-ttu-id="89d62-102">ICorProfilerInfo9 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="89d62-102">ICorProfilerInfo9 Interface</span></span>

<span data-ttu-id="89d62-103">Birden çok yerel kod sürümüne sahip işlevlerle ilgili bilgileri sorgulamak için yöntemler sağlayan bir [ICorProfilerInfo8](icorprofilerinfo8-interface.md) alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="89d62-103">A subclass of [ICorProfilerInfo8](icorprofilerinfo8-interface.md) that provides methods to query information about functions with multiple native code versions.</span></span>  

## <a name="methods"></a><span data-ttu-id="89d62-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="89d62-104">Methods</span></span>  

| <span data-ttu-id="89d62-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="89d62-105">Method</span></span>|<span data-ttu-id="89d62-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89d62-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="89d62-107">GetNativeCodeStartAddresses Metodu</span><span class="sxs-lookup"><span data-stu-id="89d62-107">GetNativeCodeStartAddresses Method</span></span>](icorprofilerinfo9-getnativecodestartaddresses-method.md)| <span data-ttu-id="89d62-108">Bir FunctionID ve ReJITID verildiğinde, bu kodun Şu anda var olan tüm jıderlenen sürümlerinin yerel kod başlangıç adresini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="89d62-108">Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.</span></span> |
|[<span data-ttu-id="89d62-109">GetILToNativeMapping3 Metodu</span><span class="sxs-lookup"><span data-stu-id="89d62-109">GetILToNativeMapping3 Method</span></span>](icorprofilerinfo9-getiltonativemapping3-method.md)| <span data-ttu-id="89d62-110">Yerel kod başlangıç adresi verildiğinde, kodun bu jderlenen sürümü için yerel-Il eşleme bilgilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="89d62-110">Given the native code start address, returns the native to IL mapping information for this jitted version of the code.</span></span> |
|[<span data-ttu-id="89d62-111">GetCodeInfo4 Metodu</span><span class="sxs-lookup"><span data-stu-id="89d62-111">GetCodeInfo4 Method</span></span>](icorprofilerinfo9-getcodeinfo4-method.md)| <span data-ttu-id="89d62-112">Yerel kod başlangıç adresi verildiğinde, bu kodu depolayan sanal bellek bloklarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="89d62-112">Given the native code start address, returns the blocks of virtual memory that store this code.</span></span> |

## <a name="requirements"></a><span data-ttu-id="89d62-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="89d62-113">Requirements</span></span>  
<span data-ttu-id="89d62-114">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="89d62-114">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
<span data-ttu-id="89d62-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="89d62-115">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="89d62-116">**.NET sürümleri:**[!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89d62-116">**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="89d62-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89d62-117">See also</span></span>

- [<span data-ttu-id="89d62-118">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="89d62-118">Profiling Interfaces</span></span>](profiling-interfaces.md)
