---
description: 'Hakkında daha fazla bilgi edinin: COR_PRF_EVENTPIPE_PARAM_TYPE numaralandırması'
title: COR_PRF_EVENTPIPE_PARAM_TYPE numaralandırması
ms.date: 03/19/2021
api_name:
- COR_PRF_EVENTPIPE_PARAM_TYPE
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 29aed86e4a991598d038a60ae086e77e25df24bb
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805785"
---
# <a name="cor_prf_eventpipe_param_type-enumeration"></a><span data-ttu-id="683ff-103">COR_PRF_EVENTPIPE_PARAM_TYPE numaralandırması</span><span class="sxs-lookup"><span data-stu-id="683ff-103">COR_PRF_EVENTPIPE_PARAM_TYPE Enumeration</span></span>

<span data-ttu-id="683ff-104">Bir EventPipe olayı için bir parametre türünü açıklar.</span><span class="sxs-lookup"><span data-stu-id="683ff-104">Describes the type of a parameter for an EventPipe event.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="683ff-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="683ff-105">Syntax</span></span>  
  
```cpp  
typedef enum
{
    COR_PRF_EVENTPIPE_OBJECT = 1,
    COR_PRF_EVENTPIPE_BOOLEAN = 3,
    COR_PRF_EVENTPIPE_CHAR = 4,
    COR_PRF_EVENTPIPE_SBYTE = 5,
    COR_PRF_EVENTPIPE_BYTE = 6,
    COR_PRF_EVENTPIPE_INT16 = 7,
    COR_PRF_EVENTPIPE_UINT16 = 8,
    COR_PRF_EVENTPIPE_INT32 = 9,
    COR_PRF_EVENTPIPE_UINT32 = 10,
    COR_PRF_EVENTPIPE_INT64 = 11,
    COR_PRF_EVENTPIPE_UINT64 = 12,
    COR_PRF_EVENTPIPE_SINGLE = 13,
    COR_PRF_EVENTPIPE_DOUBLE = 14,
    COR_PRF_EVENTPIPE_DECIMAL = 15,
    COR_PRF_EVENTPIPE_DATETIME = 16,
    COR_PRF_EVENTPIPE_GUID = 17,
    COR_PRF_EVENTPIPE_STRING = 18,
    COR_PRF_EVENTPIPE_ARRAY = 19,
} COR_PRF_EVENTPIPE_PARAM_TYPE;
```  
  
## <a name="members"></a><span data-ttu-id="683ff-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="683ff-106">Members</span></span>  
  
|<span data-ttu-id="683ff-107">Üye</span><span class="sxs-lookup"><span data-stu-id="683ff-107">Member</span></span>|<span data-ttu-id="683ff-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="683ff-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_EVENTPIPE_OBJECT`|<span data-ttu-id="683ff-109">Parametre türü kendini açıklayan bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="683ff-109">The parameter type is a self describing object.</span></span>|
|`COR_PRF_EVENTPIPE_BOOLEAN`|<span data-ttu-id="683ff-110">Parametre türü bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="683ff-110">The parameter type is a boolean.</span></span>|
|`COR_PRF_EVENTPIPE_CHAR`|<span data-ttu-id="683ff-111">Parametre türü, 16 bit geniş bir karakterdir.</span><span class="sxs-lookup"><span data-stu-id="683ff-111">The parameter type is a 16 bit wide character.</span></span>|
|`COR_PRF_EVENTPIPE_SBYTE`|<span data-ttu-id="683ff-112">Parametre türü işaretli 8 bit tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="683ff-112">The parameter type is a signed 8 bit integer.</span></span>|
|`COR_PRF_EVENTPIPE_BYTE`|<span data-ttu-id="683ff-113">Parametre türü işaretsiz 8 bitlik bir tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="683ff-113">The parameter type is an unsigned 8 bit integer.</span></span>|
|`COR_PRF_EVENTPIPE_INT16`|<span data-ttu-id="683ff-114">Parametre türü, işaretli bir 16 bit tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="683ff-114">The parameter type is a signed 16 bit integer.</span></span>|
|`COR_PRF_EVENTPIPE_UINT16`|<span data-ttu-id="683ff-115">Parametre türü işaretsiz 16 bit tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="683ff-115">The parameter type is an unsigned 16 bit integer.</span></span>|
|`COR_PRF_EVENTPIPE_INT32`|<span data-ttu-id="683ff-116">Parametre türü işaretli bir 32 bit tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="683ff-116">The parameter type is a signed 32 bit integer.</span></span>|
|`COR_PRF_EVENTPIPE_UINT32`|<span data-ttu-id="683ff-117">Parametre türü işaretsiz bir 32 bit tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="683ff-117">The parameter type is an unsigned 32 bit integer.</span></span>|
|`COR_PRF_EVENTPIPE_INT64`|<span data-ttu-id="683ff-118">Parametre türü işaretli bir 64 bit tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="683ff-118">The parameter type is a signed 64 bit integer.</span></span>|
|`COR_PRF_EVENTPIPE_UINT64`|<span data-ttu-id="683ff-119">Parametre türü işaretsiz bir 64 bit tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="683ff-119">The parameter type is an unsigned 64 bit integer.</span></span>|
|`COR_PRF_EVENTPIPE_SINGLE`|<span data-ttu-id="683ff-120">Parametre türü 32 bitlik bir kayan noktalı sayıdır.</span><span class="sxs-lookup"><span data-stu-id="683ff-120">The parameter type is a 32 bit floating point number.</span></span>|
|`COR_PRF_EVENTPIPE_DOUBLE`|<span data-ttu-id="683ff-121">Parametre türü 64 bitlik bir kayan noktalı sayıdır.</span><span class="sxs-lookup"><span data-stu-id="683ff-121">The parameter type is a 64 bit floating point number.</span></span>|
|`COR_PRF_EVENTPIPE_DECIMAL`|<span data-ttu-id="683ff-122">Parametre türü 128 bitlik bir kayan noktalı sayıdır.</span><span class="sxs-lookup"><span data-stu-id="683ff-122">The parameter type is a 128 bit floating point number.</span></span>|
|`COR_PRF_EVENTPIPE_DATETIME`|<span data-ttu-id="683ff-123">Parametre türü serileştirilmiş bir DataTime yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="683ff-123">The parameter type is a serialized DataTime structure.</span></span>|
|`COR_PRF_EVENTPIPE_GUID`|<span data-ttu-id="683ff-124">Parametre türü bir GUID 'dir.</span><span class="sxs-lookup"><span data-stu-id="683ff-124">The parameter type is a GUID.</span></span>|
|`COR_PRF_EVENTPIPE_STRING`|<span data-ttu-id="683ff-125">Parametre türü, 16 bit boş sonlandırılmış geniş karakter dizesidir.</span><span class="sxs-lookup"><span data-stu-id="683ff-125">The parameter type is a 16 bit null terminated wide character string.</span></span>|
|`COR_PRF_EVENTPIPE_ARRAY`|<span data-ttu-id="683ff-126">Parametre türü, yukarıdaki türlerden birinin bir dizisidir.</span><span class="sxs-lookup"><span data-stu-id="683ff-126">The parameter type is an array of one of the preceding types.</span></span>|
  
## <a name="remarks"></a><span data-ttu-id="683ff-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="683ff-127">Remarks</span></span>  

 <span data-ttu-id="683ff-128">`COR_PRF_EVENTPIPE_PARAM_TYPE`Sabit listesi, [COR_PRF_EVENTPIPE_PARAM_DESC](cor-prf-eventpipe-param-desc-structure.md) yapısı tarafından parametrenin türünü belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="683ff-128">The `COR_PRF_EVENTPIPE_PARAM_TYPE` enumeration is used by the [COR_PRF_EVENTPIPE_PARAM_DESC](cor-prf-eventpipe-param-desc-structure.md) structure to indicate the type of the parameter.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="683ff-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="683ff-129">Requirements</span></span>  

<span data-ttu-id="683ff-130">**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="683ff-130">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>
<span data-ttu-id="683ff-131">**Üst bilgi:** CorProf. IDL, CorProf. h **.NET sürümleri:**[!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span><span class="sxs-lookup"><span data-stu-id="683ff-131">**Header:** CorProf.idl, CorProf.h **.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="683ff-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="683ff-132">See also</span></span>

- [<span data-ttu-id="683ff-133">Profil Oluşturma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="683ff-133">Profiling Enumerations</span></span>](profiling-enumerations.md)
