---
title: DLL İşlevini Çağırma
description: Kafa karıştırıcı görünebilir bir DLL işlevini çağırma hakkındaki sorunları gözden geçirin. İşlem çağırma işlevi, dönüş türünün blittable olduğuna göre değişir.
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged functions, calling
- unmanaged functions
- COM interop, platform invoke
- platform invoke, calling unmanaged functions
- interoperation with unmanaged code, platform invoke
- DLL functions
ms.assetid: 113646de-7ea0-4f0e-8df0-c46dab3e8733
ms.openlocfilehash: 90f8f47148e652a9942a35be1564bed94c155216
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620904"
---
# <a name="calling-a-dll-function"></a><span data-ttu-id="6cd1e-104">DLL İşlevini Çağırma</span><span class="sxs-lookup"><span data-stu-id="6cd1e-104">Calling a DLL Function</span></span>
<span data-ttu-id="6cd1e-105">Yönetilmeyen DLL işlevlerinin çağrılması, diğer yönetilen kodu çağırmaya neredeyse özdeş olsa da, ilk olarak DLL işlevlerinin kafa karıştırıcı görünmesine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="6cd1e-105">Although calling unmanaged DLL functions is nearly identical to calling other managed code, there are differences that can make DLL functions seem confusing at first.</span></span> <span data-ttu-id="6cd1e-106">Bu bölümde, bazı olağan dışı arama ile ilgili sorunlardan bazıları açıklanır.</span><span class="sxs-lookup"><span data-stu-id="6cd1e-106">This section introduces topics that describe some of the unusual calling-related issues.</span></span>  
  
 <span data-ttu-id="6cd1e-107">Platform çağırma çağrılarının döndürdüğü yapıların, yönetilen ve yönetilmeyen koddaki aynı gösterimine sahip veri türleri olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6cd1e-107">Structures that are returned from platform invoke calls must be data types that have the same representation in managed and unmanaged code.</span></span> <span data-ttu-id="6cd1e-108">Bu tür türler, dönüşüm gerektirmediğinden *blittable türler* olarak adlandırılır (bkz. [blittable ve blittable olmayan türler](blittable-and-non-blittable-types.md)).</span><span class="sxs-lookup"><span data-stu-id="6cd1e-108">Such types are called *blittable types* because they do not require conversion (see [Blittable and Non-Blittable Types](blittable-and-non-blittable-types.md)).</span></span> <span data-ttu-id="6cd1e-109">Dönüş türü olarak blittable olmayan bir yapıya sahip bir işlevi çağırmak için, blittable olmayan türle aynı büyüklükte bir blittable yardımcı türü tanımlayabilir ve işlevin döndürdüğü sonra verileri dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6cd1e-109">To call a function that has a non-blittable structure as its return type, you can define a blittable helper type of the same size as the non-blittable type and convert the data after the function returns.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6cd1e-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="6cd1e-110">In This Section</span></span>  
 [<span data-ttu-id="6cd1e-111">Yapıları Geçirme</span><span class="sxs-lookup"><span data-stu-id="6cd1e-111">Passing Structures</span></span>](passing-structures.md)  
 <span data-ttu-id="6cd1e-112">Önceden tanımlanmış bir düzen ile veri yapıları geçirme sorunlarını belirler.</span><span class="sxs-lookup"><span data-stu-id="6cd1e-112">Identifies the issues of passing data structures with a predefined layout.</span></span>  
  
 [<span data-ttu-id="6cd1e-113">Geri Çağırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="6cd1e-113">Callback Functions</span></span>](callback-functions.md)  
 <span data-ttu-id="6cd1e-114">Geri çağırma işlevleriyle ilgili temel bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="6cd1e-114">Provides basic information about callback functions.</span></span>  
  
 [<span data-ttu-id="6cd1e-115">Nasıl yapılır: Geri Çağırma İşlevlerini Uygulama</span><span class="sxs-lookup"><span data-stu-id="6cd1e-115">How to: Implement Callback Functions</span></span>](how-to-implement-callback-functions.md)  
 <span data-ttu-id="6cd1e-116">Yönetilen kodda geri çağırma işlevlerinin nasıl uygulanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="6cd1e-116">Describes how to implement callback functions in managed code.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6cd1e-117">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="6cd1e-117">Related Sections</span></span>  
 [<span data-ttu-id="6cd1e-118">Yönetilmeyen DLL İşlevlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="6cd1e-118">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)  
 <span data-ttu-id="6cd1e-119">Platform Invoke kullanılarak yönetilmeyen DLL işlevlerinin nasıl çağrılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="6cd1e-119">Describes how to call unmanaged DLL functions using platform invoke.</span></span>  
  
 [<span data-ttu-id="6cd1e-120">Platform Çağırma ile Veri Sıralama</span><span class="sxs-lookup"><span data-stu-id="6cd1e-120">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)  
 <span data-ttu-id="6cd1e-121">Yöntem parametrelerinin nasıl bildirilemeyeceğini ve yönetilmeyen kitaplıklar tarafından dışarıya alınan işlevlere bağımsız değişkenlerin nasıl geçirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="6cd1e-121">Describes how to declare method parameters and pass arguments to functions exported by unmanaged libraries.</span></span>
