---
title: "DLL İşlevini Çağırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unmanaged functions, calling
- unmanaged functions
- COM interop, platform invoke
- platform invoke, calling unmanaged functions
- interoperation with unmanaged code, platform invoke
- DLL functions
ms.assetid: 113646de-7ea0-4f0e-8df0-c46dab3e8733
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8755173b9c64a6457b94e689204c6a5aabc971cc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="calling-a-dll-function"></a><span data-ttu-id="7ab08-102">DLL İşlevini Çağırma</span><span class="sxs-lookup"><span data-stu-id="7ab08-102">Calling a DLL Function</span></span>
<span data-ttu-id="7ab08-103">Yönetilmeyen DLL işlevleri çağırma diğer yönetilen kodu çağırma için neredeyse aynı olsa da, DLL işlevleri kafa karıştırıcı göründüğü yapabilirsiniz farklar vardır ilk.</span><span class="sxs-lookup"><span data-stu-id="7ab08-103">Although calling unmanaged DLL functions is nearly identical to calling other managed code, there are differences that can make DLL functions seem confusing at first.</span></span> <span data-ttu-id="7ab08-104">Bu bölümde bazı olağan dışı arama ile ilgili sorunları açıklayan konulara tanıtır.</span><span class="sxs-lookup"><span data-stu-id="7ab08-104">This section introduces topics that describe some of the unusual calling-related issues.</span></span>  
  
 <span data-ttu-id="7ab08-105">Platformundan döndürülen yapıları çağırma çağrıları aynı gösterimi yönetilen ve yönetilmeyen kodunda varsa veri türleri olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7ab08-105">Structures that are returned from platform invoke calls must be data types that have the same representation in managed and unmanaged code.</span></span> <span data-ttu-id="7ab08-106">Bu tür türleri olarak adlandırılır *blittable türleri* dönüştürme gerektirmediği için (bkz [blok halinde kopyalanabilir ve olmayan Blittable türleri](../../../docs/framework/interop/blittable-and-non-blittable-types.md)).</span><span class="sxs-lookup"><span data-stu-id="7ab08-106">Such types are called *blittable types* because they do not require conversion (see [Blittable and Non-Blittable Types](../../../docs/framework/interop/blittable-and-non-blittable-types.md)).</span></span> <span data-ttu-id="7ab08-107">Dönüş türü olarak blittable olmayan yapısının bir işlevi çağırmak için aynı boyutta blittable Yardımcısı tür blittable olmayan türü olarak tanımlama ve işlev döndükten sonra verileri dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="7ab08-107">To call a function that has a non-blittable structure as its return type, you can define a blittable helper type of the same size as the non-blittable type and convert the data after the function returns.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7ab08-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="7ab08-108">In This Section</span></span>  
 [<span data-ttu-id="7ab08-109">Yapıları Geçirme</span><span class="sxs-lookup"><span data-stu-id="7ab08-109">Passing Structures</span></span>](../../../docs/framework/interop/passing-structures.md)  
 <span data-ttu-id="7ab08-110">Önceden tanımlanmış bir düzende veri yapıları geçirme sorunlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7ab08-110">Identifies the issues of passing data structures with a predefined layout.</span></span>  
  
 [<span data-ttu-id="7ab08-111">Geri Arama İşlevleri</span><span class="sxs-lookup"><span data-stu-id="7ab08-111">Callback Functions</span></span>](../../../docs/framework/interop/callback-functions.md)  
 <span data-ttu-id="7ab08-112">Geri arama işlevleri ile ilgili temel bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="7ab08-112">Provides basic information about callback functions.</span></span>  
  
 [<span data-ttu-id="7ab08-113">Nasıl yapılır: Geri Çağırma İşlevlerini Uygulama</span><span class="sxs-lookup"><span data-stu-id="7ab08-113">How to: Implement Callback Functions</span></span>](../../../docs/framework/interop/how-to-implement-callback-functions.md)  
 <span data-ttu-id="7ab08-114">Yönetilen kodda geri çağırma işlevlerini gerçekleştirmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="7ab08-114">Describes how to implement callback functions in managed code.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7ab08-115">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="7ab08-115">Related Sections</span></span>  
 [<span data-ttu-id="7ab08-116">Yönetilmeyen DLL İşlevlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="7ab08-116">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 <span data-ttu-id="7ab08-117">Yönetilmeyen çağrılacağını açıklar platformu kullanılarak DLL işlevleri çağırma.</span><span class="sxs-lookup"><span data-stu-id="7ab08-117">Describes how to call unmanaged DLL functions using platform invoke.</span></span>  
  
 [<span data-ttu-id="7ab08-118">Platform Çağırma ile Veri Hazırlama</span><span class="sxs-lookup"><span data-stu-id="7ab08-118">Marshaling Data with Platform Invoke</span></span>](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)  
 <span data-ttu-id="7ab08-119">Yöntem parametreleri bildirme ve yönetilmeyen kitaplıkları tarafından dışarı aktarılan işlevler için bağımsız değişkenler geçirmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="7ab08-119">Describes how to declare method parameters and pass arguments to functions exported by unmanaged libraries.</span></span>
