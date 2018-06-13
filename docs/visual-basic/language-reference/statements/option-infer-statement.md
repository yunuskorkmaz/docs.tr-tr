---
title: Option Infer Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.OptionInfer
- vb.Infer
helpviewer_keywords:
- variables [Visual Basic], declaring
- Option Infer statement [Visual Basic]
- Infer keyword [Visual Basic]
- declaring variables [Visual Basic], inferred
- inferred variable declaration
ms.assetid: 4ad3e6e9-8f5b-4209-a248-de22ef6e4652
ms.openlocfilehash: c7628e5c4c0cda527a4c3b1a211c45760640fc63
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605517"
---
# <a name="option-infer-statement"></a><span data-ttu-id="62b58-102">Option Infer Deyimi</span><span class="sxs-lookup"><span data-stu-id="62b58-102">Option Infer Statement</span></span>
<span data-ttu-id="62b58-103">Değişkenleri bildirme içinde yerel türü çıkarımı kullanımını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="62b58-103">Enables the use of local type inference in declaring variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62b58-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="62b58-104">Syntax</span></span>  
  
```  
Option Infer { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="62b58-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="62b58-105">Parts</span></span>  
  
|<span data-ttu-id="62b58-106">Terim</span><span class="sxs-lookup"><span data-stu-id="62b58-106">Term</span></span>|<span data-ttu-id="62b58-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="62b58-107">Definition</span></span>|  
|---|---|  
|`On`|<span data-ttu-id="62b58-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="62b58-108">Optional.</span></span> <span data-ttu-id="62b58-109">Yerel türü çıkarımı sağlar.</span><span class="sxs-lookup"><span data-stu-id="62b58-109">Enables local type inference.</span></span>|  
|`Off`|<span data-ttu-id="62b58-110">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="62b58-110">Optional.</span></span> <span data-ttu-id="62b58-111">Yerel türü çıkarımı devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="62b58-111">Disables local type inference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62b58-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="62b58-112">Remarks</span></span>  
 <span data-ttu-id="62b58-113">Ayarlamak için `Option Infer` bir dosyaya yazın `Option Infer On` veya `Option Infer Off` önce başka bir kaynak kod dosyasının üst.</span><span class="sxs-lookup"><span data-stu-id="62b58-113">To set `Option Infer` in a file, type `Option Infer On` or `Option Infer Off` at the top of the file, before any other source code.</span></span> <span data-ttu-id="62b58-114">Değeri ayarlarsanız `Option Infer` IDE veya komut satırında ayarlanan değer ile dosya çakışmalarını içinde dosyasındaki değer önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="62b58-114">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>  
  
 <span data-ttu-id="62b58-115">Ayarladığınızda `Option Infer` için `On`, açıkça bir veri türü bildirmeden yerel değişkenler bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62b58-115">When you set `Option Infer` to `On`, you can declare local variables without explicitly stating a data type.</span></span> <span data-ttu-id="62b58-116">Derleyici, başlatma ifadesinin türünden bir değişken veri türü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="62b58-116">The compiler infers the data type of a variable from the type of its initialization expression.</span></span>  
  
 <span data-ttu-id="62b58-117">Aşağıdaki çizimde, `Option Infer` açıktır.</span><span class="sxs-lookup"><span data-stu-id="62b58-117">In the following illustration, `Option Infer` is turned on.</span></span> <span data-ttu-id="62b58-118">Değişken bildirimi `Dim someVar = 2` bir tamsayı olarak tür çıkarımı tarafından bildirilmedi.</span><span class="sxs-lookup"><span data-stu-id="62b58-118">The variable in the declaration `Dim someVar = 2` is declared as an integer by type inference.</span></span>  
  
 <span data-ttu-id="62b58-119">![Bildirim IntelliSense görünümü. ] (../../../visual-basic/language-reference/statements/media/optioninferasinteger.png "optionInferAsInteger")</span><span class="sxs-lookup"><span data-stu-id="62b58-119">![IntelliSense view of the declaration.](../../../visual-basic/language-reference/statements/media/optioninferasinteger.png "optionInferAsInteger")</span></span>  
<span data-ttu-id="62b58-120">Option Infer açık olduğunda IntelliSense</span><span class="sxs-lookup"><span data-stu-id="62b58-120">IntelliSense when Option Infer is on</span></span>  
  
 <span data-ttu-id="62b58-121">Aşağıdaki çizimde, `Option Infer` kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="62b58-121">In the following illustration, `Option Infer` is turned off.</span></span> <span data-ttu-id="62b58-122">Değişken bildirimi `Dim someVar = 2` olarak bildirilen bir `Object` tür çıkarımı tarafından.</span><span class="sxs-lookup"><span data-stu-id="62b58-122">The variable in the declaration `Dim someVar = 2` is declared as an `Object` by type inference.</span></span> <span data-ttu-id="62b58-123">Bu örnekte, **Option Strict** ayar **kapalı** üzerinde [derleme sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="62b58-123">In this example, the **Option Strict** setting is set to **Off** on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="62b58-124">![Bildirim IntelliSense görünümü. ] (../../../visual-basic/language-reference/statements/media/optioninferasobject.png "optionInferAsObject")</span><span class="sxs-lookup"><span data-stu-id="62b58-124">![IntelliSense view of the declaration.](../../../visual-basic/language-reference/statements/media/optioninferasobject.png "optionInferAsObject")</span></span>  
<span data-ttu-id="62b58-125">Option Infer kapalı olduğunda IntelliSense</span><span class="sxs-lookup"><span data-stu-id="62b58-125">IntelliSense when Option Infer is off</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="62b58-126">Ne zaman bir değişken bildirilen olarak bir `Object`, program çalışırken çalışma zamanı türünü değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62b58-126">When a variable is declared as an `Object`, the run-time type can change while the program is running.</span></span> <span data-ttu-id="62b58-127">Visual Basic adlı işlemler gerçekleştirdiğinde *kutulama* ve *kutudan çıkarma* arasında dönüştürme için bir `Object` ve yürütme yavaş olmasını sağlayan bir değer türü.</span><span class="sxs-lookup"><span data-stu-id="62b58-127">Visual Basic performs operations called *boxing* and *unboxing* to convert between an `Object` and a value type, which makes execution slower.</span></span> <span data-ttu-id="62b58-128">Kutulama ve kutudan çıkarma hakkında daha fazla bilgi için bkz: [Visual Basic dil belirtimi](../../../visual-basic/reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="62b58-128">For information about boxing and unboxing, see the [Visual Basic Language Specification](../../../visual-basic/reference/language-specification/index.md).</span></span>
  
 <span data-ttu-id="62b58-129">Tür çıkarımı yordamı düzeyinde uygulanır ve sınıf, yapı, modül veya arabirim yordam dışında geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="62b58-129">Type inference applies at the procedure level, and does not apply outside a procedure in a class, structure, module, or interface.</span></span>  
  
 <span data-ttu-id="62b58-130">Ek bilgi için bkz: [yerel türü çıkarımı](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="62b58-130">For additional information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
## <a name="when-an-option-infer-statement-is-not-present"></a><span data-ttu-id="62b58-131">Bir Option Infer deyimi mevcut değil</span><span class="sxs-lookup"><span data-stu-id="62b58-131">When an Option Infer Statement Is Not Present</span></span>  
 <span data-ttu-id="62b58-132">Kaynak kodu içermiyorsa bir `Option Infer` deyimi, **Option Infer** ayarı [derleme sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) kullanılır.</span><span class="sxs-lookup"><span data-stu-id="62b58-132">If the source code does not contain an `Option Infer` statement, the **Option Infer** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="62b58-133">Komut satırı derleyicisi kullanılırsa, [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) derleyici seçeneği kullanılır.</span><span class="sxs-lookup"><span data-stu-id="62b58-133">If the command-line compiler is used, the [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-infer-in-the-ide"></a><span data-ttu-id="62b58-134">Option Infer IDE'de ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="62b58-134">To set Option Infer in the IDE</span></span>  
  
1.  <span data-ttu-id="62b58-135">İçinde **Çözüm Gezgini**, bir proje seçin.</span><span class="sxs-lookup"><span data-stu-id="62b58-135">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="62b58-136">Üzerinde **proje** menüsünde tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="62b58-136">On the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="62b58-137">Tıklatın **derleme** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="62b58-137">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="62b58-138">Değer kümesinde **Option Infer** kutusu.</span><span class="sxs-lookup"><span data-stu-id="62b58-138">Set the value in the **Option infer** box.</span></span>  
  
 <span data-ttu-id="62b58-139">Yeni bir proje oluşturduğunuzda **Option Infer** ayarı **derleme** sekmesinde ayarlanmış **Option Infer** ayarı **VB varsayılanlarını** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="62b58-139">When you create a new project, the **Option Infer** setting on the **Compile** tab is set to the **Option Infer** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="62b58-140">Erişim için **VB varsayılan olarak** iletişim kutusundaki **Araçları** menüsünde tıklatın **seçenekleri**.</span><span class="sxs-lookup"><span data-stu-id="62b58-140">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="62b58-141">İçinde **seçenekleri** iletişim kutusunda, genişletin **projeler ve çözümler**ve ardından **VB varsayılanları**.</span><span class="sxs-lookup"><span data-stu-id="62b58-141">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="62b58-142">İlk varsayılan ayarı **VB varsayılanları** olan `On`.</span><span class="sxs-lookup"><span data-stu-id="62b58-142">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-infer-on-the-command-line"></a><span data-ttu-id="62b58-143">Option Infer komut satırında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="62b58-143">To set Option Infer on the command line</span></span>  
  
-   <span data-ttu-id="62b58-144">Dahil [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) derleyici seçeneği **vbc** komutu.</span><span class="sxs-lookup"><span data-stu-id="62b58-144">Include the [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="default-data-types-and-values"></a><span data-ttu-id="62b58-145">Varsayılan veri türleri ve değerleri</span><span class="sxs-lookup"><span data-stu-id="62b58-145">Default Data Types and Values</span></span>  
 <span data-ttu-id="62b58-146">Veri türü ve Başlatıcı belirtmenin çeşitli birleşimleri sonuçları aşağıdaki tabloda açıklanmaktadır bir `Dim` deyimi.</span><span class="sxs-lookup"><span data-stu-id="62b58-146">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>  
  
|<span data-ttu-id="62b58-147">Belirtilen veri türü?</span><span class="sxs-lookup"><span data-stu-id="62b58-147">Data type specified?</span></span>|<span data-ttu-id="62b58-148">Belirtilen başlatıcı?</span><span class="sxs-lookup"><span data-stu-id="62b58-148">Initializer specified?</span></span>|<span data-ttu-id="62b58-149">Örnek</span><span class="sxs-lookup"><span data-stu-id="62b58-149">Example</span></span>|<span data-ttu-id="62b58-150">Sonuç</span><span class="sxs-lookup"><span data-stu-id="62b58-150">Result</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="62b58-151">Hayır</span><span class="sxs-lookup"><span data-stu-id="62b58-151">No</span></span>|<span data-ttu-id="62b58-152">Hayır</span><span class="sxs-lookup"><span data-stu-id="62b58-152">No</span></span>|`Dim qty`|<span data-ttu-id="62b58-153">Varsa `Option Strict` olan kapalı (varsayılan), değişkenini ayarlamak `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="62b58-153">If `Option Strict` is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="62b58-154">Varsa `Option Strict` olduğundan, bir derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="62b58-154">If `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="62b58-155">Hayır</span><span class="sxs-lookup"><span data-stu-id="62b58-155">No</span></span>|<span data-ttu-id="62b58-156">Evet</span><span class="sxs-lookup"><span data-stu-id="62b58-156">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="62b58-157">Varsa `Option Infer` Başlatıcı değişken alır veri türü (varsayılan), olduğunda.</span><span class="sxs-lookup"><span data-stu-id="62b58-157">If `Option Infer` is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="62b58-158">Bkz: [yerel türü çıkarımı](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="62b58-158">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="62b58-159">Varsa `Option Infer` kapalıdır ve `Option Strict` kapalıysa, değişken veri türü alır `Object`.</span><span class="sxs-lookup"><span data-stu-id="62b58-159">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="62b58-160">Varsa `Option Infer` kapalıdır ve `Option Strict` olduğundan, bir derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="62b58-160">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="62b58-161">Evet</span><span class="sxs-lookup"><span data-stu-id="62b58-161">Yes</span></span>|<span data-ttu-id="62b58-162">Hayır</span><span class="sxs-lookup"><span data-stu-id="62b58-162">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="62b58-163">Değişken veri türü için varsayılan değer için başlatılır.</span><span class="sxs-lookup"><span data-stu-id="62b58-163">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="62b58-164">Daha fazla bilgi için bkz: [Dim deyimi](../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="62b58-164">For more information, see [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>|  
|<span data-ttu-id="62b58-165">Evet</span><span class="sxs-lookup"><span data-stu-id="62b58-165">Yes</span></span>|<span data-ttu-id="62b58-166">Evet</span><span class="sxs-lookup"><span data-stu-id="62b58-166">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="62b58-167">Başlatıcı'veri türü belirtilen veri türüne dönüştürülebilir değilse, bir derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="62b58-167">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="62b58-168">Örnek</span><span class="sxs-lookup"><span data-stu-id="62b58-168">Example</span></span>  
 <span data-ttu-id="62b58-169">Aşağıdaki örnekler göstermektedir nasıl `Option Infer` ifade yerel türü çıkarımı etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="62b58-169">The following examples demonstrate how the `Option Infer` statement enables local type inference.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#6](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-infer-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="62b58-170">Örnek</span><span class="sxs-lookup"><span data-stu-id="62b58-170">Example</span></span>  
 <span data-ttu-id="62b58-171">Aşağıdaki örnek, bir değişken olarak tanımlandığında, çalışma zamanı türü farklı olduğunu gösterir. bir `Object`.</span><span class="sxs-lookup"><span data-stu-id="62b58-171">The following example demonstrates that the run-time type can differ when a variable is identified as an `Object`.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#11](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-infer-statement_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="62b58-172">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="62b58-172">See Also</span></span>  
 [<span data-ttu-id="62b58-173">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="62b58-173">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="62b58-174">Yerel Çıkarım</span><span class="sxs-lookup"><span data-stu-id="62b58-174">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="62b58-175">Option Compare Deyimi</span><span class="sxs-lookup"><span data-stu-id="62b58-175">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [<span data-ttu-id="62b58-176">Option Explicit Deyimi</span><span class="sxs-lookup"><span data-stu-id="62b58-176">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [<span data-ttu-id="62b58-177">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="62b58-177">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="62b58-178">Visual Basic Varsayılanları, projeler, Seçenekler iletişim kutusu</span><span class="sxs-lookup"><span data-stu-id="62b58-178">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)  
 [<span data-ttu-id="62b58-179">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="62b58-179">/optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="62b58-180">Kutulama ve Kutudan Çıkarma</span><span class="sxs-lookup"><span data-stu-id="62b58-180">Boxing and Unboxing</span></span>](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
