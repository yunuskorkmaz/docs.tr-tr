---
title: Shared
ms.date: 07/20/2015
f1_keywords:
- vb.Shared
helpviewer_keywords:
- Shared keyword [Visual Basic]
- members [Visual Basic], shared
- shared members
- nonshared
- shared [elements VB]
- elements [Visual Basic], shared
ms.assetid: 2bf7cf2c-b0dd-485e-8749-b5d674dab4cd
ms.openlocfilehash: bc63de4bda1e8e605e25fbe293686c187dd4d005
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290999"
---
# <a name="shared-visual-basic"></a><span data-ttu-id="17bf5-102">Shared (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="17bf5-102">Shared (Visual Basic)</span></span>

<span data-ttu-id="17bf5-103">Bir veya daha fazla bildirilmemiş programlama öğesinin, bir sınıf veya yapı ile ilişkili olduğunu ve sınıf veya yapının belirli bir örneğiyle ilişkilendirildiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="17bf5-103">Specifies that one or more declared programming elements are associated with a class or structure at large, and not with a specific instance of the class or structure.</span></span>

## <a name="when-to-use-shared"></a><span data-ttu-id="17bf5-104">Paylaşılan ne zaman kullanılır</span><span class="sxs-lookup"><span data-stu-id="17bf5-104">When to Use Shared</span></span>

<span data-ttu-id="17bf5-105">Bir sınıfın veya yapının bir üyesinin paylaşılması, her örneğin kendi kopyasını sakladığı, *paylaşılmayan*değil, her örnek için kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="17bf5-105">Sharing a member of a class or structure makes it available to every instance, rather than *non-shared*, where each instance keeps its own copy.</span></span> <span data-ttu-id="17bf5-106">Örneğin, bir değişkenin değeri uygulamanın tamamına geçerliyse, bu yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="17bf5-106">This is useful, for example, if the value of a variable applies to the entire application.</span></span> <span data-ttu-id="17bf5-107">Bu değişkenin olduğunu bildirirseniz `Shared` , tüm örnekler aynı depolama konumuna erişir ve bir örnek değişkenin değerini değiştirirse, tüm örnekler güncelleştirilmiş değere erişir.</span><span class="sxs-lookup"><span data-stu-id="17bf5-107">If you declare that variable to be `Shared`, then all instances access the same storage location, and if one instance changes the variable's value, all instances access the updated value.</span></span>

<span data-ttu-id="17bf5-108">Paylaşım, üyenin erişim düzeyini değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="17bf5-108">Sharing does not alter the access level of a member.</span></span> <span data-ttu-id="17bf5-109">Örneğin, bir sınıf üyesi paylaşılabilir ve özel (yalnızca sınıftan erişilebilir) veya paylaşılmayan ve genel olabilir.</span><span class="sxs-lookup"><span data-stu-id="17bf5-109">For example, a class member can be shared and private (accessible only from within the class), or non-shared and public.</span></span> <span data-ttu-id="17bf5-110">Daha fazla bilgi için bkz. [Visual Basic erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="17bf5-110">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

## <a name="rules"></a><span data-ttu-id="17bf5-111">Kurallar</span><span class="sxs-lookup"><span data-stu-id="17bf5-111">Rules</span></span>

- <span data-ttu-id="17bf5-112">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="17bf5-112">**Declaration Context.**</span></span> <span data-ttu-id="17bf5-113">`Shared`Yalnızca modül düzeyinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="17bf5-113">You can use `Shared` only at module level.</span></span> <span data-ttu-id="17bf5-114">Diğer bir deyişle, bir öğe için bildirim bağlamı `Shared` bir sınıf veya yapı olmalıdır ve kaynak dosya, ad alanı veya yordam olamaz.</span><span class="sxs-lookup"><span data-stu-id="17bf5-114">This means the declaration context for a `Shared` element must be a class or structure, and cannot be a source file, namespace, or procedure.</span></span>

- <span data-ttu-id="17bf5-115">**Birleşik değiştiriciler.**</span><span class="sxs-lookup"><span data-stu-id="17bf5-115">**Combined Modifiers.**</span></span> <span data-ttu-id="17bf5-116">`Shared`Aynı bildirimde [geçersiz kılmalar](../../../visual-basic/language-reference/modifiers/overrides.md), geçersiz [kılınabilir](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)veya [static](../../../visual-basic/language-reference/modifiers/static.md) ile birlikte belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="17bf5-116">You cannot specify `Shared` together with [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md), [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md), or [Static](../../../visual-basic/language-reference/modifiers/static.md) in the same declaration.</span></span>

- <span data-ttu-id="17bf5-117">**Erişme.**</span><span class="sxs-lookup"><span data-stu-id="17bf5-117">**Accessing.**</span></span> <span data-ttu-id="17bf5-118">Bir paylaşılan öğeye, sınıfının veya yapısının belirli bir örneğinin değişken adıyla değil, sınıf veya yapı adıyla niteleyerek erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="17bf5-118">You access a shared element by qualifying it with its class or structure name, not with the variable name of a specific instance of its class or structure.</span></span> <span data-ttu-id="17bf5-119">Paylaşılan üyelerine erişmek için bir sınıf veya yapının örneğini oluşturmanız da gerekmez.</span><span class="sxs-lookup"><span data-stu-id="17bf5-119">You do not even have to create an instance of a class or structure to access its shared members.</span></span>

     <span data-ttu-id="17bf5-120">Aşağıdaki örnek, <xref:System.Double.IsNaN%2A> Yapı tarafından sunulan paylaşılan yordamı çağırır <xref:System.Double> .</span><span class="sxs-lookup"><span data-stu-id="17bf5-120">The following example calls the shared procedure <xref:System.Double.IsNaN%2A> exposed by the <xref:System.Double> structure.</span></span>

     ```vb
     If Double.IsNaN(result) Then Console.WriteLine("Result is mathematically undefined.")
     ```

- <span data-ttu-id="17bf5-121">**Örtük paylaşım.**</span><span class="sxs-lookup"><span data-stu-id="17bf5-121">**Implicit Sharing.**</span></span> <span data-ttu-id="17bf5-122">`Shared`Bir [const ifadesinde](../../../visual-basic/language-reference/statements/const-statement.md)değiştirici kullanamazsınız, ancak sabitler örtülü olarak paylaşılır.</span><span class="sxs-lookup"><span data-stu-id="17bf5-122">You cannot use the `Shared` modifier in a [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md), but constants are implicitly shared.</span></span> <span data-ttu-id="17bf5-123">Benzer şekilde, bir modülün veya arabirimin bir üyesini `Shared` değil, örtülü olarak paylaşılırlar.</span><span class="sxs-lookup"><span data-stu-id="17bf5-123">Similarly, you cannot declare a member of a module or an interface to be `Shared`, but they are implicitly shared.</span></span>

## <a name="behavior"></a><span data-ttu-id="17bf5-124">Davranış</span><span class="sxs-lookup"><span data-stu-id="17bf5-124">Behavior</span></span>

- <span data-ttu-id="17bf5-125">**Depo.**</span><span class="sxs-lookup"><span data-stu-id="17bf5-125">**Storage.**</span></span> <span data-ttu-id="17bf5-126">Paylaşılan bir değişken veya olay, sınıfı veya yapısını kaç tane veya birkaç örnek oluşturduğunuz ve bu durumda yalnızca bir kez bellekte depolanır.</span><span class="sxs-lookup"><span data-stu-id="17bf5-126">A shared variable or event is stored in memory only once, no matter how many or few instances you create of its class or structure.</span></span> <span data-ttu-id="17bf5-127">Benzer şekilde, paylaşılan bir yordam veya özellik yalnızca bir yerel değişken kümesi tutar.</span><span class="sxs-lookup"><span data-stu-id="17bf5-127">Similarly, a shared procedure or property holds only one set of local variables.</span></span>

- <span data-ttu-id="17bf5-128">**Örnek değişkenine erişme.**</span><span class="sxs-lookup"><span data-stu-id="17bf5-128">**Accessing through an Instance Variable.**</span></span> <span data-ttu-id="17bf5-129">Kendi sınıfının veya yapısının belirli bir örneğini içeren bir değişkenin adı ile niteleyerek paylaşılan bir öğeye erişmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="17bf5-129">It is possible to access a shared element by qualifying it with the name of a variable that contains a specific instance of its class or structure.</span></span> <span data-ttu-id="17bf5-130">Bu, genellikle beklenen şekilde çalışsa da, derleyici bir uyarı mesajı oluşturur ve değişken yerine sınıf veya yapı adıyla erişimi yapar.</span><span class="sxs-lookup"><span data-stu-id="17bf5-130">Although this usually works as expected, the compiler generates a warning message and makes the access through the class or structure name instead of the variable.</span></span>

- <span data-ttu-id="17bf5-131">**Örnek Ifadesiyle erişme.**</span><span class="sxs-lookup"><span data-stu-id="17bf5-131">**Accessing through an Instance Expression.**</span></span> <span data-ttu-id="17bf5-132">Sınıfının veya yapısının bir örneğini döndüren bir ifade aracılığıyla paylaşılan bir öğeye eriştiğinizde, derleyici, ifadeyi değerlendirmek yerine sınıf veya yapı adı üzerinden erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="17bf5-132">If you access a shared element through an expression that returns an instance of its class or structure, the compiler makes the access through the class or structure name instead of evaluating the expression.</span></span> <span data-ttu-id="17bf5-133">Bu, ifadenin diğer eylemleri gerçekleştirmesini ve örneği döndürmesini amaçlıyorsanız beklenmedik sonuçlar üretir.</span><span class="sxs-lookup"><span data-stu-id="17bf5-133">This produces unexpected results if you intended the expression to perform other actions as well as returning the instance.</span></span> <span data-ttu-id="17bf5-134">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="17bf5-134">The following example illustrates this.</span></span>
  
    ```vb
    Sub Main()
        ' The following line is the preferred way to access Total.
        ShareTotal.Total = 10

        ' The following line generates a compiler warning message and
        ' accesses total through class ShareTotal instead of through
        ' the variable instanceVar. This works as expected and adds
        ' 100 to Total.
        Dim instanceVar As New ShareTotal
        instanceVar.Total += 100

        ' The following line generates a compiler warning message and
        ' accesses total through class ShareTotal instead of calling
        ' ReturnClass(). This adds 1000 to total but does not work as
        ' expected, because the WriteLine in ReturnClass() does not run.
        Console.WriteLine("Value of total is " & CStr(ShareTotal.Total))
        ReturnClass().Total += 1000
    End Sub

    Public Function ReturnClass() As ShareTotal
        Console.WriteLine("Function ReturnClass() called")
        Return New ShareTotal
    End Function

    Public Class ShareTotal
        Public Shared Property Total As Integer
    End Class
    ```

     <span data-ttu-id="17bf5-135">Önceki örnekte, derleyici her iki durumda da kodun paylaşılan özelliğe bir örnek aracılığıyla eriştiği bir uyarı mesajı oluşturur `Total` .</span><span class="sxs-lookup"><span data-stu-id="17bf5-135">In the preceding example, the compiler generates a warning message both times the code accesses the shared property `Total` through an instance.</span></span> <span data-ttu-id="17bf5-136">Her durumda, erişimi doğrudan sınıf üzerinden yapar `ShareTotal` ve herhangi bir örneği kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="17bf5-136">In each case it makes the access directly through the class `ShareTotal` and does not make use of any instance.</span></span> <span data-ttu-id="17bf5-137">Yordama yönelik amaçlanan çağrı durumunda `ReturnClass` Bu, bir çağrı üretmediği anlamına gelir; bu `ReturnClass` nedenle "Function returnClass ()" adlı "işlev" olarak adlandırılan ek eylem gerçekleştirilmez.</span><span class="sxs-lookup"><span data-stu-id="17bf5-137">In the case of the intended call to the procedure `ReturnClass`, this means it does not even generate a call to `ReturnClass`, so the additional action of displaying "Function ReturnClass() called" is not performed.</span></span>

<span data-ttu-id="17bf5-138">`Shared`Değiştirici şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="17bf5-138">The `Shared` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="17bf5-139">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="17bf5-139">Dim Statement</span></span>](../statements/dim-statement.md)
- [<span data-ttu-id="17bf5-140">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="17bf5-140">Event Statement</span></span>](../statements/event-statement.md)
- [<span data-ttu-id="17bf5-141">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="17bf5-141">Function Statement</span></span>](../statements/function-statement.md)
- [<span data-ttu-id="17bf5-142">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="17bf5-142">Operator Statement</span></span>](../operator-statement.md)
- [<span data-ttu-id="17bf5-143">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="17bf5-143">Property Statement</span></span>](../property-statement.md)
- [<span data-ttu-id="17bf5-144">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="17bf5-144">Sub Statement</span></span>](../sub-statement.md)
  
## <a name="see-also"></a><span data-ttu-id="17bf5-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17bf5-145">See also</span></span>

- [<span data-ttu-id="17bf5-146">Shadows</span><span class="sxs-lookup"><span data-stu-id="17bf5-146">Shadows</span></span>](shadows.md)
- [<span data-ttu-id="17bf5-147">Se</span><span class="sxs-lookup"><span data-stu-id="17bf5-147">Static</span></span>](static.md)
- [<span data-ttu-id="17bf5-148">Visual Basic'de Ömür</span><span class="sxs-lookup"><span data-stu-id="17bf5-148">Lifetime in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="17bf5-149">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="17bf5-149">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="17bf5-150">Yapılar</span><span class="sxs-lookup"><span data-stu-id="17bf5-150">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="17bf5-151">Nesneler ve sınıflar</span><span class="sxs-lookup"><span data-stu-id="17bf5-151">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
