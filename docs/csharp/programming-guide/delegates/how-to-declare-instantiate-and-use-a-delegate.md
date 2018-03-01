---
title: "Nasıl yapılır: Temsilci Bildirme, Oluşturma ve Kullanma (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- delegates [C#], declaring and instantiating
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b5a5329b9e99fcd5830a57eb8f97b4edb67ad8a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-instantiate-and-use-a-delegate-c-programming-guide"></a><span data-ttu-id="f1cbe-102">Nasıl yapılır: Temsilci Bildirme, Oluşturma ve Kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="f1cbe-102">How to: Declare, Instantiate, and Use a Delegate (C# Programming Guide)</span></span>
<span data-ttu-id="f1cbe-103">C# 1.0 ve daha sonra aşağıdaki örnekte gösterildiği gibi temsilciler bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="f1cbe-103">In C# 1.0 and later, delegates can be declared as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#13](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_1.cs)]  
  
 [!code-csharp[csProgGuideDelegates#14](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_2.cs)]  
  
 <span data-ttu-id="f1cbe-104">C# 2.0, aşağıdaki örnekte gösterildiği gibi önceki bildirimi yazmak için daha basit bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1cbe-104">C# 2.0 provides a simpler way to write the previous declaration, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#32](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_3.cs)]  
  
 <span data-ttu-id="f1cbe-105">C# 2.0 ve daha sonra aynı zamanda adsız bir yöntem bildirin ve başlatmak için kullanmak mümkün bir [temsilci](../../../csharp/language-reference/keywords/delegate.md), aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="f1cbe-105">In C# 2.0 and later, it is also possible to use an anonymous method to declare and initialize a [delegate](../../../csharp/language-reference/keywords/delegate.md), as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#15](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_4.cs)]  
  
 <span data-ttu-id="f1cbe-106">C# 3.0 ve sonraki sürümlerinde, temsilciler ayrıca bildirilmiş ve bir lambda ifadesi kullanarak aşağıdaki örnekte gösterildiği gibi örneği.</span><span class="sxs-lookup"><span data-stu-id="f1cbe-106">In C# 3.0 and later, delegates can also be declared and instantiated by using a lambda expression, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#31](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_5.cs)]  
  
 <span data-ttu-id="f1cbe-107">Daha fazla bilgi için bkz: [Lambda ifadeleri](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="f1cbe-107">For more information, see [Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="f1cbe-108">Aşağıdaki örnek, bir temsilci kullanarak bildirme ve örnek oluşturma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f1cbe-108">The following example illustrates declaring, instantiating, and using a delegate.</span></span> <span data-ttu-id="f1cbe-109">`BookDB` Sınıfı defterleri bir veritabanının bakımını yapan bir kitap veritabanı yalıtır.</span><span class="sxs-lookup"><span data-stu-id="f1cbe-109">The `BookDB` class encapsulates a bookstore database that maintains a database of books.</span></span> <span data-ttu-id="f1cbe-110">Bir yöntemi gösterir `ProcessPaperbackBooks`, veritabanında defterleri, tüm paperback bulur ve her biri için bir temsilcisini çağırır.</span><span class="sxs-lookup"><span data-stu-id="f1cbe-110">It exposes a method, `ProcessPaperbackBooks`, which finds all paperback books in the database and calls a delegate for each one.</span></span> <span data-ttu-id="f1cbe-111">`delegate` Kullanılan türünü adlandırılan `ProcessBookDelegate`.</span><span class="sxs-lookup"><span data-stu-id="f1cbe-111">The `delegate` type that is used is named `ProcessBookDelegate`.</span></span> <span data-ttu-id="f1cbe-112">`Test` Sınıfı başlıklarını ve ortalama fiyat kitapçığın defterlerinden yazdırmak için bu sınıfı kullanır.</span><span class="sxs-lookup"><span data-stu-id="f1cbe-112">The `Test` class uses this class to print the titles and average price of the paperback books.</span></span>  
  
 <span data-ttu-id="f1cbe-113">Temsilciler kullanımını işlevselliği kitap veritabanı ve istemci kodu arasında iyi ayrılması yükseltir.</span><span class="sxs-lookup"><span data-stu-id="f1cbe-113">The use of delegates promotes good separation of functionality between the bookstore database and the client code.</span></span> <span data-ttu-id="f1cbe-114">İstemci kodu books nasıl depolandığını veya Kitap kod kitapçığın books nasıl bulacağını olanağıyla sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f1cbe-114">The client code has no knowledge of how the books are stored or how the bookstore code finds paperback books.</span></span> <span data-ttu-id="f1cbe-115">Kitap kod bunları bulduktan sonra hangi işleme kitapçığın books üzerinde gerçekleştirilir hiçbir bilgiye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f1cbe-115">The bookstore code has no knowledge of what processing is performed on the paperback books after it finds them.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1cbe-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="f1cbe-116">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#12](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_6.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="f1cbe-117">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="f1cbe-117">Robust Programming</span></span>  
  
-   <span data-ttu-id="f1cbe-118">Bir temsilci bildirme.</span><span class="sxs-lookup"><span data-stu-id="f1cbe-118">Declaring a delegate.</span></span>  
  
     <span data-ttu-id="f1cbe-119">Aşağıdaki ifade, yeni bir temsilci türü bildirir.</span><span class="sxs-lookup"><span data-stu-id="f1cbe-119">The following statement declares a new delegate type.</span></span>  
  
     [!code-csharp[csProgGuideDelegates#16](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_7.cs)]  
  
     <span data-ttu-id="f1cbe-120">Her bir temsilci türü sayısı ve bağımsız değişken türleri ve onu sarmalayabilen yöntemleri dönüş değerini türünü açıklar.</span><span class="sxs-lookup"><span data-stu-id="f1cbe-120">Each delegate type describes the number and types of the arguments, and the type of the return value of methods that it can encapsulate.</span></span> <span data-ttu-id="f1cbe-121">Yeni bir bağımsız değişken türleri veya dönüş değeri türü kümesi gerektiğinde yeni bir temsilci türü bildirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f1cbe-121">Whenever a new set of argument types or return value type is needed, a new delegate type must be declared.</span></span>  
  
-   <span data-ttu-id="f1cbe-122">Bir temsilci örnekleme.</span><span class="sxs-lookup"><span data-stu-id="f1cbe-122">Instantiating a delegate.</span></span>  
  
     <span data-ttu-id="f1cbe-123">Bir temsilci türü bildirildikten sonra bir temsilci nesnesi oluşturulabilir ve belirli bir yöntem ile ilişkilendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="f1cbe-123">After a delegate type has been declared, a delegate object must be created and associated with a particular method.</span></span> <span data-ttu-id="f1cbe-124">Önceki örnekte geçirerek bunu `PrintTitle` yönteme `ProcessPaperbackBooks` yöntem aşağıdaki örnekteki gibi:</span><span class="sxs-lookup"><span data-stu-id="f1cbe-124">In the previous example, you do this by passing the `PrintTitle` method to the `ProcessPaperbackBooks` method as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#17](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_8.cs)]  
  
     <span data-ttu-id="f1cbe-125">Bu ile ilişkili yeni bir temsilci nesnesi oluşturur [statik](../../../csharp/language-reference/keywords/static.md) yöntemi `Test.PrintTitle`.</span><span class="sxs-lookup"><span data-stu-id="f1cbe-125">This creates a new delegate object associated with the [static](../../../csharp/language-reference/keywords/static.md) method `Test.PrintTitle`.</span></span> <span data-ttu-id="f1cbe-126">Benzer şekilde, statik olmayan yöntemi `AddBookToTotal` nesne üzerinde `totaller` aşağıdaki örnekteki geçirilir:</span><span class="sxs-lookup"><span data-stu-id="f1cbe-126">Similarly, the non-static method `AddBookToTotal` on the object `totaller` is passed as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#18](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_9.cs)]  
  
     <span data-ttu-id="f1cbe-127">Yeni bir temsilci nesnesi geçirilir her iki durumda da `ProcessPaperbackBooks` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f1cbe-127">In both cases a new delegate object is passed to the `ProcessPaperbackBooks` method.</span></span>  
  
     <span data-ttu-id="f1cbe-128">Bir temsilci oluşturulduktan sonra, hiçbir zaman değişikliklerle ilişkili yöntemdir; temsilci nesneleri değişmez.</span><span class="sxs-lookup"><span data-stu-id="f1cbe-128">After a delegate is created, the method it is associated with never changes; delegate objects are immutable.</span></span>  
  
-   <span data-ttu-id="f1cbe-129">Bir temsilci çağrılıyor.</span><span class="sxs-lookup"><span data-stu-id="f1cbe-129">Calling a delegate.</span></span>  
  
     <span data-ttu-id="f1cbe-130">Temsilci nesne oluşturulduktan sonra temsilci nesnesini genellikle temsilci çağıracak diğer kod geçirilir.</span><span class="sxs-lookup"><span data-stu-id="f1cbe-130">After a delegate object is created, the delegate object is typically passed to other code that will call the delegate.</span></span> <span data-ttu-id="f1cbe-131">Temsilci nesnesini, temsilciye geçirilecek parantez içine alınmış bağımsız değişkenler ve ardından temsilci nesnesinin adı kullanılarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f1cbe-131">A delegate object is called by using the name of the delegate object, followed by the parenthesized arguments to be passed to the delegate.</span></span> <span data-ttu-id="f1cbe-132">Aşağıda, bir temsilci çağrı örneğidir:</span><span class="sxs-lookup"><span data-stu-id="f1cbe-132">Following is an example of a delegate call:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#19](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_10.cs)]  
  
     <span data-ttu-id="f1cbe-133">Bir temsilci ya da zaman uyumlu olarak, bu örnekte olduğu gibi veya zaman uyumsuz olarak kullanarak çağrılabilir `BeginInvoke` ve `EndInvoke` yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="f1cbe-133">A delegate can be either called synchronously, as in this example, or asynchronously by using `BeginInvoke` and `EndInvoke` methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1cbe-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f1cbe-134">See Also</span></span>  
 [<span data-ttu-id="f1cbe-135">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f1cbe-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f1cbe-136">Olayları</span><span class="sxs-lookup"><span data-stu-id="f1cbe-136">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
 [<span data-ttu-id="f1cbe-137">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="f1cbe-137">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
