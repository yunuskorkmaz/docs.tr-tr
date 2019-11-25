---
title: Dize Temelleri
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Like operator
- strings [Visual Basic], Visual Basic
- strings [Visual Basic], regular expressions
ms.assetid: 5674418d-f00d-4f72-9f98-d15897793350
ms.openlocfilehash: 7141966e3c8a8cbce42111c56a85a00709e8fe1a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344289"
---
# <a name="string-basics-in-visual-basic"></a><span data-ttu-id="dfa10-102">Visual Basic'de Dize Temelleri</span><span class="sxs-lookup"><span data-stu-id="dfa10-102">String Basics in Visual Basic</span></span>
<span data-ttu-id="dfa10-103">The `String` data type represents a series of characters (each representing in turn an instance of the `Char` data type).</span><span class="sxs-lookup"><span data-stu-id="dfa10-103">The `String` data type represents a series of characters (each representing in turn an instance of the `Char` data type).</span></span> <span data-ttu-id="dfa10-104">This topic introduces the basic concepts of strings in Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="dfa10-104">This topic introduces the basic concepts of strings in Visual Basic.</span></span>  
  
## <a name="string-variables"></a><span data-ttu-id="dfa10-105">String Variables</span><span class="sxs-lookup"><span data-stu-id="dfa10-105">String Variables</span></span>  
 <span data-ttu-id="dfa10-106">An instance of a string can be assigned a literal value that represents a series of characters.</span><span class="sxs-lookup"><span data-stu-id="dfa10-106">An instance of a string can be assigned a literal value that represents a series of characters.</span></span> <span data-ttu-id="dfa10-107">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="dfa10-107">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#63)]  
  
 <span data-ttu-id="dfa10-108">A `String` variable can also accept any expression that evaluates to a string.</span><span class="sxs-lookup"><span data-stu-id="dfa10-108">A `String` variable can also accept any expression that evaluates to a string.</span></span> <span data-ttu-id="dfa10-109">Aşağıda örnekler gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="dfa10-109">Examples are shown below:</span></span>  
  
 [!code-vb[VbVbalrStrings#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#64)]  
  
 <span data-ttu-id="dfa10-110">Any literal that is assigned to a `String` variable must be enclosed in quotation marks ("").</span><span class="sxs-lookup"><span data-stu-id="dfa10-110">Any literal that is assigned to a `String` variable must be enclosed in quotation marks ("").</span></span> <span data-ttu-id="dfa10-111">This means that a quotation mark within a string cannot be represented by a quotation mark.</span><span class="sxs-lookup"><span data-stu-id="dfa10-111">This means that a quotation mark within a string cannot be represented by a quotation mark.</span></span> <span data-ttu-id="dfa10-112">For example, the following code causes a compiler error:</span><span class="sxs-lookup"><span data-stu-id="dfa10-112">For example, the following code causes a compiler error:</span></span>  
  
 [!code-vb[VbVbalrStrings#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#65)]  
  
 <span data-ttu-id="dfa10-113">This code causes an error because the compiler terminates the string after the second quotation mark, and the remainder of the string is interpreted as code.</span><span class="sxs-lookup"><span data-stu-id="dfa10-113">This code causes an error because the compiler terminates the string after the second quotation mark, and the remainder of the string is interpreted as code.</span></span> <span data-ttu-id="dfa10-114">To solve this problem, Visual Basic interprets two quotation marks in a string literal as one quotation mark in the string.</span><span class="sxs-lookup"><span data-stu-id="dfa10-114">To solve this problem, Visual Basic interprets two quotation marks in a string literal as one quotation mark in the string.</span></span> <span data-ttu-id="dfa10-115">The following example demonstrates the correct way to include a quotation mark in a string:</span><span class="sxs-lookup"><span data-stu-id="dfa10-115">The following example demonstrates the correct way to include a quotation mark in a string:</span></span>  
  
 [!code-vb[VbVbalrStrings#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#66)]  
  
 <span data-ttu-id="dfa10-116">In the preceding example, the two quotation marks preceding the word `Look` become one quotation mark in the string.</span><span class="sxs-lookup"><span data-stu-id="dfa10-116">In the preceding example, the two quotation marks preceding the word `Look` become one quotation mark in the string.</span></span> <span data-ttu-id="dfa10-117">The three quotation marks at the end of the line represent one quotation mark in the string and the string termination character.</span><span class="sxs-lookup"><span data-stu-id="dfa10-117">The three quotation marks at the end of the line represent one quotation mark in the string and the string termination character.</span></span>  
  
 <span data-ttu-id="dfa10-118">String literals can contain multiple lines:</span><span class="sxs-lookup"><span data-stu-id="dfa10-118">String literals can contain multiple lines:</span></span>  
  
```vb  
Dim x = "hello  
world"  
```  
  
 <span data-ttu-id="dfa10-119">The resulting string contains newline sequences that you used in your string literal (vbcr, vbcrlf, etc.).</span><span class="sxs-lookup"><span data-stu-id="dfa10-119">The resulting string contains newline sequences that you used in your string literal (vbcr, vbcrlf, etc.).</span></span>  <span data-ttu-id="dfa10-120">You no longer need to use the old workaround:</span><span class="sxs-lookup"><span data-stu-id="dfa10-120">You no longer need to use the old workaround:</span></span>  
  
```vb  
Dim x = <xml><![CDATA[Hello  
World]]></xml>.Value  
```  
  
## <a name="characters-in-strings"></a><span data-ttu-id="dfa10-121">Characters in Strings</span><span class="sxs-lookup"><span data-stu-id="dfa10-121">Characters in Strings</span></span>  
 <span data-ttu-id="dfa10-122">A string can be thought of as a series of `Char` values, and the `String` type has built-in functions that allow you to perform many manipulations on a string that resemble the manipulations allowed by arrays.</span><span class="sxs-lookup"><span data-stu-id="dfa10-122">A string can be thought of as a series of `Char` values, and the `String` type has built-in functions that allow you to perform many manipulations on a string that resemble the manipulations allowed by arrays.</span></span> <span data-ttu-id="dfa10-123">Like all array in .NET Framework, these are zero-based arrays.</span><span class="sxs-lookup"><span data-stu-id="dfa10-123">Like all array in .NET Framework, these are zero-based arrays.</span></span> <span data-ttu-id="dfa10-124">You may refer to a specific character in a string through the `Chars` property, which provides a way to access a character by the position in which it appears in the string.</span><span class="sxs-lookup"><span data-stu-id="dfa10-124">You may refer to a specific character in a string through the `Chars` property, which provides a way to access a character by the position in which it appears in the string.</span></span> <span data-ttu-id="dfa10-125">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="dfa10-125">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#67)]  
  
 <span data-ttu-id="dfa10-126">In the above example, the `Chars` property of the string returns the fourth character in the string, which is `D`, and assigns it to `myChar`.</span><span class="sxs-lookup"><span data-stu-id="dfa10-126">In the above example, the `Chars` property of the string returns the fourth character in the string, which is `D`, and assigns it to `myChar`.</span></span> <span data-ttu-id="dfa10-127">You can also get the length of a particular string through the `Length` property.</span><span class="sxs-lookup"><span data-stu-id="dfa10-127">You can also get the length of a particular string through the `Length` property.</span></span> <span data-ttu-id="dfa10-128">If you need to perform multiple array-type manipulations on a string, you can convert it to an array of `Char` instances using the `ToCharArray` function of the string.</span><span class="sxs-lookup"><span data-stu-id="dfa10-128">If you need to perform multiple array-type manipulations on a string, you can convert it to an array of `Char` instances using the `ToCharArray` function of the string.</span></span> <span data-ttu-id="dfa10-129">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="dfa10-129">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#68)]  
  
 <span data-ttu-id="dfa10-130">The variable `myArray` now contains an array of `Char` values, each representing a character from `myString`.</span><span class="sxs-lookup"><span data-stu-id="dfa10-130">The variable `myArray` now contains an array of `Char` values, each representing a character from `myString`.</span></span>  
  
## <a name="the-immutability-of-strings"></a><span data-ttu-id="dfa10-131">The Immutability of Strings</span><span class="sxs-lookup"><span data-stu-id="dfa10-131">The Immutability of Strings</span></span>  
 <span data-ttu-id="dfa10-132">A string is *immutable*, which means its value cannot be changed once it has been created.</span><span class="sxs-lookup"><span data-stu-id="dfa10-132">A string is *immutable*, which means its value cannot be changed once it has been created.</span></span> <span data-ttu-id="dfa10-133">However, this does not prevent you from assigning more than one value to a string variable.</span><span class="sxs-lookup"><span data-stu-id="dfa10-133">However, this does not prevent you from assigning more than one value to a string variable.</span></span> <span data-ttu-id="dfa10-134">Consider the following example:</span><span class="sxs-lookup"><span data-stu-id="dfa10-134">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#69)]  
  
 <span data-ttu-id="dfa10-135">Here, a string variable is created, given a value, and then its value is changed.</span><span class="sxs-lookup"><span data-stu-id="dfa10-135">Here, a string variable is created, given a value, and then its value is changed.</span></span>  
  
 <span data-ttu-id="dfa10-136">More specifically, in the first line, an instance of type `String` is created and given the value `This string is immutable`.</span><span class="sxs-lookup"><span data-stu-id="dfa10-136">More specifically, in the first line, an instance of type `String` is created and given the value `This string is immutable`.</span></span> <span data-ttu-id="dfa10-137">In the second line of the example, a new instance is created and given the value `Or is it?`, and the string variable discards its reference to the first instance and stores a reference to the new instance.</span><span class="sxs-lookup"><span data-stu-id="dfa10-137">In the second line of the example, a new instance is created and given the value `Or is it?`, and the string variable discards its reference to the first instance and stores a reference to the new instance.</span></span>  
  
 <span data-ttu-id="dfa10-138">Unlike other intrinsic data types, `String` is a reference type.</span><span class="sxs-lookup"><span data-stu-id="dfa10-138">Unlike other intrinsic data types, `String` is a reference type.</span></span> <span data-ttu-id="dfa10-139">When a variable of reference type is passed as an argument to a function or subroutine, a reference to the memory address where the data is stored is passed instead of the actual value of the string.</span><span class="sxs-lookup"><span data-stu-id="dfa10-139">When a variable of reference type is passed as an argument to a function or subroutine, a reference to the memory address where the data is stored is passed instead of the actual value of the string.</span></span> <span data-ttu-id="dfa10-140">So in the previous example, the name of the variable remains the same, but it points to a new and different instance of the `String` class, which holds the new value.</span><span class="sxs-lookup"><span data-stu-id="dfa10-140">So in the previous example, the name of the variable remains the same, but it points to a new and different instance of the `String` class, which holds the new value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfa10-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dfa10-141">See also</span></span>

- [<span data-ttu-id="dfa10-142">Introduction to Strings in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dfa10-142">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
- [<span data-ttu-id="dfa10-143">String Veri Türü</span><span class="sxs-lookup"><span data-stu-id="dfa10-143">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)
- [<span data-ttu-id="dfa10-144">Char Veri Türü</span><span class="sxs-lookup"><span data-stu-id="dfa10-144">Char Data Type</span></span>](../../../../visual-basic/language-reference/data-types/char-data-type.md)
- [<span data-ttu-id="dfa10-145">Temel Dize İşlemleri</span><span class="sxs-lookup"><span data-stu-id="dfa10-145">Basic String Operations</span></span>](../../../../standard/base-types/basic-string-operations.md)
