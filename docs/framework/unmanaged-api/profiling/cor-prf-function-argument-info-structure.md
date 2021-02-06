---
description: 'Daha fazla bilgi edinin: COR_PRF_FUNCTION_ARGUMENT_INFO yapısı'
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
ms.openlocfilehash: c40c9b20dad79fa36a1ed4471106a54f2c55b422
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649071"
---
# <a name="cor_prf_function_argument_info-structure"></a><span data-ttu-id="a737b-103">COR_PRF_FUNCTION_ARGUMENT_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="a737b-103">COR_PRF_FUNCTION_ARGUMENT_INFO Structure</span></span>

<span data-ttu-id="a737b-104">İşlevin bağımsız değişkenlerini soldan sağa sırada temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a737b-104">Represents a function's arguments, in left-to-right order.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a737b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a737b-105">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_INFO {  
    ULONG numRanges;  
    ULONG totalArgumentSize;  
    COR_PRF_FUNCTION_ARGUMENT_RANGE ranges[1];  
} COR_PRF_FUNCTION_ARGUMENT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="a737b-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="a737b-106">Members</span></span>  
  
|<span data-ttu-id="a737b-107">Üye</span><span class="sxs-lookup"><span data-stu-id="a737b-107">Member</span></span>|<span data-ttu-id="a737b-108">Description</span><span class="sxs-lookup"><span data-stu-id="a737b-108">Description</span></span>|  
|------------|-----------------|  
|`numRanges`|<span data-ttu-id="a737b-109">Bağımsız değişken blok sayısı.</span><span class="sxs-lookup"><span data-stu-id="a737b-109">The number of blocks of arguments.</span></span> <span data-ttu-id="a737b-110">Diğer bir deyişle, bu değer dizideki [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) yapıların sayısıdır `ranges` .</span><span class="sxs-lookup"><span data-stu-id="a737b-110">That is, this value is the number of [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) structures in the `ranges` array.</span></span>|  
|`totalArgumentSize`|<span data-ttu-id="a737b-111">Tüm bağımsız değişkenlerin toplam boyutu.</span><span class="sxs-lookup"><span data-stu-id="a737b-111">The total size of all arguments.</span></span> <span data-ttu-id="a737b-112">Diğer bir deyişle, bu değer bağımsız değişken uzunluklarının toplamıdır.</span><span class="sxs-lookup"><span data-stu-id="a737b-112">In other words, this value is the sum of the argument lengths.</span></span>|  
|`ranges`|<span data-ttu-id="a737b-113">`COR_PRF_FUNCTION_ARGUMENT_RANGE`Her biri bir işlev bağımsız değişkenlerinin bloğunu temsil eden yapıların dizisi.</span><span class="sxs-lookup"><span data-stu-id="a737b-113">An array of `COR_PRF_FUNCTION_ARGUMENT_RANGE` structures, each of which represents one block of function arguments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a737b-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a737b-114">Remarks</span></span>  

 <span data-ttu-id="a737b-115">Bir işlevde birçok bağımsız değişken olabilir.</span><span class="sxs-lookup"><span data-stu-id="a737b-115">A function may have many arguments.</span></span> <span data-ttu-id="a737b-116">Bu bağımsız değişkenler bellekte bitişik olarak depolanmayabilir.</span><span class="sxs-lookup"><span data-stu-id="a737b-116">Those arguments might not be stored contiguously in memory.</span></span> <span data-ttu-id="a737b-117">Tek bir yerde üç bağımsız değişkeni, başka bir yerde iki bağımsız değişken bloğunu ve bir bağımsız değişkenin son bloğunu farklı bir yerde engellemeniz olabilir.</span><span class="sxs-lookup"><span data-stu-id="a737b-117">You might have a block of three arguments in one place, a block of two arguments in another place, and a final block of one argument in a different place.</span></span> <span data-ttu-id="a737b-118">Bu bağımsız değişkenlerin hepsi aynı işleve yöneliktir; yalnızca farklı yerlerde depolanırlar.</span><span class="sxs-lookup"><span data-stu-id="a737b-118">These arguments are all for the same function; they're just stored in different places.</span></span>  
  
 <span data-ttu-id="a737b-119">`COR_PRF_FUNCTION_ARGUMENT_INFO`Yapı, tek bir işlevin tüm bağımsız değişkenlerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a737b-119">The `COR_PRF_FUNCTION_ARGUMENT_INFO` structure represents all the arguments of a single function.</span></span> <span data-ttu-id="a737b-120">İşlev bağımsız değişkenlerinin tüm bloklarına başvurmak için bir dizi kullanır.</span><span class="sxs-lookup"><span data-stu-id="a737b-120">It uses an array to reference all the blocks of function arguments.</span></span> <span data-ttu-id="a737b-121">Bu nedenle, tek bir işlev için, `COR_PRF_FUNCTION_ARGUMENT_INFO` `COR_PRF_FUNCTION_ARGUMENT_RANGE` her biri bir veya daha fazla işlev bağımsız değişkenine işaret eden birden çok yapıya başvuran tek bir yapıya sahip olursunuz.</span><span class="sxs-lookup"><span data-stu-id="a737b-121">So, for a single function, you have a single `COR_PRF_FUNCTION_ARGUMENT_INFO` structure, which references multiple `COR_PRF_FUNCTION_ARGUMENT_RANGE` structures, each of which points to one or more function arguments.</span></span>  
  
 <span data-ttu-id="a737b-122">Yazmaçlarda depolanan bağımsız değişkenler, yapıları oluşturmak için belleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="a737b-122">Arguments that are stored in registers are spilled into memory to build the structures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a737b-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a737b-123">Requirements</span></span>  

 <span data-ttu-id="a737b-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a737b-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a737b-125">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="a737b-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="a737b-126">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a737b-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a737b-127">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a737b-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a737b-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a737b-128">See also</span></span>

- [<span data-ttu-id="a737b-129">Profil Oluşturma Yapıları</span><span class="sxs-lookup"><span data-stu-id="a737b-129">Profiling Structures</span></span>](profiling-structures.md)
