---
title: Imports Statement - .NET Namespace and Type
ms.date: 07/20/2015
f1_keywords:
- vb.Imports
- imports
helpviewer_keywords:
- declared element names [Visual Basic], qualification
- imports [Visual Basic]
- Imports statement [Visual Basic]
- aliases [Visual Basic], Imports statement
- container elements [Visual Basic]
- namespaces [Visual Basic], importing
- Imports statement [Visual Basic], syntax
- import aliases [Visual Basic]
- aliases [Visual Basic], import
- declared elements [Visual Basic], container elements
ms.assetid: 7062f8aa-d890-4232-9eed-92836e13fb6e
ms.openlocfilehash: 39fa4e74f973bcb575b5751c387c0b879f4e398d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351076"
---
# <a name="imports-statement-net-namespace-and-type"></a><span data-ttu-id="6b797-102">Imports Deyimi (.NET Ad Alanı ve Türü)</span><span class="sxs-lookup"><span data-stu-id="6b797-102">Imports Statement (.NET Namespace and Type)</span></span>

<span data-ttu-id="6b797-103">Enables type names to be referenced without namespace qualification.</span><span class="sxs-lookup"><span data-stu-id="6b797-103">Enables type names to be referenced without namespace qualification.</span></span>

## <a name="syntax"></a><span data-ttu-id="6b797-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6b797-104">Syntax</span></span>

```vb
Imports [ aliasname = ] namespace
' -or-
Imports [ aliasname = ] namespace.element
```

## <a name="parts"></a><span data-ttu-id="6b797-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="6b797-105">Parts</span></span>

|<span data-ttu-id="6b797-106">Terim</span><span class="sxs-lookup"><span data-stu-id="6b797-106">Term</span></span>|<span data-ttu-id="6b797-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="6b797-107">Definition</span></span>|
|---|---|
|`aliasname`|<span data-ttu-id="6b797-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="6b797-108">Optional.</span></span> <span data-ttu-id="6b797-109">An *import alias* or name by which code can refer to `namespace` instead of the full qualification string.</span><span class="sxs-lookup"><span data-stu-id="6b797-109">An *import alias* or name by which code can refer to `namespace` instead of the full qualification string.</span></span> <span data-ttu-id="6b797-110">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="6b797-110">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|
|`namespace`|<span data-ttu-id="6b797-111">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="6b797-111">Required.</span></span> <span data-ttu-id="6b797-112">The fully qualified name of the namespace being imported.</span><span class="sxs-lookup"><span data-stu-id="6b797-112">The fully qualified name of the namespace being imported.</span></span> <span data-ttu-id="6b797-113">Can be a string of namespaces nested to any level.</span><span class="sxs-lookup"><span data-stu-id="6b797-113">Can be a string of namespaces nested to any level.</span></span>|
|`element`|<span data-ttu-id="6b797-114">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="6b797-114">Optional.</span></span> <span data-ttu-id="6b797-115">The name of a programming element declared in the namespace.</span><span class="sxs-lookup"><span data-stu-id="6b797-115">The name of a programming element declared in the namespace.</span></span> <span data-ttu-id="6b797-116">Can be any container element.</span><span class="sxs-lookup"><span data-stu-id="6b797-116">Can be any container element.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6b797-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6b797-117">Remarks</span></span>

<span data-ttu-id="6b797-118">The `Imports` statement enables types that are contained in a given namespace to be referenced directly.</span><span class="sxs-lookup"><span data-stu-id="6b797-118">The `Imports` statement enables types that are contained in a given namespace to be referenced directly.</span></span>

<span data-ttu-id="6b797-119">You can supply a single namespace name or a string of nested namespaces.</span><span class="sxs-lookup"><span data-stu-id="6b797-119">You can supply a single namespace name or a string of nested namespaces.</span></span> <span data-ttu-id="6b797-120">Each nested namespace is separated from the next higher level namespace by a period (`.`), as the following example illustrates:</span><span class="sxs-lookup"><span data-stu-id="6b797-120">Each nested namespace is separated from the next higher level namespace by a period (`.`), as the following example illustrates:</span></span>

```vb
Imports System.Collections.Generic
```

<span data-ttu-id="6b797-121">Each source file can contain any number of `Imports` statements.</span><span class="sxs-lookup"><span data-stu-id="6b797-121">Each source file can contain any number of `Imports` statements.</span></span> <span data-ttu-id="6b797-122">These must follow any option declarations, such as the `Option Strict` statement, and they must precede any programming element declarations, such as `Module` or `Class` statements.</span><span class="sxs-lookup"><span data-stu-id="6b797-122">These must follow any option declarations, such as the `Option Strict` statement, and they must precede any programming element declarations, such as `Module` or `Class` statements.</span></span>

<span data-ttu-id="6b797-123">You can use `Imports` only at file level.</span><span class="sxs-lookup"><span data-stu-id="6b797-123">You can use `Imports` only at file level.</span></span> <span data-ttu-id="6b797-124">This means the declaration context for importation must be a source file, and cannot be a namespace, class, structure, module, interface, procedure, or block.</span><span class="sxs-lookup"><span data-stu-id="6b797-124">This means the declaration context for importation must be a source file, and cannot be a namespace, class, structure, module, interface, procedure, or block.</span></span>

<span data-ttu-id="6b797-125">Note that the `Imports` statement does not make elements from other projects and assemblies available to your project.</span><span class="sxs-lookup"><span data-stu-id="6b797-125">Note that the `Imports` statement does not make elements from other projects and assemblies available to your project.</span></span> <span data-ttu-id="6b797-126">Importing does not take the place of setting a reference.</span><span class="sxs-lookup"><span data-stu-id="6b797-126">Importing does not take the place of setting a reference.</span></span> <span data-ttu-id="6b797-127">It only removes the need to qualify names that are already available to your project.</span><span class="sxs-lookup"><span data-stu-id="6b797-127">It only removes the need to qualify names that are already available to your project.</span></span> <span data-ttu-id="6b797-128">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="6b797-128">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

> [!NOTE]
> <span data-ttu-id="6b797-129">You can define implicit `Imports` statements by using the [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="6b797-129">You can define implicit `Imports` statements by using the [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span> <span data-ttu-id="6b797-130">For more information, see [How to: Add or Remove Imported Namespaces (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="6b797-130">For more information, see [How to: Add or Remove Imported Namespaces (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span></span>

## <a name="import-aliases"></a><span data-ttu-id="6b797-131">Import Aliases</span><span class="sxs-lookup"><span data-stu-id="6b797-131">Import Aliases</span></span>

<span data-ttu-id="6b797-132">An *import alias* defines the alias for a namespace or type.</span><span class="sxs-lookup"><span data-stu-id="6b797-132">An *import alias* defines the alias for a namespace or type.</span></span> <span data-ttu-id="6b797-133">Import aliases are useful when you need to use items with the same name that are declared in one or more namespaces.</span><span class="sxs-lookup"><span data-stu-id="6b797-133">Import aliases are useful when you need to use items with the same name that are declared in one or more namespaces.</span></span> <span data-ttu-id="6b797-134">For more information and an example, see "Qualifying an Element Name" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="6b797-134">For more information and an example, see "Qualifying an Element Name" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

<span data-ttu-id="6b797-135">You should not declare a member at module level with the same name as `aliasname`.</span><span class="sxs-lookup"><span data-stu-id="6b797-135">You should not declare a member at module level with the same name as `aliasname`.</span></span> <span data-ttu-id="6b797-136">If you do, the Visual Basic compiler uses `aliasname` only for the declared member and no longer recognizes it as an import alias.</span><span class="sxs-lookup"><span data-stu-id="6b797-136">If you do, the Visual Basic compiler uses `aliasname` only for the declared member and no longer recognizes it as an import alias.</span></span>

<span data-ttu-id="6b797-137">Although the syntax used for declaring an import alias is like that used for importing an XML namespace prefix, the results are different.</span><span class="sxs-lookup"><span data-stu-id="6b797-137">Although the syntax used for declaring an import alias is like that used for importing an XML namespace prefix, the results are different.</span></span> <span data-ttu-id="6b797-138">An import alias can be used as an expression in your code, whereas an XML namespace prefix can be used only in XML literals or XML axis properties as the prefix for a qualified element or attribute name.</span><span class="sxs-lookup"><span data-stu-id="6b797-138">An import alias can be used as an expression in your code, whereas an XML namespace prefix can be used only in XML literals or XML axis properties as the prefix for a qualified element or attribute name.</span></span>

### <a name="element-names"></a><span data-ttu-id="6b797-139">Öğe adları</span><span class="sxs-lookup"><span data-stu-id="6b797-139">Element Names</span></span>

<span data-ttu-id="6b797-140">If you supply `element`, it must represent a *container element*, that is, a programming element that can contain other elements.</span><span class="sxs-lookup"><span data-stu-id="6b797-140">If you supply `element`, it must represent a *container element*, that is, a programming element that can contain other elements.</span></span> <span data-ttu-id="6b797-141">Container elements include classes, structures, modules, interfaces, and enumerations.</span><span class="sxs-lookup"><span data-stu-id="6b797-141">Container elements include classes, structures, modules, interfaces, and enumerations.</span></span>

<span data-ttu-id="6b797-142">The scope of the elements made available by an `Imports` statement depends on whether you specify `element`.</span><span class="sxs-lookup"><span data-stu-id="6b797-142">The scope of the elements made available by an `Imports` statement depends on whether you specify `element`.</span></span> <span data-ttu-id="6b797-143">If you specify only `namespace`, all uniquely named members of that namespace, and members of container elements within that namespace, are available without qualification.</span><span class="sxs-lookup"><span data-stu-id="6b797-143">If you specify only `namespace`, all uniquely named members of that namespace, and members of container elements within that namespace, are available without qualification.</span></span> <span data-ttu-id="6b797-144">If you specify both `namespace` and `element`, only the members of that element are available without qualification.</span><span class="sxs-lookup"><span data-stu-id="6b797-144">If you specify both `namespace` and `element`, only the members of that element are available without qualification.</span></span>

## <a name="example"></a><span data-ttu-id="6b797-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="6b797-145">Example</span></span>

<span data-ttu-id="6b797-146">The following example returns all the folders in the *C:\\* directory by using the <xref:System.IO.DirectoryInfo> class:</span><span class="sxs-lookup"><span data-stu-id="6b797-146">The following example returns all the folders in the *C:\\* directory by using the <xref:System.IO.DirectoryInfo> class:</span></span>

<span data-ttu-id="6b797-147">The code has no `Imports` statements at the top of the file.</span><span class="sxs-lookup"><span data-stu-id="6b797-147">The code has no `Imports` statements at the top of the file.</span></span> <span data-ttu-id="6b797-148">Therefore, the <xref:System.IO.DirectoryInfo>, <xref:System.Text.StringBuilder>, and <xref:Microsoft.VisualBasic.ControlChars.CrLf> references are all fully qualified with the namespaces.</span><span class="sxs-lookup"><span data-stu-id="6b797-148">Therefore, the <xref:System.IO.DirectoryInfo>, <xref:System.Text.StringBuilder>, and <xref:Microsoft.VisualBasic.ControlChars.CrLf> references are all fully qualified with the namespaces.</span></span>

[!code-vb[VbVbalrStatements#152](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#152)]

## <a name="example"></a><span data-ttu-id="6b797-149">Örnek</span><span class="sxs-lookup"><span data-stu-id="6b797-149">Example</span></span>

<span data-ttu-id="6b797-150">The following example includes `Imports` statements for the referenced namespaces.</span><span class="sxs-lookup"><span data-stu-id="6b797-150">The following example includes `Imports` statements for the referenced namespaces.</span></span> <span data-ttu-id="6b797-151">Therefore, the types do not have to be fully qualified with the namespaces.</span><span class="sxs-lookup"><span data-stu-id="6b797-151">Therefore, the types do not have to be fully qualified with the namespaces.</span></span>

[!code-vb[VbVbalrStatements#153](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#153)]

[!code-vb[VbVbalrStatements#154](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#154)]
  
## <a name="example"></a><span data-ttu-id="6b797-152">Örnek</span><span class="sxs-lookup"><span data-stu-id="6b797-152">Example</span></span>

<span data-ttu-id="6b797-153">The following example includes `Imports` statements that create aliases for the referenced namespaces.</span><span class="sxs-lookup"><span data-stu-id="6b797-153">The following example includes `Imports` statements that create aliases for the referenced namespaces.</span></span> <span data-ttu-id="6b797-154">The types are qualified with the aliases.</span><span class="sxs-lookup"><span data-stu-id="6b797-154">The types are qualified with the aliases.</span></span>

[!code-vb[VbVbalrStatements#155](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#155)]

[!code-vb[VbVbalrStatements#156](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#156)]

## <a name="example"></a><span data-ttu-id="6b797-155">Örnek</span><span class="sxs-lookup"><span data-stu-id="6b797-155">Example</span></span>

<span data-ttu-id="6b797-156">The following example includes `Imports` statements that create aliases for the referenced types.</span><span class="sxs-lookup"><span data-stu-id="6b797-156">The following example includes `Imports` statements that create aliases for the referenced types.</span></span> <span data-ttu-id="6b797-157">Aliases are used to specify the types.</span><span class="sxs-lookup"><span data-stu-id="6b797-157">Aliases are used to specify the types.</span></span>

[!code-vb[VbVbalrStatements#157](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#157)]

[!code-vb[VbVbalrStatements#158](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#158)]
  
## <a name="see-also"></a><span data-ttu-id="6b797-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b797-158">See also</span></span>

- [<span data-ttu-id="6b797-159">Namespace Deyimi</span><span class="sxs-lookup"><span data-stu-id="6b797-159">Namespace Statement</span></span>](namespace-statement.md)
- [<span data-ttu-id="6b797-160">Namespaces in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6b797-160">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="6b797-161">References ve Imports Deyimi</span><span class="sxs-lookup"><span data-stu-id="6b797-161">References and the Imports Statement</span></span>](../../programming-guide/program-structure/references-and-the-imports-statement.md)
- [<span data-ttu-id="6b797-162">Imports Deyimi (XML Ad Alanı)</span><span class="sxs-lookup"><span data-stu-id="6b797-162">Imports Statement (XML Namespace)</span></span>](imports-statement-xml-namespace.md)
- [<span data-ttu-id="6b797-163">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="6b797-163">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
