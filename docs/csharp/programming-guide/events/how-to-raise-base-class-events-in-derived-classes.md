---
title: 'Nasıl Yapılır: -Türetilmiş sınıflarda temel sınıf olayları yükseltmek C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
ms.openlocfilehash: 11f34e230a1f953ba3d886e416f1ece4253e3c8d
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239624"
---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a><span data-ttu-id="227f1-102">Nasıl Yapılır: Türetilmiş sınıflarda temel sınıf olayları yükseltmek (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="227f1-102">How to: Raise Base Class Events in Derived Classes (C# Programming Guide)</span></span>
<span data-ttu-id="227f1-103">Aşağıdaki basit örnekte, böylece türetilmiş sınıflardan de oluşturulabilir, bir temel sınıf olayları bildirmek için standart bir yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="227f1-103">The following simple example shows the standard way to declare events in a base class so that they can also be raised from derived classes.</span></span> <span data-ttu-id="227f1-104">Bu düzen Windows Forms sınıfları yaygın olarak kullanılan [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sınıf kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="227f1-104">This pattern is used extensively in Windows Forms classes in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] class library.</span></span>  
  
 <span data-ttu-id="227f1-105">Diğer sınıflar için temel sınıf olarak kullanılan bir sınıfı oluşturduğunuzda, olaylar yalnızca gelen bunları bildiren sınıfın içinden çağrılabilen temsilciyi özel bir tür olması, düşünmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="227f1-105">When you create a class that can be used as a base class for other classes, you should consider the fact that events are a special type of delegate that can only be invoked from within the class that declared them.</span></span> <span data-ttu-id="227f1-106">Türetilmiş sınıflar temel sınıf içinde bildirilen olayları doğrudan çağrılamıyor.</span><span class="sxs-lookup"><span data-stu-id="227f1-106">Derived classes cannot directly invoke events that are declared within the base class.</span></span> <span data-ttu-id="227f1-107">Çoğu zaman, yalnızca taban sınıfı tarafından oluşturulan bir olay bazen isteyebilirsiniz ancak türetilen sınıfın temel sınıf olayları çağırmak etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="227f1-107">Although sometimes you may want an event that can only be raised by the base class, most of the time, you should enable the derived class to invoke base class events.</span></span> <span data-ttu-id="227f1-108">Bunu yapmak için olay sarmalar ve taban sınıfta korumalı çağrılıyor bir yöntem oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="227f1-108">To do this, you can create a protected invoking method in the base class that wraps the event.</span></span> <span data-ttu-id="227f1-109">Türetilen sınıfların çağrı yapma veya bu çağrılıyor yöntemini geçersiz kılma, olay dolaylı olarak çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="227f1-109">By calling or overriding this invoking method, derived classes can invoke the event indirectly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="227f1-110">Sanal bir temel sınıf olayları bildirme değil ve bunları türetilen bir sınıfta geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="227f1-110">Do not declare virtual events in a base class and override them in a derived class.</span></span> <span data-ttu-id="227f1-111">C# Derleyici doğru bu işlemez ve türetilmiş bir olaya abone aslında temel sınıf olaya abone olup olmadığını tahmin edilemez.</span><span class="sxs-lookup"><span data-stu-id="227f1-111">The C# compiler does not handle these correctly and it is unpredictable whether a subscriber to the derived event will actually be subscribing to the base class event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="227f1-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="227f1-112">Example</span></span>  
 [!code-csharp[csProgGuideEvents#1](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-raise-base-class-events-in-derived-classes_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="227f1-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="227f1-113">See Also</span></span>

- [<span data-ttu-id="227f1-114">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="227f1-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="227f1-115">Olaylar</span><span class="sxs-lookup"><span data-stu-id="227f1-115">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
- [<span data-ttu-id="227f1-116">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="227f1-116">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
- [<span data-ttu-id="227f1-117">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="227f1-117">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
- [<span data-ttu-id="227f1-118">Windows Forms'ta Olay İşleyicileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="227f1-118">Creating Event Handlers in Windows Forms</span></span>](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)
