---
title: "Profil Oluşturma Yapıları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- profiling structures [.NET Framework]
- unmanaged structures [.NET Framework], profiling
- structures [.NET Framework profiling]
ms.assetid: 750385f2-f365-41b1-939f-ca2f2ff9b466
caps.latest.revision: "27"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 42762812c9d27073fac34b20df5011b386f05740
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="profiling-structures"></a><span data-ttu-id="42ad1-102">Profil Oluşturma Yapıları</span><span class="sxs-lookup"><span data-stu-id="42ad1-102">Profiling Structures</span></span>
<span data-ttu-id="42ad1-103">Bu bölümde, profil oluşturma API'si kullanan yönetilmeyen yapılar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="42ad1-103">This section describes the unmanaged structures that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="42ad1-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="42ad1-104">In This Section</span></span>  
 [<span data-ttu-id="42ad1-105">Cor_prf_assembly_reference_ınfo yapısı</span><span class="sxs-lookup"><span data-stu-id="42ad1-105">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)  
 <span data-ttu-id="42ad1-106">Ortak dil çalışma zamanı bir derleme başvurusu kapatma ilerlemesi gerçekleştirirken düşünmelisiniz bir başvuru derleme hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="42ad1-106">Provides the common language runtime with information about a reference assembly that it should consider when performing an assembly reference closure walk.</span></span>  
  
 [<span data-ttu-id="42ad1-107">Cor_prf_code_ınfo yapısı</span><span class="sxs-lookup"><span data-stu-id="42ad1-107">COR_PRF_CODE_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)  
 <span data-ttu-id="42ad1-108">Yerel kod bellekte bir bitişik bloğunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="42ad1-108">Represents one contiguous block of native code stored in memory.</span></span>  
  
 [<span data-ttu-id="42ad1-109">Cor_prf_ex_clause_ınfo yapısı</span><span class="sxs-lookup"><span data-stu-id="42ad1-109">COR_PRF_EX_CLAUSE_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-ex-clause-info-structure.md)  
 <span data-ttu-id="42ad1-110">Bir özel durum yan tümcesi örneği ve ilişkili çerçevesini ilgili bilgileri depolar.</span><span class="sxs-lookup"><span data-stu-id="42ad1-110">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
 [<span data-ttu-id="42ad1-111">Cor_prf_functıon yapısı</span><span class="sxs-lookup"><span data-stu-id="42ad1-111">COR_PRF_FUNCTION Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-structure.md)  
 <span data-ttu-id="42ad1-112">Derlenmiş sürüm kimliği Kimliğini birleştiren bir işlev benzersiz bir gösterimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="42ad1-112">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
 [<span data-ttu-id="42ad1-113">Cor_prf_functıon_argument_ınfo yapısı</span><span class="sxs-lookup"><span data-stu-id="42ad1-113">COR_PRF_FUNCTION_ARGUMENT_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md)  
 <span data-ttu-id="42ad1-114">Soldan sağa sırayla bir işlevin bağımsız değişkenler temsil eder.</span><span class="sxs-lookup"><span data-stu-id="42ad1-114">Represents a function's arguments, in left-to-right order.</span></span>  
  
 [<span data-ttu-id="42ad1-115">Cor_prf_functıon_argument_range yapısı</span><span class="sxs-lookup"><span data-stu-id="42ad1-115">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md)  
 <span data-ttu-id="42ad1-116">İşlev bağımsız değişkenleri bitişik bellek soldan sağa sırayla depolanan bloğunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="42ad1-116">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
 [<span data-ttu-id="42ad1-117">Cor_prf_gc_generatıon_range yapısı</span><span class="sxs-lookup"><span data-stu-id="42ad1-117">COR_PRF_GC_GENERATION_RANGE Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md)  
 <span data-ttu-id="42ad1-118">Çöp toplama yapılıyor bir bellek aralığı (yani, blok) açıklar.</span><span class="sxs-lookup"><span data-stu-id="42ad1-118">Describes a range (that is, block) of memory that is undergoing garbage collection.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="42ad1-119">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="42ad1-119">Related Sections</span></span>  
 <span data-ttu-id="42ad1-120">COR_DEBUG_IL_TO_NATIVE_MAP</span><span class="sxs-lookup"><span data-stu-id="42ad1-120">COR_DEBUG_IL_TO_NATIVE_MAP</span></span>  
  
 <span data-ttu-id="42ad1-121">COR_IL_MAP</span><span class="sxs-lookup"><span data-stu-id="42ad1-121">COR_IL_MAP</span></span>  
  
 [<span data-ttu-id="42ad1-122">Profil oluşturmaya genel bakış</span><span class="sxs-lookup"><span data-stu-id="42ad1-122">Profiling Overview</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [<span data-ttu-id="42ad1-123">Profil oluşturma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="42ad1-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [<span data-ttu-id="42ad1-124">Profil oluşturma genel statik işlevleri</span><span class="sxs-lookup"><span data-stu-id="42ad1-124">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [<span data-ttu-id="42ad1-125">Profil oluşturma numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="42ad1-125">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
