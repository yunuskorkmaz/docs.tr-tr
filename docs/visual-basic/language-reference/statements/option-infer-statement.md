---
title: Option Infer Deyimi
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "72"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4634c198b5fc41a4834cbd3cd96f9d3f1863d09b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="option-infer-statement"></a><span data-ttu-id="dc454-102">Option Infer Deyimi</span><span class="sxs-lookup"><span data-stu-id="dc454-102">Option Infer Statement</span></span>
<span data-ttu-id="dc454-103">Değişkenleri bildirme içinde yerel türü çıkarımı kullanımını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="dc454-103">Enables the use of local type inference in declaring variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc454-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dc454-104">Syntax</span></span>  
  
```  
Option Infer { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="dc454-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="dc454-105">Parts</span></span>  
  
|<span data-ttu-id="dc454-106">Terim</span><span class="sxs-lookup"><span data-stu-id="dc454-106">Term</span></span>|<span data-ttu-id="dc454-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="dc454-107">Definition</span></span>|  
|---|---|  
|`On`|<span data-ttu-id="dc454-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="dc454-108">Optional.</span></span> <span data-ttu-id="dc454-109">Yerel türü çıkarımı sağlar.</span><span class="sxs-lookup"><span data-stu-id="dc454-109">Enables local type inference.</span></span>|  
|`Off`|<span data-ttu-id="dc454-110">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="dc454-110">Optional.</span></span> <span data-ttu-id="dc454-111">Yerel türü çıkarımı devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="dc454-111">Disables local type inference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc454-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dc454-112">Remarks</span></span>  
 <span data-ttu-id="dc454-113">Ayarlamak için `Option Infer` bir dosyaya yazın `Option Infer On` veya `Option Infer Off` önce başka bir kaynak kod dosyasının üst.</span><span class="sxs-lookup"><span data-stu-id="dc454-113">To set `Option Infer` in a file, type `Option Infer On` or `Option Infer Off` at the top of the file, before any other source code.</span></span> <span data-ttu-id="dc454-114">Değeri ayarlarsanız `Option Infer` IDE veya komut satırında ayarlanan değer ile dosya çakışmalarını içinde dosyasındaki değer önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="dc454-114">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>  
  
 <span data-ttu-id="dc454-115">Ayarladığınızda `Option Infer` için `On`, açıkça bir veri türü bildirmeden yerel değişkenler bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc454-115">When you set `Option Infer` to `On`, you can declare local variables without explicitly stating a data type.</span></span> <span data-ttu-id="dc454-116">Derleyici, başlatma ifadesinin türünden bir değişken veri türü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dc454-116">The compiler infers the data type of a variable from the type of its initialization expression.</span></span>  
  
 <span data-ttu-id="dc454-117">Aşağıdaki çizimde, `Option Infer` açıktır.</span><span class="sxs-lookup"><span data-stu-id="dc454-117">In the following illustration, `Option Infer` is turned on.</span></span> <span data-ttu-id="dc454-118">Değişken bildirimi `Dim someVar = 2` bir tamsayı olarak tür çıkarımı tarafından bildirilmedi.</span><span class="sxs-lookup"><span data-stu-id="dc454-118">The variable in the declaration `Dim someVar = 2` is declared as an integer by type inference.</span></span>  
  
 <span data-ttu-id="dc454-119">![Bildirim IntelliSense görünümü. ] (../../../visual-basic/language-reference/statements/media/optioninferasinteger.png "optionInferAsInteger")</span><span class="sxs-lookup"><span data-stu-id="dc454-119">![IntelliSense view of the declaration.](../../../visual-basic/language-reference/statements/media/optioninferasinteger.png "optionInferAsInteger")</span></span>  
<span data-ttu-id="dc454-120">Option Infer açık olduğunda IntelliSense</span><span class="sxs-lookup"><span data-stu-id="dc454-120">IntelliSense when Option Infer is on</span></span>  
  
 <span data-ttu-id="dc454-121">Aşağıdaki çizimde, `Option Infer` kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="dc454-121">In the following illustration, `Option Infer` is turned off.</span></span> <span data-ttu-id="dc454-122">Değişken bildirimi `Dim someVar = 2` olarak bildirilen bir `Object` tür çıkarımı tarafından.</span><span class="sxs-lookup"><span data-stu-id="dc454-122">The variable in the declaration `Dim someVar = 2` is declared as an `Object` by type inference.</span></span> <span data-ttu-id="dc454-123">Bu örnekte, **Option Strict** ayar **kapalı** üzerinde [derleme sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="dc454-123">In this example, the **Option Strict** setting is set to **Off** on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="dc454-124">![Bildirim IntelliSense görünümü. ] (../../../visual-basic/language-reference/statements/media/optioninferasobject.png "optionInferAsObject")</span><span class="sxs-lookup"><span data-stu-id="dc454-124">![IntelliSense view of the declaration.](../../../visual-basic/language-reference/statements/media/optioninferasobject.png "optionInferAsObject")</span></span>  
<span data-ttu-id="dc454-125">Option Infer kapalı olduğunda IntelliSense</span><span class="sxs-lookup"><span data-stu-id="dc454-125">IntelliSense when Option Infer is off</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dc454-126">Ne zaman bir değişken bildirilen olarak bir `Object`, program çalışırken çalışma zamanı türünü değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc454-126">When a variable is declared as an `Object`, the run-time type can change while the program is running.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="dc454-127">adlı işlemleri gerçekleştirir *kutulama* ve *kutudan çıkarma* arasında dönüştürme için bir `Object` ve yürütme yavaş olmasını sağlayan bir değer türü.</span><span class="sxs-lookup"><span data-stu-id="dc454-127"> performs operations called *boxing* and *unboxing* to convert between an `Object` and a value type, which makes execution slower.</span></span> <span data-ttu-id="dc454-128">Kutulama ve kutudan çıkarma hakkında daha fazla bilgi için bkz: [Visual Basic dil belirtimi](../../../visual-basic/reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="dc454-128">For information about boxing and unboxing, see the [Visual Basic Language Specification](../../../visual-basic/reference/language-specification/index.md).</span></span>
  
 <span data-ttu-id="dc454-129">Tür çıkarımı yordamı düzeyinde uygulanır ve sınıf, yapı, modül veya arabirim yordam dışında geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="dc454-129">Type inference applies at the procedure level, and does not apply outside a procedure in a class, structure, module, or interface.</span></span>  
  
 <span data-ttu-id="dc454-130">Ek bilgi için bkz: [yerel türü çıkarımı](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="dc454-130">For additional information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
## <a name="when-an-option-infer-statement-is-not-present"></a><span data-ttu-id="dc454-131">Bir Option Infer deyimi mevcut değil</span><span class="sxs-lookup"><span data-stu-id="dc454-131">When an Option Infer Statement Is Not Present</span></span>  
 <span data-ttu-id="dc454-132">Kaynak kodu içermiyorsa bir `Option Infer` deyimi, **Option Infer** ayarı [derleme sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dc454-132">If the source code does not contain an `Option Infer` statement, the **Option Infer** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="dc454-133">Komut satırı derleyicisi kullanılırsa, [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) derleyici seçeneği kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dc454-133">If the command-line compiler is used, the [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-infer-in-the-ide"></a><span data-ttu-id="dc454-134">Option Infer IDE'de ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="dc454-134">To set Option Infer in the IDE</span></span>  
  
1.  <span data-ttu-id="dc454-135">İçinde **Çözüm Gezgini**, bir proje seçin.</span><span class="sxs-lookup"><span data-stu-id="dc454-135">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="dc454-136">Üzerinde **proje** menüsünde tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="dc454-136">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="dc454-137">Daha fazla bilgi için bkz: [NIB: Proje özellikleriyle yönetme Proje Tasarımcısı](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).</span><span class="sxs-lookup"><span data-stu-id="dc454-137">For more information, see [NIB: Managing Project Properties with the Project Designer](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).</span></span>  
  
2.  <span data-ttu-id="dc454-138">Tıklatın **derleme** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="dc454-138">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="dc454-139">Değer kümesinde **Option Infer** kutusu.</span><span class="sxs-lookup"><span data-stu-id="dc454-139">Set the value in the **Option infer** box.</span></span>  
  
 <span data-ttu-id="dc454-140">Yeni bir proje oluşturduğunuzda **Option Infer** ayarı **derleme** sekmesinde ayarlanmış **Option Infer** ayarı **VB varsayılanlarını** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="dc454-140">When you create a new project, the **Option Infer** setting on the **Compile** tab is set to the **Option Infer** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="dc454-141">Erişim için **VB varsayılan olarak** iletişim kutusundaki **Araçları** menüsünde tıklatın **seçenekleri**.</span><span class="sxs-lookup"><span data-stu-id="dc454-141">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="dc454-142">İçinde **seçenekleri** iletişim kutusunda, genişletin **projeler ve çözümler**ve ardından **VB varsayılanları**.</span><span class="sxs-lookup"><span data-stu-id="dc454-142">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="dc454-143">İlk varsayılan ayarı **VB varsayılanları** olan `On`.</span><span class="sxs-lookup"><span data-stu-id="dc454-143">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-infer-on-the-command-line"></a><span data-ttu-id="dc454-144">Option Infer komut satırında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="dc454-144">To set Option Infer on the command line</span></span>  
  
-   <span data-ttu-id="dc454-145">Dahil [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) derleyici seçeneği **vbc** komutu.</span><span class="sxs-lookup"><span data-stu-id="dc454-145">Include the [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="default-data-types-and-values"></a><span data-ttu-id="dc454-146">Varsayılan veri türleri ve değerleri</span><span class="sxs-lookup"><span data-stu-id="dc454-146">Default Data Types and Values</span></span>  
 <span data-ttu-id="dc454-147">Veri türü ve Başlatıcı belirtmenin çeşitli birleşimleri sonuçları aşağıdaki tabloda açıklanmaktadır bir `Dim` deyimi.</span><span class="sxs-lookup"><span data-stu-id="dc454-147">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>  
  
|<span data-ttu-id="dc454-148">Belirtilen veri türü?</span><span class="sxs-lookup"><span data-stu-id="dc454-148">Data type specified?</span></span>|<span data-ttu-id="dc454-149">Belirtilen başlatıcı?</span><span class="sxs-lookup"><span data-stu-id="dc454-149">Initializer specified?</span></span>|<span data-ttu-id="dc454-150">Örnek</span><span class="sxs-lookup"><span data-stu-id="dc454-150">Example</span></span>|<span data-ttu-id="dc454-151">Sonuç</span><span class="sxs-lookup"><span data-stu-id="dc454-151">Result</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="dc454-152">Hayır</span><span class="sxs-lookup"><span data-stu-id="dc454-152">No</span></span>|<span data-ttu-id="dc454-153">Hayır</span><span class="sxs-lookup"><span data-stu-id="dc454-153">No</span></span>|`Dim qty`|<span data-ttu-id="dc454-154">Varsa `Option Strict` olan kapalı (varsayılan), değişkenini ayarlamak `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="dc454-154">If `Option Strict` is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="dc454-155">Varsa `Option Strict` olduğundan, bir derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="dc454-155">If `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="dc454-156">Hayır</span><span class="sxs-lookup"><span data-stu-id="dc454-156">No</span></span>|<span data-ttu-id="dc454-157">Evet</span><span class="sxs-lookup"><span data-stu-id="dc454-157">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="dc454-158">Varsa `Option Infer` Başlatıcı değişken alır veri türü (varsayılan), olduğunda.</span><span class="sxs-lookup"><span data-stu-id="dc454-158">If `Option Infer` is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="dc454-159">Bkz: [yerel türü çıkarımı](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="dc454-159">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="dc454-160">Varsa `Option Infer` kapalıdır ve `Option Strict` kapalıysa, değişken veri türü alır `Object`.</span><span class="sxs-lookup"><span data-stu-id="dc454-160">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="dc454-161">Varsa `Option Infer` kapalıdır ve `Option Strict` olduğundan, bir derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="dc454-161">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="dc454-162">Evet</span><span class="sxs-lookup"><span data-stu-id="dc454-162">Yes</span></span>|<span data-ttu-id="dc454-163">Hayır</span><span class="sxs-lookup"><span data-stu-id="dc454-163">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="dc454-164">Değişken veri türü için varsayılan değer için başlatılır.</span><span class="sxs-lookup"><span data-stu-id="dc454-164">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="dc454-165">Daha fazla bilgi için bkz: [Dim deyimi](../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="dc454-165">For more information, see [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>|  
|<span data-ttu-id="dc454-166">Evet</span><span class="sxs-lookup"><span data-stu-id="dc454-166">Yes</span></span>|<span data-ttu-id="dc454-167">Evet</span><span class="sxs-lookup"><span data-stu-id="dc454-167">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="dc454-168">Başlatıcı'veri türü belirtilen veri türüne dönüştürülebilir değilse, bir derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="dc454-168">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="dc454-169">Örnek</span><span class="sxs-lookup"><span data-stu-id="dc454-169">Example</span></span>  
 <span data-ttu-id="dc454-170">Aşağıdaki örnekler göstermektedir nasıl `Option Infer` ifade yerel türü çıkarımı etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="dc454-170">The following examples demonstrate how the `Option Infer` statement enables local type inference.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#6](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-infer-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="dc454-171">Örnek</span><span class="sxs-lookup"><span data-stu-id="dc454-171">Example</span></span>  
 <span data-ttu-id="dc454-172">Aşağıdaki örnek, bir değişken olarak tanımlandığında, çalışma zamanı türü farklı olduğunu gösterir. bir `Object`.</span><span class="sxs-lookup"><span data-stu-id="dc454-172">The following example demonstrates that the run-time type can differ when a variable is identified as an `Object`.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#11](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-infer-statement_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="dc454-173">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dc454-173">See Also</span></span>  
 [<span data-ttu-id="dc454-174">Dim deyimi</span><span class="sxs-lookup"><span data-stu-id="dc454-174">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="dc454-175">Yerel tür çıkarımı</span><span class="sxs-lookup"><span data-stu-id="dc454-175">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="dc454-176">Option Compare deyimi</span><span class="sxs-lookup"><span data-stu-id="dc454-176">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [<span data-ttu-id="dc454-177">Option Explicit deyimi</span><span class="sxs-lookup"><span data-stu-id="dc454-177">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [<span data-ttu-id="dc454-178">Option Strict deyimi</span><span class="sxs-lookup"><span data-stu-id="dc454-178">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="dc454-179">Visual Basic Varsayılanları, projeler, Seçenekler iletişim kutusu</span><span class="sxs-lookup"><span data-stu-id="dc454-179">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)  
 [<span data-ttu-id="dc454-180">/ optioninfer</span><span class="sxs-lookup"><span data-stu-id="dc454-180">/optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="dc454-181">Kutulama ve kutudan çıkarma</span><span class="sxs-lookup"><span data-stu-id="dc454-181">Boxing and Unboxing</span></span>](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
