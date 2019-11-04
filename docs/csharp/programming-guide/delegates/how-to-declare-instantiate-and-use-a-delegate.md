---
title: 'Nasıl yapılır: temsilci C# programlama kılavuzunu bildirme, oluşturma ve kullanma'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], declaring and instantiating
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
ms.openlocfilehash: bd3d80023f6cb382f057e976dba01daf5e28db50
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423316"
---
# <a name="how-to-declare-instantiate-and-use-a-delegate-c-programming-guide"></a><span data-ttu-id="41a94-102">Nasıl yapılır: Temsilci Bildirme, Oluşturma ve Kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="41a94-102">How to: Declare, Instantiate, and Use a Delegate (C# Programming Guide)</span></span>
<span data-ttu-id="41a94-103">C# 1,0 ve sonraki sürümlerde, temsilciler aşağıdaki örnekte gösterildiği gibi bildirilebilecek.</span><span class="sxs-lookup"><span data-stu-id="41a94-103">In C# 1.0 and later, delegates can be declared as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#13)]  
  
 [!code-csharp[csProgGuideDelegates#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#14)]  
  
 <span data-ttu-id="41a94-104">C#2,0, aşağıdaki örnekte gösterildiği gibi önceki bildirimi yazmak için daha basit bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="41a94-104">C# 2.0 provides a simpler way to write the previous declaration, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#32)]  
  
 <span data-ttu-id="41a94-105">C# 2,0 ve sonraki sürümlerde, aşağıdaki örnekte gösterildiği gibi bir [temsilciyi](../../language-reference/builtin-types/reference-types.md)bildirmek ve başlatmak için anonim bir yöntem kullanmak da mümkündür.</span><span class="sxs-lookup"><span data-stu-id="41a94-105">In C# 2.0 and later, it is also possible to use an anonymous method to declare and initialize a [delegate](../../language-reference/builtin-types/reference-types.md), as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#15)]  
  
 <span data-ttu-id="41a94-106">C# 3,0 ve sonraki sürümlerde temsilciler, aşağıdaki örnekte gösterildiği gibi bir lambda ifadesi kullanılarak da bildirilebilecek ve örneklenebilir.</span><span class="sxs-lookup"><span data-stu-id="41a94-106">In C# 3.0 and later, delegates can also be declared and instantiated by using a lambda expression, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#31)]  
  
 <span data-ttu-id="41a94-107">Daha fazla bilgi için bkz. [lambda ifadeleri](../statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="41a94-107">For more information, see [Lambda Expressions](../statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="41a94-108">Aşağıdaki örnek, bir temsilciyi bildirme, örneklendirme ve kullanma hakkında gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="41a94-108">The following example illustrates declaring, instantiating, and using a delegate.</span></span> <span data-ttu-id="41a94-109">`BookDB` sınıfı, kitap veritabanını tutan bir kitaplığı veritabanını kapsüller.</span><span class="sxs-lookup"><span data-stu-id="41a94-109">The `BookDB` class encapsulates a bookstore database that maintains a database of books.</span></span> <span data-ttu-id="41a94-110">Bu, veritabanındaki tüm kağıt geri kitaplarını bulan ve her biri için bir temsilci çağıran `ProcessPaperbackBooks`bir yöntem sunar.</span><span class="sxs-lookup"><span data-stu-id="41a94-110">It exposes a method, `ProcessPaperbackBooks`, which finds all paperback books in the database and calls a delegate for each one.</span></span> <span data-ttu-id="41a94-111">Kullanılan `delegate` türü `ProcessBookDelegate`olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="41a94-111">The `delegate` type that is used is named `ProcessBookDelegate`.</span></span> <span data-ttu-id="41a94-112">`Test` sınıfı, Paperback kitaplarının başlıklarını ve ortalama fiyatını yazdırmak için bu sınıfı kullanır.</span><span class="sxs-lookup"><span data-stu-id="41a94-112">The `Test` class uses this class to print the titles and average price of the paperback books.</span></span>  
  
 <span data-ttu-id="41a94-113">Temsilcilerin kullanımı, kitaplığı veritabanı ve istemci kodu arasındaki işlevlerin iyi bir şekilde ayrılmasını yükseltir.</span><span class="sxs-lookup"><span data-stu-id="41a94-113">The use of delegates promotes good separation of functionality between the bookstore database and the client code.</span></span> <span data-ttu-id="41a94-114">İstemci kodu kitaplarının nasıl depolandığını veya kitaplığı kodunun kağıt geri defterlerini nasıl bulduğunu bilmiştir.</span><span class="sxs-lookup"><span data-stu-id="41a94-114">The client code has no knowledge of how the books are stored or how the bookstore code finds paperback books.</span></span> <span data-ttu-id="41a94-115">Kitaplığı kodu, her şeyi bulduktan sonra, kağıt geri defterlerinde gerçekleştirilen işleme ilişkin hiçbir bilgiye sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="41a94-115">The bookstore code has no knowledge of what processing is performed on the paperback books after it finds them.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41a94-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="41a94-116">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#12)]  
  
## <a name="robust-programming"></a><span data-ttu-id="41a94-117">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="41a94-117">Robust Programming</span></span>  
  
- <span data-ttu-id="41a94-118">Temsilci bildirme.</span><span class="sxs-lookup"><span data-stu-id="41a94-118">Declaring a delegate.</span></span>  
  
     <span data-ttu-id="41a94-119">Aşağıdaki ifade yeni bir temsilci türü bildirir.</span><span class="sxs-lookup"><span data-stu-id="41a94-119">The following statement declares a new delegate type.</span></span>  
  
     [!code-csharp[csProgGuideDelegates#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#16)]  
  
     <span data-ttu-id="41a94-120">Her temsilci türü, bağımsız değişkenlerin sayısını ve türlerini ve kapsülleyeşabolduğu yöntemlerin dönüş değeri türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="41a94-120">Each delegate type describes the number and types of the arguments, and the type of the return value of methods that it can encapsulate.</span></span> <span data-ttu-id="41a94-121">Bağımsız değişken türlerinin veya dönüş değeri türünün her yeni kümesi gerektiğinde, yeni bir temsilci türü bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="41a94-121">Whenever a new set of argument types or return value type is needed, a new delegate type must be declared.</span></span>  
  
- <span data-ttu-id="41a94-122">Bir temsilciyi örnekleme.</span><span class="sxs-lookup"><span data-stu-id="41a94-122">Instantiating a delegate.</span></span>  
  
     <span data-ttu-id="41a94-123">Bir temsilci türü bildirildiğinde, bir temsilci nesnesi oluşturulmalı ve belirli bir yöntemle ilişkilendirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="41a94-123">After a delegate type has been declared, a delegate object must be created and associated with a particular method.</span></span> <span data-ttu-id="41a94-124">Önceki örnekte, aşağıdaki örnekte olduğu gibi `PrintTitle` yöntemini `ProcessPaperbackBooks` yöntemine geçirerek bunu yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="41a94-124">In the previous example, you do this by passing the `PrintTitle` method to the `ProcessPaperbackBooks` method as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#17)]  
  
     <span data-ttu-id="41a94-125">Bu, `Test.PrintTitle`[statik](../../language-reference/keywords/static.md) yöntemiyle ilişkili yeni bir temsilci nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="41a94-125">This creates a new delegate object associated with the [static](../../language-reference/keywords/static.md) method `Test.PrintTitle`.</span></span> <span data-ttu-id="41a94-126">Benzer şekilde, nesne `totaller` `AddBookToTotal` statik olmayan yöntem aşağıdaki örnekte olduğu gibi geçirilir:</span><span class="sxs-lookup"><span data-stu-id="41a94-126">Similarly, the non-static method `AddBookToTotal` on the object `totaller` is passed as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#18)]  
  
     <span data-ttu-id="41a94-127">Her iki durumda da `ProcessPaperbackBooks` yöntemine yeni bir temsilci nesnesi geçirilir.</span><span class="sxs-lookup"><span data-stu-id="41a94-127">In both cases a new delegate object is passed to the `ProcessPaperbackBooks` method.</span></span>  
  
     <span data-ttu-id="41a94-128">Bir temsilci oluşturulduktan sonra, ilişkili olduğu yöntem hiçbir değişiklik hiçbir şekilde değişmez; temsilci nesneleri sabittir.</span><span class="sxs-lookup"><span data-stu-id="41a94-128">After a delegate is created, the method it is associated with never changes; delegate objects are immutable.</span></span>  
  
- <span data-ttu-id="41a94-129">Temsilci çağırma.</span><span class="sxs-lookup"><span data-stu-id="41a94-129">Calling a delegate.</span></span>  
  
     <span data-ttu-id="41a94-130">Temsilci nesnesi oluşturulduktan sonra temsilci nesnesi genellikle temsilciyi çağıran diğer koda geçirilir.</span><span class="sxs-lookup"><span data-stu-id="41a94-130">After a delegate object is created, the delegate object is typically passed to other code that will call the delegate.</span></span> <span data-ttu-id="41a94-131">Temsilci nesnesi, temsilci nesnesinin adı kullanılarak çağrılır ve ardından temsilciye geçirilecek parantez içine alınmış bağımsız değişkenler gelir.</span><span class="sxs-lookup"><span data-stu-id="41a94-131">A delegate object is called by using the name of the delegate object, followed by the parenthesized arguments to be passed to the delegate.</span></span> <span data-ttu-id="41a94-132">Aşağıda bir temsilci çağrısı örneği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="41a94-132">Following is an example of a delegate call:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#19)]  
  
     <span data-ttu-id="41a94-133">Bir temsilci, bu örnekte olduğu gibi zaman uyumlu olarak ya da `BeginInvoke` ve `EndInvoke` yöntemleri kullanılarak zaman uyumsuz olarak çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="41a94-133">A delegate can be either called synchronously, as in this example, or asynchronously by using `BeginInvoke` and `EndInvoke` methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41a94-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41a94-134">See also</span></span>

- [<span data-ttu-id="41a94-135">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="41a94-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="41a94-136">Olaylar</span><span class="sxs-lookup"><span data-stu-id="41a94-136">Events</span></span>](../events/index.md)
- [<span data-ttu-id="41a94-137">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="41a94-137">Delegates</span></span>](./index.md)
