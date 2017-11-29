---
title: "Statik Oluşturucular (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ee5448095cf06c2473c94bae542c02557918271a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="static-constructors-c-programming-guide"></a><span data-ttu-id="b45b8-102">Statik Oluşturucular (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="b45b8-102">Static Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="b45b8-103">Statik Oluşturucu herhangi başlatmak için kullanılan [statik](../../../csharp/language-reference/keywords/static.md) verileri, yalnızca bir kez gerçekleştirilmesi gerekir belirli bir eylemi gerçekleştirmek için veya.</span><span class="sxs-lookup"><span data-stu-id="b45b8-103">A static constructor is used to initialize any [static](../../../csharp/language-reference/keywords/static.md) data, or to perform a particular action that needs to be performed once only.</span></span> <span data-ttu-id="b45b8-104">Otomatik olarak ilk örneği oluşturulduğunda veya herhangi bir statik üye başvurulan önce çağrılır.</span><span class="sxs-lookup"><span data-stu-id="b45b8-104">It is called automatically before the first instance is created or any static members are referenced.</span></span>  
  
 [!code-csharp[csProgGuideObjects#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_1.cs)]  
  
 <span data-ttu-id="b45b8-105">Statik oluşturucular aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="b45b8-105">Static constructors have the following properties:</span></span>  
  
-   <span data-ttu-id="b45b8-106">Statik Oluşturucu erişim değiştiricileri alın ya da parametrelere sahip.</span><span class="sxs-lookup"><span data-stu-id="b45b8-106">A static constructor does not take access modifiers or have parameters.</span></span>  
  
-   <span data-ttu-id="b45b8-107">Statik Oluşturucu otomatik olarak başlatmak için çağrılır [sınıfı](../../../csharp/language-reference/keywords/class.md) ilk örneği oluşturulduğunda veya herhangi bir statik üye başvurulan önce.</span><span class="sxs-lookup"><span data-stu-id="b45b8-107">A static constructor is called automatically to initialize the [class](../../../csharp/language-reference/keywords/class.md) before the first instance is created or any static members are referenced.</span></span>  
  
-   <span data-ttu-id="b45b8-108">Statik Oluşturucu doğrudan çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="b45b8-108">A static constructor cannot be called directly.</span></span>  
  
-   <span data-ttu-id="b45b8-109">Kullanıcının statik Oluşturucusu programa zaman yürütülür üzerinde denetimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="b45b8-109">The user has no control on when the static constructor is executed in the program.</span></span>  
  
-   <span data-ttu-id="b45b8-110">Statik Oluşturucular, tipik kullanımını sınıfı bir günlük dosyası kullanıyor ve Oluşturucusu girişler bu dosyaya yazmak için kullanılan durumdur.</span><span class="sxs-lookup"><span data-stu-id="b45b8-110">A typical use of static constructors is when the class is using a log file and the constructor is used to write entries to this file.</span></span>  
  
-   <span data-ttu-id="b45b8-111">Statik oluşturucular de yararlı Oluşturucusu çağırabilirsiniz yönetilmeyen kod için sarmalayıcı sınıflar oluştururken `LoadLibrary` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b45b8-111">Static constructors are also useful when creating wrapper classes for unmanaged code, when the constructor can call the `LoadLibrary` method.</span></span>  
  
-   <span data-ttu-id="b45b8-112">Statik Oluşturucusu bir özel durum oluşturursa, çalışma zamanı, ikinci kez çağırmayacaktır ve türü programınızı çalıştığı uygulama etki alanı için kullanım ömrünü başlatılmamış kalır.</span><span class="sxs-lookup"><span data-stu-id="b45b8-112">If a static constructor throws an exception, the runtime will not invoke it a second time, and the type will remain uninitialized for the lifetime of the application domain in which your program is running.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b45b8-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="b45b8-113">Example</span></span>  
 <span data-ttu-id="b45b8-114">Bu örnekte, sınıf `Bus` statik bir oluşturucuya sahip.</span><span class="sxs-lookup"><span data-stu-id="b45b8-114">In this example, class `Bus` has a static constructor.</span></span> <span data-ttu-id="b45b8-115">Zaman ilk örneğini `Bus` oluşturulur (`bus1`), statik Oluşturucusu sınıfını başlatmak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="b45b8-115">When the first instance of `Bus` is created (`bus1`), the static constructor is invoked to initialize the class.</span></span> <span data-ttu-id="b45b8-116">Örnek çıktı statik oluşturucusunu yalnızca bir kez rağmen iki örneğini çalıştığını doğrular `Bus` oluşturulur ve örnek oluşturucu döngülerinden önce çalışır.</span><span class="sxs-lookup"><span data-stu-id="b45b8-116">The sample output verifies that the static constructor runs only one time, even though two instances of `Bus` are created, and that it runs before the instance constructor runs.</span></span>  
  
 [!code-csharp[csProgGuideObjects#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="b45b8-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b45b8-117">See Also</span></span>  
 [<span data-ttu-id="b45b8-118">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b45b8-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b45b8-119">Sınıflar ve yapılar</span><span class="sxs-lookup"><span data-stu-id="b45b8-119">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="b45b8-120">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="b45b8-120">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [<span data-ttu-id="b45b8-121">Statik sınıflar ve statik sınıf üyeleri</span><span class="sxs-lookup"><span data-stu-id="b45b8-121">Static Classes and Static Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)  
 [<span data-ttu-id="b45b8-122">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="b45b8-122">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
