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
ms.openlocfilehash: 977e492c1c8ec5040c22169d91268c9c2241f6c4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404362"
---
# <a name="option-infer-statement"></a><span data-ttu-id="cb5ab-102">Option Infer Deyimi</span><span class="sxs-lookup"><span data-stu-id="cb5ab-102">Option Infer Statement</span></span>

<span data-ttu-id="cb5ab-103">Değişkenleri bildirirken yerel tür çıkarımı kullanımını mümkün.</span><span class="sxs-lookup"><span data-stu-id="cb5ab-103">Enables the use of local type inference in declaring variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="cb5ab-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cb5ab-104">Syntax</span></span>

```vb
Option Infer { On | Off }
```

## <a name="parts"></a><span data-ttu-id="cb5ab-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="cb5ab-105">Parts</span></span>

|<span data-ttu-id="cb5ab-106">Terim</span><span class="sxs-lookup"><span data-stu-id="cb5ab-106">Term</span></span>|<span data-ttu-id="cb5ab-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="cb5ab-107">Definition</span></span>|
|---|---|
|`On`|<span data-ttu-id="cb5ab-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="cb5ab-108">Optional.</span></span> <span data-ttu-id="cb5ab-109">Yerel tür çıkarımı etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="cb5ab-109">Enables local type inference.</span></span>|
|`Off`|<span data-ttu-id="cb5ab-110">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="cb5ab-110">Optional.</span></span> <span data-ttu-id="cb5ab-111">Yerel tür çıkarımını devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="cb5ab-111">Disables local type inference.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cb5ab-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cb5ab-112">Remarks</span></span>

<span data-ttu-id="cb5ab-113">Bir dosyada ayarlamak için, `Option Infer` `Option Infer On` `Option Infer Off` dosyanın en üstüne, diğer herhangi bir kaynak kodundan önce yazın.</span><span class="sxs-lookup"><span data-stu-id="cb5ab-113">To set `Option Infer` in a file, type `Option Infer On` or `Option Infer Off` at the top of the file, before any other source code.</span></span> <span data-ttu-id="cb5ab-114">Bir dosyada için ayarlanan değer `Option Infer` IDE 'de veya komut satırında ayarlanan değerle çakışıyorsa, dosyadaki değerin önceliği vardır.</span><span class="sxs-lookup"><span data-stu-id="cb5ab-114">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>

<span data-ttu-id="cb5ab-115">`Option Infer` `On` ' I ' a ayarladığınızda, açıkça bir veri türü belirtmeden yerel değişkenler bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cb5ab-115">When you set `Option Infer` to `On`, you can declare local variables without explicitly stating a data type.</span></span> <span data-ttu-id="cb5ab-116">Derleyici, başlangıç ifadesinin türünden bir değişkenin veri türünü ifade eden.</span><span class="sxs-lookup"><span data-stu-id="cb5ab-116">The compiler infers the data type of a variable from the type of its initialization expression.</span></span>

<span data-ttu-id="cb5ab-117">Aşağıdaki çizimde `Option Infer` açıktır.</span><span class="sxs-lookup"><span data-stu-id="cb5ab-117">In the following illustration, `Option Infer` is turned on.</span></span> <span data-ttu-id="cb5ab-118">Bildirimdeki değişken `Dim someVar = 2` tür çıkarımı tarafından tamsayı olarak bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="cb5ab-118">The variable in the declaration `Dim someVar = 2` is declared as an integer by type inference.</span></span>

<span data-ttu-id="cb5ab-119">Aşağıdaki ekran görüntüsünde, seçenek çıkarımı açık olduğunda IntelliSense gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="cb5ab-119">The following screenshot shows IntelliSense when Option Infer is on:</span></span>

![Seçenek çıkarımı açık olduğunda IntelliSense görünümünü gösteren ekran görüntüsü.](./media/option-infer-statement/option-infer-as-integer-on.png)

<span data-ttu-id="cb5ab-121">Aşağıdaki çizimde kapalı `Option Infer` .</span><span class="sxs-lookup"><span data-stu-id="cb5ab-121">In the following illustration, `Option Infer` is turned off.</span></span> <span data-ttu-id="cb5ab-122">Bildirimdeki değişken `Dim someVar = 2` `Object` tür çıkarımı olarak bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="cb5ab-122">The variable in the declaration `Dim someVar = 2` is declared as an `Object` by type inference.</span></span> <span data-ttu-id="cb5ab-123">Bu örnekte, **seçenek katı** ayarı [derleme sayfasında, Proje tasarımcısı 'nda (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) **kapalı** olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="cb5ab-123">In this example, the **Option Strict** setting is set to **Off** on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>

<span data-ttu-id="cb5ab-124">Aşağıdaki ekran görüntüsünde, seçenek çıkarımı kapalı olduğunda IntelliSense gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="cb5ab-124">The following screenshot shows IntelliSense when Option Infer is off:</span></span>

![Seçenek çıkarımı kapalıyken IntelliSense görünümünü gösteren ekran görüntüsü.](./media/option-infer-statement/option-infer-as-object-off.png)

> [!NOTE]
> <span data-ttu-id="cb5ab-126">Bir değişken olarak bildirildiği zaman `Object` , program çalışırken çalışma zamanı türü değişebilir.</span><span class="sxs-lookup"><span data-stu-id="cb5ab-126">When a variable is declared as an `Object`, the run-time type can change while the program is running.</span></span> <span data-ttu-id="cb5ab-127">Visual Basic, bir ve bir değer türü arasında dönüştürmek için *kutulama* ve *kutudan* çıkarma adlı işlemleri gerçekleştirir `Object` , bu da yürütmeyi daha yavaş yapar.</span><span class="sxs-lookup"><span data-stu-id="cb5ab-127">Visual Basic performs operations called *boxing* and *unboxing* to convert between an `Object` and a value type, which makes execution slower.</span></span> <span data-ttu-id="cb5ab-128">Kutulama ve kutudan çıkarma hakkında daha fazla bilgi için [Visual Basic dil belirtimine](~/_vblang/spec/conversions.md#value-type-conversions)bakın.</span><span class="sxs-lookup"><span data-stu-id="cb5ab-128">For information about boxing and unboxing, see the [Visual Basic Language Specification](~/_vblang/spec/conversions.md#value-type-conversions).</span></span>

<span data-ttu-id="cb5ab-129">Tür çıkarımı yordam düzeyinde uygulanır ve bir sınıf, yapı, modül veya arabirimdeki bir yordamın dışında uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="cb5ab-129">Type inference applies at the procedure level, and does not apply outside a procedure in a class, structure, module, or interface.</span></span>

<span data-ttu-id="cb5ab-130">Daha fazla bilgi için bkz. [Yerel tür çıkarımı](../../programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="cb5ab-130">For additional information, see [Local Type Inference](../../programming-guide/language-features/variables/local-type-inference.md).</span></span>

## <a name="when-an-option-infer-statement-is-not-present"></a><span data-ttu-id="cb5ab-131">Bir Option Infer deyimleri mevcut olmadığında</span><span class="sxs-lookup"><span data-stu-id="cb5ab-131">When an Option Infer Statement Is Not Present</span></span>

<span data-ttu-id="cb5ab-132">Kaynak kodu bir `Option Infer` ifade içermiyorsa, derleme sayfasındaki **seçenek çıkarımı** ayarı [, proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cb5ab-132">If the source code does not contain an `Option Infer` statement, the **Option Infer** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="cb5ab-133">Komut satırı derleyicisi kullanılırsa [-OptionInfer](../../reference/command-line-compiler/optioninfer.md) derleyici seçeneği kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cb5ab-133">If the command-line compiler is used, the [-optioninfer](../../reference/command-line-compiler/optioninfer.md) compiler option is used.</span></span>

#### <a name="to-set-option-infer-in-the-ide"></a><span data-ttu-id="cb5ab-134">IDE 'de seçenek çıkarımı ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="cb5ab-134">To set Option Infer in the IDE</span></span>

1. <span data-ttu-id="cb5ab-135">**Çözüm Gezgini**bir proje seçin.</span><span class="sxs-lookup"><span data-stu-id="cb5ab-135">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="cb5ab-136">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="cb5ab-136">On the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="cb5ab-137">**Derle** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="cb5ab-137">Click the **Compile** tab.</span></span>

3. <span data-ttu-id="cb5ab-138">**Seçenek çıkarımı** kutusunda değeri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="cb5ab-138">Set the value in the **Option infer** box.</span></span>

<span data-ttu-id="cb5ab-139">Yeni bir proje oluşturduğunuzda, **Derle** sekmesindeki **seçenek** çıkar ayarı, **vb Varsayılanları** iletişim kutusundaki **seçenek çıkarımı** ayarı olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="cb5ab-139">When you create a new project, the **Option Infer** setting on the **Compile** tab is set to the **Option Infer** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="cb5ab-140">**Vb Varsayılanları** iletişim kutusuna erişmek Için, **Araçlar** menüsünde **Seçenekler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="cb5ab-140">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="cb5ab-141">**Seçenekler** iletişim kutusunda, **Projeler ve çözümler**' i genişletin ve ardından **vb Varsayılanları**' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="cb5ab-141">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="cb5ab-142">**Vb** varsayılan olarak ilk varsayılan ayar `On` .</span><span class="sxs-lookup"><span data-stu-id="cb5ab-142">The initial default setting in **VB Defaults** is `On`.</span></span>

#### <a name="to-set-option-infer-on-the-command-line"></a><span data-ttu-id="cb5ab-143">Komut satırında bir seçenek çıkarımı ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="cb5ab-143">To set Option Infer on the command line</span></span>

<span data-ttu-id="cb5ab-144">**Vbc** komutuna [-OptionInfer](../../reference/command-line-compiler/optioninfer.md) derleyici seçeneğini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cb5ab-144">Include the [-optioninfer](../../reference/command-line-compiler/optioninfer.md) compiler option in the **vbc** command.</span></span>

## <a name="default-data-types-and-values"></a><span data-ttu-id="cb5ab-145">Varsayılan veri türleri ve değerleri</span><span class="sxs-lookup"><span data-stu-id="cb5ab-145">Default Data Types and Values</span></span>

<span data-ttu-id="cb5ab-146">Aşağıdaki tabloda, bir deyimindeki veri türünü ve başlatıcıyı belirtmenin çeşitli birleşimlerinin sonuçları açıklanmaktadır `Dim` .</span><span class="sxs-lookup"><span data-stu-id="cb5ab-146">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>

|<span data-ttu-id="cb5ab-147">Veri türü belirtildi mi?</span><span class="sxs-lookup"><span data-stu-id="cb5ab-147">Data type specified?</span></span>|<span data-ttu-id="cb5ab-148">Başlatıcı belirtildi mi?</span><span class="sxs-lookup"><span data-stu-id="cb5ab-148">Initializer specified?</span></span>|<span data-ttu-id="cb5ab-149">Örnek</span><span class="sxs-lookup"><span data-stu-id="cb5ab-149">Example</span></span>|<span data-ttu-id="cb5ab-150">Sonuç</span><span class="sxs-lookup"><span data-stu-id="cb5ab-150">Result</span></span>|
|---|---|---|---|
|<span data-ttu-id="cb5ab-151">Hayır</span><span class="sxs-lookup"><span data-stu-id="cb5ab-151">No</span></span>|<span data-ttu-id="cb5ab-152">Hayır</span><span class="sxs-lookup"><span data-stu-id="cb5ab-152">No</span></span>|`Dim qty`|<span data-ttu-id="cb5ab-153">`Option Strict`Kapalıysa (varsayılan), değişkeni olarak ayarlanır `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="cb5ab-153">If `Option Strict` is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="cb5ab-154">`Option Strict`Açık ise, bir derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="cb5ab-154">If `Option Strict` is on, a compile-time error occurs.</span></span>|
|<span data-ttu-id="cb5ab-155">No</span><span class="sxs-lookup"><span data-stu-id="cb5ab-155">No</span></span>|<span data-ttu-id="cb5ab-156">Evet</span><span class="sxs-lookup"><span data-stu-id="cb5ab-156">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="cb5ab-157">`Option Infer`Açık ise (varsayılan), değişkeni başlatıcının veri türünü alır.</span><span class="sxs-lookup"><span data-stu-id="cb5ab-157">If `Option Infer` is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="cb5ab-158">Bkz. [Yerel tür çıkarımı](../../programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="cb5ab-158">See [Local Type Inference](../../programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="cb5ab-159">`Option Infer`Kapalıysa ve `Option Strict` kapalıysa, değişken veri türünü alır `Object` .</span><span class="sxs-lookup"><span data-stu-id="cb5ab-159">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="cb5ab-160">`Option Infer`Kapalıysa ve açık ise `Option Strict` , bir derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="cb5ab-160">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|
|<span data-ttu-id="cb5ab-161">Yes</span><span class="sxs-lookup"><span data-stu-id="cb5ab-161">Yes</span></span>|<span data-ttu-id="cb5ab-162">No</span><span class="sxs-lookup"><span data-stu-id="cb5ab-162">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="cb5ab-163">Değişken, veri türü için varsayılan değer olarak başlatılır.</span><span class="sxs-lookup"><span data-stu-id="cb5ab-163">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="cb5ab-164">Daha fazla bilgi için bkz. [Dim deyimleri](dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cb5ab-164">For more information, see [Dim Statement](dim-statement.md).</span></span>|
|<span data-ttu-id="cb5ab-165">Yes</span><span class="sxs-lookup"><span data-stu-id="cb5ab-165">Yes</span></span>|<span data-ttu-id="cb5ab-166">Yes</span><span class="sxs-lookup"><span data-stu-id="cb5ab-166">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="cb5ab-167">Başlatıcının veri türü belirtilen veri türüne dönüştürülebilir değilse, bir derleme zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="cb5ab-167">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|

## <a name="example"></a><span data-ttu-id="cb5ab-168">Örnek</span><span class="sxs-lookup"><span data-stu-id="cb5ab-168">Example</span></span>

<span data-ttu-id="cb5ab-169">Aşağıdaki örneklerde, `Option Infer` ifadesinin yerel tür çıkarımı nasıl etkinleştirdiğini gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="cb5ab-169">The following examples demonstrate how the `Option Infer` statement enables local type inference.</span></span>

[!code-vb[VbVbalrTypeInference#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#6)]

## <a name="example"></a><span data-ttu-id="cb5ab-170">Örnek</span><span class="sxs-lookup"><span data-stu-id="cb5ab-170">Example</span></span>

<span data-ttu-id="cb5ab-171">Aşağıdaki örnek, bir değişken olarak tanımlandığında çalışma zamanı türünün farklı kullanılabileceğini gösterir `Object` .</span><span class="sxs-lookup"><span data-stu-id="cb5ab-171">The following example demonstrates that the run-time type can differ when a variable is identified as an `Object`.</span></span>

[!code-vb[VbVbalrTypeInference#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#11)]

## <a name="see-also"></a><span data-ttu-id="cb5ab-172">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb5ab-172">See also</span></span>

- [<span data-ttu-id="cb5ab-173">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="cb5ab-173">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="cb5ab-174">Yerel Tür Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cb5ab-174">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="cb5ab-175">Option Compare Deyimi</span><span class="sxs-lookup"><span data-stu-id="cb5ab-175">Option Compare Statement</span></span>](option-compare-statement.md)
- [<span data-ttu-id="cb5ab-176">Option Explicit Deyimi</span><span class="sxs-lookup"><span data-stu-id="cb5ab-176">Option Explicit Statement</span></span>](option-explicit-statement.md)
- [<span data-ttu-id="cb5ab-177">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="cb5ab-177">Option Strict Statement</span></span>](option-strict-statement.md)
- [<span data-ttu-id="cb5ab-178">Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu</span><span class="sxs-lookup"><span data-stu-id="cb5ab-178">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [<span data-ttu-id="cb5ab-179">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="cb5ab-179">-optioninfer</span></span>](../../reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="cb5ab-180">Kutulama ve Kutudan Çıkarma</span><span class="sxs-lookup"><span data-stu-id="cb5ab-180">Boxing and Unboxing</span></span>](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
