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
ms.openlocfilehash: a40b9524990213eaaf2ed78503b6f831776306ec
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54524318"
---
# <a name="qualifying-net-types-for-interoperation"></a><span data-ttu-id="2b346-102">Birlikte Çalışma için Niteleyici .NET Türleri</span><span class="sxs-lookup"><span data-stu-id="2b346-102">Qualifying .NET Types for Interoperation</span></span>
<span data-ttu-id="2b346-103">COM uygulamaları için bir bütünleştirilmiş kodundaki türler kullanıma sunmak istiyorsanız, tasarım zamanında COM birlikte çalışabilirlik gereksinimlerini göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="2b346-103">If you intend to expose types in an assembly to COM applications, consider the requirements of COM interop at design time.</span></span> <span data-ttu-id="2b346-104">Aşağıdaki yönergelere uyunuz, yönetilen türler (sınıfı, arabirim, yapı ve sabit listesi) COM türleri ile sorunsuz şekilde tümleştirin:</span><span class="sxs-lookup"><span data-stu-id="2b346-104">Managed types (class, interface, structure, and enumeration) seamlessly integrate with COM types when you adhere to the following guidelines:</span></span>  
  
-   <span data-ttu-id="2b346-105">Sınıfları, arabirimleri açıkça uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="2b346-105">Classes should implement interfaces explicitly.</span></span>  
  
     <span data-ttu-id="2b346-106">COM birlikte çalışma otomatik olarak bir sınıfın tüm üyeleri ve temel sınıfın üyelerini içeren bir arabirim oluşturmak için bir mekanizma sağlar, ancak açık bir arabirim sağlamak çok daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="2b346-106">Although COM interop provides a mechanism to automatically generate an interface containing all members of the class and the members of its base class, it is far better to provide explicit interfaces.</span></span> <span data-ttu-id="2b346-107">Otomatik olarak oluşturulan arabirimi sınıf arabirimi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="2b346-107">The automatically generated interface is called the class interface.</span></span> <span data-ttu-id="2b346-108">Yönergeler için bkz: [sınıf arabirimine giriş](com-callable-wrapper.md#introducing-the-class-interface).</span><span class="sxs-lookup"><span data-stu-id="2b346-108">For guidelines, see [Introducing the class interface](com-callable-wrapper.md#introducing-the-class-interface).</span></span>  
  
     <span data-ttu-id="2b346-109">Visual Basic kullanabileceğiniz C#ve C++ arabirim tanımlama dili (IDL) ya da eşdeğerine kullanmak zorunda olmak yerine kodunuzun içinde Arabirim tanımları birleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="2b346-109">You can use Visual Basic, C#, and C++ to incorporate interface definitions in your code, instead of having to use Interface Definition Language (IDL) or its equivalent.</span></span> <span data-ttu-id="2b346-110">Söz dizimi ayrıntılarını dil belgelerinize bakın.</span><span class="sxs-lookup"><span data-stu-id="2b346-110">For syntax details, see your language documentation.</span></span>  
  
-   <span data-ttu-id="2b346-111">Yönetilen türler genel olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2b346-111">Managed types must be public.</span></span>  
  
     <span data-ttu-id="2b346-112">Yalnızca genel türleri bir derlemede kayıtlı ve için tür kitaplığı dışarı.</span><span class="sxs-lookup"><span data-stu-id="2b346-112">Only public types in an assembly are registered and exported to the type library.</span></span> <span data-ttu-id="2b346-113">Sonuç olarak, yalnızca genel türler COM'a görünebilir</span><span class="sxs-lookup"><span data-stu-id="2b346-113">As a result, only public types are visible to COM.</span></span>  
  
     <span data-ttu-id="2b346-114">Türleri sunmaya özellikleri COM'a gösterilmeyen diğer yönetilen kod için yönetilen</span><span class="sxs-lookup"><span data-stu-id="2b346-114">Managed types expose features to other managed code that might not be exposed to COM.</span></span> <span data-ttu-id="2b346-115">Örneğin, parametreli Oluşturucular, statik yöntemleri ve sabit alanlarını COM istemcilerine sunulmaz.</span><span class="sxs-lookup"><span data-stu-id="2b346-115">For instance, parameterized constructors, static methods, and constant fields are not exposed to COM clients.</span></span> <span data-ttu-id="2b346-116">Çalışma zamanı türü veriyi sürekliliğe devreder gibi daha fazla veri dönüştürülür ve kopyalanmak.</span><span class="sxs-lookup"><span data-stu-id="2b346-116">Further, as the runtime marshals data in and out of a type, the data might be copied or transformed.</span></span>  
  
-   <span data-ttu-id="2b346-117">Yöntemler, özellikler, alanlar ve olaylar, ortak olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2b346-117">Methods, properties, fields, and events must be public.</span></span>  
  
     <span data-ttu-id="2b346-118">Genel türlerin üyelerini de COM'a görünür olmasını olmaları durumunda ortak olmalıdır</span><span class="sxs-lookup"><span data-stu-id="2b346-118">Members of public types must also be public if they are to be visible to COM.</span></span> <span data-ttu-id="2b346-119">Uygulayarak bir derleme, ortak bir türü veya genel bir türün genel üyeleri görünürlüğünü kısıtlayabilirsiniz <xref:System.Runtime.InteropServices.ComVisibleAttribute>.</span><span class="sxs-lookup"><span data-stu-id="2b346-119">You can restrict the visibility of an assembly, a public type, or public members of a public type by applying the <xref:System.Runtime.InteropServices.ComVisibleAttribute>.</span></span> <span data-ttu-id="2b346-120">Varsayılan olarak, tüm genel türler ve üyeler görülebilir.</span><span class="sxs-lookup"><span data-stu-id="2b346-120">By default, all public types and members are visible.</span></span>  
  
-   <span data-ttu-id="2b346-121">Türleri COM'dan etkinleştirilmesi için bir ortak varsayılan oluşturucusu olmalıdır</span><span class="sxs-lookup"><span data-stu-id="2b346-121">Types must have a public default constructor to be activated from COM.</span></span>  
  
     <span data-ttu-id="2b346-122">Yönetilen, genel türler COM'a görünebilir</span><span class="sxs-lookup"><span data-stu-id="2b346-122">Managed, public types are visible to COM.</span></span> <span data-ttu-id="2b346-123">Ancak, bir ortak varsayılan Oluşturucusu (bağımsız değişken içermeyen bir oluşturucu) tür COM istemcileri oluşturulamıyor.</span><span class="sxs-lookup"><span data-stu-id="2b346-123">However, without a public default constructor (a constructor with no arguments), COM clients cannot create the type.</span></span> <span data-ttu-id="2b346-124">Başka bir yolla tarafından etkinleştirilmişse COM istemcileri türü kullanmaya devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b346-124">COM clients can still use the type if it is activated by some other means.</span></span>  
  
-   <span data-ttu-id="2b346-125">Türleri Özet olamaz.</span><span class="sxs-lookup"><span data-stu-id="2b346-125">Types cannot be abstract.</span></span>  
  
     <span data-ttu-id="2b346-126">Soyut türlerin COM istemcilerini ne .NET istemcileri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b346-126">Neither COM clients nor .NET clients can create abstract types.</span></span>  
  
 <span data-ttu-id="2b346-127">COM dışarı aktardığınızda, yönetilen bir tür devralma hiyerarşisinde düzleştirilir.</span><span class="sxs-lookup"><span data-stu-id="2b346-127">When exported to COM, the inheritance hierarchy of a managed type is flattened.</span></span> <span data-ttu-id="2b346-128">Sürüm oluşturma, yönetilen ve yönetilmeyen ortamlar arasında da farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="2b346-128">Versioning also differs between managed and unmanaged environments.</span></span> <span data-ttu-id="2b346-129">Türler com'a diğer yönetilen türleri aynı sürüm özelliklere sahip değilsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b346-129">Types exposed to COM do not have the same versioning characteristics as other managed types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b346-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b346-130">See also</span></span>
- <xref:System.Runtime.InteropServices.ComVisibleAttribute>
- [<span data-ttu-id="2b346-131">.NET Framework Bileşenlerini COM'da Gösterme</span><span class="sxs-lookup"><span data-stu-id="2b346-131">Exposing .NET Framework Components to COM</span></span>](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="2b346-132">Sınıf arabirimine giriş</span><span class="sxs-lookup"><span data-stu-id="2b346-132">Introducing the class interface</span></span>](com-callable-wrapper.md#introducing-the-class-interface)
- [<span data-ttu-id="2b346-133">Birlikte Çalışma Özniteliklerini Uygulama</span><span class="sxs-lookup"><span data-stu-id="2b346-133">Applying Interop Attributes</span></span>](../../../docs/framework/interop/applying-interop-attributes.md)
- [<span data-ttu-id="2b346-134">COM için Bütünleştirilmiş Kod Paketleme</span><span class="sxs-lookup"><span data-stu-id="2b346-134">Packaging an Assembly for COM</span></span>](../../../docs/framework/interop/packaging-an-assembly-for-com.md)
