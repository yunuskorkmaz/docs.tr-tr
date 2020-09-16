---
title: Değişken Bildirimi
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], declaring
- member variables [Visual Basic], declarations
- Dim statement [Visual Basic], variable declaration
- declaring variables [Visual Basic]
- variables [Visual Basic], scope
- variables [Visual Basic], data types
- data types [Visual Basic], variable declarations
- lifetime [Visual Basic], variables
- variables [Visual Basic], lifetime
- access levels [Visual Basic], variables
- scope [Visual Basic], declaration statements
- variables [Visual Basic], access level
- local variables [Visual Basic], declarations
- scope [Visual Basic], variables
ms.assetid: d8f10226-92b1-480f-9f53-df377b2d7e15
ms.openlocfilehash: e3e2b6173a36490328801afd7fe711f1a003e2ae
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557482"
---
# <a name="variable-declaration-in-visual-basic"></a><span data-ttu-id="428f8-102">Visual Basic'de Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="428f8-102">Variable Declaration in Visual Basic</span></span>
<span data-ttu-id="428f8-103">Adını ve özelliklerini belirtmek için bir değişken bildirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="428f8-103">You declare a variable to specify its name and characteristics.</span></span> <span data-ttu-id="428f8-104">Değişkenler için bildirim bildirimi, [Dim deyimidir](../../../language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="428f8-104">The declaration statement for variables is the [Dim Statement](../../../language-reference/statements/dim-statement.md).</span></span> <span data-ttu-id="428f8-105">Konumu ve içeriği, değişkenin özelliklerini tespit.</span><span class="sxs-lookup"><span data-stu-id="428f8-105">Its location and contents determine the variable's characteristics.</span></span>  
  
 <span data-ttu-id="428f8-106">Değişken adlandırma kuralları ve konuları için bkz. [bildirilmemiş öğe adları](../declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="428f8-106">For variable naming rules and considerations, see [Declared Element Names](../declared-elements/declared-element-names.md).</span></span>  
  
## <a name="declaration-levels"></a><span data-ttu-id="428f8-107">Bildirim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="428f8-107">Declaration Levels</span></span>  
  
### <a name="local-and-member-variables"></a><span data-ttu-id="428f8-108">Yerel ve üye değişkenleri</span><span class="sxs-lookup"><span data-stu-id="428f8-108">Local and Member Variables</span></span>  
 <span data-ttu-id="428f8-109">*Yerel değişken* , bir yordam içinde belirtilen biridir.</span><span class="sxs-lookup"><span data-stu-id="428f8-109">A *local variable* is one that is declared within a procedure.</span></span> <span data-ttu-id="428f8-110">*Üye değişkeni* , Visual Basic türünün bir üyesidir; modül düzeyinde, bir sınıf, yapı veya modül içinde, ancak bu sınıf, yapı veya modülle iç yordam içinde değil, modül düzeyinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="428f8-110">A *member variable* is a member of a Visual Basic type; it is declared at module level, inside a class, structure, or module, but not within any procedure internal to that class, structure, or module.</span></span>  
  
### <a name="shared-and-instance-variables"></a><span data-ttu-id="428f8-111">Paylaşılan ve örnek değişkenleri</span><span class="sxs-lookup"><span data-stu-id="428f8-111">Shared and Instance Variables</span></span>  
 <span data-ttu-id="428f8-112">Bir sınıf veya yapıda, bir üye değişkeninin kategorisi paylaşılıp paylaşıldığına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="428f8-112">In a class or structure, the category of a member variable depends on whether or not it is shared.</span></span> <span data-ttu-id="428f8-113">[Paylaşılan](../../../language-reference/modifiers/shared.md) anahtar sözcüğü ile bildirilirse, *paylaşılan bir değişkendir*ve sınıf veya yapının tüm örnekleri arasında paylaşılan tek bir kopyada bulunur.</span><span class="sxs-lookup"><span data-stu-id="428f8-113">If it is declared with the [Shared](../../../language-reference/modifiers/shared.md) keyword, it is a *shared variable*, and it exists in a single copy shared among all instances of the class or structure.</span></span>  
  
 <span data-ttu-id="428f8-114">Aksi takdirde, bir *örnek değişkenidir*ve sınıfın ya da yapının her örneği için ayrı bir kopyası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="428f8-114">Otherwise it is an *instance variable*, and a separate copy of it is created for each instance of the class or structure.</span></span> <span data-ttu-id="428f8-115">Örnek değişkeninin belirli bir kopyası yalnızca oluşturulduğu sınıf veya yapının örneği için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="428f8-115">A given copy of an instance variable is available only to the instance of the class or structure in which it was created.</span></span> <span data-ttu-id="428f8-116">Sınıf veya yapının diğer örneğindeki örnek değişkeninin bir kopyasından bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="428f8-116">It is independent of a copy of the instance variable in any other instance of the class or structure.</span></span>  
  
## <a name="declaring-data-type"></a><span data-ttu-id="428f8-117">Veri türü bildirme</span><span class="sxs-lookup"><span data-stu-id="428f8-117">Declaring Data Type</span></span>  
 <span data-ttu-id="428f8-118">Bildirim deyimindeki [as](../../../language-reference/statements/as-clause.md) yan tümcesi, bildirdiğiniz değişkenin veri türünü veya nesne türünü tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="428f8-118">The [As](../../../language-reference/statements/as-clause.md) clause in the declaration statement allows you to define the data type or object type of the variable you are declaring.</span></span> <span data-ttu-id="428f8-119">Bir değişken için aşağıdaki türlerden herhangi birini belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="428f8-119">You can specify any of the following types for a variable:</span></span>  
  
- <span data-ttu-id="428f8-120">, Veya gibi bir Öğesel veri türü `Boolean` `Long``Decimal`</span><span class="sxs-lookup"><span data-stu-id="428f8-120">An elementary data type, such as `Boolean`, `Long`, or `Decimal`</span></span>  
  
- <span data-ttu-id="428f8-121">Dizi veya yapı gibi bir bileşik veri türü</span><span class="sxs-lookup"><span data-stu-id="428f8-121">A composite data type, such as an array or structure</span></span>  
  
- <span data-ttu-id="428f8-122">Uygulamanızda ya da başka bir uygulamada tanımlanan bir nesne türü veya sınıf</span><span class="sxs-lookup"><span data-stu-id="428f8-122">An object type, or class, defined either in your application or in another application</span></span>  
  
- <span data-ttu-id="428f8-123">Veya gibi bir .NET Framework sınıfı <xref:System.Windows.Forms.Label><xref:System.Windows.Forms.TextBox></span><span class="sxs-lookup"><span data-stu-id="428f8-123">A .NET Framework class, such as <xref:System.Windows.Forms.Label> or <xref:System.Windows.Forms.TextBox></span></span>  
  
- <span data-ttu-id="428f8-124">Veya gibi bir arabirim türü <xref:System.IComparable><xref:System.IDisposable></span><span class="sxs-lookup"><span data-stu-id="428f8-124">An interface type, such as <xref:System.IComparable> or <xref:System.IDisposable></span></span>  
  
 <span data-ttu-id="428f8-125">Veri türünü yinelemek zorunda kalmadan, tek bir bildirimde birkaç değişken bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="428f8-125">You can declare several variables in one statement without having to repeat the data type.</span></span> <span data-ttu-id="428f8-126">Aşağıdaki deyimlerde, ve değişkenleri tür olarak, ve ve olarak olarak `i` `j` `k` bildirilmiştir `Integer` `l` `m` `Long` `x` `y` `Single` :</span><span class="sxs-lookup"><span data-stu-id="428f8-126">In the following statements, the variables `i`, `j`, and `k` are declared as type `Integer`, `l` and `m` as `Long`, and `x` and `y` as `Single`:</span></span>  
  
```vb  
Dim i, j, k As Integer  
' All three variables in the preceding statement are declared as Integer.  
Dim l, m As Long, x, y As Single  
' In the preceding statement, l and m are Long, x and y are Single.  
```  
  
 <span data-ttu-id="428f8-127">Veri türleri hakkında daha fazla bilgi için bkz. [veri türleri](../data-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="428f8-127">For more information on data types, see [Data Types](../data-types/index.md).</span></span> <span data-ttu-id="428f8-128">Nesneler hakkında daha fazla bilgi için bkz. [nesneler ve sınıflar](../objects-and-classes/index.md) ve [bileşenlerle programlama](/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="428f8-128">For more information on objects, see [Objects and Classes](../objects-and-classes/index.md) and [Programming with Components](/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120)).</span></span>  
  
## <a name="local-type-inference"></a><span data-ttu-id="428f8-129">Yerel Tür Arabirimi</span><span class="sxs-lookup"><span data-stu-id="428f8-129">Local Type Inference</span></span>  
 <span data-ttu-id="428f8-130">*Tür çıkarımı* , yan tümce olmadan belirtilen yerel değişkenlerin veri türlerini belirlemede kullanılır `As` .</span><span class="sxs-lookup"><span data-stu-id="428f8-130">*Type inference* is used to determine the data types of local variables declared without an `As` clause.</span></span> <span data-ttu-id="428f8-131">Derleyici, değişkenin türünü başlatma ifadesinin türünden algılar.</span><span class="sxs-lookup"><span data-stu-id="428f8-131">The compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="428f8-132">Bu, açıkça bir tür belirtmeden değişkenleri bildirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="428f8-132">This enables you to declare variables without explicitly stating a type.</span></span> <span data-ttu-id="428f8-133">Aşağıdaki örnekte, her ikisi de `num1` `num2` kesin olarak tam sayı olarak türdedir.</span><span class="sxs-lookup"><span data-stu-id="428f8-133">In the following example, both `num1` and `num2` are strongly typed as integers.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]  
  
 <span data-ttu-id="428f8-134">Yerel tür çıkarımı kullanmak istiyorsanız, `Option Infer` olarak ayarlanması gerekir `On` .</span><span class="sxs-lookup"><span data-stu-id="428f8-134">If you want to use local type inference, `Option Infer` must be set to `On`.</span></span> <span data-ttu-id="428f8-135">Daha fazla bilgi için bkz. [Yerel tür çıkarımı](local-type-inference.md) ve [Option Infer deyimleri](../../../language-reference/statements/option-infer-statement.md).</span><span class="sxs-lookup"><span data-stu-id="428f8-135">For more information, see [Local Type Inference](local-type-inference.md) and [Option Infer Statement](../../../language-reference/statements/option-infer-statement.md).</span></span>  
  
## <a name="characteristics-of-declared-variables"></a><span data-ttu-id="428f8-136">Belirtilen değişkenlerin özellikleri</span><span class="sxs-lookup"><span data-stu-id="428f8-136">Characteristics of Declared Variables</span></span>  
 <span data-ttu-id="428f8-137">Bir değişkenin kullanım *ömrü* , kullanım için kullanılabilir olduğu süredir.</span><span class="sxs-lookup"><span data-stu-id="428f8-137">The *lifetime* of a variable is the period of time during which it is available for use.</span></span> <span data-ttu-id="428f8-138">Genel olarak, bir değişken, kendisini bildiren öğe (bir yordam veya sınıf gibi) var olmaya devam ettiği sürece vardır.</span><span class="sxs-lookup"><span data-stu-id="428f8-138">In general, a variable exists as long as the element that declares it (such as a procedure or class) continues to exist.</span></span> <span data-ttu-id="428f8-139">Değişkenin, kapsayan öğesinin yaşam süresinden daha fazla devam etmesi gerekmiyorsa, bildirimde özel bir şey yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="428f8-139">If the variable does not need to continue existing beyond the lifetime of its containing element, you do not need to do anything special in the declaration.</span></span> <span data-ttu-id="428f8-140">Değişkenin, kapsayan öğesinden daha uzun bir süre içinde var olmaya devam etmesi gerekiyorsa, `Static` veya `Shared` anahtar sözcüğünü `Dim` ifadesine ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="428f8-140">If the variable needs to continue to exist longer than its containing element, you can include the `Static` or `Shared` keyword in its `Dim` statement.</span></span> <span data-ttu-id="428f8-141">Daha fazla bilgi için [Visual Basic ömrü](../declared-elements/lifetime.md)' ne bakın.</span><span class="sxs-lookup"><span data-stu-id="428f8-141">For more information, see [Lifetime in Visual Basic](../declared-elements/lifetime.md).</span></span>  
  
 <span data-ttu-id="428f8-142">Bir değişkenin *kapsamı* , adını nitelemeden kendisine başvurabilen tüm kod kümesidir.</span><span class="sxs-lookup"><span data-stu-id="428f8-142">The *scope* of a variable is the set of all code that can refer to it without qualifying its name.</span></span> <span data-ttu-id="428f8-143">Bir değişkenin kapsamı, bildirildiği yere göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="428f8-143">A variable's scope is determined by where it is declared.</span></span> <span data-ttu-id="428f8-144">Belirli bir bölgede bulunan kod, adlarını nitelemek zorunda kalmadan bu bölgede tanımlanan değişkenleri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="428f8-144">Code located in a given region can use the variables defined in that region without having to qualify their names.</span></span> <span data-ttu-id="428f8-145">Daha fazla bilgi için [Visual Basic kapsam](../declared-elements/scope.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="428f8-145">For more information, see [Scope in Visual Basic](../declared-elements/scope.md).</span></span>  
  
 <span data-ttu-id="428f8-146">Bir değişkenin *erişim düzeyi* , erişim izni olan kodun kapsamı olur.</span><span class="sxs-lookup"><span data-stu-id="428f8-146">A variable's *access level* is the extent of code that has permission to access it.</span></span> <span data-ttu-id="428f8-147">Bu, bildiriminde kullandığınız erişim değiştiricisine ( [genel](../../../language-reference/modifiers/public.md) veya [özel](../../../language-reference/modifiers/private.md)) göre belirlenir `Dim` .</span><span class="sxs-lookup"><span data-stu-id="428f8-147">This is determined by the access modifier (such as [Public](../../../language-reference/modifiers/public.md) or [Private](../../../language-reference/modifiers/private.md)) that you use in the `Dim` statement.</span></span> <span data-ttu-id="428f8-148">Daha fazla bilgi için bkz. [Visual Basic erişim düzeyleri](../declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="428f8-148">For more information, see [Access levels in Visual Basic](../declared-elements/access-levels.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="428f8-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="428f8-149">See also</span></span>

- [<span data-ttu-id="428f8-150">Nasıl yapılır: Yeni Değişken Oluşturma</span><span class="sxs-lookup"><span data-stu-id="428f8-150">How to: Create a New Variable</span></span>](how-to-create-a-new-variable.md)
- [<span data-ttu-id="428f8-151">Nasıl yapılır: Bir Değişkende Veri Ekleme Çıkarma</span><span class="sxs-lookup"><span data-stu-id="428f8-151">How to: Move Data Into and Out of a Variable</span></span>](how-to-move-data-into-and-out-of-a-variable.md)
- [<span data-ttu-id="428f8-152">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="428f8-152">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="428f8-153">Korunamadı</span><span class="sxs-lookup"><span data-stu-id="428f8-153">Protected</span></span>](../../../language-reference/modifiers/protected.md)
- [<span data-ttu-id="428f8-154">Arkadaş</span><span class="sxs-lookup"><span data-stu-id="428f8-154">Friend</span></span>](../../../language-reference/modifiers/friend.md)
- [<span data-ttu-id="428f8-155">Static</span><span class="sxs-lookup"><span data-stu-id="428f8-155">Static</span></span>](../../../language-reference/modifiers/static.md)
- [<span data-ttu-id="428f8-156">Bildirilen Öğe Özellikleri</span><span class="sxs-lookup"><span data-stu-id="428f8-156">Declared Element Characteristics</span></span>](../declared-elements/declared-element-characteristics.md)
- [<span data-ttu-id="428f8-157">Yerel Tür Arabirimi</span><span class="sxs-lookup"><span data-stu-id="428f8-157">Local Type Inference</span></span>](local-type-inference.md)
- [<span data-ttu-id="428f8-158">Option Infer Deyimi</span><span class="sxs-lookup"><span data-stu-id="428f8-158">Option Infer Statement</span></span>](../../../language-reference/statements/option-infer-statement.md)
