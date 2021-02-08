---
description: Daha fazla bilgi için bkz. profil oluşturma yapıları
title: Profil Oluşturma Yapıları
ms.date: 03/30/2017
helpviewer_keywords:
- profiling structures [.NET Framework]
- unmanaged structures [.NET Framework], profiling
- structures [.NET Framework profiling]
ms.assetid: 750385f2-f365-41b1-939f-ca2f2ff9b466
ms.openlocfilehash: 7a76c49aaa301ba45c41fb2eb3f7770539dcc6c0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798894"
---
# <a name="profiling-structures"></a><span data-ttu-id="9a9cb-103">Profil Oluşturma Yapıları</span><span class="sxs-lookup"><span data-stu-id="9a9cb-103">Profiling Structures</span></span>

<span data-ttu-id="9a9cb-104">Bu bölümde profil oluşturma API 'sinin kullandığı yönetilmeyen yapılar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9a9cb-104">This section describes the unmanaged structures that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9a9cb-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="9a9cb-105">In This Section</span></span>  

 [<span data-ttu-id="9a9cb-106">COR_PRF_ASSEMBLY_REFERENCE_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="9a9cb-106">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>](cor-prf-assembly-reference-info-structure.md)  
 <span data-ttu-id="9a9cb-107">Ortak dil çalışma zamanını, bir derleme başvurusu kapatma ilerlemesi gerçekleştirirken göz önünde bulundurmanız gereken bir başvuru bütünleştirilmiş kodu hakkında bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9a9cb-107">Provides the common language runtime with information about a reference assembly that it should consider when performing an assembly reference closure walk.</span></span>  
  
 [<span data-ttu-id="9a9cb-108">COR_PRF_CODE_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="9a9cb-108">COR_PRF_CODE_INFO Structure</span></span>](cor-prf-code-info-structure.md)  
 <span data-ttu-id="9a9cb-109">Bellekte depolanan yerel kodun bir bitişik bloğunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9a9cb-109">Represents one contiguous block of native code stored in memory.</span></span>  
  
 [<span data-ttu-id="9a9cb-110">COR_PRF_EX_CLAUSE_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="9a9cb-110">COR_PRF_EX_CLAUSE_INFO Structure</span></span>](cor-prf-ex-clause-info-structure.md)  
 <span data-ttu-id="9a9cb-111">Belirli bir özel durum yan tümcesi ve onunla ilişkili çerçevesini hakkında bilgi depolar.</span><span class="sxs-lookup"><span data-stu-id="9a9cb-111">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
 [<span data-ttu-id="9a9cb-112">COR_PRF_FUNCTION Yapısı</span><span class="sxs-lookup"><span data-stu-id="9a9cb-112">COR_PRF_FUNCTION Structure</span></span>](cor-prf-function-structure.md)  
 <span data-ttu-id="9a9cb-113">, KIMLIĞINI yeniden derlenmesi sürümünün KIMLIĞIYLE birleştirerek bir işlevin benzersiz bir gösterimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="9a9cb-113">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
 [<span data-ttu-id="9a9cb-114">COR_PRF_FUNCTION_ARGUMENT_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="9a9cb-114">COR_PRF_FUNCTION_ARGUMENT_INFO Structure</span></span>](cor-prf-function-argument-info-structure.md)  
 <span data-ttu-id="9a9cb-115">İşlevin bağımsız değişkenlerini soldan sağa sırada temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9a9cb-115">Represents a function's arguments, in left-to-right order.</span></span>  
  
 [<span data-ttu-id="9a9cb-116">COR_PRF_FUNCTION_ARGUMENT_RANGE Yapısı</span><span class="sxs-lookup"><span data-stu-id="9a9cb-116">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>](cor-prf-function-argument-range-structure.md)  
 <span data-ttu-id="9a9cb-117">Bitişik olarak depolanan bir işlev bağımsız değişkenlerinin bloğunu, bellekte soldan sağa doğru sırada olacak şekilde gösterir.</span><span class="sxs-lookup"><span data-stu-id="9a9cb-117">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
 [<span data-ttu-id="9a9cb-118">COR_PRF_GC_GENERATION_RANGE Yapısı</span><span class="sxs-lookup"><span data-stu-id="9a9cb-118">COR_PRF_GC_GENERATION_RANGE Structure</span></span>](cor-prf-gc-generation-range-structure.md)  
 <span data-ttu-id="9a9cb-119">Çöp toplama işlemi yapılmakta olan belleğin bir aralığını (yani bloğunu) açıklar.</span><span class="sxs-lookup"><span data-stu-id="9a9cb-119">Describes a range (that is, block) of memory that is undergoing garbage collection.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9a9cb-120">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="9a9cb-120">Related Sections</span></span>  

 <span data-ttu-id="9a9cb-121">COR_DEBUG_IL_TO_NATIVE_MAP</span><span class="sxs-lookup"><span data-stu-id="9a9cb-121">COR_DEBUG_IL_TO_NATIVE_MAP</span></span>  
  
 <span data-ttu-id="9a9cb-122">COR_IL_MAP</span><span class="sxs-lookup"><span data-stu-id="9a9cb-122">COR_IL_MAP</span></span>  
  
 [<span data-ttu-id="9a9cb-123">Profil Oluşturmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9a9cb-123">Profiling Overview</span></span>](profiling-overview.md)  
  
 [<span data-ttu-id="9a9cb-124">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9a9cb-124">Profiling Interfaces</span></span>](profiling-interfaces.md)  
  
 [<span data-ttu-id="9a9cb-125">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="9a9cb-125">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)  
  
 [<span data-ttu-id="9a9cb-126">Profil Oluşturma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="9a9cb-126">Profiling Enumerations</span></span>](profiling-enumerations.md)
