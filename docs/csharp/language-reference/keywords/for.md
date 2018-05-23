---
title: for (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: 2c099411499c6ca8396c55955bdc634e48caf621
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/18/2018
---
# <a name="for-c-reference"></a><span data-ttu-id="1f29b-102">(için C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="1f29b-102">for (C# reference)</span></span>

<span data-ttu-id="1f29b-103">Kullanarak bir `for` döngü, çalıştırabileceğiniz bir deyim veya deyimleri bloğu art arda için belirtilen ifadeyi değerlendirir kadar `false`.</span><span class="sxs-lookup"><span data-stu-id="1f29b-103">By using a `for` loop, you can run a statement or a block of statements repeatedly until a specified expression evaluates to `false`.</span></span> <span data-ttu-id="1f29b-104">Bu tür bir döngü hem de önceden yinelemek için döngü istediğiniz kaç kez bilmeniz diğer uygulamalar diziler yineleme için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="1f29b-104">This kind of loop is useful for iterating over arrays and for other applications in which you know in advance how many times you want the loop to iterate.</span></span>
  
## <a name="example"></a><span data-ttu-id="1f29b-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="1f29b-105">Example</span></span>

<span data-ttu-id="1f29b-106">Aşağıdaki örnekte, değeri `i` konsola yazılır ve her döngü sırasında 1 azaltılır:</span><span class="sxs-lookup"><span data-stu-id="1f29b-106">In the following example, the value of `i` is written to the console and incremented by 1 during each iteration of the loop:</span></span>
  
[!code-csharp[csrefKeywordsIteration#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_1.cs)]
  
<span data-ttu-id="1f29b-107">[Deyimi için](/dotnet/csharp/language-reference/language-specification/statements#the-for-statement) önceki örnekte aşağıdaki eylemleri gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="1f29b-107">The [for statement](/dotnet/csharp/language-reference/language-specification/statements#the-for-statement) in the previous example performs the following actions:</span></span>
  
1.  <span data-ttu-id="1f29b-108">İlk olarak, ilk değişkenin değeri olarak `i` kurulur.</span><span class="sxs-lookup"><span data-stu-id="1f29b-108">First, the initial value of variable `i` is established.</span></span> <span data-ttu-id="1f29b-109">Bu adım, döngü yineler birçok kez nasıl bağımsız olarak yalnızca bir kez gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="1f29b-109">This step happens only once, regardless of how many times the loop repeats.</span></span> <span data-ttu-id="1f29b-110">Bu başlatılması döngü işlemin dışında oluşmasını olarak düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f29b-110">You can think of this initialization as happening outside the looping process.</span></span>
  
2.  <span data-ttu-id="1f29b-111">Koşulunu hesaplamayı (`i <= 5`), değeri `i` 5 ile karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="1f29b-111">To evaluate the condition (`i <= 5`), the value of `i` is compared to 5.</span></span>
  
    -   <span data-ttu-id="1f29b-112">Varsa `i` küçük veya ona eşit için 5, koşulu değerlendirir `true`, ve aşağıdaki eylemler gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="1f29b-112">If `i` is less than or equal to 5, the condition evaluates to `true`, and the following actions occur.</span></span>  
  
        1.  <span data-ttu-id="1f29b-113">`Console.WriteLine` Döngü gövdesine ifade değerini görüntüler `i`.</span><span class="sxs-lookup"><span data-stu-id="1f29b-113">The `Console.WriteLine` statement in the body of the loop displays the value of `i`.</span></span>  
  
        2.  <span data-ttu-id="1f29b-114">Değeri `i` 1 artırılır.</span><span class="sxs-lookup"><span data-stu-id="1f29b-114">The value of `i` is incremented by 1.</span></span>  
  
        3.  <span data-ttu-id="1f29b-115">Döngü koşulu yeniden değerlendirmek için 2. adım başlangıcını döndürür.</span><span class="sxs-lookup"><span data-stu-id="1f29b-115">The loop returns to the start of step 2 to evaluate the condition again.</span></span>  
  
    -   <span data-ttu-id="1f29b-116">Varsa `i` 5'ten büyük olduğu için koşulu değerlendirir `false`, ve döngüden çıkın.</span><span class="sxs-lookup"><span data-stu-id="1f29b-116">If `i` is greater than 5, the condition evaluates to `false`, and you exit the loop.</span></span>  
  
<span data-ttu-id="1f29b-117">Unutmayın ilk değeri `i` 5'ten büyük döngünün gövdesi bile bir kez çalıştırmaz.</span><span class="sxs-lookup"><span data-stu-id="1f29b-117">Note that, if the initial value of `i` is greater than 5, the body of the loop doesn't run even once.</span></span>

## <a name="sections-of-a-for-statement"></a><span data-ttu-id="1f29b-118">Bölümlerini bir deyim için</span><span class="sxs-lookup"><span data-stu-id="1f29b-118">Sections of a for statement</span></span>
  
<span data-ttu-id="1f29b-119">Her [deyimi için](/dotnet/csharp/language-reference/language-specification/statements#the-for-statement) tanımlar *Başlatıcı*, *koşulu*, ve *yineleyici* bölümler.</span><span class="sxs-lookup"><span data-stu-id="1f29b-119">Every [for statement](/dotnet/csharp/language-reference/language-specification/statements#the-for-statement) defines *initializer*, *condition*, and *iterator* sections.</span></span> <span data-ttu-id="1f29b-120">Bu bölümler genellikle döngü tekrarlanan kaç kez belirler.</span><span class="sxs-lookup"><span data-stu-id="1f29b-120">These sections usually determine how many times the loop iterates.</span></span>  
  
```csharp  
for (initializer; condition; iterator)  
    body  
```  
  
<span data-ttu-id="1f29b-121">Bölümler aşağıdaki amaca hizmet eder:</span><span class="sxs-lookup"><span data-stu-id="1f29b-121">The sections serve the following purposes:</span></span>
  
-   <span data-ttu-id="1f29b-122">Başlatıcı bölüm ilk koşul ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1f29b-122">The initializer section sets the initial conditions.</span></span> <span data-ttu-id="1f29b-123">Döngü girmeden önce bu bölümdeki deyimleri yalnızca bir kez çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1f29b-123">The statements in this section run only once, before you enter the loop.</span></span> <span data-ttu-id="1f29b-124">Bölüm yalnızca aşağıdaki iki seçenekten birini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="1f29b-124">The section can contain only one of the following two options.</span></span>  
  
    -   <span data-ttu-id="1f29b-125">Bildirim ve başlatma İlk örnekte gösterildiği gibi bir yerel döngü değişkenin (`int i = 1`).</span><span class="sxs-lookup"><span data-stu-id="1f29b-125">The declaration and initialization of a local loop variable, as the first example shows (`int i = 1`).</span></span> <span data-ttu-id="1f29b-126">Değişkeni döngü için yerel olan ve gelen döngü dışında erişilemez.</span><span class="sxs-lookup"><span data-stu-id="1f29b-126">The variable is local to the loop and can't be accessed from outside the loop.</span></span>  
  
    -   <span data-ttu-id="1f29b-127">Sıfır veya daha fazla deyim expressons virgülle ayırarak aşağıdaki listeden.</span><span class="sxs-lookup"><span data-stu-id="1f29b-127">Zero or more statement expressons from the following list, separated by commas.</span></span>  
  
        -   <span data-ttu-id="1f29b-128">[atama](../../../csharp/language-reference/operators/assignment-operator.md) deyimi</span><span class="sxs-lookup"><span data-stu-id="1f29b-128">[assignment](../../../csharp/language-reference/operators/assignment-operator.md) statement</span></span>  
  
        -   <span data-ttu-id="1f29b-129">bir yöntemi çağrıldı</span><span class="sxs-lookup"><span data-stu-id="1f29b-129">invocation of a method</span></span>  
  
        -   <span data-ttu-id="1f29b-130">önek veya sonek [artırma](../../../csharp/language-reference/operators/increment-operator.md) ifadesi gibi `++i` veya `i++`</span><span class="sxs-lookup"><span data-stu-id="1f29b-130">prefix or postfix [increment](../../../csharp/language-reference/operators/increment-operator.md) expression, such as `++i` or `i++`</span></span>  
  
        -   <span data-ttu-id="1f29b-131">önek veya sonek [azaltma](../../../csharp/language-reference/operators/decrement-operator.md) ifadesi gibi `--i` veya `i--`</span><span class="sxs-lookup"><span data-stu-id="1f29b-131">prefix or postfix [decrement](../../../csharp/language-reference/operators/decrement-operator.md) expression, such as `--i` or `i--`</span></span>  
  
        -   <span data-ttu-id="1f29b-132">kullanarak bir nesne oluşturulmasını [yeni](../../../csharp/language-reference/keywords/new-operator.md)</span><span class="sxs-lookup"><span data-stu-id="1f29b-132">creation of an object by using [new](../../../csharp/language-reference/keywords/new-operator.md)</span></span>  
  
        -   <span data-ttu-id="1f29b-133">[await](../../../csharp/language-reference/keywords/await.md) ifadesi</span><span class="sxs-lookup"><span data-stu-id="1f29b-133">[await](../../../csharp/language-reference/keywords/await.md) expression</span></span>  
  
-   <span data-ttu-id="1f29b-134">Koşul bölüm döngü çıkmalıdır veya yeniden çalışması gerektiğini belirlemek için değerlendirilen boolean bir ifade içeriyor.</span><span class="sxs-lookup"><span data-stu-id="1f29b-134">The condition section contains a boolean expression that’s evaluated to determine whether the loop should exit or should run again.</span></span>  
  
-   <span data-ttu-id="1f29b-135">Yineleyici bölümü döngüden gövdesinin her yinelemeden sonra ne olacağını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1f29b-135">The iterator section defines what happens after each iteration of the body of the loop.</span></span> <span data-ttu-id="1f29b-136">Yineleyici bölüm sıfır veya daha fazla virgülle ayırarak aşağıdaki deyimi ifadeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="1f29b-136">The iterator section contains zero or more of the following statement expressions, separated by commas:</span></span>  
  
    -   <span data-ttu-id="1f29b-137">[atama](../../../csharp/language-reference/operators/assignment-operator.md) deyimi</span><span class="sxs-lookup"><span data-stu-id="1f29b-137">[assignment](../../../csharp/language-reference/operators/assignment-operator.md) statement</span></span>  
  
    -   <span data-ttu-id="1f29b-138">bir yöntemi çağrıldı</span><span class="sxs-lookup"><span data-stu-id="1f29b-138">invocation of a method</span></span>  
  
    -   <span data-ttu-id="1f29b-139">önek veya sonek [artırma](../../../csharp/language-reference/operators/increment-operator.md) ifadesi gibi `++i` veya `i++`</span><span class="sxs-lookup"><span data-stu-id="1f29b-139">prefix or postfix [increment](../../../csharp/language-reference/operators/increment-operator.md) expression, such as `++i` or `i++`</span></span>  
  
    -   <span data-ttu-id="1f29b-140">önek veya sonek [azaltma](../../../csharp/language-reference/operators/decrement-operator.md) ifadesi gibi `--i` veya `i--`</span><span class="sxs-lookup"><span data-stu-id="1f29b-140">prefix or postfix [decrement](../../../csharp/language-reference/operators/decrement-operator.md) expression, such as `--i` or `i--`</span></span>  
  
    -   <span data-ttu-id="1f29b-141">kullanarak bir nesne oluşturulmasını [yeni](../../../csharp/language-reference/keywords/new-operator.md)</span><span class="sxs-lookup"><span data-stu-id="1f29b-141">creation of an object by using [new](../../../csharp/language-reference/keywords/new-operator.md)</span></span>  
  
    -   <span data-ttu-id="1f29b-142">[await](../../../csharp/language-reference/keywords/await.md) ifadesi</span><span class="sxs-lookup"><span data-stu-id="1f29b-142">[await](../../../csharp/language-reference/keywords/await.md) expression</span></span>  
  
-   <span data-ttu-id="1f29b-143">Döngünün gövdesi bir deyim, boş bir deyimi veya sıfır veya daha fazla deyimleri ayraçlar içinde kapsayan tarafından oluşturduğunuz deyimleri bloğu oluşur.</span><span class="sxs-lookup"><span data-stu-id="1f29b-143">The body of the loop consists of a statement, an empty statement, or a block of statements, which you create by enclosing zero or more statements in braces.</span></span>  
  
     <span data-ttu-id="1f29b-144">İşyeri dışında bölünebilir bir `for` kullanarak döngü [sonu](../../../csharp/language-reference/keywords/break.md) anahtar sözcüğü veya adım sonraki yinelemeye kullanarak [devam](../../../csharp/language-reference/keywords/continue.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="1f29b-144">You can break out of a `for` loop by using the [break](../../../csharp/language-reference/keywords/break.md) keyword, or you can step to the next iteration by using the [continue](../../../csharp/language-reference/keywords/continue.md) keyword.</span></span> <span data-ttu-id="1f29b-145">Kullanarak her döngü çıkabilirsiniz bir [goto](../../../csharp/language-reference/keywords/goto.md), [dönmek](../../../csharp/language-reference/keywords/return.md), veya [throw](../../../csharp/language-reference/keywords/throw.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="1f29b-145">You also can exit any loop by using a [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md), or [throw](../../../csharp/language-reference/keywords/throw.md) statement.</span></span>  
  
<span data-ttu-id="1f29b-146">Bu konudaki ilk örnek tür en tipik gösterir `for` döngüsü bölümleri için aşağıdaki seçenekleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="1f29b-146">The first example in this topic shows the most typical kind of `for` loop, which makes the following choices for the sections:</span></span>
  
-   <span data-ttu-id="1f29b-147">Başlatıcı bildirir ve bir yerel döngü değişkenini `i`, döngü yineleme sayısını tutar.</span><span class="sxs-lookup"><span data-stu-id="1f29b-147">The initializer declares and initializes a local loop variable, `i`, that maintains a count of the iterations of the loop.</span></span>  
  
-   <span data-ttu-id="1f29b-148">Koşul değişkenin değeri olarak döngü bilinen son bir değer olan 5 karşı denetler.</span><span class="sxs-lookup"><span data-stu-id="1f29b-148">The condition checks the value of the loop variable against a known final value, 5.</span></span>  
  
-   <span data-ttu-id="1f29b-149">Sonek artırma deyimi yineleyici kullanıyorsa `i++`, her döngü tekrarında kaydetmesini.</span><span class="sxs-lookup"><span data-stu-id="1f29b-149">The iterator section uses a postfix increment statement, `i++`, to tally each iteration of the loop.</span></span>

## <a name="more-examples"></a><span data-ttu-id="1f29b-150">Daha fazla örnek</span><span class="sxs-lookup"><span data-stu-id="1f29b-150">More examples</span></span>
  
<span data-ttu-id="1f29b-151">Aşağıdaki örnek birkaç genel seçenek daha az gösterilmektedir: Başlatıcı bölümünde bir dış döngü değişkene bir değer atama, çağırma `Console.WriteLine` hem Başlatıcı yineleyici bölümleri ve iki değerlerini değiştirme yöntemi Yineleyici bölümünde değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="1f29b-151">The following example illustrates several less common choices: assigning a value to an external loop variable in the initializer section, invoking the `Console.WriteLine` method in both the initializer and the iterator sections, and changing the values of two variables in the iterator section.</span></span>
  
[!code-csharp[csrefKeywordsIteration#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_2.cs)]  
  
<span data-ttu-id="1f29b-152">Tüm tanımlayan bir ifade bir `for` deyimi isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1f29b-152">All of the expressions that define a `for` statement are optional.</span></span> <span data-ttu-id="1f29b-153">Örneğin, aşağıdaki deyim sonsuz bir döngüde oluşturur:</span><span class="sxs-lookup"><span data-stu-id="1f29b-153">For example, the following statement creates an infinite loop:</span></span>
  
[!code-csharp[csrefKeywordsIteration#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_3.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="1f29b-154">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="1f29b-154">C# language specification</span></span>  

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]
  
## <a name="see-also"></a><span data-ttu-id="1f29b-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f29b-155">See also</span></span>

[<span data-ttu-id="1f29b-156">Deyimi (C# dil belirtimi) için</span><span class="sxs-lookup"><span data-stu-id="1f29b-156">The for statement (C# language specification)</span></span>](/dotnet/csharp/language-reference/language-specification/statements#the-for-statement)  
[<span data-ttu-id="1f29b-157">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="1f29b-157">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
[<span data-ttu-id="1f29b-158">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="1f29b-158">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
[<span data-ttu-id="1f29b-159">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="1f29b-159">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
[<span data-ttu-id="1f29b-160">foreach, in</span><span class="sxs-lookup"><span data-stu-id="1f29b-160">foreach, in</span></span>](../../../csharp/language-reference/keywords/foreach-in.md)  
[<span data-ttu-id="1f29b-161">for Deyimi (C++)</span><span class="sxs-lookup"><span data-stu-id="1f29b-161">for Statement (C++)</span></span>](/cpp/cpp/for-statement-cpp)  
[<span data-ttu-id="1f29b-162">Yineleme Deyimleri</span><span class="sxs-lookup"><span data-stu-id="1f29b-162">Iteration Statements</span></span>](../../../csharp/language-reference/keywords/iteration-statements.md)
