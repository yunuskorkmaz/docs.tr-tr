---
description: Daha fazla bilgi için bkz. profil oluşturma yapıları
title: Profil Oluşturma Yapıları
ms.date: 03/30/2017
helpviewer_keywords:
- profiling structures [.NET Framework]
- unmanaged structures [.NET Framework], profiling
- structures [.NET Framework profiling]
ms.assetid: 750385f2-f365-41b1-939f-ca2f2ff9b466
ms.openlocfilehash: 176830cac519f22864ba004b176cb575d80e50e2
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760242"
---
# <a name="profiling-structures"></a><span data-ttu-id="ab196-103">Profil Oluşturma Yapıları</span><span class="sxs-lookup"><span data-stu-id="ab196-103">Profiling Structures</span></span>

<span data-ttu-id="ab196-104">Bu bölümde profil oluşturma API 'sinin kullandığı yönetilmeyen yapılar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ab196-104">This section describes the unmanaged structures that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ab196-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="ab196-105">In This Section</span></span>  

 [<span data-ttu-id="ab196-106">COR_PRF_ASSEMBLY_REFERENCE_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="ab196-106">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>](cor-prf-assembly-reference-info-structure.md)  
 <span data-ttu-id="ab196-107">Ortak dil çalışma zamanını, bir derleme başvurusu kapatma ilerlemesi gerçekleştirirken göz önünde bulundurmanız gereken bir başvuru bütünleştirilmiş kodu hakkında bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ab196-107">Provides the common language runtime with information about a reference assembly that it should consider when performing an assembly reference closure walk.</span></span>  
  
 [<span data-ttu-id="ab196-108">COR_PRF_CODE_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="ab196-108">COR_PRF_CODE_INFO Structure</span></span>](cor-prf-code-info-structure.md)  
 <span data-ttu-id="ab196-109">Bellekte depolanan yerel kodun bir bitişik bloğunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ab196-109">Represents one contiguous block of native code stored in memory.</span></span>  
  
 [<span data-ttu-id="ab196-110">COR_PRF_EX_CLAUSE_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="ab196-110">COR_PRF_EX_CLAUSE_INFO Structure</span></span>](cor-prf-ex-clause-info-structure.md)  
 <span data-ttu-id="ab196-111">Belirli bir özel durum yan tümcesi ve onunla ilişkili çerçevesini hakkında bilgi depolar.</span><span class="sxs-lookup"><span data-stu-id="ab196-111">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
 [<span data-ttu-id="ab196-112">COR_PRF_FUNCTION Yapısı</span><span class="sxs-lookup"><span data-stu-id="ab196-112">COR_PRF_FUNCTION Structure</span></span>](cor-prf-function-structure.md)  
 <span data-ttu-id="ab196-113">, KIMLIĞINI yeniden derlenmesi sürümünün KIMLIĞIYLE birleştirerek bir işlevin benzersiz bir gösterimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="ab196-113">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
 [<span data-ttu-id="ab196-114">COR_PRF_FUNCTION_ARGUMENT_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="ab196-114">COR_PRF_FUNCTION_ARGUMENT_INFO Structure</span></span>](cor-prf-function-argument-info-structure.md)  
 <span data-ttu-id="ab196-115">İşlevin bağımsız değişkenlerini soldan sağa sırada temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ab196-115">Represents a function's arguments, in left-to-right order.</span></span>  
  
 [<span data-ttu-id="ab196-116">COR_PRF_FUNCTION_ARGUMENT_RANGE Yapısı</span><span class="sxs-lookup"><span data-stu-id="ab196-116">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>](cor-prf-function-argument-range-structure.md)  
 <span data-ttu-id="ab196-117">Bitişik olarak depolanan bir işlev bağımsız değişkenlerinin bloğunu, bellekte soldan sağa doğru sırada olacak şekilde gösterir.</span><span class="sxs-lookup"><span data-stu-id="ab196-117">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
 [<span data-ttu-id="ab196-118">COR_PRF_GC_GENERATION_RANGE Yapısı</span><span class="sxs-lookup"><span data-stu-id="ab196-118">COR_PRF_GC_GENERATION_RANGE Structure</span></span>](cor-prf-gc-generation-range-structure.md)  
 <span data-ttu-id="ab196-119">Çöp toplama işlemi yapılmakta olan belleğin bir aralığını (yani bloğunu) açıklar.</span><span class="sxs-lookup"><span data-stu-id="ab196-119">Describes a range (that is, block) of memory that is undergoing garbage collection.</span></span>  

 <span data-ttu-id="ab196-120">[COR_PRF_EVENTPIPE_PROVIDER_CONFIG yapısı](cor-prf-eventpipe-provider-config-structure.md) Bir EventPipe sağlayıcısını yapılandırmak için gereken alanları açıklar.</span><span class="sxs-lookup"><span data-stu-id="ab196-120">[COR_PRF_EVENTPIPE_PROVIDER_CONFIG Structure](cor-prf-eventpipe-provider-config-structure.md) Describes the fields necessary to configure an EventPipe provider.</span></span>

 <span data-ttu-id="ab196-121">[COR_PRF_EVENTPIPE_PARAM_DESC yapısı](cor-prf-eventpipe-param-desc-structure.md) Bir EventPipe olayının parametre adını ve türünü açıklar.</span><span class="sxs-lookup"><span data-stu-id="ab196-121">[COR_PRF_EVENTPIPE_PARAM_DESC Structure](cor-prf-eventpipe-param-desc-structure.md) Describes the parameter name and type for an EventPipe event.</span></span>

 <span data-ttu-id="ab196-122">[COR_PRF_EVENT_DATA yapısı](cor-prf-event-data-structure.md) Yazılan bir EventPipe olayının olay verilerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="ab196-122">[COR_PRF_EVENT_DATA Structure](cor-prf-event-data-structure.md) Describes the event data for an EventPipe event being written.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="ab196-123">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="ab196-123">Related Sections</span></span>  

 <span data-ttu-id="ab196-124">COR_DEBUG_IL_TO_NATIVE_MAP</span><span class="sxs-lookup"><span data-stu-id="ab196-124">COR_DEBUG_IL_TO_NATIVE_MAP</span></span>  
  
 <span data-ttu-id="ab196-125">COR_IL_MAP</span><span class="sxs-lookup"><span data-stu-id="ab196-125">COR_IL_MAP</span></span>  
  
 [<span data-ttu-id="ab196-126">Profil Oluşturmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ab196-126">Profiling Overview</span></span>](profiling-overview.md)  
  
 [<span data-ttu-id="ab196-127">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ab196-127">Profiling Interfaces</span></span>](profiling-interfaces.md)  
  
 [<span data-ttu-id="ab196-128">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="ab196-128">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)  
  
 [<span data-ttu-id="ab196-129">Profil Oluşturma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="ab196-129">Profiling Enumerations</span></span>](profiling-enumerations.md)
