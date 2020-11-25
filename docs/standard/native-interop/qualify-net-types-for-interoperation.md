---
title: COM birlikte çalışma için .NET türlerini nitelendirme
description: Bu makalede, bir .NET derlemesindeki türleri COM birlikte çalışabilirliğine yönelik COM uygulamalarına açığa çıkarmak için yönergeler sağlanmaktadır.
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET components to COM
- COM interop, qualifying .NET types
- qualifying .NET types for interoperation
- interoperation with unmanaged code, qualifying .NET types
- interoperation with unmanaged code, exposing .NET components
- COM interop, exposing COM components
ms.assetid: 4b8afb52-fb8d-4e65-b47c-fd82956a3cdd
ms.openlocfilehash: 3f5fe0f168e0e520ce1985faf5a8228c1bfbdf20
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734315"
---
# <a name="qualifying-net-types-for-com-interoperation"></a><span data-ttu-id="9f8c9-103">COM birlikte çalışma için .NET türlerini nitelendirme</span><span class="sxs-lookup"><span data-stu-id="9f8c9-103">Qualifying .NET Types for COM Interoperation</span></span>

<span data-ttu-id="9f8c9-104">Türleri bir derlemede COM uygulamalarına sunmak istiyorsanız, tasarım zamanında COM birlikte çalışma gereksinimlerini göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="9f8c9-104">If you intend to expose types in an assembly to COM applications, consider the requirements of COM interop at design time.</span></span> <span data-ttu-id="9f8c9-105">Yönetilen türler (sınıf, arabirim, yapı ve numaralandırma) aşağıdaki yönergelere uydığınızda COM türleriyle sorunsuz bir şekilde tümleşir:</span><span class="sxs-lookup"><span data-stu-id="9f8c9-105">Managed types (class, interface, structure, and enumeration) seamlessly integrate with COM types when you adhere to the following guidelines:</span></span>  
  
- <span data-ttu-id="9f8c9-106">Sınıfların arabirimleri açıkça uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9f8c9-106">Classes should implement interfaces explicitly.</span></span>  
  
     <span data-ttu-id="9f8c9-107">COM birlikte çalışabilirliği, sınıfın tüm üyelerini ve temel sınıfının üyelerini içeren bir arabirimi otomatik olarak oluşturmak için bir mekanizma sağlar, ancak açık arabirimler sağlamak çok daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="9f8c9-107">Although COM interop provides a mechanism to automatically generate an interface containing all members of the class and the members of its base class, it is far better to provide explicit interfaces.</span></span> <span data-ttu-id="9f8c9-108">Otomatik olarak oluşturulan arabirime sınıf arabirimi denir.</span><span class="sxs-lookup"><span data-stu-id="9f8c9-108">The automatically generated interface is called the class interface.</span></span> <span data-ttu-id="9f8c9-109">Yönergeler için bkz. [sınıf arabirimine giriş](com-callable-wrapper.md#introducing-the-class-interface).</span><span class="sxs-lookup"><span data-stu-id="9f8c9-109">For guidelines, see [Introducing the class interface](com-callable-wrapper.md#introducing-the-class-interface).</span></span>  
  
     <span data-ttu-id="9f8c9-110">Visual Basic, C# ve C++ ' ı, arabirim tanımı dili (IDL) veya eşdeğerini kullanmak yerine kodunuzda arabirim tanımlarını eklemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f8c9-110">You can use Visual Basic, C#, and C++ to incorporate interface definitions in your code, instead of having to use Interface Definition Language (IDL) or its equivalent.</span></span> <span data-ttu-id="9f8c9-111">Sözdizimi ayrıntıları için dil belgelerinize bakın.</span><span class="sxs-lookup"><span data-stu-id="9f8c9-111">For syntax details, see your language documentation.</span></span>  
  
- <span data-ttu-id="9f8c9-112">Yönetilen türler ortak olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9f8c9-112">Managed types must be public.</span></span>  
  
     <span data-ttu-id="9f8c9-113">Yalnızca bir derlemedeki ortak türler kaydedilir ve tür kitaplığına verilir.</span><span class="sxs-lookup"><span data-stu-id="9f8c9-113">Only public types in an assembly are registered and exported to the type library.</span></span> <span data-ttu-id="9f8c9-114">Sonuç olarak, yalnızca ortak türler COM tarafından görülebilir.</span><span class="sxs-lookup"><span data-stu-id="9f8c9-114">As a result, only public types are visible to COM.</span></span>  
  
     <span data-ttu-id="9f8c9-115">Yönetilen türler, COM 'a sunulmayan diğer yönetilen koda özellikler sunar.</span><span class="sxs-lookup"><span data-stu-id="9f8c9-115">Managed types expose features to other managed code that might not be exposed to COM.</span></span> <span data-ttu-id="9f8c9-116">Örneğin, parametreli oluşturucular, statik yöntemler ve sabit alanlar COM istemcilerine gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="9f8c9-116">For instance, parameterized constructors, static methods, and constant fields are not exposed to COM clients.</span></span> <span data-ttu-id="9f8c9-117">Diğer bir deyişle, çalışma zamanı bir tür içinde ve dışında veri sıraladığında, veriler kopyalanabilir veya dönüştürülebilirler.</span><span class="sxs-lookup"><span data-stu-id="9f8c9-117">Further, as the runtime marshals data in and out of a type, the data might be copied or transformed.</span></span>  
  
- <span data-ttu-id="9f8c9-118">Yöntemler, özellikler, alanlar ve olaylar ortak olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9f8c9-118">Methods, properties, fields, and events must be public.</span></span>  
  
     <span data-ttu-id="9f8c9-119">Ortak türlerin üyeleri COM 'a görünür olmaları durumunda da genel olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9f8c9-119">Members of public types must also be public if they are to be visible to COM.</span></span> <span data-ttu-id="9f8c9-120">Bir derlemenin görünürlüğünü, ortak bir türü veya genel bir türün genel üyelerini ' a uygulayarak kısıtlayabilirsiniz <xref:System.Runtime.InteropServices.ComVisibleAttribute> .</span><span class="sxs-lookup"><span data-stu-id="9f8c9-120">You can restrict the visibility of an assembly, a public type, or public members of a public type by applying the <xref:System.Runtime.InteropServices.ComVisibleAttribute>.</span></span> <span data-ttu-id="9f8c9-121">Varsayılan olarak, tüm genel türler ve Üyeler görünür durumdadır.</span><span class="sxs-lookup"><span data-stu-id="9f8c9-121">By default, all public types and members are visible.</span></span>  
  
- <span data-ttu-id="9f8c9-122">Türler COM 'dan etkinleştirilecek Ortak parametresiz bir oluşturucuya sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9f8c9-122">Types must have a public parameterless constructor to be activated from COM.</span></span>  
  
     <span data-ttu-id="9f8c9-123">Yönetilen, ortak türler COM tarafından görülebilir.</span><span class="sxs-lookup"><span data-stu-id="9f8c9-123">Managed, public types are visible to COM.</span></span> <span data-ttu-id="9f8c9-124">Ancak, Ortak parametresiz bir Oluşturucu (bağımsız değişken içermeyen bir Oluşturucu) olmadan, COM istemcileri türü oluşturamaz.</span><span class="sxs-lookup"><span data-stu-id="9f8c9-124">However, without a public parameterless constructor (a constructor with no arguments), COM clients cannot create the type.</span></span> <span data-ttu-id="9f8c9-125">COM istemcileri, başka bir yöntemle etkinleştirildiyse türü kullanmaya devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="9f8c9-125">COM clients can still use the type if it is activated by some other means.</span></span>  
  
- <span data-ttu-id="9f8c9-126">Türler özet olamaz.</span><span class="sxs-lookup"><span data-stu-id="9f8c9-126">Types cannot be abstract.</span></span>  
  
     <span data-ttu-id="9f8c9-127">Ne COM istemcisi ne de .NET istemcisi soyut türler oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="9f8c9-127">Neither COM clients nor .NET clients can create abstract types.</span></span>  
  
 <span data-ttu-id="9f8c9-128">COM 'a aktarıldığında, yönetilen bir türün devralma hiyerarşisi düzleştirilir.</span><span class="sxs-lookup"><span data-stu-id="9f8c9-128">When exported to COM, the inheritance hierarchy of a managed type is flattened.</span></span> <span data-ttu-id="9f8c9-129">Sürüm oluşturma yönetilen ve yönetilmeyen ortamlar arasında da farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="9f8c9-129">Versioning also differs between managed and unmanaged environments.</span></span> <span data-ttu-id="9f8c9-130">COM 'a sunulan türler, diğer yönetilen türlerle aynı sürüm oluşturma özelliklerine sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="9f8c9-130">Types exposed to COM do not have the same versioning characteristics as other managed types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f8c9-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f8c9-131">See also</span></span>

- <xref:System.Runtime.InteropServices.ComVisibleAttribute>
- [<span data-ttu-id="9f8c9-132">.NET Framework Bileşenlerini COM'da Gösterme</span><span class="sxs-lookup"><span data-stu-id="9f8c9-132">Exposing .NET Framework Components to COM</span></span>](../../framework/interop/exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="9f8c9-133">Sınıf arabirimine giriş</span><span class="sxs-lookup"><span data-stu-id="9f8c9-133">Introducing the class interface</span></span>](com-callable-wrapper.md#introducing-the-class-interface)
- [<span data-ttu-id="9f8c9-134">Birlikte Çalışma Özniteliklerini Uygulama</span><span class="sxs-lookup"><span data-stu-id="9f8c9-134">Applying Interop Attributes</span></span>](apply-interop-attributes.md)
- [<span data-ttu-id="9f8c9-135">COM için bir .NET Framework derlemesi paketleme</span><span class="sxs-lookup"><span data-stu-id="9f8c9-135">Packaging a .NET Framework Assembly for COM</span></span>](../../framework/interop/packaging-an-assembly-for-com.md)
