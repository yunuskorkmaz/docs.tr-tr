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
ms.openlocfilehash: d62c3480db56b5cbf22c1f3f6ff59ab220a48b09
ms.sourcegitcommit: 5e05f983e63d5bbd8c0b246d02c6e4f23d2fc1db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2019
ms.locfileid: "67152047"
---
# <a name="operator-procedures-visual-basic"></a><span data-ttu-id="259fb-102">İşleç Yordamları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="259fb-102">Operator Procedures (Visual Basic)</span></span>
<span data-ttu-id="259fb-103">Bir işleç yordamı standart işlecinin davranışını tanımlayan Visual Basic deyimleri bir dizisidir (gibi `*`, `<>`, veya `And`) bir sınıf veya yapı tanımladığınız üzerinde.</span><span class="sxs-lookup"><span data-stu-id="259fb-103">An operator procedure is a series of Visual Basic statements that define the behavior of a standard operator (such as `*`, `<>`, or `And`) on a class or structure you have defined.</span></span> <span data-ttu-id="259fb-104">Bu da adlandırılır *İşleç aşırı yüklemesi*.</span><span class="sxs-lookup"><span data-stu-id="259fb-104">This is also called *operator overloading*.</span></span>  
  
## <a name="when-to-define-operator-procedures"></a><span data-ttu-id="259fb-105">İşleç yordamları tanımlamak ne zaman</span><span class="sxs-lookup"><span data-stu-id="259fb-105">When to Define Operator Procedures</span></span>  
 <span data-ttu-id="259fb-106">Bir sınıf veya yapı tanımlandığında, bu sınıfın veya yapının türünde olmasını değişkenleri bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="259fb-106">When you have defined a class or structure, you can declare variables to be of the type of that class or structure.</span></span> <span data-ttu-id="259fb-107">Bazen bir ifadenin bir parçası olarak bir işlem katılmak bu tür bir değişken gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="259fb-107">Sometimes such a variable needs to participate in an operation as part of an expression.</span></span> <span data-ttu-id="259fb-108">Bunu yapmak için bir işlecinin bir işleneni olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="259fb-108">To do this, it must be an operand of an operator.</span></span>  
  
 <span data-ttu-id="259fb-109">Visual Basic, yalnızca temel veri türleri üzerinde işleçler tanımlar.</span><span class="sxs-lookup"><span data-stu-id="259fb-109">Visual Basic defines operators only on its fundamental data types.</span></span> <span data-ttu-id="259fb-110">Bir operatörün davranışını tanımlayabilirsiniz veya iki işlenenleri sınıf veya yapının türüdür.</span><span class="sxs-lookup"><span data-stu-id="259fb-110">You can define the behavior of an operator when one or both of the operands are of the type of your class or structure.</span></span>  
  
 <span data-ttu-id="259fb-111">Daha fazla bilgi için [Operator deyimi](../../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="259fb-111">For more information, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
## <a name="types-of-operator-procedure"></a><span data-ttu-id="259fb-112">İşleç yordamı türleri</span><span class="sxs-lookup"><span data-stu-id="259fb-112">Types of Operator Procedure</span></span>  
 <span data-ttu-id="259fb-113">Bir işleç yordamı şu türlerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="259fb-113">An operator procedure can be one of the following types:</span></span>  
  
- <span data-ttu-id="259fb-114">Bağımsız değişkeni, sınıfın veya yapının türünü olduğu birli işleç tanımı.</span><span class="sxs-lookup"><span data-stu-id="259fb-114">A definition of a unary operator where the argument is of the type of your class or structure.</span></span>  
  
- <span data-ttu-id="259fb-115">Sınıf veya yapı türünde olduğu en az bir bağımsız değişken ikili bir işleç tanımını.</span><span class="sxs-lookup"><span data-stu-id="259fb-115">A definition of a binary operator where at least one of the arguments is of the type of your class or structure.</span></span>  
  
- <span data-ttu-id="259fb-116">Bağımsız değişkeni, sınıfın veya yapının türünü olduğu bir dönüştürme operatörünün tanımı.</span><span class="sxs-lookup"><span data-stu-id="259fb-116">A definition of a conversion operator where the argument is of the type of your class or structure.</span></span>  
  
- <span data-ttu-id="259fb-117">Sınıf veya yapı türü döndüren bir dönüştürme operatörünün tanımı.</span><span class="sxs-lookup"><span data-stu-id="259fb-117">A definition of a conversion operator that returns the type of your class or structure.</span></span>  
  
 <span data-ttu-id="259fb-118">Dönüştürme işleçleri her zaman birli ve her zaman `CType` olduğunu tanımlama işleci olarak.</span><span class="sxs-lookup"><span data-stu-id="259fb-118">Conversion operators are always unary, and you always use `CType` as the operator you are defining.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="259fb-119">Bildirim Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="259fb-119">Declaration Syntax</span></span>  
 <span data-ttu-id="259fb-120">Bir işleç yordamı bildirmek için sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="259fb-120">The syntax for declaring an operator procedure is as follows:</span></span>  
 
 ```vb 
 Public Shared [Widening | Narrowing] Operator operatorsymbol ( operand1 [,  operand2 ]) As datatype  
  
 ' Statements of the operator procedure.
  
 End Operator
 ```
 
 <span data-ttu-id="259fb-121">Kullandığınız `Widening` veya `Narrowing` yalnızca bir tür dönüştürme işleci anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="259fb-121">You use the `Widening` or `Narrowing` keyword only on a type conversion operator.</span></span> <span data-ttu-id="259fb-122">Her zaman işlecin olduğu [CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md) için tür dönüştürme işleci.</span><span class="sxs-lookup"><span data-stu-id="259fb-122">The operator symbol is always [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) for a type conversion operator.</span></span>  
  
 <span data-ttu-id="259fb-123">İkili işleç tanımlamak için iki işlenenden bildirme ve bir tür dönüştürme işleci dahil olmak üzere bir birli işleç tanımlamak için tek bir işlenen bildirin.</span><span class="sxs-lookup"><span data-stu-id="259fb-123">You declare two operands to define a binary operator, and you declare one operand to define a unary operator, including a type conversion operator.</span></span> <span data-ttu-id="259fb-124">Tüm işlenenler bildirilmelidir `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="259fb-124">All operands must be declared `ByVal`.</span></span>  
  
 <span data-ttu-id="259fb-125">Her işlenen bildirmek için parametreleri aynı şekilde bildirmek [alt yordamlar](./sub-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="259fb-125">You declare each operand the same way you declare parameters for [Sub Procedures](./sub-procedures.md).</span></span>  
  
### <a name="data-type"></a><span data-ttu-id="259fb-126">Veri Türü</span><span class="sxs-lookup"><span data-stu-id="259fb-126">Data Type</span></span>  
 <span data-ttu-id="259fb-127">Bir sınıf veya yapı sizin tanımladığınız bir işleci tanımlama için en az bir işlenen, sınıfın veya yapının veri türünde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="259fb-127">Because you are defining an operator on a class or structure you have defined, at least one of the operands must be of the data type of that class or structure.</span></span> <span data-ttu-id="259fb-128">Tür dönüştürme işleci için işlenen ya da dönüş türü, sınıfın veya yapının veri türünde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="259fb-128">For a type conversion operator, either the operand or the return type must be of the data type of the class or structure.</span></span>  
  
 <span data-ttu-id="259fb-129">Daha fazla ayrıntı için [Operator deyimi](../../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="259fb-129">For more details, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="259fb-130">Arama söz dizimi</span><span class="sxs-lookup"><span data-stu-id="259fb-130">Calling Syntax</span></span>  
 <span data-ttu-id="259fb-131">Bir işleç yordamı örtük olarak bir ifadede operatör sembolünü kullanarak çağırın.</span><span class="sxs-lookup"><span data-stu-id="259fb-131">You invoke an operator procedure implicitly by using the operator symbol in an expression.</span></span> <span data-ttu-id="259fb-132">Önceden tanımlı operatörler için yaptığınız gibi işlenenler sağladığınız.</span><span class="sxs-lookup"><span data-stu-id="259fb-132">You supply the operands the same way you do for predefined operators.</span></span>  
  
 <span data-ttu-id="259fb-133">Bir işleç yordamı örtük çağrıyla sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="259fb-133">The syntax for an implicit call to an operator procedure is as follows:</span></span>  
  
 <span data-ttu-id="259fb-134">`Dim testStruct As`  *structurename*</span><span class="sxs-lookup"><span data-stu-id="259fb-134">`Dim testStruct As`  *structurename*</span></span>  
  
 <span data-ttu-id="259fb-135">`Dim testNewStruct As`  *structurename*`= testStruct`*işlecin*  `10`</span><span class="sxs-lookup"><span data-stu-id="259fb-135">`Dim testNewStruct As`  *structurename*  `= testStruct`  *operatorsymbol*  `10`</span></span>  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="259fb-136">Bildirim ve çağrı gösterimi</span><span class="sxs-lookup"><span data-stu-id="259fb-136">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="259fb-137">Aşağıdaki yapıya bağlı yüksek ve düşük düzey parçaları olarak 128-bit imzalı bir tamsayı değeri depolar.</span><span class="sxs-lookup"><span data-stu-id="259fb-137">The following structure stores a signed 128-bit integer value as the constituent high-order and low-order parts.</span></span> <span data-ttu-id="259fb-138">Tanımladığı `+` işleci iki eklemek için `veryLong` değerleri ve bir sonuç üretmek `veryLong` değeri.</span><span class="sxs-lookup"><span data-stu-id="259fb-138">It defines the `+` operator to add two `veryLong` values and generate a resulting `veryLong` value.</span></span>  
  
 [!code-vb[VbVbcnProcedures#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#23)]  
  
 <span data-ttu-id="259fb-139">Aşağıdaki örnek, tipik bir çağrı gösterir `+` tanımlanan işleci `veryLong`.</span><span class="sxs-lookup"><span data-stu-id="259fb-139">The following example shows a typical call to the `+` operator defined on `veryLong`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#24)]  

## <a name="see-also"></a><span data-ttu-id="259fb-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="259fb-140">See also</span></span>

- [<span data-ttu-id="259fb-141">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="259fb-141">Procedures</span></span>](./index.md)
- [<span data-ttu-id="259fb-142">Alt Yordamlar</span><span class="sxs-lookup"><span data-stu-id="259fb-142">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="259fb-143">İşlev Yordamları</span><span class="sxs-lookup"><span data-stu-id="259fb-143">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="259fb-144">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="259fb-144">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="259fb-145">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="259fb-145">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="259fb-146">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="259fb-146">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="259fb-147">Nasıl yapılır: Bir işleci tanımlama</span><span class="sxs-lookup"><span data-stu-id="259fb-147">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="259fb-148">Nasıl yapılır: Bir dönüşüm işleci tanımlama</span><span class="sxs-lookup"><span data-stu-id="259fb-148">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="259fb-149">Nasıl yapılır: Bir işleç yordamı çağırma</span><span class="sxs-lookup"><span data-stu-id="259fb-149">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="259fb-150">Nasıl yapılır: İşleçleri tanımlayan bir sınıf kullanma</span><span class="sxs-lookup"><span data-stu-id="259fb-150">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
