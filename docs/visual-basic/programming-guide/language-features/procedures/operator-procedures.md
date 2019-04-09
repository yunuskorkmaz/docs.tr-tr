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
ms.openlocfilehash: 80c9a77494be95365899c6a25435fcfc5d2a7293
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59175025"
---
# <a name="operator-procedures-visual-basic"></a><span data-ttu-id="a2ae0-102">İşleç Yordamları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2ae0-102">Operator Procedures (Visual Basic)</span></span>
<span data-ttu-id="a2ae0-103">Bir işleç yordamı standart işlecinin davranışını tanımlayan Visual Basic deyimleri bir dizisidir (gibi `*`, `<>`, veya `And`) bir sınıf veya yapı tanımladığınız üzerinde.</span><span class="sxs-lookup"><span data-stu-id="a2ae0-103">An operator procedure is a series of Visual Basic statements that define the behavior of a standard operator (such as `*`, `<>`, or `And`) on a class or structure you have defined.</span></span> <span data-ttu-id="a2ae0-104">Bu da adlandırılır *İşleç aşırı yüklemesi*.</span><span class="sxs-lookup"><span data-stu-id="a2ae0-104">This is also called *operator overloading*.</span></span>  
  
## <a name="when-to-define-operator-procedures"></a><span data-ttu-id="a2ae0-105">İşleç yordamları tanımlamak ne zaman</span><span class="sxs-lookup"><span data-stu-id="a2ae0-105">When to Define Operator Procedures</span></span>  
 <span data-ttu-id="a2ae0-106">Bir sınıf veya yapı tanımlandığında, bu sınıfın veya yapının türünde olmasını değişkenleri bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a2ae0-106">When you have defined a class or structure, you can declare variables to be of the type of that class or structure.</span></span> <span data-ttu-id="a2ae0-107">Bazen bir ifadenin bir parçası olarak bir işlem katılmak bu tür bir değişken gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="a2ae0-107">Sometimes such a variable needs to participate in an operation as part of an expression.</span></span> <span data-ttu-id="a2ae0-108">Bunu yapmak için bir işlecinin bir işleneni olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a2ae0-108">To do this, it must be an operand of an operator.</span></span>  
  
 <span data-ttu-id="a2ae0-109">Visual Basic, yalnızca temel veri türleri üzerinde işleçler tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a2ae0-109">Visual Basic defines operators only on its fundamental data types.</span></span> <span data-ttu-id="a2ae0-110">Bir operatörün davranışını tanımlayabilirsiniz veya iki işlenenleri sınıf veya yapının türüdür.</span><span class="sxs-lookup"><span data-stu-id="a2ae0-110">You can define the behavior of an operator when one or both of the operands are of the type of your class or structure.</span></span>  
  
 <span data-ttu-id="a2ae0-111">Daha fazla bilgi için [Operator deyimi](../../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a2ae0-111">For more information, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
## <a name="types-of-operator-procedure"></a><span data-ttu-id="a2ae0-112">İşleç yordamı türleri</span><span class="sxs-lookup"><span data-stu-id="a2ae0-112">Types of Operator Procedure</span></span>  
 <span data-ttu-id="a2ae0-113">Bir işleç yordamı şu türlerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="a2ae0-113">An operator procedure can be one of the following types:</span></span>  
  
-   <span data-ttu-id="a2ae0-114">Bağımsız değişkeni, sınıfın veya yapının türünü olduğu birli işleç tanımı.</span><span class="sxs-lookup"><span data-stu-id="a2ae0-114">A definition of a unary operator where the argument is of the type of your class or structure.</span></span>  
  
-   <span data-ttu-id="a2ae0-115">Sınıf veya yapı türünde olduğu en az bir bağımsız değişken ikili bir işleç tanımını.</span><span class="sxs-lookup"><span data-stu-id="a2ae0-115">A definition of a binary operator where at least one of the arguments is of the type of your class or structure.</span></span>  
  
-   <span data-ttu-id="a2ae0-116">Bağımsız değişkeni, sınıfın veya yapının türünü olduğu bir dönüştürme operatörünün tanımı.</span><span class="sxs-lookup"><span data-stu-id="a2ae0-116">A definition of a conversion operator where the argument is of the type of your class or structure.</span></span>  
  
-   <span data-ttu-id="a2ae0-117">Sınıf veya yapı türü döndüren bir dönüştürme operatörünün tanımı.</span><span class="sxs-lookup"><span data-stu-id="a2ae0-117">A definition of a conversion operator that returns the type of your class or structure.</span></span>  
  
 <span data-ttu-id="a2ae0-118">Dönüştürme işleçleri her zaman birli ve her zaman `CType` olduğunu tanımlama işleci olarak.</span><span class="sxs-lookup"><span data-stu-id="a2ae0-118">Conversion operators are always unary, and you always use `CType` as the operator you are defining.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="a2ae0-119">Bildirim Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a2ae0-119">Declaration Syntax</span></span>  
 <span data-ttu-id="a2ae0-120">Bir işleç yordamı bildirmek için sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="a2ae0-120">The syntax for declaring an operator procedure is as follows:</span></span>  
  
 `Public Shared`   `[Widening | Narrowing]`   `Operator`  <span data-ttu-id="a2ae0-121">*işlecin* `(` *işlenen1*`[,`*işlenen2* `]) As` *veri türü* </span><span class="sxs-lookup"><span data-stu-id="a2ae0-121">*operatorsymbol*  `(` *operand1*  `[,`  *operand2* `]) As`  *datatype*</span></span>  
  
 `' Statements of the operator procedure.`  
  
 `End Operator`  
  
 <span data-ttu-id="a2ae0-122">Kullandığınız `Widening` veya `Narrowing` yalnızca bir tür dönüştürme işleci anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="a2ae0-122">You use the `Widening` or `Narrowing` keyword only on a type conversion operator.</span></span> <span data-ttu-id="a2ae0-123">Her zaman işlecin olduğu [CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md) için tür dönüştürme işleci.</span><span class="sxs-lookup"><span data-stu-id="a2ae0-123">The operator symbol is always [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) for a type conversion operator.</span></span>  
  
 <span data-ttu-id="a2ae0-124">İkili işleç tanımlamak için iki işlenenden bildirme ve bir tür dönüştürme işleci dahil olmak üzere bir birli işleç tanımlamak için tek bir işlenen bildirin.</span><span class="sxs-lookup"><span data-stu-id="a2ae0-124">You declare two operands to define a binary operator, and you declare one operand to define a unary operator, including a type conversion operator.</span></span> <span data-ttu-id="a2ae0-125">Tüm işlenenler bildirilmelidir `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="a2ae0-125">All operands must be declared `ByVal`.</span></span>  
  
 <span data-ttu-id="a2ae0-126">Her işlenen bildirmek için parametreleri aynı şekilde bildirmek [alt yordamlar](./sub-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="a2ae0-126">You declare each operand the same way you declare parameters for [Sub Procedures](./sub-procedures.md).</span></span>  
  
### <a name="data-type"></a><span data-ttu-id="a2ae0-127">Veri Türü</span><span class="sxs-lookup"><span data-stu-id="a2ae0-127">Data Type</span></span>  
 <span data-ttu-id="a2ae0-128">Bir sınıf veya yapı sizin tanımladığınız bir işleci tanımlama için en az bir işlenen, sınıfın veya yapının veri türünde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a2ae0-128">Because you are defining an operator on a class or structure you have defined, at least one of the operands must be of the data type of that class or structure.</span></span> <span data-ttu-id="a2ae0-129">Tür dönüştürme işleci için işlenen ya da dönüş türü, sınıfın veya yapının veri türünde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a2ae0-129">For a type conversion operator, either the operand or the return type must be of the data type of the class or structure.</span></span>  
  
 <span data-ttu-id="a2ae0-130">Daha fazla ayrıntı için [Operator deyimi](../../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a2ae0-130">For more details, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="a2ae0-131">Arama söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a2ae0-131">Calling Syntax</span></span>  
 <span data-ttu-id="a2ae0-132">Bir işleç yordamı örtük olarak bir ifadede operatör sembolünü kullanarak çağırın.</span><span class="sxs-lookup"><span data-stu-id="a2ae0-132">You invoke an operator procedure implicitly by using the operator symbol in an expression.</span></span> <span data-ttu-id="a2ae0-133">Önceden tanımlı operatörler için yaptığınız gibi işlenenler sağladığınız.</span><span class="sxs-lookup"><span data-stu-id="a2ae0-133">You supply the operands the same way you do for predefined operators.</span></span>  
  
 <span data-ttu-id="a2ae0-134">Bir işleç yordamı örtük çağrıyla sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="a2ae0-134">The syntax for an implicit call to an operator procedure is as follows:</span></span>  
  
 `Dim testStruct As`  *<span data-ttu-id="a2ae0-135">structurename</span><span class="sxs-lookup"><span data-stu-id="a2ae0-135">structurename</span></span>*  
  
 `Dim testNewStruct As`  <span data-ttu-id="a2ae0-136">*structurename*`= testStruct`*işlecin* </span><span class="sxs-lookup"><span data-stu-id="a2ae0-136">*structurename*  `= testStruct`  *operatorsymbol*</span></span>  `10`  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="a2ae0-137">Bildirim ve çağrı gösterimi</span><span class="sxs-lookup"><span data-stu-id="a2ae0-137">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="a2ae0-138">Aşağıdaki yapıya bağlı yüksek ve düşük düzey parçaları olarak 128-bit imzalı bir tamsayı değeri depolar.</span><span class="sxs-lookup"><span data-stu-id="a2ae0-138">The following structure stores a signed 128-bit integer value as the constituent high-order and low-order parts.</span></span> <span data-ttu-id="a2ae0-139">Tanımladığı `+` işleci iki eklemek için `veryLong` değerleri ve bir sonuç üretmek `veryLong` değeri.</span><span class="sxs-lookup"><span data-stu-id="a2ae0-139">It defines the `+` operator to add two `veryLong` values and generate a resulting `veryLong` value.</span></span>  
  
 [!code-vb[VbVbcnProcedures#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#23)]  
  
 <span data-ttu-id="a2ae0-140">Aşağıdaki örnek, tipik bir çağrı gösterir `+` tanımlanan işleci `veryLong`.</span><span class="sxs-lookup"><span data-stu-id="a2ae0-140">The following example shows a typical call to the `+` operator defined on `veryLong`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#24)]  

## <a name="see-also"></a><span data-ttu-id="a2ae0-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2ae0-141">See also</span></span>

- [<span data-ttu-id="a2ae0-142">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="a2ae0-142">Procedures</span></span>](./index.md)
- [<span data-ttu-id="a2ae0-143">Alt Yordamlar</span><span class="sxs-lookup"><span data-stu-id="a2ae0-143">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="a2ae0-144">İşlev Yordamları</span><span class="sxs-lookup"><span data-stu-id="a2ae0-144">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="a2ae0-145">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="a2ae0-145">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="a2ae0-146">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="a2ae0-146">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="a2ae0-147">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="a2ae0-147">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="a2ae0-148">Nasıl yapılır: İşleç Tanımlama</span><span class="sxs-lookup"><span data-stu-id="a2ae0-148">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="a2ae0-149">Nasıl yapılır: Dönüştürme İşleci Tanımlama</span><span class="sxs-lookup"><span data-stu-id="a2ae0-149">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="a2ae0-150">Nasıl yapılır: Bir İşleç Yordamı Çağırma</span><span class="sxs-lookup"><span data-stu-id="a2ae0-150">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="a2ae0-151">Nasıl yapılır: İşleçleri Tanımlayan Bir Sınıf Kullanma</span><span class="sxs-lookup"><span data-stu-id="a2ae0-151">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
