---
description: 'Daha fazla bilgi edinin: operatör yordamları (Visual Basic)'
title: İşleç Yordamları
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
ms.assetid: 8c513d38-246b-4fb7-8b75-29e1364e555b
ms.openlocfilehash: 836eeb2e705a96c49b5fa53e277ccf025d1915b2
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100479965"
---
# <a name="operator-procedures-visual-basic"></a><span data-ttu-id="9057d-103">İşleç Yordamları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9057d-103">Operator Procedures (Visual Basic)</span></span>

<span data-ttu-id="9057d-104">İşleç yordamı, `*` `<>` `And` tanımladığınız bir sınıf veya yapıda standart işlecin (örneğin,, veya) davranışını tanımlayan Visual Basic deyimlerinin bir dizisidir.</span><span class="sxs-lookup"><span data-stu-id="9057d-104">An operator procedure is a series of Visual Basic statements that define the behavior of a standard operator (such as `*`, `<>`, or `And`) on a class or structure you have defined.</span></span> <span data-ttu-id="9057d-105">Buna *işleç aşırı yüklemesi* de denir.</span><span class="sxs-lookup"><span data-stu-id="9057d-105">This is also called *operator overloading*.</span></span>

## <a name="when-to-define-operator-procedures"></a><span data-ttu-id="9057d-106">Operatör yordamları ne zaman tanımlanır</span><span class="sxs-lookup"><span data-stu-id="9057d-106">When to Define Operator Procedures</span></span>

<span data-ttu-id="9057d-107">Bir sınıf veya yapı tanımladığınızda, değişkenleri bu sınıf veya yapının türünde olacak şekilde bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9057d-107">When you have defined a class or structure, you can declare variables to be of the type of that class or structure.</span></span> <span data-ttu-id="9057d-108">Bazen bu tür bir değişkenin bir ifadenin parçası olarak bir işleme katılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9057d-108">Sometimes such a variable needs to participate in an operation as part of an expression.</span></span> <span data-ttu-id="9057d-109">Bunu yapmak için, bir işlecinin işleneni olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9057d-109">To do this, it must be an operand of an operator.</span></span>

<span data-ttu-id="9057d-110">Visual Basic işleçleri yalnızca temel veri türlerinde tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9057d-110">Visual Basic defines operators only on its fundamental data types.</span></span> <span data-ttu-id="9057d-111">Bir işlecin bir veya her ikisi de sınıfınızın veya yapınızın türünden olduğunda bir işlecin davranışını tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9057d-111">You can define the behavior of an operator when one or both of the operands are of the type of your class or structure.</span></span>

<span data-ttu-id="9057d-112">Daha fazla bilgi için bkz. [operator deyimleri](../../../language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9057d-112">For more information, see [Operator Statement](../../../language-reference/statements/operator-statement.md).</span></span>

## <a name="types-of-operator-procedure"></a><span data-ttu-id="9057d-113">Işleç yordamının türleri</span><span class="sxs-lookup"><span data-stu-id="9057d-113">Types of Operator Procedure</span></span>

<span data-ttu-id="9057d-114">Bir işleç yordamı aşağıdaki türlerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="9057d-114">An operator procedure can be one of the following types:</span></span>

- <span data-ttu-id="9057d-115">Bağımsız değişkenin sınıfınızın veya yapınızın türünde olduğu birli işlecin tanımı.</span><span class="sxs-lookup"><span data-stu-id="9057d-115">A definition of a unary operator where the argument is of the type of your class or structure.</span></span>

- <span data-ttu-id="9057d-116">Bağımsız değişkenlerden en az birinin sınıfınızın veya yapınızın türü olduğu bir ikili işlecinin tanımı.</span><span class="sxs-lookup"><span data-stu-id="9057d-116">A definition of a binary operator where at least one of the arguments is of the type of your class or structure.</span></span>

- <span data-ttu-id="9057d-117">Bağımsız değişkenin sınıfınızın veya yapınızın türünde olduğu bir dönüştürme işlecinin tanımı.</span><span class="sxs-lookup"><span data-stu-id="9057d-117">A definition of a conversion operator where the argument is of the type of your class or structure.</span></span>

- <span data-ttu-id="9057d-118">Sınıfınızın veya yapınızın türünü döndüren bir dönüştürme işlecinin tanımı.</span><span class="sxs-lookup"><span data-stu-id="9057d-118">A definition of a conversion operator that returns the type of your class or structure.</span></span>

 <span data-ttu-id="9057d-119">Dönüştürme işleçleri her zaman birli ve `CType` tanımladığınız operatör olarak her zaman kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9057d-119">Conversion operators are always unary, and you always use `CType` as the operator you are defining.</span></span>

## <a name="declaration-syntax"></a><span data-ttu-id="9057d-120">Bildirim Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9057d-120">Declaration Syntax</span></span>

<span data-ttu-id="9057d-121">Bir işleç yordamını bildirmek için sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="9057d-121">The syntax for declaring an operator procedure is as follows:</span></span>

```vb
Public Shared [Widening | Narrowing] Operator operatorsymbol ( operand1 [,  operand2 ]) As datatype

' Statements of the operator procedure.

End Operator
```

<span data-ttu-id="9057d-122">`Widening`Or `Narrowing` anahtar sözcüğünü yalnızca bir tür dönüştürme işleci üzerinde kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="9057d-122">You use the `Widening` or `Narrowing` keyword only on a type conversion operator.</span></span> <span data-ttu-id="9057d-123">İşleç sembolü, bir tür dönüştürme işleci için her zaman [CType işlevidir](../../../language-reference/functions/ctype-function.md) .</span><span class="sxs-lookup"><span data-stu-id="9057d-123">The operator symbol is always [CType Function](../../../language-reference/functions/ctype-function.md) for a type conversion operator.</span></span>

<span data-ttu-id="9057d-124">İkili bir işleç tanımlamak için iki işlenen bildirir ve bir tür dönüştürme işleci dahil birli işleç tanımlamak için bir işlenen bildirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9057d-124">You declare two operands to define a binary operator, and you declare one operand to define a unary operator, including a type conversion operator.</span></span> <span data-ttu-id="9057d-125">Tüm işlenenler bildirilmelidir `ByVal` .</span><span class="sxs-lookup"><span data-stu-id="9057d-125">All operands must be declared `ByVal`.</span></span>

<span data-ttu-id="9057d-126">Her işleneni, [Sub yordamları](./sub-procedures.md)için parametreleri bildirdiğiniz şekilde bildirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9057d-126">You declare each operand the same way you declare parameters for [Sub Procedures](./sub-procedures.md).</span></span>

### <a name="data-type"></a><span data-ttu-id="9057d-127">Veri Türü</span><span class="sxs-lookup"><span data-stu-id="9057d-127">Data Type</span></span>

<span data-ttu-id="9057d-128">Tanımladığınız bir sınıf veya yapı üzerinde bir işleç tanımladığınız için işlenenlerinden en az birinin bu sınıf veya yapının veri türünde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9057d-128">Because you are defining an operator on a class or structure you have defined, at least one of the operands must be of the data type of that class or structure.</span></span> <span data-ttu-id="9057d-129">Bir tür dönüştürme işleci için, işlenen ya da dönüş türü, sınıfın veya yapının veri türünde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9057d-129">For a type conversion operator, either the operand or the return type must be of the data type of the class or structure.</span></span>

<span data-ttu-id="9057d-130">Daha ayrıntılı bilgi için bkz. [Işleç açıklaması](../../../language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9057d-130">For more details, see [Operator Statement](../../../language-reference/statements/operator-statement.md).</span></span>

## <a name="calling-syntax"></a><span data-ttu-id="9057d-131">Çağırma sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9057d-131">Calling Syntax</span></span>

<span data-ttu-id="9057d-132">Bir ifadede işleç sembolünü kullanarak örtük olarak bir operatör yordamı çağırılır.</span><span class="sxs-lookup"><span data-stu-id="9057d-132">You invoke an operator procedure implicitly by using the operator symbol in an expression.</span></span> <span data-ttu-id="9057d-133">İşlenenleri önceden tanımlanmış işleçler için yaptığınız şekilde sağlarsınız.</span><span class="sxs-lookup"><span data-stu-id="9057d-133">You supply the operands the same way you do for predefined operators.</span></span>

<span data-ttu-id="9057d-134">İşleç yordamına örtük çağrının sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="9057d-134">The syntax for an implicit call to an operator procedure is as follows:</span></span>

<span data-ttu-id="9057d-135">`Dim testStruct As`  *structurename*</span><span class="sxs-lookup"><span data-stu-id="9057d-135">`Dim testStruct As`  *structurename*</span></span>

<span data-ttu-id="9057d-136">`Dim testNewStruct As`  *structurename* `= testStruct` *operatorsymbol*      `10`</span><span class="sxs-lookup"><span data-stu-id="9057d-136">`Dim testNewStruct As`  *structurename*  `= testStruct`  *operatorsymbol*  `10`</span></span>

### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="9057d-137">Bildirim ve çağrı gösterimi</span><span class="sxs-lookup"><span data-stu-id="9057d-137">Illustration of Declaration and Call</span></span>

<span data-ttu-id="9057d-138">Aşağıdaki yapı, imzalı bir 128 bitlik tamsayı değerini, anayen yüksek sıralı ve düşük sıralı parçalar olarak depolar.</span><span class="sxs-lookup"><span data-stu-id="9057d-138">The following structure stores a signed 128-bit integer value as the constituent high-order and low-order parts.</span></span> <span data-ttu-id="9057d-139">`+`İki `veryLong` değer eklemek ve elde edilen bir değer oluşturmak için işlecini tanımlar `veryLong` .</span><span class="sxs-lookup"><span data-stu-id="9057d-139">It defines the `+` operator to add two `veryLong` values and generate a resulting `veryLong` value.</span></span>

[!code-vb[VbVbcnProcedures#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#23)]

<span data-ttu-id="9057d-140">Aşağıdaki örnek, üzerinde tanımlanan işlecine tipik bir çağrı gösterir `+` `veryLong` .</span><span class="sxs-lookup"><span data-stu-id="9057d-140">The following example shows a typical call to the `+` operator defined on `veryLong`.</span></span>

[!code-vb[VbVbcnProcedures#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#24)]

## <a name="see-also"></a><span data-ttu-id="9057d-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9057d-141">See also</span></span>

- [<span data-ttu-id="9057d-142">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="9057d-142">Procedures</span></span>](./index.md)
- [<span data-ttu-id="9057d-143">Alt Yordamlar</span><span class="sxs-lookup"><span data-stu-id="9057d-143">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="9057d-144">İşlev Yordamları</span><span class="sxs-lookup"><span data-stu-id="9057d-144">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="9057d-145">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="9057d-145">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="9057d-146">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="9057d-146">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="9057d-147">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="9057d-147">Operator Statement</span></span>](../../../language-reference/statements/operator-statement.md)
- [<span data-ttu-id="9057d-148">Nasıl yapılır: İşleç Tanımlama</span><span class="sxs-lookup"><span data-stu-id="9057d-148">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="9057d-149">Nasıl yapılır: Dönüştürme İşleci Tanımlama</span><span class="sxs-lookup"><span data-stu-id="9057d-149">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="9057d-150">Nasıl yapılır: Bir İşleç Yordamı Çağırma</span><span class="sxs-lookup"><span data-stu-id="9057d-150">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="9057d-151">Nasıl yapılır: İşleçleri Tanımlayan Bir Sınıf Kullanma</span><span class="sxs-lookup"><span data-stu-id="9057d-151">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
