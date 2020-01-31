---
title: Profil Oluşturma Yapıları
ms.date: 03/30/2017
helpviewer_keywords:
- profiling structures [.NET Framework]
- unmanaged structures [.NET Framework], profiling
- structures [.NET Framework profiling]
ms.assetid: 750385f2-f365-41b1-939f-ca2f2ff9b466
ms.openlocfilehash: c3bbc66079e05abf494ad112b8aa0ac68e3c3e2f
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868115"
---
# <a name="profiling-structures"></a><span data-ttu-id="4273a-102">Profil Oluşturma Yapıları</span><span class="sxs-lookup"><span data-stu-id="4273a-102">Profiling Structures</span></span>
<span data-ttu-id="4273a-103">Bu bölümde profil oluşturma API 'sinin kullandığı yönetilmeyen yapılar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4273a-103">This section describes the unmanaged structures that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4273a-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="4273a-104">In This Section</span></span>  
 [<span data-ttu-id="4273a-105">COR_PRF_ASSEMBLY_REFERENCE_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="4273a-105">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>](cor-prf-assembly-reference-info-structure.md)  
 <span data-ttu-id="4273a-106">Ortak dil çalışma zamanını, bir derleme başvurusu kapatma ilerlemesi gerçekleştirirken göz önünde bulundurmanız gereken bir başvuru bütünleştirilmiş kodu hakkında bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="4273a-106">Provides the common language runtime with information about a reference assembly that it should consider when performing an assembly reference closure walk.</span></span>  
  
 [<span data-ttu-id="4273a-107">COR_PRF_CODE_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="4273a-107">COR_PRF_CODE_INFO Structure</span></span>](cor-prf-code-info-structure.md)  
 <span data-ttu-id="4273a-108">Bellekte depolanan yerel kodun bir bitişik bloğunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4273a-108">Represents one contiguous block of native code stored in memory.</span></span>  
  
 [<span data-ttu-id="4273a-109">COR_PRF_EX_CLAUSE_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="4273a-109">COR_PRF_EX_CLAUSE_INFO Structure</span></span>](cor-prf-ex-clause-info-structure.md)  
 <span data-ttu-id="4273a-110">Belirli bir özel durum yan tümcesi ve onunla ilişkili çerçevesini hakkında bilgi depolar.</span><span class="sxs-lookup"><span data-stu-id="4273a-110">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
 [<span data-ttu-id="4273a-111">COR_PRF_FUNCTION Yapısı</span><span class="sxs-lookup"><span data-stu-id="4273a-111">COR_PRF_FUNCTION Structure</span></span>](cor-prf-function-structure.md)  
 <span data-ttu-id="4273a-112">, KIMLIĞINI yeniden derlenmesi sürümünün KIMLIĞIYLE birleştirerek bir işlevin benzersiz bir gösterimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="4273a-112">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
 [<span data-ttu-id="4273a-113">COR_PRF_FUNCTION_ARGUMENT_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="4273a-113">COR_PRF_FUNCTION_ARGUMENT_INFO Structure</span></span>](cor-prf-function-argument-info-structure.md)  
 <span data-ttu-id="4273a-114">İşlevin bağımsız değişkenlerini soldan sağa sırada temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4273a-114">Represents a function's arguments, in left-to-right order.</span></span>  
  
 [<span data-ttu-id="4273a-115">COR_PRF_FUNCTION_ARGUMENT_RANGE Yapısı</span><span class="sxs-lookup"><span data-stu-id="4273a-115">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>](cor-prf-function-argument-range-structure.md)  
 <span data-ttu-id="4273a-116">Bitişik olarak depolanan bir işlev bağımsız değişkenlerinin bloğunu, bellekte soldan sağa doğru sırada olacak şekilde gösterir.</span><span class="sxs-lookup"><span data-stu-id="4273a-116">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
 [<span data-ttu-id="4273a-117">COR_PRF_GC_GENERATION_RANGE Yapısı</span><span class="sxs-lookup"><span data-stu-id="4273a-117">COR_PRF_GC_GENERATION_RANGE Structure</span></span>](cor-prf-gc-generation-range-structure.md)  
 <span data-ttu-id="4273a-118">Çöp toplama işlemi yapılmakta olan belleğin bir aralığını (yani bloğunu) açıklar.</span><span class="sxs-lookup"><span data-stu-id="4273a-118">Describes a range (that is, block) of memory that is undergoing garbage collection.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4273a-119">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="4273a-119">Related Sections</span></span>  
 <span data-ttu-id="4273a-120">COR_DEBUG_IL_TO_NATIVE_MAP</span><span class="sxs-lookup"><span data-stu-id="4273a-120">COR_DEBUG_IL_TO_NATIVE_MAP</span></span>  
  
 <span data-ttu-id="4273a-121">COR_IL_MAP</span><span class="sxs-lookup"><span data-stu-id="4273a-121">COR_IL_MAP</span></span>  
  
 [<span data-ttu-id="4273a-122">Profil Oluşturmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4273a-122">Profiling Overview</span></span>](profiling-overview.md)  
  
 [<span data-ttu-id="4273a-123">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4273a-123">Profiling Interfaces</span></span>](profiling-interfaces.md)  
  
 [<span data-ttu-id="4273a-124">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="4273a-124">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)  
  
 [<span data-ttu-id="4273a-125">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="4273a-125">Profiling Enumerations</span></span>](profiling-enumerations.md)
