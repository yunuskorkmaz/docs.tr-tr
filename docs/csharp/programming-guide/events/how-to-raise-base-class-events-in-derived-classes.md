---
title: 'Nasıl yapılır: Türetilmiş sınıflarda temel sınıf olaylarını yükseltme- C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
ms.openlocfilehash: 820bdcb895a1c3eb7c56db55b298c1a9636f2f85
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921872"
---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a><span data-ttu-id="57e90-102">Nasıl yapılır: Türetilmiş sınıflarda temel sınıf olayları oluştur (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="57e90-102">How to: Raise Base Class Events in Derived Classes (C# Programming Guide)</span></span>
<span data-ttu-id="57e90-103">Aşağıdaki basit örnek, bir temel sınıfta olayları bildirmenin standart yolunu gösterir ve bu sayede türetilmiş sınıflardan da oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="57e90-103">The following simple example shows the standard way to declare events in a base class so that they can also be raised from derived classes.</span></span> <span data-ttu-id="57e90-104">Bu model, .NET Framework sınıf kitaplığındaki Windows Forms sınıflarında yaygın olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="57e90-104">This pattern is used extensively in Windows Forms classes in the .NET Framework class library.</span></span>  
  
 <span data-ttu-id="57e90-105">Diğer sınıflar için temel sınıf olarak kullanılabilecek bir sınıf oluşturduğunuzda, olayların yalnızca kendilerini tanımlayan sınıfın içinden çağrılabilen özel bir temsilci türü olduğunu düşünmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="57e90-105">When you create a class that can be used as a base class for other classes, you should consider the fact that events are a special type of delegate that can only be invoked from within the class that declared them.</span></span> <span data-ttu-id="57e90-106">Türetilmiş sınıflar, temel sınıf içinde belirtilen olayları doğrudan çağıramaz.</span><span class="sxs-lookup"><span data-stu-id="57e90-106">Derived classes cannot directly invoke events that are declared within the base class.</span></span> <span data-ttu-id="57e90-107">Bazen yalnızca temel sınıf tarafından ortaya çıkarılan bir olay isteyebilir, çoğu zaman, temel sınıf olaylarını çağırmak için türetilmiş sınıfı etkinleştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="57e90-107">Although sometimes you may want an event that can only be raised by the base class, most of the time, you should enable the derived class to invoke base class events.</span></span> <span data-ttu-id="57e90-108">Bunu yapmak için, olayı sarmalayan temel sınıfta korumalı çağırma yöntemi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="57e90-108">To do this, you can create a protected invoking method in the base class that wraps the event.</span></span> <span data-ttu-id="57e90-109">Bu çağırma yöntemini çağırarak veya geçersiz kılarak, türetilmiş sınıflar olayı dolaylı olarak çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="57e90-109">By calling or overriding this invoking method, derived classes can invoke the event indirectly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="57e90-110">Bir temel sınıfta sanal olayları bildirmeyin ve bunları türetilmiş bir sınıfta geçersiz kılarsınız.</span><span class="sxs-lookup"><span data-stu-id="57e90-110">Do not declare virtual events in a base class and override them in a derived class.</span></span> <span data-ttu-id="57e90-111">C# Derleyici bunları doğru işlemez ve türetilmiş olaya bir abonenin gerçekten de temel sınıf olayına abone olup olmayacağını tahmin edilemez.</span><span class="sxs-lookup"><span data-stu-id="57e90-111">The C# compiler does not handle these correctly and it is unpredictable whether a subscriber to the derived event will actually be subscribing to the base class event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57e90-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="57e90-112">Example</span></span>  
 [!code-csharp[csProgGuideEvents#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="57e90-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="57e90-113">See also</span></span>

- [<span data-ttu-id="57e90-114">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="57e90-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="57e90-115">Olaylar</span><span class="sxs-lookup"><span data-stu-id="57e90-115">Events</span></span>](./index.md)
- [<span data-ttu-id="57e90-116">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="57e90-116">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="57e90-117">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="57e90-117">Access Modifiers</span></span>](../classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="57e90-118">Windows Forms'ta Olay İşleyicileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="57e90-118">Creating Event Handlers in Windows Forms</span></span>](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)
