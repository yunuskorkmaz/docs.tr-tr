---
title: İşleç Yordamları (Visual Basic)
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
ms.openlocfilehash: 46afbbe411a1adf27960e3c7d9d3ca98046ecec5
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524533"
---
# <a name="operator-procedures-visual-basic"></a><span data-ttu-id="abf98-102">İşleç Yordamları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="abf98-102">Operator Procedures (Visual Basic)</span></span>

<span data-ttu-id="abf98-103">İşleç yordamı, tanımladığınız bir sınıf veya yapıda standart bir işlecin (`*`, `<>` veya `And`) davranışını tanımlayan Visual Basic deyimlerinin bir dizisidir.</span><span class="sxs-lookup"><span data-stu-id="abf98-103">An operator procedure is a series of Visual Basic statements that define the behavior of a standard operator (such as `*`, `<>`, or `And`) on a class or structure you have defined.</span></span> <span data-ttu-id="abf98-104">Buna *işleç aşırı yüklemesi*de denir.</span><span class="sxs-lookup"><span data-stu-id="abf98-104">This is also called *operator overloading*.</span></span>

## <a name="when-to-define-operator-procedures"></a><span data-ttu-id="abf98-105">Operatör yordamları ne zaman tanımlanır</span><span class="sxs-lookup"><span data-stu-id="abf98-105">When to Define Operator Procedures</span></span>

<span data-ttu-id="abf98-106">Bir sınıf veya yapı tanımladığınızda, değişkenleri bu sınıf veya yapının türünde olacak şekilde bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="abf98-106">When you have defined a class or structure, you can declare variables to be of the type of that class or structure.</span></span> <span data-ttu-id="abf98-107">Bazen bu tür bir değişkenin bir ifadenin parçası olarak bir işleme katılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="abf98-107">Sometimes such a variable needs to participate in an operation as part of an expression.</span></span> <span data-ttu-id="abf98-108">Bunu yapmak için, bir işlecinin işleneni olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="abf98-108">To do this, it must be an operand of an operator.</span></span>

<span data-ttu-id="abf98-109">Visual Basic işleçleri yalnızca temel veri türlerinde tanımlar.</span><span class="sxs-lookup"><span data-stu-id="abf98-109">Visual Basic defines operators only on its fundamental data types.</span></span> <span data-ttu-id="abf98-110">Bir işlecin bir veya her ikisi de sınıfınızın veya yapınızın türünden olduğunda bir işlecin davranışını tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="abf98-110">You can define the behavior of an operator when one or both of the operands are of the type of your class or structure.</span></span>

<span data-ttu-id="abf98-111">Daha fazla bilgi için bkz. [operator deyimleri](../../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="abf98-111">For more information, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>

## <a name="types-of-operator-procedure"></a><span data-ttu-id="abf98-112">Işleç yordamının türleri</span><span class="sxs-lookup"><span data-stu-id="abf98-112">Types of Operator Procedure</span></span>

<span data-ttu-id="abf98-113">Bir işleç yordamı aşağıdaki türlerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="abf98-113">An operator procedure can be one of the following types:</span></span>

- <span data-ttu-id="abf98-114">Bağımsız değişkenin sınıfınızın veya yapınızın türünde olduğu birli işlecin tanımı.</span><span class="sxs-lookup"><span data-stu-id="abf98-114">A definition of a unary operator where the argument is of the type of your class or structure.</span></span>

- <span data-ttu-id="abf98-115">Bağımsız değişkenlerden en az birinin sınıfınızın veya yapınızın türü olduğu bir ikili işlecinin tanımı.</span><span class="sxs-lookup"><span data-stu-id="abf98-115">A definition of a binary operator where at least one of the arguments is of the type of your class or structure.</span></span>

- <span data-ttu-id="abf98-116">Bağımsız değişkenin sınıfınızın veya yapınızın türünde olduğu bir dönüştürme işlecinin tanımı.</span><span class="sxs-lookup"><span data-stu-id="abf98-116">A definition of a conversion operator where the argument is of the type of your class or structure.</span></span>

- <span data-ttu-id="abf98-117">Sınıfınızın veya yapınızın türünü döndüren bir dönüştürme işlecinin tanımı.</span><span class="sxs-lookup"><span data-stu-id="abf98-117">A definition of a conversion operator that returns the type of your class or structure.</span></span>

 <span data-ttu-id="abf98-118">Dönüştürme işleçleri her zaman tekil değildir ve `CType` her zaman tanımladığınız operatör olarak kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="abf98-118">Conversion operators are always unary, and you always use `CType` as the operator you are defining.</span></span>

## <a name="declaration-syntax"></a><span data-ttu-id="abf98-119">Bildirim Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="abf98-119">Declaration Syntax</span></span>

<span data-ttu-id="abf98-120">Bir işleç yordamını bildirmek için sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="abf98-120">The syntax for declaring an operator procedure is as follows:</span></span>

```vb
Public Shared [Widening | Narrowing] Operator operatorsymbol ( operand1 [,  operand2 ]) As datatype

' Statements of the operator procedure.

End Operator
```

<span data-ttu-id="abf98-121">@No__t_0 veya `Narrowing` anahtar sözcüğünü yalnızca bir tür dönüştürme işleci üzerinde kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="abf98-121">You use the `Widening` or `Narrowing` keyword only on a type conversion operator.</span></span> <span data-ttu-id="abf98-122">İşleç sembolü, bir tür dönüştürme işleci için her zaman [CType işlevidir](../../../../visual-basic/language-reference/functions/ctype-function.md) .</span><span class="sxs-lookup"><span data-stu-id="abf98-122">The operator symbol is always [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) for a type conversion operator.</span></span>

<span data-ttu-id="abf98-123">İkili bir işleç tanımlamak için iki işlenen bildirir ve bir tür dönüştürme işleci dahil birli işleç tanımlamak için bir işlenen bildirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="abf98-123">You declare two operands to define a binary operator, and you declare one operand to define a unary operator, including a type conversion operator.</span></span> <span data-ttu-id="abf98-124">Tüm işlenenler `ByVal` olarak bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="abf98-124">All operands must be declared `ByVal`.</span></span>

<span data-ttu-id="abf98-125">Her işleneni, [Sub yordamları](./sub-procedures.md)için parametreleri bildirdiğiniz şekilde bildirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="abf98-125">You declare each operand the same way you declare parameters for [Sub Procedures](./sub-procedures.md).</span></span>

### <a name="data-type"></a><span data-ttu-id="abf98-126">Veri Türü</span><span class="sxs-lookup"><span data-stu-id="abf98-126">Data Type</span></span>

<span data-ttu-id="abf98-127">Tanımladığınız bir sınıf veya yapı üzerinde bir işleç tanımladığınız için işlenenlerinden en az birinin bu sınıf veya yapının veri türünde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="abf98-127">Because you are defining an operator on a class or structure you have defined, at least one of the operands must be of the data type of that class or structure.</span></span> <span data-ttu-id="abf98-128">Bir tür dönüştürme işleci için, işlenen ya da dönüş türü, sınıfın veya yapının veri türünde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="abf98-128">For a type conversion operator, either the operand or the return type must be of the data type of the class or structure.</span></span>

<span data-ttu-id="abf98-129">Daha ayrıntılı bilgi için bkz. [Işleç açıklaması](../../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="abf98-129">For more details, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>

## <a name="calling-syntax"></a><span data-ttu-id="abf98-130">Çağırma sözdizimi</span><span class="sxs-lookup"><span data-stu-id="abf98-130">Calling Syntax</span></span>

<span data-ttu-id="abf98-131">Bir ifadede işleç sembolünü kullanarak örtük olarak bir operatör yordamı çağırılır.</span><span class="sxs-lookup"><span data-stu-id="abf98-131">You invoke an operator procedure implicitly by using the operator symbol in an expression.</span></span> <span data-ttu-id="abf98-132">İşlenenleri önceden tanımlanmış işleçler için yaptığınız şekilde sağlarsınız.</span><span class="sxs-lookup"><span data-stu-id="abf98-132">You supply the operands the same way you do for predefined operators.</span></span>

<span data-ttu-id="abf98-133">İşleç yordamına örtük çağrının sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="abf98-133">The syntax for an implicit call to an operator procedure is as follows:</span></span>

<span data-ttu-id="abf98-134">`Dim testStruct As`  *structurename*</span><span class="sxs-lookup"><span data-stu-id="abf98-134">`Dim testStruct As`  *structurename*</span></span>

<span data-ttu-id="abf98-135">`Dim testNewStruct As`*structurename* `= testStruct`*operatorsymbol* `10`</span><span class="sxs-lookup"><span data-stu-id="abf98-135">`Dim testNewStruct As`  *structurename*  `= testStruct`  *operatorsymbol*  `10`</span></span>

### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="abf98-136">Bildirim ve çağrı gösterimi</span><span class="sxs-lookup"><span data-stu-id="abf98-136">Illustration of Declaration and Call</span></span>

<span data-ttu-id="abf98-137">Aşağıdaki yapı, imzalı bir 128 bitlik tamsayı değerini, anayen yüksek sıralı ve düşük sıralı parçalar olarak depolar.</span><span class="sxs-lookup"><span data-stu-id="abf98-137">The following structure stores a signed 128-bit integer value as the constituent high-order and low-order parts.</span></span> <span data-ttu-id="abf98-138">İki `veryLong` değer eklemek ve elde edilen bir `veryLong` değeri oluşturmak için `+` işlecini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="abf98-138">It defines the `+` operator to add two `veryLong` values and generate a resulting `veryLong` value.</span></span>

[!code-vb[VbVbcnProcedures#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#23)]

<span data-ttu-id="abf98-139">Aşağıdaki örnek, `veryLong` tanımlanan `+` işlecine tipik bir çağrı gösterir.</span><span class="sxs-lookup"><span data-stu-id="abf98-139">The following example shows a typical call to the `+` operator defined on `veryLong`.</span></span>

[!code-vb[VbVbcnProcedures#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#24)]

## <a name="see-also"></a><span data-ttu-id="abf98-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="abf98-140">See also</span></span>

- [<span data-ttu-id="abf98-141">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="abf98-141">Procedures</span></span>](./index.md)
- [<span data-ttu-id="abf98-142">Alt Yordamlar</span><span class="sxs-lookup"><span data-stu-id="abf98-142">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="abf98-143">İşlev Yordamları</span><span class="sxs-lookup"><span data-stu-id="abf98-143">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="abf98-144">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="abf98-144">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="abf98-145">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="abf98-145">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="abf98-146">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="abf98-146">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="abf98-147">Nasıl yapılır: İşleç Tanımlama</span><span class="sxs-lookup"><span data-stu-id="abf98-147">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="abf98-148">Nasıl yapılır: Dönüştürme İşleci Tanımlama</span><span class="sxs-lookup"><span data-stu-id="abf98-148">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="abf98-149">Nasıl yapılır: Bir İşleç Yordamı Çağırma</span><span class="sxs-lookup"><span data-stu-id="abf98-149">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="abf98-150">Nasıl yapılır: İşleçleri Tanımlayan Bir Sınıf Kullanma</span><span class="sxs-lookup"><span data-stu-id="abf98-150">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
