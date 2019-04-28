---
title: DLL İşlevini Çağırma
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged functions, calling
- unmanaged functions
- COM interop, platform invoke
- platform invoke, calling unmanaged functions
- interoperation with unmanaged code, platform invoke
- DLL functions
ms.assetid: 113646de-7ea0-4f0e-8df0-c46dab3e8733
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 98d363b6c0838ff1211d969391f04ce8ccddd003
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61643575"
---
# <a name="calling-a-dll-function"></a><span data-ttu-id="766f6-102">DLL İşlevini Çağırma</span><span class="sxs-lookup"><span data-stu-id="766f6-102">Calling a DLL Function</span></span>
<span data-ttu-id="766f6-103">Yönetilmeyen DLL işlevleri çağırma diğer yönetilen kod çağırmak için neredeyse aynı olsa da, karmaşık görünen DLL işlevleri yapabilirsiniz farklar vardır ilk.</span><span class="sxs-lookup"><span data-stu-id="766f6-103">Although calling unmanaged DLL functions is nearly identical to calling other managed code, there are differences that can make DLL functions seem confusing at first.</span></span> <span data-ttu-id="766f6-104">Bu bölüm, olağan dışı arama ile ilgili sorunlardan bazılarını açıklayan konulara tanıtır.</span><span class="sxs-lookup"><span data-stu-id="766f6-104">This section introduces topics that describe some of the unusual calling-related issues.</span></span>  
  
 <span data-ttu-id="766f6-105">Platformdan iade yapıları çağrıları çağırma veri türleri, yönetilen ve yönetilmeyen kod içinde aynı gösterimi sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="766f6-105">Structures that are returned from platform invoke calls must be data types that have the same representation in managed and unmanaged code.</span></span> <span data-ttu-id="766f6-106">Bu türler olarak adlandırılır *türlerse* dönüştürme gerektirmediğinden (bkz [blok halinde kopyalanabilir ve örnekteki](../../../docs/framework/interop/blittable-and-non-blittable-types.md)).</span><span class="sxs-lookup"><span data-stu-id="766f6-106">Such types are called *blittable types* because they do not require conversion (see [Blittable and Non-Blittable Types](../../../docs/framework/interop/blittable-and-non-blittable-types.md)).</span></span> <span data-ttu-id="766f6-107">Dönüş türü olarak kopyalanamaz yapısının bir işlevi çağırmak için kopyalanamaz türü olarak aynı boyutta blittable Yardımcısı tür tanımlama ve işlev döndürdükten sonra verileri dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="766f6-107">To call a function that has a non-blittable structure as its return type, you can define a blittable helper type of the same size as the non-blittable type and convert the data after the function returns.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="766f6-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="766f6-108">In This Section</span></span>  
 [<span data-ttu-id="766f6-109">Yapıları Geçirme</span><span class="sxs-lookup"><span data-stu-id="766f6-109">Passing Structures</span></span>](../../../docs/framework/interop/passing-structures.md)  
 <span data-ttu-id="766f6-110">Önceden tanımlanmış bir düzen ile veri yapıları geçirme sorunları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="766f6-110">Identifies the issues of passing data structures with a predefined layout.</span></span>  
  
 [<span data-ttu-id="766f6-111">Geri Arama İşlevleri</span><span class="sxs-lookup"><span data-stu-id="766f6-111">Callback Functions</span></span>](../../../docs/framework/interop/callback-functions.md)  
 <span data-ttu-id="766f6-112">Geri çağırma işlevleri hakkında temel bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="766f6-112">Provides basic information about callback functions.</span></span>  
  
 [<span data-ttu-id="766f6-113">Nasıl yapılır: Geri çağırma işlevlerini uygulama</span><span class="sxs-lookup"><span data-stu-id="766f6-113">How to: Implement Callback Functions</span></span>](../../../docs/framework/interop/how-to-implement-callback-functions.md)  
 <span data-ttu-id="766f6-114">Geri çağırma işlevleri yönetilen koda uygulanması açıklar.</span><span class="sxs-lookup"><span data-stu-id="766f6-114">Describes how to implement callback functions in managed code.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="766f6-115">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="766f6-115">Related Sections</span></span>  
 [<span data-ttu-id="766f6-116">Yönetilmeyen DLL İşlevlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="766f6-116">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 <span data-ttu-id="766f6-117">Yönetilmeyen çağrı açıklamaktadır platformunu kullanarak DLL işlevleri çağırma.</span><span class="sxs-lookup"><span data-stu-id="766f6-117">Describes how to call unmanaged DLL functions using platform invoke.</span></span>  
  
 [<span data-ttu-id="766f6-118">Platform Çağırma ile Veri Hazırlama</span><span class="sxs-lookup"><span data-stu-id="766f6-118">Marshaling Data with Platform Invoke</span></span>](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)  
 <span data-ttu-id="766f6-119">Yöntem parametreleri bildirmek ve yönetilmeyen kitaplıkları tarafından dışarı aktarılan işlevler için bağımsız değişkenler geçirmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="766f6-119">Describes how to declare method parameters and pass arguments to functions exported by unmanaged libraries.</span></span>
