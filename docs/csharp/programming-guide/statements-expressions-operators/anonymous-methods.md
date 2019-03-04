---
title: Anonim yöntemler - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous methods [C#]
- methods [C#], anonymous
- delegates [C#], anonymous methods
ms.assetid: a62441fa-f0a3-4acb-9aa6-93762a635275
ms.openlocfilehash: 94e9f7133c9a78ece7df5bd10cfc27c79d0652c2
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57203019"
---
# <a name="anonymous-methods-c-programming-guide"></a><span data-ttu-id="9d76c-102">Anonim Yöntemler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="9d76c-102">Anonymous Methods (C# Programming Guide)</span></span>
<span data-ttu-id="9d76c-103">C# ' ın sürümlerinde 2.0, tek yolu bildirmek için önce bir [temsilci](../../../csharp/language-reference/keywords/delegate.md) kullanılmasıydır [yöntemleri adlı](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md).</span><span class="sxs-lookup"><span data-stu-id="9d76c-103">In versions of C# before 2.0, the only way to declare a [delegate](../../../csharp/language-reference/keywords/delegate.md) was to use [named methods](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md).</span></span> <span data-ttu-id="9d76c-104">Anonim yöntemler C# 2.0 kullanılmaya ve C# 3.0 ve sonraki sürümlerinde, lambda ifadeleri anonim yöntemler satır içi kod yazmak için tercih edilen yol geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="9d76c-104">C# 2.0 introduced anonymous methods and in C# 3.0 and later, lambda expressions supersede anonymous methods as the preferred way to write inline code.</span></span> <span data-ttu-id="9d76c-105">Ancak, bu konudaki anonim yöntemler hakkında bilgi, lambda ifadeleri için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="9d76c-105">However, the information about anonymous methods in this topic also applies to lambda expressions.</span></span> <span data-ttu-id="9d76c-106">Anonim bir yöntem lambda ifadelerinde bulunamadı işlevselliği sağlayan bir durum yoktur.</span><span class="sxs-lookup"><span data-stu-id="9d76c-106">There is one case in which an anonymous method provides functionality not found in lambda expressions.</span></span> <span data-ttu-id="9d76c-107">Anonim yöntemler parametre listesini atlamak etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="9d76c-107">Anonymous methods enable you to omit the parameter list.</span></span> <span data-ttu-id="9d76c-108">Bu, anonim bir yöntem imzaları çeşitli temsilcilere dönüştürülebilir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="9d76c-108">This means that an anonymous method can be converted to delegates with a variety of signatures.</span></span> <span data-ttu-id="9d76c-109">Bu, lambda ifadeleri ile mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="9d76c-109">This is not possible with lambda expressions.</span></span> <span data-ttu-id="9d76c-110">Özellikle, lambda ifadeleri hakkında daha fazla bilgi için bkz. [Lambda ifadeleri](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="9d76c-110">For more information specifically about lambda expressions, see [Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="9d76c-111">Anonim yöntemler oluşturmak bir kod bloğu bir temsilcinin parametre olarak geçmesine aslında bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="9d76c-111">Creating anonymous methods is essentially a way to pass a code block as a delegate parameter.</span></span> <span data-ttu-id="9d76c-112">İki örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="9d76c-112">Here are two examples:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#6)]  
  
 [!code-csharp[csProgGuideDelegates#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#5)]  
  
 <span data-ttu-id="9d76c-113">Anonim yöntemler kullanarak, ek yükü ayrı bir yöntem oluşturmak olmadığı için temsilciler örnekleme kodlama azaltın.</span><span class="sxs-lookup"><span data-stu-id="9d76c-113">By using anonymous methods, you reduce the coding overhead in instantiating delegates because you do not have to create a separate method.</span></span>  
  
 <span data-ttu-id="9d76c-114">Örneğin, bir kod bloğu bir Temsilcinizin yerine bir yöntem oluşturmak zorunda kalmadan bir durumda kullanışlı olabilir belirtme gereksiz bir ek yük görünebilir.</span><span class="sxs-lookup"><span data-stu-id="9d76c-114">For example, specifying a code block instead of a delegate can be useful in a situation when having to create a method might seem an unnecessary overhead.</span></span> <span data-ttu-id="9d76c-115">Yeni bir iş parçacığı başlatıldığında, iyi bir örnek olacaktır.</span><span class="sxs-lookup"><span data-stu-id="9d76c-115">A good example would be when you start a new thread.</span></span> <span data-ttu-id="9d76c-116">Bu sınıf, bir iş parçacığı oluşturur ve ayrıca ek bir yöntem için temsilci oluşturmak zorunda kalmadan iş parçacığı yürütülen kod içerir.</span><span class="sxs-lookup"><span data-stu-id="9d76c-116">This class creates a thread and also contains the code that the thread executes without creating an additional method for the delegate.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#7)]  
  
## <a name="remarks"></a><span data-ttu-id="9d76c-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9d76c-117">Remarks</span></span>  
 <span data-ttu-id="9d76c-118">Anonim bir yöntem parametrelerini kapsamı *yöntem bloğu anonim*.</span><span class="sxs-lookup"><span data-stu-id="9d76c-118">The scope of the parameters of an anonymous method is the *anonymous-method-block*.</span></span>  
  
 <span data-ttu-id="9d76c-119">Bir atlama deyimi sahip bir hata olduğunu [goto](../../../csharp/language-reference/keywords/goto.md), [sonu](../../../csharp/language-reference/keywords/break.md), veya [devam](../../../csharp/language-reference/keywords/continue.md), hedefi blok dışındaysa ise anonim yöntem bloğu içinde.</span><span class="sxs-lookup"><span data-stu-id="9d76c-119">It is an error to have a jump statement, such as [goto](../../../csharp/language-reference/keywords/goto.md), [break](../../../csharp/language-reference/keywords/break.md), or [continue](../../../csharp/language-reference/keywords/continue.md), inside the anonymous method block if the target is outside the block.</span></span> <span data-ttu-id="9d76c-120">Ayrıca bir atlama deyimi sahip bir hata olduğunu `goto`, `break`, veya `continue`, hedef blok içinde ise anonim yöntem bloğu dışında.</span><span class="sxs-lookup"><span data-stu-id="9d76c-120">It is also an error to have a jump statement, such as `goto`, `break`, or `continue`, outside the anonymous method block if the target is inside the block.</span></span>  
  
 <span data-ttu-id="9d76c-121">Yerel değişkenleri ve parametreleri içeren bir anonim yöntem bildiriminde kapsamı adlı *dış* anonim yöntemin değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="9d76c-121">The local variables and parameters whose scope contains an anonymous method declaration are called *outer* variables of the anonymous method.</span></span> <span data-ttu-id="9d76c-122">Örneğin, aşağıdaki kod kesimi içinde `n` dış bir değişkendir:</span><span class="sxs-lookup"><span data-stu-id="9d76c-122">For example, in the following code segment, `n` is an outer variable:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#8)]  
  
 <span data-ttu-id="9d76c-123">Bir dış değişkenine başvuru `n` olduğu söylenir *yakalanan* temsilci oluşturulduğunda.</span><span class="sxs-lookup"><span data-stu-id="9d76c-123">A reference to the outer variable `n` is said to be *captured* when the delegate is created.</span></span> <span data-ttu-id="9d76c-124">Anonim yöntemler başvuran temsilcileri çöp toplama işlemi için uygun olana kadar yerel değişkenler farklı olarak, yakalanan bir değişkenin ömrü genişletir.</span><span class="sxs-lookup"><span data-stu-id="9d76c-124">Unlike local variables, the lifetime of a captured variable extends until the delegates that reference the anonymous methods are eligible for garbage collection.</span></span>  
  
 <span data-ttu-id="9d76c-125">Anonim bir yöntem erişemiyor [içinde](../../../csharp/language-reference/keywords/in.md), [ref](../../../csharp/language-reference/keywords/ref.md) veya [kullanıma](../../../csharp/language-reference/keywords/out-parameter-modifier.md) bir dış kapsam parametreleri.</span><span class="sxs-lookup"><span data-stu-id="9d76c-125">An anonymous method cannot access the [in](../../../csharp/language-reference/keywords/in.md), [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameters of an outer scope.</span></span>  
  
 <span data-ttu-id="9d76c-126">Güvenli olmayan kod içinde erişilebilir *yöntem bloğu anonim*.</span><span class="sxs-lookup"><span data-stu-id="9d76c-126">No unsafe code can be accessed within the *anonymous-method-block*.</span></span>  
  
 <span data-ttu-id="9d76c-127">Anonim yöntemler sol tarafında verilmez [olduğu](../../../csharp/language-reference/keywords/is.md) işleci.</span><span class="sxs-lookup"><span data-stu-id="9d76c-127">Anonymous methods are not allowed on the left side of the [is](../../../csharp/language-reference/keywords/is.md) operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d76c-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="9d76c-128">Example</span></span>  
 <span data-ttu-id="9d76c-129">Aşağıdaki örnek, bir temsilci örnekleme iki yolu gösterir:</span><span class="sxs-lookup"><span data-stu-id="9d76c-129">The following example demonstrates two ways of instantiating a delegate:</span></span>  
  
-   <span data-ttu-id="9d76c-130">Temsilci, adsız bir yöntem ile ilişkilendirme.</span><span class="sxs-lookup"><span data-stu-id="9d76c-130">Associating the delegate with an anonymous method.</span></span>  
  
-   <span data-ttu-id="9d76c-131">Temsilci adlandırılmış bir yöntem ile ilişkilendirme (`DoWork`).</span><span class="sxs-lookup"><span data-stu-id="9d76c-131">Associating the delegate with a named method (`DoWork`).</span></span>  
  
 <span data-ttu-id="9d76c-132">Temsilci çağrıldığında her durumda, bir ileti görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="9d76c-132">In each case, a message is displayed when the delegate is invoked.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="9d76c-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d76c-133">See also</span></span>

- [<span data-ttu-id="9d76c-134">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="9d76c-134">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="9d76c-135">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9d76c-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="9d76c-136">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="9d76c-136">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
- [<span data-ttu-id="9d76c-137">Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="9d76c-137">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
- [<span data-ttu-id="9d76c-138">Güvenli Olmayan Kod ve İşaretçiler</span><span class="sxs-lookup"><span data-stu-id="9d76c-138">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
- [<span data-ttu-id="9d76c-139">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9d76c-139">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
- [<span data-ttu-id="9d76c-140">Temsilcilerin Adlandırılmış ve Anonim Yöntemlerde Karşılaştırılması</span><span class="sxs-lookup"><span data-stu-id="9d76c-140">Delegates with Named vs. Anonymous Methods</span></span>](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)
