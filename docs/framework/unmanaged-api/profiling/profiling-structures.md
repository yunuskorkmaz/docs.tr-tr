---
title: Profil Oluşturma Yapıları
ms.date: 03/30/2017
helpviewer_keywords:
- profiling structures [.NET Framework]
- unmanaged structures [.NET Framework], profiling
- structures [.NET Framework profiling]
ms.assetid: 750385f2-f365-41b1-939f-ca2f2ff9b466
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 229218cb15963846da91f688b0d2faacb20031c8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000447"
---
# <a name="profiling-structures"></a><span data-ttu-id="c1f76-102">Profil Oluşturma Yapıları</span><span class="sxs-lookup"><span data-stu-id="c1f76-102">Profiling Structures</span></span>
<span data-ttu-id="c1f76-103">Bu bölümde, profil oluşturma API'SİNİN kullandığı yönetilmeyen yapıları açıklar.</span><span class="sxs-lookup"><span data-stu-id="c1f76-103">This section describes the unmanaged structures that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c1f76-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="c1f76-104">In This Section</span></span>  
 [<span data-ttu-id="c1f76-105">COR_PRF_ASSEMBLY_REFERENCE_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="c1f76-105">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)  
 <span data-ttu-id="c1f76-106">Ortak dil çalışma zamanı, bir derleme başvurusu kapanış Yürüme yaparken göz önünde bulundurmanız gereken bir başvuru bütünleştirilmiş kodu hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c1f76-106">Provides the common language runtime with information about a reference assembly that it should consider when performing an assembly reference closure walk.</span></span>  
  
 [<span data-ttu-id="c1f76-107">COR_PRF_CODE_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="c1f76-107">COR_PRF_CODE_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)  
 <span data-ttu-id="c1f76-108">Yerel kod bellekte bitişik bir bloğunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c1f76-108">Represents one contiguous block of native code stored in memory.</span></span>  
  
 [<span data-ttu-id="c1f76-109">COR_PRF_EX_CLAUSE_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="c1f76-109">COR_PRF_EX_CLAUSE_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-ex-clause-info-structure.md)  
 <span data-ttu-id="c1f76-110">Bir özel durum yan tümcesi örneği ve ilişkili çerçevesini hakkındaki bilgileri saklar.</span><span class="sxs-lookup"><span data-stu-id="c1f76-110">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
 [<span data-ttu-id="c1f76-111">COR_PRF_FUNCTION Yapısı</span><span class="sxs-lookup"><span data-stu-id="c1f76-111">COR_PRF_FUNCTION Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-structure.md)  
 <span data-ttu-id="c1f76-112">Znovu sürümü kimliği Kimliğini birleştirerek bir işlev benzersiz bir gösterimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="c1f76-112">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
 [<span data-ttu-id="c1f76-113">COR_PRF_FUNCTION_ARGUMENT_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="c1f76-113">COR_PRF_FUNCTION_ARGUMENT_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md)  
 <span data-ttu-id="c1f76-114">Soldan sağa doğru sırayla bir işlevin bağımsız değişkenlerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c1f76-114">Represents a function's arguments, in left-to-right order.</span></span>  
  
 [<span data-ttu-id="c1f76-115">COR_PRF_FUNCTION_ARGUMENT_RANGE Yapısı</span><span class="sxs-lookup"><span data-stu-id="c1f76-115">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md)  
 <span data-ttu-id="c1f76-116">İşlev bağımsız değişkenleri bitişik bellek sırayla soldan sağa depolanan bloğunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c1f76-116">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
 [<span data-ttu-id="c1f76-117">COR_PRF_GC_GENERATION_RANGE Yapısı</span><span class="sxs-lookup"><span data-stu-id="c1f76-117">COR_PRF_GC_GENERATION_RANGE Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md)  
 <span data-ttu-id="c1f76-118">Çöp toplama aşamasında bir bellek aralığı (yani, blok) açıklar.</span><span class="sxs-lookup"><span data-stu-id="c1f76-118">Describes a range (that is, block) of memory that is undergoing garbage collection.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c1f76-119">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="c1f76-119">Related Sections</span></span>  
 <span data-ttu-id="c1f76-120">COR_DEBUG_IL_TO_NATIVE_MAP</span><span class="sxs-lookup"><span data-stu-id="c1f76-120">COR_DEBUG_IL_TO_NATIVE_MAP</span></span>  
  
 <span data-ttu-id="c1f76-121">COR_IL_MAP</span><span class="sxs-lookup"><span data-stu-id="c1f76-121">COR_IL_MAP</span></span>  
  
 [<span data-ttu-id="c1f76-122">Profil Oluşturmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c1f76-122">Profiling Overview</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [<span data-ttu-id="c1f76-123">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c1f76-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [<span data-ttu-id="c1f76-124">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="c1f76-124">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [<span data-ttu-id="c1f76-125">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="c1f76-125">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
