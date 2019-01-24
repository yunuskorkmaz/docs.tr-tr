---
title: Statik oluşturucular - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
ms.openlocfilehash: 74932c9a080a077a60ecbc45c997108afa176956
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54676893"
---
# <a name="static-constructors-c-programming-guide"></a><span data-ttu-id="7656f-102">Statik Oluşturucular (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="7656f-102">Static Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="7656f-103">Statik Oluşturucu herhangi başlatmak için kullanılan [statik](../../../csharp/language-reference/keywords/static.md) verileri veya yalnızca bir kez gerçekleştirilmesi gereken belirli bir eylemi gerçekleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="7656f-103">A static constructor is used to initialize any [static](../../../csharp/language-reference/keywords/static.md) data, or to perform a particular action that needs to be performed once only.</span></span> <span data-ttu-id="7656f-104">İlk örneği oluşturulduğunda veya herhangi bir statik üye başvurulan önce otomatik olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="7656f-104">It is called automatically before the first instance is created or any static members are referenced.</span></span>  
  
 [!code-csharp[csProgGuideObjects#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_1.cs)]  
  
 <span data-ttu-id="7656f-105">Statik Oluşturucular, aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="7656f-105">Static constructors have the following properties:</span></span>  
  
-   <span data-ttu-id="7656f-106">Statik Oluşturucu erişim değiştiricileri alın veya parametreleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="7656f-106">A static constructor does not take access modifiers or have parameters.</span></span>  
  
-   <span data-ttu-id="7656f-107">Statik Oluşturucu otomatik olarak başlatmak için çağırılır [sınıfı](../../../csharp/language-reference/keywords/class.md) önce ilk örneği oluşturulduğunda veya herhangi bir statik üye başvurulur.</span><span class="sxs-lookup"><span data-stu-id="7656f-107">A static constructor is called automatically to initialize the [class](../../../csharp/language-reference/keywords/class.md) before the first instance is created or any static members are referenced.</span></span>  
  
-   <span data-ttu-id="7656f-108">Statik Oluşturucu doğrudan çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="7656f-108">A static constructor cannot be called directly.</span></span>  
  
-   <span data-ttu-id="7656f-109">Kullanıcının statik Oluşturucu programa ne zaman çalıştırılır üzerinde denetimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="7656f-109">The user has no control on when the static constructor is executed in the program.</span></span>  
  
-   <span data-ttu-id="7656f-110">Tipik bir kullanımı statik Oluşturucular, sınıf, bir günlük dosyası kullanarak ve oluşturucu girişleri bu dosyaya yazmak için kullanılan andır.</span><span class="sxs-lookup"><span data-stu-id="7656f-110">A typical use of static constructors is when the class is using a log file and the constructor is used to write entries to this file.</span></span>  
  
-   <span data-ttu-id="7656f-111">Statik oluşturucular da yararlı Oluşturucu çağırabilir, yönetilmeyen kod için sarmalayıcı sınıflar oluşturma `LoadLibrary` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7656f-111">Static constructors are also useful when creating wrapper classes for unmanaged code, when the constructor can call the `LoadLibrary` method.</span></span>  
  
-   <span data-ttu-id="7656f-112">Statik Oluşturucu bir özel durum oluşturursa, çalışma zamanı, ikinci kez çağırmayacaktır ve türü, programınızın çalıştığı uygulama etki alanı ömrü boyunca başlatılmamış kalır.</span><span class="sxs-lookup"><span data-stu-id="7656f-112">If a static constructor throws an exception, the runtime will not invoke it a second time, and the type will remain uninitialized for the lifetime of the application domain in which your program is running.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7656f-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="7656f-113">Example</span></span>  
 <span data-ttu-id="7656f-114">Bu örnekte, sınıf `Bus` bir statik Oluşturucusu vardır.</span><span class="sxs-lookup"><span data-stu-id="7656f-114">In this example, class `Bus` has a static constructor.</span></span> <span data-ttu-id="7656f-115">Zaman ilk örneğinin `Bus` oluşturulur (`bus1`), sınıf için statik Oluşturucu çağrılır.</span><span class="sxs-lookup"><span data-stu-id="7656f-115">When the first instance of `Bus` is created (`bus1`), the static constructor is invoked to initialize the class.</span></span> <span data-ttu-id="7656f-116">Statik Oluşturucu yalnızca bir kez olsa bile iki örneği çalıştığından örnek çıktısı doğrular `Bus` oluşturulur, ve örnek oluşturucu döngülerinden önce çalışır.</span><span class="sxs-lookup"><span data-stu-id="7656f-116">The sample output verifies that the static constructor runs only one time, even though two instances of `Bus` are created, and that it runs before the instance constructor runs.</span></span>  
  
 [!code-csharp[csProgGuideObjects#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="7656f-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7656f-117">See also</span></span>

- [<span data-ttu-id="7656f-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7656f-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="7656f-119">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="7656f-119">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
- [<span data-ttu-id="7656f-120">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="7656f-120">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)
- [<span data-ttu-id="7656f-121">Statik Sınıflar ve Statik Sınıf Üyeleri</span><span class="sxs-lookup"><span data-stu-id="7656f-121">Static Classes and Static Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [<span data-ttu-id="7656f-122">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="7656f-122">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
