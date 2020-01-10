---
title: Örnek COM sınıfı- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- examples [C#], COM classes
- COM, exposing Visual C# objects to
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
ms.openlocfilehash: 6af85d0314a44acbde0996cecbe6dad82cdcc8db
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712084"
---
# <a name="example-com-class-c-programming-guide"></a><span data-ttu-id="8041d-102">Örnek COM Sınıfı (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="8041d-102">Example COM Class (C# Programming Guide)</span></span>
<span data-ttu-id="8041d-103">Aşağıda bir COM nesnesi olarak kullanıma sunabileceğiniz bir sınıf örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8041d-103">The following is an example of a class that you would expose as a COM object.</span></span> <span data-ttu-id="8041d-104">Bu kod bir. cs dosyasına yerleştirildikten ve projenize eklendikten sonra, **com birlikte çalışma özelliğini kaydet** özelliğini **doğru**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8041d-104">After this code has been placed in a .cs file and added to your project, set the **Register for COM Interop** property to **True**.</span></span> <span data-ttu-id="8041d-105">Daha fazla bilgi için bkz. [nasıl yapılır: bir BILEŞENI com birlikte çalışması Için kaydetme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="8041d-105">For more information, see [How to: Register a Component for COM Interop](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100)).</span></span>
  
 <span data-ttu-id="8041d-106">Visual C# Objects 'i com 'a göstermek için bir sınıf arabirimi, gerekliyse bir olay arabirimi ve sınıfın kendisi için bildirim gerekir.</span><span class="sxs-lookup"><span data-stu-id="8041d-106">Exposing Visual C# objects to COM requires declaring a class interface, an events interface if it is required, and the class itself.</span></span> <span data-ttu-id="8041d-107">Sınıf üyelerinin COM 'a görünür olması için bu kuralları izlemesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="8041d-107">Class members must follow these rules to be visible to COM:</span></span>  
  
- <span data-ttu-id="8041d-108">Sınıf ortak olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8041d-108">The class must be public.</span></span>  
  
- <span data-ttu-id="8041d-109">Özellikler, Yöntemler ve olaylar ortak olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8041d-109">Properties, methods, and events must be public.</span></span>  
  
- <span data-ttu-id="8041d-110">Özellikler ve Yöntemler sınıf arabiriminde bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="8041d-110">Properties and methods must be declared on the class interface.</span></span>  
  
- <span data-ttu-id="8041d-111">Olaylar olay arabiriminde bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="8041d-111">Events must be declared in the event interface.</span></span>  
  
 <span data-ttu-id="8041d-112">Bu arabirimlerde bildirilmemiş olan sınıftaki diğer genel Üyeler COM 'a görünmez, ancak diğer .NET Framework nesneleri tarafından görülecektir.</span><span class="sxs-lookup"><span data-stu-id="8041d-112">Other public members in the class that are not declared in these interfaces will not be visible to COM, but they will be visible to other .NET Framework objects.</span></span>  
  
 <span data-ttu-id="8041d-113">Özellikleri ve yöntemleri COM 'a sunmak için, bunları sınıf arabiriminde bildirmeniz ve bir `DispId` özniteliğiyle işaretlemeniz ve bunları sınıfında uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8041d-113">To expose properties and methods to COM, you must declare them on the class interface and mark them with a `DispId` attribute, and implement them in the class.</span></span> <span data-ttu-id="8041d-114">Üyelerin arabirimde bildirildiği sıra, COM vtable için kullanılan sıradır.</span><span class="sxs-lookup"><span data-stu-id="8041d-114">The order in which the members are declared in the interface is the order used for the COM vtable.</span></span>  
  
 <span data-ttu-id="8041d-115">Sınıfınızdan olayları göstermek için bunları olaylar arabiriminde bildirmeniz ve bir `DispId` özniteliğiyle işaretlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8041d-115">To expose events from your class, you must declare them on the events interface and mark them with a `DispId` attribute.</span></span> <span data-ttu-id="8041d-116">Sınıf bu arabirimi uygulamamalıdır.</span><span class="sxs-lookup"><span data-stu-id="8041d-116">The class should not implement this interface.</span></span>  
  
 <span data-ttu-id="8041d-117">Sınıfı sınıfı arabirimini uygular; birden fazla arabirim uygulayabilir, ancak ilk uygulama varsayılan sınıf arabirimi olur.</span><span class="sxs-lookup"><span data-stu-id="8041d-117">The class implements the class interface; it can implement more than one interface, but the first implementation will be the default class interface.</span></span> <span data-ttu-id="8041d-118">COM 'a sunulan yöntemleri ve özellikleri buraya uygulayın.</span><span class="sxs-lookup"><span data-stu-id="8041d-118">Implement the methods and properties exposed to COM here.</span></span> <span data-ttu-id="8041d-119">Bunların ortak olarak işaretlenmesi ve sınıf arabirimindeki bildirimlerle eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="8041d-119">They must be marked public and must match the declarations in the class interface.</span></span> <span data-ttu-id="8041d-120">Ayrıca, burada sınıf tarafından oluşturulan olayları bildirin.</span><span class="sxs-lookup"><span data-stu-id="8041d-120">Also, declare the events raised by the class here.</span></span> <span data-ttu-id="8041d-121">Bunların ortak olarak işaretlenmesi ve olaylar arabirimindeki bildirimlerle eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="8041d-121">They must be marked public and must match the declarations in the events interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8041d-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="8041d-122">Example</span></span>  
 [!code-csharp[csProgGuideInterop#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/ExampleCOM.cs#8)]  
  
## <a name="see-also"></a><span data-ttu-id="8041d-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8041d-123">See also</span></span>

- [<span data-ttu-id="8041d-124">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8041d-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8041d-125">Birlikte çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="8041d-125">Interoperability</span></span>](./index.md)
- [<span data-ttu-id="8041d-126">Derleme Sayfası, Proje Tasarımcısı (C#)</span><span class="sxs-lookup"><span data-stu-id="8041d-126">Build Page, Project Designer (C#)</span></span>](/visualstudio/ide/reference/build-page-project-designer-csharp)
