---
title: Anonim Yöntemler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous methods [C#]
- methods [C#], anonymous
- delegates [C#], anonymous methods
ms.assetid: a62441fa-f0a3-4acb-9aa6-93762a635275
ms.openlocfilehash: 7f6c596dcc73cdfb335071f57aab18e836ceaae8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33338428"
---
# <a name="anonymous-methods-c-programming-guide"></a><span data-ttu-id="aa729-102">Anonim Yöntemler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="aa729-102">Anonymous Methods (C# Programming Guide)</span></span>
<span data-ttu-id="aa729-103">Sürümlerinde C# 2.0, bildirmek için tek yolu önce bir [temsilci](../../../csharp/language-reference/keywords/delegate.md) kullanılmasıydır [yöntemleri adlı](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md).</span><span class="sxs-lookup"><span data-stu-id="aa729-103">In versions of C# before 2.0, the only way to declare a [delegate](../../../csharp/language-reference/keywords/delegate.md) was to use [named methods](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md).</span></span> <span data-ttu-id="aa729-104">C# 2.0 anonim yöntemler açıklanmıştır ve C# 3.0 ve sonraki sürümlerinde, lambda ifadeleri anonim yöntemler satır içi kod yazmak için tercih edilen yol geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="aa729-104">C# 2.0 introduced anonymous methods and in C# 3.0 and later, lambda expressions supersede anonymous methods as the preferred way to write inline code.</span></span> <span data-ttu-id="aa729-105">Ancak, bu konudaki anonim yöntemler hakkında bilgi lambda ifadeleri için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="aa729-105">However, the information about anonymous methods in this topic also applies to lambda expressions.</span></span> <span data-ttu-id="aa729-106">Adsız bir yöntem lambda ifadelerini bulunamadı işlevselliği sağlayan bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="aa729-106">There is one case in which an anonymous method provides functionality not found in lambda expressions.</span></span> <span data-ttu-id="aa729-107">Anonim yöntemler parametre listesi atlamak etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="aa729-107">Anonymous methods enable you to omit the parameter list.</span></span> <span data-ttu-id="aa729-108">Bu, adsız bir yöntem imzaları çeşitli temsilcilere dönüştürülebilir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="aa729-108">This means that an anonymous method can be converted to delegates with a variety of signatures.</span></span> <span data-ttu-id="aa729-109">Bu lambda ifadeleri ile mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="aa729-109">This is not possible with lambda expressions.</span></span> <span data-ttu-id="aa729-110">Lambda ifadeleri özellikle hakkında daha fazla bilgi için bkz: [Lambda ifadeleri](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="aa729-110">For more information specifically about lambda expressions, see [Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="aa729-111">Anonim yöntemler oluşturma kod bloğu temsilci parametre olarak geçirmek için temel bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="aa729-111">Creating anonymous methods is essentially a way to pass a code block as a delegate parameter.</span></span> <span data-ttu-id="aa729-112">Aşağıda, iki örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="aa729-112">Here are two examples:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#6](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_1.cs)]  
  
 [!code-csharp[csProgGuideDelegates#5](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_2.cs)]  
  
 <span data-ttu-id="aa729-113">Anonim yöntemler kullanarak ek yükü temsilciler örneği ayrı bir yöntem oluşturmak olmadığından kodlama azaltın.</span><span class="sxs-lookup"><span data-stu-id="aa729-113">By using anonymous methods, you reduce the coding overhead in instantiating delegates because you do not have to create a separate method.</span></span>  
  
 <span data-ttu-id="aa729-114">Örneğin, bir temsilci yerine kod bloğu bir yöntem oluşturmak zorunda kalmadan bir durumda kullanışlı olabilir belirtme gereksiz bir ek yük görünebilir.</span><span class="sxs-lookup"><span data-stu-id="aa729-114">For example, specifying a code block instead of a delegate can be useful in a situation when having to create a method might seem an unnecessary overhead.</span></span> <span data-ttu-id="aa729-115">Yeni bir iş parçacığı başlattığınızda güzel bir örnek olacaktır.</span><span class="sxs-lookup"><span data-stu-id="aa729-115">A good example would be when you start a new thread.</span></span> <span data-ttu-id="aa729-116">Bu sınıf, bir iş parçacığı oluşturur ve ayrıca iş parçacığı temsilci için ek bir yöntem oluşturmadan yürütülen kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="aa729-116">This class creates a thread and also contains the code that the thread executes without creating an additional method for the delegate.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#7](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_3.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="aa729-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aa729-117">Remarks</span></span>  
 <span data-ttu-id="aa729-118">Anonim bir yöntemin parametrelerini kapsamı *yöntem bloğu anonim*.</span><span class="sxs-lookup"><span data-stu-id="aa729-118">The scope of the parameters of an anonymous method is the *anonymous-method-block*.</span></span>  
  
 <span data-ttu-id="aa729-119">Atlama deyimi gibi sağlamak için bir hata olduğunu [goto](../../../csharp/language-reference/keywords/goto.md), [sonu](../../../csharp/language-reference/keywords/break.md), veya [devam](../../../csharp/language-reference/keywords/continue.md), hedef blok dışında ise adsız yöntem bloğu içinde.</span><span class="sxs-lookup"><span data-stu-id="aa729-119">It is an error to have a jump statement, such as [goto](../../../csharp/language-reference/keywords/goto.md), [break](../../../csharp/language-reference/keywords/break.md), or [continue](../../../csharp/language-reference/keywords/continue.md), inside the anonymous method block if the target is outside the block.</span></span> <span data-ttu-id="aa729-120">Ayrıca bir atlama deyimi gibi sağlamak için bir hata olduğunu `goto`, `break`, veya `continue`, hedef blok içinde ise adsız yöntem bloğu dışında.</span><span class="sxs-lookup"><span data-stu-id="aa729-120">It is also an error to have a jump statement, such as `goto`, `break`, or `continue`, outside the anonymous method block if the target is inside the block.</span></span>  
  
 <span data-ttu-id="aa729-121">Yerel değişkenleri ve parametreleri, kapsam içeren bir anonim yöntem bildirimi adlı *dış* anonim yöntemin değişkenlerinin.</span><span class="sxs-lookup"><span data-stu-id="aa729-121">The local variables and parameters whose scope contains an anonymous method declaration are called *outer* variables of the anonymous method.</span></span> <span data-ttu-id="aa729-122">Örneğin, aşağıdaki kod parçası olarak `n` bir dış değişken:</span><span class="sxs-lookup"><span data-stu-id="aa729-122">For example, in the following code segment, `n` is an outer variable:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#8](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_4.cs)]  
  
 <span data-ttu-id="aa729-123">Dış değişken başvuru `n` olarak kabul edilir *yakalanan* temsilci oluşturulduğunda.</span><span class="sxs-lookup"><span data-stu-id="aa729-123">A reference to the outer variable `n` is said to be *captured* when the delegate is created.</span></span> <span data-ttu-id="aa729-124">Anonim yöntemler başvuru temsilcileri atık toplama için uygun olana kadar yerel değişkenler, yakalanan bir değişken ömrü genişletir.</span><span class="sxs-lookup"><span data-stu-id="aa729-124">Unlike local variables, the lifetime of a captured variable extends until the delegates that reference the anonymous methods are eligible for garbage collection.</span></span>  
  
 <span data-ttu-id="aa729-125">Adsız bir yöntem erişemiyor [içinde](../../../csharp/language-reference/keywords/in.md), [ref](../../../csharp/language-reference/keywords/ref.md) veya [çıkışı](../../../csharp/language-reference/keywords/out-parameter-modifier.md) bir dış kapsam parametreleri.</span><span class="sxs-lookup"><span data-stu-id="aa729-125">An anonymous method cannot access the [in](../../../csharp/language-reference/keywords/in.md), [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameters of an outer scope.</span></span>  
  
 <span data-ttu-id="aa729-126">Güvenli olmayan kod içinde erişilebilir *yöntem bloğu anonim*.</span><span class="sxs-lookup"><span data-stu-id="aa729-126">No unsafe code can be accessed within the *anonymous-method-block*.</span></span>  
  
 <span data-ttu-id="aa729-127">Anonim yöntemler sol tarafında verilmez [olan](../../../csharp/language-reference/keywords/is.md) işleci.</span><span class="sxs-lookup"><span data-stu-id="aa729-127">Anonymous methods are not allowed on the left side of the [is](../../../csharp/language-reference/keywords/is.md) operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa729-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="aa729-128">Example</span></span>  
 <span data-ttu-id="aa729-129">Aşağıdaki örnek, bir temsilci başlatmasını iki yolu gösterir:</span><span class="sxs-lookup"><span data-stu-id="aa729-129">The following example demonstrates two ways of instantiating a delegate:</span></span>  
  
-   <span data-ttu-id="aa729-130">Temsilci anonim yöntemi ile ilişkilendirme.</span><span class="sxs-lookup"><span data-stu-id="aa729-130">Associating the delegate with an anonymous method.</span></span>  
  
-   <span data-ttu-id="aa729-131">Temsilci adlandırılmış bir yöntem ile ilişkilendirme (`DoWork`).</span><span class="sxs-lookup"><span data-stu-id="aa729-131">Associating the delegate with a named method (`DoWork`).</span></span>  
  
 <span data-ttu-id="aa729-132">Temsilci çağrıldığında her durumda, bir ileti görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="aa729-132">In each case, a message is displayed when the delegate is invoked.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#4](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_5.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="aa729-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aa729-133">See Also</span></span>  
 [<span data-ttu-id="aa729-134">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="aa729-134">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="aa729-135">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="aa729-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="aa729-136">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="aa729-136">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="aa729-137">Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="aa729-137">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [<span data-ttu-id="aa729-138">Güvenli Olmayan Kod ve İşaretçiler</span><span class="sxs-lookup"><span data-stu-id="aa729-138">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="aa729-139">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="aa729-139">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [<span data-ttu-id="aa729-140">Temsilcilerin Adlandırılmış ve Anonim Yöntemlerde Karşılaştırılması</span><span class="sxs-lookup"><span data-stu-id="aa729-140">Delegates with Named vs. Anonymous Methods</span></span>](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)
