---
title: 'Nasıl yapılır: -Türetilmiş sınıflarda temel sınıf olayları yükseltmek C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
ms.openlocfilehash: 6d6e84861ec48be5bccbc050624b0843947cb727
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539870"
---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a><span data-ttu-id="15d6d-102">Nasıl yapılır: Türetilmiş sınıflarda temel sınıf olayları yükseltmek (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="15d6d-102">How to: Raise Base Class Events in Derived Classes (C# Programming Guide)</span></span>
<span data-ttu-id="15d6d-103">Aşağıdaki basit örnekte, böylece türetilmiş sınıflardan de oluşturulabilir, bir temel sınıf olayları bildirmek için standart bir yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="15d6d-103">The following simple example shows the standard way to declare events in a base class so that they can also be raised from derived classes.</span></span> <span data-ttu-id="15d6d-104">Bu düzen Windows Forms sınıfları yaygın olarak kullanılan [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sınıf kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="15d6d-104">This pattern is used extensively in Windows Forms classes in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] class library.</span></span>  
  
 <span data-ttu-id="15d6d-105">Diğer sınıflar için temel sınıf olarak kullanılan bir sınıfı oluşturduğunuzda, olaylar yalnızca gelen bunları bildiren sınıfın içinden çağrılabilen temsilciyi özel bir tür olması, düşünmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="15d6d-105">When you create a class that can be used as a base class for other classes, you should consider the fact that events are a special type of delegate that can only be invoked from within the class that declared them.</span></span> <span data-ttu-id="15d6d-106">Türetilmiş sınıflar temel sınıf içinde bildirilen olayları doğrudan çağrılamıyor.</span><span class="sxs-lookup"><span data-stu-id="15d6d-106">Derived classes cannot directly invoke events that are declared within the base class.</span></span> <span data-ttu-id="15d6d-107">Çoğu zaman, yalnızca taban sınıfı tarafından oluşturulan bir olay bazen isteyebilirsiniz ancak türetilen sınıfın temel sınıf olayları çağırmak etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="15d6d-107">Although sometimes you may want an event that can only be raised by the base class, most of the time, you should enable the derived class to invoke base class events.</span></span> <span data-ttu-id="15d6d-108">Bunu yapmak için olay sarmalar ve taban sınıfta korumalı çağrılıyor bir yöntem oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="15d6d-108">To do this, you can create a protected invoking method in the base class that wraps the event.</span></span> <span data-ttu-id="15d6d-109">Türetilen sınıfların çağrı yapma veya bu çağrılıyor yöntemini geçersiz kılma, olay dolaylı olarak çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="15d6d-109">By calling or overriding this invoking method, derived classes can invoke the event indirectly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="15d6d-110">Sanal bir temel sınıf olayları bildirme değil ve bunları türetilen bir sınıfta geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="15d6d-110">Do not declare virtual events in a base class and override them in a derived class.</span></span> <span data-ttu-id="15d6d-111">C# Derleyici doğru bu işlemez ve türetilmiş bir olaya abone aslında temel sınıf olaya abone olup olmadığını tahmin edilemez.</span><span class="sxs-lookup"><span data-stu-id="15d6d-111">The C# compiler does not handle these correctly and it is unpredictable whether a subscriber to the derived event will actually be subscribing to the base class event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15d6d-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="15d6d-112">Example</span></span>  
 [!code-csharp[csProgGuideEvents#1](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-raise-base-class-events-in-derived-classes_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="15d6d-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15d6d-113">See also</span></span>

- [<span data-ttu-id="15d6d-114">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="15d6d-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="15d6d-115">Olaylar</span><span class="sxs-lookup"><span data-stu-id="15d6d-115">Events</span></span>](../../../csharp/programming-guide/events/index.md)
- [<span data-ttu-id="15d6d-116">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="15d6d-116">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
- [<span data-ttu-id="15d6d-117">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="15d6d-117">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="15d6d-118">Windows Forms'ta Olay İşleyicileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="15d6d-118">Creating Event Handlers in Windows Forms</span></span>](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)
