---
title: Shared (Visual Basic)
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
ms.openlocfilehash: b15dd08d69f372317b9140001e8072eeb66d44ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604555"
---
# <a name="shared-visual-basic"></a><span data-ttu-id="09244-102">Shared (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="09244-102">Shared (Visual Basic)</span></span>
<span data-ttu-id="09244-103">Bir veya daha fazla bildirilen programlama öğeleri ile bir sınıf veya yapı büyük ve değil sınıf veya yapı belirli bir örneği ile ilişkili olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="09244-103">Specifies that one or more declared programming elements are associated with a class or structure at large, and not with a specific instance of the class or structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09244-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="09244-104">Remarks</span></span>  
  
## <a name="when-to-use-shared"></a><span data-ttu-id="09244-105">Ne zaman kullanılacağı paylaşılan</span><span class="sxs-lookup"><span data-stu-id="09244-105">When to Use Shared</span></span>  
 <span data-ttu-id="09244-106">Bir sınıf veya yapı üyesi paylaşımı kullanılabilir hale getirir, her örneği için yerine *paylaşılmayan*, burada her örneğinin kendi kopyasını tutar.</span><span class="sxs-lookup"><span data-stu-id="09244-106">Sharing a member of a class or structure makes it available to every instance, rather than *nonshared*, where each instance keeps its own copy.</span></span> <span data-ttu-id="09244-107">Bir değişkenin değeri uygulamanın tümünü uygulanıyorsa, örneğin, kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="09244-107">This is useful, for example, if the value of a variable applies to the entire application.</span></span> <span data-ttu-id="09244-108">Olması için bu değişkeni bildirirseniz `Shared`, ardından tüm örnekleri aynı depolama konumuna erişim ve bir örnek değişkenin değeri değişirse, tüm örnekler güncelleştirilmiş değeri erişim.</span><span class="sxs-lookup"><span data-stu-id="09244-108">If you declare that variable to be `Shared`, then all instances access the same storage location, and if one instance changes the variable's value, all instances access the updated value.</span></span>  
  
 <span data-ttu-id="09244-109">Paylaşım erişim düzeyi üyenin değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="09244-109">Sharing does not alter the access level of a member.</span></span> <span data-ttu-id="09244-110">Örneğin, bir sınıf üyesi paylaşılabilir ve özel (sınıf içinde erişilebilir yalnızca gelen), ya da paylaşılmayan hem de genel.</span><span class="sxs-lookup"><span data-stu-id="09244-110">For example, a class member can be shared and private (accessible only from within the class), or nonshared and public.</span></span> <span data-ttu-id="09244-111">Daha fazla bilgi için bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="09244-111">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="09244-112">Kurallar</span><span class="sxs-lookup"><span data-stu-id="09244-112">Rules</span></span>  
  
-   <span data-ttu-id="09244-113">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="09244-113">**Declaration Context.**</span></span> <span data-ttu-id="09244-114">Kullanabileceğiniz `Shared` yalnızca modülü düzeyinde.</span><span class="sxs-lookup"><span data-stu-id="09244-114">You can use `Shared` only at module level.</span></span> <span data-ttu-id="09244-115">Bu bildirimi bağlamının anlamına gelir bir `Shared` öğesi bir sınıf veya yapı olması ve kaynak dosyasını, ad alanı veya yordam olamaz.</span><span class="sxs-lookup"><span data-stu-id="09244-115">This means the declaration context for a `Shared` element must be a class or structure, and cannot be a source file, namespace, or procedure.</span></span>  
  
-   <span data-ttu-id="09244-116">**Birleşik değiştirici.**</span><span class="sxs-lookup"><span data-stu-id="09244-116">**Combined Modifiers.**</span></span> <span data-ttu-id="09244-117">Belirtemeyeceğiniz `Shared` ile birlikte [geçersiz kılmaları](../../../visual-basic/language-reference/modifiers/overrides.md), [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md), veya [ Statik](../../../visual-basic/language-reference/modifiers/static.md) aynı bildirimi.</span><span class="sxs-lookup"><span data-stu-id="09244-117">You cannot specify `Shared` together with [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md), [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md), or [Static](../../../visual-basic/language-reference/modifiers/static.md) in the same declaration.</span></span>  
  
-   <span data-ttu-id="09244-118">**Erişme.**</span><span class="sxs-lookup"><span data-stu-id="09244-118">**Accessing.**</span></span> <span data-ttu-id="09244-119">Sınıf veya yapı adıyla birlikte, belirli bir sınıf ya da yapısı örneği değişken adını bilgisayardı niteleme tarafından paylaşılan bir öğenin erişin.</span><span class="sxs-lookup"><span data-stu-id="09244-119">You access a shared element by qualifying it with its class or structure name, not with the variable name of a specific instance of its class or structure.</span></span> <span data-ttu-id="09244-120">Hatta sınıfı veya paylaşılan üyelerine erişmek için yapısının bir örneğini oluşturmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="09244-120">You do not even have to create an instance of a class or structure to access its shared members.</span></span>  
  
     <span data-ttu-id="09244-121">Aşağıdaki örnek paylaşılan yordam çağrıları <xref:System.Double.IsNaN%2A> tarafından sunulan <xref:System.Double> yapısı.</span><span class="sxs-lookup"><span data-stu-id="09244-121">The following example calls the shared procedure <xref:System.Double.IsNaN%2A> exposed by the <xref:System.Double> structure.</span></span>  
  
     `If Double.IsNaN(result) Then MsgBox("Result is mathematically undefined.")`  
  
-   <span data-ttu-id="09244-122">**Örtük paylaşımı.**</span><span class="sxs-lookup"><span data-stu-id="09244-122">**Implicit Sharing.**</span></span> <span data-ttu-id="09244-123">Kullanamazsınız `Shared` değiştiricisi bir [Const deyimi](../../../visual-basic/language-reference/statements/const-statement.md), ancak sabitleri örtük olarak paylaşılan.</span><span class="sxs-lookup"><span data-stu-id="09244-123">You cannot use the `Shared` modifier in a [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md), but constants are implicitly shared.</span></span> <span data-ttu-id="09244-124">Benzer şekilde, olması için bir modül veya üyesi bir arabirim bildiremezsiniz `Shared`, ancak örtük olarak paylaşılır.</span><span class="sxs-lookup"><span data-stu-id="09244-124">Similarly, you cannot declare a member of a module or an interface to be `Shared`, but they are implicitly shared.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="09244-125">Davranış</span><span class="sxs-lookup"><span data-stu-id="09244-125">Behavior</span></span>  
  
-   <span data-ttu-id="09244-126">**depolama alanı.**</span><span class="sxs-lookup"><span data-stu-id="09244-126">**Storage.**</span></span> <span data-ttu-id="09244-127">Yalnızca kaç veya birkaç örneği olsun, kendi sınıf veya yapı oluşturduktan sonra bir paylaşılan değişken veya olay bellekte depolanır.</span><span class="sxs-lookup"><span data-stu-id="09244-127">A shared variable or event is stored in memory only once, no matter how many or few instances you create of its class or structure.</span></span> <span data-ttu-id="09244-128">Benzer şekilde, bir paylaşılan bir yordam veya özellik, yerel değişkenleri yalnızca bir kümesi tutar.</span><span class="sxs-lookup"><span data-stu-id="09244-128">Similarly, a shared procedure or property holds only one set of local variables.</span></span>  
  
-   <span data-ttu-id="09244-129">**Bir örnek değişkeni erişme.**</span><span class="sxs-lookup"><span data-stu-id="09244-129">**Accessing through an Instance Variable.**</span></span> <span data-ttu-id="09244-130">Belirli bir sınıf ya da yapısı örneği içeren bir değişkeni adı ile niteleme tarafından paylaşılan bir öğesine erişmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="09244-130">It is possible to access a shared element by qualifying it with the name of a variable that contains a specific instance of its class or structure.</span></span> <span data-ttu-id="09244-131">Bu genellikle beklendiği gibi çalışır, ancak derleyici bir uyarı iletisi oluşturur ve sınıf veya yapı adı değişkeni yerine üzerinden erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="09244-131">Although this usually works as expected, the compiler generates a warning message and makes the access through the class or structure name instead of the variable.</span></span>  
  
-   <span data-ttu-id="09244-132">**Bir örneği ifade yoluyla erişme.**</span><span class="sxs-lookup"><span data-stu-id="09244-132">**Accessing through an Instance Expression.**</span></span> <span data-ttu-id="09244-133">Paylaşılan bir öğe, sınıf veya yapı örneğini döndüren bir ifadeye erişirseniz, derleyici ifade değerlendirme yerine sınıf veya yapı adı ile erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="09244-133">If you access a shared element through an expression that returns an instance of its class or structure, the compiler makes the access through the class or structure name instead of evaluating the expression.</span></span> <span data-ttu-id="09244-134">Diğer eylemlerin yanı sıra örneği döndüren gerçekleştirmek için ifade amaçlıyorsanız bu beklenmeyen sonuçlar üretir.</span><span class="sxs-lookup"><span data-stu-id="09244-134">This produces unexpected results if you intended the expression to perform other actions as well as returning the instance.</span></span> <span data-ttu-id="09244-135">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="09244-135">The following example illustrates this.</span></span>  
  
    ```  
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
  
     <span data-ttu-id="09244-136">Önceki örnekte derleyici bir uyarı iletisi kodu paylaşılan değişken erişen her iki kez oluşturur `total` bir örnek üzerinden.</span><span class="sxs-lookup"><span data-stu-id="09244-136">In the preceding example, the compiler generates a warning message both times the code accesses the shared variable `total` through an instance.</span></span> <span data-ttu-id="09244-137">Her durumda kolaylaştırır sınıfı aracılığıyla doğrudan erişim `shareTotal` ve kullanmayan herhangi bir örneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="09244-137">In each case it makes the access directly through the class `shareTotal` and does not make use of any instance.</span></span> <span data-ttu-id="09244-138">Yordam hedeflenen çağrısı durumunda `returnClass`, bu, hatta oluşturmaz yapılan bir çağrı anlamına gelir `returnClass`, "olarak adlandırılan işlevi returnClass()" görüntüleme başka bir işlem gerçekleştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="09244-138">In the case of the intended call to the procedure `returnClass`, this means it does not even generate a call to `returnClass`, so the additional action of displaying "Function returnClass() called" is not performed.</span></span>  
  
 <span data-ttu-id="09244-139">`Shared` Değiştiricisi bu bağlamlarında kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="09244-139">The `Shared` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="09244-140">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="09244-140">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="09244-141">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="09244-141">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="09244-142">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="09244-142">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="09244-143">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="09244-143">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="09244-144">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="09244-144">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="09244-145">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="09244-145">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="09244-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="09244-146">See Also</span></span>  
 [<span data-ttu-id="09244-147">Shadows</span><span class="sxs-lookup"><span data-stu-id="09244-147">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="09244-148">Static</span><span class="sxs-lookup"><span data-stu-id="09244-148">Static</span></span>](../../../visual-basic/language-reference/modifiers/static.md)  
 [<span data-ttu-id="09244-149">Visual Basic'de ömür</span><span class="sxs-lookup"><span data-stu-id="09244-149">Lifetime in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [<span data-ttu-id="09244-150">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="09244-150">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="09244-151">Yapılar</span><span class="sxs-lookup"><span data-stu-id="09244-151">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="09244-152">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="09244-152">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
