---
title: COR_PRF_FUNCTION_ARGUMENT_INFO Yapısı
ms.date: 03/30/2017
api_name:
- COR_PRF_FUNCTION_ARGUMENT_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FUNCTION_ARGUMENT_INFO
helpviewer_keywords:
- COR_PRF_FUNCTION_ARGUMENT_INFO structure [.NET Framework profiling]
ms.assetid: 07cf3bab-e193-4991-8205-3f41cf2d67b3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 293ad30ebf47ca8684d158b1ae1772ab245d7981
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59163123"
---
# <a name="corprffunctionargumentinfo-structure"></a><span data-ttu-id="54445-102">COR_PRF_FUNCTION_ARGUMENT_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="54445-102">COR_PRF_FUNCTION_ARGUMENT_INFO Structure</span></span>
<span data-ttu-id="54445-103">Soldan sağa doğru sırayla bir işlevin bağımsız değişkenlerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="54445-103">Represents a function's arguments, in left-to-right order.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54445-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="54445-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_INFO {  
    ULONG numRanges;  
    ULONG totalArgumentSize;  
    COR_PRF_FUNCTION_ARGUMENT_RANGE ranges[1];  
} COR_PRF_FUNCTION_ARGUMENT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="54445-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="54445-105">Members</span></span>  
  
|<span data-ttu-id="54445-106">Üye</span><span class="sxs-lookup"><span data-stu-id="54445-106">Member</span></span>|<span data-ttu-id="54445-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="54445-107">Description</span></span>|  
|------------|-----------------|  
|`numRanges`|<span data-ttu-id="54445-108">Bağımsız değişkenlerin blokların sayısı.</span><span class="sxs-lookup"><span data-stu-id="54445-108">The number of blocks of arguments.</span></span> <span data-ttu-id="54445-109">Diğer bir deyişle, bu değer sayısıdır [cor_prf_functıon_argument_range](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) içindeki yapıları `ranges` dizisi.</span><span class="sxs-lookup"><span data-stu-id="54445-109">That is, this value is the number of [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structures in the `ranges` array.</span></span>|  
|`totalArgumentSize`|<span data-ttu-id="54445-110">Tüm bağımsız değişkenler toplam boyutu.</span><span class="sxs-lookup"><span data-stu-id="54445-110">The total size of all arguments.</span></span> <span data-ttu-id="54445-111">Diğer bir deyişle, bu bağımsız değişken uzunluklarının toplamını değerdir.</span><span class="sxs-lookup"><span data-stu-id="54445-111">In other words, this value is the sum of the argument lengths.</span></span>|  
|`ranges`|<span data-ttu-id="54445-112">Bir dizi `COR_PRF_FUNCTION_ARGUMENT_RANGE` yapıları, her biri bir işlev bağımsız değişkenleri bloğunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="54445-112">An array of `COR_PRF_FUNCTION_ARGUMENT_RANGE` structures, each of which represents one block of function arguments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54445-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="54445-113">Remarks</span></span>  
 <span data-ttu-id="54445-114">Bir işlev, fazla sayıda bağımsız değişken olabilir.</span><span class="sxs-lookup"><span data-stu-id="54445-114">A function may have many arguments.</span></span> <span data-ttu-id="54445-115">Bu bağımsız değişkenlerden bitişik bellekte depolanması.</span><span class="sxs-lookup"><span data-stu-id="54445-115">Those arguments might not be stored contiguously in memory.</span></span> <span data-ttu-id="54445-116">Tek bir yerde üç bağımsız değişken bir blok, iki bağımsız değişkeni başka bir yerde bloğunu ve farklı bir yerde bir bağımsız değişkenin bir son blok olabilir.</span><span class="sxs-lookup"><span data-stu-id="54445-116">You might have a block of three arguments in one place, a block of two arguments in another place, and a final block of one argument in a different place.</span></span> <span data-ttu-id="54445-117">Bu bağımsız değişkenler tüm; aynı işlevi farklı yerlerde yalnızca depolandıkları.</span><span class="sxs-lookup"><span data-stu-id="54445-117">These arguments are all for the same function; they're just stored in different places.</span></span>  
  
 <span data-ttu-id="54445-118">`COR_PRF_FUNCTION_ARGUMENT_INFO` Yapısı tek bir işlevin tüm bağımsız değişkenleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="54445-118">The `COR_PRF_FUNCTION_ARGUMENT_INFO` structure represents all the arguments of a single function.</span></span> <span data-ttu-id="54445-119">Bir dizi işlev bağımsız değişkenlerinin tüm blokları başvurmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="54445-119">It uses an array to reference all the blocks of function arguments.</span></span> <span data-ttu-id="54445-120">Bu nedenle, tek bir sahip tek bir işlev için `COR_PRF_FUNCTION_ARGUMENT_INFO` birden çok başvuran yapısı `COR_PRF_FUNCTION_ARGUMENT_RANGE` yapıları, her biri bir veya daha fazla işlev bağımsız değişkenleri için işaret eder.</span><span class="sxs-lookup"><span data-stu-id="54445-120">So, for a single function, you have a single `COR_PRF_FUNCTION_ARGUMENT_INFO` structure, which references multiple `COR_PRF_FUNCTION_ARGUMENT_RANGE` structures, each of which points to one or more function arguments.</span></span>  
  
 <span data-ttu-id="54445-121">Kayıtlara depolanan bağımsız değişkenler, yapıları yapı belleğe geçmiş.</span><span class="sxs-lookup"><span data-stu-id="54445-121">Arguments that are stored in registers are spilled into memory to build the structures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54445-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="54445-122">Requirements</span></span>  
 <span data-ttu-id="54445-123">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54445-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54445-124">**Üst bilgi:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="54445-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="54445-125">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="54445-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="54445-126">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54445-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54445-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54445-127">See also</span></span>

- [<span data-ttu-id="54445-128">Profil Oluşturma Yapıları</span><span class="sxs-lookup"><span data-stu-id="54445-128">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
