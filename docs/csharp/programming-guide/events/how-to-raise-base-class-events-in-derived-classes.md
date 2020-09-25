---
title: Türetilmiş sınıflarda temel sınıf olayları nasıl tetiklemeli-C# Programlama Kılavuzu
description: Türetilmiş sınıflarda temel sınıf olaylarının nasıl tetikleyeceğinizi öğrenin. Bir kod örneğine bakın ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
ms.openlocfilehash: b9708876e7d46072439ae498fd551a7b3b23a29e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167528"
---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a><span data-ttu-id="98516-104">Türetilmiş sınıflarda temel sınıf olayları nasıl tetiklemeli (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="98516-104">How to raise base class events in derived classes (C# Programming Guide)</span></span>

<span data-ttu-id="98516-105">Aşağıdaki basit örnek, bir temel sınıfta olayları bildirmenin standart yolunu gösterir ve bu sayede türetilmiş sınıflardan da oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="98516-105">The following simple example shows the standard way to declare events in a base class so that they can also be raised from derived classes.</span></span> <span data-ttu-id="98516-106">Bu model, .NET sınıf kitaplıklarındaki Windows Forms sınıflarında yaygın olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="98516-106">This pattern is used extensively in Windows Forms classes in the .NET class libraries.</span></span>  
  
 <span data-ttu-id="98516-107">Diğer sınıflar için temel sınıf olarak kullanılabilecek bir sınıf oluşturduğunuzda, olayların yalnızca kendilerini tanımlayan sınıfın içinden çağrılabilen özel bir temsilci türü olduğunu düşünmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="98516-107">When you create a class that can be used as a base class for other classes, you should consider the fact that events are a special type of delegate that can only be invoked from within the class that declared them.</span></span> <span data-ttu-id="98516-108">Türetilmiş sınıflar, temel sınıf içinde belirtilen olayları doğrudan çağıramaz.</span><span class="sxs-lookup"><span data-stu-id="98516-108">Derived classes cannot directly invoke events that are declared within the base class.</span></span> <span data-ttu-id="98516-109">Bazen yalnızca temel sınıf tarafından ortaya çıkarılan bir olay isteyebilir, çoğu zaman, temel sınıf olaylarını çağırmak için türetilmiş sınıfı etkinleştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="98516-109">Although sometimes you may want an event that can only be raised by the base class, most of the time, you should enable the derived class to invoke base class events.</span></span> <span data-ttu-id="98516-110">Bunu yapmak için, olayı sarmalayan temel sınıfta korumalı çağırma yöntemi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="98516-110">To do this, you can create a protected invoking method in the base class that wraps the event.</span></span> <span data-ttu-id="98516-111">Bu çağırma yöntemini çağırarak veya geçersiz kılarak, türetilmiş sınıflar olayı dolaylı olarak çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="98516-111">By calling or overriding this invoking method, derived classes can invoke the event indirectly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="98516-112">Bir temel sınıfta sanal olayları bildirmeyin ve bunları türetilmiş bir sınıfta geçersiz kılarsınız.</span><span class="sxs-lookup"><span data-stu-id="98516-112">Do not declare virtual events in a base class and override them in a derived class.</span></span> <span data-ttu-id="98516-113">C# derleyicisi bunları doğru işlemez ve türetilmiş olaya bir abonenin gerçekten de temel sınıf olayına abone olup olmayacağını tahmin edilemez.</span><span class="sxs-lookup"><span data-stu-id="98516-113">The C# compiler does not handle these correctly and it is unpredictable whether a subscriber to the derived event will actually be subscribing to the base class event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="98516-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="98516-114">Example</span></span>  

 [!code-csharp[csProgGuideEvents#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="98516-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98516-115">See also</span></span>

- [<span data-ttu-id="98516-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="98516-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="98516-117">Olaylar</span><span class="sxs-lookup"><span data-stu-id="98516-117">Events</span></span>](./index.md)
- [<span data-ttu-id="98516-118">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="98516-118">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="98516-119">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="98516-119">Access Modifiers</span></span>](../classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="98516-120">Windows Forms'ta Olay İşleyicileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="98516-120">Creating Event Handlers in Windows Forms</span></span>](/dotnet/desktop/winforms/creating-event-handlers-in-windows-forms)
