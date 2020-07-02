---
title: DLL İşlevleri için bir Sınıf Oluşturma
description: .NET ' te platform işlevlerinin kapsüllemeye yardımcı olan DLL işlevlerini barındırmak için yönetilen bir sınıf sarmalayıcı oluşturun.
ms.date: 03/30/2017
helpviewer_keywords:
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke, creating class for functions
- DLL functions
ms.assetid: e08e4c34-0223-45f7-aa55-a3d8dd979b0f
ms.openlocfilehash: b8aa0361ee5213cb947a102f903d1a7a35331f17
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622178"
---
# <a name="creating-a-class-to-hold-dll-functions"></a><span data-ttu-id="9d739-103">DLL İşlevleri için bir Sınıf Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9d739-103">Creating a Class to Hold DLL Functions</span></span>
<span data-ttu-id="9d739-104">Yönetilen bir sınıfta sık kullanılan bir DLL işlevinin sarmalanması, platform işlevlerini kapsüllemek için etkili bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="9d739-104">Wrapping a frequently used DLL function in a managed class is an effective approach to encapsulate platform functionality.</span></span> <span data-ttu-id="9d739-105">Her durumda bunu yapmak zorunlu olmasa da, DLL işlevlerinin tanımlanması çok fazla ve hataya açık olabileceğinden sınıf sarmalayıcı sağlanması kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="9d739-105">Although it is not mandatory to do so in every case, providing a class wrapper is convenient because defining DLL functions can be cumbersome and error-prone.</span></span> <span data-ttu-id="9d739-106">Visual Basic veya C# ' de programlıyorsanız, DLL işlevlerini bir sınıf veya Visual Basic modülü içinde bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9d739-106">If you are programming in Visual Basic or C#, you must declare DLL functions within a class or Visual Basic module.</span></span>  
  
 <span data-ttu-id="9d739-107">Bir sınıf içinde, çağırmak istediğiniz her DLL işlevi için bir statik yöntem tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="9d739-107">Within a class, you define a static method for each DLL function you want to call.</span></span> <span data-ttu-id="9d739-108">Tanım, yöntem bağımsız değişkenlerinde kullanılan karakter kümesi veya çağırma kuralı gibi ek bilgileri içerebilir; Bu bilgileri atlayarak varsayılan ayarları seçersiniz.</span><span class="sxs-lookup"><span data-stu-id="9d739-108">The definition can include additional information, such as the character set or the calling convention used in passing method arguments; by omitting this information, you select the default settings.</span></span> <span data-ttu-id="9d739-109">Bildirim seçeneklerinin ve varsayılan ayarlarının tüm listesi için bkz. [yönetilen kodda prototipler oluşturma](creating-prototypes-in-managed-code.md).</span><span class="sxs-lookup"><span data-stu-id="9d739-109">For a complete list of declaration options and their default settings, see [Creating Prototypes in Managed Code](creating-prototypes-in-managed-code.md).</span></span>  
  
 <span data-ttu-id="9d739-110">Sarmalanan bir kez, diğer herhangi bir sınıfta statik yöntemleri çağırmış olduğunuz sınıftaki yöntemleri çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9d739-110">Once wrapped, you can call the methods on the class as you call static methods on any other class.</span></span> <span data-ttu-id="9d739-111">Platform çağırma, temel alınan içe aktarılmış işlevi otomatik olarak işler.</span><span class="sxs-lookup"><span data-stu-id="9d739-111">Platform invoke handles the underlying exported function automatically.</span></span>  
  
 <span data-ttu-id="9d739-112">Platform çağırma için yönetilen bir sınıf tasarlarken sınıflar ve DLL işlevleri arasındaki ilişkileri göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="9d739-112">When designing a managed class for platform invoke, consider the relationships between classes and DLL functions.</span></span> <span data-ttu-id="9d739-113">Örneğin, şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9d739-113">For example, you can:</span></span>  
  
- <span data-ttu-id="9d739-114">Varolan bir sınıf içinde DLL işlevleri bildirin.</span><span class="sxs-lookup"><span data-stu-id="9d739-114">Declare DLL functions within an existing class.</span></span>  
  
- <span data-ttu-id="9d739-115">Her DLL işlevi için tek bir sınıf oluşturun ve işlevleri yalıtılmış ve kolay bir şekilde bulabilir.</span><span class="sxs-lookup"><span data-stu-id="9d739-115">Create an individual class for each DLL function, keeping functions isolated and easy to find.</span></span>  
  
- <span data-ttu-id="9d739-116">Mantıksal gruplandırmaları biçimlendirmek ve ek yükü azaltmak için bir dizi ilgili DLL işlevi için bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9d739-116">Create one class for a set of related DLL functions to form logical groupings and reduce overhead.</span></span>  
  
 <span data-ttu-id="9d739-117">Sınıfı ve yöntemlerini sizin gibi adlandırın.</span><span class="sxs-lookup"><span data-stu-id="9d739-117">You can name the class and its methods as you please.</span></span> <span data-ttu-id="9d739-118">Nasıl oluşturulacağını gösteren örnekler için. Platform çağırma ile kullanılacak NET tabanlı bildirimler, bkz. [Platform çağırma Ile verileri sıralama](marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="9d739-118">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d739-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d739-119">See also</span></span>

- [<span data-ttu-id="9d739-120">Yönetilmeyen DLL İşlevlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="9d739-120">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)
- [<span data-ttu-id="9d739-121">DLL'lerde İşlevleri Tanımlama</span><span class="sxs-lookup"><span data-stu-id="9d739-121">Identifying Functions in DLLs</span></span>](identifying-functions-in-dlls.md)
- [<span data-ttu-id="9d739-122">Yönetilen Kodda Prototipler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9d739-122">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="9d739-123">DLL İşlevini Çağırma</span><span class="sxs-lookup"><span data-stu-id="9d739-123">Calling a DLL Function</span></span>](calling-a-dll-function.md)
