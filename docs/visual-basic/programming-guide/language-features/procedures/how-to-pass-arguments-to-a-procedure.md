---
title: 'Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme'
ms.date: 07/20/2015
helpviewer_keywords:
- arguments [Visual Basic], passing to procedures
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], calling
- argument passing [Visual Basic], procedures
ms.assetid: 08723588-3890-4ddc-8249-79e049e0f241
ms.openlocfilehash: 816d6388a0dbb7ae346074d258ff651c793c5e0e
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071514"
---
# <a name="how-to-pass-arguments-to-a-procedure-visual-basic"></a><span data-ttu-id="d33a3-102">Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d33a3-102">How to: Pass Arguments to a Procedure (Visual Basic)</span></span>

<span data-ttu-id="d33a3-103">Bir yordamı çağırdığınızda, yordam adını parantez içindeki bir bağımsız değişken listesiyle takip edersiniz.</span><span class="sxs-lookup"><span data-stu-id="d33a3-103">When you call a procedure, you follow the procedure name with an argument list in parentheses.</span></span> <span data-ttu-id="d33a3-104">Yordamın tanımladığı her gerekli parametreye karşılık gelen bir bağımsız değişken sağlarsınız ve isteğe bağlı olarak parametrelere bağımsız değişkenler sağlayabilirsiniz `Optional` .</span><span class="sxs-lookup"><span data-stu-id="d33a3-104">You supply an argument corresponding to every required parameter the procedure defines, and you can optionally supply arguments to the `Optional` parameters.</span></span> <span data-ttu-id="d33a3-105">`Optional`Çağrıda bir parametre belirtmezseniz, sonraki bağımsız değişkenleri sağlarsanız, bağımsız değişken listesindeki yerini işaretlemek için bir virgül dahil etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d33a3-105">If you do not supply an `Optional` parameter in the call, you must include a comma to mark its place in the argument list if you are supplying any subsequent arguments.</span></span>  
  
 <span data-ttu-id="d33a3-106">Bir veri türünün bağımsız değişkenini, gibi karşılık gelen parametresinden farklı bir şekilde geçirmek istiyorsanız, `Byte` `String` tür denetimi anahtarını ([Option Strict ifadesini](../../../language-reference/statements/option-strict-statement.md)) olarak ayarlayabilirsiniz `Off` .</span><span class="sxs-lookup"><span data-stu-id="d33a3-106">If you intend to pass an argument of a data type different from that of its corresponding parameter, such as `Byte` to `String`, you can set the type-checking switch ([Option Strict Statement](../../../language-reference/statements/option-strict-statement.md)) to `Off`.</span></span> <span data-ttu-id="d33a3-107">`Option Strict`İse `On` , genişleyen dönüşümler ya da açık dönüştürme anahtar sözcükleri kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d33a3-107">If `Option Strict` is `On`, you must use either widening conversions or explicit conversion keywords.</span></span> <span data-ttu-id="d33a3-108">Daha fazla bilgi için bkz. [genişletme ve daraltma dönüştürmeleri](../data-types/widening-and-narrowing-conversions.md) ve [tür dönüştürme işlevleri](../../../language-reference/functions/type-conversion-functions.md).</span><span class="sxs-lookup"><span data-stu-id="d33a3-108">For more information, see [Widening and Narrowing Conversions](../data-types/widening-and-narrowing-conversions.md) and [Type Conversion Functions](../../../language-reference/functions/type-conversion-functions.md).</span></span>  
  
 <span data-ttu-id="d33a3-109">Daha fazla bilgi için bkz. [yordam parametreleri ve bağımsız değişkenleri](./procedure-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="d33a3-109">For more information, see [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md).</span></span>  
  
### <a name="to-pass-one-or-more-arguments-to-a-procedure"></a><span data-ttu-id="d33a3-110">Bir yordama bir veya daha fazla bağımsız değişken geçirmek için</span><span class="sxs-lookup"><span data-stu-id="d33a3-110">To pass one or more arguments to a procedure</span></span>  
  
1. <span data-ttu-id="d33a3-111">Çağırma ifadesinde, parantez ile yordam adını izleyin.</span><span class="sxs-lookup"><span data-stu-id="d33a3-111">In the calling statement, follow the procedure name with parentheses.</span></span>  
  
2. <span data-ttu-id="d33a3-112">Parantez içinde bir bağımsız değişken listesi koyun.</span><span class="sxs-lookup"><span data-stu-id="d33a3-112">Inside the parentheses, put an argument list.</span></span> <span data-ttu-id="d33a3-113">Yordamın tanımladığı her bir gerekli parametre için bir bağımsız değişken ekleyin ve bağımsız değişkenleri virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="d33a3-113">Include an argument for each required parameter the procedure defines, and separate the arguments with commas.</span></span>  
  
3. <span data-ttu-id="d33a3-114">Her bağımsız değişkenin, karşılık gelen parametre için, yordamın tanımladığı türe dönüştürülebilir bir veri türünü değerlendiren geçerli bir ifade olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="d33a3-114">Make sure each argument is a valid expression that evaluates to a data type convertible to the type the procedure defines for the corresponding parameter.</span></span>  
  
4. <span data-ttu-id="d33a3-115">Bir parametre [Isteğe bağlı](../../../language-reference/modifiers/optional.md)olarak tanımlanmışsa bağımsız değişken listesine dahil edebilir veya atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d33a3-115">If a parameter is defined as [Optional](../../../language-reference/modifiers/optional.md), you can either include it in the argument list or omit it.</span></span> <span data-ttu-id="d33a3-116">Bunu atlarsanız yordam, bu parametre için tanımlanan varsayılan değeri kullanır.</span><span class="sxs-lookup"><span data-stu-id="d33a3-116">If you omit it, the procedure uses the default value defined for that parameter.</span></span>  
  
5. <span data-ttu-id="d33a3-117">Bir parametre için bir bağımsız değişkeni atlarsanız `Optional` ve parametre listesinde bundan sonra başka bir parametre varsa, atlanan bağımsız değişkenin yerini bağımsız değişken listesinde fazladan bir virgülle işaretleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d33a3-117">If you omit an argument for an `Optional` parameter and there is another parameter after it in the parameter list, you can mark the place of the omitted argument by an extra comma in the argument list.</span></span>  
  
     <span data-ttu-id="d33a3-118">Aşağıdaki örnek Visual Basic <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> işlevini çağırır.</span><span class="sxs-lookup"><span data-stu-id="d33a3-118">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function.</span></span>  
  
     [!code-vb[VbVbcnProcedures#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#34)]  
  
     <span data-ttu-id="d33a3-119">Önceki örnek, görüntülenecek ileti dizesi olan gerekli ilk bağımsız değişkeni sağlar.</span><span class="sxs-lookup"><span data-stu-id="d33a3-119">The preceding example supplies the required first argument, which is the message string to be displayed.</span></span> <span data-ttu-id="d33a3-120">İleti kutusunda görüntülenecek düğmeleri belirten isteğe bağlı ikinci parametre için bir bağımsız değişkeni atlar.</span><span class="sxs-lookup"><span data-stu-id="d33a3-120">It omits an argument for the optional second parameter, which specifies the buttons to be displayed on the message box.</span></span> <span data-ttu-id="d33a3-121">Çağrı bir değer sağlamadığı için, `MsgBox` `MsgBoxStyle.OKOnly` yalnızca bir **Tamam** düğmesini görüntüleyen varsayılan değeri kullanır.</span><span class="sxs-lookup"><span data-stu-id="d33a3-121">Because the call does not supply a value, `MsgBox` uses the default value, `MsgBoxStyle.OKOnly`, which displays only an **OK** button.</span></span>  
  
     <span data-ttu-id="d33a3-122">Bağımsız değişken listesindeki ikinci virgül, atlanan ikinci bağımsız değişkenin yerini işaret ediyor ve son dize, `MsgBox` başlık çubuğunda görüntülenecek metin olan isteğe bağlı üçüncü parametreye geçirilir.</span><span class="sxs-lookup"><span data-stu-id="d33a3-122">The second comma in the argument list marks the place of the omitted second argument, and the last string is passed to the optional third parameter of `MsgBox`, which is the text to be displayed in the title bar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d33a3-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d33a3-123">See also</span></span>

- [<span data-ttu-id="d33a3-124">Alt Yordamlar</span><span class="sxs-lookup"><span data-stu-id="d33a3-124">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="d33a3-125">İşlev Yordamları</span><span class="sxs-lookup"><span data-stu-id="d33a3-125">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="d33a3-126">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="d33a3-126">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="d33a3-127">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="d33a3-127">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="d33a3-128">Nasıl yapılır: Bir Yordamın Parametresini Tanımlama</span><span class="sxs-lookup"><span data-stu-id="d33a3-128">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="d33a3-129">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="d33a3-129">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="d33a3-130">Özyinelemeli Yordamlar</span><span class="sxs-lookup"><span data-stu-id="d33a3-130">Recursive Procedures</span></span>](./recursive-procedures.md)
- [<span data-ttu-id="d33a3-131">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="d33a3-131">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="d33a3-132">Nesneler ve sınıflar</span><span class="sxs-lookup"><span data-stu-id="d33a3-132">Objects and Classes</span></span>](../objects-and-classes/index.md)
- [<span data-ttu-id="d33a3-133">Nesne odaklı programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d33a3-133">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)
