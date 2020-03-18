---
title: Örnek COM Sınıfı - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- examples [C#], COM classes
- COM, exposing Visual C# objects to
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
ms.openlocfilehash: 6af85d0314a44acbde0996cecbe6dad82cdcc8db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712084"
---
# <a name="example-com-class-c-programming-guide"></a><span data-ttu-id="69195-102">Örnek COM Sınıfı (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="69195-102">Example COM Class (C# Programming Guide)</span></span>
<span data-ttu-id="69195-103">Aşağıda, COM nesnesi olarak ortaya çıkaracağınız bir sınıf örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="69195-103">The following is an example of a class that you would expose as a COM object.</span></span> <span data-ttu-id="69195-104">Bu kod bir .cs dosyasına yerleştirildikten ve projenize eklendikten sonra COM **Interop özelliğini** **True**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="69195-104">After this code has been placed in a .cs file and added to your project, set the **Register for COM Interop** property to **True**.</span></span> <span data-ttu-id="69195-105">Daha fazla bilgi için [bkz: COM Interop için bir Bileşen kaydedin.](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="69195-105">For more information, see [How to: Register a Component for COM Interop](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100)).</span></span>
  
 <span data-ttu-id="69195-106">Visual C# nesnelerinin COM'a teşhir edilmesi için bir sınıf arabirimi, gerekirse olaylar arabirimi ve sınıfın kendisini bildirme gerekir.</span><span class="sxs-lookup"><span data-stu-id="69195-106">Exposing Visual C# objects to COM requires declaring a class interface, an events interface if it is required, and the class itself.</span></span> <span data-ttu-id="69195-107">Sınıf üyeleri COM tarafından görülebilmek için aşağıdaki kurallara uymalıdır:</span><span class="sxs-lookup"><span data-stu-id="69195-107">Class members must follow these rules to be visible to COM:</span></span>  
  
- <span data-ttu-id="69195-108">Sınıf halka açık olmalı.</span><span class="sxs-lookup"><span data-stu-id="69195-108">The class must be public.</span></span>  
  
- <span data-ttu-id="69195-109">Özellikler, yöntemler ve olaylar herkese açık olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="69195-109">Properties, methods, and events must be public.</span></span>  
  
- <span data-ttu-id="69195-110">Özellikler ve yöntemler sınıf arabiriminde bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="69195-110">Properties and methods must be declared on the class interface.</span></span>  
  
- <span data-ttu-id="69195-111">Olaylar olay arabiriminde bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="69195-111">Events must be declared in the event interface.</span></span>  
  
 <span data-ttu-id="69195-112">Bu arabirimlerde bildirilmemiş sınıfdaki diğer ortak üyeler COM tarafından görülemez, ancak diğer .NET Framework nesneleri tarafından görünür olacaktır.</span><span class="sxs-lookup"><span data-stu-id="69195-112">Other public members in the class that are not declared in these interfaces will not be visible to COM, but they will be visible to other .NET Framework objects.</span></span>  
  
 <span data-ttu-id="69195-113">Özellikleri ve yöntemleri COM'a maruz bırakmak için, bunları sınıf `DispId` arabiriminde bildirmeniz ve bir öznitelikle işaretlemeniz ve bunları sınıfta uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="69195-113">To expose properties and methods to COM, you must declare them on the class interface and mark them with a `DispId` attribute, and implement them in the class.</span></span> <span data-ttu-id="69195-114">Üyelerin arabirimde beyan edildiği sıra, COM vtable için kullanılan sıradır.</span><span class="sxs-lookup"><span data-stu-id="69195-114">The order in which the members are declared in the interface is the order used for the COM vtable.</span></span>  
  
 <span data-ttu-id="69195-115">Sınıfınızdaki olayları ortaya çıkarmak için, bunları olaylar arabiriminde `DispId` bildirmeniz ve bunları bir öznitelikle işaretlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="69195-115">To expose events from your class, you must declare them on the events interface and mark them with a `DispId` attribute.</span></span> <span data-ttu-id="69195-116">Sınıf bu arabirimi uygulamamalıdır.</span><span class="sxs-lookup"><span data-stu-id="69195-116">The class should not implement this interface.</span></span>  
  
 <span data-ttu-id="69195-117">Sınıf arabirimini uygular; birden fazla arabirim uygulayabilir, ancak ilk uygulama varsayılan sınıf arabirimi olacaktır.</span><span class="sxs-lookup"><span data-stu-id="69195-117">The class implements the class interface; it can implement more than one interface, but the first implementation will be the default class interface.</span></span> <span data-ttu-id="69195-118">COM'a maruz kalan yöntemleri ve özellikleri burada uygulayın.</span><span class="sxs-lookup"><span data-stu-id="69195-118">Implement the methods and properties exposed to COM here.</span></span> <span data-ttu-id="69195-119">Bunlar genel olarak işaretlenmeli ve sınıf arabirimindeki bildirimlerle eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="69195-119">They must be marked public and must match the declarations in the class interface.</span></span> <span data-ttu-id="69195-120">Ayrıca, burada sınıf tarafından yetiştirilen olayları bildirin.</span><span class="sxs-lookup"><span data-stu-id="69195-120">Also, declare the events raised by the class here.</span></span> <span data-ttu-id="69195-121">Bunlar genel olarak işaretlenmeli ve olaylar arabirimindeki bildirimlerle eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="69195-121">They must be marked public and must match the declarations in the events interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="69195-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="69195-122">Example</span></span>  
 [!code-csharp[csProgGuideInterop#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/ExampleCOM.cs#8)]  
  
## <a name="see-also"></a><span data-ttu-id="69195-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69195-123">See also</span></span>

- [<span data-ttu-id="69195-124">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="69195-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="69195-125">Birlikte çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="69195-125">Interoperability</span></span>](./index.md)
- [<span data-ttu-id="69195-126">Derleme Sayfası, Proje Tasarımcısı (C#)</span><span class="sxs-lookup"><span data-stu-id="69195-126">Build Page, Project Designer (C#)</span></span>](/visualstudio/ide/reference/build-page-project-designer-csharp)
