---
description: 'Daha fazla bilgi edinin: Yerel tür çıkarımı (Visual Basic)'
title: Yerel Tür Arabirimi
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
ms.openlocfilehash: 50be8544229360287d2aef27f31360d7140640ac
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100481707"
---
# <a name="local-type-inference-visual-basic"></a><span data-ttu-id="47cd5-103">Yerel Türü Arabirimi (Visual Basic Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="47cd5-103">Local Type Inference (Visual Basic)</span></span>

<span data-ttu-id="47cd5-104">Visual Basic derleyici, bir yan tümce olmadan belirtilen yerel değişkenlerin veri türlerini belirlemede *tür çıkarımı* kullanır `As` .</span><span class="sxs-lookup"><span data-stu-id="47cd5-104">The Visual Basic compiler uses *type inference* to determine the data types of local variables declared without an `As` clause.</span></span> <span data-ttu-id="47cd5-105">Derleyici, değişkenin türünü başlatma ifadesinin türünden algılar.</span><span class="sxs-lookup"><span data-stu-id="47cd5-105">The compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="47cd5-106">Bu, aşağıdaki örnekte gösterildiği gibi, bir türü açıkça belirtmeden değişkenleri bildirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="47cd5-106">This enables you to declare variables without explicitly stating a type, as shown in the following example.</span></span> <span data-ttu-id="47cd5-107">Bildirimlerin bir sonucu olarak, `num1` ve `num2` kesin olarak tam sayı olarak türdedir.</span><span class="sxs-lookup"><span data-stu-id="47cd5-107">As a result of the declarations, both `num1` and `num2` are strongly typed as integers.</span></span>

[!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]

> [!NOTE]
> <span data-ttu-id="47cd5-108">`num2`Önceki örnekte bir olarak yazılmaları istemiyorsanız `Integer` , veya gibi bir bildirim kullanarak başka bir tür belirtebilirsiniz `Dim num3 As Object = 3` `Dim num4 As Double = 3` .</span><span class="sxs-lookup"><span data-stu-id="47cd5-108">If you do not want `num2` in the previous example to be typed as an `Integer`, you can specify another type by using a declaration like `Dim num3 As Object = 3` or `Dim num4 As Double = 3`.</span></span>

> [!NOTE]
> <span data-ttu-id="47cd5-109">Tür çıkarımı, yalnızca statik olmayan yerel değişkenler için kullanılabilir; sınıf alanları, özellikler veya işlevlerin türünü belirleyebilmek için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="47cd5-109">Type inference can be used only for non-static local variables; it cannot be used to determine the type of class fields, properties, or functions.</span></span>

<span data-ttu-id="47cd5-110">Yerel tür çıkarımı yordam düzeyinde geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="47cd5-110">Local type inference applies at procedure level.</span></span> <span data-ttu-id="47cd5-111">Modül düzeyinde (bir sınıf, yapı, modül veya arabirim içinde değil, yordam veya blok içinde değil) değişkenleri bildirmek için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="47cd5-111">It cannot be used to declare variables at module level (within a class, structure, module, or interface but not within a procedure or block).</span></span> <span data-ttu-id="47cd5-112">`num2`Önceki örnekte, bir yordamda yerel bir değişken yerine bir sınıfın alanı olsaydı, bildirim üzerinde bir hataya neden olur `Option Strict` ve `num2` ile bir olarak sınıflandırır `Object` `Option Strict` .</span><span class="sxs-lookup"><span data-stu-id="47cd5-112">If `num2` in the previous example were a field of a class instead of a local variable in a procedure, the declaration would cause an error with `Option Strict` on, and would classify `num2` as an `Object` with `Option Strict` off.</span></span> <span data-ttu-id="47cd5-113">Benzer şekilde, yerel tür çıkarımı olarak belirtilen yordam düzeyi değişkenlerine uygulanmaz `Static` .</span><span class="sxs-lookup"><span data-stu-id="47cd5-113">Similarly, local type inference does not apply to procedure level variables declared as `Static`.</span></span>

## <a name="type-inference-vs-late-binding"></a><span data-ttu-id="47cd5-114">Tür çıkarımı ile geç bağlama</span><span class="sxs-lookup"><span data-stu-id="47cd5-114">Type Inference vs. Late Binding</span></span>

<span data-ttu-id="47cd5-115">Tür çıkarımı kullanan kod, geç bağlamaya dayanan koda benzer.</span><span class="sxs-lookup"><span data-stu-id="47cd5-115">Code that uses type inference resembles code that relies on late binding.</span></span> <span data-ttu-id="47cd5-116">Ancak tür çıkarımı, değişkeni olarak bırakmak yerine değişkeni kesin bir şekilde bırakır `Object` .</span><span class="sxs-lookup"><span data-stu-id="47cd5-116">However, type inference strongly types the variable instead of leaving it as `Object`.</span></span> <span data-ttu-id="47cd5-117">Derleyici, değişkenin türünü, erken bağlantılı kod oluşturmak için derleme zamanında değişkenin türünü tespit etmek için bir değişkenin başlatıcısı kullanır.</span><span class="sxs-lookup"><span data-stu-id="47cd5-117">The compiler uses a variable's initializer to determine the variable's type at compile time to produce early-bound code.</span></span> <span data-ttu-id="47cd5-118">Önceki örnekte, gibi, `num2` `num1` bir olarak yazılır `Integer` .</span><span class="sxs-lookup"><span data-stu-id="47cd5-118">In the previous example, `num2`, like `num1`, is typed as an `Integer`.</span></span>

<span data-ttu-id="47cd5-119">Erken bağlanan değişkenlerin davranışı, türü yalnızca çalışma zamanında bilinen, geç bağlanan değişkenlerden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="47cd5-119">The behavior of early-bound variables differs from that of late-bound variables, for which the type is known only at run time.</span></span> <span data-ttu-id="47cd5-120">Türün erken olması, derleyicinin yürütmeden önce sorunları belirlemesini, belleği tam olarak ayırmasını ve diğer iyileştirmeleri gerçekleştirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="47cd5-120">Knowing the type early enables the compiler to identify problems before execution, allocate memory precisely, and perform other optimizations.</span></span> <span data-ttu-id="47cd5-121">Erken bağlama Ayrıca, Visual Basic tümleşik geliştirme ortamının (IDE) bir nesnenin üyeleri hakkında IntelliSense yardımı sağlamasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="47cd5-121">Early binding also enables the Visual Basic integrated development environment (IDE) to provide IntelliSense Help about the members of an object.</span></span> <span data-ttu-id="47cd5-122">Erken bağlama de performans için tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="47cd5-122">Early binding is also preferred for performance.</span></span> <span data-ttu-id="47cd5-123">Bunun nedeni, geç bağlantılı bir değişkende depolanan tüm verilerin tür olarak sarmalanması `Object` ve çalışma zamanında tür üyelerine erişmesi, programın daha yavaş olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="47cd5-123">This is because all data stored in a late-bound variable must be wrapped as type `Object`, and accessing members of the type at run time makes the program slower.</span></span>

## <a name="examples"></a><span data-ttu-id="47cd5-124">Örnekler</span><span class="sxs-lookup"><span data-stu-id="47cd5-124">Examples</span></span>

<span data-ttu-id="47cd5-125">Yerel bir değişken bir yan tümce olmadan bildirildiğinde ve başlatıldığında tür çıkarımı oluşur `As` .</span><span class="sxs-lookup"><span data-stu-id="47cd5-125">Type inference occurs when a local variable is declared without an `As` clause and initialized.</span></span> <span data-ttu-id="47cd5-126">Derleyici, değişkenin türü olarak atanan ilk değerin türünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="47cd5-126">The compiler uses the type of the assigned initial value as the type of the variable.</span></span> <span data-ttu-id="47cd5-127">Örneğin, aşağıdaki kod satırlarının her biri türünde bir değişken bildirir `String` .</span><span class="sxs-lookup"><span data-stu-id="47cd5-127">For example, each of the following lines of code declares a variable of type `String`.</span></span>

[!code-vb[VbVbalrTypeInference#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#2)]

<span data-ttu-id="47cd5-128">Aşağıdaki kod, tamsayılar dizisi oluşturmanın iki denk yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="47cd5-128">The following code demonstrates two equivalent ways to create an array of integers.</span></span>

[!code-vb[VbVbalrTypeInference#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#3)]

<span data-ttu-id="47cd5-129">Döngü denetim değişkeninin türünü belirleyebilmek için tür çıkarımı kullanmak uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="47cd5-129">It is convenient to use type inference to determine the type of a loop control variable.</span></span> <span data-ttu-id="47cd5-130">Aşağıdaki kodda, `number` bir `Integer` önceki örnekteki bir tamsayılar dizisi olduğu için derleyici bir `someNumbers2` .</span><span class="sxs-lookup"><span data-stu-id="47cd5-130">In the following code, the compiler infers that `number` is an `Integer` because `someNumbers2` from the previous example is an array of integers.</span></span>

[!code-vb[VbVbalrTypeInference#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#4)]

<span data-ttu-id="47cd5-131">Yerel tür çıkarımı, `Using` Aşağıdaki örnekte gösterildiği gibi, kaynak adının türünü oluşturmak için ifadelerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="47cd5-131">Local type inference can be used in `Using` statements to establish the type of the resource name, as the following example demonstrates.</span></span>

[!code-vb[VbVbalrTypeInference#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#7)]

<span data-ttu-id="47cd5-132">Aşağıdaki örnekte gösterildiği gibi, bir değişkenin türü, işlevlerin dönüş değerlerinden de çıkarsanamıyor.</span><span class="sxs-lookup"><span data-stu-id="47cd5-132">The type of a variable can also be inferred from the return values of functions, as the following example demonstrates.</span></span> <span data-ttu-id="47cd5-133">Her ikisi `pList1` ve `pList2` işlem dizileri, çünkü `Process.GetProcesses` bir işlem dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="47cd5-133">Both `pList1` and `pList2` are arrays of processes because `Process.GetProcesses` returns an array of processes.</span></span>

[!code-vb[VbVbalrTypeInference#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#5)]

## <a name="option-infer"></a><span data-ttu-id="47cd5-134">Seçenek çıkarımı</span><span class="sxs-lookup"><span data-stu-id="47cd5-134">Option Infer</span></span>

<span data-ttu-id="47cd5-135">`Option Infer` belirli bir dosyada yerel tür çıkarımı izin verilip verilmeyeceğini belirtmenizi belirler.</span><span class="sxs-lookup"><span data-stu-id="47cd5-135">`Option Infer` enables you specify whether local type inference is allowed in a particular file.</span></span> <span data-ttu-id="47cd5-136">Seçeneği etkinleştirmek veya engellemek için, dosyanın başlangıcında aşağıdaki deyimlerden birini yazın.</span><span class="sxs-lookup"><span data-stu-id="47cd5-136">To enable or to block the option, type one of the following statements at the start of the file.</span></span>

`Option Infer On`

`Option Infer Off`

<span data-ttu-id="47cd5-137">Kodunuzda için bir değer belirtmezseniz `Option Infer` , derleyici varsayılanı olur `Option Infer On` .</span><span class="sxs-lookup"><span data-stu-id="47cd5-137">If you do not specify a value for `Option Infer` in your code, the compiler default is `Option Infer On`.</span></span>

<span data-ttu-id="47cd5-138">Bir dosyada için ayarlanan değer `Option Infer` IDE 'de veya komut satırında ayarlanan değerle çakışıyorsa, dosyadaki değerin önceliği vardır.</span><span class="sxs-lookup"><span data-stu-id="47cd5-138">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>

<span data-ttu-id="47cd5-139">Daha fazla bilgi için bkz. [Option Infer deyimleri](../../../language-reference/statements/option-infer-statement.md) ve [derleme sayfası, proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="47cd5-139">For more information, see [Option Infer Statement](../../../language-reference/statements/option-infer-statement.md) and [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>

## <a name="see-also"></a><span data-ttu-id="47cd5-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47cd5-140">See also</span></span>

- [<span data-ttu-id="47cd5-141">Anonim Türler</span><span class="sxs-lookup"><span data-stu-id="47cd5-141">Anonymous Types</span></span>](../objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="47cd5-142">Erken ve geç bağlama</span><span class="sxs-lookup"><span data-stu-id="47cd5-142">Early and Late Binding</span></span>](../early-late-binding/index.md)
- [<span data-ttu-id="47cd5-143">For Each...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="47cd5-143">For Each...Next Statement</span></span>](../../../language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="47cd5-144">For...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="47cd5-144">For...Next Statement</span></span>](../../../language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="47cd5-145">Option Infer Deyimi</span><span class="sxs-lookup"><span data-stu-id="47cd5-145">Option Infer Statement</span></span>](../../../language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="47cd5-146">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="47cd5-146">-optioninfer</span></span>](../../../reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="47cd5-147">Visual Basic'de LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="47cd5-147">Introduction to LINQ in Visual Basic</span></span>](../linq/introduction-to-linq.md)
