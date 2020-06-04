---
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
ms.openlocfilehash: 3979396d32aa5d3b853aa087d43f70d5987e510b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410405"
---
# <a name="local-type-inference-visual-basic"></a><span data-ttu-id="8cbcb-102">Yerel Türü Arabirimi (Visual Basic Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="8cbcb-102">Local Type Inference (Visual Basic)</span></span>

<span data-ttu-id="8cbcb-103">Visual Basic derleyici, bir yan tümce olmadan belirtilen yerel değişkenlerin veri türlerini belirlemede *tür çıkarımı* kullanır `As` .</span><span class="sxs-lookup"><span data-stu-id="8cbcb-103">The Visual Basic compiler uses *type inference* to determine the data types of local variables declared without an `As` clause.</span></span> <span data-ttu-id="8cbcb-104">Derleyici, değişkenin türünü başlatma ifadesinin türünden algılar.</span><span class="sxs-lookup"><span data-stu-id="8cbcb-104">The compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="8cbcb-105">Bu, aşağıdaki örnekte gösterildiği gibi, bir türü açıkça belirtmeden değişkenleri bildirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="8cbcb-105">This enables you to declare variables without explicitly stating a type, as shown in the following example.</span></span> <span data-ttu-id="8cbcb-106">Bildirimlerin bir sonucu olarak, `num1` ve `num2` kesin olarak tam sayı olarak türdedir.</span><span class="sxs-lookup"><span data-stu-id="8cbcb-106">As a result of the declarations, both `num1` and `num2` are strongly typed as integers.</span></span>

[!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]

> [!NOTE]
> <span data-ttu-id="8cbcb-107">`num2`Önceki örnekte bir olarak yazılmaları istemiyorsanız `Integer` , veya gibi bir bildirim kullanarak başka bir tür belirtebilirsiniz `Dim num3 As Object = 3` `Dim num4 As Double = 3` .</span><span class="sxs-lookup"><span data-stu-id="8cbcb-107">If you do not want `num2` in the previous example to be typed as an `Integer`, you can specify another type by using a declaration like `Dim num3 As Object = 3` or `Dim num4 As Double = 3`.</span></span>

> [!NOTE]
> <span data-ttu-id="8cbcb-108">Tür çıkarımı, yalnızca statik olmayan yerel değişkenler için kullanılabilir; sınıf alanları, özellikler veya işlevlerin türünü belirleyebilmek için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="8cbcb-108">Type inference can be used only for non-static local variables; it cannot be used to determine the type of class fields, properties, or functions.</span></span>

<span data-ttu-id="8cbcb-109">Yerel tür çıkarımı yordam düzeyinde geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="8cbcb-109">Local type inference applies at procedure level.</span></span> <span data-ttu-id="8cbcb-110">Modül düzeyinde (bir sınıf, yapı, modül veya arabirim içinde değil, yordam veya blok içinde değil) değişkenleri bildirmek için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="8cbcb-110">It cannot be used to declare variables at module level (within a class, structure, module, or interface but not within a procedure or block).</span></span> <span data-ttu-id="8cbcb-111">`num2`Önceki örnekte, bir yordamda yerel bir değişken yerine bir sınıfın alanı olsaydı, bildirim üzerinde bir hataya neden olur `Option Strict` ve `num2` ile bir olarak sınıflandırır `Object` `Option Strict` .</span><span class="sxs-lookup"><span data-stu-id="8cbcb-111">If `num2` in the previous example were a field of a class instead of a local variable in a procedure, the declaration would cause an error with `Option Strict` on, and would classify `num2` as an `Object` with `Option Strict` off.</span></span> <span data-ttu-id="8cbcb-112">Benzer şekilde, yerel tür çıkarımı olarak belirtilen yordam düzeyi değişkenlerine uygulanmaz `Static` .</span><span class="sxs-lookup"><span data-stu-id="8cbcb-112">Similarly, local type inference does not apply to procedure level variables declared as `Static`.</span></span>

## <a name="type-inference-vs-late-binding"></a><span data-ttu-id="8cbcb-113">Tür çıkarımı ile geç bağlama</span><span class="sxs-lookup"><span data-stu-id="8cbcb-113">Type Inference vs. Late Binding</span></span>

<span data-ttu-id="8cbcb-114">Tür çıkarımı kullanan kod, geç bağlamaya dayanan koda benzer.</span><span class="sxs-lookup"><span data-stu-id="8cbcb-114">Code that uses type inference resembles code that relies on late binding.</span></span> <span data-ttu-id="8cbcb-115">Ancak tür çıkarımı, değişkeni olarak bırakmak yerine değişkeni kesin bir şekilde bırakır `Object` .</span><span class="sxs-lookup"><span data-stu-id="8cbcb-115">However, type inference strongly types the variable instead of leaving it as `Object`.</span></span> <span data-ttu-id="8cbcb-116">Derleyici, değişkenin türünü, erken bağlantılı kod oluşturmak için derleme zamanında değişkenin türünü tespit etmek için bir değişkenin başlatıcısı kullanır.</span><span class="sxs-lookup"><span data-stu-id="8cbcb-116">The compiler uses a variable's initializer to determine the variable's type at compile time to produce early-bound code.</span></span> <span data-ttu-id="8cbcb-117">Önceki örnekte, gibi, `num2` `num1` bir olarak yazılır `Integer` .</span><span class="sxs-lookup"><span data-stu-id="8cbcb-117">In the previous example, `num2`, like `num1`, is typed as an `Integer`.</span></span>

<span data-ttu-id="8cbcb-118">Erken bağlanan değişkenlerin davranışı, türü yalnızca çalışma zamanında bilinen, geç bağlanan değişkenlerden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="8cbcb-118">The behavior of early-bound variables differs from that of late-bound variables, for which the type is known only at run time.</span></span> <span data-ttu-id="8cbcb-119">Türün erken olması, derleyicinin yürütmeden önce sorunları belirlemesini, belleği tam olarak ayırmasını ve diğer iyileştirmeleri gerçekleştirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="8cbcb-119">Knowing the type early enables the compiler to identify problems before execution, allocate memory precisely, and perform other optimizations.</span></span> <span data-ttu-id="8cbcb-120">Erken bağlama Ayrıca, Visual Basic tümleşik geliştirme ortamının (IDE) bir nesnenin üyeleri hakkında IntelliSense yardımı sağlamasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="8cbcb-120">Early binding also enables the Visual Basic integrated development environment (IDE) to provide IntelliSense Help about the members of an object.</span></span> <span data-ttu-id="8cbcb-121">Erken bağlama de performans için tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="8cbcb-121">Early binding is also preferred for performance.</span></span> <span data-ttu-id="8cbcb-122">Bunun nedeni, geç bağlantılı bir değişkende depolanan tüm verilerin tür olarak sarmalanması `Object` ve çalışma zamanında tür üyelerine erişmesi, programın daha yavaş olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="8cbcb-122">This is because all data stored in a late-bound variable must be wrapped as type `Object`, and accessing members of the type at run time makes the program slower.</span></span>

## <a name="examples"></a><span data-ttu-id="8cbcb-123">Örnekler</span><span class="sxs-lookup"><span data-stu-id="8cbcb-123">Examples</span></span>

<span data-ttu-id="8cbcb-124">Yerel bir değişken bir yan tümce olmadan bildirildiğinde ve başlatıldığında tür çıkarımı oluşur `As` .</span><span class="sxs-lookup"><span data-stu-id="8cbcb-124">Type inference occurs when a local variable is declared without an `As` clause and initialized.</span></span> <span data-ttu-id="8cbcb-125">Derleyici, değişkenin türü olarak atanan ilk değerin türünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="8cbcb-125">The compiler uses the type of the assigned initial value as the type of the variable.</span></span> <span data-ttu-id="8cbcb-126">Örneğin, aşağıdaki kod satırlarının her biri türünde bir değişken bildirir `String` .</span><span class="sxs-lookup"><span data-stu-id="8cbcb-126">For example, each of the following lines of code declares a variable of type `String`.</span></span>

[!code-vb[VbVbalrTypeInference#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#2)]

<span data-ttu-id="8cbcb-127">Aşağıdaki kod, tamsayılar dizisi oluşturmanın iki denk yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="8cbcb-127">The following code demonstrates two equivalent ways to create an array of integers.</span></span>

[!code-vb[VbVbalrTypeInference#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#3)]

<span data-ttu-id="8cbcb-128">Döngü denetim değişkeninin türünü belirleyebilmek için tür çıkarımı kullanmak uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="8cbcb-128">It is convenient to use type inference to determine the type of a loop control variable.</span></span> <span data-ttu-id="8cbcb-129">Aşağıdaki kodda, `number` bir `Integer` önceki örnekteki bir tamsayılar dizisi olduğu için derleyici bir `someNumbers2` .</span><span class="sxs-lookup"><span data-stu-id="8cbcb-129">In the following code, the compiler infers that `number` is an `Integer` because `someNumbers2` from the previous example is an array of integers.</span></span>

[!code-vb[VbVbalrTypeInference#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#4)]

<span data-ttu-id="8cbcb-130">Yerel tür çıkarımı, `Using` Aşağıdaki örnekte gösterildiği gibi, kaynak adının türünü oluşturmak için ifadelerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8cbcb-130">Local type inference can be used in `Using` statements to establish the type of the resource name, as the following example demonstrates.</span></span>

[!code-vb[VbVbalrTypeInference#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#7)]

<span data-ttu-id="8cbcb-131">Aşağıdaki örnekte gösterildiği gibi, bir değişkenin türü, işlevlerin dönüş değerlerinden de çıkarsanamıyor.</span><span class="sxs-lookup"><span data-stu-id="8cbcb-131">The type of a variable can also be inferred from the return values of functions, as the following example demonstrates.</span></span> <span data-ttu-id="8cbcb-132">Her ikisi `pList1` ve `pList2` işlem dizileri, çünkü `Process.GetProcesses` bir işlem dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="8cbcb-132">Both `pList1` and `pList2` are arrays of processes because `Process.GetProcesses` returns an array of processes.</span></span>

[!code-vb[VbVbalrTypeInference#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#5)]

## <a name="option-infer"></a><span data-ttu-id="8cbcb-133">Seçenek çıkarımı</span><span class="sxs-lookup"><span data-stu-id="8cbcb-133">Option Infer</span></span>

<span data-ttu-id="8cbcb-134">`Option Infer`belirli bir dosyada yerel tür çıkarımı izin verilip verilmeyeceğini belirtmenizi belirler.</span><span class="sxs-lookup"><span data-stu-id="8cbcb-134">`Option Infer` enables you specify whether local type inference is allowed in a particular file.</span></span> <span data-ttu-id="8cbcb-135">Seçeneği etkinleştirmek veya engellemek için, dosyanın başlangıcında aşağıdaki deyimlerden birini yazın.</span><span class="sxs-lookup"><span data-stu-id="8cbcb-135">To enable or to block the option, type one of the following statements at the start of the file.</span></span>

`Option Infer On`

`Option Infer Off`

<span data-ttu-id="8cbcb-136">Kodunuzda için bir değer belirtmezseniz `Option Infer` , derleyici varsayılanı olur `Option Infer On` .</span><span class="sxs-lookup"><span data-stu-id="8cbcb-136">If you do not specify a value for `Option Infer` in your code, the compiler default is `Option Infer On`.</span></span>

<span data-ttu-id="8cbcb-137">Bir dosyada için ayarlanan değer `Option Infer` IDE 'de veya komut satırında ayarlanan değerle çakışıyorsa, dosyadaki değerin önceliği vardır.</span><span class="sxs-lookup"><span data-stu-id="8cbcb-137">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>

<span data-ttu-id="8cbcb-138">Daha fazla bilgi için bkz. [Option Infer deyimleri](../../../language-reference/statements/option-infer-statement.md) ve [derleme sayfası, proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="8cbcb-138">For more information, see [Option Infer Statement](../../../language-reference/statements/option-infer-statement.md) and [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>

## <a name="see-also"></a><span data-ttu-id="8cbcb-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8cbcb-139">See also</span></span>

- [<span data-ttu-id="8cbcb-140">Anonim Türler</span><span class="sxs-lookup"><span data-stu-id="8cbcb-140">Anonymous Types</span></span>](../objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="8cbcb-141">Erken ve geç bağlama</span><span class="sxs-lookup"><span data-stu-id="8cbcb-141">Early and Late Binding</span></span>](../early-late-binding/index.md)
- [<span data-ttu-id="8cbcb-142">For Each...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="8cbcb-142">For Each...Next Statement</span></span>](../../../language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="8cbcb-143">For...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="8cbcb-143">For...Next Statement</span></span>](../../../language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="8cbcb-144">Option Infer Deyimi</span><span class="sxs-lookup"><span data-stu-id="8cbcb-144">Option Infer Statement</span></span>](../../../language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="8cbcb-145">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="8cbcb-145">-optioninfer</span></span>](../../../reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="8cbcb-146">Visual Basic'de LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="8cbcb-146">Introduction to LINQ in Visual Basic</span></span>](../linq/introduction-to-linq.md)
