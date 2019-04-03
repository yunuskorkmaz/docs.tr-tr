---
title: Yerel Türü Arabirimi (Visual Basic Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- local type inference
- vb.TypeInfer
helpviewer_keywords:
- Option Infer statement [Visual Basic]
- local type inference [Visual Basic]
- implicitly-typed local variables [Visual Basic]
- variables [Visual Basic], type inference
- inference [Visual Basic]
- type inference [Visual Basic]
ms.assetid: b8307f18-2e56-4ab3-a45a-826873f400f6
ms.openlocfilehash: e6214938262b987a1bae4a9ca1d5c945f8b7fe6e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826827"
---
# <a name="local-type-inference-visual-basic"></a><span data-ttu-id="90f82-102">Yerel Türü Arabirimi (Visual Basic Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="90f82-102">Local Type Inference (Visual Basic)</span></span>
<span data-ttu-id="90f82-103">Visual Basic Derleyicisi kullanan *anlam çıkarma* olmadan bildirilen yerel değişkenlerin veri türlerini belirlemek için bir `As` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="90f82-103">The Visual Basic compiler uses *type inference* to determine the data types of local variables declared without an `As` clause.</span></span> <span data-ttu-id="90f82-104">Derleyici, başlatma ifadesinin türünden değişkeninin türü çıkarır.</span><span class="sxs-lookup"><span data-stu-id="90f82-104">The compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="90f82-105">Bu, açıkça bir türü bildirmeden aşağıdaki örnekte gösterildiği gibi değişkenleri tanımlayın sağlar.</span><span class="sxs-lookup"><span data-stu-id="90f82-105">This enables you to declare variables without explicitly stating a type, as shown in the following example.</span></span> <span data-ttu-id="90f82-106">Bildirimleri sonucu olarak hem de `num1` ve `num2` tamsayı olarak kesin olarak belirlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="90f82-106">As a result of the declarations, both `num1` and `num2` are strongly typed as integers.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]  
 
> [!NOTE]
>  <span data-ttu-id="90f82-107">İstemiyorsanız, `num2` olarak yazılması için önceki örnekte bir `Integer`, gibi bir bildirim kullanarak başka bir tür belirtebilirsiniz `Dim num3 As Object = 3` veya `Dim num4 As Double = 3`.</span><span class="sxs-lookup"><span data-stu-id="90f82-107">If you do not want `num2` in the previous example to be typed as an `Integer`, you can specify another type by using a declaration like `Dim num3 As Object = 3` or `Dim num4 As Double = 3`.</span></span>  

> [!NOTE]
>  <span data-ttu-id="90f82-108">Tür çıkarımı, yalnızca statik olmayan yerel değişkenler için kullanılabilir. sınıf alanlar, özellikler veya İşlevler türünü belirlemek için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="90f82-108">Type inference can be used only for non-static local variables; it cannot be used to determine the type of class fields, properties, or functions.</span></span>
 
 <span data-ttu-id="90f82-109">Yerel tür çıkarımı yordamı düzeyinde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="90f82-109">Local type inference applies at procedure level.</span></span> <span data-ttu-id="90f82-110">Modül düzeyinde (bir sınıf, yapı, modül veya arabirimi içinde ancak bir yordam veya blok içinde değil) değişkenler bildirmek için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="90f82-110">It cannot be used to declare variables at module level (within a class, structure, module, or interface but not within a procedure or block).</span></span> <span data-ttu-id="90f82-111">Varsa `num2` önceki örnekte yerine yerel bir değişken bir yordamda bir sınıfının bir alanı, bildirimi ile ilgili bir hata oluşturabilecek `Option Strict` ve sınıflandırabilir `num2` olarak bir `Object` ile `Option Strict` devre dışı.</span><span class="sxs-lookup"><span data-stu-id="90f82-111">If `num2` in the previous example were a field of a class instead of a local variable in a procedure, the declaration would cause an error with `Option Strict` on, and would classify `num2` as an `Object` with `Option Strict` off.</span></span> <span data-ttu-id="90f82-112">Benzer şekilde, yerel tür çıkarımı olarak bildirilen yordam düzeyi değişkenler uygulanmaz `Static`.</span><span class="sxs-lookup"><span data-stu-id="90f82-112">Similarly, local type inference does not apply to procedure level variables declared as `Static`.</span></span>  
  
## <a name="type-inference-vs-late-binding"></a><span data-ttu-id="90f82-113">Çıkarım vs yazın. Geç bağlama</span><span class="sxs-lookup"><span data-stu-id="90f82-113">Type Inference vs. Late Binding</span></span>  
 <span data-ttu-id="90f82-114">Tür çıkarımı kullanan kod geç bağlama kullanan koda benzer.</span><span class="sxs-lookup"><span data-stu-id="90f82-114">Code that uses type inference resembles code that relies on late binding.</span></span> <span data-ttu-id="90f82-115">Tür çıkarımı kesin olarak bırakmak yerine değişken türleri ancak `Object`.</span><span class="sxs-lookup"><span data-stu-id="90f82-115">However, type inference strongly types the variable instead of leaving it as `Object`.</span></span> <span data-ttu-id="90f82-116">Derleyici, değişkenin türüne erken bağlanan kod üretmek için derleme zamanında belirlemek için bir değişken başlatıcı kullanır.</span><span class="sxs-lookup"><span data-stu-id="90f82-116">The compiler uses a variable's initializer to determine the variable's type at compile time to produce early-bound code.</span></span> <span data-ttu-id="90f82-117">Önceki örnekte, `num2`gibi `num1`, olarak belirlenmiş bir `Integer`.</span><span class="sxs-lookup"><span data-stu-id="90f82-117">In the previous example, `num2`, like `num1`, is typed as an `Integer`.</span></span>  
  
 <span data-ttu-id="90f82-118">Erken bağlanmış değişkenleri davranışı, geç bağlanan değişken, yalnızca çalışma zamanında bilinen türü için farklıdır.</span><span class="sxs-lookup"><span data-stu-id="90f82-118">The behavior of early-bound variables differs from that of late-bound variables, for which the type is known only at run time.</span></span> <span data-ttu-id="90f82-119">Türü erken bilmek yürütmeden önce sorunları belirlemenize, tam olarak bellek ve diğer iyileştirmeler gerçekleştirmek derleyiciyi etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="90f82-119">Knowing the type early enables the compiler to identify problems before execution, allocate memory precisely, and perform other optimizations.</span></span> <span data-ttu-id="90f82-120">Erken bağlama, ayrıca Visual Basic tümleşik geliştirme ortamı (IDE) IntelliSense Yardım bir nesnenin üyelerine hakkında sağlamaya olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="90f82-120">Early binding also enables the Visual Basic integrated development environment (IDE) to provide IntelliSense Help about the members of an object.</span></span> <span data-ttu-id="90f82-121">Erken bağlama de performans için tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="90f82-121">Early binding is also preferred for performance.</span></span> <span data-ttu-id="90f82-122">Geç bağlama değişkeninde depolanan tüm veriler türü olarak alınmalıdır olmasıdır `Object`, ve tür üyelerinin çalışma zamanında erişme programın daha yavaş hale getirir.</span><span class="sxs-lookup"><span data-stu-id="90f82-122">This is because all data stored in a late-bound variable must be wrapped as type `Object`, and accessing members of the type at run time makes the program slower.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="90f82-123">Örnekler</span><span class="sxs-lookup"><span data-stu-id="90f82-123">Examples</span></span>  
 <span data-ttu-id="90f82-124">Tür çıkarımı oluşuyor olmadan bildirilen yerel değişken bir `As` yan tümcesi ve başlatılır.</span><span class="sxs-lookup"><span data-stu-id="90f82-124">Type inference occurs when a local variable is declared without an `As` clause and initialized.</span></span> <span data-ttu-id="90f82-125">Derleyici, değişken türü olarak atanan başlangıç değeri türünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="90f82-125">The compiler uses the type of the assigned initial value as the type of the variable.</span></span> <span data-ttu-id="90f82-126">Örneğin, her biri aşağıdaki kod satırlarını türünde bir değişken bildirir `String`.</span><span class="sxs-lookup"><span data-stu-id="90f82-126">For example, each of the following lines of code declares a variable of type `String`.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#2)]  
  
 <span data-ttu-id="90f82-127">Aşağıdaki kod, tamsayı dizisi oluşturmak için iki eşdeğer yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="90f82-127">The following code demonstrates two equivalent ways to create an array of integers.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#3)]  
  
 <span data-ttu-id="90f82-128">Bir for döngüsü denetim değişkeni türünü tür çıkarımı kullanmak uygundur.</span><span class="sxs-lookup"><span data-stu-id="90f82-128">It is convenient to use type inference to determine the type of a loop control variable.</span></span> <span data-ttu-id="90f82-129">Derleyici aşağıdaki kodda algılar `number` olduğu bir `Integer` çünkü `someNumbers2` önceki örnekten tamsayılar dizisidir.</span><span class="sxs-lookup"><span data-stu-id="90f82-129">In the following code, the compiler infers that `number` is an `Integer` because `someNumbers2` from the previous example is an array of integers.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#4)]  
  
 <span data-ttu-id="90f82-130">Yerel tür çıkarımı kullanılabilir `Using` ifadeleri, aşağıdaki örnekte de gösterildiği gibi kaynak adı, türü oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="90f82-130">Local type inference can be used in `Using` statements to establish the type of the resource name, as the following example demonstrates.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#7)]  
  
 <span data-ttu-id="90f82-131">Aşağıdaki örnekte de gösterildiği gibi bir değişken türü işlevlerinin dönüş değerleri de çıkarılan.</span><span class="sxs-lookup"><span data-stu-id="90f82-131">The type of a variable can also be inferred from the return values of functions, as the following example demonstrates.</span></span> <span data-ttu-id="90f82-132">Her ikisi de `pList1` ve `pList2` çünkü dizilerdir işlemlerin `Process.GetProcesses` süreçlerini bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="90f82-132">Both `pList1` and `pList2` are arrays of processes because `Process.GetProcesses` returns an array of processes.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#5)]  
  
## <a name="option-infer"></a><span data-ttu-id="90f82-133">Option Infer</span><span class="sxs-lookup"><span data-stu-id="90f82-133">Option Infer</span></span>  
 <span data-ttu-id="90f82-134">`Option Infer` etkinleştirir, belirli bir dosya yerel tür çıkarımı izin verilip verilmeyeceğini belirtin.</span><span class="sxs-lookup"><span data-stu-id="90f82-134">`Option Infer` enables you specify whether local type inference is allowed in a particular file.</span></span> <span data-ttu-id="90f82-135">Dosyasının başında, etkinleştirmek veya seçeneği engellemek için aşağıdaki deyimleri birini yazın.</span><span class="sxs-lookup"><span data-stu-id="90f82-135">To enable or to block the option, type one of the following statements at the start of the file.</span></span>  
  
 `Option Infer On`  
  
 `Option Infer Off`  
  
 <span data-ttu-id="90f82-136">İçin bir değer belirtmezseniz `Option Infer` kodunuzda derleyici varsayılandır `Option Infer On`.</span><span class="sxs-lookup"><span data-stu-id="90f82-136">If you do not specify a value for `Option Infer` in your code, the compiler default is `Option Infer On`.</span></span> <span data-ttu-id="90f82-137">Projeleri uygulamasından yükseltilen için [!INCLUDE[vb_orcas_long](~/includes/vb-orcas-long-md.md)] veya önceki sürümlerinde, derleyici varsayılan `Option Infer Off`.</span><span class="sxs-lookup"><span data-stu-id="90f82-137">For projects upgraded from [!INCLUDE[vb_orcas_long](~/includes/vb-orcas-long-md.md)] or earlier, the compiler default is `Option Infer Off`.</span></span>  
  
 <span data-ttu-id="90f82-138">Değeri ayarlarsanız `Option Infer` IDE veya komut satırında ayarlanan değer ile dosya çakışmalarını içinde dosyasındaki değeri önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="90f82-138">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>  
  
 <span data-ttu-id="90f82-139">Daha fazla bilgi için [Option Infer deyimi](../../../../visual-basic/language-reference/statements/option-infer-statement.md) ve [derleme sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="90f82-139">For more information, see [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90f82-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="90f82-140">See also</span></span>

- [<span data-ttu-id="90f82-141">Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="90f82-141">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="90f82-142">Erken ve Geç Bağlama</span><span class="sxs-lookup"><span data-stu-id="90f82-142">Early and Late Binding</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [<span data-ttu-id="90f82-143">For Each...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="90f82-143">For Each...Next Statement</span></span>](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="90f82-144">For...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="90f82-144">For...Next Statement</span></span>](../../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="90f82-145">Option Infer Deyimi</span><span class="sxs-lookup"><span data-stu-id="90f82-145">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="90f82-146">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="90f82-146">/optioninfer</span></span>](../../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="90f82-147">Visual Basic'de LINQ'e giriş</span><span class="sxs-lookup"><span data-stu-id="90f82-147">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
