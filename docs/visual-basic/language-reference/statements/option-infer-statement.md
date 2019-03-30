---
title: Option Infer deyimi (Visual Basic)
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
ms.openlocfilehash: 43ac5bc9e32892541ed2f9b0410b6e0ef10558a6
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58654334"
---
# <a name="option-infer-statement"></a><span data-ttu-id="9a34b-102">Option Infer Deyimi</span><span class="sxs-lookup"><span data-stu-id="9a34b-102">Option Infer Statement</span></span>
<span data-ttu-id="9a34b-103">Bildirme değişkenleri olarak yerel tür çıkarımı kullanımını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="9a34b-103">Enables the use of local type inference in declaring variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a34b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9a34b-104">Syntax</span></span>  
  
```  
Option Infer { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="9a34b-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="9a34b-105">Parts</span></span>  
  
|<span data-ttu-id="9a34b-106">Terim</span><span class="sxs-lookup"><span data-stu-id="9a34b-106">Term</span></span>|<span data-ttu-id="9a34b-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="9a34b-107">Definition</span></span>|  
|---|---|  
|`On`|<span data-ttu-id="9a34b-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="9a34b-108">Optional.</span></span> <span data-ttu-id="9a34b-109">Yerel tür çıkarımı sağlar.</span><span class="sxs-lookup"><span data-stu-id="9a34b-109">Enables local type inference.</span></span>|  
|`Off`|<span data-ttu-id="9a34b-110">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="9a34b-110">Optional.</span></span> <span data-ttu-id="9a34b-111">Yerel tür çıkarımı devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="9a34b-111">Disables local type inference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a34b-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9a34b-112">Remarks</span></span>  
 <span data-ttu-id="9a34b-113">Ayarlanacak `Option Infer` bir dosyaya yazın `Option Infer On` veya `Option Infer Off` önce başka bir kaynak kodu dosyasının üst.</span><span class="sxs-lookup"><span data-stu-id="9a34b-113">To set `Option Infer` in a file, type `Option Infer On` or `Option Infer Off` at the top of the file, before any other source code.</span></span> <span data-ttu-id="9a34b-114">Değeri ayarlarsanız `Option Infer` IDE veya komut satırında ayarlanan değer ile dosya çakışmalarını içinde dosyasındaki değeri önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="9a34b-114">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>  
  
 <span data-ttu-id="9a34b-115">Ayarladığınızda `Option Infer` için `On`, açıkça bir veri türü bildirmeden yerel değişkenleri bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a34b-115">When you set `Option Infer` to `On`, you can declare local variables without explicitly stating a data type.</span></span> <span data-ttu-id="9a34b-116">Derleyici, veri türü bir değişkenin kendi başlatma ifadesinin türünden çıkarır.</span><span class="sxs-lookup"><span data-stu-id="9a34b-116">The compiler infers the data type of a variable from the type of its initialization expression.</span></span>  
  
 <span data-ttu-id="9a34b-117">Aşağıdaki çizimde, `Option Infer` açıktır.</span><span class="sxs-lookup"><span data-stu-id="9a34b-117">In the following illustration, `Option Infer` is turned on.</span></span> <span data-ttu-id="9a34b-118">Değişken bildiriminde `Dim someVar = 2` tür çıkarımı tarafından bir tamsayı olarak bildirilir.</span><span class="sxs-lookup"><span data-stu-id="9a34b-118">The variable in the declaration `Dim someVar = 2` is declared as an integer by type inference.</span></span>

 <span data-ttu-id="9a34b-119">Option Infer açık olduğunda IntelliSense aşağıdaki ekran gösterilir:</span><span class="sxs-lookup"><span data-stu-id="9a34b-119">The following screenshot shows IntelliSense when Option Infer is on:</span></span> 
  
 ![Option Infer açık olduğunda, IntelliSense görünümü gösteren ekran görüntüsü.](./media/option-infer-statement/option-infer-as-integer-on.png)  
  
 <span data-ttu-id="9a34b-121">Aşağıdaki çizimde, `Option Infer` devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="9a34b-121">In the following illustration, `Option Infer` is turned off.</span></span> <span data-ttu-id="9a34b-122">Değişken bildiriminde `Dim someVar = 2` olarak bildirilen bir `Object` tür çıkarımı tarafından.</span><span class="sxs-lookup"><span data-stu-id="9a34b-122">The variable in the declaration `Dim someVar = 2` is declared as an `Object` by type inference.</span></span> <span data-ttu-id="9a34b-123">Bu örnekte, **Option Strict** ayarı **kapalı** üzerinde [derleme sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="9a34b-123">In this example, the **Option Strict** setting is set to **Off** on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="9a34b-124">Option Infer devre dışıyken IntelliSense aşağıdaki ekran görüntüsünde gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="9a34b-124">The following screenshot shows IntelliSense when Option Infer is off:</span></span>
 
 ![Option Infer devre dışıyken IntelliSense görünümü gösteren ekran görüntüsü.](./media/option-infer-statement/option-infer-as-object-off.png)  
  
> [!NOTE]
>  <span data-ttu-id="9a34b-126">Ne zaman bir değişken bildirimi olarak bir `Object`, program çalışırken çalışma zamanı türünü değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a34b-126">When a variable is declared as an `Object`, the run-time type can change while the program is running.</span></span> <span data-ttu-id="9a34b-127">Visual Basic adlı işlemler gerçekleştirdiğinde *kutulama* ve *kutudan çıkarma* arasında dönüştürmek için bir `Object` ve daha yavaş yürütme getiren bir değer türü.</span><span class="sxs-lookup"><span data-stu-id="9a34b-127">Visual Basic performs operations called *boxing* and *unboxing* to convert between an `Object` and a value type, which makes execution slower.</span></span> <span data-ttu-id="9a34b-128">Kutulama ve kutudan çıkarma hakkında daha fazla bilgi için bkz. [Visual Basic dil belirtimi](~/_vblang/spec/conversions.md#value-type-conversions).</span><span class="sxs-lookup"><span data-stu-id="9a34b-128">For information about boxing and unboxing, see the [Visual Basic Language Specification](~/_vblang/spec/conversions.md#value-type-conversions).</span></span>
  
 <span data-ttu-id="9a34b-129">Tür çıkarımı yordam düzeyinde uygulanır ve bir yordamda bir sınıf, yapı, modül veya arabirimi dışından geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="9a34b-129">Type inference applies at the procedure level, and does not apply outside a procedure in a class, structure, module, or interface.</span></span>  
  
 <span data-ttu-id="9a34b-130">Ek bilgi için bkz: [yerel tür çıkarımı](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="9a34b-130">For additional information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
## <a name="when-an-option-infer-statement-is-not-present"></a><span data-ttu-id="9a34b-131">Bir Option Infer deyimi mevcut değil</span><span class="sxs-lookup"><span data-stu-id="9a34b-131">When an Option Infer Statement Is Not Present</span></span>  
 <span data-ttu-id="9a34b-132">Kaynak kodu içermiyorsa bir `Option Infer` deyimi **Option Infer** ayarını [derleme sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9a34b-132">If the source code does not contain an `Option Infer` statement, the **Option Infer** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="9a34b-133">Komut satırı derleyicisini kullanılıyorsa [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) derleyici seçeneği kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9a34b-133">If the command-line compiler is used, the [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-infer-in-the-ide"></a><span data-ttu-id="9a34b-134">Option Infer IDE içinde ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="9a34b-134">To set Option Infer in the IDE</span></span>  
  
1.  <span data-ttu-id="9a34b-135">İçinde **Çözüm Gezgini**, bir proje seçin.</span><span class="sxs-lookup"><span data-stu-id="9a34b-135">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="9a34b-136">Üzerinde **proje** menüsünü tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="9a34b-136">On the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="9a34b-137">Tıklayın **derleme** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="9a34b-137">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="9a34b-138">Değer kümesindeki **Option Infer** kutusu.</span><span class="sxs-lookup"><span data-stu-id="9a34b-138">Set the value in the **Option infer** box.</span></span>  
  
 <span data-ttu-id="9a34b-139">Yeni bir proje oluşturduğunuzda **Option Infer** ayarını **derleme** sekmesinde ayarlanmış **Option Infer** ayarı **VB varsayılanları** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="9a34b-139">When you create a new project, the **Option Infer** setting on the **Compile** tab is set to the **Option Infer** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="9a34b-140">Erişim için **VB varsayılanları** iletişim kutusundaki **Araçları** menüsünde tıklatın **seçenekleri**.</span><span class="sxs-lookup"><span data-stu-id="9a34b-140">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="9a34b-141">İçinde **seçenekleri** iletişim kutusunda **projeler ve çözümler**ve ardından **VB varsayılanları**.</span><span class="sxs-lookup"><span data-stu-id="9a34b-141">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="9a34b-142">İlk varsayılan ayarda **VB varsayılanları** olduğu `On`.</span><span class="sxs-lookup"><span data-stu-id="9a34b-142">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-infer-on-the-command-line"></a><span data-ttu-id="9a34b-143">Option Infer komut satırında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="9a34b-143">To set Option Infer on the command line</span></span>  
  
-   <span data-ttu-id="9a34b-144">Dahil [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) derleyici seçeneğini **vbc** komutu.</span><span class="sxs-lookup"><span data-stu-id="9a34b-144">Include the [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="default-data-types-and-values"></a><span data-ttu-id="9a34b-145">Varsayılan veri türleri ve değerleri</span><span class="sxs-lookup"><span data-stu-id="9a34b-145">Default Data Types and Values</span></span>  
 <span data-ttu-id="9a34b-146">Aşağıdaki tabloda çeşitli birleşimlerini başlatıcısında ve veri türünü belirtmenin sonuçlarını açıklar bir `Dim` deyimi.</span><span class="sxs-lookup"><span data-stu-id="9a34b-146">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>  
  
|<span data-ttu-id="9a34b-147">Belirtilen veri türü?</span><span class="sxs-lookup"><span data-stu-id="9a34b-147">Data type specified?</span></span>|<span data-ttu-id="9a34b-148">Belirtilen başlatıcı?</span><span class="sxs-lookup"><span data-stu-id="9a34b-148">Initializer specified?</span></span>|<span data-ttu-id="9a34b-149">Örnek</span><span class="sxs-lookup"><span data-stu-id="9a34b-149">Example</span></span>|<span data-ttu-id="9a34b-150">Sonuç</span><span class="sxs-lookup"><span data-stu-id="9a34b-150">Result</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="9a34b-151">Hayır</span><span class="sxs-lookup"><span data-stu-id="9a34b-151">No</span></span>|<span data-ttu-id="9a34b-152">Hayır</span><span class="sxs-lookup"><span data-stu-id="9a34b-152">No</span></span>|`Dim qty`|<span data-ttu-id="9a34b-153">Varsa `Option Strict` olan kapalı (varsayılan), değişkeni ayarlanır `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="9a34b-153">If `Option Strict` is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="9a34b-154">Varsa `Option Strict` açıktır, bir derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="9a34b-154">If `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="9a34b-155">Hayır</span><span class="sxs-lookup"><span data-stu-id="9a34b-155">No</span></span>|<span data-ttu-id="9a34b-156">Evet</span><span class="sxs-lookup"><span data-stu-id="9a34b-156">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="9a34b-157">Varsa `Option Infer` değişken alır veri öğesinin başlatıcısını yazın (varsayılan), olan.</span><span class="sxs-lookup"><span data-stu-id="9a34b-157">If `Option Infer` is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="9a34b-158">Bkz: [yerel tür çıkarımı](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="9a34b-158">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="9a34b-159">Varsa `Option Infer` kapalıdır ve `Option Strict` kapalıysa, değişken veri türünü alan `Object`.</span><span class="sxs-lookup"><span data-stu-id="9a34b-159">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="9a34b-160">Varsa `Option Infer` kapalıdır ve `Option Strict` açıktır, bir derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="9a34b-160">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="9a34b-161">Evet</span><span class="sxs-lookup"><span data-stu-id="9a34b-161">Yes</span></span>|<span data-ttu-id="9a34b-162">Hayır</span><span class="sxs-lookup"><span data-stu-id="9a34b-162">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="9a34b-163">Değişken veri türü için varsayılan değer için başlatılır.</span><span class="sxs-lookup"><span data-stu-id="9a34b-163">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="9a34b-164">Daha fazla bilgi için [Dim deyimi](../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9a34b-164">For more information, see [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>|  
|<span data-ttu-id="9a34b-165">Evet</span><span class="sxs-lookup"><span data-stu-id="9a34b-165">Yes</span></span>|<span data-ttu-id="9a34b-166">Evet</span><span class="sxs-lookup"><span data-stu-id="9a34b-166">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="9a34b-167">Başlatıcı veri türü belirtilen veri türüne dönüştürülebilir değil, bir derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="9a34b-167">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9a34b-168">Örnek</span><span class="sxs-lookup"><span data-stu-id="9a34b-168">Example</span></span>  
 <span data-ttu-id="9a34b-169">Aşağıdaki örnekler göstermektedir nasıl `Option Infer` ifade yerel tür çıkarımı etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="9a34b-169">The following examples demonstrate how the `Option Infer` statement enables local type inference.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="9a34b-170">Örnek</span><span class="sxs-lookup"><span data-stu-id="9a34b-170">Example</span></span>  
 <span data-ttu-id="9a34b-171">Aşağıdaki örnek, bir değişken olarak tanımlandığında çalışma zamanı tür farklı olduğunu gösterir. bir `Object`.</span><span class="sxs-lookup"><span data-stu-id="9a34b-171">The following example demonstrates that the run-time type can differ when a variable is identified as an `Object`.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="9a34b-172">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a34b-172">See also</span></span>
- [<span data-ttu-id="9a34b-173">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="9a34b-173">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="9a34b-174">Yerel Çıkarım</span><span class="sxs-lookup"><span data-stu-id="9a34b-174">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="9a34b-175">Option Compare Deyimi</span><span class="sxs-lookup"><span data-stu-id="9a34b-175">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="9a34b-176">Option Explicit Deyimi</span><span class="sxs-lookup"><span data-stu-id="9a34b-176">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="9a34b-177">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="9a34b-177">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="9a34b-178">Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu</span><span class="sxs-lookup"><span data-stu-id="9a34b-178">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [<span data-ttu-id="9a34b-179">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="9a34b-179">/optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="9a34b-180">Kutulama ve Kutudan Çıkarma</span><span class="sxs-lookup"><span data-stu-id="9a34b-180">Boxing and Unboxing</span></span>](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
