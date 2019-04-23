---
title: DLL İşlevleri için bir Sınıf Oluşturma
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 399ad6649016e53d91d5d9d30ecc031ae8a97a4a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59149363"
---
# <a name="creating-a-class-to-hold-dll-functions"></a><span data-ttu-id="aae1e-102">DLL İşlevleri için bir Sınıf Oluşturma</span><span class="sxs-lookup"><span data-stu-id="aae1e-102">Creating a Class to Hold DLL Functions</span></span>
<span data-ttu-id="aae1e-103">Sık kullanılan bir DLL işlevinin yönetilen sınıfta sarmalama platform işlevi kapsülleyen etkili bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="aae1e-103">Wrapping a frequently used DLL function in a managed class is an effective approach to encapsulate platform functionality.</span></span> <span data-ttu-id="aae1e-104">Her durumda bunu yapmak için zorunlu olmasa da, sınıf sarmalayıcı DLL işlevlerini tanımlama kullanışlı çünkü sağlamak hantal ve hataya eğilimli olabilir.</span><span class="sxs-lookup"><span data-stu-id="aae1e-104">Although it is not mandatory to do so in every case, providing a class wrapper is convenient because defining DLL functions can be cumbersome and error-prone.</span></span> <span data-ttu-id="aae1e-105">Visual Basic'te programlama yapıyorsanız veya C#, DLL işlevleri bir sınıf veya Visual Basic module'u içinde bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="aae1e-105">If you are programming in Visual Basic or C#, you must declare DLL functions within a class or Visual Basic module.</span></span>  
  
 <span data-ttu-id="aae1e-106">Bir sınıf içinde aramak istediğiniz her DLL işlevi için statik bir yöntem tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="aae1e-106">Within a class, you define a static method for each DLL function you want to call.</span></span> <span data-ttu-id="aae1e-107">Tanımı karakter kümesi veya çağırma yöntemi bağımsız değişkenleri geçirme içinde kullanılan gibi ek bilgiler içerebilir. Bu bilgiler gt;(yok) varsayılan ayarları seçin.</span><span class="sxs-lookup"><span data-stu-id="aae1e-107">The definition can include additional information, such as the character set or the calling convention used in passing method arguments; by omitting this information, you select the default settings.</span></span> <span data-ttu-id="aae1e-108">Bildirim seçenekleri ve varsayılan ayarlarının tam listesi için bkz: [yönetilen kodda prototipler oluşturma](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).</span><span class="sxs-lookup"><span data-stu-id="aae1e-108">For a complete list of declaration options and their default settings, see [Creating Prototypes in Managed Code](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).</span></span>  
  
 <span data-ttu-id="aae1e-109">Üzerinde başka bir sınıfın statik yöntemleri çağırmak olarak sarmalanmış sonra sınıf üzerinde yöntemleri çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="aae1e-109">Once wrapped, you can call the methods on the class as you call static methods on any other class.</span></span> <span data-ttu-id="aae1e-110">Platform çağırma tanıtıcıları işlevi otomatik olarak verilen temel.</span><span class="sxs-lookup"><span data-stu-id="aae1e-110">Platform invoke handles the underlying exported function automatically.</span></span>  
  
 <span data-ttu-id="aae1e-111">Platform için yönetilen sınıf tasarlama çağırdığınızda, sınıflar ve DLL işlevleri arasındaki ilişkileri göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="aae1e-111">When designing a managed class for platform invoke, consider the relationships between classes and DLL functions.</span></span> <span data-ttu-id="aae1e-112">Örneğin, şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="aae1e-112">For example, you can:</span></span>  
  
-   <span data-ttu-id="aae1e-113">Varolan bir sınıf içinde DLL işlevleri bildirme.</span><span class="sxs-lookup"><span data-stu-id="aae1e-113">Declare DLL functions within an existing class.</span></span>  
  
-   <span data-ttu-id="aae1e-114">Yalıtılmış ve kolay bulmak işlevleri tutmak, her bir DLL işlevi için ayrı bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="aae1e-114">Create an individual class for each DLL function, keeping functions isolated and easy to find.</span></span>  
  
-   <span data-ttu-id="aae1e-115">Bir dizi mantıksal gruplandırmaları form ve ek yükü azaltmak için ilgili DLL işlevleri için bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="aae1e-115">Create one class for a set of related DLL functions to form logical groupings and reduce overhead.</span></span>  
  
 <span data-ttu-id="aae1e-116">Lütfen sınıfı ve metotlarını şekilde adlandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aae1e-116">You can name the class and its methods as you please.</span></span> <span data-ttu-id="aae1e-117">Nasıl oluşturulacağını gösteren örnekler için. NET tabanlı bildirimler platformuyla kullanılacak çağırmak için bkz: [Platform Çağırma ile veri hazırlama](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="aae1e-117">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aae1e-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aae1e-118">See also</span></span>

- [<span data-ttu-id="aae1e-119">Yönetilmeyen DLL İşlevlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="aae1e-119">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)
- [<span data-ttu-id="aae1e-120">DLL'lerde İşlevleri Tanımlama</span><span class="sxs-lookup"><span data-stu-id="aae1e-120">Identifying Functions in DLLs</span></span>](../../../docs/framework/interop/identifying-functions-in-dlls.md)
- [<span data-ttu-id="aae1e-121">Yönetilen Kodda Prototipler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="aae1e-121">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="aae1e-122">DLL İşlevini Çağırma</span><span class="sxs-lookup"><span data-stu-id="aae1e-122">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)
