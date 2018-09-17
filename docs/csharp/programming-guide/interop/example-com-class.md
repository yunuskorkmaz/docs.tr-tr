---
title: Örnek COM Sınıfı (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- examples [C#], COM classes
- COM, exposing Visual C# objects to
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
ms.openlocfilehash: a77f022b4cf7659d506a7893923ce47270cb8c1b
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45745487"
---
# <a name="example-com-class-c-programming-guide"></a><span data-ttu-id="fa99a-102">Örnek COM Sınıfı (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="fa99a-102">Example COM Class (C# Programming Guide)</span></span>
<span data-ttu-id="fa99a-103">Bir sınıfın, bir COM nesnesi olarak kullanıma bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="fa99a-103">The following is an example of a class that you would expose as a COM object.</span></span> <span data-ttu-id="fa99a-104">Bu kod bir .cs dosyasına yerleştirilir ve projenize eklenir sonra ayarlayın **kaydetme COM birlikte çalışması için** özelliğini **True**.</span><span class="sxs-lookup"><span data-stu-id="fa99a-104">After this code has been placed in a .cs file and added to your project, set the **Register for COM Interop** property to **True**.</span></span> <span data-ttu-id="fa99a-105">Daha fazla bilgi için [nasıl yapılır: COM birlikte çalışması için bir bileşeni kayıt](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="fa99a-105">For more information, see [How to: Register a Component for COM Interop](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100)).</span></span>
  
 <span data-ttu-id="fa99a-106">COM Visual C# nesnelerini gösterme, bir sınıf arabirimi, gerekirse olayları arabirim ve sınıf bildirme gerektirir.</span><span class="sxs-lookup"><span data-stu-id="fa99a-106">Exposing Visual C# objects to COM requires declaring a class interface, an events interface if it is required, and the class itself.</span></span> <span data-ttu-id="fa99a-107">Sınıf üyeleri için COM görünür olmasını şu kurallara uymalıdır:</span><span class="sxs-lookup"><span data-stu-id="fa99a-107">Class members must follow these rules to be visible to COM:</span></span>  
  
-   <span data-ttu-id="fa99a-108">Sınıfı, ortak olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fa99a-108">The class must be public.</span></span>  
  
-   <span data-ttu-id="fa99a-109">Özellikleri, yöntemleri ve olayların ortak olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fa99a-109">Properties, methods, and events must be public.</span></span>  
  
-   <span data-ttu-id="fa99a-110">Özellikler ve yöntemler sınıf arabirimi bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="fa99a-110">Properties and methods must be declared on the class interface.</span></span>  
  
-   <span data-ttu-id="fa99a-111">Olayları olay arabirimi bildirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="fa99a-111">Events must be declared in the event interface.</span></span>  
  
 <span data-ttu-id="fa99a-112">Bu arabirimleri bildirilmemiş olan diğer genel sınıf üyeleri için COM görünür durumda değildir, ancak diğer .NET Framework nesneleri için görünür olur.</span><span class="sxs-lookup"><span data-stu-id="fa99a-112">Other public members in the class that are not declared in these interfaces will not be visible to COM, but they will be visible to other .NET Framework objects.</span></span>  
  
 <span data-ttu-id="fa99a-113">Özellikler ve yöntemler com göstermek için bunları sınıf arabirimi bildirmek ve bunları ile işaretleyin bir `DispId` özniteliği ve bunları sınıfında uygulama.</span><span class="sxs-lookup"><span data-stu-id="fa99a-113">To expose properties and methods to COM, you must declare them on the class interface and mark them with a `DispId` attribute, and implement them in the class.</span></span> <span data-ttu-id="fa99a-114">Üyeleri bir arabirimde bildirilen siparişi için COM vtable kullanılan sırasıdır.</span><span class="sxs-lookup"><span data-stu-id="fa99a-114">The order in which the members are declared in the interface is the order used for the COM vtable.</span></span>  
  
 <span data-ttu-id="fa99a-115">Sizin sınıfınızdan olaylar oluşturmak için bunları olayları arabirimi bildirme ve bunlarla işaretlemek bir `DispId` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="fa99a-115">To expose events from your class, you must declare them on the events interface and mark them with a `DispId` attribute.</span></span> <span data-ttu-id="fa99a-116">Sınıf bu arabirim uygulamamalıdır.</span><span class="sxs-lookup"><span data-stu-id="fa99a-116">The class should not implement this interface.</span></span>  
  
 <span data-ttu-id="fa99a-117">Sınıfı, sınıf arabirimi uygular; Daha fazla arabirim uygulayabilir, ancak ilk uygulama varsayılan sınıf arabirimi olacaktır.</span><span class="sxs-lookup"><span data-stu-id="fa99a-117">The class implements the class interface; it can implement more than one interface, but the first implementation will be the default class interface.</span></span> <span data-ttu-id="fa99a-118">Burada com'a özellikleri ve yöntemleri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="fa99a-118">Implement the methods and properties exposed to COM here.</span></span> <span data-ttu-id="fa99a-119">Bunlar genel olarak işaretlenmelidir ve sınıf arabirimi bildirimlerinde eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="fa99a-119">They must be marked public and must match the declarations in the class interface.</span></span> <span data-ttu-id="fa99a-120">Ayrıca, burada sınıfı tarafından tetiklenen olayları bildirin.</span><span class="sxs-lookup"><span data-stu-id="fa99a-120">Also, declare the events raised by the class here.</span></span> <span data-ttu-id="fa99a-121">Bunlar genel olarak işaretlenmelidir ve olayları arabirimi bildirimlerinde eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="fa99a-121">They must be marked public and must match the declarations in the events interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa99a-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="fa99a-122">Example</span></span>  
 [!code-csharp[csProgGuideInterop#8](../../../csharp/programming-guide/interop/codesnippet/CSharp/example-com-class_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="fa99a-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fa99a-123">See Also</span></span>

- [<span data-ttu-id="fa99a-124">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="fa99a-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="fa99a-125">Birlikte çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="fa99a-125">Interoperability</span></span>](../../../csharp/programming-guide/interop/index.md)  
- [<span data-ttu-id="fa99a-126">Derleme Sayfası, Proje Tasarımcısı (C#)</span><span class="sxs-lookup"><span data-stu-id="fa99a-126">Build Page, Project Designer (C#)</span></span>](/visualstudio/ide/reference/build-page-project-designer-csharp)
