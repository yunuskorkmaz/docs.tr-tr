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
ms.openlocfilehash: 5b4641ce8509e3111a11ed803d36194d5a301bce
ms.sourcegitcommit: fc70fcb9c789b6a4aefcdace46f3643fd076450f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2018
ms.locfileid: "34805717"
---
# <a name="operator-procedures-visual-basic"></a><span data-ttu-id="f4735-102">İşleç Yordamları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f4735-102">Operator Procedures (Visual Basic)</span></span>
<span data-ttu-id="f4735-103">Bir dizi standart işleci davranışını tanımlamak Visual Basic deyimi bir işleç yordamı olduğu (gibi `*`, `<>`, veya `And`) bir sınıf veya yapı tanımladığınız.</span><span class="sxs-lookup"><span data-stu-id="f4735-103">An operator procedure is a series of Visual Basic statements that define the behavior of a standard operator (such as `*`, `<>`, or `And`) on a class or structure you have defined.</span></span> <span data-ttu-id="f4735-104">Bu da adlandırılır *İşleç aşırı yüklemesi*.</span><span class="sxs-lookup"><span data-stu-id="f4735-104">This is also called *operator overloading*.</span></span>  
  
## <a name="when-to-define-operator-procedures"></a><span data-ttu-id="f4735-105">İşleç yordamları tanımlamak ne zaman</span><span class="sxs-lookup"><span data-stu-id="f4735-105">When to Define Operator Procedures</span></span>  
 <span data-ttu-id="f4735-106">Bir sınıf veya yapı tanımlandığında, bu sınıf veya yapı türünde olmasını değişkenleri bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4735-106">When you have defined a class or structure, you can declare variables to be of the type of that class or structure.</span></span> <span data-ttu-id="f4735-107">Bazen bir ifadenin bir parçası olarak bir işlem katılmayı gibi bir değişken gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="f4735-107">Sometimes such a variable needs to participate in an operation as part of an expression.</span></span> <span data-ttu-id="f4735-108">Bunu yapmak için bir işlecinin işleneni olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f4735-108">To do this, it must be an operand of an operator.</span></span>  
  
 <span data-ttu-id="f4735-109">Visual Basic işleçleri üzerinde yalnızca kendi temel veri türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f4735-109">Visual Basic defines operators only on its fundamental data types.</span></span> <span data-ttu-id="f4735-110">Bir işleç davranışını tanımlamak ya da işlenen her ikisi de sınıf veya yapı türünü.</span><span class="sxs-lookup"><span data-stu-id="f4735-110">You can define the behavior of an operator when one or both of the operands are of the type of your class or structure.</span></span>  
  
 <span data-ttu-id="f4735-111">Daha fazla bilgi için bkz: [Operator deyimi](../../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f4735-111">For more information, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
## <a name="types-of-operator-procedure"></a><span data-ttu-id="f4735-112">İşleç yordamı türleri</span><span class="sxs-lookup"><span data-stu-id="f4735-112">Types of Operator Procedure</span></span>  
 <span data-ttu-id="f4735-113">Bir işleç yordamı şu türlerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="f4735-113">An operator procedure can be one of the following types:</span></span>  
  
-   <span data-ttu-id="f4735-114">Bağımsız değişken sınıf veya yapı türünü olduğu birli işleç tanımı.</span><span class="sxs-lookup"><span data-stu-id="f4735-114">A definition of a unary operator where the argument is of the type of your class or structure.</span></span>  
  
-   <span data-ttu-id="f4735-115">Sınıf veya yapı türünü olduğu en az bir bağımsız değişken ikili işleç tanımı.</span><span class="sxs-lookup"><span data-stu-id="f4735-115">A definition of a binary operator where at least one of the arguments is of the type of your class or structure.</span></span>  
  
-   <span data-ttu-id="f4735-116">Bağımsız değişken sınıf veya yapı türünü olduğu bir dönüşüm işleci tanımı.</span><span class="sxs-lookup"><span data-stu-id="f4735-116">A definition of a conversion operator where the argument is of the type of your class or structure.</span></span>  
  
-   <span data-ttu-id="f4735-117">Sınıf veya yapı türü döndüren bir dönüşüm işleci tanımı.</span><span class="sxs-lookup"><span data-stu-id="f4735-117">A definition of a conversion operator that returns the type of your class or structure.</span></span>  
  
 <span data-ttu-id="f4735-118">Dönüştürme işleçleri her zaman birli ve her zaman kullanmanız `CType` olduğunu tanımlama işleci olarak.</span><span class="sxs-lookup"><span data-stu-id="f4735-118">Conversion operators are always unary, and you always use `CType` as the operator you are defining.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="f4735-119">Bildirim Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f4735-119">Declaration Syntax</span></span>  
 <span data-ttu-id="f4735-120">Bir işleç yordamı bildirme söz dizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="f4735-120">The syntax for declaring an operator procedure is as follows:</span></span>  
  
 <span data-ttu-id="f4735-121">`Public Shared`   `[Widening | Narrowing]`   `Operator`  *işlecin* `(` *operand1*`[,`*operand2* `]) As` *veri türü*</span><span class="sxs-lookup"><span data-stu-id="f4735-121">`Public Shared`   `[Widening | Narrowing]`   `Operator`  *operatorsymbol*  `(` *operand1*  `[,`  *operand2* `]) As`  *datatype*</span></span>  
  
 `' Statements of the operator procedure.`  
  
 `End Operator`  
  
 <span data-ttu-id="f4735-122">Kullandığınız `Widening` veya `Narrowing` anahtar sözcüğü yalnızca bir tür dönüştürme işleci.</span><span class="sxs-lookup"><span data-stu-id="f4735-122">You use the `Widening` or `Narrowing` keyword only on a type conversion operator.</span></span> <span data-ttu-id="f4735-123">İşleç simgesi her zaman olduğu [CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md) için tür dönüştürme işleci.</span><span class="sxs-lookup"><span data-stu-id="f4735-123">The operator symbol is always [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) for a type conversion operator.</span></span>  
  
 <span data-ttu-id="f4735-124">İkili işleç tanımlamak için iki işlenen bildirme ve bir tür dönüştürme işleci dahil olmak üzere bir birli işleç tanımlamak için bir işlenen bildirin.</span><span class="sxs-lookup"><span data-stu-id="f4735-124">You declare two operands to define a binary operator, and you declare one operand to define a unary operator, including a type conversion operator.</span></span> <span data-ttu-id="f4735-125">Tüm işlenenleri bildirilmelidir `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="f4735-125">All operands must be declared `ByVal`.</span></span>  
  
 <span data-ttu-id="f4735-126">Her işlenen parametrelerini bildirme aynı şekilde bildirme [alt yordamlar](./sub-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="f4735-126">You declare each operand the same way you declare parameters for [Sub Procedures](./sub-procedures.md).</span></span>  
  
### <a name="data-type"></a><span data-ttu-id="f4735-127">Veri Türü</span><span class="sxs-lookup"><span data-stu-id="f4735-127">Data Type</span></span>  
 <span data-ttu-id="f4735-128">Bir sınıf veya yapı tanımladığınız bir işleci tanımlama olduğundan, işlenen en az biri bu sınıf veya yapı, veri türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f4735-128">Because you are defining an operator on a class or structure you have defined, at least one of the operands must be of the data type of that class or structure.</span></span> <span data-ttu-id="f4735-129">Tür dönüştürme işleci için işlenen veya dönüş türü sınıf veya yapı, veri türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f4735-129">For a type conversion operator, either the operand or the return type must be of the data type of the class or structure.</span></span>  
  
 <span data-ttu-id="f4735-130">Daha fazla ayrıntı için bkz: [Operator deyimi](../../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f4735-130">For more details, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="f4735-131">Arama sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f4735-131">Calling Syntax</span></span>  
 <span data-ttu-id="f4735-132">Bir işleç yordamı örtük olarak bir ifadede işleç simgesi kullanarak çağırır.</span><span class="sxs-lookup"><span data-stu-id="f4735-132">You invoke an operator procedure implicitly by using the operator symbol in an expression.</span></span> <span data-ttu-id="f4735-133">Önceden tanımlı işleçler için yaptığınız gibi işlenen sağlayın.</span><span class="sxs-lookup"><span data-stu-id="f4735-133">You supply the operands the same way you do for predefined operators.</span></span>  
  
 <span data-ttu-id="f4735-134">Bir işleç yordamı için örtük bir arama söz dizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="f4735-134">The syntax for an implicit call to an operator procedure is as follows:</span></span>  
  
 <span data-ttu-id="f4735-135">`Dim testStruct As`  *structurename*</span><span class="sxs-lookup"><span data-stu-id="f4735-135">`Dim testStruct As`  *structurename*</span></span>  
  
 <span data-ttu-id="f4735-136">`Dim testNewStruct As`  *structurename*`= testStruct`*işlecin*  `10`</span><span class="sxs-lookup"><span data-stu-id="f4735-136">`Dim testNewStruct As`  *structurename*  `= testStruct`  *operatorsymbol*  `10`</span></span>  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="f4735-137">Bildirim ve çağrı çizimi</span><span class="sxs-lookup"><span data-stu-id="f4735-137">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="f4735-138">Aşağıdaki yapısını imzalı 128-bit tamsayı değeri bağlı sırası yüksek ve düşük düzey parçaları olarak depolar.</span><span class="sxs-lookup"><span data-stu-id="f4735-138">The following structure stores a signed 128-bit integer value as the constituent high-order and low-order parts.</span></span> <span data-ttu-id="f4735-139">Tanımladığı `+` iki eklemek için işleci `veryLong` değerleri ve bir kaynaklanan oluşturmak `veryLong` değeri.</span><span class="sxs-lookup"><span data-stu-id="f4735-139">It defines the `+` operator to add two `veryLong` values and generate a resulting `veryLong` value.</span></span>  
  
 [!code-vb[VbVbcnProcedures#23](./codesnippet/VisualBasic/operator-procedures_1.vb)]  
  
 <span data-ttu-id="f4735-140">Aşağıdaki örnek tipik bir çağrı gösterilmektedir `+` tanımlanan işleci `veryLong`.</span><span class="sxs-lookup"><span data-stu-id="f4735-140">The following example shows a typical call to the `+` operator defined on `veryLong`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#24](./codesnippet/VisualBasic/operator-procedures_2.vb)]  
  
 <span data-ttu-id="f4735-141">Daha fazla bilgi ve örnekler için bkz: [İşleç aşırı yüklemesi Visual Basic 2005](https://msdn.microsoft.com/library/ms379613(v=vs.80).aspx).</span><span class="sxs-lookup"><span data-stu-id="f4735-141">For more information and examples, see [Operator Overloading in Visual Basic 2005](https://msdn.microsoft.com/library/ms379613(v=vs.80).aspx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4735-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f4735-142">See Also</span></span>  
 [<span data-ttu-id="f4735-143">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="f4735-143">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="f4735-144">Alt Yordamlar</span><span class="sxs-lookup"><span data-stu-id="f4735-144">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="f4735-145">İşlev Yordamları</span><span class="sxs-lookup"><span data-stu-id="f4735-145">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="f4735-146">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="f4735-146">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="f4735-147">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="f4735-147">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="f4735-148">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="f4735-148">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="f4735-149">Nasıl yapılır: İşleç Tanımlama</span><span class="sxs-lookup"><span data-stu-id="f4735-149">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)  
 [<span data-ttu-id="f4735-150">Nasıl yapılır: Dönüştürme İşleci Tanımlama</span><span class="sxs-lookup"><span data-stu-id="f4735-150">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="f4735-151">Nasıl yapılır: Bir İşleç Yordamı Çağırma</span><span class="sxs-lookup"><span data-stu-id="f4735-151">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)  
 [<span data-ttu-id="f4735-152">Nasıl yapılır: İşleçleri Tanımlayan Bir Sınıf Kullanma</span><span class="sxs-lookup"><span data-stu-id="f4735-152">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
