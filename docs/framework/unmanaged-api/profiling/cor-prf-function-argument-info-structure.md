---
title: "COR_PRF_FUNCTION_ARGUMENT_INFO Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_FUNCTION_ARGUMENT_INFO
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_FUNCTION_ARGUMENT_INFO
helpviewer_keywords: COR_PRF_FUNCTION_ARGUMENT_INFO structure [.NET Framework profiling]
ms.assetid: 07cf3bab-e193-4991-8205-3f41cf2d67b3
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e26377fe3c5cfbae68f90087e3fb624ae4db0dc8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="corprffunctionargumentinfo-structure"></a><span data-ttu-id="e49ef-102">COR_PRF_FUNCTION_ARGUMENT_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="e49ef-102">COR_PRF_FUNCTION_ARGUMENT_INFO Structure</span></span>
<span data-ttu-id="e49ef-103">Soldan sağa sırayla bir işlevin bağımsız değişkenler temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e49ef-103">Represents a function's arguments, in left-to-right order.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e49ef-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e49ef-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_INFO {  
    ULONG numRanges;  
    ULONG totalArgumentSize;  
    COR_PRF_FUNCTION_ARGUMENT_RANGE ranges[1];  
} COR_PRF_FUNCTION_ARGUMENT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="e49ef-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e49ef-105">Members</span></span>  
  
|<span data-ttu-id="e49ef-106">Üye</span><span class="sxs-lookup"><span data-stu-id="e49ef-106">Member</span></span>|<span data-ttu-id="e49ef-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e49ef-107">Description</span></span>|  
|------------|-----------------|  
|`numRanges`|<span data-ttu-id="e49ef-108">Bağımsız değişkenler blok sayısı.</span><span class="sxs-lookup"><span data-stu-id="e49ef-108">The number of blocks of arguments.</span></span> <span data-ttu-id="e49ef-109">Diğer bir deyişle, bu değer sayısıdır [cor_prf_functıon_argument_range](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) içindeki yapıları `ranges` dizi.</span><span class="sxs-lookup"><span data-stu-id="e49ef-109">That is, this value is the number of [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structures in the `ranges` array.</span></span>|  
|`totalArgumentSize`|<span data-ttu-id="e49ef-110">Tüm bağımsız değişkenler toplam boyutu.</span><span class="sxs-lookup"><span data-stu-id="e49ef-110">The total size of all arguments.</span></span> <span data-ttu-id="e49ef-111">Diğer bir deyişle, bu değer bağımsız değişken uzunlukta toplamıdır.</span><span class="sxs-lookup"><span data-stu-id="e49ef-111">In other words, this value is the sum of the argument lengths.</span></span>|  
|`ranges`|<span data-ttu-id="e49ef-112">Bir dizi `COR_PRF_FUNCTION_ARGUMENT_RANGE` yapıları, her biri bir işlev bağımsız değişkenleri bloğunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e49ef-112">An array of `COR_PRF_FUNCTION_ARGUMENT_RANGE` structures, each of which represents one block of function arguments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e49ef-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e49ef-113">Remarks</span></span>  
 <span data-ttu-id="e49ef-114">Bir işlev fazla sayıda bağımsız değişken olabilir.</span><span class="sxs-lookup"><span data-stu-id="e49ef-114">A function may have many arguments.</span></span> <span data-ttu-id="e49ef-115">Bu bağımsız değişkenlerden bitişik bellek depolanabilir değil.</span><span class="sxs-lookup"><span data-stu-id="e49ef-115">Those arguments might not be stored contiguously in memory.</span></span> <span data-ttu-id="e49ef-116">Tek bir yerde üç bağımsız değişken bloğunu, başka bir yerde iki bağımsız değişken bir blok ve farklı bir yerde tek bir bağımsız değişken son bloğunu olabilir.</span><span class="sxs-lookup"><span data-stu-id="e49ef-116">You might have a block of three arguments in one place, a block of two arguments in another place, and a final block of one argument in a different place.</span></span> <span data-ttu-id="e49ef-117">Bu bağımsız değişkenler tüm aynı işlevin; yalnızca farklı yerlerde depolandıkları.</span><span class="sxs-lookup"><span data-stu-id="e49ef-117">These arguments are all for the same function; they're just stored in different places.</span></span>  
  
 <span data-ttu-id="e49ef-118">`COR_PRF_FUNCTION_ARGUMENT_INFO` Yapısı tek bir işlevin tüm bağımsız değişkenler temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e49ef-118">The `COR_PRF_FUNCTION_ARGUMENT_INFO` structure represents all the arguments of a single function.</span></span> <span data-ttu-id="e49ef-119">İşlev bağımsız değişkenleri tüm bloklarını başvurmak için bir dizi kullanır.</span><span class="sxs-lookup"><span data-stu-id="e49ef-119">It uses an array to reference all the blocks of function arguments.</span></span> <span data-ttu-id="e49ef-120">Bu nedenle, tek bir işlev için tek bir elinizde `COR_PRF_FUNCTION_ARGUMENT_INFO` birden çok başvuran yapısı `COR_PRF_FUNCTION_ARGUMENT_RANGE` yapıları, her biri bir veya daha fazla işlev bağımsız değişkenleri için işaret eder.</span><span class="sxs-lookup"><span data-stu-id="e49ef-120">So, for a single function, you have a single `COR_PRF_FUNCTION_ARGUMENT_INFO` structure, which references multiple `COR_PRF_FUNCTION_ARGUMENT_RANGE` structures, each of which points to one or more function arguments.</span></span>  
  
 <span data-ttu-id="e49ef-121">Yazmaçları depolanan bağımsız değişkenleri yapılarının belleğe geçmiş.</span><span class="sxs-lookup"><span data-stu-id="e49ef-121">Arguments that are stored in registers are spilled into memory to build the structures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e49ef-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e49ef-122">Requirements</span></span>  
 <span data-ttu-id="e49ef-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e49ef-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e49ef-124">**Başlık:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="e49ef-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="e49ef-125">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e49ef-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e49ef-126">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e49ef-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e49ef-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e49ef-127">See Also</span></span>  
 [<span data-ttu-id="e49ef-128">Profil Oluşturma Yapıları</span><span class="sxs-lookup"><span data-stu-id="e49ef-128">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
