---
title: With...End With Deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.With
helpviewer_keywords:
- With keyword [Visual Basic]
- loop structures [Visual Basic], and With...End With statements
- execution [Visual Basic], on object
- instructions, repeating
- With...End With statements [Visual Basic]
- With statement [Visual Basic]
- With statement [Visual Basic], nesting
- objects [Visual Basic], accessing
- With block
- End keyword [Visual Basic], With...End With statements
ms.assetid: 340d5fbb-4f43-48ec-a024-80843c137817
ms.openlocfilehash: de2edc6b16689673c3be6703ff1a201febe73526
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698648"
---
# <a name="withend-with-statement-visual-basic"></a><span data-ttu-id="73788-102">With...End With Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="73788-102">With...End With Statement (Visual Basic)</span></span>
<span data-ttu-id="73788-103">Deyimlerin, nesne veya yapı üyelerine erişim sağlarken basitleştirilmiş bir sözdizimi kullanabilmesi için sürekli olarak tek bir nesneye veya yapıya başvuran bir dizi deyim yürütür.</span><span class="sxs-lookup"><span data-stu-id="73788-103">Executes a series of statements that repeatedly refer to a single object or structure so that the statements can use a simplified syntax when accessing members of the object or structure.</span></span>  <span data-ttu-id="73788-104">Bir yapı kullanırken yalnızca üyelerinin değerlerini okuyabilir veya çağırma yöntemlerinin ve kullanılan bir yapının üyelerine değer atamak çalışırsanız hata alırsınız bir `With...End With` deyimi.</span><span class="sxs-lookup"><span data-stu-id="73788-104">When using a structure, you can only read the values of members or invoke methods, and you get an error if you try to assign values to members of a structure used in a `With...End With` statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73788-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="73788-105">Syntax</span></span>  
  
```  
With objectExpression  
    [ statements ]  
End With  
```  
  
## <a name="parts"></a><span data-ttu-id="73788-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="73788-106">Parts</span></span>  
  
|<span data-ttu-id="73788-107">Terim</span><span class="sxs-lookup"><span data-stu-id="73788-107">Term</span></span>|<span data-ttu-id="73788-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="73788-108">Definition</span></span>|  
|---|---|  
|`objectExpression`|<span data-ttu-id="73788-109">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="73788-109">Required.</span></span> <span data-ttu-id="73788-110">Nesne olarak değerlendirilen bir ifade.</span><span class="sxs-lookup"><span data-stu-id="73788-110">An expression that evaluates to an object.</span></span> <span data-ttu-id="73788-111">İfade rasgele karmaşık olabilir ve yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="73788-111">The expression may be arbitrarily complex and is evaluated only once.</span></span> <span data-ttu-id="73788-112">İfade, basit türler de dahil olmak üzere herhangi bir veri türü olarak değerlendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="73788-112">The expression can evaluate to any data type, including elementary types.</span></span>|  
|`statements`|<span data-ttu-id="73788-113">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="73788-113">Optional.</span></span> <span data-ttu-id="73788-114">Bir veya daha fazla deyim arasında `With` ve `End With` öğesinin değerlendirilmesiyle oluşturulan bir nesnenin üyelerine başvuruda `objectExpression`.</span><span class="sxs-lookup"><span data-stu-id="73788-114">One or more statements between `With` and `End With` that may refer to members of an object that's produced by the evaluation of `objectExpression`.</span></span>|  
|`End With`|<span data-ttu-id="73788-115">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="73788-115">Required.</span></span> <span data-ttu-id="73788-116">Tanımını sonlandırır `With` blok.</span><span class="sxs-lookup"><span data-stu-id="73788-116">Terminates the definition of the `With` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73788-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="73788-117">Remarks</span></span>  
 <span data-ttu-id="73788-118">Kullanarak `With...End With`, nesnenin adını birçok kez belirtmeden belirtilen bir nesne üzerinde bir dizi deyim gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73788-118">By using `With...End With`, you can perform a series of statements on a specified object without specifying the name of the object multiple times.</span></span> <span data-ttu-id="73788-119">İçinde bir `With` deyim bloğunu belirtebileceğiniz bir nokta ile başlayan nesnenin bir üyesi olarak `With` deyim nesnesi varmış.</span><span class="sxs-lookup"><span data-stu-id="73788-119">Within a `With` statement block, you can specify a member of the object starting with a period, as if the `With` statement object preceded it.</span></span>  
  
 <span data-ttu-id="73788-120">Örneğin, tek bir nesnede birden çok özelliklerini değiştirmek için özellik atama deyimlerini içine yerleştirin. `With...End With` nesnesine yalnızca bir kez her özellik ataması için bir kez yerine başvuran bloğu.</span><span class="sxs-lookup"><span data-stu-id="73788-120">For example, to change multiple properties on a single object, place the property assignment statements inside the `With...End With` block, referring to the object only once instead of once for each property assignment.</span></span>  
  
 <span data-ttu-id="73788-121">Kodunuzu birden fazla deyimde aynı nesneye erişirse, aşağıdaki faydaları kullanarak elde `With` deyimi:</span><span class="sxs-lookup"><span data-stu-id="73788-121">If your code accesses the same object in multiple statements, you gain the following benefits by using the `With` statement:</span></span>  
  
- <span data-ttu-id="73788-122">Karmaşık ifadenin üyelerine birden çok kez başvuruda bulunmak için sonucu geçici bir değişkene atamanıza veya karmaşık ifadeyi birden çok kez değerlendirmenize gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="73788-122">You don't need to evaluate a complex expression multiple times or assign the result to a temporary variable to refer to its members multiple times.</span></span>  
  
- <span data-ttu-id="73788-123">Yinelenen niteleyici ifadeleri ortadan kaldırarak kodunuzu daha okunur hale getirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73788-123">You make your code more readable by eliminating repetitive qualifying expressions.</span></span>  
  
 <span data-ttu-id="73788-124">Veri türü `objectExpression` gibi herhangi bir sınıf veya yapı türü veya hatta bir Visual Basic basit türü olabilir `Integer`.</span><span class="sxs-lookup"><span data-stu-id="73788-124">The data type of `objectExpression` can be any class or structure type or even a Visual Basic elementary type such as `Integer`.</span></span>  <span data-ttu-id="73788-125">Varsa `objectExpression` sonuçları dışında herhangi bir nesne, yalnızca üyelerinin değerlerini okuyabilir veya çağırma yöntemlerinin ve kullanılan bir yapının üyelerine değer atamak çalışırsanız hata alırsınız bir `With...End With` deyimi.</span><span class="sxs-lookup"><span data-stu-id="73788-125">If `objectExpression` results in anything other than an object, you can only read the values of its members or invoke methods, and you get an error if you try to assign values to members of a structure used in a `With...End With` statement.</span></span>  <span data-ttu-id="73788-126">Aynı hata, yapı döndüren ve hemen erişilen ve bir değer gibi işlev sonucunun bir üyesine atanmış bir yöntemi çağırdığınız alma budur `GetAPoint().x = 1`.</span><span class="sxs-lookup"><span data-stu-id="73788-126">This is the same error you would get if you invoked a method that returned a structure and immediately accessed and assigned a value to a member of the function’s result, such as `GetAPoint().x = 1`.</span></span>  <span data-ttu-id="73788-127">İki durumda da sorun şudur: Yapı yalnızca çağrı yığınında mevcuttur ve değiştirilmiş bir yapı üyesinin bu durumlarda, programdaki diğer herhangi bir kodun değişikliği gözlemleyebileceği şekilde bir konuma yazabilmesinin hiçbir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="73788-127">The problem in both cases is that the structure exists only on the call stack, and there is no way a modified structure member in these situations can write to  a location such that any other code in the program can observe the change.</span></span>  
  
 <span data-ttu-id="73788-128">`objectExpression` Bloğuna girişte bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="73788-128">The `objectExpression` is evaluated once, upon entry into the block.</span></span> <span data-ttu-id="73788-129">Atayamazsınız `objectExpression` içinden `With` blok.</span><span class="sxs-lookup"><span data-stu-id="73788-129">You can't reassign the `objectExpression` from within the `With` block.</span></span>  
  
 <span data-ttu-id="73788-130">İçinde bir `With` bloğu bunları nitelemeden yalnızca belirtilen nesnenin özellikleri ve yöntemleri erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73788-130">Within a `With` block, you can access the methods and properties of only the specified object without qualifying them.</span></span> <span data-ttu-id="73788-131">Diğer nesnelerin yöntemlerini ve özelliklerini kullanabilirsiniz, ancak bunları nesne adlarıyla nitelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="73788-131">You can use methods and properties of other objects, but you must qualify them with their object names.</span></span>  
  
 <span data-ttu-id="73788-132">Bir yerleştirebilirsiniz `With...End With` deyimi içinde başka bir.</span><span class="sxs-lookup"><span data-stu-id="73788-132">You can place one `With...End With` statement within another.</span></span> <span data-ttu-id="73788-133">İç içe geçmiş `With...End With` deyimleri için başvurulan nesneler bağlamdan açık değilse kafa karıştırıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="73788-133">Nested `With...End With` statements may be confusing if the objects that are being referred to aren't clear from context.</span></span> <span data-ttu-id="73788-134">Bir dış bir nesne için tam bir başvuru sağlamalısınız `With` nesne bir iç başvuruluyor, block `With` blok.</span><span class="sxs-lookup"><span data-stu-id="73788-134">You must provide a fully qualified reference to an object that's in an outer `With` block when the object is referenced from within an inner `With` block.</span></span>  
  
 <span data-ttu-id="73788-135">Dal oluşturamazsınız bir `With` deyim bloğuna bloğun dışından.</span><span class="sxs-lookup"><span data-stu-id="73788-135">You can't branch into a `With` statement block from outside the block.</span></span>  
  
 <span data-ttu-id="73788-136">Blok bir döngü içermediği sürece deyimler yalnızca bir kez çalışır.</span><span class="sxs-lookup"><span data-stu-id="73788-136">Unless the block contains a loop, the statements run only once.</span></span> <span data-ttu-id="73788-137">Farklı türlerde denetim yapılarını iç içe yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73788-137">You can nest different kinds of control structures.</span></span> <span data-ttu-id="73788-138">Daha fazla bilgi için [iç içe geçmiş denetim yapıları](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="73788-138">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="73788-139">Kullanabileceğiniz `With` anahtar sözcüğünü nesne başlatıcılarda da.</span><span class="sxs-lookup"><span data-stu-id="73788-139">You can use the `With` keyword in object initializers also.</span></span> <span data-ttu-id="73788-140">Daha fazla bilgi ve örnekler için bkz. [nesne başlatıcıları: Adlandırılmış ve anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) ve [anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="73788-140">For more information and examples, see [Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) and [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
>   
>  <span data-ttu-id="73788-141">Kullanıyorsanız, bir `With` blok özelliklerle veya alanlarla hemen kullanmanızın, bir nesnenin yalnızca başlatmak için bir nesne Başlatıcı kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="73788-141">If you're using a `With` block only to initialize the properties or fields of an object that you've just instantiated, consider using an object initializer instead.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73788-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="73788-142">Example</span></span>  
 <span data-ttu-id="73788-143">Aşağıdaki örnekte, her `With` blok, tek bir nesne üzerinde bir dizi deyim yürütür.</span><span class="sxs-lookup"><span data-stu-id="73788-143">In the following example, each `With` block executes a series of statements on a single object.</span></span>  
  
 [!code-vb[VbVbalrWithStatement#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrwithstatement/vb/mainwindow.xaml.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="73788-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="73788-144">Example</span></span>  
 <span data-ttu-id="73788-145">Aşağıdaki örnek Yuvalar `With…End With` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="73788-145">The following example nests `With…End With` statements.</span></span> <span data-ttu-id="73788-146">İç içe içinde `With` deyimi, sözdizimi içteki nesneye başvurur.</span><span class="sxs-lookup"><span data-stu-id="73788-146">Within the nested `With` statement, the syntax refers to the inner object.</span></span>  
  
 [!code-vb[VbVbalrWithStatement#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrwithstatement/vb/mainwindow.xaml.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="73788-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73788-147">See also</span></span>

- <xref:System.Collections.Generic.List%601>
- [<span data-ttu-id="73788-148">İç İçe Geçmiş Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="73788-148">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="73788-149">Nesne başlatıcıları: Adlandırılmış ve anonim türler</span><span class="sxs-lookup"><span data-stu-id="73788-149">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="73788-150">Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="73788-150">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
