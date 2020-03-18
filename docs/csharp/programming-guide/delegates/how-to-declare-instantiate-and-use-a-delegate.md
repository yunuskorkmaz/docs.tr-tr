---
title: Nasıl beyan, anlık ve bir temsilci kullanmak - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], declaring and instantiating
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
ms.openlocfilehash: 7ac1d736e19c4dcf1c8408db944505c399762778
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712370"
---
# <a name="how-to-declare-instantiate-and-use-a-delegate-c-programming-guide"></a><span data-ttu-id="56e5f-102">Temsilci (C# Programlama Kılavuzu) nasıl beyan edilir, anlık olarak kullanılır ve kullanılır?</span><span class="sxs-lookup"><span data-stu-id="56e5f-102">How to declare, instantiate, and use a Delegate (C# Programming Guide)</span></span>
<span data-ttu-id="56e5f-103">C# 1.0 ve sonraki durumlarda, delegeler aşağıdaki örnekte gösterildiği gibi bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="56e5f-103">In C# 1.0 and later, delegates can be declared as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#13)]  
  
 [!code-csharp[csProgGuideDelegates#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#14)]  
  
 <span data-ttu-id="56e5f-104">C# 2.0, aşağıdaki örnekte gösterildiği gibi önceki bildirimi yazmak için daha basit bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="56e5f-104">C# 2.0 provides a simpler way to write the previous declaration, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#32)]  
  
 <span data-ttu-id="56e5f-105">C# 2.0 ve sonraki durumlarda, aşağıdaki örnekte gösterildiği gibi, bir [temsilciyi](../../language-reference/builtin-types/reference-types.md)bildirmek ve başlatmak için anonim bir yöntem kullanmak da mümkündür.</span><span class="sxs-lookup"><span data-stu-id="56e5f-105">In C# 2.0 and later, it is also possible to use an anonymous method to declare and initialize a [delegate](../../language-reference/builtin-types/reference-types.md), as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#15)]  
  
 <span data-ttu-id="56e5f-106">C# 3.0 ve sonraki durumlarda, aşağıdaki örnekte gösterildiği gibi, bir lambda ifadesi kullanılarak delegeler de beyan edilebilir ve anında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="56e5f-106">In C# 3.0 and later, delegates can also be declared and instantiated by using a lambda expression, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#31)]  
  
 <span data-ttu-id="56e5f-107">Daha fazla bilgi için [Lambda İfadeleri'ne](../statements-expressions-operators/lambda-expressions.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="56e5f-107">For more information, see [Lambda Expressions](../statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="56e5f-108">Aşağıdaki örnek, bir temsilciyi bildirmeyi, anlık olarak ve kullanmayı göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="56e5f-108">The following example illustrates declaring, instantiating, and using a delegate.</span></span> <span data-ttu-id="56e5f-109">Sınıf, `BookDB` kitap veritabanını koruyan bir kitapçı veritabanını kapsüller.</span><span class="sxs-lookup"><span data-stu-id="56e5f-109">The `BookDB` class encapsulates a bookstore database that maintains a database of books.</span></span> <span data-ttu-id="56e5f-110">Veritabanındaki tüm ciltsiz kitapları bulan ve her biri için bir temsilci çağıran bir yöntem `ProcessPaperbackBooks`ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="56e5f-110">It exposes a method, `ProcessPaperbackBooks`, which finds all paperback books in the database and calls a delegate for each one.</span></span> <span data-ttu-id="56e5f-111">Kullanılan `delegate` türe ". `ProcessBookDelegate`</span><span class="sxs-lookup"><span data-stu-id="56e5f-111">The `delegate` type that is used is named `ProcessBookDelegate`.</span></span> <span data-ttu-id="56e5f-112">Sınıf, `Test` ciltsiz kitapların başlıklarını ve ortalama fiyatını yazdırmak için bu sınıfı kullanır.</span><span class="sxs-lookup"><span data-stu-id="56e5f-112">The `Test` class uses this class to print the titles and average price of the paperback books.</span></span>  
  
 <span data-ttu-id="56e5f-113">Temsilcilerin kullanımı, kitapçı veritabanı ile istemci kodu arasında işlevselliğin iyi bir şekilde ayrılmasını teşvik eder.</span><span class="sxs-lookup"><span data-stu-id="56e5f-113">The use of delegates promotes good separation of functionality between the bookstore database and the client code.</span></span> <span data-ttu-id="56e5f-114">İstemci kodu, kitapların nasıl depolanır veya kitapçı kodunun ciltsiz kitapları nasıl bulduğu hakkında hiçbir bilgiye sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="56e5f-114">The client code has no knowledge of how the books are stored or how the bookstore code finds paperback books.</span></span> <span data-ttu-id="56e5f-115">Kitapçı kodunun, ciltsiz kitaplarda hangi işlemlerin yapıldığına dair hiçbir bilgisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="56e5f-115">The bookstore code has no knowledge of what processing is performed on the paperback books after it finds them.</span></span>  
  
## <a name="example"></a><span data-ttu-id="56e5f-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="56e5f-116">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#12)]  
  
## <a name="robust-programming"></a><span data-ttu-id="56e5f-117">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="56e5f-117">Robust Programming</span></span>  
  
- <span data-ttu-id="56e5f-118">Bir delege ilan etmek.</span><span class="sxs-lookup"><span data-stu-id="56e5f-118">Declaring a delegate.</span></span>  
  
     <span data-ttu-id="56e5f-119">Aşağıdaki deyimde yeni bir temsilci türü beyan eder.</span><span class="sxs-lookup"><span data-stu-id="56e5f-119">The following statement declares a new delegate type.</span></span>  
  
     [!code-csharp[csProgGuideDelegates#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#16)]  
  
     <span data-ttu-id="56e5f-120">Her temsilci türü, bağımsız değişkenlerin sayısını ve türlerini ve kapsülleebileceği yöntemlerin dönüş değerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="56e5f-120">Each delegate type describes the number and types of the arguments, and the type of the return value of methods that it can encapsulate.</span></span> <span data-ttu-id="56e5f-121">Yeni bir bağımsız değişken türü kümesi veya iade değeri türü gerektiğinde, yeni bir temsilci türü bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="56e5f-121">Whenever a new set of argument types or return value type is needed, a new delegate type must be declared.</span></span>  
  
- <span data-ttu-id="56e5f-122">Bir temsilciyi anında.</span><span class="sxs-lookup"><span data-stu-id="56e5f-122">Instantiating a delegate.</span></span>  
  
     <span data-ttu-id="56e5f-123">Bir temsilci türü seçildikten sonra, bir temsilci nesnesi oluşturulmalı ve belirli bir yöntemle ilişkilendirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="56e5f-123">After a delegate type has been declared, a delegate object must be created and associated with a particular method.</span></span> <span data-ttu-id="56e5f-124">Önceki örnekte, `PrintTitle` yöntemi aşağıdaki örnekte olduğu `ProcessPaperbackBooks` gibi yönteme geçirerek bunu yaparsınız:</span><span class="sxs-lookup"><span data-stu-id="56e5f-124">In the previous example, you do this by passing the `PrintTitle` method to the `ProcessPaperbackBooks` method as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#17)]  
  
     <span data-ttu-id="56e5f-125">Bu [statik](../../language-reference/keywords/static.md) yöntemle `Test.PrintTitle`ilişkili yeni bir temsilci nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="56e5f-125">This creates a new delegate object associated with the [static](../../language-reference/keywords/static.md) method `Test.PrintTitle`.</span></span> <span data-ttu-id="56e5f-126">Benzer şekilde, nesne `AddBookToTotal` `totaller` üzerindeki statik olmayan yöntem aşağıdaki örnekte olduğu gibi geçirilir:</span><span class="sxs-lookup"><span data-stu-id="56e5f-126">Similarly, the non-static method `AddBookToTotal` on the object `totaller` is passed as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#18)]  
  
     <span data-ttu-id="56e5f-127">Her iki durumda da yönteme `ProcessPaperbackBooks` yeni bir temsilci nesnesi geçirilir.</span><span class="sxs-lookup"><span data-stu-id="56e5f-127">In both cases a new delegate object is passed to the `ProcessPaperbackBooks` method.</span></span>  
  
     <span data-ttu-id="56e5f-128">Bir temsilci oluşturulduktan sonra, ilişkili yöntem asla değişmez; temsilci nesneleri değişmez.</span><span class="sxs-lookup"><span data-stu-id="56e5f-128">After a delegate is created, the method it is associated with never changes; delegate objects are immutable.</span></span>  
  
- <span data-ttu-id="56e5f-129">Bir temsilci çağırıyorum.</span><span class="sxs-lookup"><span data-stu-id="56e5f-129">Calling a delegate.</span></span>  
  
     <span data-ttu-id="56e5f-130">Bir temsilci nesnesi oluşturulduktan sonra, temsilci nesnesi genellikle temsilciçağıracak diğer koda geçirilir.</span><span class="sxs-lookup"><span data-stu-id="56e5f-130">After a delegate object is created, the delegate object is typically passed to other code that will call the delegate.</span></span> <span data-ttu-id="56e5f-131">Bir temsilci nesnesi, temsilci nesnesinin adı kullanılarak çağrılır ve ardından temsilciye geçirilecek parantez içinde bağımsız değişkenler yer eder.</span><span class="sxs-lookup"><span data-stu-id="56e5f-131">A delegate object is called by using the name of the delegate object, followed by the parenthesized arguments to be passed to the delegate.</span></span> <span data-ttu-id="56e5f-132">Aşağıda bir temsilci çağrısı örneği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="56e5f-132">Following is an example of a delegate call:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#19)]  
  
     <span data-ttu-id="56e5f-133">Bir temsilci, bu örnekte olduğu gibi eşzamanlı olarak veya kullanarak `BeginInvoke` ve `EndInvoke` yöntemlerle eşzamanlı olarak çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="56e5f-133">A delegate can be either called synchronously, as in this example, or asynchronously by using `BeginInvoke` and `EndInvoke` methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56e5f-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56e5f-134">See also</span></span>

- [<span data-ttu-id="56e5f-135">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="56e5f-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="56e5f-136">Olaylar</span><span class="sxs-lookup"><span data-stu-id="56e5f-136">Events</span></span>](../events/index.md)
- [<span data-ttu-id="56e5f-137">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="56e5f-137">Delegates</span></span>](./index.md)
