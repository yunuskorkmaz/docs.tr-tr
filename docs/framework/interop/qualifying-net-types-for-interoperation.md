---
title: Birlikte Çalışma için Niteleyici .NET Türleri
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- COM interop, qualifying .NET types
- qualifying .NET types for interoperation
- interoperation with unmanaged code, qualifying .NET types
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: 4b8afb52-fb8d-4e65-b47c-fd82956a3cdd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8b2e14a7508d4a5e8069a3b98dee38a0ac62750c
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363988"
---
# <a name="qualifying-net-types-for-interoperation"></a><span data-ttu-id="a6901-102">Birlikte Çalışma için Niteleyici .NET Türleri</span><span class="sxs-lookup"><span data-stu-id="a6901-102">Qualifying .NET Types for Interoperation</span></span>
<span data-ttu-id="a6901-103">Türleri bir derlemede COM uygulamalarına sunmak istiyorsanız, tasarım zamanında COM birlikte çalışma gereksinimlerini göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="a6901-103">If you intend to expose types in an assembly to COM applications, consider the requirements of COM interop at design time.</span></span> <span data-ttu-id="a6901-104">Yönetilen türler (sınıf, arabirim, yapı ve numaralandırma) aşağıdaki yönergelere uydığınızda COM türleriyle sorunsuz bir şekilde tümleşir:</span><span class="sxs-lookup"><span data-stu-id="a6901-104">Managed types (class, interface, structure, and enumeration) seamlessly integrate with COM types when you adhere to the following guidelines:</span></span>  
  
- <span data-ttu-id="a6901-105">Sınıfların arabirimleri açıkça uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a6901-105">Classes should implement interfaces explicitly.</span></span>  
  
     <span data-ttu-id="a6901-106">COM birlikte çalışabilirliği, sınıfın tüm üyelerini ve temel sınıfının üyelerini içeren bir arabirimi otomatik olarak oluşturmak için bir mekanizma sağlar, ancak açık arabirimler sağlamak çok daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="a6901-106">Although COM interop provides a mechanism to automatically generate an interface containing all members of the class and the members of its base class, it is far better to provide explicit interfaces.</span></span> <span data-ttu-id="a6901-107">Otomatik olarak oluşturulan arabirime sınıf arabirimi denir.</span><span class="sxs-lookup"><span data-stu-id="a6901-107">The automatically generated interface is called the class interface.</span></span> <span data-ttu-id="a6901-108">Yönergeler için bkz. [sınıf arabirimine giriş](com-callable-wrapper.md#introducing-the-class-interface).</span><span class="sxs-lookup"><span data-stu-id="a6901-108">For guidelines, see [Introducing the class interface](com-callable-wrapper.md#introducing-the-class-interface).</span></span>  
  
     <span data-ttu-id="a6901-109">Visual Basic, C#ve C++ ' yi kullanarak, kodunuzda ARABIRIM tanımlarını ekleyebilirsiniz (IDL) veya eşdeğerini kullanmak yerine.</span><span class="sxs-lookup"><span data-stu-id="a6901-109">You can use Visual Basic, C#, and C++ to incorporate interface definitions in your code, instead of having to use Interface Definition Language (IDL) or its equivalent.</span></span> <span data-ttu-id="a6901-110">Sözdizimi ayrıntıları için dil belgelerinize bakın.</span><span class="sxs-lookup"><span data-stu-id="a6901-110">For syntax details, see your language documentation.</span></span>  
  
- <span data-ttu-id="a6901-111">Yönetilen türler ortak olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a6901-111">Managed types must be public.</span></span>  
  
     <span data-ttu-id="a6901-112">Yalnızca bir derlemedeki ortak türler kaydedilir ve tür kitaplığına verilir.</span><span class="sxs-lookup"><span data-stu-id="a6901-112">Only public types in an assembly are registered and exported to the type library.</span></span> <span data-ttu-id="a6901-113">Sonuç olarak, yalnızca ortak türler COM tarafından görülebilir.</span><span class="sxs-lookup"><span data-stu-id="a6901-113">As a result, only public types are visible to COM.</span></span>  
  
     <span data-ttu-id="a6901-114">Yönetilen türler, COM 'a sunulmayan diğer yönetilen koda özellikler sunar.</span><span class="sxs-lookup"><span data-stu-id="a6901-114">Managed types expose features to other managed code that might not be exposed to COM.</span></span> <span data-ttu-id="a6901-115">Örneğin, parametreli oluşturucular, statik yöntemler ve sabit alanlar COM istemcilerine gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="a6901-115">For instance, parameterized constructors, static methods, and constant fields are not exposed to COM clients.</span></span> <span data-ttu-id="a6901-116">Diğer bir deyişle, çalışma zamanı bir tür içinde ve dışında veri sıraladığında, veriler kopyalanabilir veya dönüştürülebilirler.</span><span class="sxs-lookup"><span data-stu-id="a6901-116">Further, as the runtime marshals data in and out of a type, the data might be copied or transformed.</span></span>  
  
- <span data-ttu-id="a6901-117">Yöntemler, özellikler, alanlar ve olaylar ortak olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a6901-117">Methods, properties, fields, and events must be public.</span></span>  
  
     <span data-ttu-id="a6901-118">Ortak türlerin üyeleri COM 'a görünür olmaları durumunda da genel olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a6901-118">Members of public types must also be public if they are to be visible to COM.</span></span> <span data-ttu-id="a6901-119">Bir derlemenin görünürlüğünü, ortak bir türü veya genel bir türün genel üyelerini ' a uygulayarak <xref:System.Runtime.InteropServices.ComVisibleAttribute>kısıtlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a6901-119">You can restrict the visibility of an assembly, a public type, or public members of a public type by applying the <xref:System.Runtime.InteropServices.ComVisibleAttribute>.</span></span> <span data-ttu-id="a6901-120">Varsayılan olarak, tüm genel türler ve Üyeler görünür durumdadır.</span><span class="sxs-lookup"><span data-stu-id="a6901-120">By default, all public types and members are visible.</span></span>  
  
- <span data-ttu-id="a6901-121">Türler COM 'dan etkinleştirilecek Ortak parametresiz bir oluşturucuya sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a6901-121">Types must have a public parameterless constructor to be activated from COM.</span></span>  
  
     <span data-ttu-id="a6901-122">Yönetilen, ortak türler COM tarafından görülebilir.</span><span class="sxs-lookup"><span data-stu-id="a6901-122">Managed, public types are visible to COM.</span></span> <span data-ttu-id="a6901-123">Ancak, Ortak parametresiz bir Oluşturucu (bağımsız değişken içermeyen bir Oluşturucu) olmadan, COM istemcileri türü oluşturamaz.</span><span class="sxs-lookup"><span data-stu-id="a6901-123">However, without a public parameterless constructor (a constructor with no arguments), COM clients cannot create the type.</span></span> <span data-ttu-id="a6901-124">COM istemcileri, başka bir yöntemle etkinleştirildiyse türü kullanmaya devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="a6901-124">COM clients can still use the type if it is activated by some other means.</span></span>  
  
- <span data-ttu-id="a6901-125">Türler özet olamaz.</span><span class="sxs-lookup"><span data-stu-id="a6901-125">Types cannot be abstract.</span></span>  
  
     <span data-ttu-id="a6901-126">Ne COM istemcisi ne de .NET istemcisi soyut türler oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="a6901-126">Neither COM clients nor .NET clients can create abstract types.</span></span>  
  
 <span data-ttu-id="a6901-127">COM 'a aktarıldığında, yönetilen bir türün devralma hiyerarşisi düzleştirilir.</span><span class="sxs-lookup"><span data-stu-id="a6901-127">When exported to COM, the inheritance hierarchy of a managed type is flattened.</span></span> <span data-ttu-id="a6901-128">Sürüm oluşturma yönetilen ve yönetilmeyen ortamlar arasında da farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="a6901-128">Versioning also differs between managed and unmanaged environments.</span></span> <span data-ttu-id="a6901-129">COM 'a sunulan türler, diğer yönetilen türlerle aynı sürüm oluşturma özelliklerine sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="a6901-129">Types exposed to COM do not have the same versioning characteristics as other managed types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6901-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6901-130">See also</span></span>

- <xref:System.Runtime.InteropServices.ComVisibleAttribute>
- [<span data-ttu-id="a6901-131">.NET Framework Bileşenlerini COM'da Gösterme</span><span class="sxs-lookup"><span data-stu-id="a6901-131">Exposing .NET Framework Components to COM</span></span>](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="a6901-132">Sınıf arabirimine giriş</span><span class="sxs-lookup"><span data-stu-id="a6901-132">Introducing the class interface</span></span>](com-callable-wrapper.md#introducing-the-class-interface)
- [<span data-ttu-id="a6901-133">Birlikte Çalışma Özniteliklerini Uygulama</span><span class="sxs-lookup"><span data-stu-id="a6901-133">Applying Interop Attributes</span></span>](../../../docs/framework/interop/applying-interop-attributes.md)
- [<span data-ttu-id="a6901-134">COM için Bütünleştirilmiş Kod Paketleme</span><span class="sxs-lookup"><span data-stu-id="a6901-134">Packaging an Assembly for COM</span></span>](../../../docs/framework/interop/packaging-an-assembly-for-com.md)
