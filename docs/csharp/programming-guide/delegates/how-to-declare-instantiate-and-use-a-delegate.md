---
title: 'Nasıl yapılır: Bildirme, oluşturma ve bir temsilci - kullanın C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], declaring and instantiating
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
ms.openlocfilehash: 3e62dd4b4e1b1eb4586dcb3ce0e3f39c54a5686c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64608742"
---
# <a name="how-to-declare-instantiate-and-use-a-delegate-c-programming-guide"></a><span data-ttu-id="eb8d9-102">Nasıl yapılır: Bildirme, oluşturma ve bir temsilci kullanın (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="eb8d9-102">How to: Declare, Instantiate, and Use a Delegate (C# Programming Guide)</span></span>
<span data-ttu-id="eb8d9-103">C# 1.0 ve daha sonra aşağıdaki örnekte gösterildiği gibi temsilciler bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="eb8d9-103">In C# 1.0 and later, delegates can be declared as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#13)]  
  
 [!code-csharp[csProgGuideDelegates#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#14)]  
  
 <span data-ttu-id="eb8d9-104">C# 2.0, aşağıdaki örnekte gösterildiği gibi önceki bildirimi yazmak için daha basit bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="eb8d9-104">C# 2.0 provides a simpler way to write the previous declaration, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#32)]  
  
 <span data-ttu-id="eb8d9-105">C# 2.0 ve sonraki sürümlerinde, ayrıca bildirmek ve başlatmak için anonim bir yöntem kullanmak mümkün bir [temsilci](../../../csharp/language-reference/keywords/delegate.md)aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="eb8d9-105">In C# 2.0 and later, it is also possible to use an anonymous method to declare and initialize a [delegate](../../../csharp/language-reference/keywords/delegate.md), as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#15)]  
  
 <span data-ttu-id="eb8d9-106">C# 3.0 ve sonraki sürümlerinde, temsilciler ayrıca bildirilmiş ve bir lambda ifadesi kullanarak, aşağıdaki örnekte gösterildiği gibi örneği.</span><span class="sxs-lookup"><span data-stu-id="eb8d9-106">In C# 3.0 and later, delegates can also be declared and instantiated by using a lambda expression, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#31)]  
  
 <span data-ttu-id="eb8d9-107">Daha fazla bilgi için [Lambda ifadeleri](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="eb8d9-107">For more information, see [Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="eb8d9-108">Aşağıdaki örnek, bir temsilci kullanarak bildirme ve örnekleme gösterir.</span><span class="sxs-lookup"><span data-stu-id="eb8d9-108">The following example illustrates declaring, instantiating, and using a delegate.</span></span> <span data-ttu-id="eb8d9-109">`BookDB` Sınıfı, bir veritabanına kitap tutan bir Kitaplığı veritabanı kapsüller.</span><span class="sxs-lookup"><span data-stu-id="eb8d9-109">The `BookDB` class encapsulates a bookstore database that maintains a database of books.</span></span> <span data-ttu-id="eb8d9-110">Bir yöntem sunan `ProcessPaperbackBooks`, veritabanında kitapları ve her biri için bir temsilci çağıran, tüm alınabilen ciltsiz kitaba bulur.</span><span class="sxs-lookup"><span data-stu-id="eb8d9-110">It exposes a method, `ProcessPaperbackBooks`, which finds all paperback books in the database and calls a delegate for each one.</span></span> <span data-ttu-id="eb8d9-111">`delegate` Kullanılan türünün adı `ProcessBookDelegate`.</span><span class="sxs-lookup"><span data-stu-id="eb8d9-111">The `delegate` type that is used is named `ProcessBookDelegate`.</span></span> <span data-ttu-id="eb8d9-112">`Test` Sınıfı başlıklar ve ortalama fiyat kitapçığın kitap yazdırmak için bu sınıfı kullanır.</span><span class="sxs-lookup"><span data-stu-id="eb8d9-112">The `Test` class uses this class to print the titles and average price of the paperback books.</span></span>  
  
 <span data-ttu-id="eb8d9-113">Temsilciler kullanımını işlevselliği Kitaplığı veritabanı ve istemci kodu arasında iyi ayrımı yükseltir.</span><span class="sxs-lookup"><span data-stu-id="eb8d9-113">The use of delegates promotes good separation of functionality between the bookstore database and the client code.</span></span> <span data-ttu-id="eb8d9-114">İstemci kodu books nasıl depolandığını veya kitaplığı kod kitapçığın books nasıl bulacağını olanağıyla sahiptir.</span><span class="sxs-lookup"><span data-stu-id="eb8d9-114">The client code has no knowledge of how the books are stored or how the bookstore code finds paperback books.</span></span> <span data-ttu-id="eb8d9-115">Kitaplığı kod bunları bulduktan sonra hangi işleme kitapçığın kitaplar yapılır bilgisi var.</span><span class="sxs-lookup"><span data-stu-id="eb8d9-115">The bookstore code has no knowledge of what processing is performed on the paperback books after it finds them.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb8d9-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="eb8d9-116">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#12)]  
  
## <a name="robust-programming"></a><span data-ttu-id="eb8d9-117">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="eb8d9-117">Robust Programming</span></span>  
  
- <span data-ttu-id="eb8d9-118">Bir temsilci bildirme.</span><span class="sxs-lookup"><span data-stu-id="eb8d9-118">Declaring a delegate.</span></span>  
  
     <span data-ttu-id="eb8d9-119">Aşağıdaki deyim, yeni bir temsilci türü bildirir.</span><span class="sxs-lookup"><span data-stu-id="eb8d9-119">The following statement declares a new delegate type.</span></span>  
  
     [!code-csharp[csProgGuideDelegates#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#16)]  
  
     <span data-ttu-id="eb8d9-120">Her bir temsilci türü sayısı ve bağımsız değişken türlerinin ve onu kapsülleyen yöntemleri dönüş değerinin türünü açıklar.</span><span class="sxs-lookup"><span data-stu-id="eb8d9-120">Each delegate type describes the number and types of the arguments, and the type of the return value of methods that it can encapsulate.</span></span> <span data-ttu-id="eb8d9-121">Bağımsız değişken türleri ya da dönüş değeri yeni bir dizi gerektiğinde yeni bir temsilci türünün bildirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="eb8d9-121">Whenever a new set of argument types or return value type is needed, a new delegate type must be declared.</span></span>  
  
- <span data-ttu-id="eb8d9-122">Bir temsilci örneği.</span><span class="sxs-lookup"><span data-stu-id="eb8d9-122">Instantiating a delegate.</span></span>  
  
     <span data-ttu-id="eb8d9-123">Bir temsilci türü bildirildikten sonra bir temsilci nesnesinin oluşturulabilir ve belirli bir yöntem ile ilişkili.</span><span class="sxs-lookup"><span data-stu-id="eb8d9-123">After a delegate type has been declared, a delegate object must be created and associated with a particular method.</span></span> <span data-ttu-id="eb8d9-124">Önceki örnekte geçirerek bunu `PrintTitle` yönteme `ProcessPaperbackBooks` yöntem aşağıdaki örnekteki gibi:</span><span class="sxs-lookup"><span data-stu-id="eb8d9-124">In the previous example, you do this by passing the `PrintTitle` method to the `ProcessPaperbackBooks` method as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#17)]  
  
     <span data-ttu-id="eb8d9-125">Bu yeni bir temsilci nesnesi ile ilişkili oluşturur [statik](../../../csharp/language-reference/keywords/static.md) yöntemi `Test.PrintTitle`.</span><span class="sxs-lookup"><span data-stu-id="eb8d9-125">This creates a new delegate object associated with the [static](../../../csharp/language-reference/keywords/static.md) method `Test.PrintTitle`.</span></span> <span data-ttu-id="eb8d9-126">Benzer şekilde, statik olmayan yöntemi `AddBookToTotal` nesnesindeki `totaller` aşağıdaki örnekte olduğu gibi geçirilir:</span><span class="sxs-lookup"><span data-stu-id="eb8d9-126">Similarly, the non-static method `AddBookToTotal` on the object `totaller` is passed as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#18)]  
  
     <span data-ttu-id="eb8d9-127">Her iki durumda da yeni bir temsilci nesnesi için geçirilen `ProcessPaperbackBooks` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="eb8d9-127">In both cases a new delegate object is passed to the `ProcessPaperbackBooks` method.</span></span>  
  
     <span data-ttu-id="eb8d9-128">Yöntemi daha temsilci oluşturduktan sonra bile asla değişikliklerle ilişkili; temsilci nesneleri sabittir.</span><span class="sxs-lookup"><span data-stu-id="eb8d9-128">After a delegate is created, the method it is associated with never changes; delegate objects are immutable.</span></span>  
  
- <span data-ttu-id="eb8d9-129">Bir temsilci çağırma.</span><span class="sxs-lookup"><span data-stu-id="eb8d9-129">Calling a delegate.</span></span>  
  
     <span data-ttu-id="eb8d9-130">Bir temsilci nesne oluşturulduktan sonra temsilci nesne temsilci çağıran başka bir kod için genellikle geçirilir.</span><span class="sxs-lookup"><span data-stu-id="eb8d9-130">After a delegate object is created, the delegate object is typically passed to other code that will call the delegate.</span></span> <span data-ttu-id="eb8d9-131">Bir temsilci nesnesinin temsilciye geçirilecek parantez içine alınmış bağımsız değişkenleri ardından temsilci nesnesinin adı kullanılarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="eb8d9-131">A delegate object is called by using the name of the delegate object, followed by the parenthesized arguments to be passed to the delegate.</span></span> <span data-ttu-id="eb8d9-132">Bir temsilci çağrısının bir örneği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="eb8d9-132">Following is an example of a delegate call:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#19)]  
  
     <span data-ttu-id="eb8d9-133">Bir temsilci ya da zaman uyumlu olarak, bu örnekte olduğu gibi veya zaman uyumsuz olarak kullanarak çağrılabilir `BeginInvoke` ve `EndInvoke` yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="eb8d9-133">A delegate can be either called synchronously, as in this example, or asynchronously by using `BeginInvoke` and `EndInvoke` methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb8d9-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb8d9-134">See also</span></span>

- [<span data-ttu-id="eb8d9-135">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="eb8d9-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="eb8d9-136">Olaylar</span><span class="sxs-lookup"><span data-stu-id="eb8d9-136">Events</span></span>](../../../csharp/programming-guide/events/index.md)
- [<span data-ttu-id="eb8d9-137">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="eb8d9-137">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
