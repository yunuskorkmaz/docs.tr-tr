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
ms.openlocfilehash: 53bc9d41f28f63061db2012395480aa6be7515dd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346491"
---
# <a name="option-infer-statement"></a><span data-ttu-id="b336a-102">Option Infer Deyimi</span><span class="sxs-lookup"><span data-stu-id="b336a-102">Option Infer Statement</span></span>

<span data-ttu-id="b336a-103">Enables the use of local type inference in declaring variables.</span><span class="sxs-lookup"><span data-stu-id="b336a-103">Enables the use of local type inference in declaring variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="b336a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b336a-104">Syntax</span></span>

```vb
Option Infer { On | Off }
```

## <a name="parts"></a><span data-ttu-id="b336a-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="b336a-105">Parts</span></span>

|<span data-ttu-id="b336a-106">Terim</span><span class="sxs-lookup"><span data-stu-id="b336a-106">Term</span></span>|<span data-ttu-id="b336a-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="b336a-107">Definition</span></span>|
|---|---|
|`On`|<span data-ttu-id="b336a-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="b336a-108">Optional.</span></span> <span data-ttu-id="b336a-109">Enables local type inference.</span><span class="sxs-lookup"><span data-stu-id="b336a-109">Enables local type inference.</span></span>|
|`Off`|<span data-ttu-id="b336a-110">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="b336a-110">Optional.</span></span> <span data-ttu-id="b336a-111">Disables local type inference.</span><span class="sxs-lookup"><span data-stu-id="b336a-111">Disables local type inference.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b336a-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b336a-112">Remarks</span></span>

<span data-ttu-id="b336a-113">To set `Option Infer` in a file, type `Option Infer On` or `Option Infer Off` at the top of the file, before any other source code.</span><span class="sxs-lookup"><span data-stu-id="b336a-113">To set `Option Infer` in a file, type `Option Infer On` or `Option Infer Off` at the top of the file, before any other source code.</span></span> <span data-ttu-id="b336a-114">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span><span class="sxs-lookup"><span data-stu-id="b336a-114">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>

<span data-ttu-id="b336a-115">When you set `Option Infer` to `On`, you can declare local variables without explicitly stating a data type.</span><span class="sxs-lookup"><span data-stu-id="b336a-115">When you set `Option Infer` to `On`, you can declare local variables without explicitly stating a data type.</span></span> <span data-ttu-id="b336a-116">The compiler infers the data type of a variable from the type of its initialization expression.</span><span class="sxs-lookup"><span data-stu-id="b336a-116">The compiler infers the data type of a variable from the type of its initialization expression.</span></span>

<span data-ttu-id="b336a-117">In the following illustration, `Option Infer` is turned on.</span><span class="sxs-lookup"><span data-stu-id="b336a-117">In the following illustration, `Option Infer` is turned on.</span></span> <span data-ttu-id="b336a-118">The variable in the declaration `Dim someVar = 2` is declared as an integer by type inference.</span><span class="sxs-lookup"><span data-stu-id="b336a-118">The variable in the declaration `Dim someVar = 2` is declared as an integer by type inference.</span></span>

<span data-ttu-id="b336a-119">The following screenshot shows IntelliSense when Option Infer is on:</span><span class="sxs-lookup"><span data-stu-id="b336a-119">The following screenshot shows IntelliSense when Option Infer is on:</span></span>

![Screenshot showing IntelliSense view when Option Infer is on.](./media/option-infer-statement/option-infer-as-integer-on.png)

<span data-ttu-id="b336a-121">In the following illustration, `Option Infer` is turned off.</span><span class="sxs-lookup"><span data-stu-id="b336a-121">In the following illustration, `Option Infer` is turned off.</span></span> <span data-ttu-id="b336a-122">The variable in the declaration `Dim someVar = 2` is declared as an `Object` by type inference.</span><span class="sxs-lookup"><span data-stu-id="b336a-122">The variable in the declaration `Dim someVar = 2` is declared as an `Object` by type inference.</span></span> <span data-ttu-id="b336a-123">In this example, the **Option Strict** setting is set to **Off** on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="b336a-123">In this example, the **Option Strict** setting is set to **Off** on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>

<span data-ttu-id="b336a-124">The following screenshot shows IntelliSense when Option Infer is off:</span><span class="sxs-lookup"><span data-stu-id="b336a-124">The following screenshot shows IntelliSense when Option Infer is off:</span></span>

![Screenshot showing IntelliSense view when Option Infer is off.](./media/option-infer-statement/option-infer-as-object-off.png)

> [!NOTE]
> <span data-ttu-id="b336a-126">When a variable is declared as an `Object`, the run-time type can change while the program is running.</span><span class="sxs-lookup"><span data-stu-id="b336a-126">When a variable is declared as an `Object`, the run-time type can change while the program is running.</span></span> <span data-ttu-id="b336a-127">Visual Basic performs operations called *boxing* and *unboxing* to convert between an `Object` and a value type, which makes execution slower.</span><span class="sxs-lookup"><span data-stu-id="b336a-127">Visual Basic performs operations called *boxing* and *unboxing* to convert between an `Object` and a value type, which makes execution slower.</span></span> <span data-ttu-id="b336a-128">For information about boxing and unboxing, see the [Visual Basic Language Specification](~/_vblang/spec/conversions.md#value-type-conversions).</span><span class="sxs-lookup"><span data-stu-id="b336a-128">For information about boxing and unboxing, see the [Visual Basic Language Specification](~/_vblang/spec/conversions.md#value-type-conversions).</span></span>

<span data-ttu-id="b336a-129">Type inference applies at the procedure level, and does not apply outside a procedure in a class, structure, module, or interface.</span><span class="sxs-lookup"><span data-stu-id="b336a-129">Type inference applies at the procedure level, and does not apply outside a procedure in a class, structure, module, or interface.</span></span>

<span data-ttu-id="b336a-130">For additional information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="b336a-130">For additional information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>

## <a name="when-an-option-infer-statement-is-not-present"></a><span data-ttu-id="b336a-131">When an Option Infer Statement Is Not Present</span><span class="sxs-lookup"><span data-stu-id="b336a-131">When an Option Infer Statement Is Not Present</span></span>

<span data-ttu-id="b336a-132">If the source code does not contain an `Option Infer` statement, the **Option Infer** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span><span class="sxs-lookup"><span data-stu-id="b336a-132">If the source code does not contain an `Option Infer` statement, the **Option Infer** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="b336a-133">If the command-line compiler is used, the [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option is used.</span><span class="sxs-lookup"><span data-stu-id="b336a-133">If the command-line compiler is used, the [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option is used.</span></span>

#### <a name="to-set-option-infer-in-the-ide"></a><span data-ttu-id="b336a-134">To set Option Infer in the IDE</span><span class="sxs-lookup"><span data-stu-id="b336a-134">To set Option Infer in the IDE</span></span>

1. <span data-ttu-id="b336a-135">In **Solution Explorer**, select a project.</span><span class="sxs-lookup"><span data-stu-id="b336a-135">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="b336a-136">On the **Project** menu, click **Properties**.</span><span class="sxs-lookup"><span data-stu-id="b336a-136">On the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="b336a-137">Click the **Compile** tab.</span><span class="sxs-lookup"><span data-stu-id="b336a-137">Click the **Compile** tab.</span></span>

3. <span data-ttu-id="b336a-138">Set the value in the **Option infer** box.</span><span class="sxs-lookup"><span data-stu-id="b336a-138">Set the value in the **Option infer** box.</span></span>

<span data-ttu-id="b336a-139">When you create a new project, the **Option Infer** setting on the **Compile** tab is set to the **Option Infer** setting in the **VB Defaults** dialog box.</span><span class="sxs-lookup"><span data-stu-id="b336a-139">When you create a new project, the **Option Infer** setting on the **Compile** tab is set to the **Option Infer** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="b336a-140">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span><span class="sxs-lookup"><span data-stu-id="b336a-140">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="b336a-141">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span><span class="sxs-lookup"><span data-stu-id="b336a-141">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="b336a-142">The initial default setting in **VB Defaults** is `On`.</span><span class="sxs-lookup"><span data-stu-id="b336a-142">The initial default setting in **VB Defaults** is `On`.</span></span>

#### <a name="to-set-option-infer-on-the-command-line"></a><span data-ttu-id="b336a-143">To set Option Infer on the command line</span><span class="sxs-lookup"><span data-stu-id="b336a-143">To set Option Infer on the command line</span></span>

<span data-ttu-id="b336a-144">Include the [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option in the **vbc** command.</span><span class="sxs-lookup"><span data-stu-id="b336a-144">Include the [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option in the **vbc** command.</span></span>

## <a name="default-data-types-and-values"></a><span data-ttu-id="b336a-145">Default Data Types and Values</span><span class="sxs-lookup"><span data-stu-id="b336a-145">Default Data Types and Values</span></span>

<span data-ttu-id="b336a-146">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span><span class="sxs-lookup"><span data-stu-id="b336a-146">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>

|<span data-ttu-id="b336a-147">Data type specified?</span><span class="sxs-lookup"><span data-stu-id="b336a-147">Data type specified?</span></span>|<span data-ttu-id="b336a-148">Initializer specified?</span><span class="sxs-lookup"><span data-stu-id="b336a-148">Initializer specified?</span></span>|<span data-ttu-id="b336a-149">Örnek</span><span class="sxs-lookup"><span data-stu-id="b336a-149">Example</span></span>|<span data-ttu-id="b336a-150">Sonuç</span><span class="sxs-lookup"><span data-stu-id="b336a-150">Result</span></span>|
|---|---|---|---|
|<span data-ttu-id="b336a-151">Hayır</span><span class="sxs-lookup"><span data-stu-id="b336a-151">No</span></span>|<span data-ttu-id="b336a-152">Hayır</span><span class="sxs-lookup"><span data-stu-id="b336a-152">No</span></span>|`Dim qty`|<span data-ttu-id="b336a-153">If `Option Strict` is off (the default), the variable is set to `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="b336a-153">If `Option Strict` is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="b336a-154">If `Option Strict` is on, a compile-time error occurs.</span><span class="sxs-lookup"><span data-stu-id="b336a-154">If `Option Strict` is on, a compile-time error occurs.</span></span>|
|<span data-ttu-id="b336a-155">Hayır</span><span class="sxs-lookup"><span data-stu-id="b336a-155">No</span></span>|<span data-ttu-id="b336a-156">Evet</span><span class="sxs-lookup"><span data-stu-id="b336a-156">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="b336a-157">If `Option Infer` is on (the default), the variable takes the data type of the initializer.</span><span class="sxs-lookup"><span data-stu-id="b336a-157">If `Option Infer` is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="b336a-158">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="b336a-158">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="b336a-159">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span><span class="sxs-lookup"><span data-stu-id="b336a-159">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="b336a-160">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span><span class="sxs-lookup"><span data-stu-id="b336a-160">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|
|<span data-ttu-id="b336a-161">Evet</span><span class="sxs-lookup"><span data-stu-id="b336a-161">Yes</span></span>|<span data-ttu-id="b336a-162">Hayır</span><span class="sxs-lookup"><span data-stu-id="b336a-162">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="b336a-163">The variable is initialized to the default value for the data type.</span><span class="sxs-lookup"><span data-stu-id="b336a-163">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="b336a-164">For more information, see [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b336a-164">For more information, see [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>|
|<span data-ttu-id="b336a-165">Evet</span><span class="sxs-lookup"><span data-stu-id="b336a-165">Yes</span></span>|<span data-ttu-id="b336a-166">Evet</span><span class="sxs-lookup"><span data-stu-id="b336a-166">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="b336a-167">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span><span class="sxs-lookup"><span data-stu-id="b336a-167">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|

## <a name="example"></a><span data-ttu-id="b336a-168">Örnek</span><span class="sxs-lookup"><span data-stu-id="b336a-168">Example</span></span>

<span data-ttu-id="b336a-169">The following examples demonstrate how the `Option Infer` statement enables local type inference.</span><span class="sxs-lookup"><span data-stu-id="b336a-169">The following examples demonstrate how the `Option Infer` statement enables local type inference.</span></span>

[!code-vb[VbVbalrTypeInference#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#6)]

## <a name="example"></a><span data-ttu-id="b336a-170">Örnek</span><span class="sxs-lookup"><span data-stu-id="b336a-170">Example</span></span>

<span data-ttu-id="b336a-171">The following example demonstrates that the run-time type can differ when a variable is identified as an `Object`.</span><span class="sxs-lookup"><span data-stu-id="b336a-171">The following example demonstrates that the run-time type can differ when a variable is identified as an `Object`.</span></span>

[!code-vb[VbVbalrTypeInference#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#11)]

## <a name="see-also"></a><span data-ttu-id="b336a-172">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b336a-172">See also</span></span>

- [<span data-ttu-id="b336a-173">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="b336a-173">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="b336a-174">Yerel Çıkarım</span><span class="sxs-lookup"><span data-stu-id="b336a-174">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="b336a-175">Option Compare Deyimi</span><span class="sxs-lookup"><span data-stu-id="b336a-175">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="b336a-176">Option Explicit Deyimi</span><span class="sxs-lookup"><span data-stu-id="b336a-176">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="b336a-177">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="b336a-177">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="b336a-178">Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu</span><span class="sxs-lookup"><span data-stu-id="b336a-178">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [<span data-ttu-id="b336a-179">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="b336a-179">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="b336a-180">Kutulama ve Kutudan Çıkarma</span><span class="sxs-lookup"><span data-stu-id="b336a-180">Boxing and Unboxing</span></span>](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
