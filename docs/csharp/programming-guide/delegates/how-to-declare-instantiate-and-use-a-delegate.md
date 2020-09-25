---
title: Bir temsilciyi bildirme, oluşturma ve kullanma-C# Programlama Kılavuzu
description: Bir temsilciyi bildirme, oluşturma ve kullanma hakkında bilgi edinin. C# 1,0, 2,0 ve 3,0 ve üstünü kapsayan örneklere bakın.
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], declaring and instantiating
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
ms.openlocfilehash: 83dbd2dc497fafaf1922f8ad53208d0ab14f14a9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185905"
---
# <a name="how-to-declare-instantiate-and-use-a-delegate-c-programming-guide"></a><span data-ttu-id="768ea-104">Bir temsilciyi bildirme, oluşturma ve kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="768ea-104">How to declare, instantiate, and use a Delegate (C# Programming Guide)</span></span>

<span data-ttu-id="768ea-105">C# 1,0 ve üzeri sürümlerde, temsilciler aşağıdaki örnekte gösterildiği gibi bildirilebilecek.</span><span class="sxs-lookup"><span data-stu-id="768ea-105">In C# 1.0 and later, delegates can be declared as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#13)]  
  
 [!code-csharp[csProgGuideDelegates#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#14)]  
  
 <span data-ttu-id="768ea-106">C# 2,0, aşağıdaki örnekte gösterildiği gibi önceki bildirimi yazmak için daha basit bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="768ea-106">C# 2.0 provides a simpler way to write the previous declaration, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#32)]  
  
 <span data-ttu-id="768ea-107">C# 2,0 ve üzeri sürümlerde, aşağıdaki örnekte gösterildiği gibi bir [temsilciyi](../../language-reference/builtin-types/reference-types.md)bildirmek ve başlatmak için anonim bir yöntem kullanmak da mümkündür.</span><span class="sxs-lookup"><span data-stu-id="768ea-107">In C# 2.0 and later, it is also possible to use an anonymous method to declare and initialize a [delegate](../../language-reference/builtin-types/reference-types.md), as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#15)]  
  
 <span data-ttu-id="768ea-108">C# 3,0 ve üzeri sürümlerde temsilciler, aşağıdaki örnekte gösterildiği gibi bir lambda ifadesi kullanılarak da bildirilebilecek ve örneklenebilir.</span><span class="sxs-lookup"><span data-stu-id="768ea-108">In C# 3.0 and later, delegates can also be declared and instantiated by using a lambda expression, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#31)]  
  
 <span data-ttu-id="768ea-109">Daha fazla bilgi için bkz. [lambda ifadeleri](../../language-reference/operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="768ea-109">For more information, see [Lambda Expressions](../../language-reference/operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="768ea-110">Aşağıdaki örnek, bir temsilciyi bildirme, örneklendirme ve kullanma hakkında gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="768ea-110">The following example illustrates declaring, instantiating, and using a delegate.</span></span> <span data-ttu-id="768ea-111">`BookDB`Sınıfı, kitap veritabanını tutan bir kitaplığı veritabanını kapsüller.</span><span class="sxs-lookup"><span data-stu-id="768ea-111">The `BookDB` class encapsulates a bookstore database that maintains a database of books.</span></span> <span data-ttu-id="768ea-112">Bu, `ProcessPaperbackBooks` veritabanındaki tüm kağıt geri kitaplarını bulan ve her biri için bir temsilci çağıran bir yöntemi sunar.</span><span class="sxs-lookup"><span data-stu-id="768ea-112">It exposes a method, `ProcessPaperbackBooks`, which finds all paperback books in the database and calls a delegate for each one.</span></span> <span data-ttu-id="768ea-113">`delegate`Kullanılan tür adı `ProcessBookDelegate` .</span><span class="sxs-lookup"><span data-stu-id="768ea-113">The `delegate` type that is used is named `ProcessBookDelegate`.</span></span> <span data-ttu-id="768ea-114">`Test`Sınıfı, Paperback kitaplarının başlıklarını ve ortalama fiyatını yazdırmak için bu sınıfı kullanır.</span><span class="sxs-lookup"><span data-stu-id="768ea-114">The `Test` class uses this class to print the titles and average price of the paperback books.</span></span>  
  
 <span data-ttu-id="768ea-115">Temsilcilerin kullanımı, kitaplığı veritabanı ve istemci kodu arasındaki işlevlerin iyi bir şekilde ayrılmasını yükseltir.</span><span class="sxs-lookup"><span data-stu-id="768ea-115">The use of delegates promotes good separation of functionality between the bookstore database and the client code.</span></span> <span data-ttu-id="768ea-116">İstemci kodu kitaplarının nasıl depolandığını veya kitaplığı kodunun kağıt geri defterlerini nasıl bulduğunu bilmiştir.</span><span class="sxs-lookup"><span data-stu-id="768ea-116">The client code has no knowledge of how the books are stored or how the bookstore code finds paperback books.</span></span> <span data-ttu-id="768ea-117">Kitaplığı kodu, her şeyi bulduktan sonra, kağıt geri defterlerinde gerçekleştirilen işleme ilişkin hiçbir bilgiye sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="768ea-117">The bookstore code has no knowledge of what processing is performed on the paperback books after it finds them.</span></span>  
  
## <a name="example"></a><span data-ttu-id="768ea-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="768ea-118">Example</span></span>  

 [!code-csharp[csProgGuideDelegates#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#12)]  
  
## <a name="robust-programming"></a><span data-ttu-id="768ea-119">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="768ea-119">Robust Programming</span></span>  
  
- <span data-ttu-id="768ea-120">Temsilci bildirme.</span><span class="sxs-lookup"><span data-stu-id="768ea-120">Declaring a delegate.</span></span>  
  
     <span data-ttu-id="768ea-121">Aşağıdaki ifade yeni bir temsilci türü bildirir.</span><span class="sxs-lookup"><span data-stu-id="768ea-121">The following statement declares a new delegate type.</span></span>  
  
     [!code-csharp[csProgGuideDelegates#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#16)]  
  
     <span data-ttu-id="768ea-122">Her temsilci türü, bağımsız değişkenlerin sayısını ve türlerini ve kapsülleyeşabolduğu yöntemlerin dönüş değeri türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="768ea-122">Each delegate type describes the number and types of the arguments, and the type of the return value of methods that it can encapsulate.</span></span> <span data-ttu-id="768ea-123">Bağımsız değişken türlerinin veya dönüş değeri türünün her yeni kümesi gerektiğinde, yeni bir temsilci türü bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="768ea-123">Whenever a new set of argument types or return value type is needed, a new delegate type must be declared.</span></span>  
  
- <span data-ttu-id="768ea-124">Bir temsilciyi örnekleme.</span><span class="sxs-lookup"><span data-stu-id="768ea-124">Instantiating a delegate.</span></span>  
  
     <span data-ttu-id="768ea-125">Bir temsilci türü bildirildiğinde, bir temsilci nesnesi oluşturulmalı ve belirli bir yöntemle ilişkilendirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="768ea-125">After a delegate type has been declared, a delegate object must be created and associated with a particular method.</span></span> <span data-ttu-id="768ea-126">Önceki örnekte, `PrintTitle` `ProcessPaperbackBooks` Aşağıdaki örnekte olduğu gibi yöntemini yöntemine geçirerek bunu yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="768ea-126">In the previous example, you do this by passing the `PrintTitle` method to the `ProcessPaperbackBooks` method as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#17)]  
  
     <span data-ttu-id="768ea-127">Bu, [statik](../../language-reference/keywords/static.md) yöntemle ilişkili yeni bir temsilci nesnesi oluşturur `Test.PrintTitle` .</span><span class="sxs-lookup"><span data-stu-id="768ea-127">This creates a new delegate object associated with the [static](../../language-reference/keywords/static.md) method `Test.PrintTitle`.</span></span> <span data-ttu-id="768ea-128">Benzer şekilde, nesne üzerindeki statik olmayan yöntem `AddBookToTotal` `totaller` Aşağıdaki örnekte olduğu gibi geçirilir:</span><span class="sxs-lookup"><span data-stu-id="768ea-128">Similarly, the non-static method `AddBookToTotal` on the object `totaller` is passed as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#18)]  
  
     <span data-ttu-id="768ea-129">Her iki durumda da yöntemine yeni bir temsilci nesnesi geçirilir `ProcessPaperbackBooks` .</span><span class="sxs-lookup"><span data-stu-id="768ea-129">In both cases a new delegate object is passed to the `ProcessPaperbackBooks` method.</span></span>  
  
     <span data-ttu-id="768ea-130">Bir temsilci oluşturulduktan sonra, ilişkili olduğu yöntem hiçbir değişiklik hiçbir şekilde değişmez; temsilci nesneleri sabittir.</span><span class="sxs-lookup"><span data-stu-id="768ea-130">After a delegate is created, the method it is associated with never changes; delegate objects are immutable.</span></span>  
  
- <span data-ttu-id="768ea-131">Temsilci çağırma.</span><span class="sxs-lookup"><span data-stu-id="768ea-131">Calling a delegate.</span></span>  
  
     <span data-ttu-id="768ea-132">Temsilci nesnesi oluşturulduktan sonra temsilci nesnesi genellikle temsilciyi çağıran diğer koda geçirilir.</span><span class="sxs-lookup"><span data-stu-id="768ea-132">After a delegate object is created, the delegate object is typically passed to other code that will call the delegate.</span></span> <span data-ttu-id="768ea-133">Temsilci nesnesi, temsilci nesnesinin adı kullanılarak çağrılır ve ardından temsilciye geçirilecek parantez içine alınmış bağımsız değişkenler gelir.</span><span class="sxs-lookup"><span data-stu-id="768ea-133">A delegate object is called by using the name of the delegate object, followed by the parenthesized arguments to be passed to the delegate.</span></span> <span data-ttu-id="768ea-134">Aşağıda bir temsilci çağrısı örneği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="768ea-134">Following is an example of a delegate call:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#19)]  
  
     <span data-ttu-id="768ea-135">Bir temsilci, bu örnekte olduğu gibi zaman uyumlu olarak ya da ve yöntemleri kullanılarak zaman uyumsuz olarak çağrılabilir `BeginInvoke` `EndInvoke` .</span><span class="sxs-lookup"><span data-stu-id="768ea-135">A delegate can be either called synchronously, as in this example, or asynchronously by using `BeginInvoke` and `EndInvoke` methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="768ea-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="768ea-136">See also</span></span>

- [<span data-ttu-id="768ea-137">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="768ea-137">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="768ea-138">Olaylar</span><span class="sxs-lookup"><span data-stu-id="768ea-138">Events</span></span>](../events/index.md)
- [<span data-ttu-id="768ea-139">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="768ea-139">Delegates</span></span>](./index.md)
