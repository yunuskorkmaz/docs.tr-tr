---
title: Statik Oluşturucular (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
ms.openlocfilehash: 52c52f68bc3612807b810047044aedbd2c457cf1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33315717"
---
# <a name="static-constructors-c-programming-guide"></a><span data-ttu-id="12596-102">Statik Oluşturucular (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="12596-102">Static Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="12596-103">Statik Oluşturucu herhangi başlatmak için kullanılan [statik](../../../csharp/language-reference/keywords/static.md) verileri, yalnızca bir kez gerçekleştirilmesi gerekir belirli bir eylemi gerçekleştirmek için veya.</span><span class="sxs-lookup"><span data-stu-id="12596-103">A static constructor is used to initialize any [static](../../../csharp/language-reference/keywords/static.md) data, or to perform a particular action that needs to be performed once only.</span></span> <span data-ttu-id="12596-104">Otomatik olarak ilk örneği oluşturulduğunda veya herhangi bir statik üye başvurulan önce çağrılır.</span><span class="sxs-lookup"><span data-stu-id="12596-104">It is called automatically before the first instance is created or any static members are referenced.</span></span>  
  
 [!code-csharp[csProgGuideObjects#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_1.cs)]  
  
 <span data-ttu-id="12596-105">Statik oluşturucular aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="12596-105">Static constructors have the following properties:</span></span>  
  
-   <span data-ttu-id="12596-106">Statik Oluşturucu erişim değiştiricileri alın ya da parametrelere sahip.</span><span class="sxs-lookup"><span data-stu-id="12596-106">A static constructor does not take access modifiers or have parameters.</span></span>  
  
-   <span data-ttu-id="12596-107">Statik Oluşturucu otomatik olarak başlatmak için çağrılır [sınıfı](../../../csharp/language-reference/keywords/class.md) ilk örneği oluşturulduğunda veya herhangi bir statik üye başvurulan önce.</span><span class="sxs-lookup"><span data-stu-id="12596-107">A static constructor is called automatically to initialize the [class](../../../csharp/language-reference/keywords/class.md) before the first instance is created or any static members are referenced.</span></span>  
  
-   <span data-ttu-id="12596-108">Statik Oluşturucu doğrudan çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="12596-108">A static constructor cannot be called directly.</span></span>  
  
-   <span data-ttu-id="12596-109">Kullanıcının statik Oluşturucusu programa zaman yürütülür üzerinde denetimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="12596-109">The user has no control on when the static constructor is executed in the program.</span></span>  
  
-   <span data-ttu-id="12596-110">Statik Oluşturucular, tipik kullanımını sınıfı bir günlük dosyası kullanıyor ve Oluşturucusu girişler bu dosyaya yazmak için kullanılan durumdur.</span><span class="sxs-lookup"><span data-stu-id="12596-110">A typical use of static constructors is when the class is using a log file and the constructor is used to write entries to this file.</span></span>  
  
-   <span data-ttu-id="12596-111">Statik oluşturucular de yararlı Oluşturucusu çağırabilirsiniz yönetilmeyen kod için sarmalayıcı sınıflar oluştururken `LoadLibrary` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="12596-111">Static constructors are also useful when creating wrapper classes for unmanaged code, when the constructor can call the `LoadLibrary` method.</span></span>  
  
-   <span data-ttu-id="12596-112">Statik Oluşturucusu bir özel durum oluşturursa, çalışma zamanı, ikinci kez çağırmayacaktır ve türü programınızı çalıştığı uygulama etki alanı için kullanım ömrünü başlatılmamış kalır.</span><span class="sxs-lookup"><span data-stu-id="12596-112">If a static constructor throws an exception, the runtime will not invoke it a second time, and the type will remain uninitialized for the lifetime of the application domain in which your program is running.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12596-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="12596-113">Example</span></span>  
 <span data-ttu-id="12596-114">Bu örnekte, sınıf `Bus` statik bir oluşturucuya sahip.</span><span class="sxs-lookup"><span data-stu-id="12596-114">In this example, class `Bus` has a static constructor.</span></span> <span data-ttu-id="12596-115">Zaman ilk örneğini `Bus` oluşturulur (`bus1`), statik Oluşturucusu sınıfını başlatmak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="12596-115">When the first instance of `Bus` is created (`bus1`), the static constructor is invoked to initialize the class.</span></span> <span data-ttu-id="12596-116">Örnek çıktı statik oluşturucusunu yalnızca bir kez rağmen iki örneğini çalıştığını doğrular `Bus` oluşturulur ve örnek oluşturucu döngülerinden önce çalışır.</span><span class="sxs-lookup"><span data-stu-id="12596-116">The sample output verifies that the static constructor runs only one time, even though two instances of `Bus` are created, and that it runs before the instance constructor runs.</span></span>  
  
 [!code-csharp[csProgGuideObjects#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="12596-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="12596-117">See Also</span></span>  
 [<span data-ttu-id="12596-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="12596-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="12596-119">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="12596-119">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="12596-120">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="12596-120">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [<span data-ttu-id="12596-121">Statik Sınıflar ve Statik Sınıf Üyeleri</span><span class="sxs-lookup"><span data-stu-id="12596-121">Static Classes and Static Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)  
 [<span data-ttu-id="12596-122">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="12596-122">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
