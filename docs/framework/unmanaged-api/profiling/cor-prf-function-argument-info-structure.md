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
ms.openlocfilehash: c92ee580caed9f1fb87a31b676747769ad31a0e2
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867262"
---
# <a name="cor_prf_function_argument_info-structure"></a><span data-ttu-id="eb7cd-102">COR_PRF_FUNCTION_ARGUMENT_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="eb7cd-102">COR_PRF_FUNCTION_ARGUMENT_INFO Structure</span></span>
<span data-ttu-id="eb7cd-103">İşlevin bağımsız değişkenlerini soldan sağa sırada temsil eder.</span><span class="sxs-lookup"><span data-stu-id="eb7cd-103">Represents a function's arguments, in left-to-right order.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb7cd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eb7cd-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_INFO {  
    ULONG numRanges;  
    ULONG totalArgumentSize;  
    COR_PRF_FUNCTION_ARGUMENT_RANGE ranges[1];  
} COR_PRF_FUNCTION_ARGUMENT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="eb7cd-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="eb7cd-105">Members</span></span>  
  
|<span data-ttu-id="eb7cd-106">Üye</span><span class="sxs-lookup"><span data-stu-id="eb7cd-106">Member</span></span>|<span data-ttu-id="eb7cd-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eb7cd-107">Description</span></span>|  
|------------|-----------------|  
|`numRanges`|<span data-ttu-id="eb7cd-108">Bağımsız değişken blok sayısı.</span><span class="sxs-lookup"><span data-stu-id="eb7cd-108">The number of blocks of arguments.</span></span> <span data-ttu-id="eb7cd-109">Diğer bir deyişle, bu değer `ranges` dizisindeki [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) yapılarının sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="eb7cd-109">That is, this value is the number of [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) structures in the `ranges` array.</span></span>|  
|`totalArgumentSize`|<span data-ttu-id="eb7cd-110">Tüm bağımsız değişkenlerin toplam boyutu.</span><span class="sxs-lookup"><span data-stu-id="eb7cd-110">The total size of all arguments.</span></span> <span data-ttu-id="eb7cd-111">Diğer bir deyişle, bu değer bağımsız değişken uzunluklarının toplamıdır.</span><span class="sxs-lookup"><span data-stu-id="eb7cd-111">In other words, this value is the sum of the argument lengths.</span></span>|  
|`ranges`|<span data-ttu-id="eb7cd-112">Her biri bir işlev bağımsız değişkenlerinin bloğunu temsil eden `COR_PRF_FUNCTION_ARGUMENT_RANGE` yapılarının bir dizisi.</span><span class="sxs-lookup"><span data-stu-id="eb7cd-112">An array of `COR_PRF_FUNCTION_ARGUMENT_RANGE` structures, each of which represents one block of function arguments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb7cd-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eb7cd-113">Remarks</span></span>  
 <span data-ttu-id="eb7cd-114">Bir işlevde birçok bağımsız değişken olabilir.</span><span class="sxs-lookup"><span data-stu-id="eb7cd-114">A function may have many arguments.</span></span> <span data-ttu-id="eb7cd-115">Bu bağımsız değişkenler bellekte bitişik olarak depolanmayabilir.</span><span class="sxs-lookup"><span data-stu-id="eb7cd-115">Those arguments might not be stored contiguously in memory.</span></span> <span data-ttu-id="eb7cd-116">Tek bir yerde üç bağımsız değişkeni, başka bir yerde iki bağımsız değişken bloğunu ve bir bağımsız değişkenin son bloğunu farklı bir yerde engellemeniz olabilir.</span><span class="sxs-lookup"><span data-stu-id="eb7cd-116">You might have a block of three arguments in one place, a block of two arguments in another place, and a final block of one argument in a different place.</span></span> <span data-ttu-id="eb7cd-117">Bu bağımsız değişkenlerin hepsi aynı işleve yöneliktir; yalnızca farklı yerlerde depolanırlar.</span><span class="sxs-lookup"><span data-stu-id="eb7cd-117">These arguments are all for the same function; they're just stored in different places.</span></span>  
  
 <span data-ttu-id="eb7cd-118">`COR_PRF_FUNCTION_ARGUMENT_INFO` yapısı, tek bir işlevin tüm bağımsız değişkenlerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="eb7cd-118">The `COR_PRF_FUNCTION_ARGUMENT_INFO` structure represents all the arguments of a single function.</span></span> <span data-ttu-id="eb7cd-119">İşlev bağımsız değişkenlerinin tüm bloklarına başvurmak için bir dizi kullanır.</span><span class="sxs-lookup"><span data-stu-id="eb7cd-119">It uses an array to reference all the blocks of function arguments.</span></span> <span data-ttu-id="eb7cd-120">Bu nedenle, tek bir işlev için, her biri bir veya daha fazla işlev bağımsız değişkenine işaret eden birden çok `COR_PRF_FUNCTION_ARGUMENT_RANGE` yapısına başvuran tek bir `COR_PRF_FUNCTION_ARGUMENT_INFO` yapısı vardır.</span><span class="sxs-lookup"><span data-stu-id="eb7cd-120">So, for a single function, you have a single `COR_PRF_FUNCTION_ARGUMENT_INFO` structure, which references multiple `COR_PRF_FUNCTION_ARGUMENT_RANGE` structures, each of which points to one or more function arguments.</span></span>  
  
 <span data-ttu-id="eb7cd-121">Yazmaçlarda depolanan bağımsız değişkenler, yapıları oluşturmak için belleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="eb7cd-121">Arguments that are stored in registers are spilled into memory to build the structures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb7cd-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eb7cd-122">Requirements</span></span>  
 <span data-ttu-id="eb7cd-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb7cd-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb7cd-124">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="eb7cd-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="eb7cd-125">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="eb7cd-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb7cd-126">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb7cd-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb7cd-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb7cd-127">See also</span></span>

- [<span data-ttu-id="eb7cd-128">Profil Oluşturma Yapıları</span><span class="sxs-lookup"><span data-stu-id="eb7cd-128">Profiling Structures</span></span>](profiling-structures.md)
