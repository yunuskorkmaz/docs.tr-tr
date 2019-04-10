---
title: 'Nasıl yapılır: Bağımsız değişkenleri geçirmek yordamına (Visual Basic)'
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
ms.openlocfilehash: 012ad8e6229958575030ee820a3b0b79cc50facc
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59333918"
---
# <a name="how-to-pass-arguments-to-a-procedure-visual-basic"></a><span data-ttu-id="0af14-102">Nasıl yapılır: Bağımsız değişkenleri geçirmek yordamına (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0af14-102">How to: Pass Arguments to a Procedure (Visual Basic)</span></span>
<span data-ttu-id="0af14-103">Bir yordamı çağırdığınızda, parantez içinde bir bağımsız değişken listesiyle yordam adı izleyin.</span><span class="sxs-lookup"><span data-stu-id="0af14-103">When you call a procedure, you follow the procedure name with an argument list in parentheses.</span></span> <span data-ttu-id="0af14-104">Yordamı tanımlar için gerekli her parametre karşılık gelen bir bağımsız değişken sağlayın ve isteğe bağlı bağımsız değişkenler sağlayabilirsiniz `Optional` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="0af14-104">You supply an argument corresponding to every required parameter the procedure defines, and you can optionally supply arguments to the `Optional` parameters.</span></span> <span data-ttu-id="0af14-105">Sağladığınız değil, bir `Optional` çağrı parametresi, sağladığınız sonraki herhangi bir bağımsız değişken, bunun yerine bağımsız değişken listesinde işaretlemek için virgül içermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="0af14-105">If you do not supply an `Optional` parameter in the call, you must include a comma to mark its place in the argument list if you are supplying any subsequent arguments.</span></span>  
  
 <span data-ttu-id="0af14-106">Bir veri türünde bir bağımsız değişken, karşılık gelen parametresinin farklı geçirileceğini düşünüyorsanız `Byte` için `String`, tür denetimi anahtarı ayarlayabilirsiniz ([Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) için `Off`.</span><span class="sxs-lookup"><span data-stu-id="0af14-106">If you intend to pass an argument of a data type different from that of its corresponding parameter, such as `Byte` to `String`, you can set the type-checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) to `Off`.</span></span> <span data-ttu-id="0af14-107">Varsa `Option Strict` olduğu `On`, kullanmanız gerekir veya açık dönüşüm anahtar sözcükleri dönüştürme işlemleri genişletme.</span><span class="sxs-lookup"><span data-stu-id="0af14-107">If `Option Strict` is `On`, you must use either widening conversions or explicit conversion keywords.</span></span> <span data-ttu-id="0af14-108">Daha fazla bilgi için [Widening ve daraltma dönüşümleri](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) ve [tür dönüştürme işlevleri](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span><span class="sxs-lookup"><span data-stu-id="0af14-108">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span></span>  
  
 <span data-ttu-id="0af14-109">Daha fazla bilgi için [parametreler ve bağımsız değişkenler](./procedure-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="0af14-109">For more information, see [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md).</span></span>  
  
### <a name="to-pass-one-or-more-arguments-to-a-procedure"></a><span data-ttu-id="0af14-110">Bir yordam için bir veya daha fazla bağımsız değişkenleri geçirmek için</span><span class="sxs-lookup"><span data-stu-id="0af14-110">To pass one or more arguments to a procedure</span></span>  
  
1. <span data-ttu-id="0af14-111">Arama deyiminde parantezler yordamın adıyla izleyin.</span><span class="sxs-lookup"><span data-stu-id="0af14-111">In the calling statement, follow the procedure name with parentheses.</span></span>  
  
2. <span data-ttu-id="0af14-112">Parantez içinde bir bağımsız değişken listesi yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="0af14-112">Inside the parentheses, put an argument list.</span></span> <span data-ttu-id="0af14-113">Yordamı tanımlar her gerekli parametre için bir bağımsız değişken içerir ve bağımsız değişkenlerin virgülle ayırın.</span><span class="sxs-lookup"><span data-stu-id="0af14-113">Include an argument for each required parameter the procedure defines, and separate the arguments with commas.</span></span>  
  
3. <span data-ttu-id="0af14-114">Her değişken için karşılık gelen parametre veri öğesine dönüştürülebilir bir türün yordamı türü olarak değerlendirilen bir geçerli ifade tanımlar olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="0af14-114">Make sure each argument is a valid expression that evaluates to a data type convertible to the type the procedure defines for the corresponding parameter.</span></span>  
  
4. <span data-ttu-id="0af14-115">Bir parametre olarak tanımlanmışsa [isteğe bağlı](../../../../visual-basic/language-reference/modifiers/optional.md), bağımsız değişken listesinde içerebilir veya atlayın.</span><span class="sxs-lookup"><span data-stu-id="0af14-115">If a parameter is defined as [Optional](../../../../visual-basic/language-reference/modifiers/optional.md), you can either include it in the argument list or omit it.</span></span> <span data-ttu-id="0af14-116">Atlarsanız, yordam Bu parametre için tanımlanan varsayılan değeri kullanır.</span><span class="sxs-lookup"><span data-stu-id="0af14-116">If you omit it, the procedure uses the default value defined for that parameter.</span></span>  
  
5. <span data-ttu-id="0af14-117">Bir bağımsız değişken atlarsanız bir `Optional` parametresi ve başka bir parametre sonra parametre listesinde, bir atlanmış bağımsız değişkeni yerine, bağımsız değişken listesinde fazladan bir virgül tarafından işaretleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0af14-117">If you omit an argument for an `Optional` parameter and there is another parameter after it in the parameter list, you can mark the place of the omitted argument by an extra comma in the argument list.</span></span>  
  
     <span data-ttu-id="0af14-118">Aşağıdaki örnek, Visual Basic çağırır <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> işlevi.</span><span class="sxs-lookup"><span data-stu-id="0af14-118">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function.</span></span>  
  
     [!code-vb[VbVbcnProcedures#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#34)]  
  
     <span data-ttu-id="0af14-119">Yukarıdaki örnekte, görüntülenecek iletiyi dize gerekli ilk bağımsız değişkeni sağlar.</span><span class="sxs-lookup"><span data-stu-id="0af14-119">The preceding example supplies the required first argument, which is the message string to be displayed.</span></span> <span data-ttu-id="0af14-120">Bu ileti kutusunda gösterilecek düğmeler belirten isteğe bağlı ikinci parametresi için bağımsız değişken atlar.</span><span class="sxs-lookup"><span data-stu-id="0af14-120">It omits an argument for the optional second parameter, which specifies the buttons to be displayed on the message box.</span></span> <span data-ttu-id="0af14-121">Çağrısı bir değer sağlamaz çünkü `MsgBox` varsayılan değeri kullandığını `MsgBoxStyle.OKOnly`, yalnızca görüntüleyen bir **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="0af14-121">Because the call does not supply a value, `MsgBox` uses the default value, `MsgBoxStyle.OKOnly`, which displays only an **OK** button.</span></span>  
  
     <span data-ttu-id="0af14-122">İkinci bağımsız değişken listesinde virgülden belirtilmemişse ikinci bağımsız değişkenin bir yerde işaretler ve son dizeyse, isteğe bağlı üçüncü parametresi için geçirilen `MsgBox`, başlık çubuğunda görüntülenecek metni olduğu.</span><span class="sxs-lookup"><span data-stu-id="0af14-122">The second comma in the argument list marks the place of the omitted second argument, and the last string is passed to the optional third parameter of `MsgBox`, which is the text to be displayed in the title bar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0af14-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0af14-123">See also</span></span>

- [<span data-ttu-id="0af14-124">Alt Yordamlar</span><span class="sxs-lookup"><span data-stu-id="0af14-124">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="0af14-125">İşlev Yordamları</span><span class="sxs-lookup"><span data-stu-id="0af14-125">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="0af14-126">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="0af14-126">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="0af14-127">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="0af14-127">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="0af14-128">Nasıl yapılır: Bir Yordamın Parametresini Tanımlama</span><span class="sxs-lookup"><span data-stu-id="0af14-128">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="0af14-129">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="0af14-129">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="0af14-130">Özyinelemeli Yordamlar</span><span class="sxs-lookup"><span data-stu-id="0af14-130">Recursive Procedures</span></span>](./recursive-procedures.md)
- [<span data-ttu-id="0af14-131">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="0af14-131">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="0af14-132">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="0af14-132">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="0af14-133">Nesne odaklı programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0af14-133">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)
