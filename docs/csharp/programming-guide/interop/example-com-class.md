---
title: "Örnek COM Sınıfı (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- examples [C#], COM classes
- COM, exposing Visual C# objects to
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ad14b414c037d38da55ce0ec82685b790cc46d2f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="example-com-class-c-programming-guide"></a><span data-ttu-id="f654c-102">Örnek COM Sınıfı (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="f654c-102">Example COM Class (C# Programming Guide)</span></span>
<span data-ttu-id="f654c-103">Bir COM nesnesi olarak kullanıma sunmak bir sınıfın bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f654c-103">The following is an example of a class that you would expose as a COM object.</span></span> <span data-ttu-id="f654c-104">Bu kod bir .cs dosyasında yerleştirilir ve projenize eklenen sonra kümesini **kaydetmek için COM birlikte çalışma** özelliğine **doğru**.</span><span class="sxs-lookup"><span data-stu-id="f654c-104">After this code has been placed in a .cs file and added to your project, set the **Register for COM Interop** property to **True**.</span></span> <span data-ttu-id="f654c-105">Daha fazla bilgi için bkz: [NIB: nasıl yapılır: COM birlikte çalışma için bir bileşen Kaydol](http://msdn.microsoft.com/en-us/4de7d474-56e8-4027-994d-d47ca4725c5e).</span><span class="sxs-lookup"><span data-stu-id="f654c-105">For more information, see [NIB: How to: Register a Component for COM Interop](http://msdn.microsoft.com/en-us/4de7d474-56e8-4027-994d-d47ca4725c5e).</span></span>  
  
 <span data-ttu-id="f654c-106">Visual C# COM nesnelerini gösterme sınıf arabirimi, gerekli olduğunda olayları arabirim ve sınıf bildirme gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f654c-106">Exposing Visual C# objects to COM requires declaring a class interface, an events interface if it is required, and the class itself.</span></span> <span data-ttu-id="f654c-107">Sınıf üyeleri için COM görünür olması için bu kurallara uymalıdır:</span><span class="sxs-lookup"><span data-stu-id="f654c-107">Class members must follow these rules to be visible to COM:</span></span>  
  
-   <span data-ttu-id="f654c-108">Sınıf ortak olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f654c-108">The class must be public.</span></span>  
  
-   <span data-ttu-id="f654c-109">Özellikleri, yöntemleri ve olayları ortak olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f654c-109">Properties, methods, and events must be public.</span></span>  
  
-   <span data-ttu-id="f654c-110">Özellikleri ve yöntemleri sınıfı arabirimde bildirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f654c-110">Properties and methods must be declared on the class interface.</span></span>  
  
-   <span data-ttu-id="f654c-111">Olaylar olay arabirimi bildirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f654c-111">Events must be declared in the event interface.</span></span>  
  
 <span data-ttu-id="f654c-112">Bu arabirimleri bildirilmemiş diğer ortak sınıf üyelerine COM görünmez, ancak diğer .NET Framework nesneleri için görünür olacaktır.</span><span class="sxs-lookup"><span data-stu-id="f654c-112">Other public members in the class that are not declared in these interfaces will not be visible to COM, but they will be visible to other .NET Framework objects.</span></span>  
  
 <span data-ttu-id="f654c-113">Özellikleri ve yöntemleri com kullanıma sunmak için sınıf arabirimde bildirme ve bunlarla işaretlemek bir `DispId` özniteliği ve bunları sınıfında uygulama.</span><span class="sxs-lookup"><span data-stu-id="f654c-113">To expose properties and methods to COM, you must declare them on the class interface and mark them with a `DispId` attribute, and implement them in the class.</span></span> <span data-ttu-id="f654c-114">Üyeleri bir arabirimde bildirilen sırası COM vtable için kullanılan sıradır.</span><span class="sxs-lookup"><span data-stu-id="f654c-114">The order in which the members are declared in the interface is the order used for the COM vtable.</span></span>  
  
 <span data-ttu-id="f654c-115">Olaylar, sınıfından oluşturmak için olayları arabirimi bildirme ve bunlarla işaretlemek bir `DispId` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="f654c-115">To expose events from your class, you must declare them on the events interface and mark them with a `DispId` attribute.</span></span> <span data-ttu-id="f654c-116">Sınıfı bu arabirimi uygulamalıdır değil.</span><span class="sxs-lookup"><span data-stu-id="f654c-116">The class should not implement this interface.</span></span>  
  
 <span data-ttu-id="f654c-117">Sınıf sınıf arabirimi uygular; birden fazla arabirimi uygulayabilirsiniz, ancak ilk uygulaması varsayılan sınıf arabirimi olacaktır.</span><span class="sxs-lookup"><span data-stu-id="f654c-117">The class implements the class interface; it can implement more than one interface, but the first implementation will be the default class interface.</span></span> <span data-ttu-id="f654c-118">Burada com'a özellikleri ve yöntemleri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="f654c-118">Implement the methods and properties exposed to COM here.</span></span> <span data-ttu-id="f654c-119">Bunlar ortak işaretlenmesi gerekir ve sınıf arabirimi bildirimlerinde eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f654c-119">They must be marked public and must match the declarations in the class interface.</span></span> <span data-ttu-id="f654c-120">Ayrıca, burada sınıfı tarafından tetiklenen olayları bildirin.</span><span class="sxs-lookup"><span data-stu-id="f654c-120">Also, declare the events raised by the class here.</span></span> <span data-ttu-id="f654c-121">Bunlar ortak işaretlenmesi gerekir ve olayları arabirimi bildirimlerinde eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f654c-121">They must be marked public and must match the declarations in the events interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f654c-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="f654c-122">Example</span></span>  
 [!code-csharp[csProgGuideInterop#8](../../../csharp/programming-guide/interop/codesnippet/CSharp/example-com-class_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="f654c-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f654c-123">See Also</span></span>  
 [<span data-ttu-id="f654c-124">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f654c-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f654c-125">Birlikte çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="f654c-125">Interoperability</span></span>](../../../csharp/programming-guide/interop/index.md)  
 [<span data-ttu-id="f654c-126">Derleme sayfası, Proje Tasarımcısı (C#)</span><span class="sxs-lookup"><span data-stu-id="f654c-126">Build Page, Project Designer (C#)</span></span>](/visualstudio/ide/reference/build-page-project-designer-csharp)
