---
title: "Birlikte Çalışma için Niteleyici .NET Türleri"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
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
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b0a6d6a2a8139127b46484f972eb797642b4ee53
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="qualifying-net-types-for-interoperation"></a><span data-ttu-id="045a5-102">Birlikte Çalışma için Niteleyici .NET Türleri</span><span class="sxs-lookup"><span data-stu-id="045a5-102">Qualifying .NET Types for Interoperation</span></span>
<span data-ttu-id="045a5-103">COM uygulamaları için derlemedeki türleri kullanıma sunmak istiyorsanız, tasarım zamanında COM birlikte çalışma gereksinimlerini göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="045a5-103">If you intend to expose types in an assembly to COM applications, consider the requirements of COM interop at design time.</span></span> <span data-ttu-id="045a5-104">Aşağıdaki yönergelere uygun olduğunda yönetilen türler (sınıf, arabirim, yapısı ve numaralandırma) COM türleri ile sorunsuz tümleştirme:</span><span class="sxs-lookup"><span data-stu-id="045a5-104">Managed types (class, interface, structure, and enumeration) seamlessly integrate with COM types when you adhere to the following guidelines:</span></span>  
  
-   <span data-ttu-id="045a5-105">Sınıflar arabirimleri açıkça uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="045a5-105">Classes should implement interfaces explicitly.</span></span>  
  
     <span data-ttu-id="045a5-106">COM birlikte çalışma otomatik olarak sınıfın tüm üyeleri ve devralınabilir. taban sınıfı üyeleri içeren bir arabirim oluşturmak için bir mekanizma sağlasa da, açık arabirimler sağlamak çok daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="045a5-106">Although COM interop provides a mechanism to automatically generate an interface containing all members of the class and the members of its base class, it is far better to provide explicit interfaces.</span></span> <span data-ttu-id="045a5-107">Otomatik olarak oluşturulan arabirimi sınıf arabirimi adı verilir.</span><span class="sxs-lookup"><span data-stu-id="045a5-107">The automatically generated interface is called the class interface.</span></span> <span data-ttu-id="045a5-108">Yönergeler için bkz: [sınıf arabirimi Tanıtımı](com-callable-wrapper.md#introducing-the-class-interface).</span><span class="sxs-lookup"><span data-stu-id="045a5-108">For guidelines, see [Introducing the class interface](com-callable-wrapper.md#introducing-the-class-interface).</span></span>  
  
     <span data-ttu-id="045a5-109">Arabirim tanımları arabirimi tanım dili (IDL) veya eşdeğer kullanmak zorunda olmak yerine, kodunuzda birleştirmek için Visual Basic, C# ve C++ kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="045a5-109">You can use Visual Basic, C#, and C++ to incorporate interface definitions in your code, instead of having to use Interface Definition Language (IDL) or its equivalent.</span></span> <span data-ttu-id="045a5-110">Sözdizimi ayrıntılarını dil belgelerinize bakın.</span><span class="sxs-lookup"><span data-stu-id="045a5-110">For syntax details, see your language documentation.</span></span>  
  
-   <span data-ttu-id="045a5-111">Yönetilen türler ortak olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="045a5-111">Managed types must be public.</span></span>  
  
     <span data-ttu-id="045a5-112">Yalnızca genel türleri derlemedeki kayıtlı ve tür kitaplığı dışarı.</span><span class="sxs-lookup"><span data-stu-id="045a5-112">Only public types in an assembly are registered and exported to the type library.</span></span> <span data-ttu-id="045a5-113">Sonuç olarak, yalnızca genel türleri COM'a görülebilir</span><span class="sxs-lookup"><span data-stu-id="045a5-113">As a result, only public types are visible to COM.</span></span>  
  
     <span data-ttu-id="045a5-114">Türleri sunmaya özellikleri COM'a gösterilmeyen diğer yönetilen kod için yönetilen</span><span class="sxs-lookup"><span data-stu-id="045a5-114">Managed types expose features to other managed code that might not be exposed to COM.</span></span> <span data-ttu-id="045a5-115">Örneğin, parametreli Oluşturucular, statik yöntemler ve sabit alanları COM istemcilere sunulmaz.</span><span class="sxs-lookup"><span data-stu-id="045a5-115">For instance, parameterized constructors, static methods, and constant fields are not exposed to COM clients.</span></span> <span data-ttu-id="045a5-116">Veri türü ve çalışma zamanı sıralar gibi Ayrıca, verileri kopyalanan ya da.</span><span class="sxs-lookup"><span data-stu-id="045a5-116">Further, as the runtime marshals data in and out of a type, the data might be copied or transformed.</span></span>  
  
-   <span data-ttu-id="045a5-117">Yöntemler, özellikler, alanları ve olayları ortak olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="045a5-117">Methods, properties, fields, and events must be public.</span></span>  
  
     <span data-ttu-id="045a5-118">Genel tür üyeleri ayrıca COM'a görünür olmasını olmaları durumunda ortak olmalıdır</span><span class="sxs-lookup"><span data-stu-id="045a5-118">Members of public types must also be public if they are to be visible to COM.</span></span> <span data-ttu-id="045a5-119">Bir derlemeyi, genel bir tür ya da ortak bir türün genel üyeleri görünürlüğünü uygulayarak kısıtlayabilirsiniz <xref:System.Runtime.InteropServices.ComVisibleAttribute>.</span><span class="sxs-lookup"><span data-stu-id="045a5-119">You can restrict the visibility of an assembly, a public type, or public members of a public type by applying the <xref:System.Runtime.InteropServices.ComVisibleAttribute>.</span></span> <span data-ttu-id="045a5-120">Varsayılan olarak, tüm genel türleri ve üyeleri görülebilir.</span><span class="sxs-lookup"><span data-stu-id="045a5-120">By default, all public types and members are visible.</span></span>  
  
-   <span data-ttu-id="045a5-121">Türleri COM'dan etkinleştirilmesi için bir ortak varsayılan oluşturucuya sahip olmalıdır</span><span class="sxs-lookup"><span data-stu-id="045a5-121">Types must have a public default constructor to be activated from COM.</span></span>  
  
     <span data-ttu-id="045a5-122">Yönetilen, genel türleri COM'a görünür</span><span class="sxs-lookup"><span data-stu-id="045a5-122">Managed, public types are visible to COM.</span></span> <span data-ttu-id="045a5-123">Ancak, bir ortak varsayılan oluşturucu (bağımsız değişken içermeyen bir oluşturucuya) COM istemcileri türü oluşturulamıyor.</span><span class="sxs-lookup"><span data-stu-id="045a5-123">However, without a public default constructor (a constructor with no arguments), COM clients cannot create the type.</span></span> <span data-ttu-id="045a5-124">Başka bir şekilde etkinleştirdiyseniz COM istemcileri türü kullanmaya devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="045a5-124">COM clients can still use the type if it is activated by some other means.</span></span>  
  
-   <span data-ttu-id="045a5-125">Türleri Özet olamaz.</span><span class="sxs-lookup"><span data-stu-id="045a5-125">Types cannot be abstract.</span></span>  
  
     <span data-ttu-id="045a5-126">COM istemcileri ne .NET istemcileri soyut türler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="045a5-126">Neither COM clients nor .NET clients can create abstract types.</span></span>  
  
 <span data-ttu-id="045a5-127">COM verildiğinde, yönetilen tür devralma hiyerarşisini düzleştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="045a5-127">When exported to COM, the inheritance hierarchy of a managed type is flattened.</span></span> <span data-ttu-id="045a5-128">Sürüm oluşturma da yönetilen ve yönetilmeyen ortamlar arasında farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="045a5-128">Versioning also differs between managed and unmanaged environments.</span></span> <span data-ttu-id="045a5-129">Com'a türleri yönetilen diğer türleri ile aynı sürüm özelliklere sahip değilsiniz.</span><span class="sxs-lookup"><span data-stu-id="045a5-129">Types exposed to COM do not have the same versioning characteristics as other managed types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="045a5-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="045a5-130">See Also</span></span>  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>  
 [<span data-ttu-id="045a5-131">.NET Framework Bileşenlerini COM'da Gösterme</span><span class="sxs-lookup"><span data-stu-id="045a5-131">Exposing .NET Framework Components to COM</span></span>](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [<span data-ttu-id="045a5-132">Sınıf arabirimi Tanıtımı</span><span class="sxs-lookup"><span data-stu-id="045a5-132">Introducing the Class Interface</span></span>](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024)  
 [<span data-ttu-id="045a5-133">Birlikte Çalışma Özniteliklerini Uygulama</span><span class="sxs-lookup"><span data-stu-id="045a5-133">Applying Interop Attributes</span></span>](../../../docs/framework/interop/applying-interop-attributes.md)  
 [<span data-ttu-id="045a5-134">COM için Bütünleştirilmiş Kod Paketleme</span><span class="sxs-lookup"><span data-stu-id="045a5-134">Packaging an Assembly for COM</span></span>](../../../docs/framework/interop/packaging-an-assembly-for-com.md)
