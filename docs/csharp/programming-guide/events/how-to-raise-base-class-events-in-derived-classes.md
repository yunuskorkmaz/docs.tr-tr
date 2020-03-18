---
title: Türemiş sınıflarda taban sınıf olayları nasıl yükseltilir - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
ms.openlocfilehash: 48f95871aa8a5a33923286262093a143cbd16d40
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712331"
---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a><span data-ttu-id="34f58-102">Türemiş sınıflarda taban sınıf olayları nasıl yükseltilir (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="34f58-102">How to raise base class events in derived classes (C# Programming Guide)</span></span>
<span data-ttu-id="34f58-103">Aşağıdaki basit örnek, türemiş sınıflardan da yükseltilebilmeleri için olayları taban sınıfta bildirmenin standart yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="34f58-103">The following simple example shows the standard way to declare events in a base class so that they can also be raised from derived classes.</span></span> <span data-ttu-id="34f58-104">Bu desen, .NET Framework sınıf kitaplığındaki Windows Forms sınıflarında yaygın olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="34f58-104">This pattern is used extensively in Windows Forms classes in the .NET Framework class library.</span></span>  
  
 <span data-ttu-id="34f58-105">Diğer sınıflar için taban sınıf olarak kullanılabilecek bir sınıf oluşturduğunuzda, olayların yalnızca onları bildiren sınıfın içinden çağrılabilen özel bir temsilci türü olduğu gerçeğini göz önünde bulundurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="34f58-105">When you create a class that can be used as a base class for other classes, you should consider the fact that events are a special type of delegate that can only be invoked from within the class that declared them.</span></span> <span data-ttu-id="34f58-106">Türetilen sınıflar, taban sınıf içinde bildirilen olayları doğrudan çağıramaz.</span><span class="sxs-lookup"><span data-stu-id="34f58-106">Derived classes cannot directly invoke events that are declared within the base class.</span></span> <span data-ttu-id="34f58-107">Bazen yalnızca taban sınıf tarafından yükseltilebilen bir olay isteyebilirsiniz, ancak çoğu zaman, türemiş sınıfın taban sınıf olaylarını çağırmasını sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="34f58-107">Although sometimes you may want an event that can only be raised by the base class, most of the time, you should enable the derived class to invoke base class events.</span></span> <span data-ttu-id="34f58-108">Bunu yapmak için, olayı saran taban sınıfta korumalı bir çağıran yöntem oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="34f58-108">To do this, you can create a protected invoking method in the base class that wraps the event.</span></span> <span data-ttu-id="34f58-109">Bu çağırma yöntemini arayarak veya geçersiz kılarak, türetilen sınıflar olayı dolaylı olarak çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="34f58-109">By calling or overriding this invoking method, derived classes can invoke the event indirectly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="34f58-110">Sanal olayları taban sınıfta bildirin ve türetilmiş bir sınıfta geçersiz kılmayın.</span><span class="sxs-lookup"><span data-stu-id="34f58-110">Do not declare virtual events in a base class and override them in a derived class.</span></span> <span data-ttu-id="34f58-111">C# derleyicisi bunları doğru şekilde işlemez ve türetilen olayın abonesinin aslında taban sınıf olayına abone olup olmayacağı tahmin edilemez.</span><span class="sxs-lookup"><span data-stu-id="34f58-111">The C# compiler does not handle these correctly and it is unpredictable whether a subscriber to the derived event will actually be subscribing to the base class event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34f58-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="34f58-112">Example</span></span>  
 [!code-csharp[csProgGuideEvents#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="34f58-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34f58-113">See also</span></span>

- [<span data-ttu-id="34f58-114">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="34f58-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="34f58-115">Olaylar</span><span class="sxs-lookup"><span data-stu-id="34f58-115">Events</span></span>](./index.md)
- [<span data-ttu-id="34f58-116">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="34f58-116">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="34f58-117">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="34f58-117">Access Modifiers</span></span>](../classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="34f58-118">Windows Forms'ta Olay İşleyicileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="34f58-118">Creating Event Handlers in Windows Forms</span></span>](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)
