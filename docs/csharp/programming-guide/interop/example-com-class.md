---
title: Örnek COM sınıfı-C# Programlama Kılavuzu
description: C# ' de bir sınıfı COM nesnesi olarak kullanıma sunma hakkında bilgi edinin. Bu örnek, bir. cs dosyasındaki kodu bir projeye ekler ve COM birlikte çalışma özelliğini Kaydet özelliği ayarlar.
ms.date: 07/20/2015
helpviewer_keywords:
- examples [C#], COM classes
- COM, exposing Visual C# objects to
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
ms.openlocfilehash: 9274fef15e4fcfd4a268e4f245581966ad6ab750
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91170369"
---
# <a name="example-com-class-c-programming-guide"></a><span data-ttu-id="2c1cd-104">Örnek COM Sınıfı (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="2c1cd-104">Example COM Class (C# Programming Guide)</span></span>

<span data-ttu-id="2c1cd-105">Aşağıda bir COM nesnesi olarak kullanıma sunabileceğiniz bir sınıf örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2c1cd-105">The following is an example of a class that you would expose as a COM object.</span></span> <span data-ttu-id="2c1cd-106">Bu kod bir. cs dosyasına yerleştirildikten ve projenize eklendikten sonra, **com birlikte çalışma özelliğini kaydet** özelliğini **doğru**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2c1cd-106">After this code has been placed in a .cs file and added to your project, set the **Register for COM Interop** property to **True**.</span></span> <span data-ttu-id="2c1cd-107">Daha fazla bilgi için bkz. [nasıl yapılır: bir BILEŞENI com birlikte çalışması Için kaydetme](/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="2c1cd-107">For more information, see [How to: Register a Component for COM Interop](/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100)).</span></span>
  
 <span data-ttu-id="2c1cd-108">Visual C# nesnelerini COM 'a göstermek için bir sınıf arabirimi, gerekliyse bir olay arabirimi ve sınıfın kendisi için bildirim gerekir.</span><span class="sxs-lookup"><span data-stu-id="2c1cd-108">Exposing Visual C# objects to COM requires declaring a class interface, an events interface if it is required, and the class itself.</span></span> <span data-ttu-id="2c1cd-109">Sınıf üyelerinin COM 'a görünür olması için bu kuralları izlemesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="2c1cd-109">Class members must follow these rules to be visible to COM:</span></span>  
  
- <span data-ttu-id="2c1cd-110">Sınıf ortak olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2c1cd-110">The class must be public.</span></span>  
  
- <span data-ttu-id="2c1cd-111">Özellikler, Yöntemler ve olaylar ortak olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2c1cd-111">Properties, methods, and events must be public.</span></span>  
  
- <span data-ttu-id="2c1cd-112">Özellikler ve Yöntemler sınıf arabiriminde bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="2c1cd-112">Properties and methods must be declared on the class interface.</span></span>  
  
- <span data-ttu-id="2c1cd-113">Olaylar olay arabiriminde bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="2c1cd-113">Events must be declared in the event interface.</span></span>  
  
 <span data-ttu-id="2c1cd-114">Bu arabirimlerde bildirilmeyen sınıftaki diğer genel Üyeler COM 'a görünmez, ancak diğer .NET nesneleri tarafından görülecektir.</span><span class="sxs-lookup"><span data-stu-id="2c1cd-114">Other public members in the class that are not declared in these interfaces will not be visible to COM, but they will be visible to other .NET objects.</span></span>  
  
 <span data-ttu-id="2c1cd-115">Özellikleri ve yöntemleri COM 'a sunmak için, bunları sınıf arabiriminde bildirmeniz ve bir `DispId` özniteliğiyle işaretlemeniz ve bunları sınıfında uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2c1cd-115">To expose properties and methods to COM, you must declare them on the class interface and mark them with a `DispId` attribute, and implement them in the class.</span></span> <span data-ttu-id="2c1cd-116">Üyelerin arabirimde bildirildiği sıra, COM vtable için kullanılan sıradır.</span><span class="sxs-lookup"><span data-stu-id="2c1cd-116">The order in which the members are declared in the interface is the order used for the COM vtable.</span></span>  
  
 <span data-ttu-id="2c1cd-117">Sınıfınızdan olayları göstermek için bunları olaylar arabiriminde bildirmeniz ve bir özniteliğiyle işaretlemeniz gerekir `DispId` .</span><span class="sxs-lookup"><span data-stu-id="2c1cd-117">To expose events from your class, you must declare them on the events interface and mark them with a `DispId` attribute.</span></span> <span data-ttu-id="2c1cd-118">Sınıf bu arabirimi uygulamamalıdır.</span><span class="sxs-lookup"><span data-stu-id="2c1cd-118">The class should not implement this interface.</span></span>  
  
 <span data-ttu-id="2c1cd-119">Sınıfı sınıfı arabirimini uygular; birden fazla arabirim uygulayabilir, ancak ilk uygulama varsayılan sınıf arabirimi olur.</span><span class="sxs-lookup"><span data-stu-id="2c1cd-119">The class implements the class interface; it can implement more than one interface, but the first implementation will be the default class interface.</span></span> <span data-ttu-id="2c1cd-120">COM 'a sunulan yöntemleri ve özellikleri buraya uygulayın.</span><span class="sxs-lookup"><span data-stu-id="2c1cd-120">Implement the methods and properties exposed to COM here.</span></span> <span data-ttu-id="2c1cd-121">Bunların ortak olarak işaretlenmesi ve sınıf arabirimindeki bildirimlerle eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="2c1cd-121">They must be marked public and must match the declarations in the class interface.</span></span> <span data-ttu-id="2c1cd-122">Ayrıca, burada sınıf tarafından oluşturulan olayları bildirin.</span><span class="sxs-lookup"><span data-stu-id="2c1cd-122">Also, declare the events raised by the class here.</span></span> <span data-ttu-id="2c1cd-123">Bunların ortak olarak işaretlenmesi ve olaylar arabirimindeki bildirimlerle eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="2c1cd-123">They must be marked public and must match the declarations in the events interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c1cd-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="2c1cd-124">Example</span></span>  

 [!code-csharp[csProgGuideInterop#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/ExampleCOM.cs#8)]  
  
## <a name="see-also"></a><span data-ttu-id="2c1cd-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c1cd-125">See also</span></span>

- [<span data-ttu-id="2c1cd-126">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2c1cd-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="2c1cd-127">Birlikte çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="2c1cd-127">Interoperability</span></span>](./index.md)
- [<span data-ttu-id="2c1cd-128">Derleme Sayfası, Proje Tasarımcısı (C#)</span><span class="sxs-lookup"><span data-stu-id="2c1cd-128">Build Page, Project Designer (C#)</span></span>](/visualstudio/ide/reference/build-page-project-designer-csharp)
