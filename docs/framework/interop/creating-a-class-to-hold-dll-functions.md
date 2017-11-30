---
title: "DLL İşlevleri için bir Sınıf Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke, creating class for functions
- DLL functions
ms.assetid: e08e4c34-0223-45f7-aa55-a3d8dd979b0f
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ac3c3542e46168f5903ff0425740a29f16253733
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="creating-a-class-to-hold-dll-functions"></a><span data-ttu-id="5855e-102">DLL İşlevleri için bir Sınıf Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5855e-102">Creating a Class to Hold DLL Functions</span></span>
<span data-ttu-id="5855e-103">Sık kullanılan DLL işlevini yönetilen sınıfında kaydırma platform işlevleri kapsülleyen etkili bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="5855e-103">Wrapping a frequently used DLL function in a managed class is an effective approach to encapsulate platform functionality.</span></span> <span data-ttu-id="5855e-104">Her durumda bunun için zorunlu olmasa da bir sınıf sarmalayıcı DLL işlevlerini tanımlama uygun olduğundan sağlama zahmetli ve hatalara eğilimli olabilir.</span><span class="sxs-lookup"><span data-stu-id="5855e-104">Although it is not mandatory to do so in every case, providing a class wrapper is convenient because defining DLL functions can be cumbersome and error-prone.</span></span> <span data-ttu-id="5855e-105">Visual Basic veya C# programlama yapıyorsanız sınıfta veya Visual Basic modülü DLL işlevleri bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5855e-105">If you are programming in Visual Basic or C#, you must declare DLL functions within a class or Visual Basic module.</span></span>  
  
 <span data-ttu-id="5855e-106">Bir sınıf içinde aramak istediğiniz her DLL işlevi için statik bir yöntemi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="5855e-106">Within a class, you define a static method for each DLL function you want to call.</span></span> <span data-ttu-id="5855e-107">Tanımı karakter kümesini veya yöntem bağımsız değişkenleri geçirme kullanılan çağırma gibi ek bilgileri içerebilir; Bu bilgileri kaldırarak, varsayılan ayarları seçin.</span><span class="sxs-lookup"><span data-stu-id="5855e-107">The definition can include additional information, such as the character set or the calling convention used in passing method arguments; by omitting this information, you select the default settings.</span></span> <span data-ttu-id="5855e-108">Bildirim seçenekleri ve varsayılan ayarlarına tam listesi için bkz: [yönetilen kodda prototipler oluşturma](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).</span><span class="sxs-lookup"><span data-stu-id="5855e-108">For a complete list of declaration options and their default settings, see [Creating Prototypes in Managed Code](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).</span></span>  
  
 <span data-ttu-id="5855e-109">Diğer statik işlevi üzerinde yöntemleri çağırmak gibi Sarmalanan sonra işlev yöntemleri çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="5855e-109">Once wrapped, you can call methods on the function as you call methods on any other static function.</span></span> <span data-ttu-id="5855e-110">Platform çağırma tanıtıcıları arka plandaki işlevi otomatik olarak verilmiş.</span><span class="sxs-lookup"><span data-stu-id="5855e-110">Platform invoke handles the underlying exported function automatically.</span></span>  
  
 <span data-ttu-id="5855e-111">Platform için bir yönetilen sınıf tasarlama çağırdığınızda, sınıflar ve DLL işlevleri arasındaki ilişkileri göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="5855e-111">When designing a managed class for platform invoke, consider the relationships between classes and DLL functions.</span></span> <span data-ttu-id="5855e-112">Örneğin, şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5855e-112">For example, you can:</span></span>  
  
-   <span data-ttu-id="5855e-113">Varolan bir sınıfa içinde DLL işlevleri bildirme.</span><span class="sxs-lookup"><span data-stu-id="5855e-113">Declare DLL functions within an existing class.</span></span>  
  
-   <span data-ttu-id="5855e-114">Yalıtılmış ve kolay bulmak işlevleri tutma her DLL işlevi için tek bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5855e-114">Create an individual class for each DLL function, keeping functions isolated and easy to find.</span></span>  
  
-   <span data-ttu-id="5855e-115">Mantıksal gruplar oluşturmak ve ek yükü azaltmak için ilgili DLL işlevleri kümesi için bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5855e-115">Create one class for a set of related DLL functions to form logical groupings and reduce overhead.</span></span>  
  
 <span data-ttu-id="5855e-116">Sınıf ve yöntemlerinden yazarken Lütfen adı verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5855e-116">You can name the class and its methods as you please.</span></span> <span data-ttu-id="5855e-117">Örnekler için nasıl oluşturulacağını gösterir. Platformuyla kullanılacak bildirimleri NET tabanlı çağırmak için bkz: [Platform Çağırma ile veri hazırlama](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="5855e-117">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5855e-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5855e-118">See Also</span></span>  
 [<span data-ttu-id="5855e-119">Yönetilmeyen DLL işlevlerini kullanma</span><span class="sxs-lookup"><span data-stu-id="5855e-119">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 [<span data-ttu-id="5855e-120">DLL'lerde işlevleri tanımlama</span><span class="sxs-lookup"><span data-stu-id="5855e-120">Identifying Functions in DLLs</span></span>](../../../docs/framework/interop/identifying-functions-in-dlls.md)  
 [<span data-ttu-id="5855e-121">Yönetilen kodda prototipler oluşturma</span><span class="sxs-lookup"><span data-stu-id="5855e-121">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [<span data-ttu-id="5855e-122">DLL işlevini çağırma</span><span class="sxs-lookup"><span data-stu-id="5855e-122">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)
