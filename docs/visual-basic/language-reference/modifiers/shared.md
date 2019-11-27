---
title: '{1&gt;Paylaşılan&lt;1}'
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
ms.openlocfilehash: 98fa25d2283408dfb80e82fbc620a1b284e5c530
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349125"
---
# <a name="shared-visual-basic"></a><span data-ttu-id="6e38c-102">Shared (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e38c-102">Shared (Visual Basic)</span></span>
<span data-ttu-id="6e38c-103">Bir veya daha fazla bildirilmemiş programlama öğesinin, bir sınıf veya yapı ile ilişkili olduğunu ve sınıf veya yapının belirli bir örneğiyle ilişkilendirildiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6e38c-103">Specifies that one or more declared programming elements are associated with a class or structure at large, and not with a specific instance of the class or structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e38c-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6e38c-104">Remarks</span></span>  
  
## <a name="when-to-use-shared"></a><span data-ttu-id="6e38c-105">Paylaşılan ne zaman kullanılır</span><span class="sxs-lookup"><span data-stu-id="6e38c-105">When to Use Shared</span></span>  
 <span data-ttu-id="6e38c-106">Bir sınıfın veya yapının bir üyesinin paylaşılması, *paylaşılan*değil, her örneğin kendi kopyasını tutan her örnek için kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="6e38c-106">Sharing a member of a class or structure makes it available to every instance, rather than *nonshared*, where each instance keeps its own copy.</span></span> <span data-ttu-id="6e38c-107">Örneğin, bir değişkenin değeri uygulamanın tamamına geçerliyse, bu yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="6e38c-107">This is useful, for example, if the value of a variable applies to the entire application.</span></span> <span data-ttu-id="6e38c-108">Bu değişkenin `Shared`olduğunu bildirirseniz, tüm örnekler aynı depolama konumuna erişir ve bir örnek değişkenin değerini değiştirirse, tüm örnekler güncelleştirilmiş değere erişir.</span><span class="sxs-lookup"><span data-stu-id="6e38c-108">If you declare that variable to be `Shared`, then all instances access the same storage location, and if one instance changes the variable's value, all instances access the updated value.</span></span>  
  
 <span data-ttu-id="6e38c-109">Paylaşım, üyenin erişim düzeyini değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="6e38c-109">Sharing does not alter the access level of a member.</span></span> <span data-ttu-id="6e38c-110">Örneğin, bir sınıf üyesi paylaşılabilir ve özel (yalnızca sınıfın içinden erişilebilir) veya paylaşılmayan ve genel olabilir.</span><span class="sxs-lookup"><span data-stu-id="6e38c-110">For example, a class member can be shared and private (accessible only from within the class), or nonshared and public.</span></span> <span data-ttu-id="6e38c-111">Daha fazla bilgi için bkz. [Visual Basic erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="6e38c-111">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="6e38c-112">Kurallar</span><span class="sxs-lookup"><span data-stu-id="6e38c-112">Rules</span></span>  
  
- <span data-ttu-id="6e38c-113">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="6e38c-113">**Declaration Context.**</span></span> <span data-ttu-id="6e38c-114">Yalnızca modül düzeyinde `Shared` kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e38c-114">You can use `Shared` only at module level.</span></span> <span data-ttu-id="6e38c-115">Bu, bir `Shared` öğesi için bildirim bağlamının bir sınıf veya yapı olması ve kaynak dosya, ad alanı veya yordam olması anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="6e38c-115">This means the declaration context for a `Shared` element must be a class or structure, and cannot be a source file, namespace, or procedure.</span></span>  
  
- <span data-ttu-id="6e38c-116">**Birleşik değiştiriciler.**</span><span class="sxs-lookup"><span data-stu-id="6e38c-116">**Combined Modifiers.**</span></span> <span data-ttu-id="6e38c-117">Aynı bildirimde [geçersiz kılmalar](../../../visual-basic/language-reference/modifiers/overrides.md), geçersiz [kılınabilir](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)veya [static](../../../visual-basic/language-reference/modifiers/static.md) ile birlikte `Shared` belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e38c-117">You cannot specify `Shared` together with [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md), [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md), or [Static](../../../visual-basic/language-reference/modifiers/static.md) in the same declaration.</span></span>  
  
- <span data-ttu-id="6e38c-118">**Erişme.**</span><span class="sxs-lookup"><span data-stu-id="6e38c-118">**Accessing.**</span></span> <span data-ttu-id="6e38c-119">Bir paylaşılan öğeye, sınıfının veya yapısının belirli bir örneğinin değişken adıyla değil, sınıf veya yapı adıyla niteleyerek erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e38c-119">You access a shared element by qualifying it with its class or structure name, not with the variable name of a specific instance of its class or structure.</span></span> <span data-ttu-id="6e38c-120">Paylaşılan üyelerine erişmek için bir sınıf veya yapının örneğini oluşturmanız da gerekmez.</span><span class="sxs-lookup"><span data-stu-id="6e38c-120">You do not even have to create an instance of a class or structure to access its shared members.</span></span>  
  
     <span data-ttu-id="6e38c-121">Aşağıdaki örnek, <xref:System.Double> yapısı tarafından sunulan <xref:System.Double.IsNaN%2A> paylaşılan yordamı çağırır.</span><span class="sxs-lookup"><span data-stu-id="6e38c-121">The following example calls the shared procedure <xref:System.Double.IsNaN%2A> exposed by the <xref:System.Double> structure.</span></span>  
  
     `If Double.IsNaN(result) Then MsgBox("Result is mathematically undefined.")`  
  
- <span data-ttu-id="6e38c-122">**Örtük paylaşım.**</span><span class="sxs-lookup"><span data-stu-id="6e38c-122">**Implicit Sharing.**</span></span> <span data-ttu-id="6e38c-123">`Shared` değiştiricisini [const ifadesinde](../../../visual-basic/language-reference/statements/const-statement.md)kullanamazsınız, ancak sabitler örtülü olarak paylaşılır.</span><span class="sxs-lookup"><span data-stu-id="6e38c-123">You cannot use the `Shared` modifier in a [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md), but constants are implicitly shared.</span></span> <span data-ttu-id="6e38c-124">Benzer şekilde, bir modülün veya arabirimin üyesini `Shared`olarak bildiremezsiniz, ancak örtülü olarak paylaşılır.</span><span class="sxs-lookup"><span data-stu-id="6e38c-124">Similarly, you cannot declare a member of a module or an interface to be `Shared`, but they are implicitly shared.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="6e38c-125">Davranış</span><span class="sxs-lookup"><span data-stu-id="6e38c-125">Behavior</span></span>  
  
- <span data-ttu-id="6e38c-126">**Depo.**</span><span class="sxs-lookup"><span data-stu-id="6e38c-126">**Storage.**</span></span> <span data-ttu-id="6e38c-127">Paylaşılan bir değişken veya olay, sınıfı veya yapısını kaç tane veya birkaç örnek oluşturduğunuz ve bu durumda yalnızca bir kez bellekte depolanır.</span><span class="sxs-lookup"><span data-stu-id="6e38c-127">A shared variable or event is stored in memory only once, no matter how many or few instances you create of its class or structure.</span></span> <span data-ttu-id="6e38c-128">Benzer şekilde, paylaşılan bir yordam veya özellik yalnızca bir yerel değişken kümesi tutar.</span><span class="sxs-lookup"><span data-stu-id="6e38c-128">Similarly, a shared procedure or property holds only one set of local variables.</span></span>  
  
- <span data-ttu-id="6e38c-129">**Örnek değişkenine erişme.**</span><span class="sxs-lookup"><span data-stu-id="6e38c-129">**Accessing through an Instance Variable.**</span></span> <span data-ttu-id="6e38c-130">Kendi sınıfının veya yapısının belirli bir örneğini içeren bir değişkenin adı ile niteleyerek paylaşılan bir öğeye erişmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="6e38c-130">It is possible to access a shared element by qualifying it with the name of a variable that contains a specific instance of its class or structure.</span></span> <span data-ttu-id="6e38c-131">Bu, genellikle beklenen şekilde çalışsa da, derleyici bir uyarı mesajı oluşturur ve değişken yerine sınıf veya yapı adıyla erişimi yapar.</span><span class="sxs-lookup"><span data-stu-id="6e38c-131">Although this usually works as expected, the compiler generates a warning message and makes the access through the class or structure name instead of the variable.</span></span>  
  
- <span data-ttu-id="6e38c-132">**Örnek Ifadesiyle erişme.**</span><span class="sxs-lookup"><span data-stu-id="6e38c-132">**Accessing through an Instance Expression.**</span></span> <span data-ttu-id="6e38c-133">Sınıfının veya yapısının bir örneğini döndüren bir ifade aracılığıyla paylaşılan bir öğeye eriştiğinizde, derleyici, ifadeyi değerlendirmek yerine sınıf veya yapı adı üzerinden erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="6e38c-133">If you access a shared element through an expression that returns an instance of its class or structure, the compiler makes the access through the class or structure name instead of evaluating the expression.</span></span> <span data-ttu-id="6e38c-134">Bu, ifadenin diğer eylemleri gerçekleştirmesini ve örneği döndürmesini amaçlıyorsanız beklenmedik sonuçlar üretir.</span><span class="sxs-lookup"><span data-stu-id="6e38c-134">This produces unexpected results if you intended the expression to perform other actions as well as returning the instance.</span></span> <span data-ttu-id="6e38c-135">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="6e38c-135">The following example illustrates this.</span></span>  
  
    ```vb
    Sub main()  
        shareTotal.total = 10  
        ' The preceding line is the preferred way to access total.  
        Dim instanceVar As New shareTotal  
        instanceVar.total += 100  
        ' The preceding line generates a compiler warning message and  
        ' accesses total through class shareTotal instead of through  
        ' the variable instanceVar. This works as expected and adds  
        ' 100 to total.  
        returnClass().total += 1000  
        ' The preceding line generates a compiler warning message and  
        ' accesses total through class shareTotal instead of calling  
        ' returnClass(). This adds 1000 to total but does not work as  
        ' expected, because the MsgBox in returnClass() does not run.  
        MsgBox("Value of total is " & CStr(shareTotal.total))  
    End Sub  
    Public Function returnClass() As shareTotal  
        MsgBox("Function returnClass() called")  
        Return New shareTotal  
    End Function  
    Public Class shareTotal  
        Public Shared total As Integer  
    End Class  
    ```  
  
     <span data-ttu-id="6e38c-136">Önceki örnekte, derleyici her iki durumda da kodun paylaşılan değişkenine `total` bir örnek üzerinden eriştiği bir uyarı mesajı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6e38c-136">In the preceding example, the compiler generates a warning message both times the code accesses the shared variable `total` through an instance.</span></span> <span data-ttu-id="6e38c-137">Her durumda, erişimi doğrudan sınıf `shareTotal` aracılığıyla yapar ve herhangi bir örneği kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="6e38c-137">In each case it makes the access directly through the class `shareTotal` and does not make use of any instance.</span></span> <span data-ttu-id="6e38c-138">`returnClass`yordam çağrısı olması durumunda bu, `returnClass`bir çağrı üretmediği anlamına gelir; bu nedenle "Function returnClass ()" adlı Işlev "olarak adlandırılan ek eylem gerçekleştirilmez.</span><span class="sxs-lookup"><span data-stu-id="6e38c-138">In the case of the intended call to the procedure `returnClass`, this means it does not even generate a call to `returnClass`, so the additional action of displaying "Function returnClass() called" is not performed.</span></span>  
  
 <span data-ttu-id="6e38c-139">`Shared` değiştiricisi şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="6e38c-139">The `Shared` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="6e38c-140">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="6e38c-140">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="6e38c-141">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="6e38c-141">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="6e38c-142">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="6e38c-142">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="6e38c-143">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="6e38c-143">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="6e38c-144">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="6e38c-144">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="6e38c-145">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="6e38c-145">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="6e38c-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e38c-146">See also</span></span>

- [<span data-ttu-id="6e38c-147">Shadows</span><span class="sxs-lookup"><span data-stu-id="6e38c-147">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="6e38c-148">Static</span><span class="sxs-lookup"><span data-stu-id="6e38c-148">Static</span></span>](../../../visual-basic/language-reference/modifiers/static.md)
- [<span data-ttu-id="6e38c-149">Visual Basic ömrü</span><span class="sxs-lookup"><span data-stu-id="6e38c-149">Lifetime in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="6e38c-150">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="6e38c-150">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="6e38c-151">Yapılar</span><span class="sxs-lookup"><span data-stu-id="6e38c-151">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="6e38c-152">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="6e38c-152">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
