---
title: 'Nasıl yapılır: Temsilci Bildirme, Oluşturma ve Kullanma (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], declaring and instantiating
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
ms.openlocfilehash: 6c53d7572074db44976494e5eed596bf95aaf456
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43858866"
---
# <a name="how-to-declare-instantiate-and-use-a-delegate-c-programming-guide"></a><span data-ttu-id="37d04-102">Nasıl yapılır: Temsilci Bildirme, Oluşturma ve Kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="37d04-102">How to: Declare, Instantiate, and Use a Delegate (C# Programming Guide)</span></span>
<span data-ttu-id="37d04-103">C# 1.0 ve daha sonra aşağıdaki örnekte gösterildiği gibi temsilciler bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="37d04-103">In C# 1.0 and later, delegates can be declared as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#13](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_1.cs)]  
  
 [!code-csharp[csProgGuideDelegates#14](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_2.cs)]  
  
 <span data-ttu-id="37d04-104">C# 2.0, aşağıdaki örnekte gösterildiği gibi önceki bildirimi yazmak için daha basit bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="37d04-104">C# 2.0 provides a simpler way to write the previous declaration, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#32](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_3.cs)]  
  
 <span data-ttu-id="37d04-105">C# 2.0 ve sonraki sürümlerinde, ayrıca bildirmek ve başlatmak için anonim bir yöntem kullanmak mümkün bir [temsilci](../../../csharp/language-reference/keywords/delegate.md)aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="37d04-105">In C# 2.0 and later, it is also possible to use an anonymous method to declare and initialize a [delegate](../../../csharp/language-reference/keywords/delegate.md), as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#15](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_4.cs)]  
  
 <span data-ttu-id="37d04-106">C# 3.0 ve sonraki sürümlerinde, temsilciler ayrıca bildirilmiş ve bir lambda ifadesi kullanarak, aşağıdaki örnekte gösterildiği gibi örneği.</span><span class="sxs-lookup"><span data-stu-id="37d04-106">In C# 3.0 and later, delegates can also be declared and instantiated by using a lambda expression, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#31](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_5.cs)]  
  
 <span data-ttu-id="37d04-107">Daha fazla bilgi için [Lambda ifadeleri](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="37d04-107">For more information, see [Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="37d04-108">Aşağıdaki örnek, bir temsilci kullanarak bildirme ve örnekleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="37d04-108">The following example illustrates declaring, instantiating, and using a delegate.</span></span> <span data-ttu-id="37d04-109">`BookDB` Sınıfı, bir veritabanına kitap tutan bir Kitaplığı veritabanı kapsüller.</span><span class="sxs-lookup"><span data-stu-id="37d04-109">The `BookDB` class encapsulates a bookstore database that maintains a database of books.</span></span> <span data-ttu-id="37d04-110">Bir yöntem sunan `ProcessPaperbackBooks`, veritabanında kitapları ve her biri için bir temsilci çağıran, tüm alınabilen ciltsiz kitaba bulur.</span><span class="sxs-lookup"><span data-stu-id="37d04-110">It exposes a method, `ProcessPaperbackBooks`, which finds all paperback books in the database and calls a delegate for each one.</span></span> <span data-ttu-id="37d04-111">`delegate` Kullanılan türünün adı `ProcessBookDelegate`.</span><span class="sxs-lookup"><span data-stu-id="37d04-111">The `delegate` type that is used is named `ProcessBookDelegate`.</span></span> <span data-ttu-id="37d04-112">`Test` Sınıfı başlıklar ve ortalama fiyat kitapçığın kitap yazdırmak için bu sınıfı kullanır.</span><span class="sxs-lookup"><span data-stu-id="37d04-112">The `Test` class uses this class to print the titles and average price of the paperback books.</span></span>  
  
 <span data-ttu-id="37d04-113">Temsilciler kullanımını işlevselliği Kitaplığı veritabanı ve istemci kodu arasında iyi ayrımı yükseltir.</span><span class="sxs-lookup"><span data-stu-id="37d04-113">The use of delegates promotes good separation of functionality between the bookstore database and the client code.</span></span> <span data-ttu-id="37d04-114">İstemci kodu books nasıl depolandığını veya kitaplığı kod kitapçığın books nasıl bulacağını olanağıyla sahiptir.</span><span class="sxs-lookup"><span data-stu-id="37d04-114">The client code has no knowledge of how the books are stored or how the bookstore code finds paperback books.</span></span> <span data-ttu-id="37d04-115">Kitaplığı kod bunları bulduktan sonra hangi işleme kitapçığın kitaplar yapılır bilgisi var.</span><span class="sxs-lookup"><span data-stu-id="37d04-115">The bookstore code has no knowledge of what processing is performed on the paperback books after it finds them.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37d04-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="37d04-116">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#12](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_6.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="37d04-117">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="37d04-117">Robust Programming</span></span>  
  
-   <span data-ttu-id="37d04-118">Bir temsilci bildirme.</span><span class="sxs-lookup"><span data-stu-id="37d04-118">Declaring a delegate.</span></span>  
  
     <span data-ttu-id="37d04-119">Aşağıdaki deyim, yeni bir temsilci türü bildirir.</span><span class="sxs-lookup"><span data-stu-id="37d04-119">The following statement declares a new delegate type.</span></span>  
  
     [!code-csharp[csProgGuideDelegates#16](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_7.cs)]  
  
     <span data-ttu-id="37d04-120">Her bir temsilci türü sayısı ve bağımsız değişken türlerinin ve onu kapsülleyen yöntemleri dönüş değerinin türünü açıklar.</span><span class="sxs-lookup"><span data-stu-id="37d04-120">Each delegate type describes the number and types of the arguments, and the type of the return value of methods that it can encapsulate.</span></span> <span data-ttu-id="37d04-121">Bağımsız değişken türleri ya da dönüş değeri yeni bir dizi gerektiğinde yeni bir temsilci türünün bildirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="37d04-121">Whenever a new set of argument types or return value type is needed, a new delegate type must be declared.</span></span>  
  
-   <span data-ttu-id="37d04-122">Bir temsilci örneği.</span><span class="sxs-lookup"><span data-stu-id="37d04-122">Instantiating a delegate.</span></span>  
  
     <span data-ttu-id="37d04-123">Bir temsilci türü bildirildikten sonra bir temsilci nesnesinin oluşturulabilir ve belirli bir yöntem ile ilişkili.</span><span class="sxs-lookup"><span data-stu-id="37d04-123">After a delegate type has been declared, a delegate object must be created and associated with a particular method.</span></span> <span data-ttu-id="37d04-124">Önceki örnekte geçirerek bunu `PrintTitle` yönteme `ProcessPaperbackBooks` yöntem aşağıdaki örnekteki gibi:</span><span class="sxs-lookup"><span data-stu-id="37d04-124">In the previous example, you do this by passing the `PrintTitle` method to the `ProcessPaperbackBooks` method as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#17](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_8.cs)]  
  
     <span data-ttu-id="37d04-125">Bu yeni bir temsilci nesnesi ile ilişkili oluşturur [statik](../../../csharp/language-reference/keywords/static.md) yöntemi `Test.PrintTitle`.</span><span class="sxs-lookup"><span data-stu-id="37d04-125">This creates a new delegate object associated with the [static](../../../csharp/language-reference/keywords/static.md) method `Test.PrintTitle`.</span></span> <span data-ttu-id="37d04-126">Benzer şekilde, statik olmayan yöntemi `AddBookToTotal` nesnesindeki `totaller` aşağıdaki örnekte olduğu gibi geçirilir:</span><span class="sxs-lookup"><span data-stu-id="37d04-126">Similarly, the non-static method `AddBookToTotal` on the object `totaller` is passed as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#18](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_9.cs)]  
  
     <span data-ttu-id="37d04-127">Her iki durumda da yeni bir temsilci nesnesi için geçirilen `ProcessPaperbackBooks` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="37d04-127">In both cases a new delegate object is passed to the `ProcessPaperbackBooks` method.</span></span>  
  
     <span data-ttu-id="37d04-128">Yöntemi daha temsilci oluşturduktan sonra bile asla değişikliklerle ilişkili; temsilci nesneleri sabittir.</span><span class="sxs-lookup"><span data-stu-id="37d04-128">After a delegate is created, the method it is associated with never changes; delegate objects are immutable.</span></span>  
  
-   <span data-ttu-id="37d04-129">Bir temsilci çağırma.</span><span class="sxs-lookup"><span data-stu-id="37d04-129">Calling a delegate.</span></span>  
  
     <span data-ttu-id="37d04-130">Bir temsilci nesne oluşturulduktan sonra temsilci nesne temsilci çağıran başka bir kod için genellikle geçirilir.</span><span class="sxs-lookup"><span data-stu-id="37d04-130">After a delegate object is created, the delegate object is typically passed to other code that will call the delegate.</span></span> <span data-ttu-id="37d04-131">Bir temsilci nesnesinin temsilciye geçirilecek parantez içine alınmış bağımsız değişkenleri ardından temsilci nesnesinin adı kullanılarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="37d04-131">A delegate object is called by using the name of the delegate object, followed by the parenthesized arguments to be passed to the delegate.</span></span> <span data-ttu-id="37d04-132">Bir temsilci çağrısının bir örneği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="37d04-132">Following is an example of a delegate call:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#19](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_10.cs)]  
  
     <span data-ttu-id="37d04-133">Bir temsilci ya da zaman uyumlu olarak, bu örnekte olduğu gibi veya zaman uyumsuz olarak kullanarak çağrılabilir `BeginInvoke` ve `EndInvoke` yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="37d04-133">A delegate can be either called synchronously, as in this example, or asynchronously by using `BeginInvoke` and `EndInvoke` methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37d04-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="37d04-134">See Also</span></span>

- [<span data-ttu-id="37d04-135">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="37d04-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="37d04-136">Olaylar</span><span class="sxs-lookup"><span data-stu-id="37d04-136">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
- [<span data-ttu-id="37d04-137">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="37d04-137">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
